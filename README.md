# ClinicalKey AI — Customer Hub (Wireframe)

An interactive, **low-fidelity** wireframe of a self-service onboarding and enablement hub for ClinicalKey AI customers — built for customers in a self-support tier who don't have a dedicated customer success manager.

It is built as self-contained HTML with no dependencies and no build step. It is intentionally grayscale and un-branded: the goal at this stage is to align on **structure and flow**, not visual design. Design and branding come later.

## Versions

There are two versions of the wireframe:

| File | Purpose |
|------|---------|
| `index.html` | The base wireframe. No tracking. Use this for structure/flow review. |
| `xapi/index.html` | An xAPI-enabled version that captures a learner email and sends xAPI statements to a SCORM Cloud LRS. Use this to demonstrate learning-data capture. |

## Live demo

Once GitHub Pages is enabled (Settings → Pages → deploy from the `main` branch, root), the wireframes are served at:

```
Base wireframe:   https://elsevier-health.github.io/REPO-NAME/
xAPI version:     https://elsevier-health.github.io/REPO-NAME/xapi/
```

Replace `REPO-NAME` with this repository's name.

## What it demonstrates

- **Two guided paths** — an *Administrator* (deployment) path and a *User* (everyday value) path that share a common intro, then fork.
- **Inline learning model** — each asset (video, guide, quick sheet) is presented in place as part of the journey rather than as a link out.
- **Progress and resume** — a step rail tracks where the learner is and what's next.
- **Browse by concern** — a collapsible "Looking for something specific?" index that deep-links to the relevant step, for learners who just need one thing.
- **Per-section and full-PDF downloads** — light portability without breaking the journey.
- **Design notes** — toggle **Design notes** in the upper-right corner to see the rationale behind each decision.

## xAPI version (`xapi/index.html`)

The xAPI version adds learning-data capture on top of the base wireframe:

- **Email gate** — on entry, the learner enters an email, which is used as the xAPI actor (`mbox`).
- **Live status badge** — a badge in the top-right shows the LRS connection state (live / sending / error), the captured email, and a running count of statements sent. It intentionally does *not* show a full statement stream.
- **Tracked events** — statements are sent for: entering the hub (`initialized`), choosing a path (`selected`), viewing a step (`experienced`), completing a step (`completed`), completing a path (`completed`), and downloading a section or full PDF (`downloaded`).
- **Transport** — it tries a standard xAPI request first and falls back to the CORS-safe form-encoded syntax, so it works cross-origin from GitHub Pages.

**Security note.** The xAPI version contains a **SCORM Cloud sandbox** key/secret inline so the prototype works without a backend. This is acceptable only for a disposable sandbox. For any production or customer-facing use, move statement-sending behind a server-side proxy (e.g., an AWS Lambda) so the secret is never exposed in client-side code. Do not point this at a production LRS with an inline secret.

The activity IDs use a base of `https://elsevier-health.github.io/ckai-hub/`. Update that base in `xapi/index.html` to match the actual hosting path so activity IDs are consistent.

## View locally

Open either `index.html` in any modern browser. No server required. (The xAPI version will attempt to reach the LRS; a live connection is needed for statements to send.)

## Embed in another page (e.g., WordPress)

Because interactive JavaScript runs inside the hosted page, you can embed the whole experience with a single iframe — no custom scripts needed on the host page:

```html
<!-- Base wireframe -->
<iframe
  src="https://elsevier-health.github.io/REPO-NAME/"
  title="ClinicalKey AI Customer Hub wireframe"
  style="width:100%;height:900px;border:0;"
  loading="lazy">
</iframe>

<!-- xAPI version -->
<iframe
  src="https://elsevier-health.github.io/REPO-NAME/xapi/"
  title="ClinicalKey AI Customer Hub (xAPI)"
  style="width:100%;height:900px;border:0;"
  loading="lazy">
</iframe>
```

Adjust `height` to suit the page.

## Repository structure

```
.
├── index.html          # base wireframe (single self-contained file)
├── xapi/
│   └── index.html      # xAPI-enabled version
├── README.md
├── LICENSE
└── .gitignore
```

## Tech notes

Vanilla HTML, CSS, and JavaScript. No frameworks, no external runtime dependencies, no browser storage. State is held in memory for the session.

## Status & context

Prototype for an internal Elsevier Customer Learning project. Under active iteration; structure is approved in principle, with refinements ongoing.

## License

Proprietary — see [LICENSE](LICENSE).
