# osar-toolkit-v1
Open-source toolkit for AI-assisted Security and Impact Reports — applications, vendor SaaS, source-code releases. Hub-and-spoke prompt architecture: orchestrator + 7 analysis modules (NIST 800-53, POA&amp;M, vendor compliance, WCAG, cost, infra, source code). Model-agnostic baseline; portable to any LLM. Apache-2.0.

# Open Security Assessment Report (OSAR) — AI-Assisted Reporting Toolkit to generate a Security Impact Report (SIR)

An open-source, organization-agnostic toolkit for producing high-quality **security and impact reports** on technology assets — applications, vendor SaaS, infrastructure changes, and source-code releases — using a large-language-model assistant.

The toolkit is structured as a **hub-and-spoke prompt system**: a single Main AI Instructions file orchestrates the report and references six specialized analysis modules. Each module covers one analytical lens: cost, infrastructure impact, NIST 800-53 control inheritance, plan-of-action-and-milestones (POA&M), source-code analysis, vendor compliance, and WCAG accessibility. The output is a defensible, decision-grade report suitable for security review boards, change-advisory boards, and risk committees.

## Who this is for

Security teams, GRC teams, and CISOs in any organization — public-sector, private-sector, higher-ed, healthcare — who want a repeatable AI-assisted process for producing security-impact reports without paying for a vendor SaaS or building one from scratch. The toolkit ships with placeholder tokens for organization-specific values (org name, policy numbering, vendor stack, applicable laws), so adoption is a one-time configuration pass rather than a code rewrite.

## What's in the box

```
security-impact-report/
├── Security_Impact_Report_AI_Instructions.md   # the orchestrator — load this in your AI session
├── modules/
│   ├── Module_Cost_Analysis.md
│   ├── Module_Infrastructure_Impact.md
│   ├── Module_NIST_800-53_Controls.md
│   ├── Module_POAM.md
│   ├── Module_Source_Code_Analysis.md
│   ├── Module_Vendor_Compliance.md
│   └── Module_WCAG_Accessibility.md
├── assets/
│   └── Cover_Logo_Base64.txt                   # neutral placeholder — replace with your own
├── examples/
│   └── Example_Report_AcmeStateCyber.md        # fully-rendered sample using a fictional org
├── config.example.yaml                         # token map — copy to config.yaml and fill in
├── configure.sh                                # applies your config.yaml to the source files
├── LICENSE                                     # Apache-2.0
├── SECURITY.md                                 # vulnerability disclosure
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── CHANGELOG.md
```

## How it works

1. You load the Main AI Instructions file into an AI assistant session.
2. You provide source material on the asset under review — a SOC 2 report, an architecture diagram, a vendor questionnaire, source code, etc.
3. The assistant runs through a structured workflow: data-classification gate, scoping, then each module in turn.
4. The output is a single decision-grade report with a cover page, executive summary, control inheritance assessment, POA&M, cost model, infrastructure impact analysis, accessibility findings, and a recommendation.

## Quick start

```bash
# 1. Clone the repo
git clone <your-fork-url> security-impact-report
cd security-impact-report

# 2. Copy the token map and fill in your organization's values
cp config.example.yaml config.yaml
$EDITOR config.yaml

# 3. Apply your configuration to a working copy
./configure.sh

# 4. Drop your own logo into assets/Cover_Logo_Base64.txt
#    (a neutral placeholder ships with the repo)

# 5. Load the configured Security_Impact_Report_AI_Instructions.md into your AI session
#    along with the modules/ directory and start your first report
```

## Configuration tokens

The source files use curly-brace tokens for every value an adopter is expected to localize. Examples:

| Token | What it replaces |
|---|---|
| `{ORGANIZATION}` | Full agency or company name |
| `{ORG_SHORT}` | Short label used in headers, footers, IDs |
| `{DIVISION}` | Sub-org (e.g., "Cyber Security Division") |
| `{MAINTAINER_NAME}`, `{MAINTAINER_TITLE}`, `{MAINTAINER_EMAIL}` | Document maintainer metadata |
| `{IR_CONTACT_EMAIL}` | Incident-response inbox |
| `{POLICY_REF:<topic>}` | Your internal policy number for that topic |
| `{STANDARD_REF:<topic>}` | Your internal standard number |
| `{IDP}`, `{MDM}`, `{EDR}`, `{VULN_SCANNER}`, `{TENANCY}`, `{HOSTING_ENV}` | Your security-tool stack |
| `{STATE_PRIVACY_LAW}`, `{STATE_ACCESSIBILITY_LAW}`, `{STATE_PUBLIC_RECORDS_LAW}` | Applicable jurisdictional statutes |
| `{VENDOR_SECURITY_ADDENDUM}` | Your procurement security exhibit |
| `{COLOR_PRIMARY}`, `{COLOR_ACCENT}` | Your brand colors |
| `{LOGO_DATA_URI}` | Your cover-page logo |

The full token list is in `config.example.yaml`.

## Important security notes for adopters

The Main Instructions file includes a **Step 0 attestation gate** that asks the AI to refuse processing of regulated data unless the user uploads a signed authorization block. This is a **procedural control, not authentication** — the model cannot cryptographically verify the attestation and a determined bad-faith user can craft a fake one. Pair this gate with your organization's existing data-handling governance and access controls.

The default behavior on a *disputed* regulated-data finding is **refuse-and-escalate**, not proceed. Adjust this default only if your organization's governance explicitly permits.

## Origin and design philosophy

This toolkit was designed from a need by a public-sector CISO to enahnce governance programs and generalized for the open-source community. The hub-and-spoke structure is deliberate: it lets you adopt the modules you need, swap in your own, and keep the orchestrator stable across reports.

## Contributing

See `CONTRIBUTING.md`. New analysis modules, jurisdictional law mappings, and example reports are especially welcome.

## License

Apache-2.0 — see `LICENSE`.
