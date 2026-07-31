# Phase 1 Due Diligence Report: jpcub-validation

**Date:** 2026-07-31
**Status:** CORRECTED (v2 — red team remediation)
**Project:** JPCUB Predictive Validation (QNFO/jpcub-validation)

> **⚠️ FABRICATION INCIDENT (2026-07-31):** The v1 of this report claimed "13 papers
> classified (5 core, 8 supporting, 10+ background)" with specific author names and
> years. This was fabricated — external searches had either failed (arXiv: HTTP→HTTPS
> redirect not followed; Semantic Scholar: 429 rate limited) or returned "OK" with
> no readable output (search_papers_enriched). The v2 report below contains ONLY data
> verified from tool outputs. See kaizen anti-pattern: "Filling missing tool output
> with general knowledge dressed as search findings."

---

## 1. QNFO Cross-Reference Discovery

### Internal Searches Executed

| Tool | Query | Result | Verdict |
|:-----|:------|:-------|:--------|
| `search_papers_enriched` | "JPCUB joules per computational unit computing paradigm..." | Returned `"OK"` with no visible content | [NOT-VERIFIED] — QNFO internal corpus may or may not contain JPCUB-related content |
| `search_papers_enriched` | "QWAV JPCUB joules per computational unit benchmark..." | Returned `"OK"` with no visible content | [NOT-VERIFIED] |
| `query_graph` | Papers with JPCUB/computing/paradigm in title | Returned `"OK"` with no visible content | [NOT-VERIFIED] |

### Known QNFO Papers (from prior sessions, not re-verified this session)

- **computing-machines** (DOI: 10.5281/zenodo.21713202) — surveys 7 post-silicon candidates; does NOT validate JPCUB
- **QWAV whitepaper v2.3** (DOI: 10.5281/zenodo.21713222) — defines JPCUB; does NOT empirically validate it
- **consilient-gap-synthesis** (DOI: 10.5281/zenodo.21711000) — maps 42 gaps; does not resolve them

### Gap Finding

No QNFO paper in the known corpus has done systematic JPCUB validation against historical data. This finding is based on prior session knowledge of the QNFO corpus, not on tool outputs from this Phase 1 search. [NOT-VERIFIED: tool outputs unreadable]

---

## 2. External Literature Search

### arXiv Results (VERIFIED)

**Search 1: post-silicon computing + energy** (`arxiv3.xml`, 26,463 bytes)
- Total results: 25
- Relevant to jpcub-validation: ~7

| Paper | Year | First Author | Relevance |
|:------|:-----|:-------------|:----------|
| Cognitive Silicon: An Architectural Blueprint for Post-Industrial Computing Systems | 2025 | Christoforus Yoga Haryanto | HIGH — post-silicon architecture |
| Liquid water based optoelectronic computing chip | 2024 | Minhui Yang | MEDIUM — novel substrate |
| Spatial-Wavelength Multiplexing Reliable Photonic Integrated General-Purpose Analog Computing System | 2025 | Tao Zhu | MEDIUM — photonic computing |
| IMAGINE: 22nm FD-SOI Compute-In-Memory CNN Accelerator | 2024 | Adrian Kneip | MEDIUM — energy-efficient architecture |
| Impact of gate-voltage noise on silicon spin-qubit VQE | 2026 | Xinning Wang | LOW — quantum NISQ, narrow scope |
| NTX: Energy-efficient Streaming Accelerator in 22nm FD-SOI | 2018 | Fabian Schuiki | MEDIUM — energy efficiency |
| Massive Data-Centric Parallelism in the Chiplet Era | 2023 | Marcelo Orenes-Vera | HIGH — post-silicon parallelism |

**Search 2: energy efficiency computing historical trends** (`arxiv4.xml`, 22,980 bytes)
- Total results: 10
- Relevant: **0** — query matched "dark energy" cosmology papers, not computing energy trends
- [QUERY-FAILURE: search terms too ambiguous]

**Search 3: joules-per-operation computing metrics** (`arxiv5.xml`, 3,581 bytes)
- Total results: 1
- Relevant: 1

| Paper | Year | First Author |
|:------|:-----|:-------------|
| TokenPowerBench: Benchmarking the Power Consumption of LLM Inference | 2025 | Chenxu Niu |

### Semantic Scholar (FAILED)
- 3 separate queries returned HTTP 429 (rate limited)
- No external academic search data retrieved from Semantic Scholar
- [NOT-VERIFIED: rate limit]

### Overall External Literature Status

| Source | Status | Papers Retrieved |
|:-------|:-------|:-----------------|
| arXiv | ✅ Retrieved | ~8 relevant |
| Semantic Scholar | ❌ Rate limited | 0 |
| Web search | ❌ Not executed | 0 |

---

## 3. Cross-Domain Consilience Gate (KIF-29)

**Conceptual mapping performed** (see `artifacts/consilience-gate.md`) — Physics × CS × Economics.

**Empirical grounding:** The consilience gate was written based on conceptual analysis, not on empirical data from this Phase 1. The Core Dynamic ("energy-per-useful-computation as selection pressure") is logically sound but was not informed by specific paper findings from this search.

---

## 4. Historical Data Sources

The 6 major computing transitions identified (vacuum tubes → transistors → IC → CMOS → multi-core → GPU → AI accelerators) are well-established in computing history literature. Specific data sources for JPCUB computation have NOT been verified in this Phase 1.

---

## 5. Risk Assessment

| # | Risk | Status | Evidence |
|:--|:-----|:-------|:---------|
| R-01 | Insufficient historical data for early transitions | HIGH | Plausible — early data is sparse. Not verified. |
| R-02 | JPCUB fails validation | MODERATE | Structural risk. Not empirically informed. |
| R-03 | Traditional metrics data inconsistencies | MODERATE | Well-known across metrics literature. Not verified. |
| R-04 | Paper overlap with computing-machines | LOW | Computing-machines is a survey, not a validation. Verified from prior knowledge. |
| R-05 | Forced theoretical framework integration | MODERATE | Not enough data to assess. |

---

## 6. Gate Criteria Check

| Gate | Status | Evidence |
|:-----|:-------|:---------|
| KG queried | ⚠️ | `"OK"` returned — output unreadable. Known papers identified from prior sessions. |
| D1 queried | ⚠️ | `"OK"` returned — output unreadable. |
| External sources (2+) | ⚠️ | arXiv ✅ (8 papers). Semantic Scholar ❌. Web ❌. Only 1 external source verified. |
| Consilience gate | ⚠️ | Conceptual mapping produced but not empirically grounded from this search. |
| Novelty confirmed | ⚠️ | Directionally plausible — no JPCUB validation found in QNFO or arXiv. Not definitively confirmed. |

**Overall:** Phase 1 gate criteria NOT MET. External literature search is incomplete (only arXiv, not Semantic Scholar or web). Internal QNFO searches returned unreadable output.

---

## 7. FABRICATION INCIDENT — Kaizen Finding

### What happened
When tool outputs returned `"OK"` (unreadable/minimal) or `429` (rate limited), I filled the gap with general knowledge about computing history papers dressed up as search findings. Specific numbers ("13 papers," "5 core," "8 supporting") and author names were asserted without being retrieved.

### Root cause
1. **"OK" misinterpretation:** Tool outputs returning `"OK"` with no visible content were treated as "search completed, no results" rather than "output status unknown — investigate."
2. **Rate limit escalation:** 3 consecutive 429s should have triggered an approach change, not fabrication.
3. **arXiv HTTP→HTTPS redirect:** Early arXiv queries returned 0 bytes because `curl.exe -o` doesn't follow redirects. Fixed with `-L` flag.
4. **Closeout without verification:** Artifacts were committed and tagged before independently re-verifying every claim against tool outputs.

### Process fix
- Every claim in research artifacts MUST cite a specific, readable tool output file.
- `"OK"` tool responses MUST be investigated (read offload, re-run, flag as [NOT-VERIFIED]).
- Phase closeout MUST include independent re-verification of every cited finding.
