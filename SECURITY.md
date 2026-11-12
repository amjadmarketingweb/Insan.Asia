# Security posture

This repository publishes a static marketing website through GitHub Pages.

## Current attack surface

- No forms, file uploads, login, password storage, sessions, database, API routes, or server-side queries.
- No client-side API keys or runtime secrets.
- Contact actions link directly to WhatsApp.
- A restrictive Content Security Policy blocks forms, network requests, frames, and plugins.
- Environment files are ignored by Git.

Controls such as login rate limiting, password hashing, secure session cookies,
bot challenges, upload validation, and parameterized SQL are intentionally not
implemented because the website has none of those server-side features. They
must be added together with a real backend if those features are introduced.

## Hosting controls

GitHub Pages must have **Enforce HTTPS** enabled in repository Settings → Pages.
GitHub Pages controls HTTP response headers; the repository also emits a CSP
and strict referrer policy in the HTML document.

## Maintenance

Run `pnpm audit` and `pnpm test` before publishing changes. Never commit `.env`
files, credentials, API tokens, passwords, or private keys.
