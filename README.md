# DevPulse – Cloud Telemetry Landing Page

Assignment 1B for CSI 3150F26. A responsive marketing landing page and cluster pricing dashboard for **DevPulse**, a fictional cloud telemetry SaaS. Built from the user journey and component hierarchy designed in Assignment 1A.

Built with **HTML5 and CSS3 only**: no frameworks and no JavaScript.

## How to run

Clone the repo and open `index.html` in any modern browser.

```bash
git clone <this-repo-url>
cd devpulse-dashboard
open index.html   # or double-click the file
```

## File structure

```
devpulse-dashboard/
├── index.html   # semantic markup
├── styles.css   # all styling
└── README.md
```

## User journey (from 1A)

1. Land on the hero and see the "Deploy Free Cluster" call to action.
2. Click **Pricing** in the nav to compare Developer, Pro Cluster, and Enterprise Dedicated.
3. Enter node count and log throughput in the **Workload Estimator**.
4. Fill in the **API Sandbox Registration** form and submit.
5. The browser either shows a native validation message or reveals a confirmation message.

## Implementation notes

**Semantic HTML**
- Landmarks: `header`, `nav`, `main`, `section`, `article`, `footer`. No root-level `div` wrappers.
- Heading order is `h1` → `h2` → `h3` with no skipped levels.

**Native form constraints**
- Every input has a `<label for>` matched to its `id`.
- Workload estimator: `type="number"`, `min="1"`, `max="1000"`, `step="1"`, `required`.
- Registration: `type="email"` and `required` on email and company name.
- Invalid input is blocked by the browser. On a valid registration, the form navigates to `#registration-confirmed` and the CSS `:target` selector shows the confirmation message.

**CSS architecture**
- Universal `border-box` reset at the top of the stylesheet.
- Design tokens in `:root` for colors, font stack, radius, and transition timing.
- Flexbox (1D): header, nav, hero, CTA group, forms, footer.
- CSS Grid (2D): features grid and pricing grid using `repeat(auto-fit, minmax(...))`.
- Norman signifiers: the Pro Cluster card is scaled up with a colored border and a "Most popular" tag; buttons, links, and inputs have `:hover` and `:focus-visible` states; invalid inputs get a red border via `:user-invalid`.
- Responsive reflow at `max-width: 768px`: header stacks, grids collapse to one column, buttons go full width.
- `prefers-reduced-motion` turns off transitions and smooth scrolling.

## Norman principles mapping

| Principle | Component | Element |
|---|---|---|
| Signifier | Primary CTA above the fold | `<a href="#register" class="btn btn-primary">` |
| Signifier | Recommended tier | `<div class="popular-tag">Most popular</div>` |
| Constraint | Node count | `<input type="number" min="1" max="1000" step="1" required>` |
| Constraint | Work email | `<input type="email" required>` |
| Feedback | Anchors and form submit | Scroll to linked section; native validation; `:target` confirmation |
