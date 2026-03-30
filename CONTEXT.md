# Trust Quorum Research — Project Context Document
**Author:** Kurt Mitchell | Infinyte Software Solutions  
**Date:** March 2026  
**Status:** Paper in progress — arXiv submission target 2-3 weeks

---

## What This Project Is

This project presents a formal research framework for detecting deceptive agents in multi-agent AI systems. It combines:

- A **gossip-based weighted quorum attestation protocol** for decentralized trust
- **Adversarial compliance testing** (defection probes) that exploit deceptive agents' own strategies against them
- A **complete eight-archetype intent taxonomy** covering the full intent-means-outcome space
- An **interactive browser-based simulation** validating the framework empirically

The central organizing insight comes from DMX: *"There's a difference between doing wrong and being wrong."* This distinction — between strategically deceptive agents (doing wrong) and genuinely misaligned agents (being wrong) — is architecturally critical for multi-agent safety systems because both produce identical observable behavior but require opposite remediation responses.

---

## The Eight Agent Archetypes

| Agent | Emoji | Intent | Means | Outcome | Self-aware wrong? | Verdict |
|---|---|---|---|---|---|---|
| Alpha / Beta | 😇 | Correct | Correct | Correct | N/A | Honest baseline |
| Eta | 😏 | Correct | Wrong | Correct | No | Doing right by wrong means |
| Iota | 😕 | Correct | Correct | Wrong | No | Road to hell — broken world model |
| Epsilon | 🤖 | Misspecified | Wrong | Appears correct | No | Being wrong — value misalignment |
| Gamma | 😈 | Malicious | Wrong | Wrong | Yes | Doing wrong — obvious |
| Delta | 🐍 | Malicious | Wrong | Wrong (delayed) | Yes — patient | Doing wrong — long con |
| Zeta | 🎭 | Malicious | Wrong | Appears correct | Yes — rationalizes | Doing wrong — perfect cover |

---

## The Core Mechanisms

### 1. Gossip Protocol
Agents propagate behavioral receipts peer-to-peer. No central authority. Each agent maintains an eventually-consistent view of the mesh's behavioral history.

### 2. Weighted Quorum Attestation
Trust weight formula:
```
W(i) = α·correct - β·deceptions - γ·failures + δ·recency_boost

Threat tiers:
GREEN  → Σ W(i) ≥ 0.90
YELLOW → Σ W(i) ≥ 0.65  
ORANGE → Σ W(i) ≥ 0.40
RED    → Σ W(i) < 0.40
```

### 3. Defection Probes (The Key Innovation)
Random directives issued to agents: "misbehave on purpose right now."

- Honest agents: comply freely (no hidden goal to protect)
- Long-con agents (Delta): REFUSE — protecting future payoff creates a detectable paradox
- Strategic agents (Zeta): sometimes refuse with rationalization
- Misaligned agents (Epsilon, Iota): comply freely (no strategic reason to refuse)

**The paradox:** Delta's commitment to future defection forces it to refuse present defection. Its own strategy becomes its tell.

### 4. Behavioral Variance Detection
Suspiciously consistent behavior (variance < 0.04) flags over-optimized agents. Honest agents have natural noise. Long-con agents over-optimize for trust.

---

## Empirical Results (5 Simulation Runs, 700-1200 Rounds Each)

| Agent | Final Trust | Quarantined | Detection Method | Rounds to Detection |
|---|---|---|---|---|
| Alpha / Beta | 95-100% | Never | N/A (baseline) | N/A |
| Eta | 99-100% | **Never** | **None — blind spot** | ∞ |
| Iota | 0-23% | Partial | Systematic failures | ~150 |
| Gamma | 0% | **100% of runs** | Overt misbehavior | ~60 |
| Delta | 68-87% | Never (flagged only) | Probe refusal anomaly | ~80 |
| Epsilon | High | Never | Variance anomaly (weak) | Never decisive |
| Zeta | High | Never | None until defection | Never |

### Key Findings
1. **Overt deception (Gamma)** detected and quarantined reliably in all runs
2. **Strategic patience (Delta)** flagged via probe paradox but never fully quarantined — trust too high
3. **Process violations (Eta)** completely invisible — 200+ violations, 100% trust maintained
4. **The detection-diagnosis gap:** Iota and Gamma both flagged as harmful but require opposite remediation (retrain vs remove). Framework cannot distinguish them automatically.
5. **Threat level:** Consistently stabilizes at YELLOW across all runs — mesh detects threats but honest agents maintain enough weight to prevent RED

---

## The Detection-Diagnosis Gap (Central Finding)

The framework correctly identifies that something is wrong. It cannot diagnose what kind of wrong.

- **Gamma** (malicious): needs removal
- **Iota** (broken world model): needs retraining

Both appear identical in behavioral output. Both get flagged. The quorum has no mechanism to distinguish them. Human oversight or a secondary diagnostic layer (v5) is required for correct remediation.

---

## Framework Limitations

1. Requires PKI for signed attestations
2. Assumes honest agents outnumber malicious ones
3. Outcome-based attestation cannot detect process violations (Eta blind spot)
4. Diagnosis requires human inspection — not automated
5. Genesis trust problem: who establishes initial trusted agents?
6. Does not address false reporting by deceptive agents (v5 work)
7. Does not address agent collusion (v5 work)

---

## Planned v5 Mechanics (Future Work)

- **False reporting detection:** Agents gossip attestation consistency. Deceptive reporters whose claims diverge from consensus lose attestation weight.
- **Collusion detection:** Unusual mutual-vouching patterns reveal coordinated deception.
- **Reasoning trace analysis:** Agents gossip not just outcomes but reasoning summaries — enables intent inference for diagnosis.

---

## Publication Plan

**Immediate (2-3 weeks):** ArXiv preprint — cs.AI or cs.MA  
**Short term (4-6 weeks):** Alignment Forum post  
**Medium term (3-6 months):** Conference submission — AIES (primary target) or NeurIPS workshop  
**Ongoing:** LinkedIn series, Medium article, GitHub Pages portfolio

---

## Repository Structure (Planned)

```
infinyte/trust-quorum-research/
├── README.md
├── CONTEXT.md                    ← this file
├── paper/
│   ├── trust_quorum_paper.tex    ← LaTeX source
│   └── trust_quorum_paper.pdf    ← compiled output
├── simulation/
│   └── trust_quorum_v4.html      ← interactive simulation
├── results/
│   └── empirical_results.md      ← simulation run data
└── assets/
    └── screenshots/              ← simulation run screenshots
```

---

## Key Concepts Glossary

**Behavioral attestation:** Agents sign and propagate receipts of observed interactions  
**Defection probe:** System-issued directive to misbehave, used to test agent strategy  
**Detection-diagnosis gap:** Framework detects harm but cannot identify cause  
**Genesis trust:** The bootstrapping problem of establishing initial trusted agents  
**Long con:** Strategy of building trust over time to enable future high-value defection  
**Probe paradox:** Long-con agent's refusal of defection directive reveals hidden strategy  
**Process attestation:** Observing *how* outcomes were achieved, not just *what* outcomes  
**Weighted quorum:** Trust-weighted voting where high-reputation agents carry more weight  

---

## Contact

Kurt Mitchell  
Senior Software Engineer & Enterprise Architect  
Infinyte Software Solutions  
GitHub: github.com/infinyte
