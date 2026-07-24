# MIAM / MMIA Dashboard

**Mechanical Inspectors Association of Michigan (MIAM)**
**Metropolitan Mechanical Inspectors Association (MMIA)**

Live site: [mechanicalinspector.com](https://www.mechanicalinspector.com)
GitHub Pages dashboard: [miam-mmia.github.io/Dashboard](https://miam-mmia.github.io/Dashboard/)

---

## Overview

The dashboard is a fully mobile-responsive standalone HTML page (`index.html`) hosted on GitHub Pages and embedded on the mechanicalinspector.com home page via an iframe in a Weebly Embed Code element. It provides the primary navigation hub, event listings, member tools, and a job-availability submission form for Michigan Mechanical Inspectors, Building Officials, Code Officials, and Mechanical Contractors.

A companion embed (`webinars-header.html`) powers the top of the Webinars page with a step-by-step guide, credit breakdown, answer sheet reference, and course listing.

---

## File Inventory

| File | Purpose |
|---|---|
| `index.html` | Main dashboard — hosted on GitHub Pages, embedded on mechanicalinspector.com via iframe |
| `about-miam-mmia.html` | About page linked from the dashboard Learn More button |
| `webinars-header.html` | Webinar page header embed (pasted into Weebly Embed Code element) |
| `miam-post-availability-form.pdf` | Printable version of the Post Your Availability modal form |
| `README.md` | This file |

---

## Deployment Architecture

### Home Page Dashboard
`index.html` is hosted on GitHub Pages at `miam-mmia.github.io/Dashboard/` and displayed on mechanicalinspector.com via the following Weebly Embed Code element:

```html
<style>
.miam-frame-wrap {
    width: 100%;
    margin: 0;
    padding: 0;
}
.miam-frame-wrap iframe {
    width: 100%;
    height: 1200px;
    border: none;
    display: block;
}
@media (max-width: 768px) {
    .miam-frame-wrap iframe {
        height: 4200px;
    }
}
</style>

<div class="miam-frame-wrap">
    <iframe
        src="https://miam-mmia.github.io/Dashboard/"
        title="MIAM / MMIA Member Dashboard"
        loading="lazy"
        scrolling="no">
    </iframe>
</div>
```

Any changes committed to `index.html` appear on mechanicalinspector.com within 1–2 minutes after GitHub Pages rebuilds.

### Webinar Page Header
`webinars-header.html` is pasted directly into a Weebly Embed Code element at the top of the Webinars page. Unlike `index.html`, this file is not hosted on GitHub Pages — it lives only in the Weebly editor.

---

## Updating the Dashboard

> **Always upload files via Add file → Upload files (drag and drop).** Do not use the GitHub in-browser text editor for large files — pastes may save incorrectly or truncate silently.

1. Edit `index.html` locally
2. Go to **github.com/MIAM-MMIA/Dashboard**
3. Click **Add file → Upload files**
4. Drag the updated `index.html` onto the upload area
5. Click **Commit changes**
6. GitHub Pages rebuilds in ~1–2 minutes

### GitHub Pages Settings
Go to the repository **Settings tab → Pages** (not account settings):
- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/ (root)**

---

## Dashboard Content (`index.html`)

### Site Header
Navigation bar linking back to key mechanicalinspector.com pages (hidden on mobile).

### Hero Banner
- Welcome message with MIAM / MMIA logo
- **Pay Dues** → `mechanicalinspector.com/membership--dues.html`
- **View Webinars** → `mechanicalinspector.com/webinars.html`

### Top Row Cards

**Upcoming Training & Events** (wider card)
Lists current and upcoming classes with date badges and Register buttons, plus the on-demand webinar series entry.

**Member Quick Links**
- Become an Inspector
- MIAM & MMIA Class Listing
- Certificates
- MMIA Officers → `/officers.html`
- MIAM Officers → `/officers1.html`
- Members → `/members.html`
- Contact Us

**Code / LARA Updates**
- 2021 Mechanical Code
- 2021 Michigan Building Code
- 2024 Residential Code
- Re-Registration Requirements
- BCC Resources

### Bottom Row Cards

**Sponsors** — Sponsor listing and sponsorship appeal pages for MIAM and MMIA

**Looking for Work** — Job board link and Post Your Resume modal

**About MIAM / MMIA** — Organization description with Learn More link to `about-miam-mmia.html`

---

## Post Your Availability Modal

Triggered by the **Post Your Resume** button. Collects member availability information and sends it via `mailto:` to `s_schippert@yahoo.com`.

### Form Sections
- **Contact Information** — Name, email, phone
- **Type of Work Sought** — Employment type, inspection disciplines (checkboxes), other description
- **Qualifications & Certifications** — LARA license levels (checkboxes), license numbers, years experience, additional notes
- **Geographic Availability** — Primary area, travel range, geographic notes

### Submission
Validates required fields and email format, then opens a pre-populated `mailto:` to `s_schippert@yahoo.com` with subject `Member Availability: [Name] - [Employment Type]` and a plain-text body containing all form data.

---

## Webinar Page Header (`webinars-header.html`)

Placed at the top of the Webinars page above existing Weebly content.

### Hero Band
- Series: 2024–2027 On-Demand For-Credit Webinars
- Registration fee: $200 (dues-paid members)
- Total credits: 47 (18 Technical, 9 Plan Review, 10 Specialty, 10 Acts & Rules)

### Four-Step Action Cards
| Step | Action | Destination |
|---|---|---|
| 1 | Pay Here | Square payment link |
| 2 | Watch the Video(s) | Webinars page listing |
| 3 | Complete Quiz(zes) | Answer sheet PDF download |
| 4 | Email Sue Schippert | `s_schippert@yahoo.com` |

### Answer Sheet Panel
Collapsible panel listing all 19 approved courses grouped by LARA expiration date (2026 / 2027 / 2028), with CP numbers, course names, credit types, and eligible inspector categories.

### Secondary Navigation
Links to Info-Only Webinars and the 2021–2024 Cycle Info-Only Webinars.

---

## Technical Notes

### Why GitHub Pages Instead of Weebly Embed
The original dashboard was a Weebly Embed Code element (`weebly-embed.html`). Weebly's mobile theme constrains embed container heights, causing cards to collapse and become invisible on mobile devices. No CSS override resolved this. Moving to a GitHub Pages hosted page embedded via iframe solves the problem — the dashboard renders correctly on all screen sizes.

### CSS Architecture (`index.html`)
- No external dependencies — all styles are inline
- Card layout uses CSS Flexbox with `flex-direction: column` on mobile (≤ 860px)
- `overflow: visible` on `.card` is required — `overflow: hidden` clips card content on mobile
- Card headers use `border-radius` directly to preserve rounded corners without overflow clipping
- Iframe height is fixed: **1200px desktop / 4200px mobile** — increase if content grows

### Special Characters (`webinars-header.html`)
All special characters use HTML entities (`&amp;`, `&ndash;`, `&mdash;`, `&rsaquo;`) throughout. Raw UTF-8 characters must not be used — Weebly's editor can corrupt non-ASCII bytes on save. This requirement applies to `webinars-header.html` only; `index.html` is served by GitHub Pages where encoding is not an issue.

### Responsive Breakpoints (`index.html`)
- `≤ 860px` — card rows collapse to single column; site nav hidden
- `≤ 600px` — hero banner stacks vertically; action buttons full-width
- `≤ 480px` — reduced padding; event items reflow to two columns

---

## Key Contacts

| Role | Contact |
|---|---|
| Jobs / Availability Coordinator | s_schippert@yahoo.com |

---

## Update Checklist

When maintaining the dashboard, update the following as needed:

- **Upcoming events** — dates, titles, locations, credit counts, and registration links in `index.html`
- **Hero buttons** — Pay Dues and View Webinars URLs
- **Member Quick Links** — add or remove links as pages change
- **Webinar credit totals** — the "47 Total Credits" stat and credit-type tags in `webinars-header.html`
- **Answer sheet courses** — add new CP numbers to the collapsible panel; update expiration-date groups
- **Answer sheet PDF** — re-upload revised PDF to Weebly; update href if filename changes
- **Sponsor listings** — update sponsor links seasonally
- **Iframe height** — increase desktop (1200px) or mobile (4200px) values in the Weebly embed if content grows
