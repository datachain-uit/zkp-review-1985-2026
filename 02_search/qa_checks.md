# Quality checks — Phase 2 (identification), 2026-11-02

| # | Check | Result | Action taken |
|---|---|---|---|
| Q1 | Scopus exports complete | S1 = 2,422 rows, S2 = 7,249 rows, S1 + S2 = S0 = 9,671; no EID overlap; 45 columns incl. abstract (99 %) and references | none |
| Q2 | OpenAlex record types | 457 datasets, 142 software, 129 book reviews, editorials, errata, etc. in raw data | rule AUTO-EC3 (protocol §6.1a) |
| Q3 | 2026 publication spike | caused by Zenodo (1,076 deposits dated 2026), SSRN, Figshare, Research Square | exclusion EC5 / rule AUTO-SCOPE |
| Q4 | Language | OpenAlex is not language-filtered (~885 non-English by metadata); detection unreliable on short titles | flag only; decided at screening (IC4) |
| Q5 | Random sample of 100 auto-excluded works | 100/100 correctly excluded under the stated rules (proceedings front matter, repository deposits, book reviews, encyclopedia entries, research artifacts) | none |
| Q6 | Clusters with dissimilar member titles (147 with similarity < 0.9; 30 lowest inspected) + 15 random clusters | no false merge found; dissimilarity is OpenAlex truncating titles at the colon (merged correctly by DOI) | display the longest complete title |
| Q7 | Missed duplicates (title variants) | ~222 candidate groups (case, "(extended abstract)", subtitles) | normalized title key + near-duplicate pass (similarity ≥ 0.94, years ±1): 86 additional merges |
| Q8 | Gold-set recall | an early report of 98.7 % was inflated by a substring-matching bug in the check (empty titles matched everything). One gold-set title was wrong (R12: "MSM" instead of "Multi-Scalar Multiplication", copied from PDF metadata) and made a retrieved paper look missed. Correct values: initial string 71/75 = 94.7 %; after revision 1 72/75 = 96.0 % | bug fixed; gold-set title corrected; search revision 1 (protocol §5.1); 3 classic papers added via other methods |
| Q9 | Stable record identifiers | sequential IDs would change after adding sources | IDs now derived from source identifiers (SHA-1) |
| Q10 | Search log | duplicated header line | fixed |
