# ARC-AGI-3 Competition — Participant Guide

## What Is ARC-AGI-3?

ARC-AGI-3 is the third iteration of the Abstraction and Reasoning Corpus benchmark, released in 2026 by the ARC Prize Foundation. It is the **first interactive reasoning benchmark** — a collection of hundreds of original turn-based environments, each handcrafted by human game designers, where:

- There are **no instructions, no rules, and no stated goals**
- The agent must **explore** the environment to figure out how it works
- The agent must **discover** what winning looks like
- The agent must **carry knowledge forward** across increasingly difficult levels within each environment

**Human performance: 100%** | **Best AI score so far: ~0.37–0.51%**

---

## Prize Structure

**Total ARC Prize 2026 pool: $2,000,000+**

### ARC-AGI-3 Track — $850,000 total

| Prize | Amount |
|---|---|
| Grand Prize (100% on private eval) | $700,000 |
| Milestone #1 — 1st place (June 30, 2026) | $25,000 |
| Milestone #1 — 2nd place | $10,000 |
| Milestone #1 — 3rd place | $2,500 |
| Milestone #2 — 1st place (Sept 30, 2026) | $25,000 |
| Milestone #2 — 2nd place | $10,000 |
| Milestone #2 — 3rd place | $2,500 |

- The Grand Prize **rolls over to 2027** if unclaimed.
- There is also a separate **Paper Prize** track at arcprize.org/competitions/2026/paper.

---

## Key Deadlines

| Event | Date |
|---|---|
| Milestone #1 scoring cutoff | June 30, 2026 |
| Milestone #2 scoring cutoff | September 30, 2026 |

To be eligible for milestone prizes, you must **open source your solution** by each milestone deadline.

---

## How to Participate

1. **Sign up on Kaggle** at the official competition page:
   [ARC Prize 2026 - ARC-AGI-3 | Kaggle](https://www.kaggle.com/competitions/arc-prize-2026-arc-agi-3)
2. Build your agent locally or in a Kaggle notebook.
3. Submit your solution through Kaggle.
4. To claim prizes, open source your solution (CC0 or MIT-0 license) before the milestone/grand prize deadline.

---

## What Your Agent Must Do

An agent must demonstrate four core capabilities across each environment:

1. **Exploration** — Actively probe the environment by interacting with it to gather information (no passive observation)
2. **Modeling** — Convert raw observations into a generalizable world model (understand the rules of the game)
3. **Goal-setting** — Identify what "winning" or a desirable state looks like without being told
4. **Planning & Execution** — Map a path from current state to goal, and course-correct based on feedback

---

## Scoring: RHAE (Relative Human Action Efficiency)

Pronounced **"Ray"**.

- Your agent is measured by **how many actions it takes** to complete each level, compared to the **second-best human performance** (human baselines are set by first-time human players).
- Score per level = `(human_actions / agent_actions)²`
- The squaring **sharply penalizes inefficiency**: an agent taking 10× as many actions as a human scores only **1%** on that level.
- Final score = average RHAE across all environments.

**What counts as an action:**
- Any discrete interaction that changes the game state (a move, command, or input)

**What does NOT count:**
- Internal tool calls, reasoning steps, retries, or operations that don't alter the environment

---

## Submission Requirements

- Submissions must run inside a **Kaggle notebook**
- Total runtime must be **under 12 hours**
- **No internet access** during Kaggle evaluation — you cannot call hosted APIs (OpenAI, Anthropic Claude, Google Gemini, etc.) at evaluation time
- Solutions must be **reproducible**
- Prize-eligible solutions must be released under **CC0 or MIT-0 license**

---

## Agent Architecture Ideas

Based on early research, competitive agents have used combinations of:

- **Coding agents** — use code execution to test hypotheses about environment rules
- **Executable world-model templates** — formalize discovered rules into runnable models
- **Verifiers** — check whether the current world model correctly predicts observations
- **Plan executors** — execute a plan derived from the world model
- **Self-learning layers** — agents that update their behavior mid-run (shown to give ~2.6× score improvement)

---

## Key Resources

| Resource | Link |
|---|---|
| Official competition page | [arcprize.org/competitions/2026/arc-agi-3](https://arcprize.org/competitions/2026/arc-agi-3) |
| Kaggle competition | [kaggle.com/competitions/arc-prize-2026-arc-agi-3](https://www.kaggle.com/competitions/arc-prize-2026-arc-agi-3) |
| ARC-AGI-3 announcement blog | [arcprize.org/blog/arc-agi-3-launch](https://arcprize.org/blog/arc-agi-3-launch) |
| ARC-AGI-3 benchmark info | [arcprize.org/arc-agi/3](https://arcprize.org/arc-agi/3) |
| Technical report (arXiv) | [arxiv.org/abs/2603.24621](https://arxiv.org/abs/2603.24621) |
| Scoring methodology docs | [docs.arcprize.org/methodology](https://docs.arcprize.org/methodology) |
| ARC Prize verified testing policy | [arcprize.org/policy](https://arcprize.org/policy) |
| ARC Prize 2026 overview | [arcprize.org/competitions/2026](https://arcprize.org/competitions/2026) |

---

## Tips to Get Started

- Study the **RHAE scoring formula** deeply — minimizing actions matters as much as completing tasks.
- Because there's no internet at evaluation time, any model you use must be **bundled locally** (open-weight models like LLaMA, Mistral, Qwen, etc.).
- Prioritize building a good **world-model loop**: observe → hypothesize → act → verify.
- Look at papers on the agent preview competition: [arcprize.org/archive/arc-agi-3-preview-agents](https://arcprize.org/archive/arc-agi-3-preview-agents/)
- The ARC-AGI-2 track is also open in 2026 if you want a fallback challenge: [kaggle.com/competitions/arc-prize-2026-arc-agi-2](https://www.kaggle.com/competitions/arc-prize-2026-arc-agi-2)
