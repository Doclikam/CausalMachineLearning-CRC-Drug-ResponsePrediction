## **Causal Effects of Concurrent Chemoradiotherapy vs Radiotherapy Alone in Head & Neck Cancer- Survival Outcome**
---

Head and Neck Cancers (HNCs) account for > 900,000 cases and ~500,000 deaths annually worldwide. Radiotherapy (RT) is a foundational treatment. treatment strategy remains a challenge. More than two-third of head and neck cancer patients require radiation therapy, which can be given either alone or concurrently with chemotherapy. However, many patients receive chemoradiotherapy (ChemoRT), adding systemic chemotherapy to improve tumor control. Radiotherapy (RT) forms the cornerstone of curative treatment for locally advanced disease. In many patients, particularly those with aggressive tumor biology or advanced nodal involvement((T,N,M stage) chemotherapy is added concurrently with radiotherapy (chemoradiotherapy, ChemoRT) with the aim of enhancing tumor cytotoxicity.

While randomized trials suggest benefit in select populations, real-world treatment practices differ substantially: variations in tumor site, HPV status, smoking behavior, disease staging, and health system factors all influence whether chemotherapy is administered. Chemotherapy also carries major toxicity: swallowing impairment, organ injury, hospitalization, and long-term disability. 

Thus, the clinical dilemma persists:

**Does adding chemotherapy to radiotherapy improve survival for real-world patients for whom does it help or harm?**

This is a counterfactual question: what would have happened to the same patient had they received the alternative treatment? Traditional machine learning cannot answer this:  correlation is not causation, making causal inference essential.

---
## Objective
---
-To estimate Overall treatment effect (ATE)

- To estimate Individualized effects (CATE)

- To estimate Time-varying treatment effects

- To estimate Survival differences between RT and ChemoRT

### Primary Estimand (Part 1 — Baseline Total Effect)

We estimate the **total effect** of treatment \(A\) on survival \(Y\):
We define the Average Treatment Effect (ATE) as:

{ATE} = E[Y^{A=1}] - E[Y^{A=0}]

where:

Y(1) represents survival time had all patients received ChemoRT, and

Y(0) represents survival time had all patients received RT alone.

### Secondary Estimand (Part 2 — Dynamic Treatment Strategies)

Radiation dose and fractionation evolve over time and are influenced by chemotherapy. We model time-varying regimen effects using Marginal Structural Models (MSMs)
(CATE) for a patient with covariates X=xX = xX=x is:
CATE(x)=E[Y(1)−Y(0)∣X=x]
Where:
Y(1)Y(1)Y(1) = potential outcome if treated


Y(0)Y(0)Y(0) = potential outcome if untreated

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


<img width="1024" height="768" alt="DAG Flowchart Diagram Template (1)" src="https://github.com/user-attachments/assets/a5466bd8-1211-4cb9-8cf6-2b570820c9ca" />


---
## Methodology
___
We use the **RADCURE** clinical dataset (N > 3,400), a multi-institutional real-world registry of head and neck cancer patients treated with radiotherapy alone, radiotherapy+chemotherapy and radiotherapy+EGFRI
https://www.cancerimagingarchive.net/collection/radcure/

Collected variables include:
- Baseline demographics and risk factors
- Tumor site and staging (TNM, AJCC Stage)
- HPV status where clinically relevant
- Treatment details (start date, chemotherapy administration)
- Survival outcomes (death, last follow-up, recurrence)
<img width="1024" height="1536" alt="Methodologyworkflow Image Nov 14, 2025, 09_52_33 AM" src="https://github.com/user-attachments/assets/0e93321a-019d-470e-85dd-17c580233941" />






