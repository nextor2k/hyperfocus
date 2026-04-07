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
```

Then type `/hyperfocus` in any conversation. Done.

> [!TIP]
> Already using hyperfocus? Switch modes anytime: `/hyperfocus clean`, `/hyperfocus flow`, or `/hyperfocus zen`.

---

## What It Does

Hyperfocus changes **how** Claude talks to you.

Every response gets:

- **Answer first** — key point up top, context after
- **Clear sections** — subheadings you can scan in 2 seconds
- **Short chunks** — one idea per paragraph, max 3 sentences
- **Lists over walls** — bullet points instead of dense prose

> [!IMPORTANT]
> Hyperfocus doesn't dumb anything down. Same depth, same technical accuracy — just structured so your brain can absorb it.

---

## Three Modes

Pick your level of structure. Switch anytime with `/hyperfocus clean|flow|zen`.

### Clean

**For:** code reviews, quick answers, PR descriptions.

Light touch. Shorter paragraphs, front-loaded points, bullet lists. Professional tone stays intact.

### Flow *(default)*

**For:** learning, debugging, technical explanations.

Full structure. Each section follows **What → Why → How**. Recap sentences at the end of dense blocks. Subheadings every 2–3 paragraphs so you can find your place after a break.

### Zen

**For:** dense docs, architecture discussions, long sessions.

Maximum scaffolding. **TL;DR at the top** of every response. Almost everything in lists or tables. Every section stands alone — jump in anywhere.

> [!NOTE]
> Mode persists for the full session. You don't need to re-activate it each turn.

---

## Before & After

> [!IMPORTANT]
> Same information. Same depth. Just structured differently.

<table>
<tr>
<th width="50%">Default Claude</th>
<th width="50%">With Hyperfocus (flow)</th>
</tr>
<tr>
<td>

The `useMemo` hook in React is used to memoize expensive computations so that they are only recalculated when their dependencies change. This is particularly useful when you have a component that re-renders frequently but has some computation that doesn't need to run on every render. Without `useMemo`, React would recalculate the value on every render, which could lead to performance issues. You should use it when you have computationally expensive operations that depend on specific props or state values, but be careful not to overuse it as the memoization itself has a small cost.

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
</tr>
</table>

<details>
<summary><strong>See the same example in Zen mode</strong></summary>

<br>

<table>
<tr>
<th width="50%">Default Claude</th>
<th width="50%">With Hyperfocus (zen)</th>
</tr>
<tr>
<td>

The `useMemo` hook in React is used to memoize expensive computations so that they are only recalculated when their dependencies change. This is particularly useful when you have a component that re-renders frequently but has some computation that doesn't need to run on every render. Without `useMemo`, React would recalculate the value on every render, which could lead to performance issues. You should use it when you have computationally expensive operations that depend on specific props or state values, but be careful not to overuse it as the memoization itself has a small cost.

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

</details>

---

## Install

> [!TIP]
> The marketplace is the easiest way to install. One command and you're done.

**Claude Code marketplace** (recommended):

```bash
claude plugin marketplace add nextor2k/hyperfocus
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

You can also say **"focus mode"**, **"adhd mode"**, or **"adhd friendly"** in your prompt.

---

## How It Works

Hyperfocus is a **skill** — formatting rules that load into Claude's context when activated.

No code. No hooks. No build step. One file of instructions that reshapes how Claude writes prose.

> [!IMPORTANT]
> Code blocks, error messages, commits, and PRs stay untouched. Only explanatory text gets restructured.

---

## Supported Agents

- **Claude Code** — fully tested, mode persists all session
- **Codex** — supported, mode persists all session
- **GitHub Copilot** — supported via npx skills

> [!WARNING]
> Some agents (Opencode, omp) may need re-activation each turn. That's an agent limitation, not a hyperfocus one.

---

## The Research Behind It

> [!NOTE]
> These aren't opinions. Every rule in Hyperfocus comes from peer-reviewed research or published accessibility standards.

| Principle | What the research says | Source |
|---|---|---|
| **Short sentences** | Comprehension drops sharply past 20 words | Oxford/Plain English |
| **Chunking** | ADHD brains process sequential chunks better than parallel info | [PMC6996017](https://pmc.ncbi.nlm.nih.gov/articles/PMC6996017/) |
| **Front-loading** | ADHD readers may not reach the end — answer goes first | [W3C COGA](https://www.w3.org/TR/coga-usable/) |
| **Visual hierarchy** | Good subheadings enable re-entry in under 2 seconds | [ATG Publishing](https://atgpublishing.com/adhd-publishing/) |
| **Blank lines** | Walls of text trigger task abandonment | [ATG Level 1](https://atgpublishing.com/adhd-publishing/) |

Full sources: [W3C COGA](https://www.w3.org/TR/coga-usable/) ・ [ATG ADHD Standards](https://atgpublishing.com/adhd-publishing/) ・ [WCAG Cognitive](https://www.w3.org/WAI/cognitive/) ・ [MDN Writing Guide](https://developer.mozilla.org/en-US/blog/technical-writing/) ・ [Readability Guidelines](https://readabilityguidelines.co.uk/clear-language/simple-sentences/)

---

## Why "Hyperfocus"?

ADHD isn't a deficit to work around. **Hyperfocus is the superpower.**

This plugin removes the friction that blocks it from engaging. When information is structured right, your brain locks in — not because it was forced to, but because nothing got in the way.

---

## Contributing

If you have ideas for better ADHD-friendly formatting — **especially if you have ADHD yourself** — open an issue or PR.

---

## License

[MIT](LICENSE)
