
---

# BISO Glossary 

**What this is:** a practical, business-focused glossary for a **Business Information Security Officer (BISO)** — the bridge between C-suite and security/engineering. It blends terms from cybersecurity, risk, finance, strategy, privacy, legal/compliance, and operations. Definitions use **American English** and prefer globally recognized nomenclature.

**How it was compiled:** synthesis of leading frameworks, standards, and industry literature, including (non-exhaustive): NIST (CSF 2.0; SP 800-53/-61/-171), ISO/IEC 27001/27002, COBIT, CIS Controls v8, AICPA Trust Services Criteria (SOC 2), PCI DSS, FFIEC handbooks, CISA guidance, MITRE ATT\&CK/D3FEND, ISACA/FAIR Institute materials, ITIL 4, major US regulations (HIPAA, GLBA Safeguards, SOX, CCPA/CPRA, SEC cyber-disclosure), vendor/cloud shared-responsibility docs, and standard finance/strategy texts (e.g., P\&L, EBITDA, ROI, TCO, NPV). Also considered: **user-provided finance primers** for P\&L/ROI/EBITDA context.

**How to use it:** scan by section; examples are included where they clarify executive conversations.

---

## 1) Governance, Risk & Strategy

1. **Corporate Governance** — system of rules, practices, and processes by which a company is directed and controlled; sets tone for risk, compliance, and security prioritization.
   *Example:* Board Risk Committee charters include cyber oversight.

2. **Risk Appetite** — the amount and type of risk an organization is willing to pursue or retain to meet objectives.

3. **Risk Tolerance** — acceptable deviation from appetite for specific metrics (e.g., “≤ 1 critical data loss incident/year”).

4. **Risk Capacity** — maximum risk the enterprise can absorb before threatening viability (financial/operational constraints).

5. **Three Lines Model** — governance model: (1) business ownership/management, (2) risk/compliance oversight (incl. security), (3) independent assurance (internal audit).

6. **Enterprise Risk Management (ERM)** — coordinated approach to identifying, assessing, responding to, and monitoring enterprise risks.

7. **GRC (Governance, Risk, and Compliance)** — integrated processes/tools to align policies, risks, and controls with business objectives.

8. **Inherent Risk** — risk level absent any controls.

9. **Residual Risk** — risk remaining after controls.
   *Example:* Phishing residual risk after MFA and training.

10. **Control Objective** — desired outcome of a control (e.g., “only authorized users access PHI”).

11. **Compensating Control** — alternative control providing equivalent protection when a prescribed control is infeasible.

12. **Risk Register** — authoritative log of risks, owners, ratings, and treatments.

13. **Risk Treatment** — **avoid**, **reduce/mitigate**, **transfer/share** (e.g., insurance), or **accept**.

14. **Business Impact Analysis (BIA)** — identifies critical processes, dependencies, and impacts, informing RTO/RPO.

15. **Strategic Alignment** — ensuring security initiatives directly support business goals/KPIs (revenue protection, growth enablement).

---

## 2) Cybersecurity Frameworks & Control Baselines

16. **NIST CSF 2.0** — US-centric cybersecurity framework organized by **Identify-Protect-Detect-Respond-Recover** (plus governance), mapping to controls and outcomes.

17. **NIST SP 800-53** — control catalog for federal/regulated environments; families like AC (Access Control), AU (Audit), SC (System and Communications Protection).

18. **NIST SP 800-171** — requirements for protecting Controlled Unclassified Information (CUI) in non-federal systems.

19. **CMMC** — maturity model aligning with NIST 800-171 for US defense suppliers.

20. **ISO/IEC 27001** — certifiable ISMS standard; **27002** details controls (Annex A themes like IAM, crypto, supplier security).

21. **COBIT** — governance framework for enterprise IT; focus on value delivery and assurance.

22. **CIS Controls v8** — prioritized safeguards (“basic/ foundational/ organizational”).

23. **MITRE ATT\&CK** — adversary tactics/techniques knowledge base used for detection engineering and threat-informed defense.

24. **MITRE D3FEND** — countermeasure knowledge graph mapping to ATT\&CK.

25. **SOC 2 (Trust Services Criteria)** — AICPA attestation over **Security, Availability, Processing Integrity, Confidentiality, Privacy** (Type I vs Type II).

26. **PCI DSS** — payment-card security standard for entities storing/processing/transmitting cardholder data.

---

## 3) Security Architecture, Operations & Metrics

27. **Zero Trust** — “never trust, always verify”; continuous authz; micro-segmentation; data-centric controls.

28. **PoLP (Principle of Least Privilege)** — grant minimum necessary access.

29. **Defense-in-Depth** — layered controls across people, process, technology.

30. **SDLC / **S**SDLC** — (Secure) Software Development Life Cycle integrating security from design to deployment.

31. **SAST / DAST / IAST / RASP** — static/dynamic/interactive app testing; runtime self-protection.

32. **SBOM** — Software Bill of Materials; inventory of components for vulnerability/transparency.

33. **EDR / XDR** — endpoint/extended detection & response; correlates telemetry across hosts, network, identity, cloud.

34. **SIEM** — Security Information & Event Management; log aggregation, correlation, alerting.

35. **SOAR** — Security Orchestration, Automation & Response; playbooks to standardize/automate actions.

36. **UEBA** — User and Entity Behavior Analytics; anomaly detection.

37. **MTTD / MTTR** — Mean Time to Detect/Respond; key operational KPIs.

38. **CVSS** — Common Vulnerability Scoring System; standard severity rating for vulns.

39. **Vulnerability Management (VM)** — continuous discover-assess-remediate cycle.

40. **Patch Management** — prioritized application of updates based on risk.

41. **Configuration Baseline / Hardening** — secure configurations (e.g., CIS Benchmarks).

42. **Red Team / Purple Team** — adversary emulation; collaborative blue-red improvement.

---

## 4) Identity, Access & Data Protection

43. **IAM** — Identity & Access Management: provisioning, authn/authz, lifecycle.

44. **IdP** — Identity Provider; issues/validates credentials and tokens.

45. **SSO** — Single Sign-On; centralized authentication across apps.

46. **MFA** — Multi-Factor Authentication (e.g., FIDO2/WebAuthn, TOTP).

47. **SAML / OAuth 2.0 / OIDC** — federation and delegated auth standards (SAML assertions; OAuth tokens; OIDC adds identity layer).
    *Example:* B2B SAML for SaaS; consumer OIDC via OAuth 2.0.

48. **PAM** — Privileged Access Management; vaulting, session control, just-in-time access.

49. **CIEM** — Cloud Infrastructure Entitlement Management; governs cloud permissions at scale.

50. **DLP** — Data Loss Prevention; detects/prevents unauthorized data movement.

51. **Tokenization / Encryption (at rest/in transit)** — data protection techniques; leverage KMS/HSM for key control.

52. **Data Classification** — labeling by sensitivity (Public, Internal, Confidential, Restricted).

53. **PII / PHI / PCI Data** — personal, health, and cardholder data categories with specific obligations.

54. **Data Minimization** — collect/retain only what’s needed for stated purposes.

---

## 5) Cloud, SaaS & Modern Infra

55. **Shared Responsibility Model** — delineates provider vs customer duties (varies by IaaS/PaaS/SaaS).

56. **CSPM / CWPP / CNAPP** — Cloud Security Posture Mgmt; Workload Protection; converged cloud-native app protection platform.

57. **CASB** — Cloud Access Security Broker; visibility/control for SaaS usage.

58. **KMS / HSM** — key management and hardware security modules.

59. **VPC / Subnet / Security Group / NACL** — cloud networking segmentation primitives.

60. **WAF** — Web Application Firewall; shields against OWASP Top 10, bots.

61. **SRE / SLI-SLO-SLA** — Site Reliability Engineering; metrics, objectives, contractual commitments.

62. **Change Management (CAB, RFC/CRQ)** — controlled change process to reduce incidents/regressions.

63. **IaC** — Infrastructure as Code (e.g., Terraform, CloudFormation) with policy-as-code guardrails.

---

## 6) Incident Management, BCP/DR & Threats

64. **NIST 800-61 (IR)** — incident response lifecycle: **Preparation → Detection/Analysis → Containment/Eradication/Recovery → Post-Incident**.

65. **Playbook / Runbook** — documented steps for incident handling/operations.

66. **Tabletop Exercise (TTX)** — discussion-based simulation to test readiness.

67. **BCP / DRP** — Business Continuity / Disaster Recovery Plans.

68. **RTO / RPO** — Recovery Time / Recovery Point Objectives.

69. **Threat Intelligence (TI/CTI)** — curated knowledge about adversaries, TTPs, indicators.

70. **TTPs** — Tactics, Techniques, and Procedures; attacker behavior patterns.

71. **Phishing / BEC** — social engineering to steal creds or redirect payments (Business Email Compromise).

72. **Ransomware** — malware encrypting data for extortion; countered via EDR, backups, segmentation.

73. **Loss Event** — realized incident causing financial/operational impact; basis for risk quantification.

---

## 7) Third-Party & Procurement

74. **TPRM / SCRM** — Third-Party Risk Management / Supply-Chain Risk Management.

75. **RFI / RFP / RFQ** — information request, proposal, quotation; procurement stages.

76. **MSA / SOW** — Master Services Agreement; Statement of Work.

77. **DPA** — Data Processing Addendum; defines roles (controller/processor), transfers, security.

78. **BAA** — Business Associate Agreement for HIPAA-covered data.

79. **SIG / SIG Lite** — standardized vendor security questionnaires (Shared Assessments).

80. **SOC 1 vs SOC 2** — SOC 1: financial controls (ICFR); SOC 2: security/privacy criteria.

81. **Pen Test Letter / ASV Scan (PCI)** — third-party test attestations for compliance.

82. **Right-to-Audit Clause** — contractual right to inspect vendor controls.

---

## 8) Privacy & Legal (US-centric, business-relevant)

83. **CCPA/CPRA** — California consumer privacy rights (access, delete, opt-out of *sale/share*), sensitive data rules, contracts.

84. **GLBA (Safeguards Rule)** — financial institutions’ data security program requirements.

85. **HIPAA (Privacy/Security/Breach Rules)** — protections for PHI; applies to Covered Entities and Business Associates.

86. **SOX (Section 404)** — internal control over financial reporting; ITGC relevance.

87. **SEC Cyber Disclosure** — material incident and risk-management disclosures in public filings.

88. **FERPA / COPPA / VPPA** — sector-specific US privacy rules (students, children <13, video data).

89. **DPIA / PIA** — (Data) Privacy Impact Assessment for high-risk processing.

90. **Records of Processing (RoPA)** — catalog of processing activities; often required under privacy regimes.

91. **Data Subject Request (DSR)** — request to exercise privacy rights (access, delete, etc.).

92. **Breach Notification** — statutory timelines/thresholds for notifying regulators/consumers.

---

## 9) Finance, Accounting & Value (for BISO conversations)

93. **P\&L (Profit and Loss Statement)** — income statement: revenue, COGS, **Gross Profit**, **OpEx**, **Operating Income**, **Net Income**.

94. **OpEx / CapEx** — operating vs capital expenditures; impacts budget approval and depreciation.

95. **EBITDA** — Earnings Before Interest, Taxes, Depreciation, and Amortization; proxy for operating performance.

96. **Gross Margin / Contribution Margin** — profitability after COGS / incremental profit after variable costs.

97. **ROI** — Return on Investment = (Gain − Cost)/Cost.
    *Example:* \$500k loss avoidance on \$200k control ≈ **150% ROI**.

98. **IRR / NPV / Payback Period** — investment evaluation metrics; discount cash flows to assess security/business cases.

99. **TCO** — Total Cost of Ownership (license, cloud, headcount, support, training, migration, de-commissioning).

100. **ARR / MRR** — Annual/Monthly Recurring Revenue (for SaaS business context).

101. **CAC / LTV** — Customer Acquisition Cost; Lifetime Value; relevant when security measures affect conversion or churn.

102. **NRR / GRR** — Net/Gross Revenue Retention; security reliability impacts renewal/expansion.

103. **Cost of Risk (CoR)** — expected annualized loss + controls + insurance — informs optimal spend.

104. **ALE / SLE / ARO** — Annualized Loss Expectancy; Single Loss Expectancy; Annualized Rate of Occurrence (classic quantitative risk).
     *Example:* \$2M SLE × 0.2 ARO ⇒ **\$400k ALE**.

105. **FAIR** — Factor Analysis of Information Risk; calibrated, probabilistic loss modeling (e.g., P10/P50/P90).

---

## 10) Reporting, KPIs & Executive Communication

106. **KPI / KRI** — Key Performance Indicator; Key Risk Indicator (leading vs lagging).

107. **Heat Map** — visual of risk vs impact/likelihood; supports prioritization.

108. **Scorecard / Dashboard** — curated metrics for execs (e.g., patch SLAs, phishing fail rate, critical vulns > 30 days).

109. **OKR** — Objectives and Key Results; align security goals with business outcomes.

110. **Materiality** — threshold at which information influences investor decisions; central to SEC cyber disclosures.

111. **Narrative Risk Story** — concise, data-backed articulation of business risk and choices (accept/transfer/mitigate).

---

## 11) Data, Analytics & AI

112. **Data Lake / Warehouse** — raw vs modeled storage; informs logging/telemetry strategy.

113. **Data Lineage** — provenance/transformations; critical for auditability.

114. **De-identification / Pseudonymization** — privacy-preserving techniques.

115. **Model Risk Management (MRM)** — governance over ML models (bias, drift, explainability, security).

116. **Prompt Injection / Model Theft / Data Exfil via LLM** — AI-specific threats and controls.

117. **Guardrails** — policy and technical constraints for safe AI usage (red teaming, content filters, retrieval boundaries).

---

## 12) Operational Technology (OT) & Physical

118. **OT / ICS** — Operational Technology / Industrial Control Systems (SCADA, PLCs).

119. **IIoT** — Industrial Internet of Things; sensorized manufacturing/energy.

120. **Zone/Conduit Model** — segmented architecture for ICS safety/security.

121. **Safety Integrity Level (SIL)** — reliability measure for safety functions.

122. **Physical Security (CPTED, Badging, Mantraps)** — complements cyber controls.

---

## 13) Crypto/Fintech (select terms BISOs encounter)

123. **KYC / AML** — Know Your Customer / Anti-Money Laundering obligations; identity verification and transaction monitoring.

124. **Custody / Cold Storage** — safeguarding digital assets; key management, multi-sig, HSMs.

125. **Stablecoin / Fiat On-Ramp** — price-pegged crypto; bridges between banked funds and digital assets.

126. **Travel Rule** — information-sharing requirement for certain crypto transfers (VASP-to-VASP).

---

## 14) Common Documents & Artifacts

127. **ISMS** — Information Security Management System; policies, procedures, metrics, continual improvement.

128. **Policy / Standard / Procedure / Guideline** — top-down to detailed how-to hierarchy.

129. **Control Matrix / RACI** — maps controls to owners (Responsible, Accountable, Consulted, Informed).

130. **Data Map / Inventory** — systems, data categories, flows, locations.

131. **Retention Schedule** — how long data/artifacts are kept.

132. **Security Requirements Traceability Matrix (SRTM)** — links requirements to tests/evidence.

---

## 15) Talks BISO Should Navigate — example phrasings

133. **“Risk Transfer via Cyber Insurance”** — premiums, exclusions, retentions; align with incident playbooks and claims evidence.

134. **“Enablement vs. Restriction”** — frame controls as revenue protection (e.g., faster audits, faster enterprise deals).

135. **“Material Incident Escalation”** — crisply define thresholds, roles, and disclosure timing.

---

### Mini-Examples (quick reference)

* **Compensating Control:** If SaaS lacks SSO today, enforce MFA + IP allow-listing + tight off-boarding as a temporary equivalent.
* **ROI for Control:** Implement phishing-resistant MFA; expected reduction in account-takeover loss from \$800k to \$150k on \$200k spend ⇒ **225% ROI**, \~11-month payback.
* **Zero Trust Sound-bite for Execs:** “We verify every user and device, every time, for every resource — and limit blast radius via segmentation.”

---

## Appendix — Abbreviation Quick Table (selected)

**ALE, ARO, BAA, BCP, BIA, BISO, CAPEX, CASB, CIEM, CISA, CISO, CNAPP, COBIT, CVSS, DAST, DLP, DORA, DPIA, DRP, EDR, EBITDA, ERM, FAIR, FFIEC, FIDO2, GLBA, GRC, HIPAA, HSM, IAM, IaC, ICS, IdP, IRR, ISO, ITGC, ITIL, KMS, KPI/KRI, LTV/CAC, MFA, MITRE ATT\&CK, MRR/ARR, MSA, MTBF/MTTD/MTTR, NIST CSF, NPV, OIDC, OpEx, OWASP, PAM, PCI DSS, PHI/PII, PoLP, RACI, RASP, RFC/CRQ/CAB, RFP/RFI/RFQ, RoPA, ROI, RPO/RTO, SBOM, SEC (cyber), SIEM, SIG, SLA/SLO/SLI, SOW, SRE, SRTM, SSO, SAST/IAST, SOC 1/2, SOX, TCO, TI/CTI, TTPs, UEBA, WAF, WebAuthn, Zero Trust.**

---
