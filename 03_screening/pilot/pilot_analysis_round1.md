# Pilot analysis — round 1 (blind), 2026-11-02

- Sample: first 100 records of the random pilot order (seed 20261102); R1 = human (blind), R2 = claude-opus-5-5, prompt v1.
- Relevance = decision I or U.

| Metric (R1 blind labels as reference) | Value |
|---|---|
| R1: I / E / U | 53 / 42 / 5 |
| R2: I / E / U | 66 / 33 / 1 |
| Confusion (TP / FN / FP / TN) | 51 / 7 / 16 / 26 |
| Raw agreement | 0.770 |
| Cohen's κ | 0.514 |
| R2 sensitivity | 0.879 |
| R2 specificity | 0.619 |
| R1 time per record | median 27.3 s, mean 40.5 s, p90 82.2 s; 67.5 min for 100 records |

**Pre-specified option-C rule (protocol §7.2): not met with R1's blind labels as reference (sensitivity 0.879 < 0.95).**

## Pattern of the 23 relevance disagreements (before adjudication)

- 16 records R1 excluded and R2 included. Recurring causes: EC3 applied to research reports (books, book chapters, a monograph, a thesis, a technical report, an arXiv paper), EC5 applied to a thesis, EC2 applied to IC2 building blocks (polynomial commitments, PCP/IOP thesis), and EC2/EC1 applied to records whose title states that ZKPs are used.
- 7 records R1 included/unsure and R2 excluded: AI planning, broad blockchain/regulation overviews listing ZKPs among many techniques, an e-voting position paper, a formal-verification paper.
- These patterns led to screening guide v1.1 (§3a, clarifications only; criteria unchanged).

## Next step

R1 adjudicates the 23 disagreements with both labels and R2's rationale visible (`pilot_adjudication_tool.html`). Metrics are then recomputed against the adjudicated reference and both versions are reported.

## Adjudication result (R1, unblinded, 2026-11-02)

- R1 adjudicated all 23 relevance disagreements with R2's label and rationale visible, using guide v1.1.
- **R1 changed to R2's position in 23/23 cases.**
- Against the adjudicated labels: R2 sensitivity 1.00, specificity 1.00, κ 1.00; R1's blind labels: sensitivity 0.761, specificity 0.788, κ 0.514.
- **Interpretation.** Because the adjudicator saw R2's answer and rationale, the adjudicated labels are not independent of R2; R2's perfect agreement with them is partly circular and cannot by itself establish R2's accuracy (possible automation bias / anchoring). These figures are reported, but R2's validity is established with evidence that does not pass through R2's answers:
  1. sensitivity on the 75-paper gold set, mixed with 75 random corpus records so the screener cannot recognise the gold records (`goldcheck_R2_input.jsonl`);
  2. agreement among independent LLM screeners (different models, same fixed prompt);
  3. a blind human audit sample in the main screening (protocol §7, to be updated).
- R1's blind errors were concentrated in rule application (EC3/EC5 applied to books, chapters, theses and technical reports; EC2 applied to IC2 building blocks), which guide v1.1 (§3a) addresses.
