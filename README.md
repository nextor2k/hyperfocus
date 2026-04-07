# Hyperfocus

**ADHD-friendly output formatting for Claude Code.**

Hyperfocus restructures AI responses so your brain can lock in. Not fewer words — better structure.

Built on evidence-based cognitive accessibility research from W3C, ATG Publishing, and peer-reviewed neuroscience.

---

## What It Does

Hyperfocus changes **how** Claude presents information — not what it says.

Every response gets restructured with these principles:

- **Front-loaded answers** — the key point comes first, context after
- **Visual hierarchy** — descriptive subheadings, bold key terms, clear breaks
- **Chunked content** — one idea per paragraph, short sentences, bullet lists
- **Progressive disclosure** — essential info first, details on demand

The result: output your brain can scan, absorb, and act on.

---

## Why This Exists

ADHD isn't a deficit to work around. **Hyperfocus is the superpower.** This plugin removes the friction that prevents it from engaging.

The research backs this up:

- **Sentence length matters.** Comprehension drops sharply past 20 words per sentence. Hyperfocus targets 15, caps at 25.
- **Chunking is the #1 recommendation.** Adults with ADHD show reduced processing capacity for competing information streams. Sequential chunks directly address this. *(PMC6996017)*
- **Front-loading works.** ADHD readers may not reach the end. The answer belongs at the top. *(W3C COGA)*
- **Visual hierarchy enables re-entry.** After an attention break, a good subheading lets you re-orient in under 2 seconds. *(ATG Publishing)*

---

## Install

**Claude Code** (recommended):

```bash
npx skills add nextor2k/hyperfocus
```

**Codex:**

```bash
npx skills add nextor2k/hyperfocus -a codex
```

**GitHub Copilot:**

```bash
npx skills add nextor2k/hyperfocus -a github-copilot
```

**Manual install:** Clone this repo and copy the `skills/hyperfocus/` directory into your project's skills folder.

---

## Usage

Activate hyperfocus in any conversation:

```
/hyperfocus
```

Switch between modes:

```
/hyperfocus clean
/hyperfocus flow
/hyperfocus zen
```

Turn it off:

```
stop hyperfocus
```

You can also activate it naturally by saying **"focus mode"**, **"adhd mode"**, or **"adhd friendly"** in your prompt.

---

## Modes

Hyperfocus has three intensity levels. Each adds more structure.

| | **clean** | **flow** *(default)* | **zen** |
|---|---|---|---|
| **Paragraphs** | Max 4 sentences | Max 3 sentences | Max 2 sentences |
| **Subheadings** | Every 4–5 ¶ | Every 2–3 ¶ | Every 1–2 ¶ |
| **Lists** | Enumerable content | + comparisons | Nearly everything |
| **Bold** | Key terms | + actions | + all concepts |
| **Structure** | Natural + breaks | What → Why → How | TL;DR at top |
| **Recap** | — | Dense sections | Every section |

**Pick your mode based on the task:**

- **clean** — Reading code reviews, PR descriptions, quick answers. Professional tone, less noise.
- **flow** — Learning new concepts, debugging, technical explanations. Full structure without overload.
- **zen** — Dense documentation, architecture discussions, long sessions. Maximum scaffolding.

---

## Before & After

### Default Claude Response

> The `useMemo` hook in React is used to memoize expensive computations so that they are only recalculated when their dependencies change. This is particularly useful when you have a component that re-renders frequently but has some computation that doesn't need to run on every render. Without `useMemo`, React would recalculate the value on every render, which could lead to performance issues. You should use it when you have computationally expensive operations that depend on specific props or state values, but be careful not to overuse it as the memoization itself has a small cost.

### With Hyperfocus (flow)

> **`useMemo` prevents unnecessary recalculation on re-renders.**
>
> ### What It Does
>
> It caches a computed value. React only recalculates when dependencies change.
>
> ### When To Use It
>
> Use `useMemo` when:
>
> - The computation is **expensive** (sorting, filtering, complex math)
> - The component **re-renders frequently**
> - The result **depends on specific props or state**
>
> ### Watch Out
>
> Don't overuse it. Memoization itself has a small cost. Only apply it where you can measure a difference.

### With Hyperfocus (zen)

> **TL;DR:** `useMemo` caches expensive computations. Only recalculates when dependencies change.
>
> ---
>
> ### What
>
> - **Caches** a computed value between re-renders
> - **Recalculates** only when dependencies change
>
> ### When
>
> - **Expensive** computations (sort, filter, math)
> - **Frequent** re-renders
> - Result **depends on** specific props/state
>
> ### Caution
>
> - Memoization has a **small cost**
> - Only use where you can **measure** improvement

---

## How It Works

Hyperfocus is a **skill** — a set of formatting instructions injected into Claude's context when activated. No code, no hooks, no build step.

The SKILL.md file contains evidence-based rules that reshape how Claude structures its prose. Code blocks, error messages, git commits, and PRs are left untouched — only explanatory text gets restructured.

---

## Supported Agents

Hyperfocus works with any agent that supports the skills/plugin system:

- **Claude Code** — primary target, fully tested
- **Codex** — supported via plugin manifest
- **GitHub Copilot** — supported via npx skills

**Persistence note:** Mode persists for the full session in Claude Code and Codex. Some agents (Opencode, omp) may require re-activation each turn. This is an agent-level limitation, not a hyperfocus limitation.

---

## Research

The formatting rules in Hyperfocus are derived from these sources:

- [W3C COGA — Making Content Usable for People with Cognitive and Learning Disabilities](https://www.w3.org/TR/coga-usable/) (2021)
- [ATG Publishing — ADHD Friendly Publishing Standards](https://atgpublishing.com/adhd-publishing/)
- [PMC — Constraints on Information Processing Capacity in Adults with ADHD](https://pmc.ncbi.nlm.nih.gov/articles/PMC6996017/) (2020)
- [MDN — Creating Effective Technical Documentation](https://developer.mozilla.org/en-US/blog/technical-writing/)
- [Readability Guidelines — Simple Sentences](https://readabilityguidelines.co.uk/clear-language/simple-sentences/) (Oxford Guide to Plain English)
- [WCAG 2.2 — Cognitive Accessibility](https://www.w3.org/WAI/cognitive/) (2023)

---

## Contributing

Contributions are welcome. If you have ideas for improving ADHD-friendly formatting — especially if you have ADHD yourself — please open an issue or PR.

---

## License

[MIT](LICENSE)
