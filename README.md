# excusinator

A one-page excuse generator styled as an official bureaucratic form. Pick a category, generate an absurd but oddly official-sounding excuse, and share it with a link - no server, no tracking, nothing leaves your browser.

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)
![No Build](https://img.shields.io/badge/build-none-lightgrey.svg)
![Static](https://img.shields.io/badge/backend-none-brightgreen.svg)

**Live:** [imdarshangk.github.io/excusinator](https://imdarshangk.github.io/excusinator/)

## What it does

- Pick a category - work, school, social, or family - and optionally who the excuse is for.
- Click **Generate excuse** to get a randomized, wildly specific reason, an escalation, and a sign-off, stamped with a case number and a "believability" score.
- **Copy** the excuse as plain text, or **Copy shareable link** to get a URL that encodes the exact excuse so anyone who opens it sees the same one - no database, just a `?e=` query param.

## Run it locally

No install, no build step. Either:

```bash
git clone https://github.com/imdarshangk/excusinator.git
cd excusinator
```

Then just open `index.html` in your browser, or serve it locally:

```bash
python3 -m http.server 8080
# or
npx serve .
```

Then visit `http://localhost:8080`.

## How it works

Everything runs client-side in vanilla HTML, CSS, and JavaScript:

- A set of excuse components (causes, escalations, sign-offs) per category are combined at random.
- The "believability meter" is a deliberately arbitrary scoring function for comedic effect - longer or more absurd excuses score lower, "official-sounding" language scores higher.
- Shareable links work by JSON-encoding the generated excuse, base64-encoding that string, and appending it as `?e=...` on the URL. On load, the page checks for that param and renders the shared excuse instead of a blank form.

No cookies, no analytics, no external requests of any kind.

## Deploying your own copy

This is a single static `index.html` file, so it deploys anywhere that serves static files:

- **GitHub Pages:** Settings → Pages → Deploy from branch `main`, folder `/ (root)`.
- **Anywhere else:** drag the folder onto any static host.

## Contributing

PRs welcome - the easiest contribution is adding more excuse variety. Open `index.html`, find the `causesByCategory`, `escalations`, and `signoffs` arrays near the top of the `<script>` block, and add your own lines. Keep the tone dry and bureaucratic rather than explicitly jokey - the deadpan delivery is the joke.

## License

MIT. See [LICENSE](LICENSE).
