# Changelog

All notable changes to this project are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses [Semantic Versioning](https://semver.org/).

## [1.4.0] - 2026-11-11

Job offer mode (issue #5). Builds on 1.3.1 (PR #6).

### Added
- **Job offer mode** for any job offer abroad:
  - who pays the permit or visa, with official links checked 2026-11-11: UK (employer pays sponsor costs and the Immigration Skills Charge; worker pays only their own visa fee on gov.uk; sponsor register), Canada (employer pays the LMIA fee and may not recover it or recruitment fees; Job Bank; Canadian Anti-Fraud Centre), Poland (employer applies to the voivode via praca.gov.pl; agencies may not charge job seekers; KRAZ), Germany (fees only to official bodies; marked verify);
  - pay vs typical pay, always labelled *estimate*;
  - contract / offer-letter checklist: legal name = register entry, address, signatory, e-mail domain, no fee clause, passport not kept, job and country match;
  - business-register lookup and call-back on the register's number: Companies House, KRS/CEIDG, Handelsregister/Unternehmensregister, EU e-Justice registers search, Corporations Canada, Azerbaijan taxpayer search on taxes.gov.az (unverified links are marked verify);
  - plain trafficking warning and the national anti-trafficking hotline, only when its official page is opened (known: Azerbaijan 152, Nigeria NAPTIP);
  - job verdict rule: `Likely legit` only with the employer's register entry opened (UK: also the sponsor register); passport/ID scan before an interview = data harvesting.
- Optional `Employer check:` line in the VERDICT block (job mode only; then at most 4 red-flag bullets so the block stays ≤ 10 lines).
- Job-mode footer: Job & Application Copilot, "a separate Codelady Abroad skill (coming to Agensi)", optional, no link. It is not listed on Agensi yet.
- Evals JO-1 to JO-4, with blind-run results in `tests/blind-run-2026-11-11-job-offer.md`.

## [1.3.1] - 2026-11-11

Daily review fixes from a blind B1-phone user test.

### Changed
- Golden rule 1: a search snippet may support a red flag when marked "search snippet says" (never `Likely legit`); a clear lookalike domain counts even when the embassy page will not load.
- Domain age: a failed lookup (error, blocked, empty) gives `not checked (lookup failed)` plus the 2-step check.
- Job abroad: a website and a contract PDF prove nothing; check the official business register and call the number listed there; plain-words trafficking warning.
- README version badge corrected (was 1.1.0).
- Phone mode: VERDICT block at most 10 short lines; plain words instead of "registrable domain", "chargeback", "2FA"; footer translated into the user's language.

### Added
- Workflow step 8: when the link, sender, payment method or "did you apply?" is missing, give the verdict and end with one short question.
- Evals DR-1 to DR-3.

## [1.3.0] - 2026-11-10

### Added
- **Domain age** step (issue #3), one signal and never a verdict on its own. It runs on a website domain that fails the domain check. The order is: a connected WHOIS/RDAP/urlscan tool, then the public RDAP record (rdap.org / lookup.icann.org) with web access, then a 2-step manual check for the user (lookup.icann.org, then paste the "Created" date). The skill never invents or estimates an age.
- Verdict rule: a domain younger than 6 months that claims to be a government body, visa centre, university or scholarship programme is a strong flag. It is always listed next to the domain-check result.
- An old domain proves nothing. Official domains get no age-based doubt. Hidden WHOIS owners are not a flag. Owner details from WHOIS are never repeated.
- Optional `Domain age:` line in the output format, and a plan-compatibility line for hosts with no tool and no web access.
- Evals DA-1 to DA-3.

### Fixed (blind eval rounds 1-3)
- The age bullet says "strong flag" in words.
- Without web access, the official domain is named as unverified so the user can compare.
- Every visa-appointment answer says in Safe next step that appointments are free and never sold by agents.
- The first line is one single action (one step, no "and"), including when declining to label a person.

### Unchanged
- Rule 7: only the registrable domain is looked up, never the suspicious link. No network script was added; the package stays Markdown-only.

## [1.2.0] - 2026-11-10

### Fixed (blind eval round 1)
- Round 2: domain flag names the site the embassy/programme links to; a page without a fee mention is not proof it's free; portal subdomains only from opened pages; official quotes translated; bank step allowed as the next-action line.
- Search-snippet-only pages count as not opened and never support `Likely legit`.
- Visa appointments: What's normal names the booking provider the embassy links to (VFS, TLScontact, BLS or government portal), not always vfsglobal.com.
- No unchecked named authorities in reporting; ALREADY PAID doesn't assume a card and keeps VERDICT ≤ 3 lines; video-call viewings are not proof for housing.

### Added
- **Plan compatibility** section. Free plan fully supported: without web search the verdict is never `Likely legit` and fee rules are marked not checked. One check per message on tight limits.
- Evals PC-1 to PC-3 and SC-18.

### Fixed
- Visa-centre fees: appointments are free and never sold by agents, but some countries require a prepaid **service fee** on the visa centre's own site. That alone is no longer treated as a scam flag (source: vfsglobal.com/en/donotfallforfraud).

## [1.1.0] - 2026-11-09

Research-driven must-have features. See `docs/research.md`.

### Added
- **Verdict rules**: when each of `Likely legit` / `Suspicious` / `Likely scam` applies; `Likely legit` requires an official page opened in the session on the official domain; official pages pasted by the user are recognised as legit, without invented doubt; no web access means no `Likely legit`.
- **Domain check** method (registrable domain vs the one the embassy or programme links to; extra words, typos, other endings, brand in a subdomain, free mailboxes).
- **Red flags quote the triggering words**; expanded catalogue: slot sellers, visa-portal password requests, "complete packages", job-abroad fees with an explicit **trafficking warning**, ESC placement fees, data harvesting.
- **Reporting** section: platform, impersonated organisation, visa-centre fraud page, national cybercrime/consumer body looked up in session (or marked verify), local police and own embassy when abroad.
- **Already paid / shared** block in a fixed order, with a **recovery-scam warning** and passport-copy advice.
- **Privacy guard**: pasted passport/ID/card numbers, passwords or codes are never repeated; the user is told not to share them.
- **No unsourced caveats**: exceptions to an official rule only when the official page says so (found in blind evals, SC-8).
- **Special requests**: declines to label named people as criminals and offers a neutral warning text instead; refuses fake documents and gives legitimate alternatives.
- **Language and length**: answers in the user's language with the English verdict label in brackets; phone mode with the next action first, prose outside blocks of 8 lines or fewer, and at most 5 red-flag bullets.
- `docs/research.md` (condensed research, competitor gaps, must-have mapping) and `tests/evals.md` (17 cases).

### Changed
- Footer is a single line combining "not legal advice" and the optional related skills.
- Examples updated to the v1.1.0 output format (next action first).
- `README.md`: v1.1.0 features.

## [1.0.0] - 2026-11-09

### Added
- `SKILL.md`: the Scholarship & Visa Scam Checker skill, with golden rules (no "legit" without an official source, describe signals and never accuse, verify only through official contacts, privacy, user's language, not legal advice), a 5-step workflow, a red-flag list and a fixed output format (`VERDICT` + red flags + what's normal + safe next step + report, plus an `ALREADY PAID / SHARED` block).
- `templates/`: verification e-mail to an official office, scam report checklist, already-paid recovery checklist.
- `examples/`: two fictional cases (scholarship "pre-selection" fee; lookalike visa-appointment site after payment).
- `scripts/build-agensi-zip.ps1`: builds the marketplace upload package.
- `README.md`, MIT license.
