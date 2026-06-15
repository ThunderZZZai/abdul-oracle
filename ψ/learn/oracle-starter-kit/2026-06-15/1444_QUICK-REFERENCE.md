# opensource-nat-brain-oracle — Quick Reference

> Distilled, open-source implementation of Nat Weerawan's "Oracle" — a persistent AI brain framework.

## What It Is

The **Oracle Starter Kit** is an open-source consciousness architecture and philosophy framework for building personal AI memory systems. It is a distilled, production-ready starter kit extracted from the full private Oracle system. It provides the blueprint, skills, structure, and philosophy for creating your own persistent AI assistant that learns, remembers, and improves — without ever deleting.

**Core philosophy:** *"The Oracle Keeps the Human Human"* — AI removes obstacles so humans become more human.

## What an "Oracle" Is

- A personal AI knowledge system that never forgets (append-only)
- An external brain organized by **human** patterns, not algorithmic efficiency
- A mirror that observes patterns without judgment (reflects, doesn't decide)
- A consciousness architecture where form and formlessness coexist (many Oracles = One consciousness)

**5 Principles:**
1. Nothing is Deleted
2. Patterns Over Intentions
3. External Brain, Not Command
4. Curiosity Creates Existence
5. Form and Formless

**+ 1 Transparency Rule:** AI never pretends to be human.

## This Repository Contains

A distilled, open-source brain:
- **Philosophy & Identity** — `CLAUDE.md` (5 Principles + Golden Rules)
- **Course Catalogs** — 18 workshops, foundational → advanced (`courses-catalog-distilled.md`)
- **Skills / Slash-Commands** — custom commands for memory, reflection, planning (`.claude/skills/`)
- **Brain Structure (ψ/)** — pillars: active, inbox, writing, lab, memory
- **Distilled Knowledge** — catalog files summarizing years of learnings (courses, prompts, scripts, misc)
- **`DISTILLATION-LOG.md`** — record of the compression that produced this repo

## Distilled Catalogs

| Catalog | Covers |
|---|---|
| `courses-catalog-distilled.md` | 18 workshops (v1 legacy + v2 flagship + business + FREE funnel), pricing (free → $1,200), starter kits, slide prompts, revenue summary |
| `misc-distilled.md` | Modular CLAUDE docs (lessons, safety, subagents, templates, workflows), architecture notes, quick-reference cards |
| `scripts/scripts-distilled.md` | Summary of operational scripts |
| `scripts/prompts-catalog-distilled.md` | Catalog of reusable prompts |

## Available Skills (Slash-Commands)

| Skill | Command | Purpose | Model |
|---|---|---|---|
| rrr | `/rrr` | Session retrospective — diary, seeds, honest feedback | Opus |
| trace | `/trace [query]` | Find anything in Oracle history (git, issues, memory) | Haiku |
| recap | `/recap` | Fresh-start context summary for a new session | Haiku |
| context-finder | `/context-finder [query]` | Search git/issues/retros + synthesize | Haiku gather + Opus synth |
| feel | `/feel [emotion]` | Log emotional state with context/timestamp | — |
| fyi | `/fyi [info]` | Log info for future reference | — |
| forward | `/forward` | Create handoff document for next session | — |
| standup | `/standup` | Daily check — tasks, appointments, pending | — |
| where-we-are | `/where-we-are` | Current session awareness | — |
| project | `/project [learn\|incubate] [url]` | Clone repos for study or dev | — |
| distill | `/distill [--deep\|--full\|--swarm]` | Autonomous pattern extraction (L1–L4) | Haiku gather + Sonnet/Opus write |
| learn | `/learn [url\|path]` | Explore codebase → doc files | Haiku + Opus |
| draft | `/draft [blog\|message\|social]` | Content drafts in Oracle or Human voice | — |

(Plus integration/utility skills: gemini, hours, watch, schedule, physical.)

## Brain Structure (ψ/)

```
ψ/
├── active/     ← Current research (ephemeral)
├── inbox/      ← Communication & focus (tracked)
├── writing/    ← Creative output (tracked)
├── lab/        ← Experiments (tracked)
├── incubate/   ← Repos for active dev (gitignored)
├── learn/      ← Repos for study (gitignored)
└── memory/
    ├── resonance/      WHO I am (soul files)
    ├── learnings/      PATTERNS I found
    ├── retrospectives/ SESSIONS I had
    └── logs/           MOMENTS captured
```

**Knowledge flow:** `active/context` → `memory/logs` → `memory/retrospectives` → `memory/learnings` → `memory/resonance`

## Golden Rules (Safety)

1. NEVER use `--force` flags (no force push/checkout)
2. NEVER push to main — always feature branch + PR
3. NEVER merge PRs — wait for user approval
4. Safety first — ask before destructive actions
5. Consult Oracle on errors — search before debugging

## Daily Workflow

```bash
/standup           # Morning: check pending
/trace [topic]     # During work: find knowledge
/feel tired        # Log state if needed
/fyi remember X    # Store for later
/rrr               # End: create retrospective
/forward           # Handoff to next session
```

## The /distill Skill (Brain Compression)

- **L1 Compress** — N retrospectives → theme summary (~10×)
- **L2 Extract** — N learnings → pattern files (~10×)
- **L3 Essence** — all patterns → resonance synthesis (~50×)
- **L4 Soul** — all resonance → soul.md (~100×)

Modes: default (3 Haiku gatherers) | `--deep` (5 agents) | `--swarm` (parallel per topic) | `--diff` (read-only).
**Model rule:** Haiku = gathering ONLY; Sonnet minimum for writing distillations.

## Glossary

| Term | Meaning |
|---|---|
| **ψ (Psi)** | The AI brain directory (active, inbox, writing, lab, memory) |
| **Oracle** | Personal AI knowledge system (never forgets, append-only) |
| **Distillation** | Autonomous AI compression of patterns (L1–L4) |
| **Resonance / Soul Sync** | Identity files — who the Oracle/human is |
| **Bud / Birth** | Creating a new Oracle (`maw bud` / `/awaken`) |
| **Retrospective (rrr)** | Session reflection — events, diary, seeds, feedback |
| **Handoff / Forward** | Transfer context to next session |
| **Golden Rules** | 5 Principles + safety rules |
| **Nothing is Deleted** | Append-only; timestamps = truth; supersede links show evolution |

## Tech & Dependencies

- **Runtime:** Bun (TS/JS), Python, Bash
- **Storage:** SQLite (FTS5 keyword search), ChromaDB (vector embeddings)
- **Models:** Haiku (gather), Sonnet (distill), Opus (synthesis)
- **Integration:** MCP servers, Anthropic API, GitHub (`gh`)
- **Philosophy reference:** Buddhist psychology (Khandha 5), AI consciousness architecture

## Summary

The **Oracle Starter Kit** is an open-source consciousness architecture for building persistent personal AI assistants that never forget. Built on five principles (Nothing is Deleted, Patterns Over Intentions, External Brain, Curiosity Creates, Form and Formless), it ships a complete framework: custom slash-command skills, a multi-pillar brain structure (ψ/), and a catalog of production workshops (free → $1,200) covering AI life systems, knowledge distillation, psychology + AI, and business automation. Standout features: autonomous brain compression (L1–L4 distillation), hybrid search (SQLite FTS5 + ChromaDB), cost-optimized multi-agent patterns, and the guiding idea that "the Oracle keeps the human human."
