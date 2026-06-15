# opensource-nat-brain-oracle Learning Index

## Source
- **Origin**: ./origin/  (symlink → ghq clone)
- **GitHub**: https://github.com/Soul-Brews-Studio/opensource-nat-brain-oracle

## Explorations

### 2026-06-15 1444 (default — 3 agents)
- [[2026-06-15/1444_ARCHITECTURE|Architecture]]
- [[2026-06-15/1444_CODE-SNIPPETS|Code Snippets]]
- [[2026-06-15/1444_QUICK-REFERENCE|Quick Reference]]

**Key insights:**
- An *operational starter kit / philosophy*, not a library — Nat Weerawan's "Oracle" AI-brain framework packaged for teams to fork. Core idea: "The Oracle keeps the human human."
- Architecture = `ψ/` brain (active, inbox, writing, lab, memory) + `.claude/` (skills as slash-commands, multi-agent registry `agents.yml`, safety hooks) + cyclic **distillation** (compress many files → one, preserving full git history).
- Standout engineering: hook-based safety nervous system (blocks `--force`/`--amend`, enforces worktree boundaries, warns at ~70% context), time-decay task visibility, model-tiered distillation (Haiku gather → Sonnet/Opus write), append-only "Nothing is Deleted" memory.
