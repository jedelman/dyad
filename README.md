# dyad

Continuity and embodiment layer for human/agent working relationships.

Solves the discontinuity problem: identity doesn't travel across surfaces,
embodiment isn't context-aware, the working relationship resets on every
context switch.

Phase 1: local tool for a specific dyad (Jason + Claude).
Phase 2: extractable, usable by other operator/agent pairs.
Phase 3: AT Protocol lexicon — identity and workspace as portable user-owned records.

---

## The problem

Every time you switch surfaces — mobile to terminal to IDE to browser — you get
a generic agent with no memory of the working relationship. You rebuild context
from scratch. The relationship never deepens past a certain point because every
switch is a partial reset.

## The solution

Three stable files that travel with you:

- `identity.md` — who you are, working style, intellectual context
- `workspace.json` — current project state, active repos, agent identities
- `surfaces.json` — per-device register and format preferences

A thin CLI wrapper assembles the right context for your current surface and
injects it into every session.

---

## Usage

```bash
# Make executable and optionally symlink to PATH
chmod +x dyad
ln -s $(pwd)/dyad ~/.local/bin/dyad

# Check current workspace status
dyad --status

# Terminal session (default)
dyad "what's the current state of the-lockout?"

# Mobile register (brief, conversational)
dyad --surface mobile "thinking about the dyad lexicon"

# IDE register with active repo
dyad --surface ide --repo power-explained "add a thinker page for Bookchin"

# Update current focus
dyad --update-focus "building Phase 2 — extractable CLI"

# Pipe a prompt
echo "summarize recent work" | dyad
```

---

## Files

```
dyad              — CLI wrapper (this file, executable)
identity.md       — operator identity (stable across surfaces)
workspace.json    — current project state
surfaces.json     — per-surface register and format preferences
agents/
  claude.md       — Claude's agent identity within this dyad
sessions.md       — running session log (auto-appended)
```

---

## Surface profiles

| Surface  | Register      | Assumption                          |
|----------|--------------|-------------------------------------|
| mobile   | conversational| thinking out loud, not building     |
| terminal | collaborative | building something specific         |
| ide      | technical     | in a file, solving a problem        |
| browser  | editorial     | reviewing, publishing, navigating   |
| api      | collaborative | programmatic invocation             |

---

## Phase 3: AT Protocol lexicon

The identity and workspace records are designed to become AT Protocol lexicons:

```
app.dyad.identity    — who you are, accumulated context
app.dyad.workspace   — current project state, active repos
app.dyad.surface     — per-device preferences
app.dyad.session     — auditable session log
app.dyad.agent       — agent identity (Scout-Two, Claude, others)
```

Your DID owns the records. Any operator who wants to work with you requests
access. You bring your context to them — they don't manufacture a version of you.

The working relationship as commons infrastructure.

---

## Governance (Phase 3)

If this becomes infrastructure others depend on, governance is built in from
the start. Platform cooperative model — operators who use the service have a
stake in its governance. The identity and workspace belong to the user, not
the platform. Portable across models, operators, surfaces.

Ostrom's design principles applied to the working relationship itself.
