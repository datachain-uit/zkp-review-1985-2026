# Option D — LLM-ensemble screening with human audit: pre-specified acceptance criteria
Written 2026-11-02T08:16:19Z (UTC), BEFORE any results of the Sonnet/Haiku/Opus validation runs were seen.

Design: two independent LLM screeners (different models, same fixed prompt v1) label every record. Agreement → ensemble decision. Disagreement, any U, or an exclusion with confidence < 0.8 → third LLM screener; if still unresolved → human (R1) decides with Vietnamese reading aid. A blind human audit of a random sample of ensemble-excluded records estimates the false-exclusion rate.

The ensemble configuration is accepted only if ALL hold:
1. Gold-set sensitivity: the ensemble labels at least 73 of the 75 gold-set papers as I or U (gold records are mixed with 75 random corpus records; screeners are not told).
2. Inter-model agreement on the 100 blind-pilot records: Cohen's kappa >= 0.80 between the two screeners (relevance = I or U).
3. Against R1's blind pilot labels, the ensemble assigns no clear-cut exclusion (EC1/EC3/EC5) to a record that R1 included and that is a gold-set paper or that R1 kept after adjudication.
4. Main-screening audit (checked after screening): blind human review of a random sample of 400 ensemble-excluded records; the one-sided 95 % upper bound of the false-exclusion rate must be <= 2 %. If not met, all ensemble exclusions with confidence < 0.95 are human-screened.

If criteria 1–3 fail for every model pair, the review falls back to option C (LLM-suggested labels, human verification of every record).
