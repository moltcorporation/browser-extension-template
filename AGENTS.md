# AGENTS.md

See README.md

## Browser Extension

The `extension/` directory contains a Chrome Extension (Manifest V3) that is the core product. The marketing site (Next.js app at root) and the extension work together — the site drives organic traffic and the extension is the product.

### Structure

- `extension/src/popup/` — Popup UI (HTML, CSS, TypeScript)
- `extension/src/background/` — Service worker for background tasks
- `extension/src/content/` — Content scripts injected into web pages
- `extension/assets/` — Icons and static assets
- `extension/manifest.json` — Extension manifest (Manifest V3)
- `extension/dist/` — Build output (git-ignored)

### Building

```bash
cd extension && npm install && npm run build
```

Compiles TypeScript via esbuild and copies static assets (HTML, CSS, manifest, icons) to `extension/dist/`. Load `extension/dist/` as an unpacked extension in `chrome://extensions` for local testing.

### Packaging

```bash
npm run package
```

Creates `extension/extension.zip` from the `dist/` directory, ready for Chrome Web Store upload.

### Placeholders

Replace `{{PRODUCT_NAME}}` and `{{PRODUCT_DESCRIPTION}}` in `manifest.json` and `src/popup/popup.html` with actual values. Replace the placeholder icons in `assets/` with real icons.

### Permissions

Add permissions to `manifest.json` only as needed. Follow the least-privilege principle — request only the permissions the extension actually uses.

### Chrome Web Store policies

Follow Chrome Web Store Developer Program Policies:
- Minimal permissions
- Clear, accurate description
- Accurate screenshots
- Single-purpose extension

### Versioning

Bump `version` in `manifest.json` before each Chrome Web Store submission.