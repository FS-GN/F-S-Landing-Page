
**Government of Nunavut · Department of Community Services**

A suite of web-based application portals for the Fisheries & Sealing Division, consolidated under a single landing page. Built as static HTML files for deployment on GitHub Pages — no build step, no server, no dependencies.

---

## Live Site

> `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

*(Update this URL after enabling GitHub Pages)*

---

## What's Included

| File | Portal | Description |
|------|--------|-------------|
| `index.html` | **Landing Page** | Hub page with About, News, Key Dates, Quick Links, and portal cards |
| `index_funding.html` | **Funding Finder** | Cross-program discovery tool — matches users to eligible programs |
| `index_CFFS_Portal.html` | **Commercial Fisheries Freight Subsidy** | Apply for freight subsidies, check status, admin review |
| `index_FDDPP_Portal.html` | **Fisheries Development & Diversification Program** | Apply for development funding, check status, admin review |
| `index_SealFur_Portal.html` | **Seal & Fur Programs** | Four policy schedules (A–D), apply, check status, admin review |
| `rv_nuliajuk_portal.html` | **RV Nuliajuk Research Vessel** | Vessel info, season schedule, proposals, EOIs, admin dashboard |

---

## Repository Structure

```
fisheries-portals/
├── index.html                  ← Landing page (start here)
├── index_funding.html          ← Funding Finder
├── index_CFFS_Portal.html      ← Freight Subsidy portal
├── index_FDDPP_Portal.html     ← Development Program portal
├── index_SealFur_Portal.html   ← Seal & Fur portal
├── rv_nuliajuk_portal.html     ← RV Nuliajuk portal
├── images/                     ← Logo assets (add after receiving from Comms)
│   ├── gn-symbol-wordmark.png  ← Official polar bear + wordmark
│   └── gn-wordmark-negative.png← White version for dark backgrounds
└── README.md                   ← This file
```

All files must remain in the **root directory** — the landing page loads portals via iframes using relative paths.

---

## Deployment (GitHub Pages)

1. **Create a repository** at [github.com/new](https://github.com/new) (public).
2. **Upload all 6 HTML files** to the repository root via "Add file → Upload files."
3. **Enable GitHub Pages:**
   - Go to **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **main**, folder: **/ (root)**
   - Click **Save**
4. Your site will be live within 1–2 minutes at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

---

## How to Edit Content

All content is hardcoded in plain HTML. Open the relevant file in any text editor (or edit directly on GitHub) and save.

### Editing News Items (`index.html`)

News items are inside `<div class="news-list">`. Each item looks like this:

```html
<div class="news-item">
  <div class="news-meta">
    <span class="news-date">March 15, 2026</span>
    <span class="news-badge pinned">Important</span>
  </div>
  <div class="news-title">Your Headline Here</div>
  <div class="news-body">Your description text here.</div>
</div>
```

**To add a news item:** Copy the block above, paste it at the top of the news list (newest first), and change the date, title, and body.

**To remove a news item:** Delete the entire `<div class="news-item">...</div>` block.

**Badge options:**
- `<span class="news-badge pinned">Important</span>` — yellow highlight for urgent items
- `<span class="news-badge">Update</span>` — standard blue badge
- Change the text inside to anything: "Deadline", "Report", "Vessel", "New", etc.

### Editing Key Dates (`index.html`)

Key dates are inside the `<div class="sidebar-panel">` under the "Key Dates" header. Each date item:

```html
<div class="date-item">
  <div class="date-pip urgent"></div>    <!-- Remove "urgent" class for non-urgent -->
  <div class="date-label">
    <strong>Deadline Name</strong>
    <span class="date-when">April 30, 2026</span>
  </div>
</div>
```

Add `urgent` class to `date-pip` for imminent deadlines (shows red dot). Remove it for normal dates (blue dot).

### Editing the About Section (`index.html`)

Find `<div class="about-text">` and edit the paragraphs directly. Contact details are in `<div class="about-sidebar">`.

### Editing Portal Content

Each portal is a self-contained HTML file. Open the relevant file and search for the section you want to change. Key areas:

- **Supabase credentials:** Search for `YOUR_SUPABASE_URL` at the top of each portal file. Replace with real Supabase project values to go live.
- **Demo data:** Search for `DEMO_APPS` or `DEMO_PROPOSALS` to modify sample data.
- **Contact emails:** Search for `fisheries@gov.nu.ca` or the program-specific email.

---

## Demo Mode

All portals run in **demo mode** by default. Demo mode activates when Supabase credentials are set to `YOUR_SUPABASE_URL` (the placeholder value). In demo mode:

- Sample applications, proposals, and messages are loaded from hardcoded data
- Form submissions are stored in browser memory (reset on page refresh)
- A yellow "Demo Mode" banner appears at the top of each portal
- All features are fully functional for testing

To go live, replace the Supabase credentials in each portal file:

```javascript
const SUPABASE_URL      = "https://your-project.supabase.co";
const SUPABASE_ANON_KEY = "your-anon-key-here";
```

---

## GN Visual Identity Standards

The landing page follows the Government of Nunavut Visual Identity Standards (February 2000). Key requirements:

| Element | Standard | Implementation |
|---------|----------|----------------|
| **Primary colour** | Pantone 301 Blue | `#0054A4` — used for header, headings, links, accent lines |
| **Text colour** | 100% Black | `#000000` / `#1A1A1A` for body text |
| **Typeface** | Arial, Arial Bold | `font-family: Arial, Helvetica, sans-serif` throughout |
| **Horizontal rules** | Blue line treatment | Applied under header, section headings, and footer top |
| **Logo** | Polar bear symbol + wordmark only | Placeholder SVG included; replace with official assets |

### Logo Rules (from the identity guide)

- The polar bear symbol **must never appear without the wordmark** "ᓄᓇᕗᑦ Nunavut"
- The symbol must **always be in its positive configuration** — no negative/reversed versions
- On dark backgrounds, the symbol must be **separated by a white border**
- Minimum size: **4.5 picas (~57px)** for the full symbol, **1.5 picas (~19px)** for the wordmark alone
- Only **Pantone 301 Blue or 100% Black** may be used for the symbol and wordmark

### Adding the Official Logo

1. Request official digital assets from **Communications & Planning**, Executive and Intergovernmental Affairs, Government of Nunavut — Tel: (867) 979-5822
2. Place files in an `images/` folder in the repository
3. In `index.html`, find the `header-logo` div and replace the SVG placeholder:

```html
<div class="header-logo">
  <img src="images/gn-symbol-wordmark.png"
       alt="Government of Nunavut"
       style="height: 46px; width: auto;" />
</div>
```

**Note:** The individual portals use their own colour schemes and typography (IBM Plex Sans, DM Sans, Lora, etc.) for their internal UI. The GN Visual Identity Standards are applied to the **landing page** which serves as the official public-facing entry point.

---

## Architecture

- **No build step** — all files are plain HTML with inline CSS and JavaScript
- **React 18 via CDN** — portals use React loaded from cdnjs.cloudflare.com, compiled in-browser by Babel
- **Supabase backend** — portals connect to Supabase for authentication, data storage, and RPC calls (with demo mode fallback)
- **Iframe embedding** — the landing page loads portals in iframes for isolation; each portal retains its own styling and state
- **Lazy loading** — portal iframes are only loaded when first opened (not on initial page load)

---

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Hosting | GitHub Pages (static) |
| Frontend | HTML, CSS, vanilla JavaScript |
| Portal UI | React 18 + Babel (CDN, no build) |
| Backend | Supabase (PostgreSQL, Auth, Storage) |
| Fonts | Arial (landing page), IBM Plex Sans / DM Sans / Lora (portals) |

---

## Key Contacts

| Role | Email |
|------|-------|
| General Inquiries | fisheries@gov.nu.ca |
| Seal & Fur Programs | sealandfur@gov.nu.ca |
| RV Nuliajuk | nuliajuk@gov.nu.ca |

**Department of Community Services**
Fisheries & Sealing Division
P.O. Box 1000, Iqaluit, NU X0A 0H0

---

## License

© 2026 Government of Nunavut. All rights reserved.

The Government of Nunavut Symbol and Wordmark are protected under international copyright law and cannot be used without permission.

