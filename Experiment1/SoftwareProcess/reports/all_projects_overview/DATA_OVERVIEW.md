# First look — dataset overview (skimmable)

## What’s here (size)
From `table_counts.csv`:
- **Projects:** 39
- **Sprints:** 4,594
- **Issues:** 458,232
- **Change log events:** 9,253,419

## What’s strongest
- **Issue-level timestamps** → good for **cycle time** on *resolved* issues.
- **Status change history** is large and usable.
  - `status` changes: **1,363,475** (`changelog_field_counts.csv`)

## Data quality (numbers you can cite)
From `missingness_overall.csv`:
- **Sprint_ID missing:** **90.51%** of issues (only **9.49%** have a sprint)
- **Estimation date missing:** **85.72%** of issues
- **Story points missing:** **85.72%** of issues
- **Resolution date missing:** **23.05%** of issues (unresolved / not closed)

## What’s weak / incomplete
- **Sprint signal is sparse** (often missing / inconsistent).
  - `sprint` changes: **174,915** (vs 1.36M status changes)
- **Workflow/status names vary** across projects (`status_to_values_top100.csv`) → any “in progress / done” logic needs mapping.

Concrete example from `sprint_coverage_by_project_quarter.csv` (resolved issues by project×quarter):
- `MDL 2014-Q4`: **3.47%** of resolved issues have `Sprint_ID`
- `JRASERVER 2018-Q1`: **0.39%**

## Usability (quick decision guide)
Recommended
- Project / quarter benchmarks
- Cycle time distributions (median, p75/p90)
- Status-transition features (counts, first/last status)

Use carefully
- Story points / estimates (expect missingness; always report coverage)

Avoid as default
- Sprint-level benchmarking (coverage too low overall)

## Files in this folder
- `table_counts.csv` — row counts per table
- `project_coverage.csv` — coverage by project
- `missingness_overall.csv` — null rates overview
- `changelog_field_counts.csv` — most-changed fields
- `status_to_values_top100.csv` — top status values
- `sprint_coverage_by_project_quarter.csv` — sprint coverage by slice
