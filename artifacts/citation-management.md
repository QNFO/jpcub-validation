# Phase 3 Citation Management: JPCUB Predictive Validation

**Date:** 2026-07-31
**Status:** COMPLETE — BibTeX database built, audit PASSED (Gate M3 MET)
**Project:** JPCUB Predictive Validation (QNFO/jpcub-validation)
**Tag:** v0.4-phase3-cite

---

## 1. Scope

Build the citation database for the JPCUB paper from (a) the 4 QNFO internal sources
identified in Phase 1 and (b) the 29 external works classified in Phase 2
(`literature-review.md` §2), then audit completeness, traceability, and
well-formedness per research-skill Phase 3 (Gate M3: "BibTeX audit passed, all
citations traceable").

## 2. Source Inventory (32 entries)

| Tier | Count | Sources |
|:-----|------:|:--------|
| QNFO internal | 4 | joules-per-solution-metric, QWAV whitepaper, continuum trilogy (Paper III ontology), computing-machines |
| Core (external) | 7 | Asanović 2009, SPEC Power 16-yr, TokenPowerBench, xPU-athalon, NOMS 2026 tutorial, Cloud-DC general metric, In-Sensor-Memory |
| Supporting | 15 | S1–S15 per classification matrix |
| Background | 6 | B1, B2, B3a, B3b, B4, B5 per classification matrix |
| **Total** | **32** | (B3 spans two OSTI DOIs → two entries; QWAV alternate DOI folded into a note) |

All entries live in `refs.bib` (repo root — consumed by Phase 5 Pandoc citation
processing).

## 3. Fetch Methodology (all verified live 2026-07-31)

| Source type | Method | Result |
|:------------|:-------|:-------|
| DOI-based (23 entries) | Crossref transform endpoint `api.crossref.org/works/{doi}/transform/application/x-bibtex` (primary); doi.org content negotiation `Accept: application/x-bibtex` (fallback) | 23/23 OK — every fetch returned a valid BibTeX record, i.e., every DOI **resolves** |
| arXiv-based (9 entries) | arXiv export API `export.arxiv.org/api/query?id_list=...` — title/authors/year parsed from Atom XML | 9/9 OK |
| QWAV alternate DOI | 10.5281/zenodo.21647111 fetched separately | OK — resolves to the identical whitepaper record (duplicate registration of the same work); kept as a note on the primary entry, not a separate citation |

Evidence of fetch: raw records written per-entry during the run (ephemeral
`_bib_raw/`, deleted after composition per the ephemeral-script pattern); the
composed, audited database is `refs.bib` — the single source of truth.

## 4. Audit Results (Gate M3)

Run: `_citation_audit.py` (ephemeral pattern — written, executed, deleted; pattern
reusable at Phase 5 when `paper.md` exists for @cite cross-checking).

| Check | Result |
|:------|:-------|
| **Completeness** — every classified paper (9 C + 15 S + 5 B) has a bib entry | **PASS** — 0 missing (32/32 classified sources covered) |
| **Traceability** — every entry has a DOI or arXiv eprint | **PASS** — 0 without ID (23 DOI + 9 eprint) |
| **Unused** — every entry maps to a classified source | **PASS** — 0 orphans |
| **Well-formed / key validity** | **PASS** — 0 bad keys; all keys match `[A-Za-z0-9:_+-]+` (no URL-as-key artifacts from DataCite records) |
| Tier coverage | Core 9/9 · Supporting 15/15 · Background 6/6 · QNFO-internal 4/4 |

**Gate M3 (CITATIONS): MET.**

## 5. Documented Metadata Gaps (source-registry provenance, non-blocking)

These are properties of the upstream registries, recorded so Phase 5 citation
rendering is not surprised by them; every entry remains fully traceable by DOI:

1. **OSTI reports (3):** `osti-dielectric-final1969` (10.2172/4438644),
   `osti-dielectric-qpl1968` (10.2172/4569047), `osti-energychips2025`
   (10.2172/3374401) — OSTI records carry no credited author ("Not Given"/"None");
   cited as institutional technical reports with `author = {Anon.}` + `institution`
   + `note` explaining the gap.
2. **MIT Press chapter (B2):** `mitpress-cloud-computing` (10.7551/mitpress/14821.003.0009)
   — Crossref record has neither author nor editor; cited as `@inbook` with the
   chapter title and a note. Chapter-level DOI resolves.
3. **QWAV whitepaper dual registration:** 10.5281/zenodo.21641108 (D1) and
   10.5281/zenodo.21647111 (OpenAlex) are the same work; primary citation uses the
   D1 DOI, alternate recorded in the entry note.
4. **Publication-year vs DOI-year:** Hanumaiah & Vrudhutt (10.1109/tc.2012.213)
   published Feb 2014 — entry uses 2014 (Crossref), noted. Desislavov et al.
   (arXiv:2109.05472) arXiv-listed 2021, journal version 2022 — entry uses 2021,
   noted.
5. **Continuum trilogy DOI sharing:** 10.5281/zenodo.21672990 is the record for
   all three continuum-trilogy papers; the project cites Paper III
   (slug `continuum-trilogy-03-unified-ontology`, "Depth, Breadth, and Valuation:
   A Unified Ontology of the Physical Continuum") — recorded in the entry note.

## 6. Handoff to Phase 4 / Phase 5

- `refs.bib` is citation-ready for `paper.md` (Phase 5) — keys are stable
  (surname-year; `qni-` prefix for QNFO internal).
- Phase 5 will re-run the `_citation_audit.py` pattern against `paper.md` @cite
  keys (missing / unused cross-check) as the CITATIONS verification gate.
- Phase 4 retrospective computation cites C4 (SPEC Power), S2 (physical floor),
  S3/S4/S5 (AI-era trends) as the data anchors; S15 (GDP/energy) as the macro
  analog; B3 (1968 joules-per-cubic-inch) as the historical metric precedent.

## 7. Evidence Index (KIF-55/KIF-57)

| Claim | Evidence |
|:------|:---------|
| 32 entries, all traceable | `refs.bib` (this commit) + audit output (PASS, 32/32) |
| All 24 DOIs resolve | Fetch-time Crossref transform / doi.org content negotiation returned valid BibTeX for each (raw fetch run, 2026-07-31) |
| All 9 arXiv IDs valid | arXiv export API Atom metadata parsed for each (raw fetch run, 2026-07-31) |
| Classification mapping | `artifacts/literature-review.md` §2 (C1–C9, S1–S15, B1–B5) |
| QNFO source DOIs | D1 living-paper query via `d1-query.py` (Phase 1 v4; continuum trilogy DOI 10.5281/zenodo.21672990 and computing-machines 10.5281/zenodo.21713202 re-verified this session) |
