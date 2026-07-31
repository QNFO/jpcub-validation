# Practical Applications Extension: JPCUB Predictive Validation

**Date:** 2026-07-31
**Project:** jpcub-validation (QNFO/jpcub-validation)
**Phase:** 4 — Deep Research
**Artifact:** D-06 — practical-applications-extension.md (Stage 9)
**Genre:** C (Internal/Operations)

**Purpose:** Ground every forecast candidate in concrete operational domains, answering:
"If this candidate is correct, what does it enable that we cannot do today?"
This prevents forecasts from remaining purely theoretical.

---

## Domain Mapping

For each top-ranked forecast candidate (from D-05 Stage 1), we map onto
5 application domains, articulate operational signatures, generate falsifiable
claims, and register domain-specific calibration entries.

### Candidate-Domain Matrix

| Candidate | Computation | AI/ML | Measurement/Metrology | Energy/Climate | Communication |
|:----------|:-----------|:------|:----------------------|:---------------|:--------------|
| C1 (Chiplet) | ★★★ | ★★★ | ★★ | ★★ | ★★ |
| C2 (In-Memory) | ★ | ★★★ | ★ | ★ | ★ |
| C3 (Neuromorphic) | ★ | ★★★ | ★ | ★★ | ★ |
| C4 (CMOS) | ★★★ | ★★ | ★★★ | ★★ | ★★★ |
| C5 (Spintronic) | ★ | ★ | ★ | ★★ | ★ |
| C6 (Cognitive) | ★ | ★★ | — | — | — |
| C7 (Photonic) | ★ | ★ | — | — | ★★★ |

★★★ = transformative; ★★ = significant; ★ = incremental; — = not applicable

---

## Domain 1: AI/ML Computing

### C1: Chiplet → AI Training Efficiency

**Operational Signature:** AI training clusters transition from monolithic GPU/TPU
nodes to chiplet-disaggregated systems where memory, compute, and interconnect are
separate chiplets optimized independently. This reduces the JPCUB penalty of moving
data between memory and compute by 5-20× through tighter integration.

**Current practice:** GPU training node: HBM stacks adjacent to GPU die, connected
through silicon interposer (NVIDIA H100/B200). Each memory access traverses the
interposer, consuming ~3-5 pJ/bit. For a 1TB model training run with ~10^18 memory
accesses, this is ~3-5 MJ of memory-access energy alone.

**JPCUB-enabled practice:** Chiplet disaggregation places memory chiplets at the
optimal physical location per compute chiplet, using hybrid bonding at <1μm pitch.
Memory-access energy drops to ~0.1-0.5 pJ/bit. For the same training run: ~0.1-0.5 MJ.

**Falsifiable Claim:** By 2029, a chiplet-based AI training system (≥4 chiplets
per package, hybrid bonding) will demonstrate ≥3× better JPCUB (J/training-token)
than the best monolithic design at the same process node.

**Calibration Register Entry:**
```
[CHECK: 2029] A chiplet-based AI training system demonstrates ≥3× JPCUB improvement
over monolithic at iso-node.
Likelihood-Anchor: Reference Class (AMD EPYC chiplet: ~2× perf/W improvement over
equivalent monolithic at iso-node; AI workloads benefit more from memory bandwidth)
Strength: [STRONG]
Status: [PENDING]
```

### C2: In-Memory → Inference at Scale

**Operational Signature:** AI inference moves from "load weights from DRAM → compute
in ALU → write back to DRAM" to "weights reside in analog memory arrays; computation
occurs in situ via Kirchhoff's law." This eliminates the von Neumann bottleneck for
inference, reducing JPCUB by 10-100× for matrix-dominated workloads.

**Current practice:** LLM inference on H100: ~0.5 J/token (TokenPowerBench data,
C5/Niu et al.). For ChatGPT-scale serving (~10^9 tokens/day): ~500 MJ/day, ~50 MW
continuous power.

**JPCUB-enabled practice:** In-memory inference: ~0.005-0.05 J/token. Same serving
load: ~5-50 MJ/day, ~0.5-5 MW. The difference is the economic viability of deploying
frontier models at global scale.

**Falsifiable Claim:** By 2030, an in-memory compute accelerator (ReRAM, MRAM, or
flash-based) will demonstrate ≥10× better J/token than the best digital accelerator
(GPU or NPU) on a standard LLM inference benchmark (≥7B parameters), with output
quality within 1% of floating-point baseline.

**Calibration Register Entry:**
```
[CHECK: 2030] In-memory compute achieves ≥10× J/token improvement over best digital
accelerator on standard LLM inference benchmark at iso-quality.
Likelihood-Anchor: Reference Class (analog AI accelerators: Mythic demonstrated ~5×
efficiency for vision models; LLM inference is more memory-bound → larger gap)
Strength: [WEAK] — anchored to single-vendor demonstration, not published study
Status: [PENDING]
```

### C3: Neuromorphic → Always-On Edge Perception

**Operational Signature:** Event cameras and neuromorphic processors pair to create
perception systems that consume microwatts when the scene is static and scale power
linearly with scene activity — unlike frame-based cameras that consume constant power
regardless of content. JPCUB improvement is not in per-operation energy but in
ELIMINATING unnecessary operations.

**Current practice:** Always-on vision system (camera + inference chip): ~100 mW-1W
continuous. Battery life: hours to days.

**JPCUB-enabled practice:** Neuromorphic event-based vision: ~10-100 μW idle,
~1-10 mW active. Battery life: months to years on the same battery.

**Falsifiable Claim:** By 2030, a neuromorphic event-based vision system (camera +
processor) will demonstrate <1 mW average power on a standard always-on vision
benchmark (e.g., DVS Gesture or N-Caltech101) with >90% accuracy, representing
≥100× JPCUB improvement over a frame-based system at iso-accuracy.

**Calibration Register Entry:**
```
[CHECK: 2030] Neuromorphic event-based vision achieves <1 mW average at >90% accuracy
on standard benchmark.
Likelihood-Anchor: Reference Class (Loihi 2 demonstrated ~100× energy improvement over
GPU for spiking workloads; edge deployment adds system-level overhead)
Strength: [STRONG]
Status: [PENDING]
```

---

## Domain 2: High-Performance Computing (HPC)

### C1 + C4: JPCUB-Driven Procurement

**Operational Signature:** HPC procurement transitions from FLOPS/$ as the primary
selection criterion to JPCUB (FLOPS/Watt extended to useful-science/Watt). This
changes which architectures win exascale contracts — favoring efficiency-optimized
designs over peak-performance-optimized designs.

**Current practice:** TOP500 ranks by FLOPS; Green500 ranks by FLOPS/Watt. These are
separate lists reviewed by separate communities. Procurement RFPs emphasize peak FLOPS.

**JPCUB-enabled practice:** JPCUB merges the two: ranking by useful-scientific-output
per Joule. A system that achieves 80% of peak FLOPS at 40% of the power wins over
a system at 100% peak FLOPS at 100% power.

**Falsifiable Claim:** By 2028, at least one major HPC procurement (DOE exascale
follow-on, EuroHPC, or equivalent) will include an energy-efficiency metric weighted
at ≥30% of the evaluation criteria, and at least one vendor will publish JPCUB-like
per-workload efficiency data in their proposal.

**Calibration Register Entry:**
```
[CHECK: 2028] Major HPC procurement uses energy efficiency ≥30% weighting with
published per-workload JPCUB-like data.
Likelihood-Anchor: Reference Class (Green500 adoption trajectory; DOE already includes
energy efficiency in procurement; the 30% threshold is a judgment, not a known prior)
Strength: [WEAK]
Status: [PENDING]
```

---

## Domain 3: Energy & Climate

### All Candidates: Computing's Carbon Footprint

**Operational Signature:** JPCUB becomes a carbon-accounting metric. Data center
operators report not just PUE (Power Usage Effectiveness) but JPCUB per workload
class, enabling carbon-conscious workload scheduling: route inference to the
most JPCUB-efficient available hardware.

**Current practice:** Data centers report PUE and total energy. Carbon accounting
uses grid-average emission factors. No per-workload efficiency metric exists.

**JPCUB-enabled practice:** JPCUB-per-workload enables carbon-aware scheduling:
- High-JPCUB workloads (training) → scheduled when grid carbon intensity is low
- Low-JPCUB workloads (inference on efficient hardware) → any time
- Carbon cost per inference becomes a reportable metric

**Falsifiable Claim:** By 2030, at least one major cloud provider (AWS, Azure, GCP)
will publish per-workload energy efficiency metrics (J/request or J/token equivalent)
for AI inference services, enabling customers to compare the carbon cost of different
model-serving options.

**Calibration Register Entry:**
```
[CHECK: 2030] Major cloud provider publishes per-workload AI inference energy metrics.
Likelihood-Anchor: Empirical Base Rate (cloud carbon reporting adoption: AWS Carbon
Footprint Tool 2022, Azure Emissions Dashboard 2020, GCP Carbon Footprint 2021;
per-workload breakdown is the next logical step)
Strength: [STRONG]
Status: [PENDING]
```

---

## Domain 4: Mobile & Consumer Electronics

### C1 (Chiplet): Battery Life Extension

**Operational Signature:** Premium smartphone SoCs transition from monolithic dies
to chiplet-based designs (following Apple's UltraFusion model from the M-series Mac
chips). Memory chiplets placed closer to compute chiplets reduce DRAM-access energy,
which dominates mobile power budgets during active use.

**Current practice:** Smartphone SoC: monolithic die with LPDDR packaged separately
(PoP). DRAM access energy: ~20-50 pJ/bit. For video playback: ~500 mW DRAM power.

**JPCUB-enabled practice:** Chiplet-based SoC with memory on interposer or hybrid
bonded. DRAM access energy: ~2-5 pJ/bit. Video playback DRAM power: ~50-100 mW.
Battery life extension: ~30-60 minutes for video playback on a typical 15 Wh battery.

**Falsifiable Claim:** By 2028, ≥20% of premium smartphone SoCs (by unit volume)
will use chiplet-based packaging (interposer or hybrid bonding), and the chiplet
designs will demonstrate ≥15% better energy efficiency (J/benchmark-score) than
contemporary monolithic designs at iso-process-node.

**Calibration Register Entry:**
```
[CHECK: 2028] ≥20% premium smartphone SoCs use chiplet packaging with ≥15% efficiency gain.
Likelihood-Anchor: Reference Class (Apple UltraFusion M1 Ultra 2022; smartphone adoption
typically lags laptop/desktop by 2-3yr for packaging innovations)
Strength: [STRONG]
Status: [PENDING]
```

---

## Domain 5: Measurement & Metrology

### Cross-Cutting: JPCUB Benchmarking Infrastructure

**Operational Signature:** JPCUB measurement infrastructure transitions from
paper definition to deployed standard. The 6 energy components and 5-phase
protocol from the JPCUB definition paper (C1/QNFO internal, DOI 10.5281/zenodo.21637028)
are implemented in reference hardware and software, enabling cross-platform,
cross-workload JPCUB comparison.

**Current practice:** No cross-domain energy metric exists. SPEC Power covers
server CPU efficiency. ML.ENERGY covers AI training. Green500 covers HPC FLOPS/Watt.
These are incompatible — a GPU's SPEC Power score cannot be compared to its ML.ENERGY
score in a principled way.

**JPCUB-enabled practice:** JPCUB reference implementation normalizes across:
- SPEC Power (server CPU)
- ML.ENERGY (AI training)
- TokenPowerBench (AI inference)
- Green500 (HPC)
- Custom benchmarks for neuromorphic, in-memory, and spintronic

**Falsifiable Claim:** By 2029, a JPCUB reference implementation (open-source
software + reference hardware configuration) will exist that computes comparable
JPCUB scores for at least 3 different computing paradigms (e.g., CPU, GPU, and
in-memory accelerator) on at least 3 different workload classes, with published
cross-paradigm comparison tables.

**Calibration Register Entry:**
```
[CHECK: 2029] Open-source JPCUB reference implementation computes cross-paradigm
scores for ≥3 paradigms × ≥3 workloads.
Likelihood-Anchor: Reference Class (SPEC benchmark development timeline: ~3-5yr
from committee formation to first release; JPCUB is simpler — single metric, not
a suite of benchmarks)
Strength: [WEAK] — depends on community adoption, not just technical feasibility
Status: [PENDING]
```

---

## Cross-Domain Consilience Cross-References

From the Phase 1 Consilience Gate (`artifacts/consilience-gate.md`):

| Domain Translation | Practical Application Enrichment |
|:-------------------|:---------------------------------|
| **Physics:** JPCUB ↔ thermodynamic efficiency (Carnot analog for computation) | The JPCUB/thermodynamics mapping applies directly to Domain 3 (Energy/Climate): data center efficiency is a heat-engine problem, and JPCUB is the computing analog of thermal efficiency |
| **CS:** JPCUB ↔ algorithmic complexity (energy complexity replaces time complexity) | Domain 2 (HPC): JPCUB-driven procurement is effectively selecting for energy-complexity-optimal algorithms, not just time-complexity-optimal ones |
| **Economics:** JPCUB ↔ productivity (GDP/Joule for computation) | Domain 1 (AI/ML): The economic viability of frontier AI deployment depends on JPCUB crossing below the revenue-per-token threshold |
| **Biology:** JPCUB ↔ metabolic efficiency (brain ~20W for ~10^16 ops/s = ~2 × 10^-15 J/op) | Domain 1 (Neuromorphic): The brain is the existence proof that JPCUB 10,000× better than current silicon is physically possible |
| **Sociology:** JPCUB ↔ institutional inertia (benchmarks shape behavior) | Domain 5 (Measurement): The biggest barrier to JPCUB adoption is not technical — it is incumbent vendors' investment in existing benchmarks (SPEC, MLPerf) and the institutional reluctance to adopt a single cross-domain metric |

---

## Additional Calibration Register Entries

```
[CHECK: 2028] At least one peer-reviewed paper will compare JPCUB across ≥2
computing paradigms (e.g., CPU vs. GPU vs. NPU) using a published methodology.
Likelihood-Anchor: Empirical Base Rate (new metric adoption in CS: ~3-5yr from
proposal to first independent validation paper; JPCUB was proposed 2026)
Strength: [STRONG]
Status: [PENDING]

[CHECK: 2030] JPCUB or a JPCUB-derived metric will appear in ≥1 vendor's public
datasheet or marketing material (not just research paper).
Likelihood-Anchor: Reference Class (FLOPS/Watt appeared in vendor datasheets ~5yr
after Green500 launch; MLPerf scores appeared ~2yr after benchmark launch)
Strength: [WEAK]
Status: [PENDING]

[CHECK: 2032] If C2 (In-Memory) is commercially deployed for AI inference at scale,
the system-level JPCUB improvement over contemporary digital accelerators will be
≤30× (not the 100× theoretical maximum), because system overheads (data marshaling,
analog-digital conversion, error correction) consume 50-70% of the theoretical gain.
Likelihood-Anchor: Reference Class (GPU→TPU theoretical FLOPS/Watt was ~100×;
achieved system-level was ~30×; overhead erosion is a well-documented pattern)
Strength: [STRONG]
Status: [PENDING]
```

---

*End of Practical Applications Extension — D-06*
