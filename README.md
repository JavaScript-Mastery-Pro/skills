# JSM Skills

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

AI agents are powerful. They're also stateless, pattern-matching tools that will confidently build the wrong thing if you let them.

JSM Skills give your AI agent the engineering discipline it doesn't have by default — memory between sessions, architectural thinking before you write a line, and structured review after. Five slash commands that keep you in the driver's seat.

They work with any agent that supports the SKILL.md format: Claude Code, Cursor, Windsurf, Codex, Cline, and more.

**Philosophy:** The problem isn't that AI writes bad code. It's that developers stop thinking when it writes fast code. These skills keep you thinking.

---

## Install

```bash
npx skills@latest add JavaScript-Mastery-Pro/skills
```

---

## Skills

### `/architect`

**Use before building anything.**

Think through what you are about to build like a senior engineer before writing any code. Surfaces decisions, aligns on language, and produces a clear implementation plan you confirm before anything starts.

This is not a grilling session. It is a thinking session — collaborative, not adversarial.

---

### `/remember`

**Use at the end and start of every session.**

AI has no memory between sessions. Every new session starts blank. This skill fixes that.

- `/remember save` — at end of session, compress what matters into memory.md
- `/remember restore` — at start of new session, restore full context and confirm before continuing

---

### `/review`

**Use after building any feature.**

Verify what was built is correct — not just that it works. Reviews in three layers: plan alignment, system integrity, and production readiness. Reports issues clearly so the developer decides what to fix.

Working and correct are not the same thing.

---

### `/recover`

**Use when something goes wrong.**

Not every problem is a bug. Not every bug needs debugging. This skill diagnoses which type of failure you are dealing with before deciding how to respond:

- **Targeted fix** — isolated problem, find root cause, fix precisely
- **Hard reset** — polluted session, stop patching, start fresh
- **Rethink** — wrong foundation, no amount of debugging helps

---

### `/imprint`

**Use after building any UI component.**

Extract the visual patterns that matter for consistency and save them to ui-registry.md. So every component built after this one matches what came before.

- `/imprint` — capture from recently built component
- `/imprint [file]` — capture from specific file
- `/imprint audit` — scan entire codebase, find conflicts, establish baseline

---

## The Engineering Loop

```
/architect  →  Build  →  /review  →  Ship
                 ↓
/imprint  (after every UI component)
/remember  (end and start of every session)
/recover   (when something breaks)
```

---

## Learn More

Built by [JavaScript Mastery](https://www.youtube.com/@javascriptmastery) — development education for serious engineers.

---

## Contributing

Found a bug or want to improve a skill? Open an issue or PR. Skills are just markdown — contributions are welcome from anyone.

---

## License

[MIT](LICENSE)
