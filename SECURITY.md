# Security Notes

This project is a static website intended for GitHub Pages. It does not contain a private server, a database, user authentication, or secret API keys. The placement test runs locally in the visitor's browser and does not send answers to a server.

## Current safeguards
- Content JSON and local scripts/styles are expected to be served from the same site.
- The HTML includes a Content Security Policy restricting script execution to the site's own files and limiting image/style/font sources to the specific hosts currently used.
- Dynamic lesson and FAQ content is escaped before insertion. The level accent is selected from fixed CSS classes rather than arbitrary inline CSS from data.
- External links opened in new tabs use `rel="noopener noreferrer"`.
- The original image assets are tracked by SHA-256 in `assets/ASSET-MANIFEST.json`.
- `scripts/validate-site.mjs` checks required files, JSON structure, FAQ count, question count and local references. GitHub Actions runs these checks on pushes and pull requests.

## Important limitations
- A static site cannot safely hide API secrets or securely authenticate users. Do not put tokens, passwords, private keys, or API secrets in any HTML, JavaScript, JSON, workflow artifact, or public repository file.
- Meta CSP cannot set every HTTP security header (for example, `frame-ancestors`). GitHub Pages does not expose arbitrary response-header configuration. If stronger response-header control becomes a requirement, assess an edge host/proxy such as Cloudflare Pages before changing hosting.
- The policy intentionally permits inline styles because parts of the existing design and UI update CSS properties dynamically. Inline scripts remain blocked by the policy.
- The world-photo gallery loads its photographs from `images.unsplash.com`; those images need an internet connection and may not appear when the provider is blocked. Fallback cards remain visible.
- External library CSS (Google Fonts and Font Awesome CDN) requires internet access. A future self-hosting step can improve resilience and reduce third-party requests.

## Before public release
- Review the CSP in the browser console on both pages.
- Test on desktop and mobile at the actual GitHub Pages URL.
- Confirm repository settings publish the intended branch/root folder and that no secrets or unrelated private files are present.
