# 🏥 Tech.Care — Patient Dashboard

A pixel-faithful front-end build of a healthcare "Patients" dashboard, converted from an Adobe XD design into responsive, framework-free HTML/CSS/JS and wired up to a live REST API.

**🔗 Live demo:** _add your GitHub Pages link here after deploying, e.g. `https://YOUR_USERNAME.github.io/techcare-patient-dashboard/`_

![Tech.Care dashboard preview](preview.png)

---

## ✨ What this project demonstrates

This was built as a front-end skills exercise, converting a static Adobe XD design into a fully working, data-driven interface:

- **Pixel-level fidelity to design** — spacing, radii, colors, and typography matched directly against the Adobe XD inspector (exact hex values, border-radius, and layout dimensions pulled straight from the design file).
- **Live API integration** — patient data (vitals, diagnosis history, lab results, diagnostics) is fetched at runtime from a REST endpoint using HTTP Basic Auth, not hardcoded.
- **A real chart, not a mockup** — the blood pressure graph is rendered with [Chart.js](https://www.chartjs.org/), with a working time-range selector (3 / 6 / 12 months / all time) that reflows the chart from the same dataset.
- **Fully responsive** — one codebase adapts from a 3-column desktop layout down to a single scrollable column on mobile, with a collapsible nav menu.
- **No frameworks, no build step** — a single `index.html` file: vanilla JS, hand-written CSS with custom properties, zero dependencies beyond the Chart.js CDN script. Open it and it just works.
- **Interactive details beyond the static mock** — patient search/filter, a "Show All Information" modal, and a clickable lab-results list, all built to feel like natural extensions of the original design rather than bolted-on features.

## 🖥️ Tech stack

| Layer | Choice |
|---|---|
| Markup / Styling | Semantic HTML5 + hand-written CSS (custom properties, Flexbox/Grid) |
| Charting | [Chart.js v4](https://www.chartjs.org/) |
| Data | [Coalition Technologies Patient Data API](https://fedskillstest.coalitiontechnologies.workers.dev) (fetched client-side) |
| Fonts | [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts |
| Build tooling | None — it's a static file. Open it in a browser or serve it from any static host. |

## 📁 Project structure

```
techcare-patient-dashboard/
├── index.html      # everything: markup, styles, and JS in one file
└── README.md
```

## 🚀 Running it locally

Because the page calls a remote API with `fetch()`, most browsers are happiest serving it over `http://` rather than opening the file directly (`file://`) to avoid CORS quirks. Any static server works:

```bash
# clone the repo
git clone https://github.com/YOUR_USERNAME/techcare-patient-dashboard.git
cd techcare-patient-dashboard

# serve it (pick whichever you have installed)
python3 -m http.server 5500
# or
npx serve .
```

Then open `http://localhost:5500` in your browser.

## 🔌 API

Patient records are fetched from:

```
GET https://fedskillstest.coalitiontechnologies.workers.dev
Authorization: Basic <base64("coalition:skills-test")>
```

The response drives every dynamic part of the page: the patient list, profile card, blood pressure chart, vitals cards, diagnostic list, and lab results — nothing patient-specific is hardcoded.

## 📱 Responsive behavior

| Breakpoint | Behavior |
|---|---|
| `> 1280px` | Full 3-column layout matching the original design |
| `≤ 1280px` | Columns narrow proportionally |
| `≤ 1100px` | Layout stacks into a single scrollable column; top nav collapses into a hamburger menu |
| `≤ 860px` | Profile/Lab Results panels stack vertically; vitals cards go full-width |
| `≤ 480px` | Compact header, tightened spacing for small phones |

## 🎨 Design source

Built from an Adobe XD prototype ("2026 FED API Skills Test — HealthCare Dashboard"). Colors, corner radii, and spacing were cross-checked against the XD inspector panel to keep the implementation faithful to the original design rather than approximated by eye.

## 📄 License

MIT — see [LICENSE](LICENSE).
