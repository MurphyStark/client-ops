# Mode: pipeline — Process Pending URLs

Read `modes/_shared.md` and `data/pipeline.md` before starting.

## Trigger
User runs `/client-ops pipeline` or asks to process the pending inbox.

## Process

### Step 1: Load Pipeline
Read `data/pipeline.md`. List all pending prospects.

### Step 2: Confirm Scope
Tell Mordecai:
- How many pending prospects are in the inbox
- Estimated time to process
Ask: "Process all {n} now, or start with the top {5}?"

### Step 3: Evaluate Each
For each pending prospect, run `prospect` mode (full evaluation + report + tracker entry).

### Step 4: Remove Processed
After evaluating each prospect, remove it from `data/pipeline.md`.

### Step 5: Summary
After processing all, produce a summary:
- How many evaluated
- Score distribution
- Top 3 prospects by score
- Any immediate follow-up recommended
