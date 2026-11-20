# R2 (LLM second screener) — fixed prompt, version 1 (2026-11-02)

Model identifier and run date are recorded in the output file header. The prompt below is used verbatim for every batch; only the record block changes. The model receives no information about the research questions, hypotheses, the human reviewer's decisions, author names, or citation counts.

---

You are screening bibliographic records for a systematic review of zero-knowledge proofs (ZKPs). Decide for each record whether it is relevant, using **only** the criteria and rules below and **only** the title, abstract, keywords, year, venue and document type shown.

INCLUDE (I) if:
- IC1: the primary subject is a zero-knowledge proof/argument, or a succinct argument / interactive oracle proof / polynomial commitment / proof-carrying-data scheme designed or used for ZK; or the work applies ZKPs as a core mechanism of its contribution;
- IC2: non-ZK succinct arguments (SNARKs, IOPs, PCP-based arguments, polynomial commitments, lookups, folding, recursion, arithmetization such as R1CS) count as relevant building blocks;
- and the record is in English.

EXCLUDE (E) with the first applicable code:
- EC1: the terms are used in a non-cryptographic sense (graph-theory snarks, Lewis Carroll, bulletproof vests/glass/hosting, ZKP as an unrelated acronym, "zero-knowledge" storage or password managers without a proof system, zero-shot learning);
- EC3: not a research report (editorial, preface, proceedings front matter, erratum, book review, encyclopedia entry, patent, retracted paper);
- EC5: deposit only on a general-purpose repository (Zenodo, SSRN, Figshare, Research Square, HAL, OSF Preprints, TechRxiv, Preprints.org);
- IC4: not in English;
- EC2: ZKPs appear only as background, related work, an alternative or future work, not as a mechanism of the contribution; or the work is about interactive proofs/PCPs/complexity without the zero-knowledge property; or MSM/NTT acceleration without a ZKP motivation; or verifiable computation without a proof system.

Include: Σ-protocols, proofs of knowledge and identification schemes; signatures, credentials, e-cash, voting or shuffles whose construction relies on a ZKP/NIZK/Σ-protocol stated in the abstract; witness indistinguishability, ZAPs, NIWI, SZK, quantum ZK; verifiable computation/ML/databases using proofs or arguments; acceleration of ZKP proving; systems that use ZKPs in their design; attacks, bugs and formal verification of ZK systems; surveys and theses on ZKPs.

UNSURE (U) only when the title and abstract do not allow a decision (e.g., no abstract and an ambiguous title).

Output one JSON object per record, one per line, no other text:
{"rid": "<rid>", "decision": "I|E|U", "reason": "<IC1|IC2|EC1|EC2|EC3|EC5|IC4|NA>", "confidence": <0.0-1.0>, "rationale": "<at most 20 words>"}

Records:
<RECORDS>
