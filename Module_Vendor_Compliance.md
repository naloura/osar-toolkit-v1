# {ORG_SHORT} Module — Vendor Compliance and Authorization
**Module Type:** Conditional — vendor solutions only
**Trigger:** Step 1 intake identifies the asset as a vendor-provided solution (SaaS, managed service, COTS)
**Parent Document:** Security Impact Report AI Instructions
**Module Reference:** SIR-MOD-VENDOR-001

---

## Section 3 — Vendor Compliance and Authorization [CONDITIONAL — vendor solutions]

**Include for vendor SaaS or managed service solutions. Omit for internally developed assets.**

### 3.1 FedRAMP / StateRAMP Authorization Status

| Attribute | Value |
|---|---|
| Authorization Level | [e.g., FedRAMP High / Moderate / None] |
| Authorization Status | [Authorized / In Process / N/A] |
| Cloud Service Provider | [e.g., AWS GovCloud / {HOSTING_ENV} Gov] |
| Continuous Monitoring | [Active / N/A] |

### 3.2 Additional Certifications

| Certification | Status | Notes |
|---|---|---|
| [e.g., DoD CC SRG IL2] | [Compliant / Certified / Attested] | [Details] |

### 3.3 {VENDOR_SECURITY_ADDENDUM}

| Requirement | Status | Evidence |
|---|---|---|
| Vendor MFA | [Verified / Pending] | [Per {VENDOR_SECURITY_ADDENDUM} and {POLICY_REF:vendor_security}] |
| FIPS 140-2/3 Encryption | [Verified / Pending] | [Per {STANDARD_REF:data_encryption}] |
| Security Questionnaire | [Complete / Pending] | [Details] |

---

## Vendor-Specific NIST SA Control Guidance

When this module is active, the following guidance applies to the SA (System and Services Acquisition) controls in the NIST Controls module:

**For vendor solutions:** Replace SA-8 through SA-15 with a reference to the vendor's SDLC documentation, penetration test report, SOC 2 Type II, or FedRAMP/StateRAMP authorization package. Confirm MFA per {VENDOR_SECURITY_ADDENDUM} and whether FIPS 140-2/140-3 validated encryption is in use per the {ORG_SHORT} Data Encryption Standard ({STANDARD_REF:data_encryption}).

---

*{ORG_SHORT} Module — Vendor Compliance | Parent: Security Impact Report AI Instructions*
