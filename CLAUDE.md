# Context for Claude Code — meal-prep site maintenance

This repo is a personal vegetarian meal-prep knowledge base deployed via MkDocs Material to GitHub Pages.

## Owner constraints (respect in ALL recipe edits)
- Solo vegetarian, Hyderabad; monsoon rules: no raw sprouts (always steam 8-10 min), no leafy greens in monsoon, humidity shortens fridge life
- One morning cook (max 45-60 min) covers lunch + dinner; refrigerate after 30-40 min cooling, reheat thoroughly
- Weekend prep session: 1.5-2 hrs max
- Equipment: 2-burner gas, pressure cooker, kadai, idli pot, 60L OTG, 234L fridge. NO microwave yet (planned purchase) — reheating is kadai/tawa; mark optional microwave shortcuts with 🔲
- Portions: 1 person, 3 rotis or 1 bowl rice per meal
- HARD RULES: cooked rice 1-2 days fridge max; never store dough >1 day; NEVER freeze potato/curd/rice; sprouts always cooked

## Structure
- docs/recipes/ — one recipe per .md file. Template header: Type / Fridge life / Freezer-safe / Active time / Uses prepped components / Source / Kitchen-tested
- Kitchen-tested: new recipes always start `❌ not yet`; only the owner flips to `✅ <date>` after actually cooking it — never set ✅ yourself
- Type is either `weekend-prep` (component) or `weekday-dish` (consumes components)
- docs/plan/ — system, variations (5 weekly plans), storage cheat sheet, shopping, freezer guide
- validation-changelog.md — audit trail of all recipe corrections; append when recipes change

## Adding a recipe
1. Create docs/recipes/kebab-case-name.md using the template header
2. Ingredients MUST be a 2-column Markdown table (`| Ingredient | Quantity |`, quantity column right-aligned with `---:`), never a bullet list — capitalize ingredient names, keep optional/prep notes in the Quantity cell
3. Add it to the correct nav section in mkdocs.yml
4. If it changes weekly planning, update docs/plan/variations.md
5. Push to main — GitHub Actions auto-deploys

## Never
- Change storage/fridge/freezer claims without checking docs/plan/storage-cheatsheet.md
- Add recipes violating the hard rules above

## Formatting gotchas
Metadata header blocks in recipes use trailing double-spaces for hard line breaks (Python-Markdown). Never strip trailing whitespace in docs/**.md; .editorconfig enforces this. If a metadata block renders as a run-on paragraph, re-add the two trailing spaces.
