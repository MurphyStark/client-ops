# Mode: patterns — Win/Loss Analysis

Read `data/leads.md`, all `reports/`, and `modes/_profile.md` before starting.

## Trigger
User asks about win/loss patterns, wants to improve targeting, or runs `/client-ops patterns`.

## Process

### Step 1: Aggregate Data
From `data/leads.md`, extract all Won and Lost deals.
Cross-reference with evaluation reports in `reports/`.

### Step 2: Win Pattern Analysis
For Won deals:
- What sectors / archetypes appear most?
- What was the average score of deals that converted?
- What was the most common first-touch channel?
- What service packages appeared most?
- What was the average deal size?
- How long did the pipeline take from Identified to Won?

### Step 3: Loss Pattern Analysis
For Lost deals:
- What were the most common reasons for loss?
- At what stage did most deals die (Contacted, Discovery, Proposal)?
- Were there scoring patterns? (Did we pursue too many C/D scores?)
- Any sectors where we consistently lose?

### Step 4: Scoring Calibration
Compare scored prospects vs actual outcomes:
- Were our A/B scores actually converting?
- Were we scoring some sectors too high?
- Recommend scoring adjustments to `modes/_profile.md`

### Step 5: Recommendations
Output 5 specific, actionable recommendations:
1. Sectors/archetypes to focus on more
2. Sectors/archetypes to de-prioritise
3. Outreach channel or approach changes
4. Scoring model adjustments
5. Pipeline stage where most deals are stuck and how to fix it

### Step 6: Update Profile
Ask Mordecai: "Want me to update `modes/_profile.md` with these insights?"
If yes, apply the recommended changes and confirm.
