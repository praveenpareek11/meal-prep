# Recipe Guide — meal-prep site

Self-contained instructions for generating recipes for this repo (praveenpareek11/meal-prep). Attach this file to any AI assistant project (ChatGPT, Claude, etc.) so generated recipes stay consistent in formatting and food safety.

The site is a personal vegetarian meal-prep knowledge base built with MkDocs Material, deployed to GitHub Pages via GitHub Actions on every push to `main`.

---

## 1. Who this is for (owner constraints — respect in EVERY recipe)

- Solo vegetarian in Hyderabad. Portions: **1 person**, 3 rotis or 1 bowl rice per meal. Most fresh dishes make **2 meals** (lunch + dinner from one morning cook).
- **One morning cook: 45–60 min max active time.** Weekend prep session: 1.5–2 hrs max.
- **Monsoon rules:** no raw sprouts ever (always steam 8–10 min), no leafy greens in monsoon, humidity shortens fridge life — be conservative.
- Equipment available: 2-burner gas stove, pressure cooker, kadai, idli pot, 60L OTG, 234L fridge. **NO microwave** (planned future purchase) — all reheating instructions must use kadai/tawa; a microwave alternative may be added only as an optional shortcut marked with 🔲. Do not write recipes needing anything else (no air fryer, no blender assumptions unless a basic mixer-grinder task).

## 2. Food-safety HARD RULES (never violate, never "improve")

1. Cooked rice: **1–2 days fridge max** (prefer cooking fresh).
2. Never store any dough **more than 1 day**.
3. **NEVER freeze potato, curd/dahi, or rice** — or any dish containing them.
4. Sprouts are **always cooked** (steamed 8–10 min minimum), never raw.
5. Cook → cool to warm (**30–40 min, never hours**) → lid → fridge.
6. Reheat thoroughly, piping hot — and **only the portion being eaten**.
7. Dishes containing paneer, soya, or potato: **same day to 1 day fridge**, no freezing.

## 3. Storage reference table

Do NOT invent fridge/freezer durations from general knowledge. Use this table. (Canonical source in the repo: `docs/plan/storage-cheatsheet.md` — if that file and this guide ever disagree, the cheat sheet wins.)

| Item | Fridge | Freezer |
|---|---|---|
| Onion-tomato masala base | 4 days | 3-4 weeks |
| Boiled legumes (in liquid) | 3 days | 2-3 weeks |
| Plain boiled dal | 3 days | 2-3 weeks |
| Cooked gravy dishes (rajma/chole) | 2-3 days | 2 weeks |
| Sambar-style dal | 3 days | 2 weeks |
| Cooked dry sabzi | 2-3 days | ❌ |
| Cooked rice | 1-2 days (but just cook fresh) | ❌ |
| Cooked rotis | 2-3 days | ❌ (theplas: 1 week ✅) |
| Boiled potatoes (skin on) | 3-4 days | ❌ |
| Chopped raw veggies (dry, airtight) | 3-4 days | ❌ |
| Idli/dosa batter (readymade) | 3-4 days | ❌ |
| Home curd | 4-5 days | ❌ |
| Steamed sprouts | 2 days | ❌ |
| Paneer (opened) | 2-3 days | ❌ |
| Dishes with paneer / soya / potato | same day-1 day | ❌ |

In monsoon, treat chopped raw veg as usable through day 3; day 4 is a smell-test fallback, not a plan.

## 4. File conventions

- One recipe per file: `docs/recipes/kebab-case-name.md` (e.g. `aloo-pyaaz-tamatar-jhol.md`).
- Recipe **Type** is one of exactly two values:
    - `weekend-prep` — a component made in the weekend session (masala base, boiled legumes, curd…)
    - `weekday-dish` — a dish cooked on a weekday, fresh or from prepped components
- Hindi/Indian ingredient names are used as-is (jeera, haldi, hing, dhania, amchur, kasuri methi).

### 4a. Metadata header — CRITICAL formatting rule

Every recipe starts with an H1 title, then a metadata block. **Every line of the metadata block must end with exactly two trailing spaces** — that is how Python-Markdown makes hard line breaks. Without them, the whole block renders as one run-on paragraph on the live site, with no error anywhere.

⚠️ Chat interfaces silently strip trailing spaces. After committing, verify the raw file on GitHub actually contains the two trailing spaces on each header line. This is the single most common way generated recipes break.

Template (the `␠␠` marker means two real space characters — replace it, don't type ␠):

```
# Recipe Name

**Type:** weekday-dish␠␠
**Fridge life:** 1 day; refrigerate the dinner portion after cooling 30-40 min · **Freezer-safe:** No, because potato texture deteriorates after freezing␠␠
**Active time:** 20-25 min (morning) · **Makes:** 2 meals for 1 person␠␠
**Uses prepped components:** none␠␠
**Source:** own␠␠
**Kitchen-tested:** ❌ not yet␠␠
```

- **Freezer-safe** must include the reason when it is "No".
- **Uses prepped components** lists weekend-prep components consumed (e.g. "onion-tomato masala base, boiled legumes") or `none`.
- **Kitchen-tested** tracks whether the owner has actually cooked the recipe and confirmed the quantities and process work. Every NEW recipe starts as `❌ not yet` — an AI assistant must NEVER set this to ✅ on its own; only the owner flips it after a successful cook, changing it to `✅ 2026-07-15` (date of first cook, plus an optional short note like "reduce salt slightly"). If the owner reports corrections instead, fix the recipe (VALIDATION & CORRECTION MODE), keep ❌ until they confirm a good cook, and log the change in `validation-changelog.md`.
- Optionally after the header, one italic *Style:* line describing the dish and its pairing (e.g. `*Style: thin, spoonable jhol gravy. Pairs with 3 rotis per meal.*`).

### 4b. Ingredients — MUST be a table, never a bullet list

Two-column Markdown table, quantity column right-aligned with `---:`. Capitalize ingredient names. Keep prep notes and "optional" inside the Quantity cell.

```
## Ingredients

| Ingredient        |                  Quantity |
| ----------------- | ------------------------: |
| Potato            | 3 medium, about 300-350 g |
| Oil               |                   1½ tbsp |
| Amchur            |           ¼ tsp, optional |
```

Use unicode fractions (½, ¼, ¾) and metric weights where helpful.

### 4c. Body sections

1. `## Process` (or `## Process — Pressure Cooker` etc.) — numbered steps; **bold** the quantities, times, and heat levels inside steps (e.g. "cook for **4–5 minutes**").
2. `## Portioning and Storage` (or `## Storage for dinner`) — bullet list; must state the 30–40 min cooling rule and portion-only reheating explicitly.

## 5. Adding a recipe to the site (checklist)

1. Create `docs/recipes/<kebab-case-name>.md` per the template above.
2. Add one nav line to `mkdocs.yml` under the correct section — the nav has three recipe groups: **Weekend Prep Components**, **Weekday Dishes**, and **Fresh Recipes** (fresh dishes cooked from raw ingredients, no prepped components). Match the existing indentation (6 spaces):
   `      - Recipe Display Name: recipes/kebab-case-name.md`
3. If the recipe changes weekly planning, also update `docs/plan/variations.md`.
4. If you are **correcting** an existing recipe (not adding a new one), append an entry to `validation-changelog.md`.
5. Commit and push to `main` — GitHub Actions builds and deploys automatically.
6. **After pushing, check the Actions tab** on GitHub for a green run. There is no local build check in this workflow, so a broken nav path or bad link only surfaces there.

## 6. Never do these

- Never change a storage/fridge/freezer claim without checking the table in section 3.
- Never strip trailing whitespace anywhere in `docs/**.md` files — existing trailing double-spaces are load-bearing.
- Never add a recipe that violates the hard rules in section 2, even if a source recipe suggests it (e.g. "freeze the extra portion" — not for potato/curd/rice dishes).
- Never scale recipes to family portions; everything is for 1 person.
