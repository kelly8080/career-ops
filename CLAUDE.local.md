# Local context: Álvaro's setup

CLAUDE.md and AGENTS.md are system files that `update-system.mjs` replaces. This file is not, so the personal setup is loaded from here in every session, not only when a career-ops mode runs.

## Always loaded

@modes/_custom.md
@modes/_profile.md

## CV flow

`output/all_info.json` -> `output/cv.md` -> CVs, always in that direction. The root `cv.md` is an exact copy of `output/cv.md`, kept because the career-ops scripts read the CV only from the root; it is never edited on its own (`preprint.rules` 0.3b).

1. `output/all_info.json` holds every confirmed fact, in the structure fixed by `output/all_info.schema.json`. New facts, including ones stated in chat, go here first; then run `node output/validate_all_info.mjs --cv output/cv.md --mirror cv.md`.
2. `output/cv.md` is built from the archive and the project's conventions following `preprint.rules`. Part 1 holds the common rules (selection, structure, content, checks); Part 2 is the flow from `output/all_info.md`, Part 3 the flow from `output/all_info.json`. Only one archive is active at a time: today the JSON (Flow B). Parts 1-3 stop at `output/cv.md` (copied to the root `cv.md`); Part 4 holds the one-page cuts applied when a CV is generated.
3. For now every CV is a one-page PDF in two versions, styled (`photo-right`) and ATS (`data/templates/ats-1page/`). Each is generated from `output/cv.md`, following the project's rules (`modes/pdf.md`), the one-page cuts in `preprint.rules` Part 4 and the agent's own judgment, with the PDF settings and file names in `modes/_custom.md`.

## User files

- `output/all_info.json`: archive of every confirmed fact, each with its sources. Items in `pending_confirmation` must not appear in any CV or application until confirmed, and items with `cv_policy: "excluded"` never do. Private sections are listed in `meta.private_sections`.
- `output/all_info.schema.json`: the JSON Schema for it (schema 1.2.0). `output/validate_all_info.mjs`: validates the JSON and, with `--cv output/cv.md`, checks each job against it; with `--mirror cv.md`, that the root copy is identical.
- `preprint.rules`: rules for turning the fact archive into `output/cv.md`, with one flow for `output/all_info.md` and one for `output/all_info.json`, plus the one-page cuts (Part 4).
- `output/cv.md`: curated source for every CV, built by `preprint.rules`. `cv.md` (root): its exact copy, the only CV file the career-ops scripts read. It is not limited to one page; the one-page budget (`cv.max_pages: 1`) applies when the one-page CV is generated.
- `config/profile.yml`: identity, targets, compensation, CV template (`photo-right`).
- `LOG_ARIOBOO.md`: history of every customization. Add a dated entry when the setup changes.
