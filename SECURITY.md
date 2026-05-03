# Security Policy

## Reporting a vulnerability

If you discover a security issue in this toolkit — for example, a prompt-injection vector in the AI instructions, a leaked credential in an example file, or a flaw in the Step 0 attestation logic that could be exploited to bypass data-handling controls — please report it privately rather than opening a public issue.

**Preferred channel:** [GitHub Security Advisories](https://docs.github.com/en/code-security/security-advisories/repository-security-advisories/about-repository-security-advisories) on this repository (Security tab → "Report a vulnerability"). This routes the report only to the maintainers and gives us a private space to coordinate a fix.

We aim to acknowledge reports within 5 business days and to publish a fix or mitigation within 30 days for high-severity issues.

## Scope

In scope:

- Prompt-injection vectors in the Main Instructions file or any module that could cause the AI to leak data, bypass the Step 0 gate, or produce unsafe output
- Hard-coded secrets, credentials, internal hostnames, or PII in any file in this repository
- Logic flaws in the configuration substitution that could result in tokens leaking into rendered reports
- Vulnerabilities in any helper script (`configure.sh`, parsers in the Cost Analysis module)

Out of scope:

- The Step 0 attestation gate is documented as a *procedural* control, not authentication. The AI cannot cryptographically verify an attestation block. This is a known design limitation, not a vulnerability — adopters are expected to pair this gate with their own governance.
- Issues in third-party tools the toolkit references (Microsoft 365, CrowdStrike, Qualys, etc.) belong to those vendors.
- Issues in user-supplied configurations (`config.yaml`) are the adopter's responsibility.

## Disclosure preference

We follow coordinated disclosure. We'll work with you to publish a fix and CVE (if applicable) before any public discussion of the issue.
