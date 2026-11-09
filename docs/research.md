# Research summary (condensed)

Researched 2026-11-09. **[S]** = sourced, **[E]** = estimate or inference. Full notes with all links live in the author's research folder; the key sources are listed here.

## Top problems (frequency × harm, [E] scoring)

| # | Problem | Score | Key sources |
|---|---|---|---|
| 1 | Scholarship "pre-selected, pay a processing/insurance fee" via WhatsApp/Telegram/e-mail | 20 | [S] Stipendium Hungaricum: "applications … are free of charge" — https://apply.stipendiumhungaricum.hu/news/new/88-warning-financial-fraud-unknown-unauthorised-addresses ; [S] Erasmus+ "registration fee" scam alert — https://www.eeas.europa.eu/delegations/canada/fraud-alert-beware-erasmus-plus-scam_und_es |
| 2 | Housing deposit scams (landlord abroad, Western Union, TikTok listings) | 20 | [S] LSVb: rental-fraud reports 1.4% (2022) → 9.3% (2024) — https://www.erasmusmagazine.nl/en/2025/04/10/lsvb-increasing-number-of-student-renters-scammed/ |
| 3 | Agents selling guaranteed admission/visa; fake admission letters | 20 | [S] German ambassador to India on "complete packages" — https://theprint.in/diplomacy/come-to-germany-but-dont-trust-your-agents-too-much-warns-german-envoy-as-fraud-cases-go-up/2754541 ; [S] Canada 9,000+ fake acceptance letters — https://amp.cbc.ca/lite/story/1.7279917 |
| 4 | Lookalike visa-appointment sites, paid "slots" | 16 | [S] VFS: 900+ fraudulent sites taken down — https://www.thenationalnews.com/business/2026/09/08/visa-scam-sites-on-rise-how-they-work-and-how-to-avoid-them/ ; [S] TLScontact: appointments free, intermediaries fraudulent — https://visas-be.tlscontact.com/en-us/country/iq/vac/iqBGW2be/scam-alert |
| 5 | Oversharing passport/ID numbers and passwords | 16 | [S] UKCISA: scammers already hold passport numbers to seem credible — https://www.ukcisa.org.uk/student-advice/life-in-the-uk/frauds-and-scams/ |
| 6 | Job-abroad offers with visa/placement fees; trafficking into scam centres | 15 | [S] FTC job scams: >105,000 reports, >$513M (2024) — https://consumer.ftc.gov/jobscams ; [S] INTERPOL, victims from 66 countries — https://www.interpol.int/en/News-and-Events/News/2025/INTERPOL-releases-new-information-on-globalization-of-scam-centres ; [S] Report Fraud recruitment scams — https://www.reportfraud.police.uk/recruitment-scams/ |
| 7 | Government/embassy impersonation ("visa problem, pay a fine") | 12 | [S] UKCISA: "The Home Office does not issue financial penalties"; [S] FBI IC3 PSA 13 May 2025 — https://www.ic3.gov/PSA/2025/PSA250513 |
| 8 | Volunteer/ESC "placement" or "training" fees | 9 | [S] ESC principles: participation involves no fee (search summary); placement guaranteed for a fee is not a real project — https://youthworkshub.org/?p=15135 (secondary) |
| 9 | Recovery scams after a loss | 8 | [S] FTC refund and recovery scams — https://consumer.ftc.gov/articles/refund-and-recovery-scams |

## Competitor gaps

| Tool | Price | Gap for this niche |
|---|---|---|
| ScamAdviser | Free | Website trust scores only; no messages; doesn't know what a programme charges |
| Norton Genie, Bitdefender Scamio | Free | General consumer scams; no official "what's normal" comparison; Scamio verdicts often hedged (KSL test) |
| Google Circle to Search / Chrome scam detection | Free | Android/Chrome only; answers only when highly confident; no reporting or recovery plan |
| Agensi "Is This a Scam? Decode a Suspicious Message" | Free | Generic (bank, parcel, tax); no student/visa focus; languages not stated |
| Claude "Suspicious Email Analyzer" | Free | E-mail phishing focus; nothing on visa centres, scholarships, housing or ESC |
| Generic chatbots | $0–20 | [E] No enforced structure; may call something legit without a source, accuse named people or repeat pasted ID numbers |

**Gap [E]:** nobody combines an official-page comparison for scholarships, visa centres, universities and volunteer programmes with country reporting routes, a recovery plan that warns about recovery scams, privacy rules for ID data, and answers in the user's language.

## Must-haves → where they live in SKILL.md

| Must-have | SKILL.md section |
|---|---|
| Three-level verdict; `Likely legit` only with an official source opened | Golden rules 1, Verdict rules |
| Red flags quote the triggering words | Red-flag catalogue, Output format |
| Official "what's normal" comparison with link | Step 2, Output format |
| Domain check (exact registrable domain vs the one the embassy links) | Domain check |
| Safe next steps via official contacts only | Golden rule 3 |
| Reporting routes (platform, impersonated body, visa-centre fraud page, national body) | Reporting |
| Already-paid plan with recovery-scam warning | Already paid / shared |
| No accusations of named people | Golden rule 2, Special requests |
| Privacy guard for pasted ID numbers and passwords | Golden rule 4, Privacy guard |
| Job-abroad trafficking warning | Red-flag catalogue |
| User's language; phone mode ≤ 8 lines prose + blocks | Language and length |
| One non-pushy footer line | Output format |

Tests for each must-have: [`tests/evals.md`](../tests/evals.md).
