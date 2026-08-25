# Install (model-agnostic)

This pack follows the [Agent Skills](https://agentskills.io/specification)
open standard. One folder. One `SKILL.md`. Works anywhere the spec is
implemented.

Folder must be named `arc-ceb` to match the YAML `name` field.

```
arc-ceb/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── r1-r8.md
    ├── control-record.md
    ├── enumeration.md
    ├── scoring.md
    ├── conformance.md
    ├── repo-hygiene.md
    └── install.md
```

The repository also keeps a root `SKILL.md` as the public contract. The two
files are the same 1.0 protocol skill; the portable pack adds references
and host chrome.

## Claude

- **Claude.ai Skills:** Settings → Capabilities → Skills → Upload the `arc-ceb` folder (or zip).
- **Claude Code:** copy the folder to `~/.claude/skills/arc-ceb/` (user) or `.claude/skills/arc-ceb/` (repo).
- **Claude Projects:** attach `SKILL.md` as project knowledge and add: “Obey SKILL.md as ground truth. Do not invent R1–R8 classes. Do not reread prose to notice issues. Do not give CASE_MATRIX.md to blind scorers.”

## ChatGPT

- **Native Skills:** upload the same folder. ChatGPT reads `name` + `description`, then loads `SKILL.md` when the task matches. UI chrome lives in `agents/openai.yaml`.
- **Codex:** copy to `$HOME/.agents/skills/arc-ceb/` or `$REPO_ROOT/.agents/skills/arc-ceb/`. Invoke with `$arc-ceb`.
- **Custom GPT / Project (fallback):** paste the full `SKILL.md` into Instructions and prepend: “This SKILL.md is canonical for ARC-CEB-1.0. Follow the firewall.”

## Cursor / Grok / other agents

Drop the folder into that product’s skills directory. Do not rewrite classes
for the host. Implicit invocation is enabled because the description is
narrow (ARC-CEB, R1–R8, CandidateSet, NEXT_PROMPT). If a host fires this
skill on unrelated code review, tighten the description rather than
inventing a ninth class.

## Pairing with QOFT

The QOFT / QOSMOS skill is methodological provenance only. Load it when the
task is about Ξ, ψ, ⊕, or QOSMOS ticks. Do not fold glyph operators into
ARC-CEB enumeration. Canonical weight of ARC-CEB-1.0 remains none.
