# Governance Control Tower

**One HTML file. No backend, no build step, no model, no external dependencies.**

The Governance Control Tower is a runnable AI governance demo: a governed
pipeline — grounded retrieval, mandated refusal, a seven-control policy-as-code
gate, human-in-the-loop review, and an append-only audit trail — expressed as
deterministic JavaScript in a single page. Open `index.html` in any browser, or
host it as one static file.

**Run it:** open [`index.html`](index.html) locally, or use the hosted copy on GitHub Pages:
**https://framework-optimization-lab.github.io/governance-control-tower/**

## What it does

| Page | What it demonstrates |
|---|---|
| **Ask** | BM25 retrieval over a fictional operating playbook; answers bounded by retrieved passages with app-generated citations and a confidence tier; out-of-scope questions refused *before* any drafting, with a numeric reason. An "ungoverned baseline" toggle shows the failure mode being prevented. |
| **Gate** | Decision records evaluated by seven deterministic controls → PASS / REVIEW / BLOCK with reasons. Four bundled scenarios (one clean, one review-routed, one triple failure, one should-have-refused); every field editable so you can watch the verdict move. |
| **Review** | REVIEW-routed records queue for a named sign-off with a written rationale. A BLOCK cannot be overridden — it must be fixed at the source. |
| **Dashboard** | Verdict mix, refusal rate, sign-off counts, and the full append-only audit trail (downloadable as JSON). |
| **Playbook** | The bounded corpus: 11 fictional playbook passages and the 6-entry evidence registry every citation is checked against. |

## What's real and what's simulated

Everything governance-critical — retrieval, thresholds, confidence tiers,
refusal, the seven controls, review rules, and audit events — is fully
implemented, deterministic logic. Because the page runs with no backend and no
model, three components are deliberately simple:

| Component | How this file implements it |
|---|---|
| Drafting layer | Extractive — answers are sentences drawn verbatim from the retrieved passages. No language model is involved. |
| Storage | Browser localStorage. Nothing leaves the page. |
| Ungoverned baseline | A labeled deterministic simulation of an unconstrained answer, shown to illustrate the failure mode the gate prevents. |

The seven controls are line-for-line ports of `gate.ts` from
[`ai-governance-explorer`](https://github.com/framework-optimization-lab/ai-governance-explorer),
which in turn implements the model enforced by
[`ai-decision-governance-gate`](https://github.com/framework-optimization-lab/ai-decision-governance-gate)
and the retrieval governance of
[`governed-playbook-assistant`](https://github.com/framework-optimization-lab/governed-playbook-assistant).

All data is fictional and domain-neutral. Clean-room demonstration only.
