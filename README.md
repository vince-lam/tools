# Tools

A collection of simple, self-contained web tools built with vanilla HTML, CSS, and JavaScript. Live at [tools.vinlam.com](https://tools.vinlam.com).

## Philosophy

This project embraces simplicity:

- **Single-file architecture**: Each tool is a standalone HTML file with embedded CSS and JavaScript
- **No build process**: No webpack, no npm, no compilation - just open and run
- **Zero dependencies**: Pure vanilla JavaScript, no frameworks or libraries
- **Instant deployment**: Push to GitHub and it's live via GitHub Pages

## Available Tools

### [Hyrox Race Predictor](https://tools.vinlam.com/hyrox-predictor)
Calculate your target Hyrox race time based on your running pace and station estimates.

### [Treadmill Pace Converter](https://tools.vinlam.com/treadmill-pace)
Convert running pace (min/km or min/mile) to treadmill speed (km/h or mph) for interval training sessions.

### [Heart Rate Zone Calculator](https://tools.vinlam.com/hr-zone-calculator)
Compare different heart rate zone calculation methods to see how Apple Watch, Garmin, and traditional formulas differ.

### [Text for LLM](https://tools.vinlam.com/text-for-llm)
Convert formatted text to clean markdown format optimized for pasting into LLMs like Claude or ChatGPT.

## Development

### Local Testing

Since these are static HTML files, you can open them directly in a browser or run a simple local server:

```bash
# Python
python -m http.server 8000

# PHP
php -S localhost:8000

# Node.js (if http-server is installed)
npx http-server
```

Then visit `http://localhost:8000` in your browser.

### Project Structure

```
.
├── index.html              # Landing page with tool listing
├── hyrox-predictor.html    # Hyrox race time calculator
├── treadmill-pace.html     # Pace to speed converter
├── text-for-llm.html       # Text formatter for LLMs
├── screenshots/            # Tool screenshots for index page
├── favicon.svg             # Site favicon
├── CNAME                   # GitHub Pages custom domain
├── CLAUDE.md               # Development guidelines
└── README.md               # This file
```

## Adding a New Tool

1. Create a new HTML file in the root directory (e.g., `my-tool.html`)
2. Follow the single-file pattern with inline CSS and JavaScript
3. Include the favicon in the `<head>`:
   ```html
   <link rel="icon" type="image/svg+xml" href="/favicon.svg">
   ```
4. Add the top navigation bar (see existing tools for examples):
   ```html
   <nav class="top-nav">
       <a href="https://tools.vinlam.com">← More Tools</a>
   </nav>
   ```
5. Use the established design system (gradients, rounded containers, responsive layouts)
6. Add an entry to [index.html](index.html) with a description and optional screenshot
7. Test locally
8. Push to main branch to deploy

## Design Guidelines

All tools share a consistent visual language:

- Purple gradient backgrounds: `linear-gradient(135deg, #667eea 0%, #764ba2 100%)`
- White rounded containers with box shadows
- Responsive layouts using CSS Grid and Flexbox
- Mobile-first design with breakpoints at 600px, 768px, and 900px
- Inter font family for clean, modern typography

## Deployment

This site is hosted on GitHub Pages and automatically deploys when changes are pushed to the main branch. The custom domain `tools.vinlam.com` is configured via the CNAME file.

No CI/CD configuration needed - GitHub Pages handles everything automatically.

## Why This Approach?

Building with single-file HTML tools offers several advantages:

- **Low friction**: Ideas go from concept to deployment in minutes
- **No maintenance burden**: No dependencies to update, no build tools to maintain
- **Maximum portability**: Tools work anywhere - just download and open
- **Easy to understand**: All code is visible in one place, perfect for learning
- **Future-proof**: Will work as long as browsers exist

This architecture is inspired by Simon Willison's concept of ["vibe coding"](https://simonwillison.net/2024/Oct/21/foreverview/) - building useful tools quickly without the overhead of modern web development.

## AI-Powered Development

Many of these tools were built with assistance from AI coding agents (ChatGPT, Claude, Gemini). The simple architecture makes them ideal for AI-assisted development since there's no complex tooling or build configuration to explain.

## License

All code is open source and available for use, modification, and learning.

## Contributing

Feel free to open issues or submit pull requests. Keep the philosophy of simplicity in mind - if a tool needs a build process or external dependencies, it probably belongs in a different project.

## Links

- Live site: [tools.vinlam.com](https://tools.vinlam.com)
- Main site: [vinlam.com](https://vinlam.com)
- GitHub: [github.com/vince-lam/tools](https://github.com/vince-lam/tools)
