# Running the SoftwareProcess notebooks

## Prereqs
- Python 3.11+
- A local MySQL instance with database `testdb` populated with the Jira export tables
- A `.env` file in the repo root with DB connection settings (copy from `.env.example`)

Expected environment variables:
- `DB_USER` (default: `root`)
- `DB_PASSWORD` (default: empty)
- `DB_HOST` (default: `127.0.0.1`)
- `DB_PORT` (default: `3306`)
- `DB_NAME` (default: `testdb`)

## Setup (once)
From the repo root:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install -r requirements.txt
python -m ipykernel install --user --name softwaredata --display-name "Python (SoftwareData)"
```

## Run notebooks
Start Jupyter from the repo root (Experiment1/):

```bash
jupyter lab
```

Open notebooks under:
- `SoftwareProcess/notebooks/`

Recommended run order:
1. `01_first_look.ipynb` (exports initial reports and interim extracts)
2. `02_projects_overview.ipynb`
3. `03_motherfiles.ipynb` (builds per-project mother files)
4. `04_summaries.ipynb` (creates summary tables + long-format exports)
5. `05_visualizations.ipynb` (creates plots from summary exports)
6. `06_project_distributions.ipynb` (creates per-project distribution plots)

## Notes on paths
Notebooks use paths relative to `SoftwareProcess/notebooks/`, e.g.:
- `../reports/...` resolves to `SoftwareProcess/reports/...`
- `../data/...` resolves to `SoftwareProcess/data/...`

If you run notebooks from a different working directory, keep this in mind.
