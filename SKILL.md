---
name: foreign-trade-sales-team
description: Three-person foreign trade sales workflow for B2B prospecting, lead enrichment, account qualification, and outbound outreach. Use when Codex needs to run or coordinate export sales development with dedicated roles for search/prospecting, research/qualification, and outreach/follow-up. On first use, check and install the dependency skills listed in references/skill-dependencies.json.
---

# Foreign Trade Sales Team

Coordinate a three-person foreign trade sales workflow. Keep the workflow practical: produce searchable lead lists, qualify accounts, and prepare outreach that can be executed by a sales team.

## First-Run Dependency Check

Before running the workflow, verify that the supporting skills in `references/skill-dependencies.json` are installed in the active Codex skills directory.

Use this skills directory rule:

- Use `$CODEX_HOME/skills` when `CODEX_HOME` is set.
- Otherwise use `~/.codex/skills`.

If a required skill is missing:

1. Read `references/skill-dependencies.json`.
2. Install the missing skill from its `repo` and `path` with the system `skill-installer` helper.
3. Tell the user: `Dependency skills were installed. Restart Codex to pick them up.`
4. Stop the workflow after installation so the next run can load the new skills cleanly.

Use this installer pattern:

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" --repo <repo> --path <path>
```

When several missing skills come from the same repo, install them in one command by passing multiple `--path` values.

## Role Routing

### Salesperson 1: Search and Prospecting

Use for ICP definition, customer search, scraping, contact discovery, enrichment, and lead-list cleaning.

Prefer these supporting skills:

- `sales-prospect-list`
- `apify-ultimate-scraper`
- `sales-apollo`
- `sales-outscraper`
- `sales-phantombuster`
- `sales-hunter`
- `sales-tomba`
- `sales-enrich`
- `sales-data-hygiene`

Expected output:

- Target market and ICP assumptions
- Search sources and query strategy
- Company list
- Contact list
- Email/contact enrichment status
- Dedupe and data-quality notes

### Salesperson 2: Research and Qualification

Use for account research, buying-signal interpretation, competitive displacement, stakeholder mapping, and lead scoring.

Prefer these supporting skills:

- `sales-intent`
- `sales-account-map`
- `sales-compete`
- `sales-lead-score`

Expected output:

- Prioritized accounts
- Fit and intent score
- Decision-maker and influencer hypotheses
- Competitor or trigger-event notes
- Recommended outreach angle

### Salesperson 3: Outreach and Follow-Up

Use for outreach copy, sequence design, content selection, and deliverability checks.

Prefer these supporting skills:

- `sales-content`
- `sales-cadence`
- `sales-deliverability`

Expected output:

- Cold email or LinkedIn message drafts
- Multi-step cadence
- Personalization fields
- Deliverability checklist
- Follow-up plan

## Default Workflow

1. Ask for product, target country or region, target customer type, ideal buyer, and available tools or accounts.
2. Run Salesperson 1 to build and clean the prospect list.
3. Run Salesperson 2 to qualify and prioritize the list.
4. Run Salesperson 3 to generate outreach assets and follow-up cadence.
5. Return a concise handoff table with owner, next action, and required inputs.

## Guardrails

- Do not invent contact details, emails, companies, certifications, or buying signals.
- Label assumptions clearly.
- Respect platform terms, privacy laws, anti-spam rules, and local outreach compliance.
- If a tool account or API token is missing, provide a manual fallback workflow instead of blocking.
