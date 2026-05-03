# {ORG_SHORT} Module — WCAG Accessibility Compliance
**Module Type:** Conditional — constituent-facing or public-facing assets only
**Trigger:** Step 1 intake identifies the asset as constituent-facing or public-facing
**Parent Document:** Security Impact Report AI Instructions
**Module Reference:** SIR-MOD-WCAG-001

---

## Analysis Task F — WCAG Accessibility Compliance [CONDITIONAL — constituent-facing assets]

**Trigger:** Execute only when the asset is **constituent-facing or public-facing**. Purely internal assets: mark N/A with brief justification.

**Regulatory basis:** Section 508 (29 U.S.C. § 794d), ADA Title II, {STATE_ACCESSIBILITY_LAW}. Current target: **WCAG 2.1 Level AA**.

Assess against four WCAG 2.1 principles at AA conformance. This is a structured review, not an exhaustive audit.

**F.1 — Perceivable:** 1.1.1 Non-text Content (A), 1.2.1–1.2.5 Time-based Media (A/AA), 1.3.1 Info and Relationships (A), 1.3.4 Orientation (AA), 1.4.1 Use of Color (A), 1.4.3 Contrast Minimum (AA), 1.4.4 Resize Text (AA), 1.4.10 Reflow (AA), 1.4.11 Non-text Contrast (AA).

**F.2 — Operable:** 2.1.1 Keyboard (A), 2.1.2 No Keyboard Trap (A), 2.4.1 Bypass Blocks (A), 2.4.2 Page Titled (A), 2.4.3 Focus Order (A), 2.4.6 Headings and Labels (AA), 2.4.7 Focus Visible (AA).

**F.3 — Understandable:** 3.1.1 Language of Page (A), 3.1.2 Language of Parts (AA), 3.2.1 On Focus (A), 3.2.2 On Input (A), 3.3.1 Error Identification (A), 3.3.2 Labels or Instructions (A), 3.3.3 Error Suggestion (AA).

**F.4 — Robust:** 4.1.1 Parsing (A), 4.1.2 Name Role Value (A), 4.1.3 Status Messages (AA).

**F.5 — WCAG 2.2 Readiness:** Assess: 2.4.11 Focus Not Obscured (AA), 2.5.7 Dragging Movements (AA), 2.5.8 Target Size Minimum (AA), 3.2.6 Consistent Help (A), 3.3.7 Redundant Entry (A), 3.3.8 Accessible Authentication Minimum (AA). Status: Ready / Partially Ready / Not Ready / N/A.

**F.6 — Summary:** Document totals, remediation priorities (Critical/Major/Minor), formal audit recommendation, WCAG 2.2 readiness summary.

---

## Report Section 8 — WCAG Accessibility Compliance [CONDITIONAL — constituent-facing only]

**Include only for constituent-facing or public-facing assets.** If internal: omit, note N/A in Section 7.3.

**Basis:** Section 508, ADA Title II, {STATE_ACCESSIBILITY_LAW}, WCAG 2.1 Level AA.

### 8.1 WCAG 2.1 Level AA Summary

| Principle | Evaluated | Met | Findings | N/A | Compliance |
|---|---|---|---|---|---|
| Perceivable | [N] | [N] | [N] | [N] | [X%] |
| Operable | [N] | [N] | [N] | [N] | [X%] |
| Understandable | [N] | [N] | [N] | [N] | [X%] |
| Robust | [N] | [N] | [N] | [N] | [X%] |
| **Total** | **[N]** | **[N]** | **[N]** | **[N]** | **[X%]** |

### 8.2 Detailed Findings

[One table per principle: Criterion, Level, Status, Finding, Remediation]

### 8.3 Remediation Priority Matrix

| Priority | Criterion | Summary | Effort | Responsible |
|---|---|---|---|---|
| Critical | [ID] | [Summary] | [Low/Med/High] | [Party] |
| Major | [ID] | [Summary] | [Low/Med/High] | [Party] |
| Minor | [ID] | [Summary] | [Low/Med/High] | [Party] |

### 8.4 WCAG 2.2 Readiness

| Criterion | Level | Readiness | Notes |
|---|---|---|---|
| 2.4.11 Focus Not Obscured | AA | [Status] | [Notes] |
| 2.5.7 Dragging Movements | AA | [Status] | [Notes] |
| 2.5.8 Target Size (Min) | AA | [Status] | [Notes] |
| 3.2.6 Consistent Help | A | [Status] | [Notes] |
| 3.3.7 Redundant Entry | A | [Status] | [Notes] |
| 3.3.8 Accessible Auth (Min) | AA | [Status] | [Notes re: {IDP} SSO] |

**Preparation Recommendations:** (1) Target size audit — 24×24px minimum. (2) Drag alternatives. (3) Focus visibility hardening. (4) Authentication pathway review vs {IDP}. (5) Help consistency. (6) Redundant entry elimination.

### 8.5 Compliance Recommendation

| Area | Finding |
|---|---|
| WCAG 2.1 AA compliance | [Compliant / With findings / Not compliant] |
| Findings count | [N] ([N] Critical, [N] Major, [N] Minor) |
| WCAG 2.2 readiness | [Ready / Partial / Not Ready] |
| Formal audit needed | [Yes / No — justification] |
| Remediation timeline | [Before deployment / 30 days / Next release] |

---

*{ORG_SHORT} Module — WCAG Accessibility | Parent: Security Impact Report AI Instructions*
