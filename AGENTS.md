# AGENTS.md

## Project Mission
Build a single-page, high-converting lead-generation site for a MedSpa automation agency.

- **Primary objective:** pre-qualify visitors with an ROI calculator, then drive them to book via Calendly.
- **Audience:** MedSpa owners overwhelmed by manual booking/admin workflows.
- **Core promise:** automation fills calendars, reduces no-shows, and lowers front-desk overhead.

## Required Deliverable
- One production-ready file: **`index.html`**
- No build tools, no framework, no backend.
- Everything inline (HTML, CSS, JS) except approved CDNs.

## Allowed Stack
- HTML5
- Tailwind CSS via CDN
- Vanilla JavaScript only
- CountUp.js via CDN
- Google Fonts
- Lucide Icons via CDN

## Design Direction: Clinical Futurism
Use these tokens consistently:

```css
--bg-primary:    #0A0F14;
--bg-card:       rgba(255,255,255,0.04);
--accent-teal:   #00C9B8;
--accent-rose:   #E8A598;
--text-primary:  #F0EDE8;
--text-muted:    #8A8F96;
--border-glass:  rgba(255,255,255,0.08);
```

- Fonts:
  - Headings/display: `Playfair Display`
  - Body/UI: `DM Sans`
- Visual style: glassmorphism cards, subtle grain texture, no stock photos.
- Prefer SVG line art and restrained motion.

## Page Structure (must follow this order)
1. Navbar
2. Hero
3. Trust strip
4. ROI calculator (`#calculator`)
5. Client portal mockup (must be before pricing)
6. Services tabs (`#services`)
7. Pricing (`#pricing`)
8. Booking/Calendly (`#calendly`)
9. Smart intake modal
10. Footer

## Non-Negotiable Behaviors
1. **Navbar scroll effect:** add blur/opacity class after `window.scrollY > 60`.
2. **ROI calculator two-phase effect:**
   - Phase 1: red dramatic CountUp (`Annual Revenue Walking Out the Door`)
   - Phase 2: teal recovery crossfade (`Recoverable With Automation`)
   - Trigger on first slider interaction.
   - Save loss value to `window.calculatedLoss`.
3. **Scroll reveal animation:** use `IntersectionObserver` for sections/cards/progress fill.
4. **Service tabs:** pure JS switcher; active tab gets teal emphasis.
5. **Modal UX:** open from pricing CTAs, close on overlay/Escape, trap focus while open.
6. **Calendly lazy load:** inject Calendly script only when `#calendly` enters viewport.

## Calculator Formula (required)
```js
const avgBookingValue = 120;
const noShowLoss = (bookings * (noShowRate / 100)) * avgBookingValue * 12;
const adminLoss = adminHours * 52 * 25;
const totalLoss = noShowLoss + adminLoss;
window.calculatedLoss = totalLoss;
```

## Required Copy Anchors (exact strings)
Do not alter these:

- `Your MedSpa. Running Itself.`
- `Stop Buying Software. Start Building Systems.`
- `1 system replaces 3 staff hours per day`
- `Built in 14 days. Runs for years.`
- `Your front desk doesn't sleep. Neither does ours.`
- `3 bookings confirmed while you slept`
- `Trusted by MedSpas in TX · FL · CA`
- `Avg. setup time: 11 days`

## Conversion-Critical Details
- Hero includes a floating proof notification card.
- Trust strip is simple text-first social proof with inline Lucide icons.
- Client portal mockup must show 14-day sprint progress and animated 42% progress bar.
- Pricing has two cards:
  - Quick Win: `$1,497`
  - Full MedSpa OS (featured): `$3,997`
- Pricing CTAs open the intake modal.
- Calendly section micro-copy should personalize from `window.calculatedLoss` when available.

## Intake Modal Requirements
Fields:
1. Name
2. MedSpa name
3. Needed system (Booking / Retention / Front Desk)
4. Loom URL (optional)
5. Submit CTA

Loom URL validation must only accept:
- `https://loom.com/...`
- `https://www.loom.com/...`

Show inline rose-accent error for invalid Loom URLs.

## Quality Bar / Definition of Done
- Opens directly in browser with no server.
- Fully responsive, with special care for mobile services-tab layout.
- All interactions functional without console errors.
- Strong visual hierarchy and premium aesthetic.
- No missing sections, no placeholder TODO text, no broken anchors.

## Agent Working Notes
- Keep implementation self-contained and maintainable in one file.
- Use semantic HTML and accessible labels/controls.
- Minimize JS complexity while preserving all required effects.
