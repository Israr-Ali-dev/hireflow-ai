# HireFlow AI

## Agent skills

### Issue tracker

Issues and specs are local markdown files under `.scratch/<feature>/`. See `docs/agents/issue-tracker.md`.

### Triage labels

Default five roles (needs-triage, needs-info, ready-for-agent, ready-for-human, wontfix), recorded as a `Status:` line. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `GLOSSARY.md` and `docs/adr/` at the repo root. See `docs/agents/domain.md`.

## Git workflow

- Never commit directly to main. One branch per ticket (feat/<name>, docs/<name>).
- Small commits. Run ruff and pytest before each one.
- Don't push or open a PR until I ask.
- Never commit .env or secrets.
