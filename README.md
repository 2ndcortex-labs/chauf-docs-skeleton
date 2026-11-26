# Organization Chauffeur Docs (`chauf-docs`)

This repository stores **organization-owned** operating policies and per-worker working context for ephemeral **Chauffeur (`chauf`)** sessions (Antigravity and Codex).

## Structure

```text
.
├── shared/
│   ├── PLAYBOOK.md                # Org-wide operating policy (edit freely in GitHub)
│   └── templates/                 # Starter stubs copied when provisioning a new worker
│       ├── northstar.md
│       ├── manifesto.md
│       ├── BRIEF.md
│       ├── PLAYBOOK_local.md
│       ├── HANDOFF.md
│       └── DECISIONS.md
└── workers/
    └── <slug>/
        ├── northstar.md           # Ultimate goal, outcomes, non-negotiables (Operator-owned)
        ├── manifesto.md           # Principles, philosophy, quality & taste bar (Operator-owned)
        ├── BRIEF.md               # Project scope, repos, operational guardrails (Operator-owned)
        ├── PLAYBOOK_local.md      # Worker-specific additions/overrides to shared/PLAYBOOK.md
        ├── HANDOFF.md             # Living AG <-> Codex shift handoff (Chauffeur-writable)
        ├── DECISIONS.md           # Append-only Operator rulings & discoveries (Chauffeur-writable)
        └── notes/                 # Ad-hoc working specs, checklists, drafts (Chauffeur-writable)
```

## Ownership & Safety

- **Operator-owned files** (`shared/PLAYBOOK.md`, `northstar.md`, `manifesto.md`, `BRIEF.md`, `PLAYBOOK_local.md`) are edited by humans in GitHub and treated as read-only by Chauffeurs unless explicitly instructed.
- **Chauffeur-writable files** (`HANDOFF.md`, `DECISIONS.md`, `notes/**`) are updated during a shift so another tool or host can pick up seamlessly on the next drive.
- **Never commit secrets, tokens, passwords, or large binaries** to this repository.
