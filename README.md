# Heterogeneous Effects of Broadband Internet Access on Health Outcomes: A Causal Forest Approach

Examining how broadband internet access affects population health across U.S. counties — using causal forests to uncover substantial variation that average treatment effects conceal.

---

## Overview

Most studies on broadband and health report a single average treatment effect. This project goes further by asking: **does broadband help everyone equally, or does it depend on who you are and where you live?**

Using data from approximately 3,000 U.S. counties, I apply **Causal Forests** — a machine learning method for estimating Conditional Average Treatment Effects (CATEs) — to reveal dramatic heterogeneity in broadband's health impact that traditional approaches miss entirely.

---

## Key Findings

- The **average treatment effect** of broadband on life expectancy is **-0.096 years** — seemingly modest
- But this masks variation ranging from **-2.0 to +0.5 years** across counties
- **Baseline health status** is the dominant predictor of who benefits and who doesn't:
  - Unhealthy counties experience significant **negative** effects
  - Healthy counties show **minimal** impact
- Broadband expansion alone is insufficient — complementary healthcare infrastructure investment is necessary for communities to benefit

---

## Results

### Distribution of Treatment Effects Across Counties
<img width="3000" height="1800" alt="image" src="https://github.com/user-attachments/assets/aace3dad-a7a7-4d63-9dd7-83e327296a78" />


### Baseline Health as Predictor of Heterogeneity
<img width="3000" height="1800" alt="image" src="https://github.com/user-attachments/assets/c49f96db-6cdd-49d6-8142-cd046ac700d7" />


### Variable Importance
<img width="3000" height="1800" alt="image" src="https://github.com/user-attachments/assets/d91e6ba7-3c38-4dee-a193-e00f37812a80" />


---

## Methods

### Why Causal Forests?

Standard regression estimates one average effect for everyone. Causal Forests (Wager & Athey, 2018) adapt Random Forests to estimate individualized treatment effects by:

1. Building trees that maximize heterogeneity in treatment effects (not just prediction accuracy)
2. Using honesty — splitting data so treatment effect estimation is unbiased
3. Providing valid confidence intervals for each county's estimated effect

### Data

- **Source:** ~3,000 U.S. counties
- **Treatment:** Broadband internet access rate
- **Outcome:** Life expectancy / population health metrics
- **Covariates:** Demographics, socioeconomic status, baseline health indicators, geography

### Analysis Pipeline

```
Data Loading & Cleaning
        ↓
Covariate Selection & Preprocessing
        ↓
Causal Forest Training (grf package)
        ↓
CATE Estimation per County
        ↓
Heterogeneity Analysis & Variable Importance
        ↓
Visualization & Interpretation
```

---

## Tech Stack

**Language:** R

**Packages:**
- `grf` — Generalized Random Forests for causal inference
- `ggplot2` — Visualization
- `dplyr`, `tidyr` — Data wrangling
- `tidycensus` / county-level data sources

---

## Repository Structure

```
├── analysis.Rmd       # Full analysis: data prep, modeling, results
├── figures/           # Output plots and visualizations
└── README.md
```

---

## Getting Started

### Prerequisites
- R 4.0+
- RStudio (recommended)

### Clone the repo
```bash
git clone https://github.com/pradeep-maripala/causal-forest-broadband-health.git
cd causal-forest-broadband-health
```

### Install R dependencies
```r
install.packages(c("grf", "ggplot2", "dplyr", "tidyr"))
```

### Run the analysis
Open `analysis.Rmd` in RStudio and knit the document.

---

## References

- Wager, S., & Athey, S. (2018). Estimation and inference of heterogeneous treatment effects using random forests. *Journal of the American Statistical Association.*
- Tibshirani, J., Athey, S., & Wager, S. (2022). grf: Generalized Random Forests. R package.

---

## Author

**Pradeep Maripala**
MS Data Science, University of Iowa
[LinkedIn](https://www.linkedin.com/in/maripala-pradeep-13425b211/) | [Email](mailto:maripalapradeep27@gmail.com)
