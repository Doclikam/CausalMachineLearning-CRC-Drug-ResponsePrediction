## **Causal Effects of Concurrent Chemoradiotherapy vs Radiotherapy Alone in Head & Neck Cancer- Survival Outcome**
---

Head and Neck Cancers (HNCs) account for > 900,000 cases and ~500,000 deaths annually worldwide. Radiotherapy (RT) is a foundational treatment. However, many patients receive chemoradiotherapy (ChemoRT), adding systemic chemotherapy to improve tumor control. Radiotherapy (RT) forms the cornerstone of curative treatment for locally advanced disease. In many patients, particularly those with aggressive tumor biology or advanced nodal involvement((T,N,M stage) chemotherapy is added concurrently with radiotherapy (chemoradiotherapy, ChemoRT) with the aim of enhancing tumor cytotoxicity.

While randomized trials suggest benefit in select populations, real-world treatment practices differ substantially:
variations in tumor site, HPV status, smoking behavior, disease staging, and health system factors all influence whether chemotherapy is administered. Chemotherapy also carries major toxicity: swallowing impairment, organ injury, hospitalization, and long-term disability. 

Thus, the clinical dilemma persists:

**Does adding chemotherapy to radiotherapy improve survival for real-world patients for whom does it help or harm?**

This is a counterfactual question: what would have happened to the same patient had they received the alternative treatment? Traditional machine learning cannot answer this:  correlation is not causation, making causal inference essential.

---
## Objective
---
- To estimate the causal effect of adding chemotherapy to radiotherapy on overall survival in head and neck cancer patients treated in routine clinical practice, using the RADCURE multi-institutional cohort.
- To personalize oncology decisions
- To enhance safer treatment pathways
- To provide cost-effective cancer care

### Primary Estimand (Part 1 — Baseline Total Effect)

We estimate the **total effect** of treatment \(A\) on survival \(Y\):
We define the Average Treatment Effect (ATE) as:

{ATE} = E[Y^{A=1}] - E[Y^{A=0}]

where:

Y(1) represents survival time had all patients received ChemoRT, and

Y(0) represents survival time had all patients received RT alone.

### Secondary Estimand (Part 2 — Dynamic Treatment Strategies)

Radiation dose and fractionation evolve over time and are influenced by chemotherapy. We model time-varying regimen effects using Marginal Structural Models (MSMs):

---
## Causal Framework
---
Confounder :A variable that causes both the treatment and the outcome

Conditional Exchangeability:
Given baseline confounders 𝑋 treatment assignment 𝐴 is independent of potential outcomes:

                                        Y(a)⊥A∣X

Positivity:
Every combination of confounders must have a non-zero probability of receiving either treatment.

Consistency (SUTVA):
Each patient’s outcome corresponds to the treatment they received, with no interference across patients.


To justify these assumptions, we developed a Directed Acyclic Graph (DAG) summarizing our causal model:

Tumor Severity ────────► Treatment (ChemoRT)
     │                    │  ▲
     │                    │  │
     └────────► Biological Effect (HPV) ───► Survival
     │
     └────► Health Status (ECOG) ─────────► Survival
     │
     └────► Smoking / Demographics ───────► Survival


---
## Methodology
___
We use the **RADCURE** clinical dataset (N > 3,400), a multi-institutional real-world registry of head and neck cancer patients treated with radiotherapy alone, radiotherapy+chemotherapy and radiotherapy+EGFRI

Collected variables include:
- Baseline demographics and risk factors
- Tumor site and staging (TNM, AJCC Stage)
- HPV status where clinically relevant
- Treatment details (start date, chemotherapy administration)
- Survival outcomes (death, last follow-up, recurrence)

---
**Time Zero and Survival Outcome Construction**

To avoid immortal-time bias, **time zero** is set to the **start of radiotherapy** (`RT Start`).  
Overall Survival (OS) is defined as:

```math
OS_i = \text{date\_of\_death}_i - \text{RT\_start}_i
