_**Cuasal Machine Learning - Colorectal Cancer Drug Response Prediction**_

**Problem Statement**

Colorectal cancer (CRC) is among the leading causes of cancer deaths worldwide.
Chemotherapy with 5-Fluorouracil (5-FU) remains a standard treatment, yet response rates vary widely; some patients benefit significantly, while others suffer toxicity without real therapeutic gain. Despite advances, predicting which patients will respond to different drugs
fluorouracil(5-FU), oxaliplatin, folfox(oxaliplatin, leucovorin, fluorouracil) remains a key challenge in oncology.


We aim to build and validate a causal machine learning system that personalizes first-line chemotherapy regimens for colorectal cancer patients by estimating individual causal effects of alternative regimens (e.g., FOLFOX vs 5-FU) on clinically meaningful outcomes (e.g., overall survival, progression-free survival, or treatment response). The system will: (a) control for confounding using robust nuisance-modeling (propensity + outcome models), (b) deliver unbiased average treatment effect estimates with valid confidence intervals, (c) discover heterogeneity in treatment effects for personalized treatment recommendations. Such models could guide oncologists in personalizing chemotherapy regimens, improving survival outcomes, and minimizing unnecessary toxicity.


Causal Machine Learning(ML) can help us understand the effects of treatment interventions, hence improving the accuracy and interpretability of models. Causal machine learning (CML) enables individualized estimation of treatment effects, offering critical advantages over traditional correlation-based methods.

Dataset:  https://zenodo.org/records/3719291
---
**Project Objectives**

- Build predictive and causal models to identify patients most likely to respond to 5-FU, Oxaliplatin, or FOLFOX
- Integrate clinical + gene expression (molecular) data to improve personalization
- Estimate Individualized Treatment Effects (ITE) to support treatment-specific decisions
- Provide interpretability using SHAP, Causal SHAP, and feature influence on treatment effects
- Deploy a prototype clinical decision support app for oncologis

---
CML enables

-Counterfactual inference (what would happen with vs. without treatment)

-Heterogeneous treatment effect estimation (HTE)

-Treatment recommendation based on expected uplift in survival probability

---
Methods:

-Propensity Score Modeling

-Doubly Robust Learners (DR-Learner)

-Causal Forests / Uplift Random Forest

-X-Learner, S-Learner, T-Learner

---
Refrence

