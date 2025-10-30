## **Cuasal Machine Learning - Colorectal Cancer Drug Response Prediction**

---
**Problem Statement**
---

Colorectal cancer (CRC) is among the leading causes of cancer deaths worldwide.
Despite breakthroughs in checkpoint blockade, most colorectal cancers remain resistant to chemotherapy. Yet, conventional chemotherapies (e.g., 5-FU, FOLFOX, oxaliplatin) can elicit immunogenic cell death (ICD) and alter the tumor immune microenvironment (TIME). However, responses vary widely between patients and are partly determined by genomic and immunologic heterogeneity. Chemotherapy with folfox(oxaliplatin, leucovorin, fluorouracil) remains a standard treatment, while fluorouracil(5-FU), oxaliplatin are also used.

key problems with chemotherapy treatment
1. Response to treatment varies widely from patient to patient
2. Genetic biomarkers may determine which patients benefit
3. Patients may get toxicity without therapeutic gain
4. There is no universal best therapy

What is the causal effect of each chemotherapy option on patient outcomes, and how does that vary by genetic profile?

___
**Goals**
___

We aim to build and validate a causal machine learning system that personalizes first-line chemotherapy regimens for colorectal cancer patients by estimating individual causal effects of alternative regimens (e.g., FOLFOX vs 5-FU) on clinically meaningful outcomes (e.g., overall survival, and treatment response). The system will: (a) control for confounding using robust nuisance-modeling (propensity + outcome models), (b) deliver unbiased average treatment effect estimates with valid confidence intervals, (c) discover heterogeneity in treatment effects for personalized treatment recommendations. Such models could guide oncologists in personalizing chemotherapy regimens, improving survival outcomes, and minimizing unnecessary toxicity.

Component	Role

Treatment	3 arms: 5-FU vs. Oxaliplatin vs. FOLFOX

Confounders	Genetics, Clinical features

Outcome 	Response or Survival metric


Modeling goal: ITEi​(t1​,t2​)=Yi​(t1​)−Yi​(t2​)



CML enables

-Counterfactual inference (what would happen with vs. without treatment)

-Heterogeneous treatment effect estimation (HTE)

-Treatment recommendation based on expected uplift in survival probability



Dataset:  https://zenodo.org/records/3719291


---
**Methodology**
___

        ┌────────────────────────────────────────┐
        │ Clinical Problem Formulation           │
        │ • Define estimand (ATE, CATE, ITE)     │
        │ • Treatment groups & outcomes          │
        └───────────────────────────────┬────────┘
                                        │
                          (Causal Assumptions: Ignorability,
                           Positivity, Consistency/SUTVA)
                                        │
        ┌───────────────────────────────▼───────────────────────────┐
        │ Data Integration & Cohort Construction                    │
        │ • Merge multi-treatment datasets                          │
        │ • Assign treatment indicator (T)                          │
        │ • Split Train/Test BEFORE causal modeling                 │
        └───────────────────────────────┬───────────────────────────┘
                                        │
        ┌───────────────────────────────▼───────────────────────────┐
        │ Preprocessing                                                  │
        │ • Missing data imputation                                      │
        │ • Feature scaling/encoding (600+ genomics)                     │
        │ • Remove leakage variables / reduce dimensionality            │
        └───────────────────────────────┬───────────────────────────┘
                                        │
        ┌───────────────────────────────▼───────────────────────────┐
        │ Propensity Score Estimation                                 │
        │ • Logistic/GBM/Random Forest                                │
        │ • Compute IPTW / Stabilized weights                         │
        │ → Check Covariate Balance (SMD, Overlap plots)              │
        └───────────────────────────────┬───────────────────────────┘
                                        │
        ┌───────────────────────────────▼───────────────────────────┐
        │ Causal ML Outcome Modeling                                  │
        │ • DR-Learner OR Causal Forest                               │
        │ • Estimate factual outcomes + pseudo-outcomes               │
        │ → Predict Individual Treatment Effect (ITE)                 │
        └───────────────────────────────┬───────────────────────────┘
                                        │
        ┌───────────────────────────────▼───────────────────────────┐
        │ Effect Estimation & Interpretation                          │
        │ • ATE, CATE, ITE with Confidence Intervals                  │
        │ • Gene signatures & subgroup discovery                      │
        │ • Uplift curves / ICE plots                                 │
        └───────────────────────────────┬───────────────────────────┘
                                        │
        ┌───────────────────────────────▼───────────────────────────┐
        │ Causal Evaluation & Validation                              │
        │ • Policy Risk, PEHE proxy                                   │
        │ • Sensitivity (Rosenbaum bounds)                            │
        │ • Positivity durability check                               │
        └───────────────────────────────┬───────────────────────────┘
                                        │
                          ┌─────────────▼──────────────┐
                          │ Clinical Decision Support   │
                          │ • Patient-level benefit     │
                          │ • Recommended treatment     │
                          │ • Confidence reporting      │
                          └────────────────────────────┘


---
References
---
