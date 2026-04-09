# client-ops — AI Client Acquisition & Proposal Pipeline

## Origin

MurphAgency's AI-powered client pipeline — reverse-engineered from career-ops and rebuilt for agency business development. Instead of evaluating job offers, it evaluates prospects. Instead of generating CVs, it generates proposals. Instead of scanning job portals, it scans for leads.

Built for Mordecai / MurphAgency — a full-stack digital agency in Harare, Zimbabwe, serving legal, agricultural, church, housing, and SME sectors across Southern Africa. Stack: Node.js, Flask, Supabase, Netlify, n8n, WhatsApp bots (Meta Cloud API).

## Data Contract (CRITICAL)

Two layers. Never mix them.

**Agency Layer (NEVER auto-updated — your business data lives here):**
- `agency.md`, `config/profile.yml`, `modes/_profile.md`, `case-studies.md`, `portals.yml`
- `data/*`, `reports/*`, `output/*`, `discovery-prep/*`

**System Layer (updatable — do not put agency data here):**
- `modes/_shared.md`, `modes/prospect.md`, all other mode files
- `CLAUDE.md`, `*.mjs` scripts, `templates/*`, `batch/*`

**THE RULE: When customising anything (archetypes, pricing, negotiation scripts, case study proof points, sector targets), ALWAYS write to `modes/_profile.md` or `config/profile.yml`. NEVER edit `modes/_shared.md` for agency-specific content.**

## What is client-ops

AI-powered client acquisition automation built on Claude Code: pipeline tracking, prospect evaluation, proposal generation, portal scanning, outreach drafting, discovery call prep, win/loss analysis.

### Main Files

| File | Function |
|------|----------|
| `data/leads.md` | Lead/prospect tracker |
| `data/pipeline.md` | Inbox of pending URLs/leads |
| `data/scan-history.tsv` | Scanner dedup history |
| `portals.yml` | Target directories, LinkedIn searches, company lists |
| `templates/proposal-template.html` | HTML template for proposals |
| `generate-pdf.mjs` | Playwright: HTML to PDF |
| `case-studies.md` | Proof points from past work |
| `discovery-prep/story-bank.md` | Discovery call stories across engagements |
| `discovery-prep/{company}-{project}.md` | Company-specific discovery intel |
| `analyze-patterns.mjs` | Win/loss pattern analysis |
| `reports/` | Evaluation reports (`{###}-{company-slug}-{YYYY-MM-DD}.md`) |

### Skill Modes

| If the user... | Mode |
|----------------|------|
| Pastes a prospect URL, company name, or brief | auto-pipeline |
| Asks to evaluate a prospect | `prospect` |
| Asks to compare multiple prospects | `prospects` |
| Wants to draft outreach (LinkedIn/email/WhatsApp) | `outreach` |
| Asks for deep company research | `deep` |
| Preps for a discovery call | `discovery` |
| Wants to generate a proposal PDF | `proposal` |
| Evaluates a new service/retainer fit | `retainer` |
| Evaluates a case study angle | `case-study` |
| Asks about pipeline status | `tracker` |
| Runs a live pitch or client meeting | `pitch` |
| Searches for new prospects | `scan` |
| Processes pending URLs | `pipeline` |
| Batch processes leads | `batch` |
| Asks about win/loss patterns | `patterns` |

### Commands

| Command | Description |
|---------|-------------|
| `/client-ops` | Show menu or evaluate prospect with args |
| `/client-ops prospect` | Evaluate a prospect (A-F scoring) |
| `/client-ops prospects` | Compare and rank multiple prospects |
| `/client-ops outreach` | Draft outreach (LinkedIn, email, WhatsApp) |
| `/client-ops deep` | Deep company research |
| `/client-ops proposal` | Generate tailored proposal PDF |
| `/client-ops discovery` | Discovery call prep |
| `/client-ops retainer` | Evaluate service/retainer fit |
| `/client-ops case-study` | Evaluate case study angle |
| `/client-ops tracker` | Pipeline status overview |
| `/client-ops pitch` | Live pitch assistant |
| `/client-ops scan` | Scan portals/directories for new prospects |
| `/client-ops pipeline` | Process pending URLs from inbox |
| `/client-ops batch` | Batch processing |
| `/client-ops patterns` | Win/loss analysis |

## First Run — Onboarding (IMPORTANT)

Check silently on every session start:
1. Does `agency.md` exist?
2. Does `config/profile.yml` exist (not just profile.example.yml)?
3. Does `modes/_profile.md` exist (not just _profile.template.md)?
4. Does `portals.yml` exist?

If `modes/_profile.md` is missing, copy from `modes/_profile.template.md` silently.

**If ANY is missing, enter onboarding mode before doing anything else.**

### Step 1: Agency Profile
If `agency.md` missing, ask:
> "I don't have MurphAgency's profile yet. You can:
> 1. Paste your agency bio/website copy and I'll structure it
> 2. Tell me your services and I'll draft it from scratch"

Create `agency.md` with: Summary, Services, Tech Stack, Sectors Served, Notable Projects, Pricing Model, Differentiators.

### Step 2: Commercial Profile
If `config/profile.yml` missing, copy from example and ask:
> "A few details to personalise the pipeline:
> - Primary sectors you target (legal, agro, church, housing, NGO, SME)
> - Ideal project size / budget range in USD
> - Services to lead with (web, automation, WhatsApp bots, etc.)
> - Deal-breakers (clients to avoid)"

### Step 3: Portals
If `portals.yml` missing, initialise from template and customise for MurphAgency's target sectors in Zimbabwe/Southern Africa.

### Step 4: Tracker
If `data/leads.md` missing, create it with headers.

### Step 5: Learn MurphAgency
> "The pipeline works much better when it knows MurphAgency deeply. Tell me:
> - What's your strongest service / where do you deliver outstanding results?
> - What kind of client do you love? What drains you?
> - Deal-breakers? (no clients without budget, no scope-creep sectors)
> - Your best project — the one you lead with in every pitch
> - Any live URLs, testimonials, or case studies I can reference?
>
> The more context you give me, the better I filter. Think of it as onboarding your best BD person."

Store insights in `config/profile.yml` (narrative), `modes/_profile.md`, or `case-studies.md`.

**After every evaluation, learn.** If Mordecai says "score is too high, we'd never win this" or "you missed we built X for a law firm" — update `modes/_profile.md` or `case-studies.md`. The system gets smarter with every deal.

## Ethical Use — CRITICAL

- **NEVER send a proposal without Mordecai reviewing it first.** Draft, generate, prepare — always STOP before sending.
- **Strongly discourage low-fit prospects.** Score below 4.0/5 → recommend against pursuing. Bad-fit clients cost more than they earn.
- **Quality over volume.** 3 tailored proposals beat a generic blast to 30.
- **Respect prospects' time.** Only reach out when there's genuine value to offer.

## Stack and Conventions

- Node.js (mjs modules), Playwright (PDF), YAML (config), HTML/CSS (proposal template), Markdown (data)
- Output in `output/` (gitignored), Reports in `reports/`
- Report numbering: 3-digit zero-padded sequential
- **RULE: NEVER create new entries in leads.md if company already exists.** Update existing entry.
- **RULE: After each batch of evaluations, run `node merge-tracker.mjs`**

### Canonical States

| State | When to use |
|-------|-------------|
| `Identified` | Lead found, not yet evaluated |
| `Evaluated` | Scored, pending outreach decision |
| `Contacted` | Outreach sent |
| `Responded` | Prospect responded |
| `Discovery` | Discovery call scheduled/completed |
| `Proposal` | Proposal sent |
| `Negotiating` | In scope/price negotiation |
| `Won` | Project confirmed / contract signed |
| `Lost` | Prospect chose another or no-decision |
| `Nurture` | Not ready now, keep warm |
| `SKIP` | Doesn't fit, do not pursue |

### TSV Format for Tracker Additions

Write one TSV to `batch/tracker-additions/{num}-{company-slug}.tsv`:
```
{num}\t{date}\t{company}\t{sector}\t{status}\t{score}/5\t{proposal_emoji}\t[{num}](reports/{num}-{slug}-{date}.md)\t{note}
```
