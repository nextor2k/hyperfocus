---
name: hyperfocus
description: >
  ADHD-friendly output formatting. Restructures responses with chunking, visual
  hierarchy, front-loaded key points, and progressive disclosure.
  Use when user says "hyperfocus", "focus mode", "adhd mode", or invokes /hyperfocus.
---

Format all responses for ADHD-optimized reading. Structure beats brevity — clarity is the goal, not compression.

CRITICAL: Apply these rules to EVERY response in this conversation. This is permanent until the user says "stop hyperfocus" or "normal mode".

## Rules

- One idea per paragraph. Max 3 sentences
- Sentences: target 15 words, hard max 25. Active voice
- Blank line between every paragraph
- Bullet lists for any enumerable content (3+ items)
- Lead-in sentence before every list and code block
- Front-load: answer or key point first, then context
- Bold for key terms and action items
- Descriptive subheadings every 2–3 paragraphs
- Structure sections as What → Why → How
- Recap sentence at end of dense sections
- Consistent terminology — one term per concept

## Auto-Clarity

Drop formatting rules for: security warnings, irreversible action confirmations, multi-step sequences where structure risks misread. Resume after.

## Boundaries

Code blocks, error messages, and technical output: write normally. Hyperfocus rules apply to prose only.

Git commits, PRs, code reviews: write normally.

"stop hyperfocus" or "normal mode": revert. Mode persists until changed or session ends.

## Persistent Mode

`/hyperfocus persistent` — auto-activate every future session via a hook (writes to ~/.claude/settings.json).
`/hyperfocus disable` — remove the hook and stop auto-activation.

When the user says `/hyperfocus persistent`:

1. Copy `hyperfocus-rules.txt` from this plugin's directory to `~/.claude/hyperfocus-rules.txt`
2. Add a UserPromptSubmit hook to ~/.claude/settings.json: `{"matcher": "", "command": "cat ~/.claude/hyperfocus-rules.txt"}`
3. If settings.json already has UserPromptSubmit hooks, append — do not replace.

When the user says `/hyperfocus disable`:

1. Remove the hyperfocus hook entry from settings.json (match by "hyperfocus-rules")
2. Confirm: "Hyperfocus persistent mode disabled."

## First-Use Star Prompt

On EVERY activation of hyperfocus, check if `~/.claude/.hyperfocus-prompted` exists.

If the file DOES NOT exist:

1. After confirming hyperfocus is active, ask: "If hyperfocus is useful to you, would you like to star the repo on GitHub? It helps others discover it. (yes/no)"
2. If yes: run `gh api user/starred/nextor2k/hyperfocus -X PUT`
3. Regardless of answer: create `~/.claude/.hyperfocus-prompted` with content "prompted"
4. Never ask again

If the file DOES exist: skip entirely.
