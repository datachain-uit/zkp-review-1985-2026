# Title/Abstract Screening Guide (v1.1, 2026-11-02 — §3a added after the 100-record pilot)

> **Tóm tắt tiếng Việt cho người screening.** Với mỗi bản ghi, đọc *tiêu đề + abstract + keywords* rồi chọn một trong ba quyết định:
> **I** = giữ (bài *về* ZKP hoặc *dùng* ZKP làm cơ chế chính) · **E** = loại (ghi mã lý do EC1/EC2/EC3/EC5/IC4) · **U** = phân vân (sẽ xem toàn văn; tính như giữ ở bước này).
> Nguyên tắc vàng: **nghi ngờ thì chọn U, không chọn E.** Mỗi bản ghi nên mất 15–30 giây. Không mở toàn văn ở bước này.

## 1. Decisions

| Code | Meaning | When |
|---|---|---|
| **I** | Include in Tier 1 | IC1–IC4 hold (see §2). |
| **E** | Exclude | One exclusion code applies; record the *first* applicable code in this order: EC1, EC3, EC5, IC4, EC2. |
| **U** | Unsure | Title/abstract do not allow a decision (e.g., no abstract and an ambiguous title). Treated as *include* for Tier 1 and resolved at full text. |

## 2. Criteria (protocol §6.1)

- **IC1** — The work's primary subject is a zero-knowledge proof/argument, or a succinct argument / IOP / polynomial commitment / proof-carrying-data scheme designed or used for ZK; **or** it applies ZKPs as a core mechanism of its contribution.
- **IC2** — Non-ZK succinct-argument works are included if they are positioned as components of ZK systems.
- **IC3** — 1985–2026; journal, conference/workshop, book chapter, ePrint/arXiv preprint, or thesis.
- **IC4** — English, title and abstract accessible.
- **EC1** — "Zero-knowledge", "SNARK", "bulletproof", "ZKP", "proof of knowledge" used in a non-cryptographic sense.
- **EC2** — ZKP is mentioned only as background, related work, an alternative, or future work — not as a mechanism of the contribution; or the work is about interactive/probabilistic proofs or complexity without the zero-knowledge property.
- **EC3** — Not a research report: editorial, preface, proceedings front matter, erratum, book review, encyclopedia entry, patent, slides, blog post, retracted paper.
- **EC5** — Only deposited on a general-purpose repository (Zenodo, SSRN, Figshare, Research Square, HAL, OSF Preprints, TechRxiv, Preprints.org).

## 3. Decision rules for frequent cases (worked examples)

| # | Case | Decision | Example (illustrative) |
|---|---|---|---|
| R1 | Graph-theory "snarks" (cubic graphs), Lewis Carroll, "bulletproof" vests/glass/hosting, ZKP as a gene/protein/company acronym, "zero-knowledge" password managers or cloud storage with no proof system | **E – EC1** | "Small snarks with large oddness"; "ASwatch: exposing bulletproof hosting" |
| R2 | Zero-shot / "zero knowledge" transfer in ML, "zero prior knowledge" | **E – EC1** | |
| R3 | Σ-protocols, proofs of knowledge, identification schemes built on them (Schnorr, Fiat–Shamir, Guillou–Quisquater) | **I** | "Efficient identification and signatures for smart cards" |
| R4 | Signatures, ring/group signatures, anonymous credentials, e-cash, e-voting, mixnets/shuffles **whose construction relies on a ZKP/NIZK/Σ-protocol stated in the abstract** | **I** | "A verifiable secret shuffle of homomorphic encryptions" |
| R5 | Same kind of scheme where the abstract does not mention ZK/NIZK/Σ-protocol as part of the method | **E – EC2** | |
| R6 | SNARKs, STARKs, IOPs, PCPs used to build arguments, polynomial commitments, lookup arguments, folding/accumulation, recursion, arithmetization (R1CS, PLONKish, AIR) — even without the ZK property | **I** (IC2) | "Fast Reed-Solomon interactive oracle proofs of proximity" |
| R7 | Interactive proofs, PCPs, complexity classes (IP, AM, MIP) **without** zero-knowledge | **E – EC2** | "IP = PSPACE" |
| R8 | Witness indistinguishability, ZAPs, NIWI, simulation-sound/extractable NIZK, statistical/perfect ZK classes (SZK), quantum ZK | **I** | "ZAPs and non-interactive witness indistinguishability…" |
| R9 | Verifiable computation, verifiable ML, verifiable databases **using proofs/arguments** | **I** | "vSQL…" |
| R10 | Verifiable computation by TEEs, replication, or signatures only (no proof system) | **E – EC2** | |
| R11 | Hardware/software acceleration of MSM, NTT, hashing, FRI **motivated by ZKP / SNARK proving** | **I** | "cuZK…" |
| R12 | MSM/NTT acceleration for ECC signatures, FHE or PQC with no ZKP motivation | **E – EC2** | NTT for homomorphic encryption |
| R13 | Blockchain/IoT/health/identity systems that **use** zk-SNARKs/ZKPs in their design | **I** | "zk-HTLC: …cross-chain…" |
| R14 | Systems papers that list ZKP among possible privacy tools, in related work, or as future work only | **E – EC2** | |
| R15 | MPC/FHE/OT protocols that use ZKPs for malicious security **as a stated component** | **I** | |
| R16 | Attacks, bugs, audits, formal verification of ZK circuits, compilers, verifiers, trusted setups | **I** | under-constrained circuit detection |
| R17 | Surveys, SoKs, tutorials, theses about ZKPs | **I** | |
| R18 | No abstract and the title alone is clearly ZKP-related | **I**; clearly unrelated → **E**; otherwise **U** | |
| R19 | Title/abstract not in English | **E – IC4** (if an English abstract exists, judge it) | |
| R20 | Proceedings volume, front matter, "Preface", book review, erratum that escaped the automatic rules | **E – EC3** | "Preface", "Crypto 2004" |

## 3a. Clarifications added after the pilot (v1.1)

The pilot showed that most disagreements came from a few recurring situations. These clarifications do not change the criteria; they make their application explicit.

| # | Situation | Decision |
|---|---|---|
| C1 | **EC3 is only for non-research items** (preface, proceedings front matter, erratum, book review, encyclopedia entry, patent, magazine/news item, fiction). Books, book chapters, monographs, theses/dissertations, technical reports and extended abstracts **are research reports** — judge their relevance normally. | e.g., a book on ZKPs → **I**; a thesis on 3-round ZK → **I** |
| C2 | arXiv and IACR ePrint papers are **never** EC5 (EC5 is only Zenodo, SSRN, Figshare, Research Square, HAL, OSF, TechRxiv, Preprints.org). Theses on university repositories are not EC5 either. | |
| C3 | The **title** says the work uses or studies ZKPs/SNARKs/ZK-rollups etc. → **I** (R13), even if the abstract is short or truncated. | "…indoor positioning using zero-knowledge proofs" → **I** |
| C4 | Polynomial/vector commitments with evaluation proofs, succinct proofs for committed data, PCP/IOP theses with cryptographic applications → **I** (IC2: R6, R9). | |
| C5 | Overviews of a broad topic (blockchain security, healthcare blockchain, digital-currency regulation, data-science ethics) that only **list** ZKPs among many techniques → **E – EC2** (R14). A survey, book or SoK **whose main topic is ZKPs** → **I** (R17). | |
| C6 | Classic identification protocols (Fiat–Shamir, Feige–Fiat–Shamir, Schnorr) and analyses of their security/abuses → **I** (R3). | |
| C7 | Physical/puzzle ZKPs (Sudoku, Kakuro, card-based) → **I**. | |
| C8 | Non-English and unrelated: record **IC4** (EC1 is also correct; both count as exclusion). | |
| C9 | ZKP mentioned as a possible enabler in a position/vision paper with no protocol design → **U** if ZKPs are part of the proposed solution, otherwise **E – EC2**. | |

## 4. What *not* to judge at this stage

Quality, venue rank, novelty, or whether the paper is "important" — these belong to the Tier 2 quality gate. Tier 1 is a relevance decision only.

## 5. Recording

Fill only the columns `decision` (I/E/U), `reason` (EC1/EC2/EC3/EC5/IC4, or rule number such as R6 for I), and optionally `note`. Do not edit other columns. Save as CSV (UTF-8).
