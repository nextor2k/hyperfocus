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
