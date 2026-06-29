# Iluminity Inc. — Website & Template Library

A static-HTML, zero-build website for **Iluminity Inc.** (AI solutions, CRM & web design agency) plus a complete **Template Library** of professional, industry-specific website templates.

Deployed on **Vercel** · Live at [iluminity-oficial.vercel.app](https://iluminity-oficial.vercel.app)

---

## Table of Contents

1. [Project Structure](#project-structure)
2. [How to Run Locally](#how-to-run-locally)
3. [Template Library Overview](#template-library-overview)
4. [How to Add a New Industry Template](#how-to-add-a-new-industry-template)
5. [Customizing Content & Assets](#customizing-content--assets)
6. [Design Tokens & Style Conventions](#design-tokens--style-conventions)

---

## Project Structure

```
Iluminity_Oficial/
│
├── index.html              # Language-detect redirect (→ en/es/pt-br)
├── en.html                 # Main site — English
├── es.html                 # Main site — Spanish
├── pt-br.html              # Main site — Portuguese (Brazil)
│
├── templates/
│   └── index.html          # Template Library gallery (all 10 industry cards)
│
├── roofing/
│   └── index.html          # Roofing company template
├── dental/
│   └── index.html          # Dental practice template
├── hvac/
│   └── index.html          # HVAC company template
├── realtor/
│   └── index.html          # Real estate agent template
├── law/
│   └── index.html          # Law firm template
├── restaurant/
│   └── index.html          # Restaurant template
├── medspa/
│   └── index.html          # Medical spa template
├── electrician/
│   └── index.html          # Electrician template
├── plumber/
│   └── index.html          # Plumber template
├── landscaping/
│   └── index.html          # Landscaping company template
│
├── assets/
│   └── brand/
│       ├── favicon.svg
│       ├── iluminity-logo.svg
│       └── og-image.svg
│
├── robots.txt
├── sitemap.xml
└── vercel.json             # Vercel routing & redirect rules
```

---

## How to Run Locally

No build step required. Just serve the files with any static server.

**Option 1 — Python (built-in, no install needed):**
```bash
cd Iluminity_Oficial
python3 -m http.server 3000
# Open http://localhost:3000
```

**Option 2 — Node.js `serve` package:**
```bash
npx serve .
# Open the URL shown in the terminal
```

**Option 3 — VS Code Live Server extension:**
Open the project folder in VS Code, right-click `index.html` → "Open with Live Server".

---

## Template Library Overview

Visit `/templates/` to browse all available industry templates. Each card links to a fully built one-page website template.

| Route | Industry | Accent Color | Mini-Feature |
|-------|----------|-------------|--------------|
| `/roofing/` | Roofing | `#e55c1a` | Roof Material Estimator |
| `/dental/` | Dental | `#0ea5e9` | Appointment Selector |
| `/hvac/` | HVAC | `#f59e0b` | Service Urgency Selector |
| `/realtor/` | Real Estate | `#8b5cf6` | Property Spotlight Filter |
| `/law/` | Law Firm | `#6366f1` | Case Intake Selector |
| `/restaurant/` | Restaurant | `#ef4444` | Table Reservation Widget |
| `/medspa/` | Medical Spa | `#ec4899` | Treatment Pricing Selector |
| `/electrician/` | Electrician | `#eab308` | Issue Diagnostic Helper |
| `/plumber/` | Plumber | `#3b82f6` | Emergency/Scheduled Toggle |
| `/landscaping/` | Landscaping | `#22c55e` | Project Budget Estimator |

Each template includes:
- **Hero** section with industry-specific headline & CTAs
- **Services** section (6 service cards with icons)
- **About / Trust** section with social proof stats
- **Testimonials** (3 client reviews)
- **Contact form** with client-side validation
- **Footer** with nav & contact info
- **Interactive mini-feature** unique to each industry

---

## How to Add a New Industry Template

1. **Create the directory and file:**
   ```
   mkdir -p <industry-name>
   touch <industry-name>/index.html
   ```

2. **Copy an existing template as your starting point:**
   ```bash
   cp roofing/index.html <industry-name>/index.html
   ```

3. **Edit the template file:**
   - Update `<title>` and all meta tags
   - Change the accent color CSS variable: `--accent: #yourcolor;`
   - Replace all copy (hero headline, services, testimonials, etc.)
   - Replace the mini-feature section with an industry-appropriate interactive widget

4. **Add the card to the library:**
   Open `templates/index.html` and add a new card in the `#templates-grid` section:
   ```html
   <article class="template-card" data-category="Home Services" data-name="new industry">
     <div class="card-icon">🔨</div>
     <div class="card-body">
       <span class="card-badge" style="--badge-color:#yourcolor">Home Services</span>
       <h3>New Industry</h3>
       <p>Short one-sentence description of this template.</p>
     </div>
     <a href="/new-industry/" class="card-cta">Preview Template →</a>
   </article>
   ```

5. **Update `vercel.json`** (optional) if you want the route to redirect cleanly without the trailing slash.

6. **Update `sitemap.xml`** to include the new route.

---

## Customizing Content & Assets

### Changing the business name, phone, or address
Search and replace in the relevant template HTML file. All contact info is in:
- The **Hero** section (phone CTA button)
- The **Contact** section (address/phone/email)
- The **Footer** (address block)

### Changing the accent color
Each template file uses a single CSS variable at the top of the `<style>` block:
```css
:root {
  --accent: #e55c1a;      /* Change this for the whole page */
  --accent-dim: rgba(229, 92, 26, 0.15);
  --accent-glow: 0 0 40px rgba(229, 92, 26, 0.25);
}
```

### Swapping images
Templates use CSS gradient backgrounds and emoji icons instead of photo images (for easy customization). To add a real photo:
1. Add the image to `assets/` (e.g., `assets/roofing-hero.jpg`)
2. Replace the hero background gradient with: `background-image: url('/assets/roofing-hero.jpg');`
3. Add `background-size: cover; background-position: center;` to the hero styles

### Updating meta tags & SEO
At the top of each HTML file, update:
- `<title>` tag
- `<meta name="description">` content
- `<meta property="og:*">` Open Graph tags

---

## Design Tokens & Style Conventions

All pages share these base design tokens (defined per-page in `<style>` blocks):

```css
:root {
  /* Base palette */
  --bg:     #02050a;
  --bg-2:   #06111f;
  --text:   #f7fbff;
  --muted:  #a7b3c4;
  --line:   rgba(255, 255, 255, 0.14);

  /* Per-industry accent (override in each template) */
  --accent:     #36a3ff;
  --accent-dim: rgba(54, 163, 255, 0.15);

  /* Typography */
  /* Font: Inter — loaded from Google Fonts in each page */

  /* Layout */
  --radius: 26px;
  --container: min(1180px, calc(100% - 40px));
}
```

**Component conventions:**
- `.btn-primary` — filled accent button, used for primary CTAs
- `.btn-outline` — bordered ghost button, used for secondary CTAs
- `.section` — standard section with `padding: 100px 0`
- `.container` — centered content wrapper at max `1180px`
- `.grid-3` — 3-column responsive grid (collapses to 1 on mobile)
- `.card` — glassmorphism card with `background: var(--card)` and `border-radius: var(--radius)`

---

## Deployment

The site is configured for **Vercel**. Push to `main` to deploy automatically.

`vercel.json` handles:
- Language-based redirects for the main site (`/` → `en.html`, `es.html`, or `pt-br.html` based on country/cookie)
- Clean URL routing for template pages (`/templates` → `/templates/`, etc.)

---

*Built by [Iluminity Inc.](https://iluminity-oficial.vercel.app) — AI Solutions for Service Businesses*
