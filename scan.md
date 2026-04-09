# Mode: scan — Scan for New Prospects

Read `modes/_shared.md`, `modes/_profile.md`, and `portals.yml` before starting.

## Trigger
User asks to scan for new leads or runs `/client-ops scan`.

## Process

### Step 1: Load Scan Config
Read `portals.yml` for the list of sources, keywords, and filters.
Check `data/scan-history.tsv` to avoid re-processing already-seen prospects.

### Step 2: Scan Sources
For each source in `portals.yml`:
- Web search with the configured keywords
- Fetch promising results with browser tools
- Extract: company name, URL, sector, apparent size, location

### Step 3: Filter
For each result:
- Is it in Zimbabwe or target SADC country? If not, skip.
- Does it match any MurphAgency archetype? If not, skip.
- Is it already in `data/leads.md` or `data/scan-history.tsv`? If yes, skip.
- Does it trigger any deal-breaker from `modes/_profile.md`? If yes, skip.

### Step 4: Quick Score
For each surviving prospect, do a rapid 30-second score (estimated, not full evaluation).
Only add to pipeline if estimated score ≥ 3.0.

### Step 5: Add to Pipeline
Write qualifying prospects to `data/pipeline.md` as pending URLs for full evaluation:
```markdown
- {URL} | {Company} | {Sector} | {Source} | {YYYY-MM-DD}
```

### Step 6: Update Scan History
Append all seen URLs (even rejected ones) to `data/scan-history.tsv` to prevent re-processing.

### Step 7: Report
Tell Mordecai:
- How many sources scanned
- How many prospects found
- How many added to pipeline
- List the new pipeline entries
Ask: "Want me to evaluate all {n} new prospects now?"

## Sources in portals.yml
Configure these categories:
- Zimbabwe business directories (Zimtrade, Yellow Pages ZW, BusinessListZW)
- LinkedIn searches (by sector, location, size)
- Local news / business press (NewsDay, The Herald business section, ZimLive)
- Sector-specific directories (Law Society of Zimbabwe, Agribusiness Zimbabwe)
- Church directories (SDA conference websites, SAUC directory)
- Government procurement notices (PRAZ — filter for ICT/digital)
