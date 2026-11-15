# Insurance AI & ML Use-Case Intake Questionnaire

**Instructions:** All internal AI/ML models and third-party vendor AI tools must complete this intake assessment prior to accessing staging/production data or deploying to production.

## Section A: Basic Identification
* **Use-Case Name:** [e.g., Automated Life Underwriting Triage v1.0]
* **Business Unit / Owner:** [e.g., Life Underwriting / Claims / Fraud SIU]
* **Technical Lead:** [Name & Team]
* **Model Type:** [ ] Predictive ML (Tabular)  [ ] NLP / Text Classification  [ ] Generative AI / LLM  [ ] Third-Party Vendor SaaS
* **Insurance Value-Chain Stage:** [ ] Underwriting & Pricing  [ ] Claims Adjudication  [ ] Fraud / SIU  [ ] Policy Servicing  [ ] Internal Operations

## Section B: Customer Impact & Decision Autonomy (EU AI Act & NAIC Alignment)
1. **Does this model evaluate risk, eligibility, or premium pricing for Life or Health insurance?** *(Triggers EU AI Act Annex III High-Risk classification)*
   * [ ] Yes  [ ] No
2. **How are the model's outputs used in decision-making?**
   * [ ] **Fully Automated Decisioning:** System approves, prices, or denies without human intervention.
   * [ ] **Human-in-the-Loop (HITL) — Approval Required:** Model recommends an outcome; a licensed underwriter/adjuster must approve before action.
   * [ ] **Human-on-the-Loop (HOTL) — Informational Only:** Model summarizes data or flags insights; human makes the independent decision.
3. **Could an incorrect or biased output result in financial loss, coverage denial, or delayed medical/claim payout to a policyholder?**
   * [ ] High Impact  [ ] Moderate Impact  [ ] Low / No Customer Impact

## Section C: Data Sensitivity, Privacy & Proxy Risk
4. **Which data categories are used for training, fine-tuning, or inference?** *(Check all that apply)*
   * [ ] Protected Health Information (PHI) / Medical Records / Lab Results
   * [ ] Personally Identifiable Information (PII — SSN, Policy ID, Name, DOB)
   * [ ] Financial / Credit / Income Data
   * [ ] Telematics / IoT / Wearable Behavioral Data
   * [ ] Third-Party External Data Brokers (Social, Lifestyle, Geospatial)
   * [ ] Non-Sensitive Internal Policy Documents / Public Data Only
5. **Does the model ingest potential proxy variables for protected classes?** *(e.g., Zip/Postal Code, Occupation, Education Level, Marital Status, Credit-Based Insurance Score)*
   * [ ] Yes (List variables: __________________)  [ ] No
6. **Is column-level data lineage documented and are automated data retention/purge schedules enforced?**
   * [ ] Yes (Link to AWS Glue / Data Catalog lineage)  [ ] No — Remediation Required

## Section D: Generative AI Specifics (Complete Only if Using LLMs)
7. **Does the LLM retrieve or process policyholder PII/PHI in prompts?**
   * [ ] Yes — Automated PII redaction enabled  [ ] Yes — Unmasked (Blocked)  [ ] No
8. **Is the output exposed directly to policyholders/agents without human review?**
   * [ ] Yes  [ ] No
