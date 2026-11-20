# Option D — validation results (2026-11-02)

Pre-specification: `option_D_prespecification.md` (written 08:16 UTC, before these results).
Screeners: claude-opus-5-5, claude-sonnet-5-5, claude-haiku-5-5; same fixed prompt v1; independent runs.
Sets: (a) the 100 blind-pilot records; (b) gold-check set = 75 gold papers + 75 random corpus records, shuffled, screeners not told.

| Criterion | Opus | Sonnet | Haiku | Threshold | Result |
|---|---|---|---|---|---|
| 1. Gold-set sensitivity (I or U) | 75/75 | 74/75 (missed GKR "Delegating computation…", EC2) | 75/75 | ≥ 73/75 | met by all |
| 2. Inter-model κ on pilot 100 | Opus–Haiku 0.91 · Opus–Sonnet 0.81 · Sonnet–Haiku 0.81 | | | ≥ 0.80 | met by all pairs; best Opus–Haiku |
| 2b. Inter-model κ on gold-check 150 | Opus–Haiku 0.92 · Opus–Sonnet 0.86 · Sonnet–Haiku 0.94 | | | (supporting) | |
| 3. Clear-cut exclusion (EC1/EC3/EC5) of a gold paper or an adjudicated-relevant pilot record | none | none | none | none | met |

Further figures (pilot 100):
- Sensitivity vs R1 blind labels: Opus 51/58, Sonnet 46/58, Haiku 50/58. Vs adjudicated labels: Opus 67/67, Sonnet 59/67, Haiku 65/67 (Haiku's 2 misses: EC2, confidence 0.80–0.85; both included by Opus → would go to the third screener).
- R1 blind vs adjudicated: sensitivity 0.761, specificity 0.788 (human screening errors concentrated in rule application).
- Note: Sonnet's run assigned decisions in groups after reading titles and the first ~330 characters of abstracts, with category-level rationales; it is therefore used only as the tie-breaking third screener.

**Decision (D7):** criteria 1–3 are met. Main screening uses option D with **Opus + Haiku** as primary screeners (highest agreement, κ 0.91; 4 % disagreement on the pilot), **Sonnet** as third screener for disagreements, U labels and low-confidence exclusions, and R1 for anything still unresolved. Criterion 4 (blind human audit of 400 ensemble-excluded records, one-sided 95 % upper bound of false-exclusion rate ≤ 2 %) is checked after the main screening.

---

## Re-validation of the execution configuration (2026-11-02, before the main run)

Configuration: Claude Code headless (`claude -p`), Max plan, prompt v1 as system prompt, tools disabled, **effort low**, 20 records per call; claude-haiku-5-5 and claude-sonnet-5-5 as primary screeners. Records: the same 249 validation records (pilot 100 + gold-check 150, one duplicate removed).

| Criterion (pre-specified) | Result | Met |
|---|---|---|
| 1. Gold-set sensitivity of the ensemble (a record is excluded only if both screeners exclude it) | 75/75 (Haiku 75/75; Sonnet 74/75) | yes |
| 2. Haiku–Sonnet κ on the 100 pilot records | 0.816 (agreement 0.92); 0.837 on gold-check; 0.830 on all 249 | yes |
| 3. Ensemble assigns no clear-cut exclusion (EC1/EC3/EC5) to a gold or adjudicated-relevant record | none at ensemble level. Note: Sonnet alone labelled one gold paper (CycloneMSM, an ePrint paper) EC5, a rule-application error; Haiku included it, so the record goes to the third screener | yes |

Other figures: sensitivity vs adjudicated pilot labels — Haiku 65/67, Sonnet 64/67; share of records routed to the third screener (disagreement, any U, or exclusion with confidence < 0.8): 32/249 = 12.9 %. Effort low vs medium on the 50 records run at both levels: Haiku 49/50, Sonnet 47/50 identical relevance decisions.
Plan usage: the 498 screenings (249 × 2 models) moved the weekly usage meter by less than one percentage point (73 % before and after).

**Decision:** the effort-low configuration is accepted for the main screening.
