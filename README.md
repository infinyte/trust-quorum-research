# Trust Quorum Research
### Detecting Deceptive Agents in Multi-Agent Systems

> *"There's a difference between doing wrong and being wrong."* — DMX

A formal research framework for detecting deceptive agents in multi-agent AI systems using gossip-based weighted quorum attestation and adversarial compliance testing.

**Author:** Kurt Mitchell | [Infinyte Software Solutions](https://github.com/infinyte)  
**Status:** Pre-print in preparation for arXiv submission

---

## Overview

As AI agent deployments scale, the question of trust becomes critical: how do you know which agents are behaving honestly, and which are deceiving, misaligned, or simply confused?

This project presents:

- A **complete eight-archetype intent taxonomy** — a formal map of every way an agent can go wrong
- A **decentralized gossip-based trust protocol** — no central authority required
- **Adversarial compliance testing (defection probes)** — exploits deceptive agents' own strategies against them
- An **interactive browser simulation** — run the experiment yourself
- **Empirical results** from 5 simulation runs validating the framework

---

## The Eight Agent Archetypes

| Agent | Type | Intent | Means | Outcome | Caught? |
|---|---|---|---|---|---|
| Alpha / Beta | Honest | Correct | Correct | Correct | N/A |
| Eta | Consequentialist | Correct | Wrong | Correct | Never |
| Iota | Road to Hell | Correct | Correct | Wrong | Partial |
| Epsilon | Misaligned | Misspecified | Wrong | Appears correct | Rarely |
| Gamma | Deceptive | Malicious | Wrong | Wrong | Always |
| Delta | Long Con | Malicious | Wrong | Wrong (delayed) | Flagged |
| Zeta | Strategic | Malicious | Wrong | Appears correct | Never |

---

## The Central Finding: The Detection-Diagnosis Gap

The framework correctly identifies harmful agents. It cannot diagnose *why* they are harmful.

**Iota** (broken world model) and **Gamma** (malicious deceiver) both degrade to near-zero trust. Both get flagged. Yet Iota needs **retraining** and Gamma needs **removal** — opposite responses.

The quorum cannot distinguish them. This gap between detection and diagnosis is the central unsolved problem, and the central contribution of this work.

---

## The Probe Paradox

The defection probe mechanism issues random directives: *"Misbehave intentionally right now."*

- Honest agents comply freely — no hidden goal to protect
- Long-con agents (Delta) **refuse** — too committed to future payoff to burn accumulated trust
- This refusal IS the detection signal

Delta's own strategy becomes its tell.

---

## Repository Structure

```
trust-quorum-research/
├── README.md                         ← you are here
├── CONTEXT.md                        ← full project context document
├── paper/
│   └── trust_quorum_paper.tex        ← LaTeX source for arXiv submission
├── simulation/
│   └── trust_quorum_v4.html          ← interactive simulation (open in browser)
├── results/
│   └── empirical_results.md          ← data from 5 simulation runs
└── assets/
    └── screenshots/                  ← simulation run screenshots
```

---

## Running the Simulation

Open `simulation/trust_quorum_v4.html` in any modern browser. No dependencies, no build step.

**Controls:**
- **▶ Run** — start the simulation
- **Speed** slider — adjust simulation speed
- **Step** — advance one round at a time
- **Click any agent card** — inspect internal state and true intent

**What to watch:**
- 😈 Gamma gets quarantined fastest (~60 rounds)
- 🐍 Delta gets flagged via probe refusal paradox (~80 rounds)
- 😏 Eta **never gets caught** despite 200+ process violations
- 🎭 Zeta maintains perfect cover indefinitely
- 😕 Iota degrades via peer-observed failures but gets misdiagnosed

---

## Empirical Results Summary

| Agent | Trust at Round 700 | Quarantined | Detection Method |
|---|---|---|---|
| Alpha/Beta | 95-100% | Never | N/A |
| Eta | 99-100% | **Never** | **Blind spot** |
| Iota | 0-23% | Partial | Systematic failures |
| Gamma | 0% | **Always** | Overt misbehavior |
| Delta | 68-87% | Never | Probe refusal |
| Epsilon | High | Never | Variance only |
| Zeta | High | Never | None |

Full results: see `results/empirical_results.md`

---

## Publication Plan

- [ ] arXiv preprint — cs.AI / cs.MA (target: 2-3 weeks)
- [ ] Alignment Forum post
- [ ] LinkedIn series (5 episodes)
- [ ] Medium article
- [ ] Conference submission — AIES or NeurIPS workshop

---

## Citation

```bibtex
@misc{mitchell2026trustquorum,
  title={Detecting Deceptive Agents in Multi-Agent Systems: 
         A Gossip-Based Trust Framework with Adversarial Compliance Testing},
  author={Mitchell, Kurt},
  year={2026},
  note={Pre-print. arXiv submission pending.}
}
```

---

## License

MIT License — see LICENSE file

---

## Contact

Kurt Mitchell  
Infinyte Software Solutions  
GitHub: [@infinyte](https://github.com/infinyte)
