# Riya Kumari — Advanced Portfolio Website

A responsive personal portfolio built with semantic HTML5, modular CSS, and vanilla JavaScript. The project demonstrates CSS Grid, Flexbox, CSS custom properties, BEM naming, accessible interactions, animation, and light/dark theme switching.

## Features

- Responsive navigation with a compact mobile menu
- Hero, About, Skills, Projects, Education, Contact, and Footer sections
- CSS Grid project gallery and skill-card layouts
- Flexbox navigation, buttons, metadata, tags, and footer layouts
- Reusable design tokens in `:root` and a dark theme using `data-theme`
- Theme preference stored in local storage; system preference used on first visit
- Contact form validation in the browser (does **not** send email)
- Keyboard focus indicators, skip link, semantic landmarks, labels, and reduced-motion support
- No Bootstrap, Tailwind, frameworks, or build step required
- CSS-created project illustrations so no image files are required to run the starter

## Technologies

- HTML5
- CSS3 (Grid, Flexbox, custom properties, animations, media queries, advanced selectors)
- Vanilla JavaScript
- Google Fonts: DM Sans and Manrope (the site uses fallback fonts if the remote font service is unavailable)

## Folder structure

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

## Run locally in VS Code

1. Extract the project ZIP.
2. Open the `advanced-portfolio` folder in Visual Studio Code.
3. Install the **Live Server** extension if it is not already installed.
4. Right-click `index.html` and select **Open with Live Server**.
5. Test the page at desktop and mobile widths. You can also open `index.html` directly, but Live Server is recommended for a consistent local workflow.

There is no package installation or build command.

## Personalize before submission

1. Replace `your.email@example.com` in `index.html` with your real contact email.
2. Replace generic LinkedIn and GitHub URLs with your profile URLs.
3. Add a profile photo following `images/README.md`, if you want one.
4. Add actual GitHub repository and live-demo URLs only after publishing those projects. Until then, project cards link to the contact section instead of fake destinations.
5. Review the education wording and dates to ensure they exactly match your official course title and records.
6. Add real screenshots to `screenshots/` after capturing the running website.
7. Do not add achievements, experience, or certificates unless they are accurate.

## Theme switching

The theme control toggles between light and dark themes. The selected theme is saved under the local-storage key `riya-portfolio-theme`. If no valid saved preference exists, the page follows the system color-scheme preference.

## Contact form behavior

The form validates name, email, and message fields on the client. It displays a local validation result only. It does not send, store, or email the message. To receive submissions, connect a backend endpoint or a reputable form service and update the form handler accordingly.

## Git and GitHub

Open a terminal in the project folder and run:

```bash
git init
git add .
git commit -m "Build responsive portfolio website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/advanced-portfolio.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username. If Git says the remote already exists, inspect it with `git remote -v` and update it using `git remote set-url origin YOUR-REPOSITORY-URL`.

## Publish with GitHub Pages

1. Push the project to a GitHub repository.
2. Open the repository on GitHub and choose **Settings**.
3. Select **Pages** in the left sidebar.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then save.
6. Wait for the deployment workflow to finish. The Pages section will show the published URL.
7. Open the URL and test navigation, styles, theme switching, and the form. Because all paths are relative, this project works from the repository root.
8. After updates, commit and push again; GitHub Pages will redeploy.

## Testing checklist

- [ ] Mobile layout at ~320–480 px: no horizontal scrolling; menu opens/closes.
- [ ] Tablet layout at ~768 px: grids adapt and text remains readable.
- [ ] Desktop layout at 1024 px and wider: hero and content grids balance correctly.
- [ ] Theme toggle switches both ways and updates its accessible label.
- [ ] Selected theme persists after refresh.
- [ ] First visit without a saved preference follows the operating-system theme.
- [ ] Keyboard-only navigation works; skip link and visible focus rings are clear.
- [ ] Form rejects a short name, invalid email, and short message; valid form clearly says it was not sent.
- [ ] Hover, active, focus, and reduced-motion behavior are checked.
- [ ] Check in Chrome, Firefox, and Edge if available; spot-check Safari/iOS if available.
- [ ] Validate HTML with the W3C Nu HTML Checker and CSS with the W3C CSS Validation Service.
- [ ] Check the browser console for errors and test after disabling network access (Google Fonts may fall back).
- [ ] Compress any added images and use descriptive alt text.
- [ ] Replace all contact and social placeholders before public deployment.

## Implementation notes

- `css/main.css` holds design tokens, typography, reusable components, and the primary visual styles.
- `css/layout.css` contains grid-area definitions, responsive grids, and breakpoints.
- `css/animations.css` contains motion and hover-related styling plus the reduced-motion override.
- `js/theme-switcher.js` handles theme preference, mobile navigation, active section links, year, and contact form validation.
- BEM-style classes use `block__element--modifier`, for example `project-card__title` and `button--primary`.
