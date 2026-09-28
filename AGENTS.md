# Project instructions

## Goal

This is a local fork of `tanabe/markdown-live-preview`.

The goal is to keep it a small, lightweight Markdown viewer while making it suitable for private local use.

Primary requirements:

- No analytics or telemetry.
- No tracking.
- No runtime requests to third-party services.
- No external CDN dependencies at runtime.
- Markdown contents must not be transmitted outside the local machine/server.
- The final application should preferably be self-contained static HTML/CSS/JavaScript served by nginx.
- Keep the implementation simple and minimize dependencies.

## Workflow

- Inspect the existing project before making changes.
- Understand the current implementation before proposing modifications.
- Prefer minimal, targeted changes.
- Do not refactor unrelated code.
- Do not introduce new abstractions unless clearly necessary.
- Do not add new features outside the agreed scope.
- Preserve existing useful functionality unless it conflicts with the security/privacy requirements.

Before modifying code, first report:

- project structure and relevant files;
- direct dependencies and their purpose;
- install/build scripts;
- npm lifecycle scripts, if any;
- Git or non-registry dependencies;
- external URLs, CDN resources, analytics, telemetry, or other network access;
- what network access occurs during build versus at runtime;
- proposed minimal changes.

Wait for explicit approval before implementing the proposed changes.

## Dependencies and network access

- Do not run `npm install`, `npm ci`, `npm update`, or similar package installation commands without explicit approval.
- Do not install system packages without explicit approval.
- Do not download files or dependencies from the Internet without explicit approval.
- Do not add or upgrade dependencies without explicit approval.
- Prefer removing unnecessary dependencies over adding new ones.
- Do not change dependency versions merely to modernize the project.

For dependency analysis, inspect the existing `package.json`, lock files, Makefile, source files, and other repository files first.

## Security and privacy

Treat privacy and absence of unexpected network access as primary requirements.

Pay particular attention to:

- analytics;
- telemetry;
- Google Analytics / Google Tag Manager;
- external JavaScript;
- external CSS;
- external fonts;
- CDN resources;
- remote images or other resources loaded automatically;
- `fetch`, XMLHttpRequest, WebSocket, beacon, or similar network APIs;
- npm lifecycle scripts;
- dependencies fetched directly from Git repositories;
- dynamically loaded resources.

Do not assume a dependency or network request is safe merely because it is commonly used.

Never put secrets, credentials, tokens, or private data into source files.

## System safety

- Do not modify nginx, firewall, DNS, operating-system configuration, or other system services without explicit approval.
- Do not modify files outside this project directory without explicit approval.
- Do not use `sudo` without explicit approval.

## Git

- Do not commit unless explicitly asked.
- Do not push unless explicitly asked.
- Do not rewrite Git history.
- Do not add remotes unless explicitly asked.
- Before proposing a commit, show or summarize the relevant `git diff`.

## Verification

After approved changes:

- inspect the final diff;
- search source and generated files for unexpected external URLs and tracking code;
- verify that runtime operation does not require Internet access;
- verify that the application still performs its intended Markdown preview functionality.

Do not claim that the application is network-isolated or tracker-free unless this has actually been verified.
