# Mode: tracker — Pipeline Status Overview

Read `data/leads.md` before starting.

## Trigger
User asks about pipeline status, deal count, or wants an overview.

## Output

Produce a structured pipeline summary:

### Pipeline Summary
```
Total leads: {n}
├── Identified:   {n}
├── Evaluated:    {n}
├── Contacted:    {n}
├── Responded:    {n}
├── Discovery:    {n}
├── Proposal:     {n}
├── Negotiating:  {n}
├── Won:          {n}
├── Lost:         {n}
├── Nurture:      {n}
└── SKIP:         {n}
```

### Active Pipeline (Contacted through Negotiating)
List each active prospect with: Company | Sector | Score | Status | Last Action | Next Step

### Hot Leads (Score ≥ 4.0, Status = Evaluated or Contacted)
These need follow-up. List with recommended next action.

### Stale Leads (no update in 14+ days, active status)
Flag these. Ask Mordecai what happened and update status.

### Pipeline Value Estimate
Based on `modes/_profile.md` pricing anchors and deal stages:
- Proposal stage: {estimated value}
- Negotiating: {estimated value}
- Total potential revenue: {total}

### Recommended Actions
Top 3 highest-priority actions to move the pipeline forward today.
