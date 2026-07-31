# Phase 4 — Structured Forecast Protocol v2.27 (Scope-Scaled)
## jpcub-validation

**Date:** 2026-07-31 | **Status:** Phase 4 COMPLETE (lightweight — single-result validation project)
**Scope note:** JPCUB is a predictive-validation project, not a paradigm forecast. Phase 4 runs scope-scaled: enumerated assumptions, uncertainty ranges, sensitivity check, one calibration prediction, and light Stages 9-10.

---

## 1. Core Claim

The JPCUB metric (Joules Per Computational Unit) provides a hardware-independent, workload-normalized measure of computing efficiency. Validating it requires demonstrating that JPCUB rankings of computing hardware are robust under workload perturbation, architecture variation, and temporal drift.

## 2. Enabling Assumptions

| # | Assumption | Confidence | Risk if False |
|:--|:-----------|:-----------|:--------------|
| A1 | Workload normalization across architectures is well-defined (a "computational unit" is comparable between CPU, GPU, TPU, FPGA) | MODERATE [speculative] | JPCUB becomes architecture-specific, not universal — still useful but scope shrinks |
| A2 | Energy measurement is accurate and comparable across hardware vendors (same metrology standard) | HIGH [mainstream interpretation] | JPCUB rankings are noisy; requires metrology calibration before validation |
| A3 | JPCUB rankings are stable over time (a hardware's efficiency rank doesn't oscillate week-to-week) | MODERATE-HIGH [speculative] | JPCUB is a snapshot metric, not a persistent ranking — limits enterprise procurement use |
| A4 | The "Joules" metric can separate compute-energy from infrastructure-energy (cooling, power supply losses) | MODERATE [debated] | JPCUB may conflate datacenter efficiency with compute efficiency; needs PUE-normalized variant |
| A5 | Open-source hardware benchmarks exist for enough platforms to validate JPCUB empirically | HIGH [mainstream interpretation] | Validation limited to platforms with public benchmark data; some architectures untestable |

## 3. Qualitative Ranking of Sub-Claims

| Rank | Sub-Claim | Assessment | Confidence |
|:----:|:----------|:-----------|:-----------|
| 1 | JPCUB ranks CPU architectures consistently | Highest-confidence — CPU benchmarks are mature, public data abundant | HIGH |
| 2 | JPCUB ranks GPU architectures consistently | Moderate — GPU efficiency varies more with workload type | MODERATE |
| 3 | JPCUB cross-ranks CPU vs GPU vs TPU | Most challenging — "computational unit" normalization is hardest here | LOW-MODERATE |

## 4. Judgment Sensitivity

- **Robust:** CPU-only JPCUB ranking holds under ALL perturbations (pessimistic workload, optimistic workload, halved-priors). Public benchmark data is sufficient.
- **Conditional:** Cross-architecture JPCUB ranking is conditional on workload normalization methodology (A1). If A1 fails, cross-architecture ranking is meaningless.
- **Fragile:** Temporal-stability claim (A3) is fragile — hardware firmware updates, driver optimizations, and thermal management policies change efficiency week-to-week. JPCUB should be reported with a timestamp and configuration hash.

## 5. Calibration Register

```
[CALIBRATION-REGISTER: JP-S5-001]
Check date: 2028-06-30
Prediction: JPCUB ranking of top 10 publicly available CPU SKUs (as of 2026 Q3)
  is stable (Spearman ρ > 0.85) when re-measured in 2028 Q2 using the same
  benchmark suite (SPEC CPU 2017) and the same workload mix.
Likelihood-Anchor: Reference Class (hardware benchmark stability — SPEC CPU
  rankings typically correlate ρ > 0.90 between generations for same workload)
Strength: STRONG
Status: PENDING

[CALIBRATION-REGISTER: JP-S5-002]
Check date: 2029-12-31
Prediction: JPCUB is cited in ≥2 enterprise hardware procurement RFPs (Request
  for Proposals) from Fortune 500 companies as an energy-efficiency metric.
Likelihood-Anchor: Calibrated Subjective
Strength: WEAK
Status: PENDING
```

---

## 6. Stage 9: Practical Applications Extension (Scope-Scaled)

### Application Domains

| Domain | Operational Signature | Falsifiable Claim | Horizon |
|:-------|:----------------------|:------------------|:--------|
| **Enterprise Procurement** | IT departments compare cloud/hardware vendors on JPCUB alongside TCO. JPCUB becomes the ENERGY dimension of procurement. | JPCUB cited in ≥2 Fortune 500 RFPs by 2029 | 2028-2030 |
| **Cloud Pricing** | Cloud providers publish JPCUB scores alongside instance types. Customers select instances by JPCUB-aware auto-scaling: migrate workloads to instances with best JPCUB for the workload type. | AWS/GCP/Azure publish JPCUB scores for ≥50% of compute instance types by 2030 | 2028-2032 |
| **Green Computing Regulation** | Government energy-efficiency standards for data centers adopt JPCUB as a compliance metric. New data centers must report JPCUB per workload class. | EU Energy Efficiency Directive amendment references JPCUB by 2032 | 2030-2035 |
| **Hardware Design** | Chip architects use JPCUB regression testing: each microarchitecture change must not regress JPCUB by >5%. JPCUB becomes part of the chip design flow alongside PPA (Power-Performance-Area). | ≥1 major chip vendor (Intel, AMD, NVIDIA, ARM) publishes JPCUB regression data for ≥1 product generation by 2030 | 2028-2032 |

---

## 7. Stage 10: Counterfactual Backcasting (Scope-Scaled)

### Target Disciplines

| Discipline | Current State (2026) | Target State |
|:-----------|:---------------------|:-------------|
| **Computer Architecture Benchmarking** | Fragmented: dozens of benchmarks (SPEC, Geekbench, PassMark, etc.), no energy-normalized cross-architecture metric | JPCUB is the standard efficiency benchmark — cited alongside SPEC and Geekbench |
| **Green Computing / Sustainable IT** | PUE (Power Usage Effectiveness) is the dominant metric, but it measures infrastructure efficiency, not compute efficiency | JPCUB is the COMPUTE-efficiency complement to PUE's infrastructure-efficiency |
| **Enterprise IT Procurement** | TCO (Total Cost of Ownership) is the dominant metric; energy is lumped into "operational cost" without compute-normalization | JPCUB is a standard line item in TCO models — "energy per compute unit" alongside "$ per compute unit" |

### Tier 1 Fork (~20yr): Green500 Adopts JPCUB in 2010

**Fork:** The Green500 list (founded 2007 as the energy-efficiency counterpart to Top500) adopts a JPCUB-like compute-normalized efficiency metric in 2010 instead of the current MFLOPS/Watt metric (which favors architectures with high FLOP counts regardless of actual workload throughput).

**Counterfactual (2026):** 15 years of Green500 data normalized by actual computational work, not theoretical peak FLOPs. Hardware vendors optimize for JPCUB, not MFLOPS/Watt. The "GPU vs CPU for HPC" debate would have been resolved on efficiency grounds by 2015. Energy-proportional computing would be a solved problem.

**Calibration claim:** If Green500 adopted JPCUB in 2010, HPC energy efficiency would have improved 2-3× faster than the observed trend (which was dominated by FLOP-optimized architectures that are energy-inefficient per actual workload).

### Tier 2 Fork (~60yr): Computing Efficiency as a Design Goal from the Start (1970s)

**Fork:** The microprocessor industry, from the Intel 4004 (1971) onward, treats energy-per-computation as a PRIMARY design metric alongside clock speed and transistor count. Moore's Law includes an "energy per operation" dimension alongside "transistors per area."

**Counterfactual (2026):** Every CPU datasheet includes a JPCUB score. Computing efficiency has improved at the same exponential rate as transistor density (rather than lagging by 10-15 years). The "dark silicon" problem (inability to power all transistors simultaneously) would have been solved architecturally in the 2000s, not patched with DVFS and power gating. Data center energy consumption would be 10-50× lower than current levels per unit of computation.

---

## 8. Recommendations

1. **Publish JPCUB validation dataset** — make all benchmark data, normalization methodology, and ranking code open-source (GitHub + Zenodo)
2. **Engage SPEC/GREEN500** — propose JPCUB as a supplementary metric
3. **Pre-register the cross-architecture validation** on OSF before collecting data
4. **Enterprise survey** — survey 50 IT procurement decision-makers on willingness to use JPCUB

## Version History

| Version | Date | Changes |
|:--------|:-----|:--------|
| v1.0 | 2026-07-31 | Initial scope-scaled Phase 4: assumptions, qualitative ranking, sensitivity, calibration register, light Stage 9 (4 domains), light Stage 10 (2 fork tiers) |
