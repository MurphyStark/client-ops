# Mode: proposal — Generate Tailored Proposal PDF

Read `modes/_shared.md`, `modes/_profile.md`, `agency.md`, and `case-studies.md` before starting.

## Trigger
User asks to generate a proposal for a specific prospect.

## Process

### Step 1: Load Prospect Data
Read the evaluation report from `reports/` for this prospect. If no report exists, run `prospect` mode first.

### Step 2: Gather Missing Info
Ask for anything not in the report:
- Client contact name and email
- Project brief / what they asked for (if different from research)
- Agreed timeline (if any verbal discussions happened)
- Any pricing signals from discovery call

### Step 3: Build Proposal Content
Structure:
1. **Cover Page** — Client name, project title, MurphAgency branding, date
2. **Executive Summary** — 1 page. Their problem, our solution, expected outcome.
3. **About MurphAgency** — Brief (from `agency.md`), relevant to this client's sector
4. **Our Understanding** — What we heard, what we think they need
5. **Proposed Solution** — Specific deliverables, tech stack, approach
6. **Timeline** — Phase-based Gantt-style breakdown (weeks)
7. **Investment** — Line-item pricing from `modes/_profile.md` anchors. Payment terms: 50% upfront, 50% on delivery.
8. **Why MurphAgency** — 1–2 relevant case studies from `case-studies.md`
9. **Next Steps** — Clear CTA: "Sign and return the deposit invoice to kick off"
10. **Contact** — Mordecai's details

### Step 4: Generate HTML
Populate `templates/proposal-template.html` with the content. Replace all `{{placeholders}}`.

### Step 5: PDF
Run `node generate-pdf.mjs --input output/{slug}-proposal.html --output output/{slug}-proposal.pdf`

### Step 6: Confirm
Tell Mordecai: "Proposal ready at `output/{slug}-proposal.pdf`. Review before sending."
Update status to `Proposal` in `data/leads.md` only after Mordecai confirms it was sent.

## Rules
- NEVER send the proposal — always present for review first
- NEVER invent case studies — only use what's in `case-studies.md`
- NEVER discount from pricing anchors without Mordecai's instruction
- Proposals expire in 14 days — include expiry date on cover page
