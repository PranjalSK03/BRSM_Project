# BRSM Project: Event Segmentation and Boundary Effects on Recognition Memory

**Course:** BRSM (Behavioural Research & Statistical Methods) - Mid-Semester Project  
**Team:** Vibe Coders  
**Date:** March 2026  
**Repository:** [https://github.com/PranjalSK03/BRSM_Project](https://github.com/PranjalSK03/BRSM_Project)

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Research Question](#research-question)
3. [Theoretical Background](#theoretical-background)
4. [Why This Study Matters](#why-this-study-matters)
5. [Experimental Design](#experimental-design)
6. [Dataset Description](#dataset-description)
7. [Data Cleaning & Preprocessing](#data-cleaning--preprocessing)
8. [Statistical Analysis Approach](#statistical-analysis-approach)
9. [Key Findings](#key-findings)
10. [File Structure](#file-structure)
11. [How to Reproduce the Analysis](#how-to-reproduce-the-analysis)
12. [Design Decisions & Rationale](#design-decisions--rationale)
13. [Dependencies](#dependencies)
14. [Team Contributions](#team-contributions)
15. [References](#references)

---

## Project Overview

This project investigates **how the temporal position of a video clip's ending relative to natural event boundaries affects recognition memory for individual video frames**. The study tests predictions from **Event Segmentation Theory (EST)**, which proposes that humans spontaneously segment continuous experiences into discrete events, and that event boundaries enhance memory encoding and consolidation.

### Core Research Question

**Does disrupting natural event boundaries impair memory for video frames, particularly for frames adjacent to those boundaries?**

---

## Research Question

We examined whether participants who viewed videos ending at **natural event boundaries** (e.g., a person completing an action) show better recognition memory compared to participants who viewed videos **truncated abruptly before reaching the boundary** (mid-event).

**Primary Hypotheses:**

1. **H1 (Main Effect):** Participants in the Natural Boundary (NB) condition will demonstrate higher overall recognition accuracy than those in the Abrupt Boundary (AB) condition.

2. **H2 (Boundary Frame Advantage):** The NB advantage will be significantly stronger for frames from 0-3 seconds before the boundary (BB frames) compared to frames from the middle of events (EM frames).

3. **H3 (Null Effect on Event-Middle Frames):** NB and AB conditions will not differ significantly on recognition accuracy for EM frames, as these frames are temporally distant from the disrupted boundary.

---

## Theoretical Background

### Event Segmentation Theory (EST)

**Event Segmentation Theory** (Zacks et al., 2007) proposes that:

- Humans spontaneously parse continuous experience into discrete events
- The cognitive system maintains **predictive models** of what will happen next
- When predictions fail (e.g., scene changes, action shifts), the system experiences **prediction error**
- These prediction errors signal **event boundaries**
- At boundaries, the cognitive system "saves" the current event representation to long-term memory while preparing to encode a new event

### The Boundary Advantage Effect

**Swallow et al. (2009)** demonstrated the **Boundary Advantage Effect**: superior memory for information presented at event boundaries compared to event middles. This occurs because:

1. **Enhanced attention** at boundaries due to prediction error
2. **Memory consolidation** of the completed event model
3. **Preparation for new encoding** as a new event begins

### Study Predictions

If natural event boundaries enhance memory encoding through these mechanisms, then **artificially truncating videos before they reach natural boundaries** should:

- **Prevent** the normal boundary-related memory enhancement
- **Impair** recognition for frames that would have been near the (now absent) boundary
- **Weaken** overall event memory by interrupting the event model updating process

---

## Why This Study Matters

### Theoretical Significance

1. **Tests Event Segmentation Theory predictions** in a controlled experimental paradigm
2. **Isolates the causal role** of event boundaries in memory encoding (not just correlational)
3. **Extends knowledge** about how temporal structure affects memory for dynamic visual information

### Practical Applications

1. **Video editing and multimedia design:** Cutting videos at natural boundaries may optimize viewer comprehension and memory retention
2. **Educational materials:** Structuring instructional videos around natural event boundaries could enhance learning outcomes
3. **Human-computer interaction:** Understanding event segmentation can inform design of video interfaces and content delivery systems
4. **Eyewitness memory:** Insight into how event structure affects memory for real-world dynamic events

---

## Experimental Design

### Design Type

**2 × 2 Mixed Design:**
- **Between-subjects factor:** Condition (NB vs AB)
- **Within-subjects factor:** Frame Type (BB vs EM)

### Independent Variables

#### 1. Condition (Between-Subjects)

- **NB (Natural Boundary):** Videos ended at natural event boundaries
  - Example: A person completing a hand gesture, finishing pouring water, closing a door
  
- **AB (Abrupt Boundary):** Videos were truncated 1-5 seconds **before** the natural boundary
  - Example: Stopping mid-gesture, mid-pour, mid-door-closing

#### 2. Frame Type (Within-Subjects)

- **BB (Before Boundary):** Frames extracted from 0-3 seconds before the natural event boundary
  - These frames are most proximal to the manipulated boundary
  
- **EM (Event Middle):** Frames extracted from the middle of the event, far from boundaries
  - These frames serve as a control to test boundary-specificity

### Dependent Variables

1. **Recognition Accuracy (Primary DV):** Binary (0 = incorrect, 1 = correct identification of target frame)
2. **Response Time (Secondary DV):** Time in seconds from stimulus onset to response
3. **Confidence Rating (Secondary DV):** Self-rated confidence (1-5 scale)

### Procedure

1. **Encoding Phase:**
   - Participants viewed 40 short video clips (17-57 seconds each)
   - Videos depicted everyday activities (cooking, cleaning, object manipulation)
   - Random assignment to NB or AB condition

2. **Recognition Phase:**
   - 40 forced-choice trials (one per video)
   - Each trial: Two frames presented side-by-side
     - **Target:** Frame actually shown in the video
     - **Lure:** Similar frame NOT shown in the video
   - Participants selected which frame they recognized
   - Confidence rating collected immediately after each decision

3. **Demographics:**
   - Age, gender, handedness, vision status collected post-experiment

### Participant Exclusion Criteria

- Participants with **< 20 valid trials** excluded from analysis (incomplete/corrupted data)
- This ensured sufficient data per participant for reliable mean accuracy estimates

---

## Dataset Description

### Data Sources

1. **Recognition Data:**
   - Individual CSV files per participant (N = 163 included, 22 excluded)
   - Location: `BRSM data csv/BRSM data csv/`
   - Naming convention: `sub[ID]_[Condition]_recognitionstage_[timestamp].csv`

2. **Demographic Data:**
   - Single Excel file: `Demographic data.xlsx`
   - Contains: Age, Gender, Handedness, Vision status per participant

3. **Stimulus Metadata:**
   - `abruptmovies.csv`: List of movies in AB condition
   - `naturalmovies.csv`: List of movies in NB condition
   - `target_and_lures.csv`: Frame pairs used in recognition trials

### Sample Characteristics

- **Total Participants:** 163 (after exclusions)
- **Age:** M = 22.0 years, SD = 1.7, Range = 19-28 years
- **Gender:** 69% Male (113), 31% Female (50)
- **Handedness:** 89% Right-handed
- **Vision:** 91% Normal or Corrected-to-Normal

### Condition Assignment

- **NB Condition:** 82 participants
- **AB Condition:** 81 participants
- Age and gender balanced across conditions (both p > .05)

### Trial Structure

- **40 trials per participant** × 163 participants = **6,520 total observations**
- Each trial tests either BB or EM frame (counterbalanced within-subjects)

---

## Data Cleaning & Preprocessing

### Why Data Cleaning Was Necessary

Raw data from PsychoPy experiments often contains:
- Inconsistent string formatting (brackets, extra spaces)
- Missing values from incomplete trials
- Extreme outliers from accidental key presses or inattention
- Redundant columns from experimental software

### Cleaning Pipeline (6 Steps)

#### Step 1: Participant Exclusion

**Decision:** Exclude participants with < 20 valid data rows

**Rationale:**
- 40 trials expected per participant
- < 20 rows suggests incomplete session, software crash, or data corruption
- Ensures reliable mean estimates per participant
- Prevents pseudoreplication from partially complete data

**Result:** 163 participants retained, 22 excluded

---

#### Step 2: Variable Type Conversion

**Actions:**
- Extracted `Condition` from filename (case-insensitive regex: `sub[0-9]+_[NB|AB]`)
- Converted `Accuracy` from character ("0", "1") to numeric (0, 1)
- Converted `RT` from string with brackets ("[2.341]") to numeric (2.341)
- Converted `Confidence` from string to numeric (1-5)

**Rationale:**
- PsychoPy stores all data as strings by default
- Numeric conversion required for mathematical operations
- Condition extraction from filename ensures correct experimental assignment even if internal variable corrupted

---

#### Step 3: Frame Type Derivation

**Decision:** Classify frame type based on `target_img` filename

**Logic:**
- If filename contains "BB" → `FrameType = "BB"`
- If filename contains "EM" → `FrameType = "EM"`
- Otherwise → `FrameType = NA` (excluded)

**Rationale:**
- Frame type is stimulus-determined, not participant-determined
- Filename encoding is most reliable source (pre-determined by experimenters)
- Alternative (inferring from trial order) would be error-prone

---

#### Step 4: Response Time Outlier Removal

**Decision:** Remove RT observations > Mean + 3 SD

**Cutoff Calculation:**
- RT Mean = 2.14 seconds
- RT SD = 0.98 seconds
- Cutoff = 2.14 + (3 × 0.98) = **5.08 seconds**

**Rationale:**
- **3 SD rule** is standard in psychology for outlier detection
- Captures ~99.7% of data under normal distribution
- Extremely long RTs (> 5 seconds) likely reflect:
  - Momentary distraction
  - Accidental key press delays
  - Confusion or task misunderstanding
- Alternative (median absolute deviation) considered but 3 SD rule more interpretable
- **Conservative choice:** Retains more data than 2 SD or 2.5 SD cutoffs

**Result:** Removed 87 trials (1.3% of data)

---

#### Step 5: Missing Data Handling

**Decision:** Listwise deletion on critical variables (Accuracy, Condition, FrameType)

**Rationale:**
- Missing accuracy = unusable trial (no DV)
- Missing condition = cannot assign to experimental group
- Missing frame type = cannot test frame-specific hypotheses
- Alternative (imputation) inappropriate for categorical DVs
- Complete-case analysis is standard for experimental data with low missingness

**Impact:** Minimal (<2% additional data loss)

---

#### Step 6: Aggregation to Participant-Level

**Decision:** Aggregate trial-level data to participant means

**Why Aggregation is Critical:**

1. **Independence Assumption:**
   - Statistical tests (t-tests) assume **independent observations**
   - Multiple trials from same participant are **not independent** (autocorrelation)
   - Using trial-level data violates this assumption → inflated Type I error

2. **Unit of Analysis:**
   - Participants (not trials) were randomly assigned to conditions
   - Experimental unit = participant
   - Inference target = participant population (not trial population)

3. **Avoid Pseudoreplication:**
   - Using 6,520 trials would artificially inflate N
   - Actual N = 163 participants
   - Treating trials as independent = pseudoreplication fallacy

**Aggregation Strategy:**

Three datasets created:

1. **participant_level:**
   - One row per participant
   - Variables: `mean_accuracy`, `mean_rt`
   - Used for: Overall condition comparisons (Tests 1 & 2)

2. **participant_frametype:**
   - One row per participant × frame type combination
   - Variables: `mean_accuracy` (separately for BB and EM)
   - Used for: Frame-specific comparisons (Tests 3 & 4)

3. **participant_demo:**
   - Merges aggregated performance with demographics
   - Used for: Demographic moderator analyses (Tests D1-D4)

---

## Statistical Analysis Approach

### Why These Methods Were Chosen

#### 1. Welch's Independent-Samples t-test

**Decision:** Use Welch's t-test (unequal variance) instead of Student's t-test

**Rationale:**
- **Does not assume equal variances** between groups
- More robust when sample sizes are slightly unequal (NB: 82, AB: 81)
- Satterthwaite degrees of freedom correction accounts for variance heterogeneity
- **Conservative choice:** Sacrifices slight power for better Type I error control
- Standard recommendation in modern statistics (Delacre et al., 2017)

**Alternative Considered:** Student's t-test rejected because:
- Requires equal variance assumption (Levene's test would add another comparison)
- Welch's test performs equally well when variances are equal, and better when unequal

---

#### 2. Bonferroni Correction for Multiple Comparisons

**Decision:** Apply Bonferroni correction to 4 primary hypothesis tests

**The Multiple Comparisons Problem:**

When conducting multiple tests on the same dataset:
- Probability of at least one Type I error (false positive) increases
- With alpha = 0.05 and 4 tests: Family-Wise Error Rate (FWER) ≈ 18.6%
- This means ~1 in 5 chance of incorrectly rejecting at least one true null hypothesis

**Bonferroni Solution:**

Adjusted alpha = 0.05 / 4 = **0.0125**

**Rationale:**
- **Controls FWER** at 5% across all 4 tests
- **Simple and transparent** (easy to report and interpret)
- **Conservative but appropriate** for confirmatory hypothesis tests
- Standard in psychology when number of tests is small (k ≤ 10)

**Alternative Methods Considered:**

| Method | Why Not Used |
|--------|--------------|
| Holm-Bonferroni | More complex; minimal power gain with k=4 |
| Benjamini-Hochberg FDR | For exploratory studies with many tests; we have 4 planned tests |
| No correction | Unacceptable inflation of FWER (18.6%) |

**Which Tests Use Bonferroni?**

- **Primary tests (alpha = 0.0125):** Tests 1-4 (confirmatory hypotheses)
- **Demographic tests (alpha = 0.05):** Tests D1-D4 (exploratory checks, separate family)

**Trade-off Accepted:**
- Bonferroni reduces statistical power (increases Type II error risk)
- This is acceptable to maintain confidence in positive findings
- With large effect sizes (d > 0.8), power remains adequate

---

#### 3. Cohen's d Effect Size

**Decision:** Report Cohen's d for all t-tests

**Formula:**

```
Cohen's d = (M₁ - M₂) / SD_pooled

where SD_pooled = sqrt[((n₁-1)×SD₁² + (n₂-1)×SD₂²) / (n₁+n₂-2)]
```

**Interpretation Guidelines:**

- Small: d ≈ 0.2
- Medium: d ≈ 0.5
- Large: d ≈ 0.8
- Very large: d ≥ 1.0

**Rationale:**
- **Standardized effect size** (unitless, comparable across studies)
- **Quantifies practical significance** beyond statistical significance
- Required by APA reporting standards
- Aids meta-analysis and power analysis for future studies
- Complements p-values (which conflate effect size and sample size)

---

#### 4. Demographic Tests (Exploratory Analyses)

**Decision:** Report demographic tests with **unadjusted alpha = 0.05**

**Tests Conducted:**

- **D1:** Age balance (NB vs AB) [Randomization check]
- **D2:** Gender balance (NB vs AB) [Randomization check]
- **D3:** Age as moderator of accuracy [Exploratory]
- **D4:** Gender as moderator of accuracy [Exploratory]

**Rationale for No Correction:**

1. **Separate hypothesis family** from primary tests
2. **Exploratory nature** (not confirmatory hypotheses)
3. **Randomization checks** (D1, D2) verify experimental validity, not test theory
4. **Moderator analyses** (D3, D4) are hypothesis-generating

Applying Bonferroni here would be overly conservative and is not standard practice for auxiliary analyses.

---

### Statistical Assumptions

#### Tested and Verified:

1. **Independence of observations:** ✓ (participant-level aggregation)
2. **Random sampling:** ✓ (convenience sample typical of psychology)
3. **Continuous/ratio-level DV:** ✓ (accuracy is proportion, approximately continuous)
4. **Normality:** Not strictly required for t-tests with n > 30 per group (Central Limit Theorem)
5. **Equal variances:** Not required (Welch's t-test robust to heteroscedasticity)

---

## Key Findings

### Primary Hypothesis Tests (Bonferroni-adjusted alpha = 0.0125)

#### Test 1: Overall Recognition Accuracy (H1)

- **Result:** NB participants (M = 0.879) significantly outperformed AB participants (M = 0.831)
- **Statistics:** t(160.3) = 6.79, p < .001, **d = 0.92** (large effect)
- **Interpretation:** Natural boundaries enhance overall memory consolidation
- **Conclusion:** ✓ **H1 Supported**

---

#### Test 2: Response Time

- **Result:** No significant difference between NB (M = 2.14s) and AB (M = 2.13s)
- **Statistics:** t(160.8) = 0.18, p = .859, d = 0.02 (negligible effect)
- **Interpretation:** Accuracy differences reflect genuine memory strength, not speed-accuracy tradeoffs
- **Conclusion:** Rules out alternative explanation

---

#### Test 3: Boundary Frame Accuracy (H2)

- **Result:** For BB frames, NB (M = 0.899) >> AB (M = 0.809)
- **Statistics:** t(159.7) = 7.34, p < .001, **d = 1.01** (very large effect)
- **Interpretation:** Boundary-adjacent frames show the largest impairment when boundaries are disrupted
- **Conclusion:** ✓ **H2 Strongly Supported**

---

#### Test 4: Event-Middle Frame Accuracy (H3)

- **Result:** For EM frames, NB (M = 0.862) > AB (M = 0.810) [unexpected]
- **Statistics:** t(161.2) = 3.15, p = .002, **d = 0.46** (medium effect)
- **Interpretation:** Boundary disruption affects broader event representations than anticipated
- **Conclusion:** ✗ **H3 Not Supported** (EM frames also impaired, though less than BB frames)

---

### Demographic Tests (Exploratory, alpha = 0.05)

#### D1: Age Balance

- **Result:** NB (M = 22.0) vs AB (M = 22.1), t(160.9) = -0.52, p = .603
- **Conclusion:** Age successfully balanced across conditions ✓

#### D2: Gender Balance

- **Result:** χ²(1) = 0.46, p = .497
- **Conclusion:** Gender successfully balanced across conditions ✓

#### D3: Age as Moderator

- **Result:** r = 0.07, p = .392
- **Conclusion:** Age does not predict recognition accuracy (narrow age range)

#### D4: Gender as Moderator

- **Result:** Female (M = 0.855) vs Male (M = 0.854), t(106.7) = 0.09, p = .930
- **Conclusion:** No gender differences in memory performance

---

### Effect Size Summary

| Test | Comparison | Cohen's d | Magnitude |
|------|------------|-----------|-----------|
| Test 1 | Overall Accuracy (NB > AB) | 0.92 | Large |
| Test 2 | Response Time (NB ≈ AB) | 0.02 | Negligible |
| Test 3 | BB Frames (NB > AB) | 1.01 | Very Large |
| Test 4 | EM Frames (NB > AB) | 0.46 | Medium |

**Pattern:** Boundary disruption has **largest impact on boundary-adjacent frames (BB)**, but also affects **entire event memory (EM)**, suggesting event boundaries provide organizational structure for entire event representations.

---

## File Structure

```
BRSM_Project/
│
├── BRSM data csv/
│   ├── BRSM data csv/                    # Individual participant CSVs (163 files)
│   │   ├── sub100_AB_recognitionstage_*.csv
│   │   ├── sub101_AB_recognitionstage_*.csv
│   │   └── ...
│   ├── Demographic data.xlsx             # Demographics (Age, Gender, Handedness, Vision)
│   ├── abruptmovies.csv                  # List of AB condition video stimuli
│   ├── naturalmovies.csv                 # List of NB condition video stimuli
│   ├── target_and_lures.csv              # Frame pairs used in recognition trials
│   └── BRSM_Project_Summary.md           # Project metadata
│
├── BRSM_report.Rmd                       # FULL DETAILED ANALYSIS (with code, EDA, demographics)
├── BRSM_report.html                      # HTML output of full report
│
├── BRSM_Final_Report.Rmd                 # CONDENSED REPORT (9 pages, no code displayed)
├── BRSM_Final_Report.html                # HTML output of condensed report
├── BRSM_Final_Report.pdf                 # PDF output of condensed report (9 pages)
│
├── BRSM_report_pdf.Rmd                   # PDF-specific formatting version (deprecated)
│
├── BRSM_analysis_cache/                  # R Markdown cache for faster compilation
├── BRSM_report_cache/                    # Cache for full report
├── BRSM_report_pdf_cache/                # Cache for PDF report
├── BRSM_report_files/                    # Generated figures (HTML)
├── BRSM_report_pdf_files/                # Generated figures (PDF/LaTeX)
│
└── README.md                             # THIS FILE

```

### Key Files Explained

#### Analysis Files

1. **`BRSM_report.Rmd`** (COMPREHENSIVE VERSION)
   - **Purpose:** Full exploratory data analysis with all code chunks visible
   - **Content:** 
     - All data cleaning steps with code
     - Comprehensive demographic summaries (8 demographic EDA figures)
     - All hypothesis tests with code and output
     - Detailed interpretations
   - **Audience:** Technical reviewers, replication researchers
   - **Output:** `BRSM_report.html`

2. **`BRSM_Final_Report.Rmd`** (CONDENSED VERSION)
   - **Purpose:** Clean professional report for submission (no code visible)
   - **Content:**
     - Condensed introduction and theory
     - Streamlined data description
     - 5 key EDA figures
     - All hypothesis tests with interpretations
     - Discussion and implications
   - **Length:** 9 pages (strict 7-9 page limit)
   - **Audience:** Instructors, general scientific audience
   - **Output:** `BRSM_Final_Report.html` and `BRSM_Final_Report.pdf`

#### Data Files

- **Individual CSVs:** One per participant, ~40 rows (trials) per file
- **Demographic data.xlsx:** 163 participants (complete records) + 22 (incomplete)
- **Stimulus metadata CSVs:** Reference files for video stimuli classification

---

## How to Reproduce the Analysis

### Prerequisites

#### Software Requirements

- **R version:** 4.5.2 (or later)
- **RStudio:** 2023.12.0 (or later, optional but recommended)
- **LaTeX distribution:** TinyTeX or TeXLive (for PDF compilation)

#### R Package Dependencies

Install all required packages:

```r
install.packages(c(
  "readr",       # CSV reading
  "dplyr",       # Data manipulation
  "ggplot2",     # Data visualization
  "stringr",     # String manipulation
  "scales",      # Scale functions for ggplot2
  "readxl",      # Excel file reading
  "tibble",      # Modern data frames
  "tidyr",       # Data tidying
  "purrr",       # Functional programming
  "knitr",       # R Markdown knitting
  "rmarkdown"    # R Markdown processing
))
```

### Step-by-Step Reproduction

#### Option 1: Generate Full Report (with code)

```r
# Set working directory
setwd("/path/to/BRSM_Project")

# Compile full report
rmarkdown::render("BRSM_report.Rmd", output_format = "html_document")
```

**Output:** `BRSM_report.html` (comprehensive analysis with all code visible)

---

#### Option 2: Generate Condensed Report (no code)

```r
# Set working directory
setwd("/path/to/BRSM_Project")

# Compile condensed report (HTML + PDF)
rmarkdown::render("BRSM_Final_Report.Rmd", output_format = "all")
```

**Output:** 
- `BRSM_Final_Report.html` (interactive, scrollable)
- `BRSM_Final_Report.pdf` (9 pages, printable)

---

#### Option 3: Run from Command Line

```bash
cd /path/to/BRSM_Project

# Full report
Rscript -e "rmarkdown::render('BRSM_report.Rmd', output_format = 'html_document')"

# Condensed report (both formats)
Rscript -e "rmarkdown::render('BRSM_Final_Report.Rmd', output_format = 'all')"
```

---

### Expected Compilation Time

- **Full report (BRSM_report.Rmd):** ~45-60 seconds
  - Reason: Many figures (13 EDA plots), detailed demographic tables
  
- **Condensed report (BRSM_Final_Report.Rmd):** ~30-40 seconds
  - Reason: Fewer figures (5), streamlined analyses

**Note:** First compilation is slower. Subsequent compilations use R Markdown cache (faster).

---

### Troubleshooting

#### Problem: LaTeX compilation fails for PDF

**Error message:** "LaTeX Error: Unicode character not set up for use with LaTeX"

**Solution:**
```r
# Install TinyTeX (lightweight LaTeX distribution)
install.packages("tinytex")
tinytex::install_tinytex()
```

**Alternative:** Install full TeXLive distribution from your OS package manager

---

#### Problem: "Cannot find file" error

**Cause:** Working directory not set correctly

**Solution:**
```r
# Check current working directory
getwd()

# Set to project folder (replace with your path)
setwd("/home/pranjal-singh-katiyar/Sem2/BRSM/BRSM_Project")

# Verify data folder exists
list.files("BRSM data csv/BRSM data csv/")
```

---

#### Problem: Package not found

**Solution:** Install missing packages
```r
# Check if package is installed
if (!require("dplyr")) install.packages("dplyr")
```

---

## Design Decisions & Rationale

### 1. Why Mixed Design (Between + Within)?

**Decision:** Use between-subjects manipulation for Condition, within-subjects for Frame Type

**Rationale:**

**Between-subjects (Condition):**
- ✓ Avoids carryover effects (seeing both NB and AB versions of same video)
- ✓ Prevents participants from inferring experimental manipulation
- ✓ Eliminates practice effects on boundary detection
- ✗ Requires larger sample size (N = 163 vs ~82 for within-subjects)

**Within-subjects (Frame Type):**
- ✓ Controls individual differences (each person is their own control)
- ✓ Increases statistical power for frame type comparisons
- ✓ Reduces required sample size
- ✓ BB and EM frames occur naturally within same video (unavoidable)

**Hybrid approach** balances power, validity, and feasibility.

---

### 2. Why 40 Trials Per Participant?

**Decision:** Each participant completes 40 recognition trials (one per video)

**Rationale:**
- **Reliability:** 40 trials provides stable mean accuracy estimates (Hedge et al., 2018)
- **Attention span:** ~15-20 minutes prevents fatigue
- **Counterbalancing:** 20 BB trials + 20 EM trials balances frame type exposure
- **Sufficient power:** With 163 participants × 40 trials = 6,520 observations
- Alternative (fewer trials) would reduce measurement reliability

---

### 3. Why Exclude Participants with < 20 Trials?

**Decision:** Participants with < 20 valid rows excluded from analysis

**Rationale:**
- 40 trials expected; < 20 suggests incomplete data (< 50% completion)
- Mean estimates unreliable with small trial counts (high standard error)
- Likely causes: Software crash, early withdrawal, data corruption
- **Conservative threshold:** Retains participants with minor data loss (≥20/40 = 50%)
- Alternative (stricter threshold like < 35) would reduce sample size unnecessarily

**Impact:** 22/185 participants excluded (11.9% exclusion rate, acceptable)

---

### 4. Why Mean + 3 SD for RT Outliers?

**Decision:** Remove RT observations exceeding Mean + 3 SD = 5.08 seconds

**Rationale:**

**3 SD chosen because:**
- Standard in psychology and cognitive science
- Captures ~99.7% of normal distribution (retains most data)
- More conservative than 2 SD (which would exclude ~5% of data)
- Less conservative than no removal (which inflates variance estimates)

**Alternative methods considered:**

| Method | Why Not Used |
|--------|--------------|
| 2 SD | Too aggressive (excludes ~5% of normal data) |
| Median Absolute Deviation (MAD) | Less interpretable; similar results |
| No removal | Inflates variance; violates normality for parametric tests |
| Fixed cutoff (e.g., 3 seconds) | Arbitrary; not data-driven |

**Result:** 87/6,520 trials removed (1.3%, minimal impact)

---

### 5. Why Participant-Level Aggregation?

**Decision:** Aggregate trial-level data to participant means before t-tests

**Rationale:**

**Statistical requirement:**
- t-tests assume **independent observations**
- Trials from same participant are **correlated** (non-independent)
- Violating independence inflates Type I error rate

**Why not mixed-effects models?**

Mixed-effects models (e.g., `lme4::lmer()`) can handle trial-level data with random intercepts for participants. We chose aggregation because:

| Aggregation (Used) | Mixed-Effects (Not Used) |
|--------------------|---------------------------|
| ✓ Simple and transparent | ✗ More complex to report |
| ✓ Standard in psychology | ✗ Requires additional assumptions |
| ✓ Robust to violations | ✗ Model convergence issues common |
| ✓ Easy to verify by reviewers | ✗ Model specification debatable |

For **balanced designs** with **sufficient trials per participant**, aggregation and mixed-effects yield **nearly identical results** (Judd et al., 2012).

---

### 6. Why Bonferroni (Not Other Corrections)?

**Decision:** Apply Bonferroni correction (alpha = 0.05/4 = 0.0125)

**Comparison of methods:**

| Method | FWER Control | Power | Complexity | Used? |
|--------|--------------|-------|------------|-------|
| **Bonferroni** | ✓ Exact | Moderate | Low | ✓ YES |
| Holm-Bonferroni | ✓ Exact | Slightly higher | Moderate | ✗ No |
| Šidák | ✓ Exact | Slightly higher | Low | ✗ No |
| Benjamini-Hochberg FDR | ✗ FDR only | High | Moderate | ✗ No |
| No correction | ✗ Inflated | Highest | None | ✗ No |

**Bonferroni chosen because:**
- Most conservative (minimizes false discoveries)
- Standard in psychology for small number of tests (k ≤ 10)
- Simple to communicate to non-statisticians
- Reviewers expect it for confirmatory hypotheses

**Not Holm-Bonferroni because:**
- Marginal power gain (~2%) not worth added complexity
- Requires ranking p-values (order matters)
- Less familiar to general audience

**Not FDR because:**
- FDR controls expected proportion of false discoveries (not FWER)
- Appropriate for exploratory studies with many tests (k > 50)
- We have 4 planned confirmatory tests

---

### 7. Why Two Reports (Full vs Condensed)?

**Decision:** Maintain two versions of the analysis report

**`BRSM_report.Rmd` (Full Version):**
- **Purpose:** Transparency, reproducibility, detailed exploration
- **Audience:** Technical reviewers, future researchers
- **Content:** All code visible, 13 EDA figures, comprehensive demographics
- **Length:** ~30 pages HTML

**`BRSM_Final_Report.Rmd` (Condensed Version):**
- **Purpose:** Professional submission, clear communication
- **Audience:** Instructors, general scientific audience
- **Content:** No code, 5 key figures, streamlined narrative
- **Length:** 9 pages PDF (within 7-9 page limit)

**Rationale:**
- Best practices in reproducible research (Wilson et al., 2017)
- Separates "analysis notebook" from "research manuscript"
- Full version enables replication; condensed version enables understanding

---

### 8. Why These Visualizations?

**Figures Included in Condensed Report:**

| Figure | Purpose | Design Choice |
|--------|---------|---------------|
| **Figure 1: Violin Plot (Condition)** | Show distribution shape, outliers, central tendency | Violin shows full distribution (better than boxplot alone) |
| **Figure 2: Density Plot** | Compare probability distributions between conditions | Smooth curves easier to compare than histograms |
| **Figure 3: Violin Plot (Frame Type)** | Demonstrate Boundary Advantage Effect (BB > EM) | Consistent with Figure 1 for comparability |
| **Figure 4: Bar Chart with 95% CI** | Quantify interaction (Condition × Frame Type) | Error bars show statistical uncertainty |
| **Figure 5: Heatmap** | Visualize 2×2 interaction pattern | Intuitive color gradient (dark blue = high accuracy) |

**Design Principles:**
- **Color scheme:** Consistent across figures (NB = blue, AB = red, BB = green, EM = orange)
- **Theme:** Clean, minimal distraction (theme_classic base)
- **Annotations:** Every figure has interpretation paragraph

---

### 9. Why Include Demographic Tests?

**Decision:** Report 4 demographic tests (D1-D4) despite not being primary hypotheses

**Rationale:**

**D1 & D2 (Randomization checks):**
- Essential for experimental validity
- Confirm random assignment succeeded
- Standard requirement in experimental psychology

**D3 & D4 (Moderator analyses):**
- Address potential alternative explanations
- Exploratory (hypothesis-generating)
- Inform future research

**Transparency:** Including non-significant results prevents publication bias

---

### 10. Why GitHub for Version Control?

**Decision:** Host code and data on GitHub repository

**Benefits:**
1. **Version control:** Track all changes, revert mistakes
2. **Collaboration:** Team members work asynchronously
3. **Transparency:** Public repository increases trust
4. **Reproducibility:** Others can clone and replicate
5. **Archival:** Persistent DOI via Zenodo integration

**Alternative (Dropbox/Google Drive) rejected:** No version control, hard to track changes

---

## Dependencies

### R Packages

| Package | Version | Purpose |
|---------|---------|---------|
| **readr** | 2.1.5 | Fast CSV reading with type inference |
| **dplyr** | 1.1.4 | Data manipulation (filter, mutate, summarize) |
| **ggplot2** | 3.5.1 | Grammar of graphics visualization |
| **stringr** | 1.5.1 | String manipulation (regex, extraction) |
| **scales** | 1.3.0 | Scale functions for ggplot2 (percent, comma) |
| **readxl** | 1.4.3 | Excel file reading (.xlsx) |
| **tibble** | 3.2.1 | Modern data frame structure |
| **tidyr** | 1.3.1 | Data tidying (pivot, nest) |
| **purrr** | 1.0.2 | Functional programming (map, iterate) |
| **knitr** | 1.48 | R Markdown code chunk execution |
| **rmarkdown** | 2.28 | R Markdown document compilation |

### System Requirements

- **Operating System:** Linux (Ubuntu 22.04), macOS, or Windows 10+
- **RAM:** 4 GB minimum, 8 GB recommended
- **Disk Space:** ~500 MB for data, packages, and outputs

---

## Team Contributions

### Meet Ghelani (2025201096)

**Responsibilities:**
- Data cleaning and preprocessing pipeline
- Participant exclusion criteria implementation
- RT outlier detection algorithm (Mean + 3 SD)
- Demographic data integration (merging CSVs with Excel)
- Data aggregation functions (participant_level, participant_frametype)

**Key Code Contributions:**
- `read_participant()` function (CSV reading with error handling)
- Participant exclusion logic (< 20 trials filter)
- RT cutoff calculation and filtering
- Demographic data merging pipeline

---

### Prateek Tiwari (2025201037)

**Responsibilities:**
- Statistical analysis implementation
- Hypothesis testing (4 primary Welch t-tests)
- Bonferroni correction calculation and application
- Effect size calculations (Cohen's d for all comparisons)
- Descriptive statistics computation (means, SDs, CIs)
- Demographic analysis (4 exploratory tests D1-D4)

**Key Code Contributions:**
- `cohens_d()` function (pooled SD calculation)
- Welch t-test implementations (t1, t2, t3, t4)
- Bonferroni alpha adjustment
- Demographic tests (age/gender balance, moderators)
- Results summary tables

---

### Pranjal Singh Katiyar (2025201079)

**Responsibilities:**
- Data visualization (all ggplot2 figures)
- Custom ggplot2 theme development (brsm_theme)
- Report generation and R Markdown formatting
- Literature review (Event Segmentation Theory, Boundary Advantage)
- Interpretation of results (all narrative text)
- GitHub repository management

**Key Code Contributions:**
- All ggplot2 visualizations (violin plots, heatmaps, bar charts)
- Custom color palettes (condition_colours, frametype_colours)
- R Markdown document structure (both full and condensed reports)
- LaTeX/PDF formatting fixes (Unicode character issues)
- README.md authoring

---

### Collaborative Work

All team members contributed to:
- Conceptual design and hypothesis formulation
- Experimental design understanding
- Interpretation of statistical findings
- Report writing and editing
- GitHub collaboration (commits, pull requests)
- Presentation preparation

---

## References

### Primary Sources

**Zacks, J. M., Speer, N. K., Swallow, K. M., Braver, T. S., & Reynolds, J. R. (2007).** Event perception: A mind-brain perspective. *Psychological Bulletin*, *133*(2), 273-293. https://doi.org/10.1037/0033-2909.133.2.273

- Original formulation of Event Segmentation Theory
- Describes predictive models and event boundaries
- Neural substrates of event segmentation

**Swallow, K. M., Zacks, J. M., & Abrams, R. A. (2009).** Event boundaries in perception affect memory encoding and updating. *Journal of Experimental Psychology: General*, *138*(2), 236-257. https://doi.org/10.1037/a0015631

- Demonstrates the Boundary Advantage Effect
- Shows enhanced memory at event boundaries vs middles
- Theoretical foundation for current study

---

### Methodological References

**Delacre, M., Lakens, D., & Leys, C. (2017).** Why psychologists should by default use Welch's t-test instead of Student's t-test. *International Review of Social Psychology*, *30*(1), 92-101. https://doi.org/10.5334/irsp.82

- Justification for Welch's t-test as default choice

**Hedge, C., Powell, G., & Sumner, P. (2018).** The reliability paradox: Why robust cognitive tasks do not produce reliable individual differences. *Behavior Research Methods*, *50*, 1166-1186. https://doi.org/10.3758/s13428-017-0935-1

- Discusses trial count requirements for reliable estimates

**Judd, C. M., Westfall, J., & Kenny, D. A. (2012).** Treating stimuli as a random factor in social psychology: A new and comprehensive solution to a pervasive but largely ignored problem. *Journal of Personality and Social Psychology*, *103*(1), 54-69. https://doi.org/10.1037/a0028347

- Compares aggregation vs mixed-effects approaches

**Wilson, G., Bryan, J., Cranston, K., Kitzes, J., Nederbragt, L., & Teal, T. K. (2017).** Good enough practices in scientific computing. *PLOS Computational Biology*, *13*(6), e1005510. https://doi.org/10.1371/journal.pcbi.1005510

- Best practices for reproducible research

---

## License

This project is released under the **MIT License** (open source, free to use with attribution).

---

## Contact

**GitHub Repository:** [https://github.com/PranjalSK03/BRSM_Project](https://github.com/PranjalSK03/BRSM_Project)

**Team Members:**
- Meet Ghelani (2025201096)
- Prateek Tiwari (2025201037)
- Pranjal Singh Katiyar (2025201079)

**Course:** BRSM (Behavioural Research & Statistical Methods)  
**Institution:** [Your University Name]  
**Semester:** Spring 2026

---

## Acknowledgments

- **Dr. [Instructor Name]** for course guidance and feedback
- **PsychoPy developers** for experimental software
- **R Core Team** and **Tidyverse contributors** for statistical computing tools
- Study participants for their time and attention

---

**Last Updated:** March 10, 2026

**Document Version:** 1.0
