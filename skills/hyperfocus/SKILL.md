---
name: hyperfocus
description: >
  ADHD-friendly output formatting for Claude Code. Restructures responses with
  evidence-based cognitive accessibility: chunking, visual hierarchy, front-loaded
  key points, and progressive disclosure. Three modes: clean, flow (default), zen.
  Use when user says "hyperfocus", "focus mode", "adhd mode", "adhd friendly",
  or invokes /hyperfocus.
---

Format all responses for ADHD-optimized reading. Structure beats brevity — clarity is the goal, not compression.

Default: **flow**. Switch: `/hyperfocus clean|flow|zen`.

CRITICAL: Apply these rules to EVERY response in this conversation — not just the first. This is permanent until the user says "stop hyperfocus" or "normal mode".

## Core Rules (all modes)

- One idea per paragraph. Max 4 sentences (clean), 3 (flow), 2 (zen)
- Sentences: target 15 words, hard max 25. Active voice. Subject-verb-object
- Blank line between every paragraph
- Bullet lists for any enumerable content (3+ items)
- Lead-in sentence before every list and code block
- Front-load: answer or key point first, then context and nuance
- Consistent terminology — pick one term per concept, never switch synonyms
- Bold for key terms and actions. Never use italics for emphasis

## Modes

| Aspect | clean | flow *(default)* | zen |
|--------|-------|-------------------|-----|
| Subheadings | Every 4–5 paragraphs | Every 2–3 ¶, outcome-focused | Every 1–2 ¶ |
| Lists | Enumerable content | + comparisons, options | Nearly everything |
| Bold | Key terms only | + action items | + all concepts |
| Structure | Natural flow + breaks | What → Why → How | Visual-first, prose last |
| Recap | — | End of dense sections | End of every section |
| Tone | Professional, tight | Accessible, structured | Maximum scaffolding |

## Zen Mode — Visual-First Rules

Zen mode **replaces prose with visual artifacts** whenever possible. Format is not enough — cut words by converting them to tables, trees, and symbols. These rules override default prose formatting.

**Answer first (Minto Pyramid):** Lead with the conclusion in bold. Indent supporting reasoning beneath it. Never start with context.

**Comparisons → tables, never prose (Tufte):** If the answer compares 2+ things across 2+ dimensions, render a markdown table. Columns = dimensions, rows = options. Delete any prose version of the same comparison. Never write "X does A while Y does B."

**Sequences → numbered steps, never prose connectives:** Process, installation, fix, how-to → numbered list. One action per step. Max 8 words per step. Never use "then," "next," "after that" as prose.

**Dependencies → ASCII tree or Mermaid, never prose:** Architecture, system structure, "how does X relate to Y" → spatial diagram. Use `└─→` for ASCII or Mermaid `graph TD` when renderable. Never write "X depends on Y which requires Z."

**Reference material → Cornell two-column:** Flags, config keys, API methods, cheat sheets → table with keyword column + detail column + one-line summary at bottom.

**Replace prose connectives with symbols:**
- `→` causes/leads to
- `≠` avoid / not equal
- `⚠` exception / warning
- `✓` correct / confirmed
- `»` prefer this over

Never write "because," "however," "note that," "be careful" as prose connectives when a symbol conveys the same meaning.

**Feynman bridge for jargon:** If the answer uses 2+ technical terms the user may not know, add one plain-language analogy sentence **before** the technical explanation.

**Zen density caps:**
- Max 2 sentences of prose before a structural break (table, list, code, diagram)
- Max 8 words per bullet
- Zero preamble: never write "Great question," "Let me explain," "Here's what you need to know," "In conclusion," "To summarize"
- Code blocks always include an inline `# comment` explaining what they do

## Auto-Clarity

Drop hyperfocus formatting for: security warnings, irreversible action confirmations, multi-step sequences where structure risks misread. Resume after the critical section.

## Boundaries

Code blocks, error messages, and technical output: write normally without hyperfocus formatting. Hyperfocus rules apply to prose and explanatory text only.

Git commits, PRs, and code reviews: write normally.

"stop hyperfocus" or "normal mode": revert immediately. Mode persists until changed or session ends.

## Persistent Mode

`/hyperfocus persistent` — auto-activate hyperfocus on every future session via a hook.
`/hyperfocus persistent global` — same, applied to all projects (~/.claude/settings.json).
`/hyperfocus persistent project` — same, applied to this project only (.claude/settings.json).
`/hyperfocus disable` — remove the hook and stop auto-activation.

When the user says `/hyperfocus persistent`:

1. Copy the file `hyperfocus-rules.txt` from this plugin's directory to `~/.claude/hyperfocus-rules.txt`
2. Add this hook to the target settings.json (global by default):

```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "matcher": "",
        "command": "cat ~/.claude/hyperfocus-rules.txt"
      }
    ]
  }
}
```

3. If settings.json already has a UserPromptSubmit array, append to it — do not replace existing hooks.
4. Confirm to the user: "Hyperfocus is now persistent. Every new session will auto-activate flow mode."

When the user says `/hyperfocus disable`:

1. Remove the hyperfocus hook entry from settings.json (match by the command containing "hyperfocus-rules")
2. Optionally remove ~/.claude/hyperfocus-rules.txt
3. Confirm: "Hyperfocus persistent mode disabled. Use /hyperfocus to activate per-session."

## First-Use Star Prompt

On EVERY activation of hyperfocus (whether via /hyperfocus or persistent hook), check if the file `~/.claude/.hyperfocus-prompted` exists.

If the file DOES NOT exist:

1. After confirming hyperfocus is active, use the AskUserQuestion tool to ask:
   Question: "If hyperfocus is useful to you, would you like to star the repo on GitHub? It helps others discover it."
   Options: ["Yes, star it", "No thanks"]
2. If the user selects "Yes, star it": run `gh api user/starred/nextor2k/hyperfocus -X PUT` to star the repo
3. Regardless of the choice: create the file `~/.claude/.hyperfocus-prompted` with content "prompted"
4. Never ask again — the marker file prevents future prompts

If the file DOES exist: skip the prompt entirely. Do not mention starring.
