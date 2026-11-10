# LOG_ARIOBOO: Personal Changes to career-ops

Everything adapted to Álvaro's way of working since the repository was downloaded (career-ops v1.39.0). Last updated: 2026-11-05.

No system file has been edited. All changes live in user-layer files, which `node update-system.mjs` does not overwrite.

## Working preferences

| Rule | Where it is stored |
|------|--------------------|
| Chat in Spanish. All documents, technical material, the CV and anything company-facing in English, never mixed. Spanish versions only on specific request. | Agent memory; `language.output: en` in `config/profile.yml` |
| Full evaluations run only on explicit request, for that specific posting, at the end of the process. | `modes/_custom.md`, agent memory |
| Contact by professional email first, phone second. | `modes/_profile.md` |

## CV

- `cv.md` created from the LinkedIn profile, then merged with `documents/CV_arioboo.pdf` through `intake`.
- Where the two sources disagreed, the PDF was used for job titles, the Deuser employer name, the freelance end date, the IAC and UCM tutor dates, and the bachelor's end year.
- The Deuser end date stays Aug 2021, as confirmed by Álvaro.
- Kept from LinkedIn: PREDCAM, H2O, PyTorch, and Python for the Deuser analysis.
- Added: GitHub, website, phone, birth year, thesis titles, specialties, skills, Coursera courses, chess achievements, Chess-analyzer.
- German and French set to Beginner.
- Personality bullets reduced to one line in the summary.
- The unfinished Big Data & Business Analytics MSc is deliberately left out.

## CV PDF

- One-page limit: `cv.max_pages: 1`.
- Photo: `documents/photo.jpg`, set as `candidate.photo`.
- Custom template: `data/templates/cv-template.photo-right.html`, a copy of the compact template with the photo in the top-right corner. It is the default.
- Current general CV: `output/cv-alvaro-rioboo-general-2026-11-05.pdf`, A4.
- Email comes first in the contact line. This is set by hand in each CV payload, because the builder puts the phone first.
- Recommendation noted: use a version without the photo for UK, US and Irish applications.

## Profile (`config/profile.yml`)

- Target roles: Data Scientist, Data Analyst, AI Engineer, Machine Learning Engineer, Deep Learning Engineer, all primary, all Junior level.
- Years of experience: 1.
- Target compensation: 30,000-50,000 EUR gross per year. No minimum set.
- Location: Córdoba, Spain. Timezone: Europe/Madrid.
- Spend tier: standard.
- Removed the template's example `language_learning` block.

## Targeting (`modes/_profile.md`)

- Archetypes, adaptive framing and cross-cutting advantage rewritten from the CV.
- Seniority policy added: junior is the primary target; mid and senior stay in scope when the salary matches.
- Still template text: exit narrative, portfolio, comp targets, negotiation scripts, location policy.

## Scanner (`portals.yml`)

- Title keywords: the target roles, ML Engineer, Machine Learning Engineer, Applied Scientist, and the Spanish titles Científico de Datos, Analista de Datos, Ingeniero IA.
- Role families added so varied titles still match: Machine Learning, Deep Learning, MLOps, Computer Vision, NLP, LLM, Data Science, Inteligencia Artificial, Aprendizaje Automático, Research Engineer. A semantic review of filtered titles added Analytics Engineer, BI Analyst, AI Consultant, AI Research, ML Platform, AI Platform Engineer, AI Business Analyst.
- Locations allowed: Spain and its main cities, Switzerland, Ireland, Iceland and the United States.
- Experience filter on: `stretch_years: 2`, `action: label`. Postings asking for more than 3 years are marked, not removed.
- Removed "Junior" from the title exclusions, and made Junior the only `seniority_boost` prefix.
- Posting age limit raised from 45 to 90 days.
- Added boards: IQM, Alice & Bob, IonQ, PsiQuantum, Rigetti, Cabify, Wallapop, Jobandtalent, Typeform, Ebury.
- The 30 enabled template search queries are off, replaced by 9 queries for Spain data roles, Accenture, Indra/Minsait, banks, consultancies and quantum companies.

## Search state

- `data/pipeline.md` holds 1163 pending postings. None has been evaluated. Provisional star ratings are in `data/pipeline-stars.md`.
- Six leads await confirmation on employer sites: Accenture, EY, BCG X, Indra, NTT DATA, Multiverse Computing.
- The original LinkedIn posting (`jobs/view/4482626188`) still needs its text pasted.

## Other

- Playwright plugin installed.
- `CAREER_OPS_CLI=claude` saved to `.env`.

## Star rating system

Configured in `modes/_profile.md`. Stars rate each posting on location (30%), work mode (20%), salary (20%), sector (15%; insurance is 1 star) and contract (15%). Default level: 3 stars; 5 stars is the strictest. They are separate from the 1-5 evaluation score.

## 2026-11-10: LinkedIn review and all_info.md

- `all_info.md` created at the repo root: the complete archive of confirmed facts, with sources, source differences and pending items. Built from `output/ALL.md`, the public LinkedIn page and the skills list Álvaro pasted. Excluded from git locally (`.git/info/exclude`).
- `cv.md` stays the curated source for the one-page CV. Rule recorded in `modes/_custom.md`: facts go to `all_info.md` first and move into `cv.md` only on confirmation.
- Added to `cv.md`: C1 Advanced (Cambridge, 2022); Coursera courses corrected to "Machine Learning" (single course) and dated 2019; BSc thesis title; Córdoba champion merged with the Andalusian title in one line.
- Kept in `all_info.md` only: Coursera credential IDs, BSc grades (TFG 8.5, GPA 6.79, Classical Electrodynamics 9.9, Astrophysics 9.0), chess monitor titles, División de Honor clubs (2010 – 2019), RSEF membership (2016 – 2018), full LinkedIn skills list.
- Confirmed: BSc ended 2017.
- New one-page CV: `output/cv-alvaro-rioboo-general-2026-11-10.pdf`, A4, email first.
- To fix on LinkedIn: BSc end (2017), IAC dates, División de Honor end (2019), RSEF end (2018), About section's mention of current contract work.
