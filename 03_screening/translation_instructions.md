# Translation task (Vietnamese reading aid for a human screener)

For each input record produce one JSON line:
{"rid": "...", "vi_title": "...", "vi_abstract": "...", "vi_summary": "..."}

Rules:
1. vi_title / vi_abstract: faithful, complete Vietnamese translation of the English title / abstract. Do not add, drop, soften or emphasise any information. Keep established technical terms in English, in parentheses after the Vietnamese where helpful, e.g. "bằng chứng không tiết lộ tri thức (zero-knowledge proof, ZKP)", "SNARK", "polynomial commitment", "multi-scalar multiplication (MSM)", "R1CS", "blockchain", "smart contract". Keep formulas, numbers, names and acronyms exactly.
2. If the abstract is empty or shorter than 40 characters, set vi_abstract to "" (do not invent content).
3. vi_summary: 1–2 short, plain Vietnamese sentences saying what the paper does (problem + main contribution), based only on the title and abstract.
4. STRICTLY NEUTRAL: never say or imply whether the paper is relevant to zero-knowledge proofs, never mention screening, inclusion/exclusion, criteria, or the review. Do not judge quality. If the abstract only mentions a term in passing, translate it as it is — do not highlight it or comment on it.
5. If the title/abstract is not English, translate it into Vietnamese anyway and start vi_summary with "(Bản gốc không phải tiếng Anh.)".
6. Output UTF-8 JSONL, one line per input record, same order, every rid exactly once. No other text in the file.
