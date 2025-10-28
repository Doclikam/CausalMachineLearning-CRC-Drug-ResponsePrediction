_**Colorectal Cancer Drug Response Prediction**_


**Problem Statement**

Colorectal cancer (CRC) is among the leading causes of cancer deaths worldwide.
Chemotherapy with 5-Fluorouracil (5-FU) remains a standard treatment, yet response rates vary widely, some patients benefit significantly, while others suffer toxicity without real therapeutic gain.Despite advances, predicting which patients will respond to different drugs
fluorouracil(5-FU), oxaliplatin, folfox(oxaliplatin, leucovorin, fluorouracil) remains a key challenge in oncology.


There is a critical need for predictive models that can identify patients who are most likely to respond to 5-FU based on their clinical and molecular (gene expression) profiles. Such models could guide oncologists in personalizing chemotherapy regimens, improving survival outcomes, and minimizing unnecessary toxicity.

Causal Machine Learning(ML) can improve help us understand the effects of treatment interventions; hence improving the accuracy and intepretability of models. We can use causal effects to identify how patients and disease characteristics influence the treatment effectiveness. Causal machine learning (CML) enables individualized estimation of treatment effects, offering critical advantages over traditional correlation-based methods.

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
Methods used include:

-Propensity Score Modeling

-Doubly Robust Learners (DR-Learner)

-Causal Forests / Uplift Random Forest

-X-Learner, S-Learner, T-Learner
**References**
-

