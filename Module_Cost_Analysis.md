# {ORG_SHORT} Module — Cost Analysis and Comparative Assessment
**Module Type:** Required for all assessments
**Parent Document:** Security Impact Report AI Instructions
**Module Reference:** SIR-MOD-COST-001

---

## Step 5 — Token Usage and Cost Analysis

After all analysis and report sections are complete, append Section 9.2 (token usage and cost) and Section 9.3 (comparative assessment model). Both are **[REQUIRED]** — use verified data for 9.2 and populate 9.3 with realistic estimates based on asset complexity.

### 5.1 Token Counts

**Source A (preferred):** Claude Code session JSONL at `~/.claude/projects/[path]/[session].jsonl`

```python
import json
path = "~/.claude/projects/[path]/[session].jsonl"
ti = to = tcc = tcr = calls = 0
with open(path) as f:
    for line in f:
        try: obj = json.loads(line.strip())
        except: continue
        usage = obj.get('message', {}).get('usage') if isinstance(obj.get('message'), dict) else None
        if not usage: continue
        ti += usage.get('input_tokens', 0); to += usage.get('output_tokens', 0)
        tcc += usage.get('cache_creation_input_tokens', 0); tcr += usage.get('cache_read_input_tokens', 0)
        calls += 1
print(f"Calls: {calls}\nInput: {ti:,}\nOutput: {to:,}\nCache writes: {tcc:,}\nCache reads: {tcr:,}\nTotal: {ti+to+tcc+tcr:,}")
```

**Source B:** Anthropic Console. **Source C:** Character estimate ÷ 4 (label as approximate).

### 5.2 Cost Rates

| Token Type | Rate (per million) |
|---|---|
| Standard input | $3.00 |
| Output | $15.00 |
| Prompt cache write | $3.75 |
| Prompt cache read | $0.30 |

### 5.3 Required Tables

**Token Usage:** Token Type / Count / Unit Price / Cost / Notes (with Total row)

**Session Metadata:** Model / API Calls / User Messages / Start / End / Duration / Pricing Reference

**Caching Efficiency:** Actual cost / Hypothetical no-cache / Savings ($ and %)

Include a paragraph on largest cost driver and note that figures represent API-equivalent costs.

---

## Report Section 9.2 — Project Resource Usage and Cost Analysis [REQUIRED]

This section documents the actual cost of AI-assisted report generation for transparency and budget accountability. Complete using token data from the Claude Code session JSONL transcript or the Anthropic Console per Step 5 instructions. Do not leave blank or estimate without labeling.

**Token Usage by Type:**

| Token Type | Count | Unit Price | Cost (USD) | Notes |
|---|---|---|---|---|
| Standard Input | [N] | $3.00/MTok | $[X.XX] | [Explain why low/high relative to report complexity] |
| Output (Generated) | [N] | $15.00/MTok | $[X.XX] | [What was generated — report sections, analysis, tables] |
| Prompt Cache Writes | [N] | $3.75/MTok | $[X.XX] | [What was cached — instruction file, source files, prior context] |
| Prompt Cache Reads | [N] | $0.30/MTok | $[X.XX] | [How many times cached context was reused across turns] |
| **Total** | **[N]** | — | **$[X.XX]** | All token types and all sessions combined |

**Session and Model Metadata:**

| Metric | Value | Details |
|---|---|---|
| Model | [MODEL NAME] | All sessions |
| Total API Calls | [N] turns | Each turn = one request/response pair |
| Total User Messages | [N] messages | Across all development sessions |
| Session Start | [TIMESTAMP UTC] | First API call in the transcript |
| Session End | [TIMESTAMP UTC] | Last API call in the transcript |
| Total Active Duration | [X hours] | Wall-clock time across the full project |
| Pricing Reference | Anthropic API — [MONTH YEAR] | Rates used for cost calculation |

**Prompt Caching Efficiency:**

| Scenario | Total Cost (USD) | Notes |
|---|---|---|
| Actual cost with prompt caching | $[X.XX] | As billed — cache reads at $0.30/MTok |
| Hypothetical cost without caching | $[X.XX] | If all tokens billed at standard input rates |
| Prompt cache savings | $[X.XX] ([XX]% reduction) | Driven by repeated reads of large cached context |

[Include a brief paragraph identifying which token type was the largest cost driver and why, and a one-sentence note clarifying that these figures represent Anthropic API-equivalent costs and that Claude Code subscription pricing may differ.]

---

## Report Section 9.3 — Comparative Assessment Model — AI-Assisted vs Alternative Delivery [REQUIRED]

This section compares the cost, timeline, and competency profile of the AI-assisted report generation approach against two alternative delivery models: third-party contractor engagement and in-house FTE execution. This data supports executive decision-making and budget justification for the AI-assisted security review program.

**Assumptions and Methodology:**

The comparison below uses the following baseline assumptions. Adjust rates to reflect current {ORG_SHORT} procurement rates and labor agreements when populating the table.

- **AI-Assisted (current model):** The CISO or designated analyst interacts with Claude (or equivalent AI tool) to generate the complete {ORG_SHORT} Security and Impact Report. The analyst provides subject matter context, reviews AI output, and validates findings. AI handles research, analysis, NIST mapping, formatting, and report assembly. Total human effort is review and validation time.
- **Third-Party Contractor:** An external cybersecurity consulting firm is engaged to perform the equivalent security assessment and produce the report. Assumes SOW scoping, vendor selection, kickoff, delivery, and review cycles. Typical rate range: $175–$350/hour depending on firm tier and clearance requirements.
- **In-House FTE:** An existing {ORG_SHORT} staff member performs the assessment. Assumes the FTE is approximately 50% capable for the scope of work (general security knowledge, familiar with {ORG_SHORT} environment) but would need to engage SME contractors (CTRs) for 25–50% of the specialized analysis (NIST 800-53 mapping, FedRAMP assessment, regulated data framework evaluation, WCAG compliance) depending on the complexity of the asset under review.

**Cost and Effort Comparison:**

| Delivery Model | Estimated Hours | Hourly Rate | Estimated Cost | Timeline | Competency Coverage | Key Assumptions |
|---|---|---|---|---|---|---|
| **AI-Assisted** (analyst + Claude) | [X] hrs analyst review + AI generation | AI: $[X.XX] (token cost from 9.2) / Analyst: $[RATE]/hr | **$[TOTAL]** | [X hours / X days] | Full scope — AI covers NIST mapping, data framework scan, WCAG, formatting; analyst validates | Analyst provides context and validates; AI performs bulk analysis |
| **Third-Party Contractor** | [X–X] hrs | $[175–350]/hr | **$[X,XXX–$X,XXX]** | [X–X weeks] | Full scope with SME depth | Includes SOW, kickoff, analysis, draft, revision, final delivery; assumes contractor has relevant certifications |
| **In-House FTE** | [X–X] hrs FTE + [X–X] hrs CTR/SME | FTE: $[RATE]/hr / CTR: $[RATE]/hr | **$[X,XXX–$X,XXX]** | [X–X weeks] | FTE: ~50% capable; CTR/SME backfill: 25–50% of specialized work | FTE handles general assessment, asset intake, report structure; CTRs engaged for NIST deep-dive, FedRAMP, regulated data frameworks, WCAG |

**Competency Gap Analysis (In-House FTE Model):**

| Assessment Area | FTE Competency | SME/CTR Required? | Estimated CTR Hours | Notes |
|---|---|---|---|---|
| Asset intake and architecture review | High | No | 0 | FTE familiar with {ORG_SHORT} environment |
| NIST 800-53 Rev 5 control mapping | Medium | Yes — 25–50% | [X–X] hrs | Requires deep familiarity with control applicability and evidence standards |
| Regulated data framework assessment (FTI, SSA, CJIS, HIPAA, PCI) | Low–Medium | Yes — 50% | [X–X] hrs | Requires specialized knowledge of federal data handling agreements and state-specific requirements |
| FedRAMP/StateRAMP vendor evaluation | Low | Yes — 50% | [X–X] hrs | Requires familiarity with authorization packages and continuous monitoring |
| WCAG 2.1/2.2 accessibility compliance | Low | Yes — 50% | [X–X] hrs | Requires accessibility testing expertise and WCAG criterion-level knowledge |
| Report formatting and delivery | High | No | 0 | FTE capable with template |
| **Total CTR/SME estimate** | — | — | **[X–X] hrs** | Engagement model: hourly CTR or T&M task order |

**Value Summary:**

[One paragraph comparing the three models on cost, speed, consistency, and scalability. Highlight that the AI-assisted model produces reports at a fraction of the cost and timeline while maintaining consistency through the standardized instruction file. Note that the AI model also creates a reusable audit trail (token cost data, session logs) that the other models do not provide by default. Acknowledge limitations: AI output requires human validation, cannot replace professional judgment for novel or ambiguous findings, and the cost comparison is most favorable for standardized assessments rather than bespoke engagements.]

---

*{ORG_SHORT} Module — Cost Analysis | Parent: Security Impact Report AI Instructions*
