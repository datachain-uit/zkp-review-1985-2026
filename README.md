# Replication package: Zero-Knowledge Proofs, 1985–2026: A Systematic Review

Khoa Tan Vo, Hong-Tri Nguyen and Tu-Anh Nguyen-Hoang. *Zero-Knowledge Proofs, 1985–2026: A Systematic Review of Constructions, Systems, Applications and Their Security.* Submitted to ACM Computing Surveys.

This package holds the records from which the article's counts and statistics are computed: the protocol, the search records, the prompts, every model output, every decision we made, the fixed rule sets and the values of all numbers that the article and its supplement compute from these records. With the method described in the article (Section 3) and the supplement (Section A), each reported number can be checked against these records without re-running the models.

Repository: https://github.com/datachain-uit/zkp-review-1985-2026

## Conventions

- `rid` identifies a work (one deduplicated record); `sid` (S1, S2, ...) identifies a Tier 2 study as cited in the article.
- Screening labels: `I` include, `E` exclude, `U` unsure. `U` counts as include at title and abstract screening. Exclusion codes follow `03_screening/screening_guide.md` (EC1–EC5, IC4).
- Model files record the model, the reasoning-effort setting and the time of each output (`_model_used`, `_effort`, `_time`).
- All percentages are rounded once, half up, from the unrounded values.
- Some of our decision notes are written in Vietnamese, the first language of the authors.

## Contents

| Folder | What it holds | Article |
|---|---|---|
| `01_protocol/` | Protocol with all dated decisions and amendments (D1–D20); pre-specified acceptance criteria for the screening design and their validation | §3, Supp. A.2 |
| `02_search/` | Per-source counts, Scopus queries, search log, gold set and its recall | §3.2, Fig. 3 |
| `03_screening/works.csv` | All 16,161 screened works (title, year, venue, document type, DOI, sources; no abstracts) | §3.3–3.4 |
| `03_screening/auto_excluded.csv` | Works removed by the two metadata rules, with the rule | §3.4 |
| `03_screening/model_labels/` | Raw labels of every screening model run (validation, main screening, third screener, add-only recheck), with rationales | §3.4, Table 2 |
| `03_screening/screening_decisions.csv`, `screening_final.csv` | Ensemble decision per work and final decision with its source | §3.4, Fig. 3 |
| `03_screening/pilot/` | Pilot records, our blind labels, model labels and adjudication | Supp. A.3 |
| `03_screening/audit/` | Blind audit samples (`audit_strata.json`), our labels, results before and after adjudication, the check of the metadata rules, the repeat labelling and its adjudication | §3.4, Supp. A.3 |
| `03_screening/calibration/` | Labels of the second human screener on the pilot records and the results | §10, Supp. A.3 |
| `03_screening/duplicates_*.csv`, `year_corrections.csv` | Merged reports of one work and corrected years | §3.9, Supp. A.2 |
| `04_quality/` | Quality gate of every Tier 1 work, Tier 2 selection and backfill queue, gate rows of the works reinstated after the repeat labelling | §3.6, Supp. A.3 |
| `05_coding/` | Tier 1 coding prompt, model codes, final codes, our blind validation codes and agreement | §3.5, Supp. A.3 |
| `06_fulltext/` | Extraction prompts, both extractors' outputs, merged and verified Tier 2 data, our adjudication, verification, security-label review and performance-claim checks | §3.7, Supp. A.3 |
| `07_snowball/` | Snowball flow, pre-filter exclusions, model labels, our decisions, works added to Tier 1 and Tier 2 | §3.8 |
| `08_analysis/tier1/` | Tables behind the Tier 1 figures, all Tier 1 values, the venue-community rules | §4 |
| `08_analysis/rq5/` | Topic of every work, topic labels and terms, trends, model settings | §9.1, Supp. A.5 |
| `08_analysis/synthesis/` | Synthesis prompts, frozen codebook, both coders' codes, verified codes and our verification | §3.9, §5–§9 |
| `08_analysis/taxonomy/`, `S1_taxonomy_classification.*` | Taxonomy dimensions and the classification of every study (Table S1) | §5.4, Supp. B |
| `08_analysis/tier2/` | Study list (`study_ids.csv`) and the tables behind Sections 5–8 | §5–§8 |
| `S7_quality_scores.csv` | Quality scores QA1–QA8 of every Tier 2 study (Table S7) | §3.7 |
| `numbers/` | The values of all number macros used in the article and supplement (`numbers.csv`, and the LaTeX macro files). Fixed values of the validation runs are in `01_protocol/` and `03_screening/pilot/` | all |

## Where the main numbers come from

| Numbers | Records |
|---|---|
| Records identified, per source | `02_search/prisma_identification.json`, `02_search/search_log.csv` |
| Works screened, included, excluded; decided by us | `03_screening/screening_final.csv` (column `decided_by`) |
| Audit false exclusions and their upper bounds | `03_screening/audit/audit_labels.csv`, `audit_strata.json`, `retest_adjudication.csv` → `audit_results_adjudicated.json` |
| Repeat labelling (agreement, κ) | `03_screening/audit/retest_labels.csv` against `audit_labels.csv` and `human_labels.csv` |
| Second human screener | `03_screening/calibration/calibration_labels.csv` against `03_screening/pilot/` |
| Tier 1 shares and trends | `05_coding/tier1_codes_final.jsonl`, `03_screening/works.csv`, `07_snowball/tier1_snowball.csv` → `08_analysis/tier1/` |
| Tier 2 counts | `06_fulltext/extraction/tier2_final_verified.jsonl`, `08_analysis/synthesis/synthesis_codes_verified.jsonl` → `08_analysis/tier2/` |
| Topics | `08_analysis/rq5/doc_topics.csv`, `topic_labels.csv` → `rq5_topic_trends.csv` |
| Human decisions (Table 2) | One row per decision (five codes per row in `05_coding/validation/human_codes.csv`) in the decision files of `03_screening/`, `05_coding/validation/`, `06_fulltext/adjudication/`, `07_snowball/r1_decisions.csv`, `08_analysis/synthesis/` |

## Not included

- Full texts and abstracts, and raw exports of Scopus, OpenAlex, the IACR ePrint Archive and arXiv: copyright and database licences. Works are identified by title and DOI.
- The labelling pages we used and our working notes.
- Timing columns that no reported number uses. The timing of our pilot labels is kept because the estimate of screening time in §3.4 is computed from it.
- The scripts that run the models and the analysis. They are available from the authors on request.

## Licence and citation

Data and documents: Creative Commons Attribution 4.0 International (CC BY 4.0). Please cite the article when you use this package.
