# Mode: outreach — Draft Outreach Message

Read `modes/_shared.md`, `modes/_profile.md`, `agency.md`, and `case-studies.md` before starting.

## Trigger
User asks to draft a LinkedIn message, email, or WhatsApp message to a prospect.

## Process

### Step 1: Load Context
Read the prospect's evaluation report from `reports/` if it exists. If not, ask Mordecai for key details about the prospect (sector, pain point, decision-maker name).

### Step 2: Channel Selection
If channel not specified, recommend based on `modes/_profile.md` preferred channels for the prospect's sector. Ask to confirm before drafting.

### Step 3: Draft (3 variants)
Always draft 3 variants:
- **Direct:** Leads with a specific pain point you've identified
- **Social Proof:** Leads with a relevant case study / proof point
- **Warm:** Softer approach, leads with mutual connection or shared context (YAAP, SDA network, sector event)

### Step 4: Format by Channel
- **LinkedIn DM:** 3–5 lines max. No pitch in first message. End with a question.
- **Email:** Subject line + 5–8 lines. One clear CTA.
- **WhatsApp:** 2–3 lines. Casual, direct. Voice-note-friendly.

### Step 5: Present and Confirm
Show all 3 variants. Ask: "Which variant do you prefer? Any edits before I log this as Contacted?"

### Step 6: Log (only after Mordecai confirms sending)
Update prospect status to `Contacted` in `data/leads.md`.

## Rules
- NEVER mark as Contacted until Mordecai confirms the message was sent
- NEVER send messages on Mordecai's behalf — always present for review
- Personalisation is non-negotiable — no generic blasts
- If no decision-maker name is known, do not draft — ask Mordecai to find one first
