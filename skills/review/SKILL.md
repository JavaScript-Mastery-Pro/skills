---
name: review
description: After building a feature, verify it matches what was planned, respects the system architecture and design standards, and is ready for production. Reports issues clearly so the developer decides what to fix.
---

Building is not done when the code runs. It is done when the code is correct.

AI moves fast. Fast means things get built that work on the surface but drift from the architecture, violate the design system, or miss edge cases that matter. This skill catches those things before they compound into bigger problems.

Run this after every feature. Before you move on.

## What This Skill Does Not Do

It does not fix anything. It reports what it finds and lets the developer decide what matters and what to do about it. Fixing without understanding is how problems get buried, not solved.

---

## Step 1 — Understand What Should Have Been Built

Before reviewing anything, establish the benchmark.

Read in this order:

- The implementation plan from `/architect` if one exists
- The feature description or task that was given
- Any relevant context files — architecture boundaries, code standards, design rules

If no plan exists, ask the developer to describe what the feature was supposed to do before reviewing. You cannot verify correctness without knowing what correct looks like.

---

## Step 2 — Review in Three Layers

### Layer 1 — Does it match the plan?

Compare what was built against what was planned.

Check:

- Every part of the feature description — is it all there?
- The decisions made during planning — are they reflected in the code?
- The scope — did the implementation stay within bounds or add things that were not asked for?

Flag anything that was planned but missing. Flag anything that was built but not planned.

### Layer 2 — Does it respect the system?

This is where AI drift most commonly happens. The feature works, but it violates rules that the project depends on.

Check:

- **Architecture boundaries** — does code in the right place own the right responsibilities? No UI logic in API routes. No DB calls in components. Whatever the project's boundaries are — are they respected?
- **Design system** — are the correct tokens, classes, and patterns used? Any hardcoded values that should be variables? Any raw color classes that should use the design system?
- **Code standards** — naming conventions, file organisation, TypeScript strictness, error handling patterns — do they match what the project established?
- **Existing patterns** — does this feature introduce a new pattern when an existing one should have been used?

### Layer 3 — Is it production ready?

Check:

- Error handling — what happens when things go wrong? Are errors caught and handled or does the feature silently fail?
- Edge cases — empty states, loading states, missing data — are these handled?
- Console errors — any errors or warnings in the browser or terminal?
- Obvious bugs — anything that would clearly break for a real user?

---

## Step 3 — Report What You Found

After completing all three layers, produce a clear report. Do not bury issues. Do not soften them. Report honestly so the developer can make informed decisions.

```
## Review — [Feature Name]

### Layer 1 — Plan alignment
[PASS / ISSUES FOUND]
[List any gaps between what was planned and what was built]

### Layer 2 — System integrity
[PASS / ISSUES FOUND]
[List any architecture, design, or code standard violations]

### Layer 3 — Production readiness
[PASS / ISSUES FOUND]
[List any error handling gaps, edge cases, or obvious bugs]

### Summary
[X] issues found across [Y] layers.

[If no issues: "No issues found. This feature is ready to ship."]
[If issues: "Resolve the above before moving to the next feature."]
```

---

## Step 4 — Let the Developer Decide

After presenting the report, stop. Do not start fixing. Do not suggest fixes unless the developer asks.

Wait for the developer to:

- Ask you to fix a specific issue
- Tell you an issue is intentional and can be ignored
- Confirm everything is resolved and ready to move on

The developer owns the quality decision. You inform it.

---

## Severity Guide

Not all issues are equal. Use this to help the developer prioritise:

**Critical — fix before moving on**

- Architecture boundary violations that will break future features
- Missing error handling that causes silent failures
- Functionality that was planned but completely missing

**Important — fix soon**

- Design system drift that will cause UI inconsistency
- Code standard violations that will compound across the codebase
- Edge cases that a real user will encounter

**Minor — fix when convenient**

- Naming inconsistencies that do not affect behaviour
- Missing optimisations
- Style issues that do not affect the design system

Label each issue with its severity so the developer can triage quickly.

---

## The Standard

The question this skill answers is not "does it work?"

The question is "is it correct?"

Working and correct are not the same thing. A feature can work today and break the project tomorrow. Review exists to catch the difference.
