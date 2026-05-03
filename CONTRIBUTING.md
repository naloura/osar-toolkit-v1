# Contributing

Thanks for your interest in contributing. This toolkit is meant to be improved by the community of practitioners who actually use it. The most valuable contributions are the ones that make the toolkit more portable, more accurate, and more useful to a wider range of organizations.

## Especially welcome

- **New analysis modules** that follow the same hub-and-spoke pattern (e.g., privacy impact, threat-modeling, data-residency).
- **Jurisdictional law mappings** — adding `{STATE_PRIVACY_LAW}` / `{STATE_ACCESSIBILITY_LAW}` examples for additional U.S. states, EU member states, Canadian provinces, etc.
- **Vendor-stack examples** beyond the Microsoft + CrowdStrike + Qualys pattern shown in the included examples.
- **Fully-rendered example reports** in `examples/` against fictional organizations — showing what a finished report looks like is one of the highest-leverage things you can contribute.
- **Bug fixes** in the configuration substitution and helper scripts.

## Before you submit

1. Open an issue first if your change is non-trivial, so we can align on direction.
2. Keep the source files org-agnostic — every value an adopter would reasonably want to change should be a `{TOKEN}`, not a hard-coded string.
3. Add or update the entry in `config.example.yaml` for any new tokens you introduce.
4. Grep your changes for any organization-specific values (your own org name, internal policy numbers, real `.gov` or `.com` email addresses, IP addresses, hostnames) before pushing. The repository is meant to be org-agnostic.

## Pull request checklist

- [ ] No hard-coded organization, person, or jurisdictional values (use `{TOKEN}`s)
- [ ] No secrets, credentials, internal hostnames, or PII
- [ ] `config.example.yaml` updated for any new tokens
- [ ] Examples directory unaffected, or updated consistently if structure changed
- [ ] CHANGELOG.md updated under "Unreleased"

## Code of conduct

See `CODE_OF_CONDUCT.md`. Be kind, assume good faith, and remember that other contributors may be working in very different organizational contexts than yours.
