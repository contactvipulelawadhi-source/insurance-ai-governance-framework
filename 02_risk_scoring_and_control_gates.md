# Insurance AI Risk Tiering Methodology & Governance Control Gates

## 1. Risk Scoring Rubric (1 to 5 Scale)
Each submitted AI use case is scored across four weighted risk dimensions:

| Dimension | Weight | Score 1 (Minimal) | Score 3 (Moderate) | Score 5 (Critical) |
| :--- | :--- | :--- | :--- | :--- |
| **1. Policyholder Impact** | **35%** | Internal staff productivity only; zero policyholder impact. | Influences marketing, retention offers, or claim routing speed. | Directly determines underwriting eligibility, premium pricing, or claim denial. |
| **2. Regulatory & Legal Exposure** | **30%** | No sector-specific AI regulation applies. | Subject to general consumer protection & privacy laws (GDPR/DPDP). | Explicitly regulated under **EU AI Act Annex III** (Life/Health Risk) or **NAIC AI Bulletin**. |
| **3. Data Sensitivity & Lineage** | **20%** | Uses public or anonymized synthetic data. | Uses internal non-medical customer metadata with verified lineage. | Ingests PHI, medical history, credit scores, or third-party external data. |
| **4. Model Complexity & Autonomy** | **15%** | Transparent rules/linear model with mandatory human sign-off. | Complex ML/RAG with human review before external communication. | Black-box ensemble or autonomous GenAI executing binding decisions. |

**Composite Risk Score Formula:**
$$\text{Total Score} = (0.35 \times \text{Impact}) + (0.30 \times \text{Regulatory}) + (0.20 \times \text{Data}) + (0.15 \times \text{Autonomy})$$

### Risk Tier Thresholds & Automatic Overrides
* **Tier 1 — High Risk (Score 3.8 – 5.0):** *Automatic Override:* Any model used for Life/Health underwriting, pricing, or automated claim denial is automatically classified as **Tier 1** regardless of composite score.
* **Tier 2 — Medium Risk (Score 2.5 – 3.7):** Moderate customer impact or high data sensitivity with strong human oversight.
* **Tier 3 — Low Risk (Score 1.6 – 2.4):** Internal decision-support tools or GenAI assistants using approved internal knowledge bases.
* **Tier 4 — Minimal Risk (Score 1.0 – 1.5):** Internal developer/actuarial productivity tools with zero PII/PHI.

---

## 2. Mandatory Pre-Deployment Control Gates (NIST AI RMF Mapped)

| Governance Control Requirement | NIST AI RMF Function | Tier 1 (High) | Tier 2 (Medium) | Tier 3 (Low) | Tier 4 (Minimal) |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **Use-Case Registration in Enterprise Inventory** | `GOVERN` | Mandatory | Mandatory | Mandatory | Mandatory |
| **Column-Level Data Lineage & Retention-by-Design Sign-Off** | `MAP` | Mandatory | Mandatory | Mandatory | Optional |
| **PHI/PII Masking & Access Control Verification (IAM)** | `GOVERN / MAP` | Mandatory | Mandatory | Mandatory | N/A |
| **Actuarial Fairness & Proxy Discrimination Audit** | `MEASURE` | Mandatory | Conditional | N/A | N/A |
| **Local Explainability (SHAP / Adverse Action Reason Codes)** | `MEASURE` | Mandatory | Mandatory | N/A | N/A |
| **Hallucination / Groundedness Threshold Check (GenAI)** | `MEASURE` | Mandatory | Mandatory | Mandatory | N/A |
| **Mandatory Human-in-the-Loop (HITL) Override Logging** | `MANAGE` | Mandatory | Mandatory | Optional | N/A |
| **Automated Production Drift & Bias Monitoring** | `MANAGE` | Monthly | Quarterly | Semi-Annual | N/A |
| **Final Production Sign-Off Authority** | `GOVERN` | **AI Risk Committee + Chief Actuary** | **2nd-Line Model Risk Lead** | **Data & AI Governance Lead** | **Business Unit Owner** |
