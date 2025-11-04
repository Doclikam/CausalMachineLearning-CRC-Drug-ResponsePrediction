## **Causal Effects of Concurrent Chemoradiotherapy vs Radiotherapy Alone in Head & Neck Cancer- Survival Outcome**

---
**Problem Statement**
---
What is the causal effect of adding chemotherapy
to radiotherapy at baseline on overall survival
in real-world head & neck cancer patients?


### Primary Estimand (Part 1 — Baseline Total Effect)

We estimate the **total effect** of treatment \(A\) on survival \(Y\):

\[
\TE{ATE} = E[Y^{A=1}] - E[Y^{A=0}]
\]

Operationalized as a hazard ratio via IPTW-weighted Cox regression:

\[
HR = \frac{\lambda(t \mid A=1)}{\lambda(t \mid A=0)}
\]

Where:
- \( A = 1 \): concurrent ChemoRT
- \( A = 0 \): RT-alone
- \( Y \): time-aligned overall survival (OS)

### Secondary Estimand (Part 2 — Dynamic Treatment Strategies)

Radiation dose and fractionation evolve over time and are influenced by chemotherapy. We model time-varying regimen effects using Marginal Structural Models (MSMs):

\[
E[Y^{\bar{a}}]
\]
under hypothetical delivered treatment policies \(\bar{a}_t\)
___
**Goals**
___

## 3. Causal Model (DAG)

A["Tumor Severity (TNM, Stage)"] --> T["ChemoRT Decision"]
B["HPV & Primary Site"] --> T
C["Smoking, Age, Sex, ECOG"] --> T
T --> M["Delivered RT Dose / Fractions"]
A --> Y["Overall Survival"]
B --> Y
C --> Y
M --> Y

**CML enables**

-Counterfactual inference (what would happen with vs. without treatment)

-Heterogeneous treatment effect estimation (HTE)

-Treatment recommendation based on expected uplift in survival probability

### Causal Assumptions

| Assumption | Definition | How Verified |
|-----------|------------|--------------|
| Exchangeability | No unmeasured confounding | Domain-validated covariates + missingness modeling |
| Positivity | All strata have both treatments | Propensity overlap diagnostics |
| Consistency | Well-defined exposure | Binary, time-aligned intervention |
| Correct model | PS & outcome well-specified | Model diagnostics + sensitivity analyses |
---
**Methodology**
___
We use the **RADCURE** clinical dataset (N > 3,400), a multi-institutional real-world registry of head and neck cancer patients treated with radiotherapy.

Collected variables include:
- Baseline demographics and risk factors
- Tumor site and staging (TNM, AJCC Stage)
- HPV status where clinically relevant
- Treatment details (start date, chemotherapy administration)
- Survival outcomes (death, last follow-up, recurrence)

---
### 4.2 Time Zero and Survival Outcome Construction
To avoid immortal-time bias, **time zero** is set to the **start of radiotherapy** (`RT Start`).  
Overall Survival (OS) is defined as:

```math
OS_i = \text{date\_of\_death}_i - \text{RT\_start}_i
