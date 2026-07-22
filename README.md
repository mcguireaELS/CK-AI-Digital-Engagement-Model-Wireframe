# ClinicalKey AI — Customer Hub (Wireframe)

An interactive, **low-fidelity** wireframe of a self-service onboarding and enablement hub for ClinicalKey AI customers — built for customers in a self-support tier who don't have a dedicated customer success manager.

It is a single, self-contained HTML file with no dependencies and no build step. It is intentionally grayscale and un-branded: the goal at this stage is to align on **structure and flow**, not visual design. Design and branding come later.

## Live demo

Once GitHub Pages is enabled for this repository (Settings → Pages → deploy from the `main` branch, root), the wireframe is served at:

```
https://elsevier-health.github.io/REPO-NAME/
```

Replace `REPO-NAME` with this repository's name.

## What it demonstrates

- **Two guided paths** — an *Administrator* (deployment) path and a *User* (everyday value) path that share a common intro, then fork.
- **Inline learning model** — each asset (video, guide, quick sheet) is presented in place as part of the journey rather than as a link out.
- **Progress and resume** — a step rail tracks where the learner is and what's next.
- **Browse by concern** — a collapsible "Looking for something specific?" index that deep-links to the relevant step, for learners who just need one thing.
- **Per-section and full-PDF downloads** — light portability without breaking the journey.
- **Design notes** — toggle **Design notes** in the upper-right corner to see the rationale behind each decision.

## View locally

Open `index.html` in any modern browser. No server required.

## Embed in another page (e.g., WordPress)

Because interactive JavaScript runs inside the hosted page, you can embed the whole experience with a single iframe — no custom scripts needed on the host page:

```html
<iframe
  src="https://elsevier-health.github.io/REPO-NAME/"
  title="ClinicalKey AI Customer Hub wireframe"
  style="width:100%;height:900px;border:0;"
  loading="lazy">
</iframe>
```

Adjust `height` to suit the page.

## Repository structure

```
.
├── index.html      # the wireframe (single self-contained file)
├── README.md
├── LICENSE
└── .gitignore
```

## Tech notes

Vanilla HTML, CSS, and JavaScript in one file. No frameworks, no external runtime dependencies, no browser storage. State is held in memory for the session.

## Status & context

Prototype for an internal Elsevier Customer Learning project. Under active iteration; structure is approved in principle, with refinements ongoing.

## License

Proprietary — see [LICENSE](LICENSE).
