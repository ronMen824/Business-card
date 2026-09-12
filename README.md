# Business Card — Ron Igal Menuhin

Assignment 1, Web Application Development course.

A responsive digital business card with a Batman / Wayne Enterprises dual theme,
built with **HTML and CSS only**. There is no JavaScript in this project.

**Live site:** [https://ronmen824.github.io/Business-card/]

## Running it

Clone or download the repository and open `index.html` in any modern browser.
No build step, no dependencies, no server required.

```
├── index.html      # semantic HTML5 markup
├── styles.css      # every style in the project
└── assets/
    ├── batman-pfp.jpeg   # portrait shown in the dark theme
    ├── wayne-pfp.jpeg    # portrait shown in the light theme
    └── favicon.svg       # bat emblem
```

## How the theme switch works without JavaScript

A single visually hidden checkbox holds the state, and CSS reads it:

```css
:root { /* Wayne Enterprises — light, the base token set */ }

#theme-toggle:checked ~ .page,
#theme-toggle:checked ~ .switch,
:root:has(#theme-toggle:checked) { /* Batman — dark overrides */ }
```

The `<label for="theme-toggle">` is styled as the pill switch in the top-right
corner, so clicking it flips the checkbox and repaints the page. The general
sibling combinator drives the card itself in every browser; `:has()` additionally
repaints the viewport canvas so the edges and overscroll match.

The checkbox carries the `checked` attribute in the markup, so the card loads in
the Batman theme. Switching themes also cross-fades the profile photo between the
two portraits — also pure CSS.

The theme is deliberately **not** wired to `prefers-color-scheme`: a checkbox's
state cannot be set by a media query, so honouring the OS setting would leave the
switch's position contradicting what is on screen.

## Built with

- Semantic HTML5 — `header`, `main`, `section`, `article`, `address`, `footer`
- CSS custom properties for a shared spacing, type, radius, shadow and motion scale
- CSS Grid and Flexbox, mobile-first, fluid via `clamp()`
- Google Fonts — Anton (display) and Inter (body)
- Inline SVG sprite for all icons, coloured entirely from the stylesheet

Accessibility and polish: visible focus states throughout, a skip link, AA colour
contrast in both themes, `prefers-reduced-motion` support, hover effects guarded
behind `@media (hover: hover)` so they do not stick on touch screens, and a print
stylesheet.

## A note on the content

The email address and phone number are fictional, as the assignment permits.
The LinkedIn and GitHub links are real.
