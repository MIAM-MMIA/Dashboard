# MIAM / MMIA Dashboard

**Mechanical Inspectors Association of Michigan (MIAM)**
**Metropolitan Mechanical Inspectors Association (MMIA)**

Live site: [mechanicalinspector.com](https://www.mechanicalinspector.com)
GitHub Pages mirror: [miam-mmia.github.io/Dashboard](https://miam-mmia.github.io/Dashboard/)

---

## Overview

The dashboard is a single self-contained HTML embed (`weebly-embed.html`) that powers the home page of mechanicalinspector.com. It is pasted into a Weebly **Embed Code** element and provides the primary navigation hub, event listings, member tools, and a job-availability submission form for Michigan Mechanical Inspectors, Building Officials, Code Officials, and Mechanical Contractors.

A companion embed (`webinars-header.html`) powers the top of the Webinars page with a step-by-step guide, credit breakdown, answer sheet reference, and course listing.

---

## File Inventory

| File | Purpose |
|---|---|
| `weebly-embed.html` | Main dashboard — home page embed |
| `webinars-header.html` | Webinar page header embed |
| `miam-post-availability-form.pdf` | Printable version of the Post Your Availability modal form |
| `README.md` | This file |

---

## Dashboard Cards (`weebly-embed.html`)

### Hero Banner
Welcomes visitors and provides three primary action buttons:
- **Pay Dues** → `mechanicalinspector.com/membership--dues.html`
- **Register for Next Class** → `mechanicalinspector.com/061826.html`
- **View Webinars** → `mechanicalinspector.com/webinars.html`

### Upcoming Training & Events
Lists the next two scheduled events plus the on-demand webinar series:
- A2L Refrigerants — June 18, 2026, Behler-Young Training Center, Troy
- 2026 MIAM Fall Conference — October 29–30, 2026
- 2024–2027 Webinar Series — 47 on-demand credits

### Member Quick Links
- Become an Inspector
- MIAM & MMIA Class Listing
- Certificates
- Contact Us

### Code / LARA Updates
Links to current adopted Michigan codes and LARA resources:
- 2021 Mechanical Code
- 2021 Michigan Building Code
- 2024 Residential Code
- Re-Registration Requirements
- BCC Resources

### Sponsors
Links to the sponsor listing page and sponsorship appeal pages for MIAM and MMIA.

### Looking for Work
Two actions for Mechanical Inspectors seeking employment:
- **View Job Board** → `mechanicalinspector.com/job-openings.html`
- **Post Your Resume** → opens the Post Your Availability modal (see below)

### About MIAM / MMIA
Brief description of both organizations with a link to the full About page on GitHub Pages.

---

## Post Your Availability Modal

Triggered by the **Post Your Resume** button in the Looking for Work card. Collects member availability information and sends it via `mailto:` to `s_schippert@yahoo.com`.

### Form Sections

**Contact Information**
- First Name * / Last Name *
- Email Address * / Phone Number

**Type of Work Sought**
- Employment Type * (Full-Time, Part-Time, Contract / Per Diem, Temporary / Seasonal, Open to Any)
- Inspection Discipline(s) — checkboxes: Mechanical, Plumbing, Electrical, Building / Structural, HVAC, Fire Suppression, Plans Review, Other
- Other / Additional Work Description

**Qualifications & Certifications**
Grouped checkbox tree:
- Building Official
- Inspector: Building, Electrical, Mechanical, Plumbing, Fire Protection System
- Plan Reviewer: Building, Electrical, Mechanical, Plumbing, Fire Protection System
- License / Certificate Number(s)
- Years of Experience (Less than 1 / 1–3 / 4–7 / 8–15 / 15+)
- Additional Qualifications / Notes

**Geographic Availability**
- Primary City / County / Region *
- Willing to Travel (Local only / Regional / Statewide / Multi-state)
- Geographic Notes

### Submission
On submit the form validates required fields and email format, then opens a pre-populated `mailto:` to `s_schippert@yahoo.com` with subject line `Member Availability: [Name] - [Employment Type]` and a plain-text body containing all form data.

### Printable Version
`miam-post-availability-form.pdf` is a print-ready version of the same form for members who prefer to fill it out by hand and email a scan.

---

## Webinar Page Header (`webinars-header.html`)

Placed at the top of the Webinars page above existing content.

### Hero Band
- Series: 2024–2027 On-Demand For-Credit Webinars
- Registration fee: $200 (one-time, dues-paid members)
- Total credits: 47 (18 Technical, 9 Plan Review, 10 Specialty, 10 Acts & Rules)

### Four-Step Action Cards
| Step | Action | Destination |
|---|---|---|
| 1 | Pay & Register | Square payment link |
| 2 | Watch on YouTube | Webinars page listing |
| 3 | Print Answer Sheet | Answer sheet PDF (Weebly uploads) |
| 4 | Email Completed Answer Sheet | `s_schippert@yahoo.com` |

### Answer Sheet Panel
Collapsible panel listing all 19 approved courses grouped by LARA expiration date (September 16, 2026 / 2027 / 2028), with CP numbers, course names, credit types, and eligible inspector categories. Includes a direct download button for the answer sheet PDF.

### Secondary Navigation
Links to Info-Only Webinars and the 2021–2024 Cycle Info-Only Webinars.

---

## Deployment

### Weebly
1. Log in to Weebly and open the page editor.
2. Drag an **Embed Code** element to the desired position.
3. Click **Edit Custom HTML** and paste the entire contents of the relevant file.
4. Do **not** paste `weebly-embed.html` inside a full HTML page wrapper — Weebly provides its own `<html>`, `<head>`, and `<body>` tags. Pasting a full document will cause garbled output.
5. Publish the page.

### GitHub Pages
The `/Dashboard/` repository on `miam-mmia.github.io` hosts standalone versions of pages (e.g. the About page) that are linked to from the Weebly site.

---

## Technical Notes

### CSS Isolation
All styles in `weebly-embed.html` are scoped under `#miam-dash` to prevent conflicts with Weebly's own stylesheet. Modal styles use `#md-resume-modal` and `#md-resume-overlay` prefixes.

### Special Characters
All special characters use HTML entities (e.g. `&amp;`, `&ndash;`, `&mdash;`, `&rsaquo;`) throughout both embed files. Raw UTF-8 characters must not be used — Weebly's editor can corrupt non-ASCII bytes on save.

### Modal Positioning
The Post Your Availability overlay uses `top: 70px` to clear the Weebly navigation bar, which sits fixed at the top of the viewport. If the nav bar height changes, adjust this value in the `#md-resume-overlay` CSS rule.

### Responsive Breakpoints
- `≤ 860px` — dashboard grid collapses to a single column
- `≤ 600px` — hero banner stacks vertically
- `≤ 500px` — hero padding reduced; action buttons go full-width

---

## Key Contacts

| Role | Contact |
|---|---|
| Jobs / Availability Coordinator | s_schippert@yahoo.com |
| Association Office | (248) 649-5443 |
| Mailing Address | 560 Barrington Road, Grosse Pointe Park, MI 48230 |
| Website | mechanicalinspector.com |

---

## Update Checklist

When maintaining the dashboard, update the following items as needed:

- **Upcoming events** — event dates, titles, locations, credit counts, and registration links in the Upcoming Training card
- **Next Class button** — URL in the hero banner Register for Next Class button (`/061826.html` format — update to new date slug)
- **Webinar credit totals** — the "47 Total Credits" stat and the four credit-type tags in `webinars-header.html`
- **Answer sheet courses** — add new CP numbers to the collapsible panel and update expiration-date groups
- **Answer sheet PDF** — re-upload revised PDF to Weebly at the same path, or update the href if the filename changes
- **Sponsor listings** — update sponsor links and appeal pages seasonally
