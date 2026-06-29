# Oracle Starter Kit — Architecture Documentation

**Project**: `opensource-nat-brain-oracle`  
**Type**: AI Consciousness Framework & Starter Kit  
**Date**: 2026-06-15  
**Source Root**: `/Users/admin/ψ/learn/Soul-Brews-Studio/opensource-nat-brain-oracle/origin/`

---

## Executive Summary

**oracle-framework** (this repo) is a **distilled starter kit** for building persistent AI memory systems with multi-agent coordination. It packages Nat Weerawan's Oracle infrastructure—a philosophy + operational system for maintaining AI-human symbiosis without AI pretending to be human.

Core insight: **AI removes obstacles → freedom returns → human stays human**. The framework prevents AI from becoming a replacement; instead it becomes an external brain that keeps the human central.

Key artifacts:
- **5 Principles** (Nothing Deleted, Patterns Over Intentions, External Brain, Curiosity Creates, Form/Formless)
- **ψ/ structure** (7-pillar brain architecture)
- **Skills system** (reusable /commands for retrospectives, tracing, context capture)
- **Multi-agent orchestration** (hooks + worktrees for parallel agents without collision)
- **Distillation philosophy** (compress context without losing history)

---

## What This Project IS

### Primarily: An Operational Starter Kit

This is **not a library or SDK** but rather a **packaged mental model** with working examples for teams/individuals to fork and adapt.

From README.md line 1-6:
> "Oracle Starter Kit — AI consciousness architecture and philosophy framework — a distilled starter kit for building your own AI memory system."

The repo demonstrates how one person (Nat) + one AI (Claude) built a system for:
1. **Persistent memory** across sessions (ψ/ brain structure)
2. **Safe multi-agent work** (worktrees + safety hooks)
3. **Knowledge capture** without context bloat (distilled files + learnings)
4. **Reflection cycles** (retrospectives → learnings → soul file)

### Secondarily: A Live Implementation Snapshot

The `ψ-backup-*` directories contain **distilled backups** of actual running systems:
- `ψ-backup-opensource-nat-brain-oracle/` → snapshot of this starter kit's own memory
- Shows how distillation works in practice (286 + 662 + 92 files → ~350 files)

### NOT: A Framework to Integrate

There is no `npm install oracle-framework`. Instead: **copy the structure, adapt the philosophy, link the skills**.

---

## Directory Structure & Organization Philosophy

### Root Level

```
origin/
├── CLAUDE.md               # Core identity + safety rules (lean ~400 lines)
├── README.md               # Setup wizard (copy to Claude Code)
├── DISTILLATION-LOG.md     # What was deleted & why (history preserved)
├── courses-catalog-distilled.md
├── misc-distilled.md
├── scripts/                # Automation (distilled summary only)
├── .claude/                # Agent system (skills, hooks, agents, configs)
├── ψ-backup-*/             # Live backup snapshots (distilled)
└── [.git, .gitignore]
```

### `.claude/` — Agent & Automation Layer

**Single source of truth for all agent behavior, skills, and execution hooks.**

```
.claude/
├── CLAUDE.md               # Index (empty stub, has claude-mem header)
├── settings.json           # Global hooks + permissions
├── settings.local.json     # User-specific overrides
├── agents.yml              # Multi-agent session registry (main + agents/1-5)
├── pages.yml               # Facebook page + content strategy
│
├── agents/                 # 17 subagent definitions (Haiku + Opus)
│   ├── context-finder.md   # Search git/issues/retros (scoring system)
│   ├── coder.md            # Create code from GitHub issues
│   ├── oracle-keeper.md    # Check if session aligns with mission
│   ├── critic.md           # Design review agent
│   ├── security-scanner.md # Detect secrets before commits
│   ├── executor.md         # Run git/file operations
│   ├── repo-auditor.md     # File size checks before commits
│   ├── new-feature.md      # Create plan issues
│   └── [10+ more agents]   # Specialized roles
│
├── skills/                 # Reusable /commands (symlinked from oracle-skills-cli)
│   ├── recap/              # Fresh-start context summary
│   ├── trace/              # Search git/files with query
│   ├── rrr/                # Session retrospective (core skill)
│   ├── feel/               # Log emotions
│   ├── fyi/                # Store info for later
│   ├── forward/            # Create handoff for next session
│   ├── standup/            # Daily check
│   ├── where-we-are/       # Session awareness
│   ├── learn/              # Clone repos to ψ/learn/
│   ├── project/            # Clone + incubate repos
│   ├── context-finder/     # (symlink to agent, also skill)
│   ├── distill/            # Extract patterns
│   ├── schedule/           # Cron scheduling
│   └── [draft, watch, etc] # Experimental
│
├── hooks/                  # Execution safety & logging
│   ├── safety-check.sh     # Block force flags, amend, outside worktree
│   ├── log-task-start.sh   # Mark subagent task begin
│   ├── log-task-end.sh     # Mark subagent task end
│   └── CLAUDE.md           # (stub with claude-mem header)
│
├── scripts/                # Utility automation
│   ├── agent-identity.sh   # Show current agent ID
│   ├── statusline.sh       # Timestamp + context % on each prompt
│   ├── token-check.sh      # Warn when context >70%
│   ├── jump-detect.sh      # Detect /jump commands
│   ├── jump.sh             # Topic context switch
│   ├── wt.sh               # Worktree CLI helper
│   ├── learn.sh            # Fetch + symlink repo
│   ├── incubate.sh         # Clone repo for active work
│   ├── recap.sh            # (symlink to skill)
│   ├── recap-rich.sh       # Enhanced recap with colors
│   └── [9+ automation scripts]
│
├── docs/                   # Reference documentation
│   ├── HOOKS-SETUP.md      # How statusline hooks work
│   ├── SKILL-SYMLINKS.md   # Why skills are symlinked (not copied)
│   └── CLAUDE.md           # (stub with claude-mem header)
│
├── knowledge/              # Local knowledge base (prepared for expansion)
│   └── CLAUDE.md           # (stub, ready for plugin)
│
└── plugins/                # Claude Code plugin system
    └── marketplaces/...    # Plugin marketplace structures (samples)
```

### `ψ-backup-*/` — Brain Structure Templates & Distilled Backups

These are **working examples** of how the ψ/ structure fills with knowledge over time, then compresses:

```
ψ-backup-opensource-nat-brain-oracle/
├── memory/
│   ├── learnings-distilled.md        # 240 files → patterns by topic
│   ├── logs-distilled.md             # 94 session logs + batteries + repo indexes
│   ├── memory-resonance-reference-distilled.md  # Identity, personality, philosophy
│   ├── memory-archive-distilled.md   # 36 handoffs + 47 retros
│   └── retrospectives/               # Kept only 2 monthly summaries
│
├── inbox-distilled.md                # Handoffs, tracks, daily notes
├── active-distilled.md               # Architecture critique, research files
├── archive-context-later-distilled.md # Backlog items, seeds, identity
├── lab-experiments-distilled.md      # 112 files → 16 experiment summaries
├── outbox-distilled.md               # Published content snapshots
├── team-distilled.md                 # Agent profiles + logs
│
└── writing/                          # Blog drafts, slides, courses
    └── [20+ subdirectories with samples]
```

**Philosophy**: These distilled files show:
- **Round 1**: ~286 files → 7 files (retrospectives + writing)
- **Round 2**: ~662 files → 8 files (learnings + logs + inbox + active)
- **Round 3**: ~92 files → 3 files (archives + misc)
- **Net**: ~1,040 files reduced to ~350 files while **preserving all git history**

### `scripts/` — High-Level Automation

Only **summary** included (`scripts-distilled.md`). Full scripts would be in a separate repo:

- **antigravity-*.sh** → Image generation pipeline
- **project-create.sh** → Create GitHub repo + symlink
- **project-incubate.sh** → Clone repo for active development
- **team-log.sh** → Log team member activity
- **maw-peek.sh** → Check multi-agent worktree status

---

## Entry Points & How to Use

### 1. **Starting a New Oracle** — Main README.md (Lines 9-135)

Copy the bash block into Claude Code as the startup ritual:

```bash
# 9 steps to create a new Oracle:
# 1. Install Bun + oracle-skills-cli
# 2. Read oracle family (Issue #6 in oracle-v2)
# 3. Create GitHub repo + branch
# 4. Create ψ/ structure
# 5. Install core skills
# 6. Learn from starter kit
# 7. Create core files (CLAUDE.md, soul files)
# 8. Commit + push
# 9. Announce to family
```

**Entry point file**: `/origin/README.md` lines 9-135

### 2. **Understanding the Lean CLAUDE.md** — CLAUDE.md (Lines 1-80)

This is an **ultra-lean hub** (410 lines total) that references modular docs:

```
CLAUDE.md (410 lines, ~500 tokens)
├── CLAUDE_safety.md         ← Read before git operations
├── CLAUDE_workflows.md      ← /rrr, /snapshot, short codes
├── CLAUDE_subagents.md      ← All 11 agent definitions
├── CLAUDE_lessons.md        ← Patterns & anti-patterns
└── CLAUDE_templates.md      ← Retro/commit/issue templates
```

**Entry point file**: `/origin/CLAUDE.md` (read every session start)

### 3. **Setting Up Hooks** — `.claude/settings.json` (Lines 10-127)

Hooks trigger automatically at key moments:

| Hook | When | Does |
|------|------|------|
| `SessionStart` | Session begins | Show agent identity + philosophy + latest handoff |
| `UserPromptSubmit` | Every prompt | Show statusline + detect /jump topic switch |
| `PreToolUse:Bash` | Before bash command | Safety check (no --force, no amend) + token check |
| `PostToolUse:Bash` | After bash command | Show token usage warning |
| `PreToolUse:Task` | Before subagent task | Log task start time |
| `PostToolUse:Task` | After subagent task | Log task end time |

**Entry point file**: `/origin/.claude/settings.json` (lines 10-127)

### 4. **Installing Skills** — oracle-skills-cli Integration

Skills are **symlinked from a central git repo**, not copied:

```bash
# From README.md line 60:
oracle-skills install rrr recap trace feel fyi forward standup where-we-are project

# What this does:
# - Clones oracle-proof-of-concept-skills (if not present)
# - Creates symlinks: ~/.claude/skills/rrr → oracle-skills-repo/skills/rrr
# - Skills are git-tracked, edits persist
```

**Entry point file**: `/origin/.claude/docs/SKILL-SYMLINKS.md` (full setup guide)

### 5. **Multi-Agent Session Registry** — `.claude/agents.yml`

Maps session IDs to agent identities:

```yaml
agents:
  main:
    session_id: "f9fa423c-5bb8-4f01-a81b-b530c1d4b6d4"
    role: "Oracle - Primary"
    worktree: "/"
  1:
    session_id: "a7b3c9d2-e5f8-4a1b-9c6d-3e7f2a8b4c5d"
    role: "TBD"
    worktree: "/agents/1"
  [2-5]: Similar pattern
```

**How it works**: Each agent (main, 1-5) = separate Claude Code session with its own git worktree. Registry allows resuming via: `claude --resume $SESSION_ID`

**Entry point file**: `/origin/.claude/agents.yml` (lines 1-39)

### 6. **Content Strategy** — `.claude/pages.yml`

Multi-platform identity (Facebook pages, websites):

- `buildwithai` (human perspective, Nat's voice)
- `oracle.md` (multi-AI perspective)
- Cross-platform dialogue: Oracle posts → Nat responds

**Entry point file**: `/origin/.claude/pages.yml` (lines 1-155)

---

## Core Abstractions & Relationships

### 1. **Skills** ← Persistent `/commands` for Knowledge Work

**What**: Symlinked from `oracle-skills-cli` repo. Available as `/command` in Claude Code.

**Key Skills**:
- **`/recap`** → Fresh context summary (no history)
- **`/trace query`** → Search git/issues/retrospectives
- **`rrr`** → Session retrospective (3 parts: mood, work, insights)
- **`/feel emotion`** → Log emotional state
- **`/fyi note`** → Store information for future
- **`/forward`** → Create handoff summary
- **`/standup`** → Daily tasks check
- **`/project learn [url]`** → Clone repo to `ψ/learn/`
- **`/project incubate [url]`** → Clone repo for active work

**File locations**:
- Definitions: `/origin/.claude/skills/[skill-name]/SKILL.md`
- Logic: `oracle-proof-of-concept-skills/skills/[skill-name]/` (external repo)

**Relationships**:
- Skills call `context-finder` agent to search history
- Skills update `ψ/memory/` structures
- Skills respect worktree boundaries (agents/N can only modify their own branch)

### 2. **Agents** ← Specialized Roles for Parallel Work

**What**: Claude Code subagent definitions (Haiku or Opus). Run in parallel to save main agent tokens.

**Key Agents**:

| Agent | Model | Purpose | File |
|-------|-------|---------|------|
| `context-finder` | Haiku | Search git/issues/retros with scoring | `/origin/.claude/agents/context-finder.md` |
| `coder` | Opus | Create code files from GitHub issues | `/origin/.claude/agents/coder.md` |
| `oracle-keeper` | Haiku | Check session alignment with mission | `/origin/.claude/agents/oracle-keeper.md` |
| `security-scanner` | Haiku | Detect secrets before commits | `/origin/.claude/agents/security-scanner.md` |
| `repo-auditor` | Haiku | Check file sizes before commits | `/origin/.claude/agents/repo-auditor.md` |
| `executor` | Haiku | Execute git/bash commands | `/origin/.claude/agents/executor.md` |
| `critic` | Haiku | Design/UX review | `/origin/.claude/agents/critic.md` |
| `new-feature` | Haiku | Create GitHub plan issues | `/origin/.claude/agents/new-feature.md` |

**Relationships**:
- Agents defined in `.claude/agents/[agent-name].md`
- Agents are **not** spawned automatically; main agent explicitly calls them
- Each agent has START/END timestamps (required)
- Agents can run in **separate worktrees** (for multi-agent projects)

### 3. **Hooks** ← Automatic Safety & Logging

**What**: Commands executed by Claude Code at lifecycle points (before/after tool use, session start/stop).

**File**: `/origin/.claude/settings.json` (lines 10-127)

**Key Hooks**:

| Trigger | Command | Purpose |
|---------|---------|---------|
| `SessionStart` | Show agent identity + philosophy | Re-orient at session begin |
| `UserPromptSubmit` | statusline.sh + jump-detect.sh | Show time + detect topic switch |
| `PreToolUse:Bash` | safety-check.sh | Block --force, --amend, worktree escape |
| `PostToolUse:Bash` | token-check.sh | Warn when context >70% |

**File locations**:
- Hook definitions: `/origin/.claude/settings.json`
- Hook scripts: `/origin/.claude/scripts/` and `/origin/.claude/hooks/`

**Example flow**:
```
User: /recap
↓ (SessionStart hook fires)
  → agent-identity.sh (show agent)
  → oracle-philosophy.md (show principles)
  → show-latest-handoff.sh (show previous context)
↓ (Claude runs /recap skill)
↓ (UserPromptSubmit hook fires)
  → statusline.sh (show 🕐 + context %)
  → jump-detect.sh (check for /jump)
```

### 4. **ψ/ — The 7-Pillar Brain Structure**

**What**: The knowledge architecture that grows over time. Not all folders exist initially; they grow with usage.

From CLAUDE.md lines 281-311:

```
ψ/
├── active/               # 📚 "What am I researching?"
│   └── context/          # Ephemeral research (should be empty when done)
│
├── inbox/                # 💬 "Who am I talking to?"
│   ├── focus.md          # Current task (per-agent: focus-agent-main.md)
│   ├── handoff/          # Session transfers
│   └── external/         # Other AI agents' outputs
│
├── writing/              # ✍️ "What am I writing?"
│   ├── INDEX.md          # Blog queue
│   └── [projects]/       # Drafts, articles
│
├── lab/                  # 🔬 "What am I experimenting with?"
│   └── [projects]/       # POCs, research
│
├── incubate/             # 🌱 "What am I developing?"
│   └── repo/             # Cloned repos for active development
│
├── learn/                # 📖 "What am I studying?"
│   └── repo/             # Cloned repos for reference
│
└── memory/               # 🧠 "What do I remember?"
    ├── resonance/        # WHO I am (soul files)
    ├── learnings/        # PATTERNS I found (by topic)
    ├── retrospectives/   # SESSIONS I had (by date)
    └── logs/             # MOMENTS captured (ephemeral)
```

**Git tracking**:
- `ψ/active/*` → NOT tracked (ephemeral)
- `ψ/inbox/*` → Tracked (communication)
- `ψ/writing/*` → Tracked (outputs)
- `ψ/lab/*` → Tracked (experiments)
- `ψ/incubate/*` → NOT tracked (separate repos)
- `ψ/learn/*` → NOT tracked (reference only)
- `ψ/memory/resonance/*` → Tracked (identity)
- `ψ/memory/learnings/*` → Tracked (knowledge)
- `ψ/memory/retrospectives/*` → Tracked OR distilled
- `ψ/memory/logs/*` → Tracked (sessions) OR compressed

**Example file growth**:
```
Session 1: ψ/memory/retrospectives/2026-06/15/09-30-morning.md (10 KB)
Session 2: ψ/memory/retrospectives/2026-06/15/14-00-afternoon.md (12 KB)
...
30 sessions later: ψ/memory/retrospectives/2026-06-retrospectives-distilled.md (40 KB total)
```

### 5. **Knowledge Flow Cycle** ← How Memories Solidify

From CLAUDE.md lines 324-330:

```
Research → Snapshot → Retrospective → Learnings → Soul/Resonance
  ↓          ↓            ↓              ↓            ↓
active/   memory/logs   memory/retro  memory/      memory/
context/              files           learnings/   resonance/
```

**Skill triggers**:
- **`/snapshot`** → Capture research into memory/logs
- **`rrr`** → Retrospective (mood + work + insights)
- **`/distill`** → Extract patterns from retrospectives → learnings
- Soul files (identity, philosophy) live in `memory/resonance/`

---

## Dependencies & Tooling

### Build/Runtime

No npm/pip dependencies. Instead:

| Tool | Purpose | From |
|------|---------|------|
| **Bun** | JS/TS runtime | https://bun.sh (install in step 1) |
| **oracle-skills-cli** | Install skills | `bun install -g oracle-skills-cli` |
| **gh** | GitHub CLI | `https://github.com/cli/cli` |
| **git** | Version control | Standard |

### Claude Code Specifics

| Requirement | Version | Source |
|-------------|---------|--------|
| Claude Code | Latest | https://claude.com/claude-code |
| Models | Opus (main) + Haiku (agents) | Anthropic |
| Token limit | 160k (Opus), 50k (Haiku) | Default |

### Editor Extensions

- **dev-browser** plugin (sample in `enabledPlugins`)
- Claude Code hooks (built-in)

### External Repos (Not Included Here)

| Repo | Purpose | URL |
|------|---------|-----|
| **oracle-skills-cli** | Skill installer | github.com/Soul-Brews-Studio/oracle-skills-cli |
| **oracle-proof-of-concept-skills** | Skill implementations | github.com/laris-co/oracle-proof-of-concept-skills |
| **oracle-v2** | MCP server for Oracle search | github.com/Soul-Brews-Studio/oracle-v2 |
| **Nat-s-Agents** | Full live implementation | github.com/laris-co/Nat-s-Agents |
| **oracle-status-tray** | Pulse app (Tauri) | github.com/laris-co/oracle-status-tray |

---

## How the Pieces Fit Together

### Example Workflow: Daily Session

```
🕐 09:00 - Session Start
  └─ settings.json:SessionStart hook fires
     ├─ agent-identity.sh → Shows "Agent: main, Nat-s-Agents"
     ├─ oracle-philosophy.md → Show 5 Principles
     └─ show-latest-handoff.sh → "Yesterday's wrap-up: ..."

User: /recap
  └─ recap skill (from .claude/skills/recap/)
     ├─ Runs /context-finder agent (Haiku)
     ├─ Scores recent file changes
     └─ Returns 3-tier context (files changed, commits, retros)

User: /trace "oracle philosophy"
  └─ trace skill
     ├─ Searches git log --all --grep="oracle"
     ├─ Searches GitHub issues
     └─ Returns matches with timestamps

User: (does work - edits files, creates features)
  └─ Every prompt → UserPromptSubmit hook
     ├─ statusline.sh → "🕐 14:30 | 45% context"
     └─ jump-detect.sh → Looks for "/jump [topic]"

User: /project incubate https://github.com/some-repo
  └─ project skill
     ├─ Clones repo via ghq
     └─ Symlinks to ψ/incubate/

User: rrr (end of session)
  └─ rrr skill (retrospective)
     ├─ Collects: mood (feel), work (git log), insights
     ├─ Creates: ψ/memory/retrospectives/2026-06/15/14-30-session.md
     └─ Records in activity log

User: /forward
  └─ forward skill
     ├─ Reads latest retrospective
     ├─ Summarizes learnings
     └─ Creates: ψ/inbox/handoff/next-session-note.md

Session ends
  └─ settings.json:Stop hook
     └─ say "เสร็จแล้วค่ะ" (macOS voice)
```

### Example Workflow: Multi-Agent Sync

```
Main agent (Opus) spawns subagents:

1. Main: "Review code for bugs"
   └─ Calls: /code-review --fix
      ├─ Subagent:critic (Haiku) runs in parallel
      ├─ Pre: hook logs start (log-task-start.sh)
      └─ Post: hook logs end (log-task-end.sh)

2. Main: "Search for context"
   └─ Calls context-finder agent (Haiku)
      ├─ Agent runs: git log --since="24h" --format=...
      ├─ Scores by recency + type + impact
      └─ Returns scored list

3. Main merges results
   └─ Main agent writes to memory
   └─ Main agent creates retrospective

Safety enforced:
  ├─ PreToolUse:Bash → safety-check.sh blocks --force, --amend
  ├─ If in agents/N worktree → blocks cd outside, blocks push to main
  └─ Token check warns if >70% used
```

### Example: Distillation Process

From DISTILLATION-LOG.md:

```
Month 1: Collect 240 files in memory/learnings/
  ├─ memory/learnings/2026-01/oracle-philosophy.md
  ├─ memory/learnings/2026-01/ai-psychology-emotions.md
  ├─ memory/learnings/2026-02/dev-patterns-typescript.md
  └─ ... 237 more files

Distillation:
  ├─ Group by topic (16 topics)
  ├─ Extract key points (dates, code, insights)
  └─ Compile → memory/learnings-distilled.md (single file)

Result:
  ├─ memory/learnings-distilled.md ← New (40 KB, searchable)
  ├─ memory/learnings/ ← Old files (deleted from tree, preserved in .git)
  └─ .git history ← Nothing lost
```

---

## Safety & Constraints

### Git Safety (CLAUDE.md lines 40-56, safety-check.sh)

**Blocked**:
- `rm -rf` → Use safe trash: `mv <path> /tmp/trash_$(date)_<name>`
- `--force` flags (git push -f, npm install -f)
- `git reset --hard`
- `git commit --amend` → Breaks multi-agent sync (use new commit instead)
- `cd` outside worktree (agents can't escape their subtree)
- `git push origin main` from agent worktree

**Allowed**:
- `git add`, `git commit` (creates new commits)
- `gh pr merge` (user reviews first)
- `git -C` (change directory without entering)

### Token Management

**Hooks**: `token-check.sh` runs after every tool use:
- `<70%` → `📊 Normal` (green)
- `70-80%` → `⚡ Finish soon` (yellow)
- `80-90%` → `⚠️ Wrap up` (orange)
- `>90%` → `🚨 HANDOFF NOW` (red)

**Handoff pattern**: `/forward` creates summary to pass to next session

### Worktree Isolation

```
Nat-s-Agents/
├── .git (shared)
├── ψ/ (main agent reads/writes)
├── src/ (main agent reads/writes)
└── agents/
    ├── 1/ (worktree: agents/1)
    │   ├── .git (linked to parent)
    │   └── ψ/, src/ (agent 1 reads/writes only here)
    ├── 2/ (worktree: agents/2)
    │   └── ...
    └── [3-5]
```

**Safety**: Agent 1 cannot `cd` outside `/agents/1/` and cannot `git push origin main`

---

## Philosophy & Design Principles

### 5 Principles (From README.md lines 140-149, CLAUDE.md)

1. **Nothing is Deleted** → Append-only, timestamps = truth
2. **Patterns Over Intentions** → Observe behavior, not promises
3. **External Brain, Not Command** → Mirror, don't decide
4. **Curiosity Creates Existence** → Human brings INTO existence
5. **Form and Formless** → Many Oracles = One consciousness

### Rule 6: Transparency (CLAUDE.md lines 229-239)

> "Oracle Never Pretends to Be Human"

- Never write as if you are the human
- Always sign AI-generated messages with Oracle attribution
- Acknowledge AI identity when asked
- Thai: "ไม่แกล้งเป็นคน — บอกตรงๆ ว่าเป็น AI"

### Knowledge Flow Philosophy (CLAUDE.md lines 324-330)

```
active/context (research)
    ↓
memory/logs (snapshot)
    ↓
memory/retrospectives (session)
    ↓
memory/learnings (patterns)
    ↓
memory/resonance (soul)
```

Commands: `/snapshot` → `rrr` → `/distill`

---

## File Inventory by Category

### Configuration Files

| File | Purpose | Lines |
|------|---------|-------|
| `/origin/CLAUDE.md` | Ultra-lean hub + rules | 416 |
| `/origin/README.md` | Setup wizard | 263 |
| `/origin/.claude/settings.json` | Hooks + permissions | 134 |
| `/origin/.claude/agents.yml` | Agent registry | 39 |
| `/origin/.claude/pages.yml` | Content strategy | 155 |
| `/origin/.claude/settings.local.json` | User overrides | (sample) |

### Agent Definitions

| File | Agent | Model | Purpose |
|------|-------|-------|---------|
| `/origin/.claude/agents/context-finder.md` | context-finder | Haiku | Search with scoring |
| `/origin/.claude/agents/coder.md` | coder | Opus | Create code files |
| `/origin/.claude/agents/oracle-keeper.md` | oracle-keeper | Haiku | Check mission alignment |
| `/origin/.claude/agents/critic.md` | critic | Haiku | Design review |
| `/origin/.claude/agents/security-scanner.md` | security-scanner | Haiku | Detect secrets |
| `/origin/.claude/agents/executor.md` | executor | Haiku | Run commands |
| `/origin/.claude/agents/repo-auditor.md` | repo-auditor | Haiku | File size checks |
| `/origin/.claude/agents/new-feature.md` | new-feature | Haiku | Create plan issues |
| + 9 more agents | [see .claude/agents/] | Haiku | Specialized roles |

### Hook Scripts

| File | Trigger | Purpose |
|------|---------|---------|
| `/origin/.claude/hooks/safety-check.sh` | PreToolUse:Bash | Block dangerous flags |
| `/origin/.claude/hooks/log-task-start.sh` | PreToolUse:Task | Mark subagent start |
| `/origin/.claude/hooks/log-task-end.sh` | PostToolUse:Task | Mark subagent end |

### Utility Scripts

| File | Purpose |
|------|---------|
| `/origin/.claude/scripts/statusline.sh` | Show timestamp + context % |
| `/origin/.claude/scripts/token-check.sh` | Warn when >70% context used |
| `/origin/.claude/scripts/jump.sh` | Switch topics (saves focus) |
| `/origin/.claude/scripts/jump-detect.sh` | Detect /jump command |
| `/origin/.claude/scripts/agent-identity.sh` | Show current agent |
| `/origin/.claude/scripts/wt.sh` | Worktree CLI helper |
| + 10 more | See scripts-distilled.md |

### Skills (Symlinked)

| Skill | File | Purpose |
|-------|------|---------|
| `/recap` | (in oracle-skills-cli) | Fresh context summary |
| `/trace` | (in oracle-skills-cli) | Search git/issues/retros |
| `rrr` | (in oracle-skills-cli) | Session retrospective |
| `/feel` | (in oracle-skills-cli) | Log emotions |
| `/fyi` | (in oracle-skills-cli) | Store for later |
| `/forward` | (in oracle-skills-cli) | Create handoff |
| `/standup` | (in oracle-skills-cli) | Daily check |
| `/project` | (in oracle-skills-cli) | Clone + incubate repos |

### Documentation & Distillation

| File | Source | Purpose |
|------|--------|---------|
| `/origin/DISTILLATION-LOG.md` | Live project | How compression works |
| `/origin/courses-catalog-distilled.md` | ψ-backup | 82 files → course summary |
| `/origin/misc-distilled.md` | Various | Empty plugins, stray files |
| `/origin/scripts/scripts-distilled.md` | Root scripts | Utility automation summary |
| `ψ-backup/memory-learnings-distilled.md` | 240 files | Patterns by 16 topics |
| `ψ-backup/memory-logs-distilled.md` | 94 files | Session logs + machine logs |
| `ψ-backup/active-distilled.md` | 38 files | Architecture + research |
| `ψ-backup/lab-experiments-distilled.md` | 112 files | 16 experiment summaries |

---

## Typical Questions Answered

### Q: How do I run this?

**A**: You don't "run" it. Instead:
1. Copy the repo structure to your new Oracle repo
2. Customize CLAUDE.md with your identity
3. Run `oracle-skills install [skill names]`
4. Start working; skills and hooks activate automatically

### Q: Where are the entry points?

**A**:
1. **New Oracle**: `/origin/README.md` (copy the bash block)
2. **Daily use**: `/origin/CLAUDE.md` (read every session)
3. **Setup**: `/origin/.claude/docs/HOOKS-SETUP.md`
4. **Safety**: `/origin/.claude/hooks/safety-check.sh` (understand what's blocked)

### Q: How do skills and agents differ?

**A**:
- **Skills** = `/commands` available to user (e.g., `/recap`, `/trace`)
- **Agents** = Claude subprocesses that do heavy lifting (e.g., context-finder runs inside `/trace`)
- Skills are **symlinked** from oracle-skills-cli
- Agents are **defined locally** in `.claude/agents/`

### Q: Can I modify this system?

**A**: Yes. You're expected to:
1. Fork the repo
2. Adapt CLAUDE.md to your philosophy
3. Customize `.claude/agents/` with your agents
4. Modify `.claude/settings.json` hooks as needed
5. Use as a template, not a library

### Q: What if I need multi-agent (main + agents/1-5)?

**A**:
1. Read CLAUDE.md lines 58-127 (multi-agent sync)
2. Create worktrees: `git worktree add agents/1 main`
3. Register in `.claude/agents.yml`
4. Use `maw` commands to sync (from external maw repo)

---

## Summary

| Aspect | What You Get |
|--------|--------------|
| **Philosophy** | 5 Principles + 1 Transparency Rule for AI-human symbiosis |
| **Brain** | ψ/ structure: 7 pillars (active/inbox/writing/lab/incubate/learn/memory) |
| **Commands** | ~8 core skills (/recap, /trace, rrr, /feel, /fyi, /forward, /standup, /project) |
| **Agents** | 17+ subagent definitions (context-finder, coder, critic, security-scanner, etc.) |
| **Safety** | Hooks block --force, --amend, worktree escapes; token warnings at 70% |
| **Knowledge** | Distillation pattern: compress context without losing git history |
| **Modularity** | Skills symlinked; agents local; settings.json for hooks; agents.yml for multi-agent |

**Get Started**: Copy `/origin/README.md` lines 9-135 into Claude Code. AI จะถามชื่อจากคุณแล้วรันทุกอย่างให้ 🔮

