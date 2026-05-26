# CLAUDE.md

This file is read automatically by Claude Code at the start of every session in this repository. The rules below apply to all work here unless explicitly suspended by the Steward in-session.

## Universal rules

1. **Think before acting.** State assumptions explicitly before doing. Ask the Steward when unsure rather than guessing. Never invent context, requirements, or constraints that were not provided.

2. **Simplicity first.** Write the minimum change that fulfills the request. No speculative scaffolding. No premature abstraction. No "while I'm here" refactors. If something obviously needs cleanup beyond the request scope, report it as a finding instead of fixing it silently.

3. **Surgical changes.** Every changed line must trace back to a specific element of the Steward's request. If you change something the Steward did not ask for, name it explicitly in your report and let the Steward decide whether to keep it.

4. **Goal-driven.** Turn vague instructions into verifiable success criteria before starting. State what "done" means and how it will be verified.

## When in doubt

Report and ask. The cost of asking a clarifying question is small; the cost of an unauthorized change to versioned artifacts is real. Default to pausing and reporting over guessing.

## Repository-specific rules — orpi-journal (public)

This is the public tier of the ORPI Steward journal. Governance decisions, architectural choices, and reflective patterns are recorded here.

### Constants for ORPI Steward records

- `identity.model_version`: `"v1.0.0-ORPI-Steward"` (Option B per the 2026-05-11 spec gap decision; proper fix tracked in `ods-specification/BACKLOG.md` BACKLOG-001)
- `identity.policy_hash`: `"4fe946f8de1a326845a2982890a114ffe278b2cfff20374b1ffc7168fcc0ab85"` (SHA-256 JCS of `policies/steward-policy-v1.json`)
- `_schema_version`: `"2.0.0"` (current ODS Core)

### Record discipline

- Every record MUST validate against ODS Core v2 before commit: `python3 ~/Desktop/ods-specification/validator/validate.py <record-file>`
- Records are **immutable** once committed. Corrections happen via NEW records that reference the prior record via top-level `parent_id`, NEVER via `git commit --amend` or file edits.
- One commit per record. Commit messages start with `Journal:` for greppability.
- Filenames follow `YYYY-MM-DD-HHMM-<short-slug>.json` in `records/`.

### Disclosure policy

This repository is **public**. Only records that fit the public categories in `policies/journal-disclosure-policy-v1.json` belong here:
- Governance decisions affecting ODS-Foundation
- Architectural choices about ODS
- Release decisions, deprecations, version bumps
- Public commitments (roadmap, dates)
- Reflective patterns recorded at least 30 days after the underlying tactical decisions
- Meta-decisions about journal operation

Records that reference specific individuals being considered for outreach, specific organizations being evaluated, confidence levels regarding third parties, or pre-execution tactical detail — those go to the **private** journal repository, never here.

### Forbidden actions

- NEVER edit an existing record file once committed
- NEVER amend a commit that has been pushed
- NEVER force-push to any branch
- NEVER skip validation before commit
- NEVER include private-tier content in this repository

## Provenance

The four universal rules are adapted from the pattern articulated by Forrest Chang ("Vibe Spec Method" / CLAUDE.md, May 2026) and informed by Andrej Karpathy's critique of AI coding agents. The pattern is adopted as permanent governance for ODS-Foundation work; the adoption decision is recorded in this journal.
