# Mode: prospect — Evaluate a Prospect

Read `modes/_shared.md`, `modes/_profile.md`, `agency.md`, and `case-studies.md` before starting.

## Trigger

User pastes a company name, URL, LinkedIn profile, or brief description and asks to evaluate it as a prospect.

## Process

### Step 1: Research
If a URL is provided, fetch it with browser tools and extract:
- Company name, sector, size, location
- Current digital presence (website quality, social media)
- Apparent pain points (outdated site, no online bookings, no payments, etc.)
- Decision-maker names and roles (LinkedIn, About page, team page)
- Any signals of budget (funded, established >3 years, multiple staff)

If only a name/brief is provided, web search for the company first.

### Step 2: Archetype Match
Map the prospect to the closest MurphAgency archetype from `modes/_shared.md`. Note any partial matches or hybrid cases.

### Step 3: Score
Score each of the 5 dimensions (Budget Fit, Sector Fit, Project Fit, Decision Maker Access, Win Probability) on a 1–5 scale. Apply any overrides from `modes/_profile.md`. Calculate weighted total.

### Step 4: Package Recommendation
Based on the archetype and score, recommend the specific MurphAgency service package most likely to close. Reference proof points from `case-studies.md` that are relevant.

### Step 5: Outreach Strategy
Recommend the outreach channel and opening message approach based on `modes/_profile.md` preferred channels for this sector.

### Step 6: Generate Report
Write the full evaluation report in `reports/{###}-{company-slug}-{YYYY-MM-DD}.md` using the format from `modes/_shared.md`.

### Step 7: Tracker Entry
Write TSV to `batch/tracker-additions/{num}-{company-slug}.tsv`.

### Step 8: Confirm
Tell Mordecai:
- Score and grade
- Recommended package
- Recommended first action
- Ask: "Want me to draft the outreach message now?"

## Rules

- NEVER hardcode pricing — read from `modes/_profile.md`
- NEVER create tracker entry if company already exists in `data/leads.md`
- If score is F, say so clearly and recommend SKIP
- If decision-maker is not identifiable, flag this as a major risk
