# Naming Conventions

Naming conventions for files, folders, and identifiers (e.g. DISC-xxx, CJ-xxx, PRD-xxx, PD-xxx, ADR-xxx).

## Folder ordering

Top-level folders (and their meaningful subfolders) use a two-digit numeric prefix (`01-`, `02-`, ...) so
that alphabetical sort matches the product process flow: `00-process` → `01-direction` → `02-discovery` →
`03-journeys` → `04-prd` → `05-ui` → `06-analytics` → `07-decisions` → `08-standards` → `09-archive`.

The same rule applies one level deeper wherever the order of the subfolders conveys meaning, for example
`01-direction/01-vision`, `02-strategy`, ... or `05-ui/02-platform/01-login`, `02-dashboard`, ...

**Exemptions** – folders that already sort correctly on their own are not prefixed:

- Year folders (`2025`, `2026`)
- Quarter folders (`Q1`–`Q4`)
- ID-sequenced folders (`DISC-001`, `CJ-001`, `PRD-001`, `PD-001`, `ADR-001`, ...)

## Process document filenames

Files under `00-process/<department>/` (e.g. `pm/`, `pd/`, `eng/`) use a numeric prefix plus a descriptive
kebab-case slug, e.g. `01-branch-strategy-repository-governance.md`, instead of a bare task ID like `ENG-01`.
The department is already implied by the parent folder, so the filename itself explains the task without
needing a role prefix — this also avoids clashing with the unrelated `PD-xxx` Product Decision IDs used
under `07-decisions/01-product/`.
