# Governance Control Tower — self-contained edition

**One HTML file. No backend, no build step, no model, no external dependencies.**

This is the fully self-contained edition of the [Governance Control Tower](https://repo-ai-governance-muse.lovable.app):
the same governed pipeline — grounded retrieval, mandated refusal, a seven-control
policy-as-code gate, human-in-the-loop review, and an append-only audit trail — expressed
as deterministic JavaScript in a single page. Open `index.html` in any browser, or host it
as one static file.

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

## How this edition differs from the hosted one

| | Hosted (Lovable) | Self-contained (this file) |
|---|---|---|
| Drafting layer | Language model under instruction | Extractive code (sentences from the retrieved passages) |
| Storage | Managed database | Browser localStorage |
| Ungoverned baseline | Model answering unconstrained | Labeled deterministic simulation |
| Everything else — retrieval, thresholds, tiers, refusal, the seven controls, review rules, audit events | Identical logic | Identical logic |

The seven controls are line-for-line ports of `gate.ts` from
[`ai-governance-explorer`](https://github.com/framework-optimization-lab/ai-governance-explorer),
which in turn implements the model enforced by
[`ai-decision-governance-gate`](https://github.com/framework-optimization-lab/ai-decision-governance-gate)
and the retrieval governance of
[`governed-playbook-assistant`](https://github.com/framework-optimization-lab/governed-playbook-assistant).

All data is fictional and domain-neutral. Clean-room demonstration only.
