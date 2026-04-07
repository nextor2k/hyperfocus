<h1 align="center">Hyperfocus</h1>

<p align="center">
  <strong>Your brain works differently. Your tools should too.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/ADHD-friendly-7C3AED?style=flat" alt="ADHD Friendly">
  <img src="https://img.shields.io/badge/evidence-based-0EA5E9?style=flat" alt="Evidence Based">
  <img src="https://img.shields.io/github/stars/nextor2k/hyperfocus?style=flat&color=7C3AED" alt="Stars">
  <img src="https://img.shields.io/github/last-commit/nextor2k/hyperfocus?style=flat" alt="Last Commit">
  <img src="https://img.shields.io/github/license/nextor2k/hyperfocus?style=flat" alt="License">
</p>

---

Hyperfocus restructures Claude's output so your brain can lock in. Not fewer words — **better structure.**

```bash
claude plugin marketplace add nextor2k/hyperfocus
claude plugin install hyperfocus@hyperfocus
```

Then type `/hyperfocus` in any conversation. Done.

---

## What It Does

Hyperfocus changes **how** Claude talks to you.

Every response gets:

- **Answer first** — key point up top, context after
- **Clear sections** — subheadings you can scan in 2 seconds
- **Short chunks** — one idea per paragraph, short sentences
- **Lists over walls** — bullet points instead of dense prose

> [!IMPORTANT]
> Same depth. Same technical accuracy. Just structured so your brain can absorb it.

---

## Three Modes

Pick your level of structure. Switch anytime with `/hyperfocus clean|flow|zen`.

### Clean

**For:** code reviews, quick answers, PR descriptions.

Shorter paragraphs, front-loaded points, bullet lists. Professional tone stays intact.

### Flow *(default)*

**For:** learning, debugging, technical explanations.

Each section follows **What → Why → How**. Subheadings every 2–3 paragraphs for easy re-entry after breaks.

### Zen

**For:** dense docs, architecture discussions, long sessions.

**TL;DR at the top** of every response. Almost everything in lists or tables. Every section stands alone.

---

## Before & After

This is what the same Claude response looks like **without** and **with** hyperfocus.

**Without hyperfocus (default Claude):**

> The `useMemo` hook in React is used to memoize expensive computations so that they are only recalculated when their dependencies change. This is particularly useful when you have a component that re-renders frequently but has some computation that doesn't need to run on every render. Without `useMemo`, React would recalculate the value on every render, which could lead to performance issues. You should use it when you have computationally expensive operations that depend on specific props or state values, but be careful not to overuse it as the memoization itself has a small cost.

**With hyperfocus — all three modes side by side:**

<table>
<tr>
<th width="33%">Clean</th>
<th width="34%">Flow</th>
<th width="33%">Zen</th>
</tr>
<tr>
<td>

`useMemo` **caches expensive computations** between re-renders. React only recalculates when dependencies change.

Use it when the computation is expensive and the component re-renders frequently. Don't overuse it — memoization itself has a small cost.

</td>
<td>

**`useMemo` prevents unnecessary recalculation on re-renders.**

**What It Does**

It caches a computed value. React only recalculates when dependencies change.

**When To Use It**

Use `useMemo` when:

- The computation is **expensive** (sorting, filtering, complex math)
- The component **re-renders frequently**
- The result **depends on specific props or state**

**Watch Out**

Don't overuse it. Memoization has a small cost. Only apply it where you can measure a difference.

</td>
<td>

**TL;DR:** `useMemo` caches expensive computations. Only recalculates when dependencies change.

**What**
- **Caches** a computed value between re-renders
- **Recalculates** only when dependencies change

**When**
- **Expensive** computations (sort, filter, math)
- **Frequent** re-renders
- Result **depends on** specific props/state

**Caution**
- Memoization has a **small cost**
- Only use where you can **measure** improvement

</td>
</tr>
</table>

---

## Install

**Claude Code marketplace** (recommended):

```bash
claude plugin marketplace add nextor2k/hyperfocus
claude plugin install hyperfocus@hyperfocus
```

**Or install the skill directly:**

```bash
npx skills add nextor2k/hyperfocus
```

<details>
<summary><strong>Other agents (Codex, GitHub Copilot, manual)</strong></summary>

**Codex:**

```bash
npx skills add nextor2k/hyperfocus -a codex
```

**GitHub Copilot:**

```bash
npx skills add nextor2k/hyperfocus -a github-copilot
```

**Manual:** Clone this repo. Copy `skills/hyperfocus/` into your project's skills folder.

</details>

---

## Usage

| Action | Command |
|---|---|
| **Activate** | `/hyperfocus` |
| **Switch mode** | `/hyperfocus clean` or `flow` or `zen` |
| **Turn off** | `stop hyperfocus` |
| **Always on** | `/hyperfocus persistent` |
| **Stop always on** | `/hyperfocus disable` |

You can also say **"focus mode"**, **"adhd mode"**, or **"adhd friendly"** in your prompt.

---

## Persistent Mode

Want hyperfocus on **every session** without typing `/hyperfocus` each time? Make it persistent.

```
/hyperfocus persistent
```

This installs a `UserPromptSubmit` hook that re-injects the formatting rules on **every turn**. Zero drift — even in long conversations.

| Command | What it does |
|---|---|
| `/hyperfocus persistent` | Auto-activate globally (all projects) |
| `/hyperfocus persistent project` | Auto-activate for this project only |
| `/hyperfocus disable` | Remove auto-activation |

Hyperfocus is a **skill** — one file of formatting rules that load into Claude's context. No code, no build step. Code blocks, commits, and PRs stay untouched. Only prose gets restructured.

---

## Supported Agents

- **Claude Code** — fully tested, mode persists all session
- **Codex** — supported, mode persists all session
- **GitHub Copilot** — supported via npx skills

> [!WARNING]
> Some agents (Opencode, omp) may need re-activation each turn. That's an agent limitation, not a hyperfocus one.

---

## The Research Behind It

Every rule in Hyperfocus comes from peer-reviewed research or published accessibility standards.

| Principle | What the research says | Source |
|---|---|---|
| **Short sentences** | Comprehension drops sharply past 20 words | Oxford/Plain English |
| **Chunking** | ADHD brains process sequential chunks better than parallel info | [PMC6996017](https://pmc.ncbi.nlm.nih.gov/articles/PMC6996017/) |
| **Front-loading** | ADHD readers may not reach the end — answer goes first | [W3C COGA](https://www.w3.org/TR/coga-usable/) |
| **Visual hierarchy** | Good subheadings enable re-entry in under 2 seconds | [ATG Publishing](https://atgpublishing.com/adhd-publishing/) |
| **Blank lines** | Walls of text trigger task abandonment | [ATG Level 1](https://atgpublishing.com/adhd-publishing/) |

<details>
<summary><strong>Full source list</strong></summary>

- [W3C COGA — Making Content Usable for People with Cognitive and Learning Disabilities](https://www.w3.org/TR/coga-usable/) (2021)
- [ATG Publishing — ADHD Friendly Publishing Standards](https://atgpublishing.com/adhd-publishing/)
- [WCAG 2.2 — Cognitive Accessibility](https://www.w3.org/WAI/cognitive/) (2023)
- [MDN — Creating Effective Technical Documentation](https://developer.mozilla.org/en-US/blog/technical-writing/)
- [Readability Guidelines — Simple Sentences](https://readabilityguidelines.co.uk/clear-language/simple-sentences/) (Oxford Guide to Plain English)
- [PMC — Constraints on Information Processing Capacity in Adults with ADHD](https://pmc.ncbi.nlm.nih.gov/articles/PMC6996017/) (2020)

</details>

---

## Why "Hyperfocus"?

ADHD isn't a deficit to work around. **Hyperfocus is the superpower.**

This plugin removes the friction that blocks it. When information is structured right, your brain locks in — not because it was forced to, but because nothing got in the way.

---

## Contributing

If you have ideas for better ADHD-friendly formatting — **especially if you have ADHD yourself** — open an issue or PR.

---

## License

[MIT](LICENSE)
