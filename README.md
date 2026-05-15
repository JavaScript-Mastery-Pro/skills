# JSM Skills

Agent skills for developers who want to build real, production-ready software with AI — without losing the engineering thinking behind it.

These skills work with any AI coding agent that supports the SKILL.md format — Claude Code, Cursor, Windsurf, Codex, Cline, and more.

**Philosophy:** AI should amplify developer thinking, not replace it. These skills teach you to direct AI like a senior engineer — not depend on it blindly.

---

## Install

```bash
npx skills@latest add jsmastery/skills
```

Install individual skills:

```bash
npx skills@latest add jsmastery/skills/architect
npx skills@latest add jsmastery/skills/remember
npx skills@latest add jsmastery/skills/review
npx skills@latest add jsmastery/skills/recover
npx skills@latest add jsmastery/skills/imprint
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

These skills were built by [JavaScript Mastery](https://www.youtube.com/@javascriptmastery) — one of the most popular development education channels with 1M+ subscribers.

Watch the full workflow video to see these skills used in a real production build:
[Coming soon]

---

## Contributing

Found a bug or want to improve a skill? Open an issue or PR. Skills are just markdown — contributions are welcome from anyone.

---

## License

MIT
