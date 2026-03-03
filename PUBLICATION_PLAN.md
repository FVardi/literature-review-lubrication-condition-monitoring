# Publication Plan: LCM for Ball Bearings — Signal Processing Review
**Target:** Mechanical Systems and Signal Processing (MSSP)
**Author:** Frederik Appel Vardinghus-Nielsen
**Plan created:** March 2026

---

## 1. Strategic Positioning for MSSP

MSSP is a signal processing journal first, and a machinery diagnostics journal second. Reviewers will expect the *signal processing taxonomy* to be the intellectual spine of the paper — not a secondary sub-list under each sensing method. The key differentiator of this paper vs. all existing LCM reviews (Shang 2024, Wang 2024, Becker-Dombrowsky 2024, etc.) must be stated crisply: **this is the first review to systematically map signal processing methods across all sensing modalities for LCM, contrasting passive/non-invasive with active/invasive approaches from a signal processing perspective.**

This framing means the paper should answer three questions that no existing review does:
1. What signal processing operations transform raw sensor data into lubrication condition estimates, and what are the underlying assumptions of each?
2. How do sensing modality constraints (frequency range, physical origin of the signal) determine which SP methods are applicable?
3. Where are the SP bottlenecks — not sensor bottlenecks — that limit practical deployment of LCM?

---

## 2. Proposed Paper Architecture

The current structure needs to be reorganized. The recommended structure for MSSP submission:

### Proposed Section Order

| # | Section | Status | Priority |
|---|---------|--------|----------|
| — | **Abstract** (structured, ~250 words) | ❌ Missing | Critical |
| 1 | **Introduction** | 🔶 Draft (incomplete) | High |
| 2 | **Systematic Review Methodology** | 🔶 Thin stub | High |
| 3 | **Lubrication Physics & Signal Origins** | ✅ Solid foundation | Medium (expand) |
| 4 | **Sensing Methods Taxonomy** | 🔶 Draft | Medium |
| 5 | **Signal Processing Methods** (restructured as main section) | 🔶 Embedded/fragmented | **Critical** |
| 6 | **Comparative Analysis** | ❌ Missing | Critical |
| 7 | **Industrial Readiness & Applications** | 🔶 Scattered fragments | High |
| 8 | **Research Gaps & Future Directions** | ❌ Missing | Critical |
| 9 | **Conclusion** | ❌ Missing | Critical |
| — | References | ✅ bib.bib exists | Cleanup needed |

### File Restructuring Needed
Currently `invasive_active_methods.tex` and `non-invasive_passive_methods.tex` live outside the `sections/` folder and are called separately in `main.tex`. These should be merged into the `sensing_methods_and_empirical_studies.tex` file and the structure unified. A dedicated `sections/signal_processing_methods.tex`, `sections/comparative_analysis.tex`, `sections/gaps_and_future.tex`, and `sections/conclusion.tex` need to be created.

---

## 3. Section-by-Section Writing Plan

### 3.1 Abstract (NEW — write last)
MSSP expects a structured abstract with the following implicit structure:
- **Context/motivation** (2–3 sentences): Why does LCM matter? Why is signal processing the bottleneck?
- **Scope** (1–2 sentences): What this review covers, how many sources, what time window.
- **Findings** (3–4 sentences): Key discoveries about which SP methods dominate, what gaps exist.
- **Contribution** (1–2 sentences): What this review adds that others do not.

*Write this last, after all sections are complete.*

---

### 3.2 Introduction (REVISE — fill TODOs + add contribution statement)

**Current state:** Good opening paragraph. TODOs in the file outline what's missing.

**What to add:**
1. **Define key terms properly** in the introduction itself (not just in the theory section): lubrication film, film thickness, Lambda-ratio, lubrication regime, active vs. passive sensing, invasive vs. non-invasive, online/at-line/in-line/offline, and where signal processing fits in each.
2. **Expand the "Existing Reviews" subsection** into a proper gap analysis table. For each existing review, note: sensor types covered, SP methods covered, whether passive/non-invasive methods are included, whether a SP taxonomy is offered. Conclude that no existing review systematically addresses SP methods for LCM.
3. **Add an explicit Contribution Statement paragraph** before the paper outline. E.g., "The contributions of this review are: (1)..., (2)..., (3)..."
4. **Paper roadmap** (1 paragraph at end of introduction): one sentence per section.

**Estimated additions:** ~600–900 words.

---

### 3.3 Systematic Review Methodology (EXPAND significantly)

**Current state:** One paragraph listing databases and keywords. This is inadequate for MSSP.

**What to add:**
1. **PRISMA-style flow diagram** (or adapted version): Initial records → removed duplicates → screened by title/abstract → full-text assessed → included. The numbers are already in the inclusion criteria section (131 → 48 relevant → breakdown). Make this a proper figure.
2. **Inclusion/exclusion criteria table**: A formal 2-column table listing inclusion criteria (e.g., "study concerns rolling element bearings", "sensing method is described in sufficient detail to assess the signal processing approach") and exclusion criteria (e.g., "studies concerning journal bearings only", "review limited to non-bearing lubrication systems").
3. **Search strategy**: Document the exact Boolean search strings used, the databases, and the date range of the search.
4. **Quality assessment approach**: How were sources evaluated? Note any limitations (e.g., grey literature, patents excluded).

**Estimated additions:** ~400–600 words + PRISMA figure.

---

### 3.4 Lubrication Physics & Signal Origins (REVISE + EXTEND)

**Current state:** Good. Covers lubrication regimes, Hamrock-Dowson, Lambda-ratio, kappa-ratio.

**What to add for MSSP:**
1. **Physical origins of measurable signals** — this is the critical bridge to the SP section and is currently missing. Add a subsection that explains *why* each physical phenomenon produces a measurable signal:
   - EHL contact → elastic wave emission (AE/ultrasound origin)
   - Asperity contact and sliding friction → broadband noise (vibration, sound, ultrasound)
   - Heat generation from friction → temperature rise
   - Dielectric properties of lubricant film → electrical capacitance/impedance changes
   This links the physics to the sensing methods and justifies why certain SP bands/features are informative.
2. **Stribeck curve** — add a brief discussion of the Stribeck curve as it directly relates lubrication regime to friction coefficient, and the friction coefficient determines the amplitude of many of the measurable signals. This is widely referenced in LCM literature and its absence is notable.
3. **Lubricant degradation mechanisms** — briefly distinguish film thickness reduction (starvation), viscosity degradation (thermal/oxidative aging), and contamination (wear debris, water ingress) as they produce different signal signatures and require different SP approaches.

**Estimated additions:** ~500–700 words + 1 figure (Stribeck curve or signal-origin diagram).

---

### 3.5 Sensing Methods Taxonomy (REVISE + CONSOLIDATE)

**Current state:** Split awkwardly across three files. Content is reasonable but tables need finishing.

**What to do:**
1. **Consolidate** `invasive_active_methods.tex` and `non-invasive_passive_methods.tex` into the main sensing methods section.
2. **Add a taxonomy figure** at the start of the section: a 2×2 matrix (Active/Passive × Invasive/Non-invasive) showing where each method falls. This is the clearest possible visual summary of the classification and will likely be cited heavily if the paper is published.
3. **Standardize the description of each method** to a consistent template: (a) physical principle, (b) sensor hardware, (c) typical signal characteristics (frequency range, SNR considerations), (d) what lubrication information it is sensitive to, (e) limitations.
4. **Expand the non-invasive/passive section** — this is your differentiating contribution, so AE, vibration, ultrasound (>20 kHz), thermal, and sound deserve more thorough treatment than the active/invasive methods.
5. **Add electrostatic sensing** — this passive, non-invasive method (mentioned in one of the commented-out TODO notes) appears to be underrepresented in the current draft.

---

### 3.6 Signal Processing Methods (RESTRUCTURE as a primary section)

**Current state:** SP methods are embedded as sub-bullets under each sensing method. For MSSP, this is insufficient. SP must be treated as a first-class dimension.

**Recommended approach:** Create a dedicated section that cuts *across* sensing modalities and organizes by SP family. For each SP family, describe the method itself (not just list papers using it), then discuss which sensing modalities it is applied to, what lubrication information it extracts, and what its limitations are.

**Recommended subsection structure:**

#### 5.1 Time-Domain Methods
- Statistical features: RMS, kurtosis, crest factor, skewness — interpretation in terms of impulsiveness and signal energy. Normalization strategies for speed/load variation.
- Threshold methods (dB-above-reference): industrial standard for ultrasound (UE Systems, Sonotec). Discuss limitations: no load/speed compensation, no degradation model.

#### 5.2 Frequency-Domain Methods
- Fourier transform and power spectral density: bearing characteristic frequencies (BPFO, BPFI, BSF, FTF), sidebands, harmonics.
- Envelope analysis: demodulation of high-frequency carrier (AE, ultrasound) to extract low-frequency modulation by bearing kinematics.
- Spectral kurtosis: optimal band selection for impulsive transients — connection to kappa-ratio (Jakobsen 2023).
- Cepstral analysis: if applicable, note any uses for LCM.

#### 5.3 Time-Frequency and Decomposition Methods
- Short-Time Fourier Transform (STFT): tradeoff between time and frequency resolution.
- Wavelet Transform: multi-resolution analysis — which wavelet families are used for AE vs. vibration?
- Empirical Mode Decomposition (EMD) / Hilbert-Huang Transform: non-stationary, nonlinear signals.
- Symplectic Geometry Mode Decomposition: used for magnetic debris signals (Yu 2021).

#### 5.4 Signal Enhancement Methods
- Minimum Entropy Deconvolution (MED): recovering weak impulses from starved lubrication — link to vibration and AE.
- Bandpass filtering strategies for AE.

#### 5.5 Physics-Based and Model-Driven Methods
- Spring model (ultrasonic reflectometry): reflection coefficient → film thickness via quasi-static spring model.
- Electrical models (capacitance, impedance): Hertzian contact geometry + dielectric constant → film thickness.
- Hamrock-Dowson as inverse model: using kappa/Lambda estimates as regression targets for data-driven methods.
- Acoustic propagation models for SAW.

#### 5.6 Machine Learning and Deep Learning
- Classical ML: SVM, random forests, logistic regression, LASSO — applied to handcrafted features from above domains.
- Deep learning: CNNs for image-based optical classification, GNNs for graph-structured multi-sensor data (Zhang 2024).
- Self-supervised and few-shot approaches: note if present or absent in the literature (likely a gap).
- Key challenge: lack of labelled degradation data (expensive to generate controlled experiments).

#### 5.7 Multi-Sensor Data Fusion
- Early, intermediate, and late fusion strategies.
- Kalman filter-based tracking for optical debris.
- Multi-modal fusion combining vibration, AE, and temperature (Zhang 2024).

**For each subsection:** include a small summary table or figure if possible. A master cross-reference matrix (Sensing method × SP method × Reference) at the end of this section would be a highly citable contribution.

---

### 3.7 Comparative Analysis (NEW — critical for MSSP)

This section is what separates a publishable review from a PhD-level literature survey. It should synthesize across sections and directly compare methods. Suggested content:

1. **Effectiveness vs. lubrication fault type**: Build a structured table — rows = lubrication fault (starvation, degraded viscosity, contamination, grease aging), columns = sensing method + SP method, cells = sensitivity (high/medium/low/not demonstrated) with key references.
2. **Sensitivity to operating conditions**: Speed, load, temperature affect signals differently for each sensing+SP combination. Summarize known limitations.
3. **Practical deployment requirements**: For each method, characterize: sensor cost/availability, required modifications to bearing or housing, need for calibration/reference signal, real-time capability, robustness to industrial environments.
4. **Maturity levels**: Map methods on a Technology Readiness Level (TRL) scale or a simpler research/prototype/industrial scale. Industrial use of ultrasound thresholding vs. lab-only AE ML methods.
5. **Performance metrics reported**: Note that the field lacks standardized benchmarks — papers use different operating conditions, bearing types, fault severities. This is itself a finding.

---

### 3.8 Research Gaps and Future Directions (NEW)

Based on the comparative analysis, identify 4–6 concrete gaps. These should be SP-focused to align with MSSP. Candidates based on the draft:

1. **No standardized benchmark dataset** for LCM signal processing — the field cannot compare methods rigorously without controlled, publicly available datasets with known lubrication conditions.
2. **Speed and load invariance** in SP features — virtually all SP methods assume stationary operating conditions; LCM under variable speed/load is largely unsolved.
3. **Passive/non-invasive methods are underexplored relative to active methods** — despite practical advantages, the signal processing pipeline for AE, ultrasound, and vibration-based LCM is less mature than for electrical or ultrasonic reflectometry methods.
4. **Lack of data-driven methods for grease LCM** — most ML approaches address oil lubrication; grease behaves differently (channeling, oxidation, thickener degradation) and is less studied.
5. **Maintenance decision integration** — the LCM → maintenance action pipeline is broken; the field lacks SP methods that produce outputs directly usable by relubrication decision algorithms.
6. **Multi-sensor fusion with non-invasive sensors** — existing fusion work uses lab setups; fusion of purely non-invasive sensors under realistic industrial conditions is not demonstrated.

---

### 3.9 Conclusion (NEW)

3–5 paragraphs:
1. Brief restatement of scope and motivation.
2. Summary of key findings about sensing methods.
3. Summary of key findings about signal processing methods.
4. Most important identified gaps (2–3 sentences each).
5. Outlook sentence.

---

## 4. Figures and Tables Checklist

These visual elements will determine the quality of the submission:

| Figure/Table | Status | Notes |
|---|---|---|
| LCM monitoring flow diagram | ✅ `lcm_overview.png` | May need updating to show SP step more prominently |
| **Active/Passive × Invasive/Non-invasive taxonomy matrix** | ❌ Needed | 2×2 matrix with sensing methods placed in cells |
| **Stribeck curve with signal-origin overlay** | ❌ Needed | Shows where each sensing method is sensitive in the regime diagram |
| PRISMA-style literature flow diagram | ❌ Needed | Numbers already exist in inclusion criteria section |
| **SP × Sensing modality cross-reference matrix** | ❌ Needed | The single highest-value table in the paper |
| Non-invasive methods summary table | ✅ `non-invasive_passive_methods.tex` | Complete but needs final review |
| Invasive methods summary table | 🔶 `invasive_active_methods.tex` | Exists but may need completion |
| **Fault type vs. method sensitivity table** | ❌ Needed | For comparative analysis section |
| **Method maturity / deployment readiness table** | ❌ Needed | For comparative analysis section |

---

## 5. MSSP Submission Requirements to Check

Before submission:
- [ ] Read MSSP Guide for Authors carefully (word/page limits, figure resolution, reference format)
- [ ] Confirm reference style: currently `biblatex` numeric — check if MSSP requires a specific style (typically Elsevier)
- [ ] Paper length: MSSP review articles typically run 10,000–15,000 words (main text). Current draft is significantly shorter.
- [ ] Highlight novelty vs. existing reviews explicitly in cover letter
- [ ] Suggest 4–5 reviewers with expertise in bearing diagnostics + SP

---

## 6. Recommended Writing Order

Work in this order to make each section build on the previous:

1. **Lubrication physics additions** (signal origins, Stribeck) — foundational
2. **Sensing methods consolidation** — unify the three files
3. **Signal processing methods section** — the core new contribution
4. **Comparative analysis** — synthesizes all prior sections
5. **Gaps and future directions** — follows from analysis
6. **Introduction revisions** — now you know what you're introducing
7. **Conclusion** — summarizes what you've written
8. **Systematic review methodology** — fill in PRISMA details
9. **Abstract** — write absolutely last

---

## 7. Effort Estimate

| Task | Estimated effort |
|---|---|
| Restructure LaTeX files | 1–2 hours |
| Fill introduction TODOs + contribution statement | 3–5 hours |
| Expand literature search methodology + PRISMA | 2–3 hours |
| Add signal origins + Stribeck to theory section | 3–4 hours |
| Consolidate & standardize sensing methods section | 4–6 hours |
| Write SP methods section (new, primary contribution) | 8–12 hours |
| Write comparative analysis | 6–8 hours |
| Write gaps and future directions | 3–4 hours |
| Write conclusion | 2–3 hours |
| Create missing figures | 4–6 hours |
| Write abstract | 1–2 hours |
| Final proofread + LaTeX cleanup | 3–4 hours |
| **Total estimate** | **~40–60 hours of focused writing** |

---

## 8. Key Differentiator Sentence (for cover letter)

> "Unlike existing reviews of lubrication condition monitoring that are organized by sensing modality, this review provides the first systematic taxonomy of signal processing methods applied across all sensing approaches for ball bearing LCM, identifying the SP assumptions, limitations, and open problems that constrain progress toward practical, passive, and non-invasive deployment."
