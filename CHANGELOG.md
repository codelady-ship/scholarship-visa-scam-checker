# Changelog

All notable changes to this project are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses [Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-11-09

### Added
- `SKILL.md`: the Scholarship & Visa Scam Checker skill, with golden rules (no "legit" without an official source, describe signals and never accuse, verify only through official contacts, privacy, user's language, not legal advice), a 5-step workflow, a red-flag list and a fixed output format (`VERDICT` + red flags + what's normal + safe next step + report, plus an `ALREADY PAID / SHARED` block).
- `templates/`: verification e-mail to an official office, scam report checklist, already-paid recovery checklist.
- `examples/`: two fictional cases (scholarship "pre-selection" fee; lookalike visa-appointment site after payment).
- `scripts/build-agensi-zip.ps1`: builds the marketplace upload package.
- `README.md`, MIT license.
