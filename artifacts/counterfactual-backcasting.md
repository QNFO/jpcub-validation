# Counterfactual Backcasting: JPCUB Predictive Validation

**Date:** 2026-07-31
**Project:** jpcub-validation (QNFO/jpcub-validation)
**Phase:** 4 — Deep Research
**Artifact:** D-07 — counterfactual-backcasting.md (Stage 10)
**Genre:** C (Internal/Operations)

**Purpose:** Stress-test the JPCUB forecast by asking "what would have to be true for
this to already exist?" This reveals hidden timeline assumptions, identifies actionable
near-term research forks, and generates a second independent set of falsifiable
predictions.

---

## Target Discipline Identification

The JPCUB forecast depends on four core disciplines:

| Discipline | Current State (2026) | Target State (JPCUB-optimal) |
|:-----------|:---------------------|:-----------------------------|
| **Computer Architecture** | von Neumann dominant; SIMD and dataflow as accelerators; heterogeneous integration emerging (Apple, AMD) | Heterogeneous integration with in-memory, neuromorphic, and chiplets as first-class paradigms; JPCUB as primary design metric |
| **Semiconductor Device Physics** | CMOS scaling approaching atomic limits (GAA at 3nm, CFET in R&D); post-silicon logic devices in early research (spintronic, photonic) | Room-temperature cascaded spin logic; sub-fJ photonic interconnects; production-grade memristors with logic endurance |
| **Energy-Efficiency Metrology** | Fragmented: SPEC Power (CPU), ML.ENERGY (AI training), Green500 (HPC FLOPS/Watt), TokenPowerBench (LLM inference) — no cross-domain metric | JPCUB as THE unified standard: cross-paradigm, cross-workload, cross-domain energy-per-useful-computation metric with open-source reference implementation |
| **Materials Science & Fabrication** | Silicon dominant; III-V and 2D materials in research; emerging memories (MRAM, ReRAM) in niche production | Production-grade memristors with logic endurance; integrated photonic circuits on CMOS; foundry ecosystem for post-silicon devices |

---

## Tiered Fork Classification

| Tier | Description | Temporal Distance | Example Fork Point |
|:-----|:------------|:------------------|:-------------------|
| **Tier 1** | Single research program reprioritized ~20 years ago | 2000s fork → impacts by 2020s | DARPA funds chiplet standardization in 2005 instead of 2015 |
| **Tier 2** | Coordinated advancement across 2-3 disciplines | 1960s fork → impacts by 2000s | Carver Mead's neuromorphic VLSI receives sustained, multi-decade funding |
| **Tier 3** | Incompatible mathematical foundations required | 1900s fork → impacts by 1980s | Reversible computing (Bennett 1973) receives the funding that went to CMOS scaling |
| **Tier 4** | The axioms themselves differ | Indefinite | Information is not physical (Landauer's principle is false); computation can be zero-energy |

---

## Counterfactual Technology Stacks

### Discipline 1: Computer Architecture

#### Tier 1 Fork: DARPA Chiplet Program (2005)

**Enabling Fork:** In 2005, DARPA launches a $500M program for "Disaggregated Computing
Architectures" — 10 years before the actual DARPA CHIPS program (2015). This program
funds:
- Silicon interposer technology (TSV, microbumps) at commercial scale
- Chiplet interconnect standards (precursor to UCIe)
- Multi-vendor chiplet ecosystem (memory chiplets from Micron, compute chiplets from
  Intel/AMD, I/O chiplets from Broadcom — all interoperable by 2012)

**Counterfactual Technology (2026):**
- **Chiplet-native server CPUs** shipping since 2012 (AMD EPYC arrives 5 years earlier)
- **Apple M-series** uses chiplets from M1 (2020) instead of M1 Ultra (2022)
- **Smartphone SoCs** with memory-on-interposer since 2018 (Samsung, Qualcomm)
- **JPCUB reduction:** chiplet-based designs achieve ~10× system-level JPCUB improvement
  over monolithic designs by 2020 (vs. ~3× in our timeline)
- **Calibration Prediction:** If this fork had occurred, we would observe: (a) chiplet-based
  CPUs at ≥80% data center unit share by 2020 (vs. ~25% actual); (b) ≥3 major chiplet
  interconnect standards by 2015 (vs. UCIe 1.0 in 2022); (c) interposer cost <$1/mm² by
  2018 (vs. ~$5/mm² actual)

#### Tier 2 Fork: Neuromorphic VLSI Program (1989)

**Enabling Fork:** Carver Mead's "Analog VLSI and Neural Systems" (1989) receives
sustained DARPA/NSF funding at $100M/year for 20 years, rather than being treated
as an academic curiosity. Intel's neuromorphic program starts in 1995 instead of 2015.

**Counterfactual Technology (2026):**
- **Neuromorphic co-processors** in every smartphone by 2010, handling always-on
  audio and basic vision at <1 mW
- **Loihi-equivalent** chips shipping in 2005 (vs. Loihi 1 in 2018)
- **Spike-based programming model** standardized and taught in undergraduate CS
  curricula by 2010
- **JPCUB:** Neuromorphic inference at ~10^-15 J/op (vs. ~10^-13 J/op on TPU v4)
  for spike-domain workloads, approaching the brain's ~2×10^-15 J/op efficiency

#### Tier 3 Fork: Reversible Computing Program (1973)

**Enabling Fork:** Bennett (1973) demonstrated that computation can be thermodynamically
reversible. In this fork, the semiconductor industry pursues reversible/adiabatic
CMOS instead of conventional voltage-scaled CMOS, starting with Mead & Conway (1980)
incorporating adiabatic design principles.

**Counterfactual Technology (2026):**
- **Adiabatic microprocessors** operating at ~10^-18 J/op at 1 GHz (vs. ~10^-12 J/op
  conventional CMOS at equivalent node)
- **Landauer limit approached** to within ~100× (vs. ~10^6× in our timeline)
- **Energy recovery circuits** standard in all digital logic since 2000
- **Calibration Prediction:** If this fork had occurred, we would observe: (a) CPU
  power decreasing with each process generation (not increasing); (b) data center
  PUE below 1.0 (net energy recovery); (c) battery-powered devices with months-long
  active use

---

### Discipline 2: Semiconductor Device Physics

#### Tier 1 Fork: Spintronic Logic Program (2002)

**Enabling Fork:** DARPA/SRC invest $500M in spintronic LOGIC (not just MRAM) starting
in 2002, following the discovery of spin-transfer torque (1996). The program targets
cascaded spin logic with gain > 1 at room temperature, not just memory.

**Counterfactual Technology (2026):**
- **SOT-MRAM logic gates** demonstrated at 10 nm scale, gain > 2, switching energy
  ~1 fJ, by 2015 (vs. SOT-MRAM still in R&D for memory only in 2026)
- **Spin-based FPGA** shipping by 2020 (reconfigurable spin logic fabric)
- **Non-volatile processors** with zero standby power for IoT since 2018
- **JPCUB:** Spin logic ~10^-17 J/op (vs. CMOS ~10^-14 J/op at equivalent density)

#### Tier 2 Fork: Josephson Junction Logic Program (1970s)

**Enabling Fork:** IBM's Josephson junction program (1970-1983), which was canceled
after failing to achieve competitive density, instead pivots to hybrid
superconducting-semiconductor integration. The program solves the cryogenic
interface problem (room-temp CMOS ↔ 4K superconducting logic) by 1985.

**Counterfactual Technology (2026):**
- **Superconducting co-processors** for HPC since 1995: cryogenic RSFQ logic at
  100 GHz, ~10^-19 J/op (vs. CMOS ~10^-10 J/op at the time)
- **Cryogenic data centers** operating at 4K with net energy savings (cooling
  cost < logic energy savings) by 2005
- **Calibration Prediction:** If this fork had occurred, we would observe:
  (a) cryogenic computing modules in TOP500 systems since 2000; (b) RSFQ logic
  as standard option in HPC procurement by 2010; (c) sub-Kelvin refrigeration
  as a standard data center infrastructure component

---

### Discipline 3: Energy-Efficiency Metrology

#### Tier 1 Fork: SPEC Power Extended to Accelerators (2008)

**Enabling Fork:** The SPEC Power committee, after releasing SPECpower_ssj2008 (the
first industry-standard server energy benchmark), immediately extends the methodology
to GPUs and accelerators in 2008, rather than waiting until 2023 (SPEC CPU 2017 with
power measurement). NVIDIA and AMD participate from the start.

**Counterfactual Technology (2026):**
- **Cross-platform energy benchmarks** with 15 years of GPU/accelerator data (2008-2023)
- **GPU FLOPS/Watt trajectory** quantified in a single, comparable dataset from
  Tesla C1060 (2008) through H100 (2022) — enabling precise Koomey's law extension
  to accelerators
- **JPCUB retrospectives** with 3× the data density for the GPU→AI accelerator
  transition (T5-T6)
- **Calibration Prediction:** If this fork had occurred, we would observe: (a) the
  GPU→AI accelerator JPCUB LEAD signal quantified with ±1 year precision (vs. ±5yr
  in our analysis); (b) data center procurement RFPs requiring SPEC Power-accelerator
  scores by 2015 (vs. still not required in 2026)

#### Tier 2 Fork: Koomey's Law Data from 1985

**Enabling Fork:** Jonathan Koomey begins collecting energy-efficiency data for
computing devices in 1985 (when he starts his PhD at Berkeley), rather than
publishing the retrospective in 2009 covering data from 1946-2009. This creates
a real-time tracking dataset rather than a retrospective.

**Counterfactual Technology (2026):**
- **40-year energy-efficiency trend data** (1985-2025) with annual resolution,
  covering every major computing transition
- **Real-time Koomey's law monitoring** enabling early detection of the Dennard
  scaling breakdown (detected in ~2003 vs. widely acknowledged ~2006-2007)
- **JPCUB historical dataset** with ~10× the temporal resolution for transitions T3-T5

---

### Discipline 4: Materials Science & Fabrication

#### Tier 1 Fork: Memristor Consortium (2008)

**Enabling Fork:** Following HP Labs' announcement of the memristor (2008, Nature),
a foundry-neutral industry consortium (modeled on the Semiconductor Research
Corporation) forms with $2B funding over 10 years to solve memristor endurance
and variability. TSMC, Samsung, Intel, and GlobalFoundries all participate.

**Counterfactual Technology (2026):**
- **Logic-grade ReRAM** (endurance >10^15 cycles, variability <1%) achieved by 2018
  (vs. still not achieved in 2026)
- **ReRAM as universal memory** (replacing DRAM, SRAM, and Flash) since 2020
- **In-memory computing** shipping in volume since 2020 (vs. Samsung HBM-PIM niche
  production in 2026)
- **JPCUB:** In-memory compute at ~10^-16 J/op (vs. ~10^-12 J/op for digital accelerators)
- **Calibration Prediction:** If this fork had occurred, we would observe:
  (a) ReRAM-based main memory in ≥30% of new server shipments by 2022;
  (b) In-memory compute accelerators as standard option in cloud AI by 2023;
  (c) The JPCUB gap between in-memory and digital accelerators documented at
  100-1000× by 2020

#### Tier 2 Fork: GaAs-on-Silicon Heteroepitaxy (1985)

**Enabling Fork:** The lattice mismatch between GaAs and silicon is solved in 1985
(vs. still an active research problem in 2026). III-V compound semiconductors
integrate monolithically with silicon CMOS, enabling:
- Optical sources (lasers, LEDs) directly on silicon
- High-electron-mobility transistors (HEMTs) alongside CMOS
- Ultra-low-voltage logic (0.3V supply) using III-V channels

**Counterfactual Technology (2026):**
- **Integrated photonics** on every CPU since 2000: on-chip optical interconnects,
  eliminating the O/E conversion penalty at the chip edge
- **III-V logic** at 0.3V supply, ~10^-17 J/op since 2005 (vs. CMOS at ~10^-12 J/op)
- **Monolithic optical-electronic chips** for data centers by 1995
- **Calibration Prediction:** If this fork had occurred, we would observe:
  (a) Optical interconnects between CPU cores by 2000; (b) III-V logic in
  battery-powered devices by 2005 with 10× battery life vs. silicon CMOS;
  (c) the semiconductor industry dominated by GaAs-on-Si, with pure silicon
  relegated to low-cost applications

---

## Summary Table: Counterfactual Technology Stacks

| Discipline × Tier | Fork Point | Counterfactual Technology | JPCUB (J/op) | Timeline Shift |
|:------------------|:-----------|:--------------------------|:-------------|:---------------|
| Architecture T1 | DARPA Chiplet 2005 | Chiplet-native CPUs | ~10^-12 (vs. ~5×10^-12) | Chiplet ecosystem 10yr ahead |
| Architecture T2 | Neuromorphic VLSI 1989 | Neuromorphic co-processors everywhere | ~10^-15 (spike domain) | Neuromorphic maturity by 2010 |
| Architecture T3 | Reversible Computing 1973 | Adiabatic microprocessors | ~10^-18 | Energy-recovering circuits standard since 2000 |
| Device Physics T1 | Spintronic Logic 2002 | SOT-MRAM logic gates | ~10^-17 | Spin FPGA by 2020 |
| Device Physics T2 | Josephson Logic 1970s | Cryogenic RSFQ co-processors | ~10^-19 | Cryogenic HPC since 2000 |
| Metrology T1 | SPEC Power Accelerator 2008 | Cross-platform energy benchmarks | — | GPU/accel benchmarks 15yr of data |
| Metrology T2 | Koomey 1985 | Real-time efficiency tracking | — | Dennard breakdown detected in real-time |
| Materials T1 | Memristor Consortium 2008 | Logic-grade ReRAM, in-memory compute | ~10^-16 | In-memory shipping since 2020 |
| Materials T2 | GaAs-on-Si 1985 | III-V logic + integrated photonics | ~10^-17 | Optical interconnects, 0.3V logic by 2000 |

---

## Backcast Calibration Register

```
[CHECK: 2028] The "Memristor Consortium" Tier 1 fork becomes ACTIVE if ≥3 major
foundries (TSMC, Samsung, Intel) announce ReRAM-based logic process nodes by 2028.
This would validate the fork's premise that foundry coordination accelerates
post-silicon device maturation.
Likelihood-Anchor: Reference Class (MRAM ecosystem: Everspin, TSMC, Samsung, GlobalFoundries
all have MRAM offerings — a de-facto consortium without formal structure; formal
consortium accelerates timeline by ~5yr)
Strength: [WEAK]
Status: [PENDING]

[CHECK: 2030] If SPEC Power or equivalent has NOT been extended to chiplet-based
systems by 2030 (the Tier 1 Metrology fork opportunity was missed), the JPCUB
retrospective for chiplet transition (T7 in future analysis) will have ≤3 years
of benchmark data — similar to the GPU transition data gap.
Likelihood-Anchor: Empirical Base Rate (SPEC benchmark development cycles: 3-7yr)
Strength: [STRONG]
Status: [PENDING]

[CHECK: 2035] The Tier 3 Architecture fork (reversible computing) is the only path
to sub-10^-18 J/op. If no reversible computing demonstration exceeds 10^6
operations at >1 MHz by 2035, the Landauer limit will remain >4 orders of magnitude
away from practical engineering — but this does NOT mean "JPCUB has room" — the
practical limits (thermal, power delivery) are hit long before Landauer.
Likelihood-Anchor: Known Prior (Landauer limit × practical engineering overhead)
Strength: [STRONG]
Status: [PENDING]
```

---

## Near-Term Fork Recommendations (Future Work)

These Tier 1 forks are actionable within 1-3 years and should appear in the
paper's Future Work section:

1. **JPCUB Benchmark Standardization NOW.** The Metrology Tier 1 fork (SPEC Power
   extended to accelerators) is achievable within 2 years. The retrospective analysis
   (D-04) shows that benchmarking infrastructure consistently lags paradigm adoption
   by 5-10 years. By building JPCUB benchmarks for chiplets and in-memory compute
   BEFORE these paradigms reach volume deployment, we can reduce that lag to near
   zero — enabling JPCUB to function as the leading indicator it theoretically can be.

2. **Memristor Reliability Consortium.** The single highest-leverage Tier 1 fork is
   a foundry-neutral consortium targeting memristor endurance. Assumption A6 (Stage 2)
   is the key fragility in the forecast — resolving it accelerates the in-memory
   computing timeline by 5-10 years.

3. **Chiplet Interconnect Energy Measurement Standard.** The chiplet ecosystem needs
   a standard method for measuring interconnect energy (pJ/bit at specific bandwidth
   and distance). Current chiplet interconnect metrics focus on bandwidth density
   (GB/s/mm), not energy. An energy-focused metric is a prerequisite for JPCUB-based
   chiplet comparison.

4. **Koomey's Law Extension to Post-Silicon.** The Koomey's law dataset (computations
   per kWh, doubling every ~1.57 years historically, now ~2.6 years) should be extended
   to include post-silicon devices as they become measurable. Without this extension,
   JPCUB's cross-paradigm comparison will lack the temporal baseline that made Koomey's
   law a compelling narrative.

---

*End of Counterfactual Backcasting — D-07*
