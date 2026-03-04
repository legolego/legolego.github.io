# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Retype 4.1.0** generated static documentation site hosted on GitHub Pages at https://legolego.github.io/. The site uses Turbopack for client-side routing and has no build process - content pages are HTML files stored directly in the repository.

## File Structure

```
├── index.html                # Home page (root)
├── 404.html                  # Custom 404 error page
├── personal/                 # Personal projects section
│   └── index.html           # Page content
├── university/               # University content section
│   └── index.html           # Page content
├── contact/                  # Contact page
│   └── index.html          # Page content
├── static/                   # Static assets (images, custom CSS)
│   ├── aboutheader.png
│   ├── lego.png
│   └── custom.css           # Site-specific styles
├── resources/               # Retype framework files
│   ├── css/retype.css       # Retype base styles (~50KB)
│   ├── fonts/               # Font assets
│   └── js/                  # JavaScript (retype.js, lunr.js, etc.)
└── global.json              # SDK config file
```

## Development Workflow

### No Build Process Required

This is a pure static site with **no build step**. Pages are edited directly as HTML files.

### Editing Content Pages

1. **Direct HTML editing** - All content pages (`*.html`) in `index.html`, `personal/index.html`, `university/index.html`, and `contact/index.html` can be edited directly
2. **Use Retype Markdown syntax** inside the `<doc-anchor-target>` elements for better formatting
3. **Revert to git** if you break something:

   ```bash
   git checkout .
   ```

### Adding New Pages

1. Add a new `index.html` file in the appropriate folder (e.g., `projects/`, `blog/`)
2. Use Retype's `<doc-anchor-target>` and `<doc-anchor-trigger>` components for navigation
3. Link from existing pages or sidebar configuration

### Common Tasks

| Task | Action |
|------|--------|
| Add a new page | Create `<folder>/index.html` with content |
| Update CSS | Edit `static/custom.css` (not `resources/css/retype.css`) |
| Replace images | Files in `static/` directory, referenced via `<img src="static/...">` |
| Fix broken links | Use git blame to find file, edit directly |

### Git Commands

- **Check status**: `git status`
- **View changes**: `git diff`
- **Commit**: `git add <files>` followed by `git commit -m "..."`
- **Push to GitHub Pages**: `git push origin main` (site builds automatically)

### Site Features

- **Turbo caching disabled** for hot reload during development
- **Dark mode support** via system preference and localStorage
- **Mobile-responsive** header with sidebar navigation
- **Search functionality** using Lunr.js
- **Theme switching** component (`doc-theme-switch`)
- **History tracking** for browsing

### Important Notes

- ⚠️ **Do not edit** `resources/css/retype.css` or `resources/js/` - these are Retype framework files
- ✅ **Edit only**: All `*.html` pages and `static/custom.css`
- 📝 Use `<doc-anchor-target id="..">` and `<doc-anchor-trigger to="#...">` for anchor links
- 🔗 External links should use `target="_blank"` (already applied in templates)

### Retype-Specific Syntax

Within HTML content, these Retype components provide functionality:

```html
<!-- Anchor target with trigger -->
<doc-anchor-target id="my-section">
    <h1>
        <doc-anchor-trigger class="header-anchor-trigger" to="#my-section">#</doc-anchor-trigger>
        My Section Title
    </h1>
</doc-anchor-target>

<!-- Link component for internal navigation -->
<a href="/personal/">
    <span class="block mt-1">Personal Projects</span>
</a>

<!-- Image with responsive classes -->
<img src="static/aboutheader.png" alt="" class="rounded-image-rounded border-image-border border-image-border-width" />
```

### Custom CSS Location

All site-specific styles should go in: `static/custom.css`

The base Retype styles in `resources/css/retype.css` are managed by the Retype generator.

---
*This site was generated with Retype 4.1.0*
