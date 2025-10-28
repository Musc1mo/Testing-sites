# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a static landing page for an English language school ("English School") built with pure HTML5 and CSS3. It is a single-page application with multiple sections (home, about, courses, teachers, contact) and is fully responsive. The content is in Russian.

## Commands

### Viewing the Site

**Open directly in browser:**
```bash
start index.html
```

**Run local development server (Python 3):**
```bash
python -m http.server 8000
```
Then navigate to `http://localhost:8000`

**Run local development server (Node.js/npx):**
```bash
npx http-server
```

### No Build/Lint/Test Commands
This project has no build process, linters, or test framework configured. It's a simple static site with HTML and CSS only.

## Architecture

### File Structure
```
english-school-website/
├── index.html      # Main HTML page (159 lines)
├── styles.css      # All styling (374 lines)
└── README.md       # Documentation in Russian
```

### HTML Structure (`index.html`)
- **Language:** Russian (`lang="ru"`)
- **Sections:**
  - `<header>`: Sticky navigation with logo and nav links
  - `#home` (hero): Call-to-action banner
  - `#about`: Three feature cards about the school
  - `#courses`: Three course cards (children, teens, adults) with pricing
  - `#teachers`: Three teacher profile cards
  - `#contact`: Contact info and registration form
  - `<footer>`: Copyright and social links
- **Form:** Contact form in `#contact` section (no JavaScript validation or submission handling)

### CSS Architecture (`styles.css`)
- **Global Reset:** Universal selector reset with `box-sizing: border-box`
- **Layout System:**
  - `.container`: Max-width 1200px, centered, responsive padding
  - CSS Grid for multi-column layouts (about-content, course-grid, teacher-grid, contact-content)
  - Flexbox for navigation and footer social links
- **Design System:**
  - **Primary gradient:** `linear-gradient(135deg, #667eea 0%, #764ba2 100%)` used in header, hero, buttons
  - **Accent color:** `#ffd700` (gold) for hover states and CTA button
  - **Background colors:** `#f8f9fa` (light gray) for alternating sections, `#333` (dark) for footer
  - **Typography:** 'Segoe UI' fallback stack
- **Sticky Header:** `position: sticky` on header element
- **Hover Effects:** `transform: translateY()` and `box-shadow` transitions on cards and buttons
- **Responsive:** Mobile breakpoint at 768px, converts grids to single column and adjusts font sizes

### Key Design Patterns
1. **Section Pattern:** Each section has 80px vertical padding and consistent heading styles (2.5rem, centered, colored)
2. **Card Pattern:** White background, rounded corners (10px), shadow (`0 5px 15px rgba(0,0,0,0.1)`), hover lift effect
3. **Form Pattern:** Vertical flex layout, consistent input styling with focus state (border-color change to `#667eea`)

## Development Guidelines

### When Editing HTML
- Maintain semantic HTML5 structure
- Keep Russian language content and HTML `lang="ru"` attribute
- All section IDs must match nav href anchors (`#home`, `#about`, `#courses`, `#teachers`, `#contact`)
- Preserve emoji icons used throughout (🎓, 📚, 🌍, 👩‍🏫, 👨‍🏫, 📍, 📞, 📧, 🕐)

### When Editing CSS
- **Maintain the gradient color scheme:** Do not change primary colors (`#667eea`, `#764ba2`) without updating all instances
- **Preserve responsive behavior:** Test changes at 768px breakpoint
- **Keep transitions consistent:** Use 0.3s duration for most transitions
- **Maintain grid patterns:** Use `repeat(auto-fit, minmax(Xpx, 1fr))` for responsive grids

### Responsive Design Notes
- Navigation collapses to vertical at mobile breakpoint (no hamburger menu implemented yet)
- Hero heading scales from 3rem to 2rem at mobile
- All three-column grids become single-column at mobile
- Mobile breakpoint: `@media (max-width: 768px)`

## Future Enhancement Suggestions (from README)
- Add JavaScript for form interactivity and validation
- Implement mobile hamburger menu for navigation
- Add photo gallery
- Connect form to backend for actual submission handling
- Add student testimonials section
