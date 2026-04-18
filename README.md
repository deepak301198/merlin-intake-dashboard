# Merlin Intake — Executive Dashboard

Live dashboard for Merlin Intake customer pipeline, automation health, performance engineering, and meeting history.

## How it works

```
OneDrive (Source.xlsx)
       ↓  Power Automate (on file change)
  GitHub /data/*.csv
       ↓  GitHub Actions (on push)
  GitHub Pages → live dashboard URL
```

**Update cycle:** Edit `Source.xlsx` on OneDrive → dashboard refreshes within ~3–5 minutes automatically.

## Repo structure

```
/
├── index.html                  ← The entire dashboard (single file)
├── data/                       ← CSVs auto-synced from OneDrive
│   ├── meetings.csv
│   ├── customers.csv
│   ├── automation.csv
│   ├── auto_failures.csv
│   ├── performance.csv
│   ├── pmg_tools.csv
│   ├── deployments.csv
│   ├── issues.csv
│   └── meetings_history.csv
├── .github/
│   └── workflows/
│       └── deploy.yml          ← Auto-deploys on every push to main
└── README.md
```

## Setup (one-time)

1. Create a GitHub Personal Access Token (PAT) with `repo` scope
2. Add it as a repository secret named `GH_PAT`
3. Configure the Power Automate flow (see Phase 3 instructions)
4. Push this repo to GitHub and enable GitHub Pages

## Dashboard URL

`https://deepak301198.github.io/merlin-intake-dashboard/`

## Rules for data entry

- **Never delete rows** in MEETINGS, AUTOMATION, or MEETINGS_HISTORY sheets
- **Always use dropdowns** for status fields — exact text match required
- **Desktop Excel only** — not Excel Online
