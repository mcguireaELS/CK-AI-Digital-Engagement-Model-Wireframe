# ClinicalKey AI Customer Hub

A branded, interactive prototype of a self-service onboarding and enablement hub for ClinicalKey AI customers, built for customers in a self-support tier who do not have a dedicated customer success manager.

It is a single self-contained HTML file plus a folder of brand web fonts. No build step and no framework. This prototype supersedes the earlier grayscale wireframe.

## Live demo

Enable GitHub Pages (Settings, then Pages, deploy from the `main` branch, root). The hub is served at:

```
https://elsevier-health.github.io/REPO-NAME/
```

Replace `REPO-NAME` with this repository's name. Deploy `index.html` and the `fonts/` folder together so the brand fonts load.

## What it includes

- Two guided paths, an Administrator (deployment) path and a User (everyday value) path, that share a common intro and then fork.
- An inline learning model. Assets are presented in place as part of the journey rather than as links out.
- Progress tracking, a step rail, and a collapsible "Looking for something specific?" index that deep-links to the relevant step.
- Per-section and full-PDF download options.
- Email capture on entry, used as the xAPI actor, with a live learning-record status badge.

## Branding

- Type: Tiempos Text (serif, headlines) and National 2 (sans-serif, body and UI), served from `fonts/` via @font-face, with Georgia and Arial as the only fallbacks.
- Color: the Elsevier palette (Vital Orange, Graphite, White, Ink, Sand, Paper, Action Blue, Ivory) applied per brand rules. Vital Orange is an accent only, Action Blue is for links and CTAs only, Ivory is for lines only.
- Public hosting of the fonts is cleared by brand and legal, so the woff2 files may be committed and served.
- The header currently uses a plain-text "Elsevier" stand-in. Replace it with the official logo asset when available. The Non Solus mark is not recreated.

## xAPI tracking

- Email gate on entry sets the xAPI actor (mbox).
- A badge in the top right shows the connection state (live, sending, error), the captured email, and a running count of statements sent. There is no full statement stream.
- Tracked events: entering the hub (initialized), choosing a path (selected), viewing a step (experienced), completing a step (completed), completing a path (completed), and downloading a section or full PDF (downloaded).
- Transport tries a standard xAPI request first and falls back to the CORS-safe form-encoded syntax, so it works cross-origin from GitHub Pages.

Security note. The prototype contains a SCORM Cloud sandbox key and secret inline so it works without a backend. This is acceptable only for a disposable sandbox. For production, move statement sending behind a server-side proxy so the secret is not exposed in client-side code.

The activity IDs use a base of `https://elsevier-health.github.io/REPO-NAME/`. Update `ACT_BASE` in `index.html` to the real Pages path.

## Embeds

Live embeds wired in to confirm production behavior:

- Introducing ClinicalKey AI: Vimeo video, responsive.
- Get Started Guide: Frontify document, inline.
- Earn CME & Redeem MOC Credit: Frontify document, inline.

The remaining steps (FAQ, User Guide, Conversation Sharing, App Guide, and the admin setup guides) show a branded placeholder until their links are added.

The Enhanced ClinicalKey AI and Quarterly Updates steps were removed from both paths.

## View locally

Open `index.html` in a modern browser with the `fonts/` folder alongside it. Note that the brand fonts and the external embeds render reliably only when the page is hosted, not always in a sandboxed preview.

## Embed in another page (for example WordPress)

Because interactive JavaScript runs inside the hosted page, embed the whole experience with a single iframe:

```html
<iframe
  src="https://elsevier-health.github.io/REPO-NAME/"
  title="ClinicalKey AI Customer Hub"
  style="width:100%;height:900px;border:0;"
  loading="lazy">
</iframe>
```

## Repository structure

```
.
├── index.html          # the branded, xAPI-enabled prototype
├── fonts/              # brand web fonts (woff2)
├── README.md
├── LICENSE
└── .gitignore
```

## Status

Prototype for an internal Elsevier Customer Learning project. Pilot targeted for early to mid September.

## License

Proprietary. See [LICENSE](LICENSE).
