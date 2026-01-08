# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a static website repository that hosts a collection of web-based utility tools at tools.vinlam.com. All tools are self-contained, single-page HTML applications with embedded CSS and JavaScript. There is no build process, compilation, or dependencies - tools are deployed directly as static files.

## Architecture

**Static HTML Architecture**: Each tool is a standalone HTML file with inline styles and scripts. All functionality is client-side JavaScript.

**File Structure**:
- `index.html` - Landing page with navigation and tool listing
- `hyrox-predictor.html` - Hyrox race time prediction calculator
- `text-for-llm.html` - Text-to-markdown converter for LLM consumption
- `treadmill-pace.html` - Running pace to treadmill speed converter
- `CNAME` - Domain configuration for GitHub Pages (tools.vinlam.com)

**Shared UI Pattern**: All tools share a consistent visual design:
- Gradient backgrounds (`linear-gradient(135deg, #667eea 0%, #764ba2 100%)`)
- Rounded containers with box shadows
- Responsive layouts using CSS Grid and Flexbox
- Mobile-first design with media queries
- Favicon from vinlam.com (`<link rel="icon" type="image/svg+xml" href="/favicon.svg">`)

**Navigation**: The index page includes a header with navigation to the main vinlam.com site, featuring a responsive hamburger menu for mobile views. The navigation structure assumes this is part of a larger vinlam.com ecosystem.

## Development Workflow

**No Build Process**: This repository has no package.json, build tools, or dependencies. All changes are direct edits to HTML files.

**Testing**: Open HTML files directly in a browser or use a local web server:
```bash
# Option 1: Python
python -m http.server 8000

# Option 2: PHP
php -S localhost:8000

# Option 3: Node.js (if http-server installed globally)
npx http-server
```

**Deployment**: The site is hosted on GitHub Pages. Changes pushed to the main branch are automatically deployed.

## Adding New Tools

When adding a new tool:

1. Create a new HTML file in the root directory (e.g., `my-tool.html`)
2. Follow the existing single-file architecture pattern
3. Use the established design system (gradients, colors, responsive patterns)
4. **Include the favicon link** in the HTML head:
   ```html
   <link rel="icon" type="image/svg+xml" href="/favicon.svg">
   ```
5. **Include the top navigation bar** - All tools must have a thin navigation bar at the top:
   - Include "← More Tools" link that points to `https://tools.vinlam.com`
   - For running-related tools, also include "Singapore Run Clubs" link to `https://vinlam.com/posts/run-clubs-in-sg/`
   - Style the nav bar to match the tool's theme (light or dark)
   - See [hyrox-predictor.html](hyrox-predictor.html:24-60) or [treadmill-pace.html](treadmill-pace.html:36-71) for implementation examples
6. Add an entry to the tool list in `index.html`:
   ```html
   <li>
       <a href="/my-tool">Tool Name</a>
       <p class="description">Brief description of what the tool does.</p>
   </li>
   ```
7. Test locally before committing
8. Push to main branch to deploy

## Tool Implementation Patterns

**Navigation Bar Structure**: All tools must include a top navigation bar:

```css
.top-nav {
    background: rgba(255, 255, 255, 0.95); /* or dark: rgba(30, 30, 30, 0.95) */
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
    padding: 8px 15px;
    display: flex;
    align-items: center;
    gap: 20px;
    flex-wrap: wrap;
}
```

```html
<body>
    <nav class="top-nav">
        <a href="https://tools.vinlam.com">← More Tools</a>
        <!-- For running tools, add: -->
        <a href="https://vinlam.com/posts/run-clubs-in-sg/">Singapore Run Clubs</a>
    </nav>
    <div class="main-wrapper">
        <!-- Tool content -->
    </div>
</body>
```

**State Management**: Tools use plain JavaScript with DOM manipulation. Common patterns:
- Range sliders synced with text inputs
- Real-time calculations on input events
- LocalStorage for persisting user preferences (if needed)

**Input Handling**: Tools typically use:
- `<input type="range">` for slider controls
- `<input type="number">` or `<input type="text">` for direct value entry
- Bidirectional syncing between slider and text input values

**Responsive Design**: All tools use mobile-first responsive design:
- Single column layouts on mobile
- Multi-column grids on desktop (typically `grid-template-columns: 1fr 1fr`)
- Breakpoints typically at 600px, 768px, and 900px
