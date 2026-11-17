# EDUAI — Your next chapter

A responsive university discovery and study-path planning website.

## Features
- Four university profiles across Taiwan, Singapore, Canada and Australia, linked to official admissions sources.
- Search, destination filters and saved-only view.
- Persistent shortlist and comparison of up to three universities.
- Personal pathway based on study interest, current stage, destination and intended start month.
- Six editable completion steps, suggested preparation dates, progress indicator and text export.
- Local browser storage; no signup or backend required.

## Run locally
Run `python3 -m http.server 4173 --directory dist` and visit http://localhost:4173.
There is no build or installation step. Optional web fonts have system fallbacks.

## Project map
- `dist/index.html`: structure and controls
- `dist/style.css`: responsive design
- `dist/data.js`: university content and official citations
- `dist/app.js`: filtering, comparison, profiles and planner
- `AGENTS.md`: reusable development and content rules
- `.github/workflows/pages.yml`: GitHub Pages deployment

## Extend
Follow AGENTS.md. Adding one university data record automatically adds it to the cards, profile modal and comparison table. For a new destination, update the filter and planner options. Keep factual information sourced and date-stamped.

## Scope
Profiles are curated starting points, not a comprehensive university database or eligibility assessment. Fees, deadlines and scholarships must be verified for the chosen programme on official websites. Roadmap dates are general planning suggestions. Saved data is stored only in the current browser and may be lost if browser storage is cleared; export a copy of your pathway.
