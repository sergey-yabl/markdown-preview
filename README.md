# Markdown Preview

A lightweight, privacy-focused Markdown editor and live preview for local/self-hosted use.

This project is based on [tanabe/markdown-live-preview](https://github.com/tanabe/markdown-live-preview) and has been adapted for a local environment.

## Changes from upstream

- Removed Google Analytics / Google Tag Manager.
- Removed Firebase deployment support.
- Removed external Git dependency `storehouse-js`.
- Removed unused dependencies and assets.
- Uses browser `localStorage` directly.
- No external CDN dependencies at runtime.
- Blocks automatic loading of external resources from rendered Markdown.
- Keeps Monaco Editor, Mermaid support, live preview and PDF/print functionality.

The production build is fully static and can be served directly by nginx or any other static web server.

## Requirements

- Node.js 20+
- npm

## Install dependencies

```bash
npm ci --ignore-scripts --no-audit --no-fund
```

The project does not require the `esbuild` postinstall script on Linux when the platform-specific esbuild package is present.

## Build

On Linux x86-64:

```bash
ESBUILD_BINARY_PATH="$PWD/node_modules/@esbuild/linux-x64/bin/esbuild" npm run build
```

The production files will be created in:

```text
dist/
```

## Development

```bash
npm run dev
```

## Deployment

Only the contents of `dist/` are required on the web server.

Example:

```bash
rsync -av --delete dist/ user@server:/opt/markdown/
```

Example nginx configuration:

```nginx
server {
    listen 8000;
    server_name markdown.host;

    root /opt/markdown;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

## Privacy

The application does not include analytics, telemetry, external CDN assets, or other intentional runtime network dependencies.

External links can still be opened explicitly by the user.

## License

See [LICENSE](LICENSE).

Original project: [tanabe/markdown-live-preview](https://github.com/tanabe/markdown-live-preview).
