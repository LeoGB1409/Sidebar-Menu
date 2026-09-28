# Collapsible Sidebar Menu

A responsive dashboard sidebar built with **vanilla HTML, CSS, and JavaScript** — no frameworks, no build step. It features a collapsible layout, a persistent light/dark theme, and a mobile-friendly off-canvas mode with an overlay.

## Features

- **Collapsible sidebar** – toggle between a full (270px) and icon-only (90px) layout with a smooth width transition.
- **Light / Dark theme** – switch with one click; the choice is saved in `localStorage`.
- **System theme detection** – on first visit, the theme follows the user's `prefers-color-scheme` setting.
- **Search-to-expand** – clicking the search field while the sidebar is collapsed expands it and focuses the input.
- **Responsive design** – on screens up to 768px, the sidebar becomes an off-canvas drawer opened from a top navbar, with a dimmed backdrop.
- **CSS custom properties** – all colors are defined as variables, making theming and customization simple.
- **Google Material Symbols** – icon set loaded from Google Fonts.

## Project Structure

```
.
├── index.html   # Page markup (navbar, sidebar, main content)
├── style.css    # Layout, theming, transitions, responsive rules
└── script.js    # Sidebar toggle, theme toggle, search behavior
```

## Getting Started

No installation is required.

1. Clone or download this repository.
2. Open `index.html` in your browser.

```bash
git clone <your-repo-url>
cd <your-repo-folder>
# Then just open index.html in your browser
```

> An internet connection is needed to load the Google Fonts (Poppins and Material Symbols) and the sample logo image.

## How It Works

### Sidebar toggle
Every element with the `.sidebar-toggle` class (the chevron in the sidebar header and the hamburger button in the mobile navbar) toggles the `collapsed` class on `.sidebar`. CSS handles the rest: the width transition, the label fade-out, and the icon rotation.

### Theme switching
The theme is controlled by the `dark-theme` class on `<body>`. On page load, the script checks `localStorage` first, then falls back to the system preference. Clicking the theme button toggles the class, updates the icon (`dark_mode` / `light_mode`), and saves the preference.

### Responsive behavior
A media query at `max-width: 768px`:
- Shows the top navbar with the hamburger button.
- Turns the sidebar into a fixed drawer that slides in from the left.
- Displays a dark backdrop (via `body::before`) whenever the sidebar is open, using the `:has()` selector.

## Customization

### Colors
Edit the CSS variables in `style.css`:

```css
:root {
    --color-text-primary: #1F2936;
    --color-bg-primary: #f9fafb;
    --color-bg-sidebar: #FFFFFF;
    --color-hover-primary: #695CFE;
    /* ... */
}

body.dark-theme {
    --color-text-primary: #F1F5F9;
    --color-bg-primary: #111827;
    --color-bg-sidebar: #1f2937;
    /* ... */
}
```

### Menu items
Add a new item by copying an existing `<li>` in `index.html` and changing the icon name and label:

```html
<li class="menu-item">
    <a href="#" class="menu-link">
        <span class="material-symbols-rounded">home</span>
        <span class="menu-label">Home</span>
    </a>
</li>
```

Browse available icon names at [Google Fonts – Material Symbols](https://fonts.google.com/icons).

### Logo
Replace the `src` of `.header-logo` in `index.html` with your own image.

### Breakpoint
To change when the mobile layout kicks in, update `768px` in both `style.css` (media query) and `script.js` (`window.innerWidth > 768`).

## Browser Support

Works in all modern browsers. The mobile overlay relies on the CSS `:has()` selector, supported in Chrome/Edge 105+, Safari 15.4+, and Firefox 121+.

## Built With

- HTML5
- CSS3 (Flexbox, custom properties, transitions, media queries)
- JavaScript (ES6+)
- [Google Fonts](https://fonts.google.com/) – Poppins
- [Material Symbols](https://fonts.google.com/icons) – Rounded

## License

This project is open source and available under the [MIT License](LICENSE).
