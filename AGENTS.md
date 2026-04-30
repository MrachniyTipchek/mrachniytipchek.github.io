## Cursor Cloud specific instructions

This is a purely static HTML/CSS/JS website (GitHub Pages). There is no build step, no package manager, and no backend.

### Running the dev server

```
python3 -m http.server 8080
```

Run from the repository root. All 6 HTML files are served directly. No compilation or bundling is needed.

### External CDN dependencies

The Markdown Viewer (`markdown-viewer.html`) loads `marked` from `cdn.jsdelivr.net` and the QR Code Generator (`qr-code-generator.html`) loads `qr-code-styling` from `unpkg.com`/`cdn.jsdelivr.net`. Internet access is required for these two tools to function. The other tools (Password Generator, MAC Address Generator, Todo List) work fully offline.

### Testing

There are no automated tests or linters. Validation is done by serving the files and manually testing each tool in a browser. All tools are self-contained single HTML files with inline `<style>` and `<script>` tags.

### Architecture

Each tool is a standalone HTML file with embedded CSS and JS. The landing page (`index.html`) links to all tools. State (Todo List) uses browser `localStorage`. Cryptographic randomness (Password/MAC generators) uses `crypto.getRandomValues()`.
