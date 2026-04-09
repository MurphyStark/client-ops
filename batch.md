# Mode: batch — Batch Processing

Read `modes/_shared.md` and `modes/_profile.md` before starting.

## Trigger
User asks to batch process multiple prospects at once.

## Process

### Step 1: Load List
Accept a list of prospects (URLs, names, or pipeline file).

### Step 2: Process in Sequence
For each prospect, run full `prospect` mode evaluation.
Write report + tracker TSV for each.

### Step 3: Merge Tracker
After all evaluations complete, run `node merge-tracker.mjs` to merge all TSV additions into `data/leads.md`.

### Step 4: Summary Report
Produce batch summary:
- Total processed
- Score distribution (A/B/C/D/F counts)
- Top 5 prospects to prioritise
- Total estimated pipeline value

## Notes
- Batch mode processes sequentially, not in parallel (to avoid rate limits)
- Reports are saved regardless of score (even F scores, for pattern analysis)
- Always merge tracker after batch — never leave TSV files unmerged
