# EDUAI project guide

## Purpose
Help prospective undergraduate students discover universities, compare a shortlist and create an editable preparation pathway. Keep the product welcoming, practical and easy to extend. Do not imply guaranteed admission or present planning suggestions as official deadlines.

## Architecture
This is a dependency-free static website. `dist/` is the deployable website, not generated output. Edit it directly. `dist/index.html` provides semantic page structure, `dist/style.css` contains design tokens and responsive layouts, `dist/data.js` contains university records, and `dist/app.js` contains interactions. GitHub Pages deploys `dist/` through `.github/workflows/pages.yml`. `.openai/hosting.json` configures Sites hosting. `README.md` explains operation and `SUBMISSION.md` is the hand-in draft.

## Design and content
Use warm off-white backgrounds, forest-green text and pale green accents. Reuse CSS variables in `:root`. Headings use Playfair Display with Georgia fallback; body uses DM Sans with sans-serif fallback. Maintain the numbered Explore / Compare / Plan sequence. Use encouraging, concise English, no rankings or invented testimonials. Keep controls accessible with labels, keyboard focus, descriptive button names and sufficient contrast. Mobile layouts must work at 375px without body overflow. Tables may scroll within their own container.

## University data contract
Add a record to `UNIVERSITIES` in `dist/data.js`. Required string fields: `id` (unique lowercase kebab-case), `name`, `short`, `city`, `country`, `color` (sage/sand/blue/rose), `symbol`, `tag`, `description`, `requirement`, `route`, `source` (official HTTPS admissions URL), `reviewed` (YYYY-MM-DD). All existing entries cover undergraduate exploration. Keep summaries brief and factual. The shared renderer must automatically include each new record in discovery, profile and comparison. Add a destination option in index.html if introducing a country. Never duplicate university data in the renderer.

## Evidence rules
Read the official admissions source before modifying factual claims. Record the actual review date. Qualification and programme requirements vary: link to the official rules rather than flattening them into one score. Never invent tuition, acceptance rates, scholarships, deadlines or eligibility. If adding fee data, include currency, academic year, applicant category, programme scope and source; unknown values must be explicit. No scraping private data.

## Behavior and storage
Use localStorage key `eduai-v1` for saved university IDs, plan inputs and completed task indices. Validate loaded data and handle unavailable storage gracefully. Compare at most three universities and provide a visible explanation at the limit. Search and country filters combine. Empty searches and empty shortlists must have helpful states. Render user inputs through `esc` or textContent; never interpolate raw input into HTML. Keep links HTTPS and external tabs `rel=noopener`.

## Extending the pathway
`tasks()` provides six preparation steps and relative-month suggestions. Changes must preserve the distinction between suggestions and official deadlines. Plan fields are interest, stage, destination and start month. Confirm before replacing progress; reject a past start month. Keep export and progress counts consistent. If task identifiers or the data schema change, migrate stored data or use a new versioned key with a clear migration strategy.

## Adding a page or feature
1. Read this file and inspect the existing components.
2. Add content to the data model before changing presentation.
3. Reuse typography, spacing, card patterns and navigation.
4. For standalone pages use lowercase kebab-case HTML filenames and relative asset links, so GitHub project Pages works under a repository subpath.
5. Update navigation, README and the verification checklist.
6. Verify search, combined filters, saving/removing, three-item limit, profiles, keyboard dismissal, plan validation, completion persistence, export, and narrow-screen layout.
7. Run `node --check dist/app.js` and `node --check dist/data.js`; preview with `python3 -m http.server 4173 --directory dist`.

## Publishing
Only deploy reviewed files in dist. Do not place secrets, personal student details or local storage exports in Git. Preserve hosting IDs and use the authorized GitHub repository. Update SUBMISSION.md with verified repository and live URLs after deployment. Do not claim tests or publication succeeded without evidence.
