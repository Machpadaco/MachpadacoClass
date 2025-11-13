<!-- Repository-specific instructions for AI coding agents. Keep concise and actionable. -->

# Copilot instructions for MachpadacoClass

Purpose: quickly orient an AI agent to the project's structure, common edit patterns, and developer workflows so small, safe changes can be made with confidence.

- Big picture
  - This is a small static website (HTML + CSS, optional JS). Pages live at the repo root: `index.html`, `About.html`, `Services.html`, `Login.html`, `SignUp.html`.
  - Styling is centralized in `CSS/styles.css`. Images live in the `img/` folder. `script.js` is the single client-side JS entry (currently empty).

- How this app is served/run
  - No build system or server required. Open `index.html` in a browser. On Windows you can run: `start index.html` from the project folder.

- Key edit patterns and examples
  - Navigation header: central shared UI is the `<header>` in `index.html`. When adding pages, add a corresponding `<a href="NewPage.html">` link here and create the new HTML file at root.
    - Dropdown pattern: markup uses `.dropdown` wrapper, `.dropbtn` anchor, and `.dropdown-content` for menu items. Example (in `index.html`):
      - `<div class="dropdown"><a href="Services.html" class="dropbtn">Services</a><div class="dropdown-content">...</div></div>`
    - Styling for this dropdown is in `CSS/styles.css` (see `.dropdown`, `.dropdown-content`, `.dropdown:hover .dropdown-content`).
  - CSS conventions: single stylesheet `CSS/styles.css`. Keep global layout changes here. Many selectors expect the header markup in `index.html` (e.g., `nav a`, `img`, `header`).
  - JavaScript hookup: `script.js` is loaded at the end of `index.html` (`<script src="script.js"></script>`). Add DOM-ready logic here for interactive features (navigation enhancements, form validations).

- Project-specific conventions to preserve
  - Files are placed at repo root (HTML pages) and `CSS/` for styles. Use relative paths (e.g., `CSS/styles.css`, `img/…`) — changing directory layout requires updating all links.
  - Filenames use capitalization (e.g., `About.html`). Keep exact names to avoid broken links on case-sensitive hosts.

- Integration points & external dependencies
  - None declared. No package manager files, no server back-end, no tests. Any external dependency must be added explicitly and referenced from HTML (e.g., CDN) or added as new project files.

- Safe change rules for an AI agent
  - Small UI fixes and content updates are allowed. When editing navigation or page filenames, update all HTML files that link to them.
  - Avoid reworking global layout without a quick visual check (CSS is the single source of truth). If changing `header` or body sizing (e.g., `width: 90%`, `height: 100vh`), make a note in the PR describing visual verification steps.
  - If adding JS behavior, modify `script.js`. Keep changes localized and add small comments explaining the DOM selectors used (so future agents can find them).

- Where to look for examples
  - `index.html` — primary header/navigation markup and script include.
  - `CSS/styles.css` — dropdown and navigation styling; useful selectors: `.dropdown`, `.dropdown-content`, `nav a`, `header`.

If anything in these notes is unclear or you want the agent to follow additional conventions (commit message format, branching rules, or a test harness), tell me and I will update this file.
