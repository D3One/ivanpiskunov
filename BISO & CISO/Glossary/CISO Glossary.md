

# CISO Glossary — executive-grade, security-led

**What this is:** a comprehensive, business-ready glossary for a **Chief Information Security Officer (CISO)**. It blends cybersecurity, network defense, Windows/Linux attack/defense, cloud, identity, privacy/compliance, budgeting/finance, people leadership, negotiations, and C-suite communications. All terms are in **American English**, with expansions, concise explanations, and occasional examples.

**How it was compiled:** synthesis of widely adopted frameworks and sources (NIST CSF/800-53/800-61/800-171, ISO/IEC 27001/27002, CIS Controls v8, COBIT, MITRE ATT\&CK/D3FEND, OWASP, AICPA SOC 2, PCI DSS, FFIEC, CISA guidance, ITIL 4), plus executive finance and org-design practices (ROI, TCO, NPV, OKR, KPIs) and frontline security operations patterns.

---

## 1) Executive Governance & Leadership

1. **Corporate Governance** — structures (board/committees/charters) that direct and oversee risk, compliance, and security.
2. **Enterprise Risk Management (ERM)** — coordinated approach to identifying, analyzing, treating, and monitoring enterprise risks.
3. **Risk Appetite** — the level/types of risk leadership is willing to accept in pursuit of goals.
4. **Risk Tolerance** — acceptable variance from appetite on specific metrics (e.g., “≤ 1 material incident/year”).
5. **Risk Capacity** — maximum risk the org can absorb without threatening viability (capital/liquidity/ops limits).
6. **Three Lines Model** — (1) management/owners of risk, (2) risk/compliance oversight, (3) independent assurance (internal audit).
7. **GRC (Governance, Risk, and Compliance)** — integrated process/technology aligning policy, risk, and control with strategy.
8. **Control Objective** — desired outcome a control must achieve (e.g., “Only authorized users access PHI”).
9. **Compensating Control** — alternate control providing equivalent protection when a standard control is infeasible.
10. **Risk Register** — authoritative log of risks, owners, treatments, and status.
11. **Materiality** — threshold at which information influences investor decisions; key to SEC cyber disclosures.
12. **Policy / Standard / Procedure / Guideline** — governance hierarchy from high-level intent to step-by-step actions.
13. **Security Strategy** — multi-year plan aligning security outcomes with business growth, reliability, and compliance.
14. **Security Operating Model** — org design, processes, and tooling that deliver the strategy (centralized, federated, hybrid).
15. **Information Security Management System (ISMS)** — management system for policies, risks, controls, metrics, improvement.

---

## 2) Finance, Budgeting & Value (CISO essentials)

16. **P\&L (Profit and Loss)** — income statement: revenue, COGS, gross margin, OpEx, operating income, net income.
17. **OpEx / CapEx** — operating vs capital expenditures; affects depreciation and budget approvals.
18. **EBITDA** — earnings before interest, taxes, depreciation, amortization; proxy for operating performance.
19. **TCO (Total Cost of Ownership)** — full cost of a solution (licenses, cloud, labor, training, migration, decomm).
20. **ROI (Return on Investment)** — (Gain − Cost)/Cost; can include **loss avoidance**.
    *Example:* \$800k expected loss → \$200k after control on \$200k spend ≈ 200% ROI.
21. **NPV / IRR / Payback Period** — discounted cash flow metrics to compare investments.
22. **Unit Economics** — per-unit profitability levers; security may impact churn, conversion, support cost.
23. **Cost of Risk (CoR)** — expected annual loss + control cost + insurance; informs optimal security spend.
24. **ALE / SLE / ARO** — Annualized/Singe Loss Expectancy; Annualized Rate of Occurrence (classic quant risk).
25. **FAIR (Factor Analysis of Information Risk)** — calibrated, probabilistic loss modeling (P10/P50/P90).
26. **Zero-Based Budgeting (ZBB)** — build budgets from baseline need, not prior year.
27. **Run-Grow-Transform (RGT) Split** — classify spend into steady-state, expansion, and strategic change.
28. **Chargeback / Showback** — allocate security costs to business units (hard/soft).
29. **Vendor Lock-In** — switching barriers (contracts, data gravity, skillsets); negotiate exit rights.
30. **Cyber Insurance** — risk transfer with deductibles, exclusions, claims evidence, and panel requirements.
31. **RFP / RFI / RFQ** — request for proposal/information/quotation in procurement cycles.
32. **Total Cost of Delay (TCD)** — economic impact of deferring a control or remediation.
33. **Depreciation / Amortization** — spreading CapEx/intangibles over useful life; impacts P\&L optics.
34. **Budget Guardrails** — caps and rules (e.g., SaaS vs perpetual, headcount vs services ratios).
35. **Business Case** — structured document quantifying benefits, costs, risks, and options for an initiative.

---

## 3) Frameworks, Standards & Compliance

36. **NIST CSF (2.0)** — Identify, Protect, Detect, Respond, Recover + Governance; outcome-based.
37. **NIST SP 800-53** — comprehensive control catalog (AC, AU, CM, IR, SC, etc.).
38. **NIST SP 800-61** — Computer Security Incident Handling Guide (IR lifecycle).
39. **NIST SP 800-171** — protecting CUI in non-federal systems; underpins **CMMC**.
40. **CMMC (Cybersecurity Maturity Model Certification)** — DoD supplier compliance levels.
41. **ISO/IEC 27001/27002** — certifiable ISMS + control practices.
42. **COBIT** — governance framework for value delivery and assurance.
43. **CIS Controls v8** — prioritized safeguards with implementation groups (IG1–IG3).
44. **MITRE ATT\&CK** — adversary tactics/techniques knowledge base; drives detection engineering.
45. **MITRE D3FEND** — countermeasure mapping to ATT\&CK techniques.
46. **SOC 2 (AICPA)** — attestation on Security, Availability, Processing Integrity, Confidentiality, Privacy (Type I/II).
47. **PCI DSS** — cardholder data protection; segments **CDE** (Cardholder Data Environment).
48. **HIPAA** — Privacy/Security/Breach Rules for PHI; CE/BA roles.
49. **GLBA (Safeguards Rule)** — financial institutions’ security program requirements.
50. **SOX (Section 404)** — internal control over financial reporting; ITGC relevance.
51. **CCPA/CPRA** — CA privacy rights (access, delete, opt-out sale/share); contracts and sensitive data.
52. **DPIA/PIA** — privacy impact assessments for high-risk processing.
53. **Records of Processing (RoPA)** — inventory of processing activities.
54. **Breach Notification** — statutory timelines/thresholds for reporting to regulators/consumers.
55. **Secure SDLC** — embed security requirements/testing into software lifecycle (see § SecOps).

---

## 4) Identity, Access & Data

56. **IAM (Identity and Access Management)** — identities, roles, provisioning, lifecycle.
57. **IdP (Identity Provider)** — authenticates users, issues tokens/assertions.
58. **SSO (Single Sign-On)** — centralized auth across apps.
59. **MFA (Multi-Factor Authentication)** — at least two of: something you know/have/are (e.g., FIDO2/WebAuthn).
60. **SAML / OAuth 2.0 / OIDC** — federation & delegated auth; OIDC adds identity layer to OAuth.
61. **PAM (Privileged Access Management)** — vaulting, session monitoring, just-in-time elevation.
62. **CIEM (Cloud Infrastructure Entitlement Management)** — rights hygiene at cloud scale.
63. **RBAC / ABAC** — role- vs attribute-based access control models.
64. **PoLP (Principle of Least Privilege)** — grant only necessary permissions.
65. **DLP (Data Loss Prevention)** — detect/prevent unauthorized data movement.
66. **Tokenization / Encryption** — replace sensitive values; protect data at rest/in transit; use **KMS/HSM**.
67. **Data Classification** — label by sensitivity (Public, Internal, Confidential, Restricted).
68. **Secrets Management** — lifecycle of API keys, credentials, certificates.
69. **Keystore / KMS / HSM** — key management service; hardware security module.
70. **Data Minimization** — collect/retain only what is needed for stated purposes.

---

## 5) Network, Edge & Zero Trust

71. **Zero Trust** — continuous verification of identity, device, and context; micro-segmentation; explicit authz.
72. **ZTNA (Zero Trust Network Access)** — app-level access broker replacing broad VPN access.
73. **SASE / SSE** — cloud-delivered networking/security (SWG, CASB, ZTNA, FWaaS, DLP).
74. **NAC (Network Access Control)** — enforce device posture and identity on network join.
75. **Segmentation / Micro-segmentation** — limit blast radius by zoning and policy.
76. **IDS/IPS / NDR** — intrusion detection/prevention; network detection & response.
77. **WAF / API Gateway** — shield web/API services (OWASP Top 10, bot mgmt, rate limiting).
78. **TLS / mTLS / QUIC** — transport security; mutual TLS for service-to-service trust.
79. **DNS Security** — DNSSEC, DNS filtering/sinkholing, egress controls.
80. **Email Authentication** — SPF, DKIM, DMARC alignment and enforcement.
81. **DDoS Protection** — absorption/scrubbing, anycast, adaptive rate limiting.
82. **BGP (Border Gateway Protocol) Security** — route hijack/ROA/RPKI considerations.
83. **Egress Filtering** — restrict outbound traffic to approved destinations/ports.
84. **Proxy / SWG (Secure Web Gateway)** — inspect outbound web traffic; policy enforcement.
85. **VPN (IPsec/SSL)** — encrypted remote access; increasingly replaced by ZTNA.
86. **NAT / PAT** — address/port translation; affects telemetry and attribution.
87. **Decryption Strategy** — lawful and risk-based TLS inspection with privacy exceptions.
88. **Network Telemetry** — NetFlow/IPFIX, span/taps; inputs to NDR/SIEM.

---

## 6) Security Operations, Detection & Response

89. **SOC (Security Operations Center)** — people/process/tech for monitoring, detection, and response.
90. **SIEM** — log aggregation, correlation, alerting, compliance reporting.
91. **SOAR** — orchestration/automation with playbooks (enrichment, contain, notify).
92. **EDR/XDR** — endpoint/extended detection & response across identity/network/cloud.
93. **UEBA** — user/entity behavior analytics for anomaly detection.
94. **Deception Technology** — breadcrumbs/honeypots to detect lateral movement.
95. **Threat Intelligence (TI/CTI)** — indicators, TTPs, actor profiles; strategic/operational/tactical tiers.
96. **Detection Engineering** — craft/test detections mapped to ATT\&CK; measure detection coverage.
97. **Use Case Catalog** — prioritized list of detections (e.g., suspicious PowerShell, credential dumping).
98. **IR Playbook** — documented steps for specific incident types (BEC, ransomware, data exfil).
99. **Tabletop Exercise (TTX)** — scenario-based rehearsal involving execs and partners (legal/PR).
100. **Post-Incident Review (PIR)** — blameless analysis; corrective actions; metrics updates.
101. **MTTD / MTTR** — mean time to detect/respond; core SOC KPIs.
102. **Containment / Eradication / Recovery** — IR phases to stop, remove, and restore.
103. **Forensics Readiness** — logging/retention, time sync, imaging, chain-of-custody.
104. **Backup Strategy (3-2-1)** — three copies, two media, one offsite/offline; immutable snapshots.
105. **Ransomware Controls** — EDR + hardening + segmentation + offline backups + playbooks (legal/LE/insurance).
106. **Security Telemetry Quality** — coverage, fidelity, normalization, time-stamping, context.
107. **Runbook** — step-by-step operational procedure (e.g., disable account, isolate host).
108. **Purple Teaming** — red/blue collaboration to validate and improve detections.
109. **Exposure Management** — continuous attack surface mgmt + vuln mgmt + configuration drift.
110. **Asset Inventory** — authoritative CMDB/asset graph for scope and prioritization.

---

## 7) Windows Enterprise: Attacks & Defenses

111. **Active Directory (AD)** — identity core (domains, forests, trusts, GPOs); hardening is critical.
112. **Kerberoasting** — request service tickets (TGS) and crack offline; defend via strong SPN keys & monitoring.
113. **Pass-the-Hash (PtH)** — reuse NTLM hashes for auth; defend with credential isolation, LAPS, SMB signing.
114. **Pass-the-Ticket (PtT)** — reuse Kerberos tickets (TGT/TGS); detect unusual ticket lifetimes/over-privileged SIDs.
115. **DCSync** — abuse Directory Replication Service to pull password hashes; monitor for non-DC DRSUAPI calls.
116. **Golden Ticket** — forged TGT using KRBTGT key; rotate KRBTGT, monitor anomalous TGT issuance.
117. **LSASS Dumping** — extract creds from memory (e.g., Mimikatz); enable Credential Guard, block non-admin dumps.
118. **NTDS.dit Exfiltration** — AD database theft; restrict DC access, enable DC isolated backups.
119. **WMI/WinRM Lateral Movement** — remote execution channels; log/alert unusual remote ops.
120. **PowerShell Abuse** — living-off-the-land (LOLBins); enable Constrained Language Mode, Script Block Logging, AMSI.
121. **AppLocker/WDAC** — application allow-listing; block unknown binaries/scripts.
122. **LAPS / LAPS-NG** — randomized local admin passwords per machine; rotate and audit access.
123. **GPO Hardening** — secure policies; restrict delegation; protected users, tiering.
124. **Sysmon / ETW** — advanced event telemetry; tune for credential theft/lateral movement.
125. **PrinterNightmare / Spooler** — disable unnecessary services; patch promptly.
126. **SAM / SECURITY Hive Protection** — block shadow copy exposure; protect registry hives.
127. **Tiered Admin Model** — separate admin tiers (workstation/server/AD) with no cross-use of creds.

---

## 8) Linux, Containers & Kubernetes

128. **PrivEsc (Privilege Escalation)** — kernel/SETUID/CONFIG exploits; patching and minimal capabilities.
129. **sudoers Abuse** — misconfigured sudo enabling root; enforce least privilege and NOPASSWD review.
130. **SSH Key Theft** — exfil of private keys/agents; use passphrases, hardware keys, limited from= restrictions.
131. **LD\_PRELOAD / Library Hijacking** — load rogue libs; integrity controls and package verification.
132. **Cron/Systemd Persistence** — malicious scheduled tasks/units; audit timers/services.
133. **Capabilities (cap\_setuid, cap\_net\_raw)** — granular privileges; drop unnecessary caps in containers.
134. **Container Escape** — breakouts via namespaces/cgroups or daemon sockets; use rootless, seccomp, AppArmor/SELinux.
135. **K8s RBAC** — least-privilege service accounts; avoid cluster-admin; network policies.
136. **Admission Control / OPA/Gatekeeper** — policy-as-code for deployments.
137. **Image Signing/Scanning (SBOM)** — verify provenance (Sigstore/COSIGN), scan for vulns, keep SBOMs.
138. **Secrets in K8s** — use external secret stores (KMS/HSM), avoid plain-text in manifests.
139. **Etcd Security** — encrypt at rest, mTLS between components, restricted access.
140. **Supply Chain Security** — SLSA levels, provenance attestations, pinned versions.
141. **Runtime Security** — eBPF-based detection, syscall rules, drift control.
142. **Docker Daemon Socket** — protect /var/run/docker.sock; avoid privileged containers.

---

## 9) Cloud & SaaS

143. **Shared Responsibility Model** — provider vs customer duties vary by IaaS/PaaS/SaaS.
144. **CSPM / CWPP / CNAPP** — posture mgmt; workload/runtime protection; converged platform.
145. **CASB / SSPM** — shadow IT visibility; SaaS posture management (misconfigs, tokens).
146. **Key Management (KMS/HSM/CSE)** — customer-managed keys; crypto separation of duties.
147. **IAM in Cloud** — least-privilege roles, permission boundaries, JIT elevation.
148. **Network Controls** — VPCs, subnets, SGs/NACLs, private endpoints, WAF/CDN.
149. **Logging & Telemetry** — native cloud logs (control/identity/data plane) to SIEM; retention.
150. **Identity Federation** — SAML/OIDC to central IdP; SCIM for provisioning.
151. **SaaS Hardening** — SSO-only login, MFA enforced, app-level roles, tenant audit logs.
152. **Data Residency & Sovereignty** — region placement, cross-border transfers, contractual clauses.
153. **Cost Governance** — tagging, budgets/alerts, right-sizing; avoid cost-driven insecure shortcuts.
154. **Backup & DR in Cloud** — cross-region replication, immutability, tested restoration.

---

## 10) AppSec & Data

155. **SAST / DAST / IAST / RASP** — static/dynamic/interactive testing; runtime self-protection.
156. **OWASP Top 10 / ASVS** — common web/API risks and verification standards.
157. **OWASP API Security Top 10** — API-specific risks (authz, excessive data, mass assignment).
158. **Threat Modeling** — structured analysis (STRIDE, attack trees) to prioritize mitigations.
159. **SBOM** — software bill of materials; dependency transparency and vuln response.
160. **Secrets Scanning** — detect credentials in code/CI logs; pre-commit hooks and pipeline checks.
161. **Data Discovery** — find sensitive data in stores/streams; classify and control.
162. **Privacy by Design** — embed data minimization and purpose limitation into systems.

---

## 11) People, Org Design & Culture

163. **Org Topology** — centralized vs federated security; BU-embedded security champions.
164. **Headcount Plan / Job Families** — role levels, competencies, succession planning.
165. **Span of Control** — number of direct reports per manager; balance focus and agility.
166. **Performance Management** — OKRs, KPIs, growth frameworks; avoid activity-only metrics.
167. **PIP (Performance Improvement Plan)** — structured remediation/support for underperformance.
168. **Blameless Postmortem** — culture of learning and systemic fixes over blame.
169. **Security Champions** — trained engineers within product teams promoting secure practices.
170. **Training & Phishing Simulations** — role-based training; measure risk reduction, not clicks alone.
171. **Duty of Care** — provide safe tools/processes; track burnout and on-call sustainability.
172. **Diversity & Inclusion** — broaden perspectives, reduce blind spots in design/ops.

---

## 12) Negotiation & Executive Communication

173. **BATNA (Best Alternative to a Negotiated Agreement)** — your fallback option; strengthens leverage.
174. **ZOPA (Zone of Possible Agreement)** — overlap of acceptable outcomes between parties.
175. **Anchoring** — set initial reference points (price/terms) to influence negotiations.
176. **Concession Strategy** — planned trade-offs tied to value (term length vs price vs exit rights).
177. **C-Suite Narrative** — crisp risk/benefit framing in business terms, not tool features.
178. **Board-Level Metrics** — few, stable, outcome-centric measures (material incidents, exposure trend, time-to-recover).
179. **Executive Readout** — one-page summary: context → risk → options → recommendation → cost/benefit.
180. **Crisis Communications** — aligned legal/PR/regulatory messaging; single source of truth.

---

## 13) Handy Mini-Examples

* **Materiality call (SEC):** “Incident impacted 17% of annual revenue system with ≥ 1 week outage risk; probable financial impact > disclosure threshold.”
* **Zero Trust in one line:** “Continuously verify user, device, and context; authorize per request; limit lateral movement.”
* **Business case sound-bite:** “\$2.4M expected loss reduction over 3 years on \$900k TCO; NPV positive by month 14.”

---

## 14) Abbreviation Quick Table (selected)

**AD, AMSI, API, ATT\&CK, ABAC, BATNA, BCP/DR, CASB, CIEM, CIS, CMDB, CNAPP, COBIT, CoR, COGS, CSF, CSPM, CWPP, DAC/RBAC/ABAC, DAST, DDoS, DLP, DMARC/DKIM/SPF, DNSSEC, EDR/XDR, ETW, FAIR, FWaaS, GLBA, HIPAA, HSM, IaC, IAM, IaaS/PaaS/SaaS, IAST, IdP, IR/IRR, ISMS, ISO 27001, KMS, KRBTGT, KPI/KRI, K8s, LAPS, LOLBins, LSASS, MITRE D3FEND, MRR/ARR, MTBF/MTTD/MTTR, NAC, NDR, NetFlow, NIST 800-53/61/171, NPV, OIDC/OAuth/SAML, OKR, OpEx/CapEx, OPA, OWASP ASVS, PAM, PCI DSS, PHI/PII, PoLP, QUIC, RACI, RASP, RFP/RFI/RFQ, RoPA, ROI/TCO, RPO/RTO, SAML, SAST, SBOM, SCD, SCOPE/CDE, SecOps, SEIM/SIEM, SLE/ALE/ARO, SLSA, SOC 2, SOAR, SOX, SSE/SASE, SSO, STRIDE, Sysmon, TCD, TCO, TGT/TGS, TI/CTI, TLS/mTLS, TTPs, UEBA, VPN, WAF, WDAC, WinRM, WMI, ZBB, ZOPA, ZTNA.**

---
