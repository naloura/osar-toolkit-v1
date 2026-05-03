# {ORG_SHORT} Module — Source Code Analysis
**Module Type:** Conditional — source code reviews only
**Trigger:** Step 1 intake determines that source code files have been provided for review
**Parent Document:** Security Impact Report AI Instructions
**Module Reference:** SIR-MOD-SOURCE-001

---

## Analysis Task C — File Size Measurement [CONDITIONAL — source code reviews only]

Skip for vendor SaaS solutions. For source code reviews:

1. Record file size in bytes
2. Calculate gzip-compressed size (level 9)
3. Calculate space saved: `(1 - compressed/uncompressed) × 100`, rounded to nearest integer
4. Count lines of code for JavaScript and CSS
5. Convert to KB with one decimal place
6. Sum raw and compressed totals
7. Identify external dependencies and estimate transfer size

---

## Analysis Task E — Capacity and Performance [CONDITIONAL — source code reviews only]

Skip for vendor SaaS. Use file sizes from Task C and user count:

```
per_user_bytes      = total_compressed_bytes + external_dependency_bytes
worst_case_mbps     = (user_count × per_user_bytes × 8) ÷ (60 × 1,000,000)
realistic_mbps      = (user_count × per_user_bytes × 8) ÷ (300 × 1,000,000)
total_cohort_mb     = (user_count × per_user_bytes) ÷ (1,024 × 1,024)
```

Round bandwidth to one decimal place. Cohort totals in MB with one decimal place.

---

## Report Section 5 — File Sizes and Deployment Analysis (Source Code Subsections)

These subsections are added to Section 5 of the report when source code is provided.

### 5.1 Asset Inventory and File Sizes [CONDITIONAL — source code reviews]

| File | Purpose | Lines of Code | Uncompressed | Compressed | Space Saved |
|---|---|---|---|---|---|
| [FILENAME] | [PURPOSE] | [N or —] | [X.X KB] | [X.X KB] | [XX%] |
| **Total** | — | — | [X.X KB] | [X.X KB] | [XX%] |

### 5.2 Per-User Download Budget [CONDITIONAL — source code reviews]

| Component | Uncompressed | Transferred | Delivered From |
|---|---|---|---|
| [COMPONENT] | [SIZE] | [SIZE] | [SOURCE] |

### 5.3 Capacity Analysis for [N] Simultaneous Users [CONDITIONAL — source code reviews or server-hosted]

| Load Scenario | Peak Bandwidth | Duration | Server CPU | Assessment |
|---|---|---|---|---|
| All [N] load in 60s (worst) | [X Mbps] | ~60s | [Level] | [Assessment] |
| All [N] load in 5min (realistic) | [X Mbps] | ~5min | [Level] | [Assessment] |
| After load (active use) | [X bytes/s] | Indefinite | [Level] | [Assessment] |
| Full cohort total | — | One-time | — | [X MB] |

### 5.7 Recommended Hosting Setup [CONDITIONAL — source code reviews or self-hosted]

| Option | How It Works | Est. Cost | Key Notes |
|---|---|---|---|
| [Recommended] | [DESC] | [COST] | [NOTES] |

[List infrastructure the asset does NOT require, if applicable.]

---

*{ORG_SHORT} Module — Source Code Analysis | Parent: Security Impact Report AI Instructions*
