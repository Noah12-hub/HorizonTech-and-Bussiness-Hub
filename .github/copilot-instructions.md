<!--
This file guides AI coding agents when working on the Horizon Tech static site.
Keep it short, actionable and tied to what is discoverable in the repo.
-->

# HorizonTech — Copilot Instructions

Summary
- This repository is a small, static marketing site for "Horizon Tech & Business Hub" composed of a single HTML file (`HorizonTech.html`) and a single stylesheet (`horizontech.css`). There is no build system, package manifest, or automated tests.

Quick goals for an AI agent
- Preserve content and contact details unless the user explicitly asks to change them.
- Favor non-breaking edits: update class names in both HTML and CSS together, and keep image filenames intact unless assets are provided.

What to know (big picture)
- The project is a single-page static site (sections: home/hero, services, about, contact, footer). The HTML contains inline navigation links and a small script that sets the current year.
- Layout and styling are in `horizontech.css`. Note: there are a few naming mismatches between HTML and CSS (e.g., HTML uses `class="hero"` but CSS contains `.hero-section`). Always search both files when changing a section.
- Images are referenced directly from the repo (examples: `noah.jpg.jpg`, `africa.jpg`, `Business.jpg`, `pexels.jpg`, `african.jpeg`, `art.png`). If you add or rename assets, update `src` attributes in the HTML and any background-image in CSS.

Developer workflows & preview
- No build step. Preview locally by opening `HorizonTech.html` in a browser. On Windows PowerShell you can run:

```powershell
Start-Process .\HorizonTech.html
```

- If you prefer live reload while editing, use the editor Live Server extension (VS Code) or any simple static server. Do not add Node/tooling unless the user requests it.

Project-specific patterns and gotchas
- Class-name mismatches: before editing a component, grep for its class in both files (e.g., search for `hero` and `hero-section`). Align names in both files or update the other file accordingly.
- Duplicate or misspelled filenames: `noah.jpg.jpg` looks accidental — confirm asset names before changing.
- Minimal JS: only a single inline script updates the footer year. Avoid adding global JS frameworks; prefer small, local scripts if needed.
- Accessibility: navigation anchors are plain anchors. When adding interactive widgets, follow semantic HTML and keep anchor hrefs working.

Examples
- To change the hero headline text: edit `HorizonTech.html` inside the `<section class="hero" id="home">` block.
- To replace the hero background image: either set an `<img>` inside the hero or edit `horizontech.css`'s hero background (search for `hero-section`/`hero`) and update the `url('...')` value.

Integration & external links
- External services used in the markup:
  - WhatsApp links using `https://wa.me/<number>` (multiple places).
  - `mailto:` link for contact email.
Do not change these endpoints without user consent.

When editing
- Keep formatting consistent with existing files (minimal reflow). This is a tiny repo — a single focused commit per change is preferred.
- When renaming classes or assets, include a short commit message explaining the coordinated changes (e.g., "align hero class name between HTML and CSS; rename hero-section -> hero").

Files to check first
- `HorizonTech.html` — primary content and structure
- `horizontech.css` — look for naming mismatches and variable usage (CSS custom properties at top)

Ask the user when uncertain
- Confirm any change to contact information, phone numbers, or WhatsApp links.
- Confirm image renames or additions (provide the intended file names).

If you need to scaffold tests or a build system
- Ask the user. This repo currently has no npm/python tooling and likely doesn't need one for simple edits.

End of instructions — ask the user if anything above is unclear or if they want stricter guardrails (e.g., block edits to contact details).
