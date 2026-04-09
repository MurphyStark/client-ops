# client-ops

> AI-powered client acquisition & proposal pipeline for MurphAgency

Reverse-engineered from [career-ops](https://github.com/santifer/career-ops) — rebuilt to find and win clients for a digital agency in Harare, Zimbabwe.

## What it does

- **Scans** LinkedIn, directories, and sector sources for qualified prospects in Zimbabwe & Southern Africa
- **Evaluates** prospects with an A-F scoring model (budget, sector fit, project type, decision-maker access)
- **Researches** target companies deeply before outreach
- **Drafts** personalised outreach (LinkedIn, email, WhatsApp)
- **Generates** tailored proposal PDFs from a branded HTML template
- **Preps** discovery calls with company-specific intel
- **Tracks** every lead through the full pipeline
- **Analyses** win/loss patterns to sharpen targeting over time

## Quick Start

```bash
git clone https://github.com/MurphyStark/client-ops
cd client-ops
npm install
cp config/profile.example.yml config/profile.yml
# Edit config/profile.yml with your details
claude
> /client-ops
```

## Commands

| Command | Description |
|---------|-------------|
| `/client-ops prospect` | Evaluate a prospect (A-F scoring) |
| `/client-ops outreach` | Draft outreach message |
| `/client-ops proposal` | Generate proposal PDF |
| `/client-ops discovery` | Discovery call prep |
| `/client-ops scan` | Scan for new prospects |
| `/client-ops tracker` | Pipeline status |
| `/client-ops patterns` | Win/loss analysis |

## Architecture

```
client-ops/
├── CLAUDE.md                  # Master orchestration brain
├── agency.md                  # MurphAgency profile
├── case-studies.md            # Proof points from past work
├── portals.yml                # Prospect sources to scan
├── config/
│   ├── profile.example.yml    # Copy to profile.yml
│   └── states.yml             # Canonical pipeline states
├── modes/                     # 14 skill modes
│   ├── _shared.md             # Shared scoring + archetypes
│   ├── _profile.template.md   # Copy to _profile.md
│   ├── prospect.md
│   ├── outreach.md
│   ├── proposal.md
│   ├── discovery.md
│   ├── deep.md
│   ├── scan.md
│   ├── pipeline.md
│   ├── pitch.md
│   ├── tracker.md
│   ├── patterns.md
│   ├── retainer.md
│   ├── case-study.md
│   └── batch.md
├── data/
│   ├── leads.md               # Master leads tracker
│   └── pipeline.md            # Pending URL inbox
├── templates/
│   └── proposal-template.html # Branded proposal template
├── reports/                   # Evaluation reports
├── output/                    # Generated PDFs (gitignored)
└── discovery-prep/            # Discovery call intel
```

---
Built on the architecture of [career-ops](https://github.com/santifer/career-ops) by santifer. Adapted for agency BD by MurphAgency.
