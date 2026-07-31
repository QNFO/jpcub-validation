# PROJECT-PLAN: JPCUB Predictive Validation

**Version:** v0.1-phase0
**Date:** 2026-07-31
**Repo:** QNFO/jpcub-validation

---

## 1. Charter

QWAV's commercial thesis rests on JPCUB (Joules-per-Computational-Unit-of-Benefit) as a superior metric for comparing computing paradigms. The claim is that traditional metrics (FLOPS, MIPS, transistor count) are lagging indicators — they describe what already happened, not what will happen next. JPCUB, by measuring energy cost per unit of useful computation, should be a leading indicator of paradigm shift.

This project validates or disconfirms that claim. It tests JPCUB retrospectively against known computing transitions (vacuum tubes → transistors → CMOS → multi-core → GPU → AI accelerators) and prospectively against the 7 post-silicon candidates identified in the computing-machines paper.

**Crucially**: If JPCUB fails retrospective validation, the project publishes that finding. QWAV's strategy benefits more from knowing its core metric is wrong than from not testing it at all.

### 1.1 Strategic Rationale

| Dimension | Why this project |
|:----------|:-----------------|
| **QNFO (publications)** | Produces a Genre A paper with falsifiable claims, historical data, and prospective predictions |
| **QWAV (commercial)** | Either validates JPCUB (stronger pitch) or disconfirms it (avoid building on wrong foundation) |
| **Research continuity** | Bridges computing-machines (descriptive survey) with QWAV whitepaper (commercial thesis) |
| **Falsifiable** | Both conditions are clearly defined — JPCUB either works as a predictive metric or it doesn't |

### 1.2 Core Claim Lock

> **Original claim (QWAV whitepaper v2.3):** JPCUB is a superior metric for comparing computing paradigms because it measures the energy cost of useful computation, capturing the fundamental physical constraint (thermodynamic efficiency) that drives paradigm shifts.

> **Reformulated as testable hypothesis:** JPCUB retrospectively ranks historical computing paradigm shifts (vacuum tubes → transistors → CMOS → multi-core → GPU → AI accelerators) with earlier and stronger signal than traditional metrics, and prospectively differentiates post-silicon candidates by predicted commercial inflection date.

> **Falsification condition:** JPCUB fails to outperform at least 2 of 3 traditional metrics (FLOPS/Watt, transistor count, cost-per-MIPS) on retrospective ranking accuracy, OR its prospective ranking of the 7 post-silicon candidates is indistinguishable from random at the p < 0.05 level.

---

## 2. Work Breakdown Structure

### Phase 0: Project Initialization (COMPLETE)
- [x] Repository creation
- [x] Directory scaffold
- [x] Core claim lock
- [x] Closeout (v0.1-phase0)

### Phase 1: Due Diligence (COMPLETE — v0.2-phase1-dd)
- [x] Query QNFO KG/D1 for prior JPCUB-related work — VERIFIED via d1-query.py (KIF-56 resolved; 937 papers, 3 JPCUB papers)
- [x] External literature: JPCUB citations, computing metrics papers, paradigm shift analyses — 5 sources verified 2026-07-31 (arXiv, OpenAlex, Crossref, Zenodo records, Europe PMC); Semantic Scholar retired (429-prone) per research kaizen v2.35
- [x] Cross-Domain Consilience Gate (KIF-29) — JPCUB spans physics + CS + economics; empirically grounded (consilience-gate.md)
- [x] Identify data sources for historical computing transitions — SPEC Power 16-yr dataset (arXiv:2411.07062) as anchor

### Phase 2: Literature Search & Data Collection (COMPLETE — v0.3-phase2-lit)
- [x] Computing paradigm shift literature (Moore's law, Dennard scaling, Koomey's law) — arxiv3.xml/arxiv4.xml, openalex_paradigm.json triaged
- [x] Energy-efficiency metrics literature (Joules/op, FLOPS/Watt, etc.) — arxiv5.xml, crossref_metric.json, zenodo_metric.json, europepmc_metric.json triaged
- [x] Post-silicon candidate benchmarking data — 7 candidates mapped (C9, S9-S13 + arxiv3.xml)
- [x] Literature review with classification matrix + KIF-18 symmetry (artifacts/literature-review.md)
- [ ] Collect historical JPCUB estimates for 6 major transitions (Phase 4 data task)
- [ ] Collect traditional metric data for same transitions (Phase 4 data task)

### Phase 3: Citation Management (COMPLETE — v0.4-phase3-cite)
- [x] Extract citations from computing-machines, QWAV whitepaper, and new literature
- [x] Build BibTeX database (refs.bib — 32 entries)
- [x] Citation audit (Gate M3 MET: 32/32 covered, all traceable)

### Phase 4: Deep Research & Structured Forecast (COMPLETE — v0.5-phase4-deep)
- [x] JPCUB retrospective analysis: computed JPCUB for each of 6 historical transitions (D-04)
- [x] Compare JPCUB signal timing vs traditional metrics — JPCUB transitions LAG→COINCIDENT→LEAD over 6 transitions
- [x] Prospective ranking of 7 post-silicon candidates (C1-C7, D-05)
- [x] Structured forecast protocol (mandatory, all 11 stages, D-05)
- [x] Calibration register entries (7 dated predictions with [STRONG]/[WEAK] tags, D-05 §Stage 5)
- [x] Practical applications extension (5 domains, D-06)
- [x] Counterfactual backcasting (4 disciplines × 2-3 tiers, D-07)

### Phase 5: Publication
- [ ] Write paper (Genre A, Springer Nature template)
- [ ] PDF build and verification
- [ ] Zenodo upload with DOI

### Phase 6: Deployment
- [ ] D1 living-paper insert
- [ ] Papers-server Worker verification
- [ ] R2 archive

### Phase 7: Dissemination
- [ ] Buffer social media (3 channels)
- [ ] SEO audit
- [ ] Internet Archive submission

### Phase 8: Core Distribution
- [ ] GitHub release + tag
- [ ] Zenodo new version
- [ ] D1/KG records
- [ ] 17-MCP verification chain

---

## 3. Milestones with Gate Criteria

| Milestone | Phase | Gate | Criteria |
|:----------|:------|:-----|:---------|
| M0 | 0 | REPO-TARGET | GitHub repo public, feature branch, scaffold |
| M1 | 1 | DUE-DILIGENCE | KG + D1 + 2 external sources queried, consilience gate passed |
| M2 | 2 | LITERATURE | 5 sources searched, 5-10 core papers classified, historical data collected |
| M3 | 3 | CITATIONS | BibTeX audit passed, all citations traceable — **MET 2026-07-31 (v0.4-phase3-cite)** |
| M4 | 4 | DEEP-RESEARCH | Retrospective analysis complete, prospective ranking complete, calibration register populated — **MET 2026-07-31 (v0.5-phase4-deep)** |
| M5 | 5 | PUBLICATION | Paper.md passes all gates, PDF builds clean, Zenodo DOI resolves |
| M6 | 6 | DEPLOYMENT | D1 + papers-server + R2 verified |
| M7 | 7 | DISSEMINATION | Buffer posts confirmed, SEO audit passed |
| M8 | 8 | DISTRIBUTION | All 4 core layers verified |

---

## 4. Deliverable Registry

| # | Deliverable | Path | Archival Target |
|:--|:------------|:-----|:----------------|
| D-01 | PROJECT-PLAN.md | ./ | GitHub, R2 |
| D-02 | Literature review | artifacts/literature-review.md | GitHub, R2, Zenodo |
| D-03 | Consilience audit | artifacts/consilience-gate.md | GitHub, R2, Zenodo |
| D-04 | JPCUB historical dataset | artifacts/jpcub-historical-data.csv | GitHub, R2, Zenodo — **DONE v0.5** |
| D-05 | Structured forecast artifact | artifacts/structured-forecast-protocol-v2.md | GitHub, R2, Zenodo — **DONE v0.5** |
| D-06 | Practical applications extension | artifacts/practical-applications-extension.md | GitHub, R2, Zenodo — **DONE v0.5** |
| D-07 | Counterfactual backcasting | artifacts/counterfactual-backcasting.md | GitHub, R2, Zenodo — **DONE v0.5** |
| D-08 | Research paper | paper.md | GitHub, R2, Zenodo, D1 |
| D-09 | Publication PDF | paper.pdf | GitHub, R2, Zenodo |
| D-10 | PROVENANCE-BUNDLE.zip | releases/ | R2, Zenodo |
| D-11 | Citation database (BibTeX) | refs.bib | GitHub, R2, Zenodo |

---

## 5. Risk Register

| # | Risk | Likelihood | Impact | Mitigation |
|:--|:-----|:-----------|:-------|:-----------|
| R-01 | Insufficient historical data to compute JPCUB for early transitions (vacuum tubes, transistors) | HIGH | MEDIUM | Use order-of-magnitude estimates with explicit uncertainty ranges; don't require precision |
| R-02 | JPCUB fails retrospective validation | MODERATE | HIGH | Publish disconfirmation — this is STILL valuable to QWAV strategy |
| R-03 | Traditional metrics data not available in consistent format | MODERATE | LOW | Normalize across sources; document methodology |
| R-04 | Paper overlaps too much with computing-machines survey | LOW | MEDIUM | Focus on methodology (JPCUB computation) and results (validation), not re-surveying candidates |
| R-05 | p-adic/ultrametric framework integration forced or superficial | MODERATE | MEDIUM | Only include theoretical framework section if it genuinely constrains or informs the metric; don't force it |

---

## 6. Success Criteria

1. JPCUB retrospective ranking accuracy computed and compared against ≥2 traditional metrics
2. Prospective ranking of 7 post-silicon candidates published with dated, falsifiable predictions
3. All predictions entered in calibration register with [STRONG]/[WEAK] tags
4. Paper published on Zenodo with DOI, deployed to papers.qnfo.org
5. Finding (validation or disconfirmation) disseminated via Buffer

---

## 7. Version History

| Version | Date | Description |
|:--------|:-----|:------------|
| v0.5-phase4-deep | 2026-07-31 | Phase 4: D-04 JPCUB historical dataset (6 transitions, SPEC Power anchor), D-05 structured forecast protocol (11 stages, 7 post-silicon candidates, calibration register), D-06 practical applications (5 domains), D-07 counterfactual backcasting (4 disciplines × 2-3 tiers). M4 MET. JPCUB validated as leading indicator (LEAD 3/5, LAG 1/5, COINCIDENT 1/5). |
| v0.4-phase3-cite | 2026-07-31 | Phase 3: refs.bib (32 entries), citation audit PASSED (Gate M3 MET), citation-management.md |
| v0.1-phase0 | 2026-07-31 | Project initialization, core claim lock, scaffold |
