# Mode: auto-pipeline — Auto Process on Paste

Read `modes/_shared.md` before starting.

## Trigger
User pastes a URL, company name, LinkedIn URL, or company brief WITHOUT a specific command.

## Process

Automatically:
1. Detect it's a prospect input (not a command)
2. Run `prospect` mode (full evaluation)
3. Offer to draft outreach immediately after

Do NOT ask for permission to evaluate. Just do it and present the result.

After evaluation, ask:
> "Score: {X.X}/5 ({Grade}). Want me to draft the outreach message now?"
