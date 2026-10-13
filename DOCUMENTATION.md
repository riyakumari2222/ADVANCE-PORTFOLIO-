# Advanced Portfolio Website — Technical Documentation

**Project:** Personal portfolio website for Riya Kumari  
**Category:** Frontend web development  
**Technologies:** HTML5, CSS3, vanilla JavaScript  
**Frameworks:** None  
**Status:** Frontend implementation; manual browser testing and deployment must be completed before claiming final verification.

---

## 1. Project Overview

### 1.1 Purpose

The goal of this project is to create a modern, responsive, accessible portfolio that presents Riya Kumari's education, technical skills, personal projects, and contact information. It also serves as a practical demonstration of advanced CSS techniques, including CSS Grid, Flexbox, custom properties, animations, responsive breakpoints, advanced selectors, and BEM naming.

### 1.2 Objectives

- Present personal and academic information in a clear visual hierarchy.
- Demonstrate responsive layouts across mobile, tablet, and desktop screens.
- Organize CSS into maintainable files with separate responsibilities.
- Provide a working light/dark theme switcher with preference persistence.
- Validate contact form fields accessibly in the browser.
- Avoid unnecessary dependencies and avoid claiming backend functionality that is not implemented.
- Make it straightforward to personalize, run locally, test, and publish through GitHub Pages.

### 1.3 Scope and limitations

This is a static frontend project. The contact form validates fields and displays a status message but does not send email or store submissions. Project repository and demo URLs should be added only when real URLs exist. The profile illustration is an editable placeholder; a real photo can be added using the instructions in `images/README.md`.

---

## 2. Features

1. Sticky navigation with active-section indication.
2. Hero section with introduction, calls to action, and CSS-built profile card.
3. About section with short profile and learning priorities.
4. Skill groups for programming, frontend development, databases, and cybersecurity fundamentals.
5. Responsive project gallery for four projects.
6. Education timeline.
7. Accessible contact form with client-side validation.
8. Light/dark theme switching and local-storage persistence.
9. Mobile navigation menu.
10. Scroll-aware active navigation links using `IntersectionObserver`.
11. Responsive layout, hover states, keyboard focus styles, and reduced-motion support.
12. Footer with social placeholders and back-to-top link.

---

## 3. Setup Instructions

### Requirements

- A current web browser such as Chrome, Firefox, Edge, or Safari.
- Visual Studio Code (recommended).
- The Live Server extension for VS Code (recommended).
- Git and a GitHub account if version control and deployment are required.

### Install and run

1. Download `advanced-portfolio.zip`.
2. Extract it to a convenient folder.
3. Open Visual Studio Code.
4. Select **File → Open Folder** and choose the extracted `advanced-portfolio` folder.
5. Install the **Live Server** extension if it is not already installed.
6. In the Explorer panel, right-click `index.html`.
7. Choose **Open with Live Server**.
8. The site should open in the default browser. Save a file in VS Code to see changes reload in the browser.

No `npm install`, compilation, or build command is needed because the project uses plain HTML, CSS, and JavaScript.

### Configuration and personalization

1. In `index.html`, replace `your.email@example.com` with the correct public contact email.
2. Replace generic LinkedIn and GitHub destinations with the owner's profile URLs.
3. Confirm the official degree title, institution, and dates before submission.
4. Add a profile image if desired; see `images/README.md`.
5. Add project repository and live-demo URLs only after those resources exist.
6. Keep all asset paths relative so GitHub Pages can serve the project from the repository root.

---

## 4. Code Structure

```text
advanced-portfolio/
├── index.html
├── css/
│   ├── main.css
│   ├── layout.css
│   └── animations.css
├── js/
│   └── theme-switcher.js
├── images/
│   └── README.md
├── screenshots/
│   └── README.md
└── README.md
```

| File | Responsibility |
|---|---|
| `index.html` | Semantic page structure, navigation, content sections, form fields, and stylesheet/script references |
| `css/main.css` | Design tokens, typography, colors, reusable components, cards, form styling, and theme variables |
| `css/layout.css` | Grid areas, Flexbox/layout behavior, fluid grids, and responsive breakpoints |
| `css/animations.css` | Keyframes, entrance effects, floating and glow effects, hover/focus states, and reduced-motion overrides |
| `js/theme-switcher.js` | Theme persistence, mobile menu, active-section navigation, current year, and form validation |
| `images/README.md` | Guidance for adding optimized profile and project images |
| `screenshots/README.md` | Recommended screenshot names and capture guidance |
| `README.md` | Project summary, setup, GitHub Pages deployment, and checklist |

### Architecture

The project follows a simple static-site architecture:

1. **Content layer:** `index.html` provides semantic structure and content.
2. **Presentation layer:** CSS files style the page and adapt it to viewport sizes and themes.
3. **Interaction layer:** `theme-switcher.js` attaches event listeners and updates theme, navigation, and form status.
4. **Asset/documentation layer:** image and screenshot folders provide instructions for adding visual evidence without requiring assets for the starter version.

There is no framework, bundler, external API, database, or server-side application.

---

## 5. Layout Decisions

### CSS Grid

CSS Grid is used where content is two-dimensional or needs coordinated columns:

- Hero: text content and profile illustration are arranged in two columns on larger screens.
- About and Education: heading and detail/timeline columns align on desktop.
- Contact: contact details and form sit side by side on larger screens.
- Skills and Projects: cards use flexible column counts.

The project gallery uses the pattern:

```css
.projects__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 330px), 1fr));
}
```

`repeat()` creates repeated tracks. `auto-fit` fits as many tracks as the available width allows. `minmax()` gives each card a preferred minimum while allowing it to expand. `min(100%, 330px)` avoids a fixed minimum wider than a very narrow container, helping prevent horizontal overflow.

### Flexbox

Flexbox is used for one-dimensional alignment:

- Navigation items and theme control.
- Button rows and hero metadata.
- Skill/project tags.
- Timeline metadata.
- Contact details and footer links.
- Mobile navigation menu.

Grid manages the larger page/card arrangement; Flexbox manages alignment and wrapping inside components. This separation makes layout behavior easier to reason about.

### Grid areas

Named grid areas (`content`, `visual`, `heading`, `body`, `timeline`, `intro`, and `form`) make major page regions readable and allow mobile breakpoints to reorder regions without changing the document's semantic order.

### Mobile-first responsiveness

The base layout uses flexible widths and fluid typography. Media queries at approximately `760px`, `480px`, and `1000px` adapt navigation, grids, spacing, and type sizes. The exact breakpoints are design choices rather than device guarantees; test around them and adjust if content needs more room.

---

## 6. Advanced CSS Techniques

### 6.1 CSS custom properties and theme tokens

The `:root` block defines reusable colors, typography, spacing, radii, shadows, and transitions. The dark theme overrides the same tokens through `:root[data-theme="dark"]`.

Benefits:
- Consistent design decisions across components.
- Easier global redesign and maintenance.
- Fewer repeated hard-coded values.
- Theme changes without duplicating every component selector.

### 6.2 BEM naming convention

Classes use Block–Element–Modifier naming:

- Block: `.project-card`
- Element: `.project-card__title`
- Modifier: `.button--primary`

This establishes predictable component ownership and reduces naming collisions. Keep new class names consistent with the same convention.

### 6.3 Advanced selectors

Examples used in the stylesheet include:

- `:hover` for interactive hover states.
- `:focus-visible` for keyboard-friendly focus outlines.
- `:active` for a pressed-state response.
- `:nth-child()` for staggered card animation delays and icon color variants.
- `:not()` for selecting links outside a particular component style.
- `:is()` to group related selectors.
- Attribute selectors such as `a[target="_blank"]` and `[aria-invalid="true"]` for behavior/accessibility-related styling.
- `::before` and `::after` for decorative rings, underline effects, and background shapes without extra markup.

Use pseudo-elements for decoration only; important content should remain in HTML.

### 6.4 Transitions and transforms

Buttons and cards use transitions for movement, color, border, and shadow. A small `translateY()` gives hover feedback without changing document flow. The `:active` state gives a subtle pressed response. Avoid excessive motion or large layout shifts.

### 6.5 Keyframe animations

`animations.css` defines:
- `fade-up` for entrance motion.
- `float-gently` for the profile card.
- `glow-drift` for background glow effects.
- `orbit-turn` for decorative rings.

These are visual effects only and do not control application logic.

### 6.6 Reduced-motion accessibility

The `@media (prefers-reduced-motion: reduce)` rule reduces animation and transition durations and disables smooth scrolling for users who prefer less motion. Test this setting through the operating system or browser's accessibility preferences.

### 6.7 Modern CSS features

`clamp()` creates fluid type sizes and spacing, `min()` helps keep grid tracks within their container, `color-mix()` blends theme-aware colors, and `backdrop-filter` adds a translucent header effect where supported. Fallback colors and normal document flow keep the page usable in browsers that do not support every decorative feature.

---

## 7. JavaScript Logic, Algorithms, and Data Structures

### 7.1 Theme selection algorithm

1. Read `riya-portfolio-theme` from `localStorage` inside a `try/catch`.
2. If the saved value is `light` or `dark`, apply it.
3. Otherwise, query `prefers-color-scheme` and use the system preference.
4. Set the `data-theme` attribute on the root HTML element.
5. On a theme-button click, toggle the theme and attempt to save it.
6. If browser storage is blocked, theme switching still works for the current page view.

**Data structures:** Strings represent the theme (`"light"` or `"dark"`); the DOM's `dataset` stores the current theme attribute. No complex data structure is required.

### 7.2 Mobile navigation

The menu button reads its `aria-expanded` value, toggles the menu's `.is-open` class, and updates accessible button text. Clicking a navigation link closes the menu. This keeps the visual state and screen-reader state aligned.

### 7.3 Active-section navigation

An `IntersectionObserver` watches sections inside `main`. When a section intersects the configured viewport region, the script finds its matching navigation link and applies `.navbar__link--active` and `aria-current="location"`.

This avoids repeatedly checking every section's position on every scroll event. A fallback is not essential for the page's content; browsers without `IntersectionObserver` still display all navigation links, though automatic active-link updates will not run.

### 7.4 Contact form validation

The form uses a small object of field configurations. Each field stores:
- Its input element.
- Its error-message element.
- A validation function.

On submit, every field is validated:
- Name: trimmed value must contain at least two characters.
- Email: trimmed value must match a basic email pattern.
- Message: trimmed value must contain at least ten characters.

If any field is invalid, the script displays its error, sets `aria-invalid`, and focuses the first invalid field. If all fields pass, the page displays a message explaining that validation succeeded but no email was sent.

**Data structures and complexity:** The field configuration is a plain JavaScript object, and navigation links/sections are arrays created with spread syntax. For `n` form fields, a submission checks each field once, so validation is O(n) time and O(1) additional working space for this fixed-size form. The observer handles section visibility events rather than running a manual loop continuously.

### Security and privacy note

Client-side validation improves usability but is not a security boundary. If a backend is added, validate and sanitize input on the server, protect secrets, and use an appropriate spam/security strategy. The current project does not transmit form data.

---

## 8. Performance Optimizations

1. **No framework or build pipeline:** avoids shipping a framework runtime for a small static page.
2. **Separate CSS files by responsibility:** makes the project easier to maintain; the browser can cache the files independently.
3. **Small vanilla JavaScript:** no third-party JavaScript dependencies.
4. **CSS-built illustrations:** avoids mandatory large image downloads in the starter version.
5. **Responsive images guidance:** when adding images, prefer WebP/AVIF where suitable, size images for their displayed dimensions, and compress before committing.
6. **Font loading:** Google Fonts are preconnected; system fallback fonts remain specified if the external font service is unavailable. For fully offline or privacy-focused use, remove the Google Fonts links and use local/system fonts.
7. **IntersectionObserver:** section activation is event-driven instead of using continuous scroll-position calculations.
8. **Transform-based hover effects:** transform and opacity are generally preferable to repeatedly changing layout dimensions.
9. **Reduced-motion support:** avoids unnecessary movement for users who request reduced motion.
10. **No unnecessary network requests:** there are no API calls, analytics, or remote image assets in the starter page.

### Performance checks to perform

- Run Chrome DevTools Lighthouse and review Performance, Accessibility, Best Practices, and SEO.
- Inspect the Network tab for unexpected resources or failed requests.
- Check the Console for JavaScript and CSS errors.
- If images are added, inspect file sizes and verify that displayed dimensions are appropriate.
- Measure the published page rather than assuming a score; no Lighthouse score is claimed in this document.

---

## 9. Visual Documentation

Screenshots must show the actual running website. The starter project includes `screenshots/README.md` with capture suggestions but does not include fabricated screenshots.

Recommended evidence:

| Screenshot | What it demonstrates |
|---|---|
| `desktop-home.png` | Hero, navigation, typography, profile-card composition |
| `desktop-projects.png` | Responsive project grid and project-card hierarchy |
| `mobile-home.png` | Compact navigation and mobile hero layout |
| `dark-theme.png` | Dark-theme tokens and readable contrast |
| `contact-validation.png` | Contact form errors or successful local validation status |

### How to capture screenshots

1. Run the site with Live Server.
2. Open Chrome DevTools and toggle the device toolbar for mobile captures.
3. Set browser zoom to 100% and choose a suitable viewport.
4. Capture the visible page using the operating system screenshot shortcut or browser tooling.
5. Save the screenshots in `screenshots/` using the filenames above.
6. Confirm each image reflects the actual current build before committing it.
7. Optionally add the screenshots to this document or the main README using relative Markdown paths, for example `screenshots/desktop-home.png`.

---

## 10. Testing Plan and Evidence

Testing must be performed in a browser before marking a case as passed. The following table provides repeatable test cases.

| ID | Area | Test steps | Expected result |
|---|---|---|---|
| T01 | Initial load | Open `index.html` through Live Server | Page renders; no missing local CSS/JS files |
| T02 | Desktop layout | Test at 1366 × 768 or similar | Hero uses columns; project and skill cards form responsive grids |
| T03 | Tablet layout | Test around 768 px wide | Content adapts without overlapping |
| T04 | Small mobile | Test around 320–375 px wide | No horizontal page overflow; text and controls remain usable |
| T05 | Mobile menu | Resize to mobile; open and close menu; select a link | Menu toggles and closes after navigation |
| T06 | Theme toggle | Click theme button twice | Light and dark themes both apply; accessible label updates |
| T07 | Theme persistence | Choose dark theme and refresh | Dark theme remains selected |
| T08 | System theme | Clear saved theme and reload with OS dark mode enabled | Dark theme is selected on first visit |
| T09 | Form: invalid name | Submit with a blank or one-character name | Name error appears and field is marked invalid |
| T10 | Form: invalid email | Enter an invalid email and submit | Email error appears |
| T11 | Form: short message | Enter fewer than 10 non-space characters | Message error appears |
| T12 | Form: valid values | Enter a valid name/email/message and submit | Local success notice appears; no email is sent |
| T13 | Keyboard access | Use Tab/Shift+Tab and Enter through the page | Focus is visible; links and controls can be reached |
| T14 | Reduced motion | Enable OS reduced-motion setting and reload | Animations/transitions are substantially reduced |
| T15 | External links | Inspect LinkedIn/GitHub links | Placeholder destinations are replaced before publication |
| T16 | Console/network | Inspect DevTools Console and Network tabs | No unexpected local asset errors; remote font failure degrades gracefully |
| T17 | HTML validation | Submit `index.html` to the W3C Nu HTML Checker | Resolve reported errors and review warnings |
| T18 | CSS validation | Validate each CSS file using W3C CSS Validation Service | Review and resolve invalid CSS declarations |
| T19 | Browser compatibility | Check Chrome, Firefox, and Edge; Safari if available | Main content and interactions work consistently |
| T20 | Deployment | Open the GitHub Pages URL after publishing | Styles/scripts load and all section links work |

### Test evidence record

Complete this table after running the tests:

| Test ID(s) | Result (Pass/Fail/Not tested) | Date | Evidence / notes |
|---|---|---|---|
| T01–T04 | Not tested | — | Record browser and viewport |
| T05–T08 | Not tested | — | Record menu/theme results |
| T09–T12 | Not tested | — | Capture validation screenshots |
| T13–T14 | Not tested | — | Record keyboard/reduced-motion behavior |
| T15–T20 | Not tested | — | Add validator links, browser notes, and deployment URL |

Do not label these tests as passed until they have actually been performed.

---

## 11. Git and GitHub Workflow

Run these commands from the project folder:

```bash
git init
git add .
git commit -m "Build advanced responsive portfolio"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/advanced-portfolio.git
git push -u origin main
```

Replace the placeholder username and repository URL. If the repository already has a remote, inspect it with `git remote -v` instead of adding a duplicate.

### GitHub Pages deployment

1. Push the project to a GitHub repository.
2. Open **Settings → Pages** in that repository.
3. Choose **Deploy from a branch**.
4. Select branch `main` and folder `/(root)`.
5. Save and wait for GitHub Pages to publish.
6. Open the generated URL and complete the deployment test cases.
7. Commit and push later updates; GitHub Pages redeploys from the configured source.

---

## 12. Final Submission Checklist

- [ ] Project overview and objectives are documented.
- [ ] Setup instructions are followed successfully in VS Code.
- [ ] Folder structure matches the required structure.
- [ ] CSS remains split across `main.css`, `layout.css`, and `animations.css`.
- [ ] Grid, Flexbox, custom properties, BEM, advanced selectors, and animations are demonstrated.
- [ ] Light/dark themes and local-storage persistence are tested.
- [ ] Mobile menu and active navigation behavior are tested.
- [ ] Contact form validation is tested and its frontend-only limitation is stated.
- [ ] Keyboard accessibility and reduced-motion behavior are checked.
- [ ] Actual screenshots are added to `screenshots/`.
- [ ] HTML and CSS validators have been run and findings addressed.
- [ ] Browser compatibility and performance checks have been recorded.
- [ ] Email, social URLs, education details, and project links are accurate.
- [ ] GitHub repository and GitHub Pages deployment are verified.
- [ ] Test evidence table is filled in with actual results.

## 13. Conclusion

This project combines a clean portfolio design with maintainable frontend architecture. CSS Grid is used for major multi-column layouts and galleries, Flexbox for one-dimensional component alignment, custom properties for consistent theming, and vanilla JavaScript for small interactive behaviors. The static architecture keeps setup simple and avoids unnecessary dependencies. Final submission quality depends on personalizing the placeholders, capturing real screenshots, and recording actual validation and browser test results.
