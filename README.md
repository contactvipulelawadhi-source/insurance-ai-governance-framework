# Insurance AI Governance, Risk Tiering & Assurance Framework

An enterprise-ready AI governance and model risk management (MRM) toolkit tailored specifically for **Life, Health, and P&C Insurance** environments. 

## Why This Framework Exists
In insurance, AI governance goes beyond generic IT security. Regulators—under the **EU AI Act (Annex III)**, **NAIC Model Bulletin on AI Systems**, and **NIST AI RMF 1.0**—specifically scrutinize:
1. **High-Risk Underwriting & Pricing:** AI systems evaluating life/health risk or setting premiums face strict regulatory obligations around explainability and human oversight.
2. **Proxy Discrimination:** Ensuring models do not indirectly discriminate against protected classes via correlated variables (e.g., postal codes, credit scores, lifestyle brokers).
3. **PHI & Lineage Integrity:** Enforcing privacy-by-design, retention schedules, and column-level lineage across cloud data platforms before sensitive claims or medical data enters ML pipelines.

## Repository Structure
* **[01_insurance_ai_intake_form.md](./01_insurance_ai_intake_form.md):** Standardized pre-development intake form capturing decision autonomy, PHI/PII exposure, proxy variables, and GenAI risks.
* **[02_risk_scoring_and_control_gates.md](./02_risk_scoring_and_control_gates.md):** Weighted 4-dimension risk scoring rubric, automatic High-Risk overrides, and mandatory pre-deployment control gates mapped to **NIST AI RMF** (`Govern, Map, Measure, Manage`).
* **[03_insurance_ai_use_case_inventory.csv](./03_insurance_ai_use_case_inventory.csv):** Sample enterprise AI registry demonstrating risk classification across six real-world insurance use cases (Underwriting, Claims STP, Fraud SIU, Retention, and Policy RAG).

## Governance Workflow
```text
[1. Business/Actuarial Intake] 
       │
       ▼
[2. Automated Risk Scoring & EU AI Act / NAIC Override Check]
       │
       ├──► Tier 1 (High Risk) ───► Proxy Bias Audit + SHAP Explainability + PHI Lineage + Chief Actuary Sign-Off
       ├──► Tier 2 (Medium Risk) ─► HITL Override Logging + Drift Monitoring + 2nd-Line Risk Sign-Off
       └──► Tier 3/4 (Low/Min) ───► PII Redaction Guardrails + Prompt Audit Logs + Governance Lead Sign-Off
