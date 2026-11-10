# LOG_ARIOBOO: Personal Changes to career-ops

Everything adapted to Álvaro's way of working since the repository was downloaded (career-ops v1.39.0). The sections before the first dated entry describe the setup as of 2026-11-05; the dated entries below record every later change and override them where they differ. Last updated: 2026-11-10.

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

## 2026-11-10: Setup review

- `CLAUDE.local.md` created: loads `modes/_custom.md` and `modes/_profile.md` in every session. CLAUDE.md and AGENTS.md stay untouched, since updates replace them.
- `modes/_custom.md`: added the chat-language rule (Spanish chat, English documents) and the email-first rule for CV payloads.
- `config/profile.yml`: `contact_preferences.preferred_channel: email`.
- Chat-language rule saved to agent memory (it was listed above as stored there, but was missing).

## 2026-11-10: CV, PDF and LinkedIn alignment

- Freelance confirmed: "Freelance Data Scientist", via Freelancer, Upwork and Fiverr, remote. Updated in `cv.md` and `all_info.md` (pending item removed).
- PDF regenerated (`output/cv-alvaro-rioboo-general-2026-11-10.pdf`, A4, one page): new freelance title, contact line with uniform separators and email first. Layout otherwise unchanged, by choice.
- The CV payload now lives in `output/cv-alvaro-rioboo-general.json`. Rebuild with `build-cv-html.mjs` and the `photo-right` template, then move the email link before the phone in the HTML.
- LinkedIn follows `cv.md` and `all_info.md`. The paste-ready texts were drafted, then deleted at Álvaro's request.

## 2026-11-10: One fact archive

- `all_info.md` and `output/ALL.md` merged into a single file, `output/all_info.md`. Both old files are gone.
- Added from `ALL.md`: the LinkedIn About text and positions table (with employment types), the Twitter handle, job search context (years of experience, salary history, no relocation, preference order, companies of interest), gaps and missing information, working rules, and the 2026-11-05 search-state snapshot.
- Added from `documents/CV_arioboo.pdf`: the "Experienced in" and "Looking to" lines.
- New source-difference rows: Deuser tools, UCM tutor employment type, Bachillerato, Coursera ML course name and date, Coursera DL date.
- Paths updated in `modes/_custom.md`, `CLAUDE.local.md`, agent memory and `.git/info/exclude`.
- UCM tutor employment type confirmed: apprenticeship (`output/all_info.md`).

## 2026-11-10: LinkedIn PDF export

- `documents/linkedin/Profile.pdf` integrated into `output/all_info.md` as source `LinkedIn PDF`. It is the Spanish-language version of the profile; the earlier cached copy was the English one.
- New facts: postal address and account email (contact info), "no unsolicited calls", satellite images at Deuser, ETL/clustering/validation in freelance work, all first-year groups and self-initiated seminars at UCM, Spanish titles and top skills.
- The pending item "fresh LinkedIn export" is closed. The LinkedIn fix list now covers both language versions.
- Mobile number and street address removed from every project file: `cv.md`, `output/all_info.md`, `config/profile.yml` (`phone: ""`), the CV payload, HTML and PDF (regenerated, one page, A4). The obsolete 2026-11-05 PDF was deleted and its `data/pdf-index.tsv` row removed. `documents/linkedin/Profile.pdf` deleted too, after its content was integrated. Still present: Claude Code session transcripts, `~/Documents/CVs/` and the LinkedIn profile itself.

## 2026-11-10: CV rules and English institution names

- `cv_preprogram_lint.rules` created at the repo root: the step-by-step process from `output/all_info.md` to the one-page PDF CV. Its never-in-the-CV list holds only sensitive data (phones, secondary emails, addresses) and, for now, the Big Data MSc.
- MSc GPA added to `output/all_info.md`: 6.98/10 (BSc stays 6.79/10).
- Institution names standardized in English with acronym in `cv.md` and `output/all_info.md`: University of Córdoba (UCO), Canary Islands Institute of Astrophysics (IAC), Complutense University of Madrid (UCM), University of La Laguna (ULL). The CV payload, HTML and PDF still carry the old names until the next build.

## 2026-11-10: Bachillerato in the CV

- Bachillerato (Santa Victoria, Córdoba, 2010 – 2012) added to the Education section of `cv.md` at Álvaro's request. It had been left out earlier without asking him; `output/all_info.md` now records the decision as his.
- The CV payload, HTML and PDF do not include it yet, until the next build. One-page fit to be checked then.

## 2026-11-10: Fixed name for the one-page CV PDF

- The general one-page CV PDF is now `output/CV_arioboo_1pager.pdf`, with no date; each build replaces it. Recorded in `modes/_custom.md` (Output Preferences), `cv_preprogram_lint.rules` (rule 8.1) and `output/all_info.md` (Working rules, Search state). Tailored CVs keep `output/cv-alvaro-rioboo-{company}-{YYYY-MM-DD}.pdf`.
- The old `output/cv-alvaro-rioboo-general-*.pdf` files no longer exist; Álvaro renamed the last one to `output/CV_arioboo_1pager_old.pdf`. The next build creates `output/CV_arioboo_1pager.pdf`.
- Tailored CV PDFs renamed too: `output/CV_arioboo_1pager_{company}.pdf`, no date (`modes/_custom.md`, `cv_preprogram_lint.rules` rule 8.1). Payload and HTML names (`output/cv-alvaro-rioboo-*.json/.html`) are unchanged.

## 2026-11-10: One-page CV rebuilt

- `output/CV_arioboo_1pager.pdf` generated from `cv.md` following `cv_preprogram_lint.rules` (A4, one page, `photo-right`, email first). The payload now carries the English institution names with acronym. All checks passed; `config/cv-facts.json` does not exist, so the forbidden-phrase checks did not run.

## 2026-11-10: Summary and Data & ML skills

- Summary now opens with an AI sentence: "AI practitioner who builds and trains deep learning models, from CNN image models in industry to a U-Net for astrophysical simulations." Built only from the Deuser and IAC entries.
- Data & ML skills: dropped Machine Learning and Data Analysis (repeated elsewhere); added pandas and NumPy, stated by Álvaro and recorded in `output/all_info.md`.
- `output/CV_arioboo_1pager.pdf` rebuilt: one page, all checks passed.

## 2026-11-10: CV flow rescoped

- `cv_preprogram_lint.rules` now covers only `output/all_info.md` -> `cv.md`: sources, selection, the structure career-ops scripts need, content rules, the `cv.md` check and the one-page budget. The payload, HTML, fact-gate and PDF stages were removed from it; the PDF belongs to the `pdf` mode.
- New content rules written into it: the Summary opens with an AI sentence, and the Data & ML line does not repeat generic terms (Machine Learning, Data Analysis).
- `modes/_custom.md`: new "CV flow" workflow and "PDF settings" (A4, one page, `photo-right`, photo rule, payload and HTML names), next to the existing file-name and email-first preferences.
- `CLAUDE.local.md`: new "CV flow" section, and `cv_preprogram_lint.rules` listed under user files.

## 2026-11-10: cv.md is the source of every CV

- Every CV (the one-page general CV, tailored CVs and any other version) is generated from `cv.md`, following the project's rules and the agent's own judgment. `cv.md` is no longer limited to one page: the one-page budget and its cut order now apply per generated CV, never as cuts to `cv.md`.
- Updated in `cv_preprogram_lint.rules` (intro, 0.2, 0.5, 1.1; Stage 5 folded into the final section), `modes/_custom.md` (house rule and CV flow), `CLAUDE.local.md`, `output/all_info.md` (intro) and agent memory.

## 2026-11-10: One-page ATS CV

- For now every CV is a one-page A4 PDF in two versions from the same payload: styled (`photo-right`, `output/CV_arioboo_1pager.pdf`) and ATS (`output/CV_arioboo_1pager_ats.pdf`; tailored: `_{company}_ats.pdf`). Recorded in `modes/_custom.md` and `CLAUDE.local.md`.
- New user template pack `data/templates/ats-1page/`: a copy of the built-in `templates/ats` (single column, no photo) with tighter spacing, short fields sharing a line, email before phone, Arial only, 0.5in margins. The built-in one ran to two pages. `cv-templates.mjs lint`: 0 findings.
- First ATS build: one page, `verify-ats.mjs` 95/100 (A). `ats-payload.mjs` reported 5 lints (department in the UCO title; parentheticals UCO, IAC, UCM and the freelance platforms in the company field), shown to Álvaro, not applied.

## 2026-11-10: ATS lint fixes

- Fixed the five `ats-payload.mjs` lints in `cv.md` and the payload, so both PDFs carry them: Experience headers without acronyms (University of Córdoba, Canary Islands Institute of Astrophysics, Complutense University of Madrid); UCO title reduced to "Data Scientist Assistant", with the KDIS group and Numerical Analysis Department moved into its first bullet; freelance employer "Self-employed" (plain "Freelance" triggered a new lint), with Freelancer, Upwork and Fiverr moved into its first bullet. Education keeps the acronyms.
- New rule 3.9 in `cv_preprogram_lint.rules`, rule 3.1 adjusted; decisions noted in the "Source differences" table of `output/all_info.md`.
- Rebuilt: `output/CV_arioboo_1pager.pdf` and `output/CV_arioboo_1pager_ats.pdf`, one page each. `ats-payload.mjs`: 0 findings. `verify-ats.mjs` on the ATS copy: 95/100 (A).

## 2026-11-10: Fuller cv.md, keyword bullet, skills reordered

- Added to `cv.md` with Álvaro's confirmation, from `output/all_info.md`: satellite images (Deuser); third UCO bullet (diagnostic techniques for model upgrades); third freelance bullet (model validation, clustering, georeferencing, ETL, web scraping, APIs for data mining and economic data).
- Summary is now two bullets: the summary text, then "Keywords:" with 16 ATS keywords (payload `competencies[]`). Skills reordered: Programming, Data & ML, Databases & Cloud, Languages, most-requested items first.
- Templates: `photo-right` and `ats-1page` render the Summary as a list with the keywords comma-separated in it; the separate Core Competencies block was removed from both. `ats-1page` also puts company, place and dates on one line and uses line-height 1.35. The ATS copy no longer goes through the `ats-payload.mjs` fold (lints still run).
- Rules: `cv_preprogram_lint.rules` 3.5 and 3.6 updated; `modes/_custom.md` ATS step updated.
- Rebuilt both PDFs, one page each. `verify-ats.mjs` on the ATS copy: 95/100 (A). `ats-payload.mjs`: 0 lint findings.

## 2026-11-10: Full rebuild of cv.md and the one-pager

- `cv.md` checked against every rule in `cv_preprogram_lint.rules`. One fix: the Deuser title carried its department (rule 3.9), so it is now "Junior Data Scientist", with the Software Department in its first bullet. Noted in rule 3.9 and in `output/all_info.md`.
- The payload is now regenerated in full from `cv.md` instead of patched, so the two cannot drift.
- Rebuilt `output/CV_arioboo_1pager.pdf` and `output/CV_arioboo_1pager_ats.pdf`, one page each. Title, structure and fact checks passed; `ats-payload.mjs` 0 lints; `verify-ats.mjs` 95/100 (A) on the ATS copy.

## 2026-11-10: Merged summary, Keywords section at the end

- Summary rewritten as one paragraph joining the physicist framing and the AI sentence: "Physicist and AI practitioner specialized in computational astrophysics, building and training deep learning models, ...".
- Keywords moved out of the Summary into a last `## Keywords` section in `cv.md`. Both templates render it after Skills in a soft grey (#a3a8ae, 9-9.5px); payload `sections.competencies: "Keywords"`. `ats-1page` page margin 0.45in to keep one page.
- Rules: `cv_preprogram_lint.rules` 2.2, 3.5, new 3.5b, 3.6; `modes/_custom.md` ATS note.
- Rebuilt both PDFs, one page each; `verify-ats.mjs` 95/100 (A) on the ATS copy.

## 2026-11-10: Skills and Keywords ordered by target role

- New rule 3.10 in `cv_preprogram_lint.rules`: Skills items and Keywords are reordered (never added or removed) for the posting being applied to; without a posting, by the closest archetype; default Data Scientist. `cv.md` always holds the Data Scientist order; tailored CVs reorder in their payload. Rule 3.6 and the final section point to it.
- `cv.md` and both one-page PDFs now use the Data Scientist order (statistics, predictive modelling, EDA and model validation first; Python, R, SQL; scikit-learn, pandas, NumPy first).

## 2026-11-10: Rebuild with all current rules

- `cv.md` re-checked against `cv_preprogram_lint.rules` (sections and order, em dashes only in job headers, titles without department, one-paragraph Summary, Keywords last, Data Scientist order): no changes needed.
- Payload regenerated in full from `cv.md`; both one-page PDFs rebuilt. Title, structure and fact checks passed, `ats-payload.mjs` 0 lints, `verify-ats.mjs` 95/100 (A) on the ATS copy.

## 2026-11-10: Shorter Summary

- Removed the project-specific clause (CNN image models, U-Net) from the Summary at Álvaro's request. It now reads: "Physicist and AI practitioner specialized in computational astrophysics, applying data analysis and machine learning across scientific and industrial projects. Detail-oriented, organized and driven team player, committed to delivering high-quality work." Rule 3.5 now keeps the Summary general, with project detail in Experience.
- Both one-page PDFs rebuilt; checks passed; ATS copy 95/100 (A).

## 2026-11-10: Default summary

- Rule 3.5 in `cv_preprogram_lint.rules` now holds the default summary verbatim (the current `cv.md` text). Tailored CVs start from it and change it only slightly (target role, posting terms `cv.md` already backs), same length and structure, in their payload only.

## 2026-11-10: Rebuild with the default summary

- `cv.md` re-checked against `cv_preprogram_lint.rules`, including the new default summary in rule 3.5: no changes needed.
- Payload regenerated from `cv.md`; both one-page PDFs rebuilt. All checks passed; ATS copy 95/100 (A).

## 2026-11-10: Department as a typed field

- `output/all_info.md` Experience now opens with one table: Employer | Role | Department | Place | Dates | Type. Department: UCO "KDIS group (Numerical Analysis Department)", Deuser "Software Department", the rest "-". Per-job sections keep only bullets and notes; repeated titles, dates and places removed, and the source-difference rows trimmed to the decision.
- `cv.md`: optional "Department: ..." line after the dates line (left out for "-"); the department text was removed from the UCO and Deuser bullets. Payload: `experience[].context`.
- Rules: 2.4 defines the Department line, 3.2 points to the Experience table, 3.9 keeps the department out of titles and bullets; the redundant "Today:" lists in 3.9 and 3.10 removed.
- `ats-1page` experience partial: department line after "company | place | dates". Both PDFs rebuilt, one page each; checks passed, ATS 95/100 (A).

## 2026-11-10: Fact archive moved to JSON

- `output/all_info.md` replaced by `output/all_info.json` (schema 1.0.0), at Álvaro's request. All content carried over; the "Working rules" section was dropped because it only repeated `modes/_custom.md`, `modes/_profile.md` and `config/profile.yml`.
- `output/all_info.schema.json`: JSON Schema (draft 2020-12). Conventions: snake_case keys and enums; dates "YYYY", "YYYY-MM" or "YYYY-MM-DD"; periods {start, end}; null for a missing value (never "-" or ""); every fact is {text, sources} with source pdf | linkedin | linkedin_pdf | stated; `cv_policy` allowed | excluded | needs_example; unique ids. Department is `experience[].department` (null when there is none).
- `output/validate_all_info.mjs`: zero-dependency validator (types, enums, patterns, unknown keys, duplicate ids, cross-references, placeholder strings). With `--cv cv.md` it checks each cv.md job against its experience entry (employer, role, Department line, dates). Tested against a broken copy of each.
- Rules updated for the JSON: `cv_preprogram_lint.rules` (0.1, new 0.1b and 4.1b, 0.6, 1.1-1.8, 2.4, 3.1-3.3, final section), `modes/_custom.md`, `CLAUDE.local.md`, `.git/info/exclude`, agent memory. Earlier log entries still mention `all_info.md`; they are history.

## 2026-11-10: preprint.rules, two archive flows

- `cv_preprogram_lint.rules` renamed to `preprint.rules` and reorganized: Part 1 common rules (sources, selection, structure, content, checks) written against archive concepts in [brackets]; Part 2 Flow A, cv.md from `output/all_info.md` (where each concept lives in the Markdown, manual check); Part 3 Flow B, cv.md from `output/all_info.json` (schema conventions, JSON paths, `validate_all_info.mjs --cv cv.md`); Part 4 generating CVs. Rule 0.2: only one archive is active at a time, today the JSON; if both exist, ask. Content rules renumbered 3.1-3.11 in reading order (ordering rule is now 3.8).
- References updated in `CLAUDE.local.md` and `modes/_custom.md`.
- Rebuild: `cv.md` passed every Stage 4 check (validator, structure, default summary, no excluded or needs-example items, at most three bullets) with no changes. The CV payload, missing from `output/`, was regenerated from `cv.md`; both one-page PDFs rebuilt, all checks passed, ATS 95/100 (A).

## 2026-11-10: covid19_dashboard in, Chess-analyzer out

- `output/all_info.json`: Chess-analyzer project and its gap removed, at Álvaro's request. New project `covid19_dashboard` (github.com/arioboo/covid19_dashboard): COVID-19 dashboard for Spain from the Narrativa COVID-19 Tracking API, pandas, matplotlib and an interactive Bokeh HTML output, Sep 2020 – Feb 2021. Description and stack read from the public repo; not yet in `cv.md`, pending Álvaro's confirmation.
- `cv.md`: Projects section removed (Chess-analyzer was its only entry). `preprint.rules` 1.8 and the cut list in Part 4 updated.
- Both payloads cleared of the project; both one-page PDFs rebuilt. Checks passed, ATS 94/100 (A). Earlier entries still mention Chess-analyzer; they are history.
- Same day, confirmed by Álvaro: `covid19_dashboard` added to `cv.md` under ## Projects (link, stack, 2020 – 2021). Both payloads carry a one-line version so the ATS copy stays on one page. The one other commit author in the repo is also Álvaro; not mentioned anywhere. `output/CV_arioboo_1pager_old.pdf` deleted. Both PDFs rebuilt, one page each; ATS 95/100 (A).

## 2026-11-10: Keywords go first when the one-pager overflows

- `preprint.rules` Part 4: if a one-page CV runs past one page, the agent first drops keywords from the end of the list (least relevant by rule 3.8) until it fits, or removes the section, without asking, and reports what it dropped. Same cut in the ATS copy; `cv.md` keeps the full list. The ask-first cut list (third bullets, skills, projects, awards, UCM tutor) applies only if it still does not fit.

## 2026-11-10: Rules review

- `preprint.rules`: the intro and the Part 4 title now say Part 4 holds the house rules for generating CVs; rule 3.8 names the Part 4 Keywords cut as its one exception; rule 3.6 accepts Projects as backing for a keyword; the Keywords cut applies to both copies, which share one payload.
- `modes/_custom.md`: the contact-line rule no longer mentions a phone (none goes in a CV, rule 1.3).
- One-pager rebuilt under the new rule: full covid19_dashboard line (description + stack) restored in both payloads; the ATS copy overflowed, so the last 6 keywords were dropped from both (Predictive Maintenance, Deep Learning, Neural Networks (CNN, U-Net), Computer Vision, Image Processing, GPU Computing (CUDA)). `cv.md` keeps all 16. Both PDFs one page; checks passed.

## 2026-11-10: Rules review, second pass

- `CLAUDE.local.md` and `modes/_custom.md` no longer say the rules end at `cv.md`: Parts 1-3 do, Part 4 holds the one-page cuts.
- `modes/_custom.md`: `-ats.json` is an exact copy of the main payload, rewritten with it on every build, never edited on its own.
- `preprint.rules` Part 4: a one-page CV fits only through the listed cuts; shortening or rewording text to save space is a cut and needs asking. Keywords cut order: generic keywords first (today Data Wrangling, ETL, Data Mining, unless the posting asks for them), then the rest from the end.
- One-pager rebuilt: dropped ETL, Data Wrangling, Data Mining, GPU Computing (CUDA), Image Processing, Computer Vision, Neural Networks (CNN, U-Net). Deep Learning stays. Both PDFs one page, payloads identical, ATS 95/100 (A).

## 2026-11-10: Rules review, third pass

- `preprint.rules`: subtitle now covers the one-page cuts; rule 3.8's exception covers all Part 4 cuts (Keywords and Skills) in Part 4's order; Part 4 orders fitting as the Keywords cut first, then the ask-first list, with shortening or rewording a line as an ask-first cut proposable anywhere in that list, never before the Keywords cut.
- `CLAUDE.local.md` step 3 now names the Part 4 one-page cuts.

## 2026-11-10: Rules review, fourth pass

- `preprint.rules` Part 4: generic keywords redefined as general data-handling methods (as opposed to modelling or analysis methods), so they still meet rule 3.6; long line rewrapped.
- `modes/_custom.md` CV flow step 3 and `CLAUDE.local.md` (User files) now name the Part 4 one-page cuts.
- `config/profile.yml`: `page_format: a4` and `cv.strict_pages: true`. PDFs are built without `--format`/`--max-pages` flags; an overflowing render no longer replaces the good PDF (the draft goes to `.overflow.pdf`).
- `cv.md`, confirmed by Álvaro: keyword "GPU Computing (CUDA)" renamed "GPU Computing"; CUDA added to Skills, Data & ML line (backed by the IAC entry and the archive's CUDA toolkit).
- One-pager rebuilt: same 7 keywords dropped as before (ETL, Data Wrangling, Data Mining, GPU Computing, Image Processing, Computer Vision, Neural Networks (CNN, U-Net)). Both PDFs one page, A4, payloads identical, checks passed.

## 2026-11-10: Rules review, fifth pass

- `preprint.rules` Part 4: a generated CV only selects and orders, except the tailored summary (rule 3.5) and the ask-first shortening; the Skills-category cut never removes Languages.
- Same pass: the one-way-flow rule now names the tailored summary (rule 3.5) as the one wording fixed in its payload; Part 4 lines rewrapped.

## 2026-11-10: Availability and work authorization

- Stated by Álvaro: available to start within 1 to 3 weeks; authorized to work in the European Union, not yet anywhere else (North America included).
- `output/all_info.json` (schema 1.1.0): new `job_search.availability` and `job_search.work_authorization`, both private. The availability gap is closed; the work-authorization gap now asks only about relocating for a strong offer (`relocation_for_strong_offer`).
- `output/all_info.schema.json` bumped to 1.1.0 for the two fields; version references updated in `preprint.rules` (B.1) and `CLAUDE.local.md`.
- `preprint.rules` 1.3: nothing from a [private section] goes into `cv.md` (job search conditions, gaps, search state, pending items); the concept is mapped in A.2 and B.2. `cv.md` unchanged.
- Validator: exit 0.

## 2026-11-10: config/profile.yml aligned with the archive

- `narrative.headline`: "Data Scientist | Astrophysicist", the decided headline (it held the long LinkedIn one).
- `location`: `authorized_in: ["European Union"]`, `needs_sponsorship: true` (evaluations no longer treat non-EU roles as needing no visa), `visa_status` in words.
- `cover_letter.notice_period_days: 21` (start within 1-3 weeks; it held the template's 30). `primary_domain` placeholder removed, so the cover mode infers it from `cv.md`.
- `validate-profile.mjs`: no structural problems.

## 2026-11-10: cv.md check and one-pager rebuild

- `cv.md` checked against `preprint.rules` Stages 1-3, including the new private-section rule: no changes needed. Validator exit 0; doctor finds the Experience section.
- Payload regenerated from `cv.md` with all 16 keywords; the ATS copy overflowed, so the Part 4 cut dropped ETL, Data Wrangling, Data Mining, GPU Computing, Image Processing, Computer Vision and Neural Networks (CNN, U-Net) from both copies. `cv.md` keeps all 16.
- Rebuilt `output/CV_arioboo_1pager.pdf` and `output/CV_arioboo_1pager_ats.pdf`: one page each, A4, payloads identical. Title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: LinkedIn PDF deleted again

- `documents/linkedin/Profile.pdf` was back on disk (saved 18:15, after the earlier deletion) with the phone number in it. Its content matched the archive's `linkedin_pdf` transcription, so nothing was lost. Deleted at Álvaro's request; `output/all_info.json` (`meta.sources`) was already correct.

## 2026-11-10: output/cv.md is the CV source

- At Álvaro's request, `output/cv.md` is now the file `preprint.rules` builds from `output/all_info.json`, and the one every CV is generated from. It had sat empty while the root `cv.md` was used.
- The root `cv.md` stays, as an exact copy of `output/cv.md`, because the career-ops scripts (fact gate, cv-title-check, verify-cv-structure, doctor) read the CV only from the root. It is rewritten with `cp output/cv.md cv.md` on every change and never edited on its own; a symlink was not used, because `add-entry.mjs` writes with an atomic rename that would replace it.
- `output/validate_all_info.mjs`: new `--mirror cv.md` option, which fails while the root copy differs. Check command: `node output/validate_all_info.mjs --cv output/cv.md --mirror cv.md`.
- New `output/build_payload.mjs`: builds the CV payload from `output/cv.md` with every keyword; the Part 4 cuts are applied to it afterwards.
- Rules updated: `preprint.rules` (0.3, new 0.3b, 4.2, A.4, B.4, Part 4), `modes/_custom.md`, `CLAUDE.local.md`, agent memory.
- `output/cv.md` built from the archive with the same confirmed selection as before, so the content is unchanged. The payloads and HTML had disappeared from `output/` between 19:59 and 20:05, removed by nothing in this session; all rebuilt from `output/cv.md`.
- Both one-page PDFs rebuilt: one page each, A4, payloads identical, same Keywords cut as before (ETL, Data Wrangling, Data Mining, GPU Computing, Image Processing, Computer Vision, Neural Networks (CNN, U-Net)). Validator with the mirror check exit 0, title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: Consistency pass and CV build

- Fixed: `preprint.rules` title and intro now name `output/cv.md` (rule 0.3); `output/all_info.json` `meta.purpose` names `output/cv.md`; `modes/_profile.md` Contact Preference no longer calls the phone "secondary" (no phone is stored; ask if a form requires one); this log's header says the undated top sections are the 2026-11-05 setup and the dated entries override them.
- Checks clean: validator with the mirror check exit 0, `validate-profile.mjs` no problems, doctor finds the Experience section. Doctor still flags the template sections of `modes/_profile.md` and `modes/_brief.md`, which need Álvaro's input.
- General one-pager built from `output/cv.md`: `output/CV_arioboo_1pager.pdf` and `output/CV_arioboo_1pager_ats.pdf`, one page each, A4, payloads identical, same 7-keyword cut. Title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: Project dates in their own field

- `covid19_dashboard`: dates moved out of the description into a date field, like Experience and Education. Archive (schema 1.2.0): new required `projects[].period` (2020-09 to 2021-02, from the public repo's commits); "Developed Sep 2020 – Feb 2021" removed from the description.
- `output/cv.md` (and its root copy): "- **[covid19_dashboard](url)**, Sep 2020 – Feb 2021. Interactive dashboard ... with Python, pandas, matplotlib and Bokeh." Month precision replaces the earlier "2020 – 2021", matching Experience.
- Payload: the dates go in `projects[].badge` (the builder has no project date field). `photo-right` shows it right-aligned like `.edu-year`; `ats-1page` shows it inline after "|", like Education. `output/build_payload.mjs` and the validator (project dates vs `projects[].period`) updated.
- `ats-1page` page margin 0.45in → 0.40in: with the longer project line the ATS copy no longer fit even without the cuttable keywords; at 0.40in both copies fit with all 16 keywords, so no Keywords cut was needed this time.
- Rules: `preprint.rules` new 2.7, [project period] in A.2 and B.2, B.1 and B.4 updated; `CLAUDE.local.md` schema version.
- Both one-page PDFs rebuilt: one page each, A4, payloads identical. Validator (mirror check) exit 0, title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: General one-pager rebuilt

- Rebuilt from `output/cv.md` with no content changes: `output/CV_arioboo_1pager.pdf` and `output/CV_arioboo_1pager_ats.pdf`, one page each, A4, all 16 keywords, payloads identical. Validator (mirror check) exit 0, title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: all_info.json no longer ignored

- At Álvaro's request, `output/all_info.json` is no longer ignored by git: `!output/all_info.json` added to `.gitignore` after the `output/*` rule, and the line removed from `.git/info/exclude`. It is not staged or committed. `output/all_info.schema.json` and `output/validate_all_info.mjs` stay ignored.

## 2026-11-10: General one-pager rebuilt again

- Both PDFs were missing from `output/` before this build (removed outside this session). Rebuilt from `output/cv.md` with no content changes: one page each, A4, all 16 keywords, payloads identical. Validator (mirror check) exit 0, title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: General one-pager rebuilt (third time today)

- Both PDFs were missing from `output/` again before this build. Rebuilt from `output/cv.md` with no content changes: one page each, A4, all 16 keywords, payloads identical. Validator (mirror check) exit 0, title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 95/100 (A).

## 2026-11-10: Awards with category prefix and dates in the year field

- `output/cv.md` (and its root copy), Awards & Honors: "- Chess - 2 International Master (IM) norm results, 2012, 2014" and "- Chess - Champion of Córdoba (open) and Andalusia (sub-16 & sub-18), 2009 – 2011". The years moved out of the titles into the year field; the second line merges two archive awards, so it carries their range (2009 – 2011). The archive already held the years in `awards[].years` and the category in `awards[].category`; no archive change.
- `output/build_payload.mjs`: awards parsed as "{title}, {years}", years into `awards[].year`.
- `photo-right`: `.award-item` laid out like `.cert-item`, so award years sit in the right-hand date column. `ats-1page` already rendered the year after the title, like certifications.
- `preprint.rules`: new rule 2.8; [award category] and [award years] mapped in A.2 and B.2.
- Both one-page PDFs rebuilt: one page each, A4, all 16 keywords, payloads identical. Validator (mirror check) exit 0, title and structure checks passed, `ats-payload.mjs` 0 findings, `verify-ats.mjs` 100/100 (A).
