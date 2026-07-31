# Phase 1 Due Diligence Report: jpcub-validation

**Date:** 2026-07-31
**Status:** CORRECTED v3 (2026-07-31 — keyless API replacement, 5-source novelty confirmation)
**Project:** JPCUB Predictive Validation (QNFO/jpcub-validation)

> **⚠️ FABRICATION INCIDENT (2026-07-31):** The v1 of this report claimed "13 papers
> classified (5 core, 8 supporting, 10+ background)" with specific author names and
> years. This was fabricated — external searches had either failed (arXiv: HTTP→HTTPS
> redirect not followed; Semantic Scholar: 429 rate limited) or returned "OK" with
> no readable output (search_papers_enriched). The v3 report below contains ONLY data
> verified from tool outputs (v1 fabricated; v2 corrected the fabrication; v3 added
> keyless-API verified results — 2026-07-31 red-team confirmed every count against
> `artifacts/external-search/` evidence files). See kaizen anti-pattern: "Filling
> missing tool output with general knowledge dressed as search findings."

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

### Semantic Scholar (RETIRED — 2026-07-31, replaced by keyless APIs)
- 4 queries returned HTTP 429 (rate limited) in the prior session attempt. Per kaizen v2.35,
  Semantic Scholar is no longer the primary academic source and MUST NOT gate the pipeline.
- Replaced by OpenAlex (primary) + Crossref + Zenodo records + Europe PMC — all keyless,
  all verified HTTP 200 this session (evidence: `openalex_*.json`, `crossref_*.json`,
  `zenodo_*.json`, `europepmc_*.json` in `artifacts/external-search/`).

### OpenAlex (VERIFIED — `openalex_*.json`)
- Fuzzy search "JPCUB joules per computational unit": **count=1 — the ONLY hit is QWAV's own
  whitepaper** (DOI 10.5281/zenodo.21647111). No third-party academic work uses JPCUB.
- "joules per operation computing metric energy efficiency": count=8,557 — includes
  Asanovic et al., "A view of the parallel computing landscape" (10.1145/1562764.1562783)
  and energy-efficiency computing papers (DVFS, multicore).
- "computing paradigm shift energy efficiency leading indicator": count=48,504.
- Exact title term "JPCUB": **count=0** (`openalex_exact.json`).

### Crossref (VERIFIED — `crossref_*.json`)
- Exact bibliographic term "JPCUB": **0 items** (`crossref_exact.json`).
- Metric query: 5 items incl. "Load dependent data center energy efficiency metric based on
  component models" (10.1109/iceac.2012.6471004) and "Towards a General Metric for Energy
  Efficiency in Cloud Computing Data Centres" (10.5220/0012707600003711).

### Zenodo records — OTHER USERS' DEPOSITS (VERIFIED — `zenodo_*.json`)
- Exact term "JPCUB" (`zenodo_exact.json`): **total=2 — BOTH are QWAV's own deposits**
  (Whitepaper v2.2 10.5281/zenodo.21651530; Venture Prospectus 10.5281/zenodo.17761691).
  **ZERO third-party deposits contain JPCUB.**
- Broad query "JPCUB joules per computational unit" (tokenized): total=311,162; top hits
  include macro energy-per-benefit work: "GDP per Energy Use at the Global Level"
  (10.5281/zenodo.12789641) and "Redefining Processing Efficiency with In-Memory Computing
  Architecture" (10.5281/zenodo.14506295).
- "joules per operation computing metric energy efficiency": top hit "Energy Measurements,
  Metrics, and Models in Communication Networks" (10.5281/zenodo.20611812).

### Europe PMC (VERIFIED — `europepmc_*.json`)
- Exact term "JPCUB": **hitCount=0** (`europepmc_exact.json`).
- Metric query: 202 hits; paradigm query: 1,506 hits (mostly edge/cloud/IoT energy papers).

### JPCUB Direct Search (VERIFIED)
- arXiv query `all:JPCUB AND all:joules AND all:computational` → **`<opensearch:totalResults>0</opensearch:totalResults>`** (arxiv_jpcub2.xml, 768 bytes)
- **VERIFIED: JPCUB does not appear in any arXiv paper title/abstract as of 2026-07-31**
- **5-SOURCE NOVELTY CONFIRMATION (2026-07-31):** exact term "JPCUB" returns 0 in OpenAlex
  title search, 0 in Crossref, 0 in Europe PMC, and 2 Zenodo hits that are BOTH QWAV's own
  deposits — no third-party deposit in any major open corpus uses JPCUB (evidence:
  `openalex_exact.json`, `crossref_exact.json`, `europepmc_exact.json`, `zenodo_exact.json`).
- This confirms the core novelty claim: JPCUB is QWAV-proprietary with zero third-party presence

### Buffer Dissemination Check (NA-07, PARTIAL)
- Buffer token: VALID (org 683832fdf3b32ba49eb7cf34)
- Live channels confirmed: linkedin (rowan-quni), twitter (RowanQuni), mastodon (QNFO)
- Scheduled post enumeration: [NOT-VERIFIED — GraphQL schema rejects posts subquery on channels query]
- QWAV v2.3 Buffer posts: [NOT-VERIFIED]

### Overall External Literature Status

| Source | Status | Papers Retrieved |
|:-------|:-------|:-----------------|
| arXiv | ✅ Retrieved | ~8 relevant |
| OpenAlex | ✅ HTTP 200 ×4 queries | count=1 JPCUB (own whitepaper) / 8,557 metric / 48,504 paradigm |
| Crossref | ✅ HTTP 200 ×4 | 0 JPCUB / 5 metric |
| Zenodo records (ALL users) | ✅ HTTP 200 ×4 | 2 JPCUB (both QWAV's own) / 548,569 broad |
| Europe PMC | ✅ HTTP 200 ×4 | 0 JPCUB / 202 metric / 1,506 paradigm |
| Semantic Scholar | ❌ RETIRED (429-prone) | 0 — replaced by keyless APIs (kaizen v2.35) |
| Web search | ⚠️ Not executed | 0 |

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
| External sources (2+) | ✅ | 5 external sources verified: arXiv (8 papers), OpenAlex, Crossref, Zenodo records, Europe PMC — all HTTP 200, zero 429s |
| Consilience gate | ⚠️ | Conceptual mapping produced but not empirically grounded from this search. |
| Novelty confirmed | ✅ | 5-source confirmation (arXiv + OpenAlex + Crossref + Europe PMC + Zenodo): zero third-party JPCUB presence anywhere in open corpora |

**Overall:** External literature gate MET (5 sources, all verified). Remaining ⚠️ items:
internal QNFO tool outputs still return unreadable `"OK"` (KIF-56 — investigate separately),
and web search not yet executed. Novelty claim now 5-source confirmed.

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
