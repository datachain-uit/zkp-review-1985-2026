# Synthesis prompts (fixed before the runs; doubled braces are template escapes)

## Codebook induction (claude-opus-5-5)

```
You are helping with the qualitative synthesis of a systematic review on zero-knowledge proofs.
You receive, for a random sample of included studies, two independent extractions (A and B) of one free-text field: {desc}.
Derive an inductive codebook for this field (Nickerson-style taxonomy development): 8-15 mutually distinct codes that together cover
the sample, at a level of abstraction useful for a survey (not paper-specific). Use UPPER_SNAKE_CASE codes. For each code give a one-sentence
definition, an inclusion rule that separates it from its nearest neighbour code, and 2-4 example study IDs from the sample. Add OTHER.
Return only JSON: {{"field": "...", "codes": [{{"code": "...", "definition": "...", "rule": "...", "examples": ["S12", ...]}}]}}
```

## Coding with the frozen codebook (claude-sonnet-5-5 and claude-opus-5-5)

```
You code included studies of a systematic review on zero-knowledge proofs. For each study you receive two independent
extractions (A and B) of several free-text fields. Code ONLY from this text. Use only the codes of the codebook below; multi-label is allowed;
use [] when the field is empty or nothing applies; use OTHER only when no code fits.
CODEBOOK:
{codebook}
Also extract PERF: every quantitative performance comparison stated in the field "speedup" as a list of objects
{{"what": system/kernel/operation, "platform": CPU|GPU|FPGA|ASIC|MULTI_NODE|MOBILE|NR, "metric": prover_time|verifier_time|proof_size|throughput|memory|other,
"factor": number (>1 means better than baseline), "baseline": short name of the baseline, "baseline_kind": prior_work|cpu_single|cpu_multi|naive|other,
"size": instance size as stated or ""}}. Do not compute factors that are not stated or directly implied by two stated numbers.
Return one JSON object per study, one per line, no other text:
{{"rid": "S..", "LIM": [...], "OPEN": [...], "WHY": [...], "STMT": [...], "PERF": [...]}}
```
