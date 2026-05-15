---
name: imprint
description: After building any UI component, extract the visual patterns that matter for consistency and save them to ui-registry.md. So every component built after this one matches what came before.
---

UI consistency does not happen by accident. It happens because every component is built with awareness of what already exists.

The problem with AI-built interfaces is that each component gets built in isolation. The agent does not remember what it built three sessions ago. So spacing drifts. Colors vary slightly. Border radius is inconsistent. The app looks like it was built by multiple people with different tastes.

This skill fixes that. Run it after building any UI component. It reads what was just built, extracts the patterns that matter for consistency, and saves them so every future component can match.

One command. Run it every time. That is the whole system.

---

## How to Invoke

After building any UI component, run:

```
/imprint
```

To target a specific file:

```
/imprint [filepath]
```

To audit an existing codebase for inconsistencies:

```
/imprint audit
```

If no filepath is given, the skill identifies recently created or modified component files automatically and captures from those.

**When to use audit mode:**

- The project UI already exists and consistency is uncertain
- Multiple sessions have passed without running `/imprint`
- Something looks visually off but it is hard to pinpoint why
- Before establishing `ui-registry.md` for the first time on an existing project

Run `/imprint audit` before running `/imprint` on any project where the UI was not tracked from the beginning.

---

## Step 1 — Find What Was Just Built

If a filepath was provided — read that file directly.

If no filepath was provided — identify which component files were most recently created or modified in this session. Look in the components directory and any other locations where UI files typically live. Read those files.

If it is unclear which files to capture from, ask the developer:

```
Which component should I capture patterns from?
```

---

## Step 2 — Extract What Matters for Consistency

Read the component code. Extract only the classes and values that affect visual consistency across the interface. Not everything — only what makes components look like they belong together.

**Extract these:**

- Background — what bg- class is used for the container, cards, panels
- Border — border color, border width, border style
- Border radius — rounded- class used for this component type
- Text colors — primary text, secondary text, muted text classes
- Text sizes and weights — for headings, body, labels, captions
- Spacing — padding inside the component, gap between elements
- Interactive states — hover, focus, active classes
- Shadow — if used
- Any accent or brand color usage

**Do not extract these:**

- Width and height — too context-dependent to be a consistency rule
- Flex and grid layout — structural, not visual
- Positioning — absolute, relative, z-index — context-dependent
- Animation and transition timing — unless it is a pattern worth enforcing
- Responsive breakpoint variants — capture the base pattern only

---

## Step 3 — Write to ui-registry.md

Open `ui-registry.md`. If it does not exist, create it.

Add a new entry for the component that was captured. Do not overwrite existing entries — append to the registry.

If an entry for this component type already exists — update it rather than duplicating.

### Entry format

```markdown
### [Component Name]

File: [filepath]
Last updated: [date]

| Property         | Class           |
| ---------------- | --------------- |
| Background       | [class]         |
| Border           | [class]         |
| Border radius    | [class]         |
| Text — primary   | [class]         |
| Text — secondary | [class]         |
| Spacing          | [class]         |
| Hover state      | [class]         |
| Shadow           | [class or none] |
| Accent usage     | [class or none] |

**Pattern notes:**
[Any important pattern decisions worth noting —
why a specific class was chosen, what this component
should always match, what variations are allowed]
```

---

## Step 4 — Confirm What Was Captured

After writing to ui-registry.md, confirm to the developer:

```
Imprinted [Component Name] → ui-registry.md

Captured:
- Background: [class]
- Border: [class]
- Radius: [class]
- Text: [classes]
- Spacing: [classes]
- Hover: [class]

Any future component of this type should match these patterns.
```

If anything looked inconsistent or surprising during extraction — flag it:

```
Note: [Something that looked inconsistent or worth the
developer knowing about]
```

---

## How ui-registry.md Gets Used

The registry is not just a record. It is the consistency enforcer for every future session.

At the start of any session that involves UI work, Claude reads ui-registry.md before writing any component. When building a new card, it checks how existing cards were built. When building a new button, it checks what button patterns already exist. When building a new status badge, it matches the exact classes already in use.

The registry grows as the project grows. The more components are imprinted, the more consistent every new component becomes — because Claude always has a precise reference for what already exists.

---

## The Rule

Build a component. Run `/imprint`. Move on.

Every time. Without exception.

A registry with ten entries is useful. A registry with thirty entries is powerful. A registry that is sometimes updated is unreliable.

Consistency is a habit, not a feature.

---

## Audit Mode — /imprint audit

Run this when the UI already exists and consistency is uncertain. Instead of capturing from one component, it scans the entire codebase, finds conflicts, and establishes a clean baseline before any further capturing happens.

### Step 1 — Scan all UI components

Find every component file in the project. Read each one. Build a complete picture of what visual patterns are currently in use across the entire interface.

### Step 2 — Identify conflicts

For each visual property that matters for consistency, list every variation found:

```
## UI Consistency Audit

### Conflicts found

**Border radius**
[List every rounded- variant found and which components use it]
Recommendation: [which one to standardise on and why]

**Background colors**
[List every bg- class found — flag any hardcoded hex values]
Recommendation: [which token classes should replace them]

**Text colors**
[List every text- color class found — flag any that bypass the design system]
Recommendation: [which token classes should replace them]

**Spacing**
[List padding and gap variations found]
Recommendation: [which values to standardise on]

**Border colors**
[List every border color class found]
Recommendation: [which token class to standardise on]

**Interactive states**
[List hover, focus, active variations found]
Recommendation: [which pattern to standardise on]

### Hardcoded values found
[List every hardcoded hex value, raw color class, or
non-token value found — with the file and line where it appears]
These must be replaced with design system tokens.

### Recommended baseline
[The correct pattern for each property —
based on what the majority already uses correctly
and what the design system defines]
```

### Step 3 — Wait for developer confirmation

Present the audit report. Do not fix anything. Do not update ui-registry.md yet.

Ask the developer:

```
Audit complete. [X] conflicts found across [Y] properties.

Before I establish the baseline in ui-registry.md:
1. Do the recommendations above look correct?
2. Are there any conflicts you want to resolve differently?
3. Should I flag the hardcoded values as issues to fix?

Confirm the baseline and I will write it to ui-registry.md.
```

### Step 4 — Write the confirmed baseline

After the developer confirms — write the agreed baseline to `ui-registry.md` as the foundation. Label it clearly:

```markdown
## Baseline — Established [date]

[Note: This baseline was established via /imprint audit]

| Property         | Correct class |
| ---------------- | ------------- |
| Card background  | [class]       |
| Card border      | [class]       |
| Card radius      | [class]       |
| Button primary   | [class]       |
| Button secondary | [class]       |
| Text primary     | [class]       |
| Text secondary   | [class]       |
| Text muted       | [class]       |
| Input background | [class]       |
| Input border     | [class]       |
```

### Step 5 — List what needs fixing

After writing the baseline, produce a fix list — every component that deviates from it:

```
## Components to fix

These components deviate from the confirmed baseline
and should be updated:

- [Component file] — [what is wrong] → [what it should be]
- [Component file] — [what is wrong] → [what it should be]
```

The developer can now fix these systematically — or fix them as they encounter each component. Either way, the baseline is established and `/imprint` can be used going forward to keep new components consistent.
