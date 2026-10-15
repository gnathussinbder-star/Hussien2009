# Hussein Badr English — Project Rules

## Identity and assets
- Brand name: Hussein Badr English.
- Keep the current navy, blue, and gold visual identity.
- `assets/hussein-badr-profile.jpg` and `assets/hussein-badr-logo.jpg` are original user-provided assets. Never replace or edit them without explicit approval.
- Use relative URLs so the project continues to work at the GitHub Pages project path `/Hussien2009/`.

## Content and experience
- Default language is Arabic with RTL direction; all key UI sections should have Arabic and English versions.
- New pages should reuse the shared design system in `style.css` and include mobile, keyboard, and dark-mode consideration.
- Keep data separate from presentation where practical (`site.json`, `faq.json`).
- Never invent specific published lesson video URLs. Use the channel's search, Videos, Shorts, or Playlists routes until an exact video is supplied.
- Placement-test results are estimates, not official CEFR scores. The current quiz checks written language use, grammar, and vocabulary; it does not directly measure listening or speaking.
- Keep the FAQ between 10 and 15 high-quality questions unless the owner requests another number.

## Change workflow
1. Inspect the current repository before editing.
2. Make changes in a separate branch or review copy, not directly in `main`.
3. Run `node --check app.js`, `node --check placement-test.js`, and `node scripts/validate-site.mjs`.
4. Review all local references and test core interactions, including search, filters, language/theme toggles, FAQ, test navigation/results, and responsive layouts.
5. Record changes in `CHANGELOG.md`.
6. Provide a ZIP only after the agreed scope is complete, clearly distinguishing static checks from browser tests.
7. Never say the live website changed unless an update was actually pushed and published.
