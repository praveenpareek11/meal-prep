# Context for Claude Code — meal-prep site maintenance

This repo is a personal vegetarian meal-prep knowledge base deployed via MkDocs Material to GitHub Pages.

## Owner constraints (respect in ALL recipe edits)
- Solo vegetarian, Hyderabad; monsoon rules: no raw sprouts (always steam 8-10 min), no leafy greens in monsoon, humidity shortens fridge life
- One morning cook (max 45-60 min) covers lunch + dinner; refrigerate after 30-40 min cooling, reheat thoroughly
- Weekend prep session: 1.5-2 hrs max
- Equipment: 2-burner gas, pressure cooker, kadai, idli pot, 60L OTG, 234L fridge, 23-25L solo microwave
- Portions: 1 person, 3 rotis or 1 bowl rice per meal
- HARD RULES: cooked rice 1-2 days fridge max; never store dough >1 day; NEVER freeze potato/curd/rice; sprouts always cooked

## Structure
- docs/recipes/ — one recipe per .md file. Template header: Type / Fridge life / Freezer-safe / Active time / Uses prepped components / Source
- Type is either `weekend-prep` (component) or `weekday-dish` (consumes components)
- docs/plan/ — system, variations (5 weekly plans), storage cheat sheet, shopping, freezer guide
- validation-changelog.md — audit trail of all recipe corrections; append when recipes change

## Adding a recipe
1. Create docs/recipes/kebab-case-name.md using the template header
2. Add it to the correct nav section in mkdocs.yml
3. If it changes weekly planning, update docs/plan/variations.md
4. Push to main — GitHub Actions auto-deploys

## Never
- Change storage/fridge/freezer claims without checking docs/plan/storage-cheatsheet.md
- Add recipes violating the hard rules above
