# Changelog

All notable changes to this toolkit will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] — 2026-05-02

### Added

- Initial open-source release.
- Main AI Instructions file (`Security_Impact_Report_AI_Instructions.md`) — orchestrates a hub-and-spoke prompt system that produces a decision-grade security and impact report.
- Six analysis modules under `modules/`:
  - Cost Analysis
  - Infrastructure Impact
  - NIST 800-53 Controls (with control inheritance worked example)
  - Plan of Action and Milestones (POA&M)
  - Source Code Analysis
  - Vendor Compliance
  - WCAG Accessibility
- Configuration token system (`config.example.yaml`) so adopters can localize organization name, policy library, vendor stack, applicable laws, and brand assets without editing source files.
- Helper script (`configure.sh`) that applies a `config.yaml` to a working copy of the source files.
- Neutral placeholder cover-page logo (`assets/Cover_Logo_Base64.txt`).
- Fully-rendered example report (`examples/Example_Report_AcmeStateCyber.md`) against a fictional organization, plus a styled PDF rendering (`examples/Example_Report_AcmeStateCyber.pdf`) so adopters can see the finished output without configuring the toolkit.
- OSS hygiene files: `LICENSE` (Apache-2.0), `SECURITY.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`.

### Security

- Step 0 attestation gate documented as a *procedural* control, not authentication. Adopters are explicitly warned that the model cannot cryptographically verify the attestation block and that the gate must be paired with their own governance.
- Default behavior on disputed regulated-data findings is **refuse-and-escalate**, not proceed.
