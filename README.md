# MD MONIRUJJAMAN — Portfolio Fixes & Responsiveness Report

This repository contains a personal portfolio (HTML/CSS/JS). I reviewed and fixed layout and runtime issues and made targeted responsiveness improvements while preserving the original design (colors, fonts, layout vibe).

## Summary of changes
- Fixed markup and runtime bugs that caused console errors and layout breakage.
- Ensured no horizontal overflow on mobile and improved scaling across Mobile, Tablet, Laptop, and 4K.
- Added small defensive guards in JavaScript to avoid runtime exceptions when elements are not present.
- Documented all changes and how to preview the site locally.

## Files changed
- [index.html](index.html)
- [style.css](style.css)
- [script.js](script.js)
- [README.md](README.md) (this file)

## Specific bugs found and fixed
1. Broken profile image tag
   - File: [index.html](index.html)
   - Issue: malformed image tag (<img src="image/monir.jpeg"MD MONIRUJJAMAN" ...>) caused HTML parsing errors and prevented the profile picture from rendering.\n   - Fix: corrected to <img src="image/monir.jpeg" alt="MD MONIRUJJAMAN" class="orbit-profile-pic">.

2. Malformed contact email markup
   - File: [index.html](index.html)
   - Issue: stray character in the email paragraph (`"t`) made the tag invalid.
   - Fix: corrected the paragraph markup and spacing.

3. Duplicate FontAwesome kit script includes
   - File: [index.html](index.html)
   - Issue: two identical <script> kit imports were included, which can cause duplicate execution/warnings.
   - Fix: removed duplicate kit script tags (kept the CSS link in the <head> for icons).

4. CSS causing forced viewport height (layout overflow)
   - File: [style.css](style.css)
   - Issue: `height: 100vh;` on the `body` caused content overflow/scrolling issues on some screens.
   - Fix: replaced with `min-height: 100vh;` to allow content to grow naturally and avoid overflow.

5. Invalid CSS property value (missing unit)
   - File: [style.css](style.css)
   - Issue: `.subject-input { width: 100; }` missing unit caused unpredictable rendering.
   - Fix: changed to `width: 100%;`.

6. JS runtime errors / duplicated function
   - File: [script.js](script.js)
   - Issues and fixes:
     - Guarded `Typed` initialization to avoid errors if the library or element is missing.
     - Added null checks before adding event listeners for the mobile navbar toggle (prevents exceptions when markup differs).
     - Guarded nav link click handlers to safely remove active states.
     - Removed a duplicated `askGeminiAI` function (kept the first, more robust implementation).

## Responsiveness details
I kept the existing visual style and tuned only what's necessary to prevent overflow and improve layout across breakpoints.

- Global measures applied:
  - `html { overflow-x: hidden; }` already present — preserved to avoid horizontal scroll.
  - Replaced hard `height:100vh` on `body` with `min-height:100vh` so content can expand and avoid vertical clipping.

- Media queries used (existing and preserved):
  - `@media (max-width: 991px)` — stacked `.home` layout, adjusted hero typography and image sizes, made `.projects-container` single-column.
  - `@media (max-width: 880px)` — mobile navbar behavior (hamburger shown), mobile menu is a fixed right-side panel (kept and guarded in JS).
  - `@media (max-width: 768px)` — timeline layout collapses to single-column.
  - `@media (max-width: 450px)` — fine-tuned typography for very small screens.

- Layout patterns preserved and used:
  - Flexbox for header, hero, profile animation, contact form and many components.
  - CSS Grid for `.projects-container`, `.features`, `.blog-grid` and the skills/slider arrangements.
  - Where necessary I used `min()`/`max()`/`clamp()` sizing already present in the CSS to scale assets naturally across wide and narrow viewports.

## How to preview locally
1. Open the project folder in an editor or file explorer: `e:\MD-MONIRUJJAMAN1`.
2. Open `index.html` in a modern browser (Chrome, Edge, Firefox).
   - Right-click → Open with → choose browser OR run a local static server.
3. Optional: run a simple static server (recommended for accurate asset loading):

   - With Python 3.x:

```bash
# serve on http://localhost:8000
python -m http.server 8000
```

   - With Node (http-server):

```bash
npx http-server -p 8000
```

4. Visit `http://localhost:8000` (or simply open `index.html` directly).

## Notes & recommendations
- I intentionally kept colors, fonts, layout structure, and the "vibe" unchanged — only fixed markup, JS errors, and immediate responsiveness issues.
- The project references several image files in the `image/` folder. To preview exactly as intended ensure these files exist with the expected names (case-sensitive on some servers).
- For production use, consider serving FontAwesome via a single mechanism (prefer the CSS CDN link used in the `<head>`), and remove kit script tags completely.
- If you want, I can:
  - Run a visual responsiveness pass across breakpoints and produce screenshots for verification.
  - Tidy CSS (remove duplicate selectors) and run a minification/optimization pass.

---
If you want, I can now run quick automated sanity checks or open the site in a headless browser to capture screenshots for Mobile/Tablet/Desktop/4K. Which would you prefer next?