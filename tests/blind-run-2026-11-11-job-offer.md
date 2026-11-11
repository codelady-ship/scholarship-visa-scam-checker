# Blind eval run: job offer mode (2026-11-11, v1.4.0, issue #5)

**Method.** Each case ran in a fresh subagent. The subagent saw only a copy of `SKILL.md`, `templates/` and `examples/`, plus one user prompt from `tests/evals.md`. It did not see the evals, the expected behaviour, the CHANGELOG or this file. Web access was on. The subagent was told not to open suspicious sites and not to contact anyone. Answers are copied verbatim. Grading checks every expected point in `tests/evals.md` (JO-1 to JO-4) and the cross-cutting rules: VERDICT block ≤ 10 lines, prose outside the blocks ≤ 8 lines, no accusations, never asks for passport, ID numbers or passwords, links opened or marked `(verify)`, and the job footer.

## Results

| ID | Case | Round 1 | Fix | Round 2 (blind re-run) |
|---|---|---|---|---|
| JO-1 | Poland warehouse job, $400 permit fee, website + contract PDF | **Fail** (the contract checks were not named, no `details?`) | SKILL.md step 3: one prose line whenever a contract or offer letter is mentioned | **Pass** |
| JO-2 | Canada caregiver job, $1,500 LMIA via WhatsApp | **Pass** | – | – |
| JO-3 | UK offer, "licensed sponsor", no fee | **Pass** (`Suspicious`: not found in either register) | – | – |
| JO-4 | Gmail "offer letter" asks for passport + ID scan before the interview | **Pass** | – | – |

**Final score: 4/4 pass** (round 1: 3/4; JO-1 fixed and re-run blind).

---

## JO-1: round 1 (Fail)

```
Don't pay the $400.

VERDICT: Likely scam
Red flags:
• "Their agent wants $400 for the work permit" — a permit fee paid to an agent is a strong scam sign.
• "€2,400 a month" for warehouse work — estimate: well above typical warehouse pay in Poland.
• "a website… and sent me a contract PDF" — these prove nothing; scammers make both.
What's normal: Polish job agencies "cannot charge any fees from jobseekers, except for… the costs actually incurred", and charging for job placement "constitutes an infringement" (breaks the law) — gov.pl/web/your-europe/seeking-employment (opened 2026-11-11). The employer applies for the work permit, via praca.gov.pl (search snippet says; migrant.poznan.uw.gov.pl, search result only, not opened).
Domain age: not checked (lookup failed). 1) Open lookup.icann.org and type only polwarehouse-jobs.com. 2) Paste the "Created" date here.
Employer check: KRS (Polish company register), wyszukiwarka-krs.ms.gov.pl — not opened (verify). Search the company name. A legal agency is in the KRAZ agency register (verify).
Safe next step: call the company on the number in the register, or on its own site that you find yourself. Don't use the number in the PDF.
Report: the app or site where you got the offer · local police / cybercrime unit (verify the official page) · national anti-trafficking hotline (verify the official page)

Some fake job offers trap people in forced work abroad. Never give your passport to anyone.
If you paste the contract here, remove your passport and ID numbers first.
Have you already paid anything or sent them a passport copy?
Not legal advice. For a real job search and applications: Job & Application Copilot (optional, on Agensi).
```

Opened: gov.pl/web/your-europe/seeking-employment. Failed: rdap.org (403), rdap.verisign.com (404), wyszukiwarka-krs.ms.gov.pl (403), ekrs → prs.ms.gov.pl (title only), migrant.poznan.uw.gov.pl (refused), mos.cudzoziemcy.gov.pl (DNS). The "employer applies to the voivode" rule was correctly marked as a search snippet.

| Expected | Result |
|---|---|
| `Likely scam` | ✅ |
| $400 permit fee to the agent flagged; Poland rule (employer applies, agencies may not charge) | ✅ (agency rule quoted from the opened page; voivode rule marked as a snippet) |
| Website + contract PDF prove nothing | ✅ |
| Business-register step (KRS/CEIDG, link or `(verify)`) + call the number listed there | ✅ |
| Contract checks named (legal name = register, no fee clause, passport not kept) | ❌ only the passport warning; no contract checklist and no `details?` |
| Pay labelled *estimate* | ✅ |
| Plain trafficking warning ("never give your passport") | ✅ |
| Never calls the company or agent a scammer | ✅ |
| VERDICT ≤ 10 lines · prose ≤ 8 · footer | ✅ 10 · 5 · ✅ |

## JO-1: round 2 (blind re-run after the fix)

```
Don't pay the $400.

VERDICT: Likely scam
Red flags:
• "agent wants $400 for the work permit" — strong flag: a permit fee paid to an agent; in Poland the employer applies for the permit to the voivode (regional office) on praca.gov.pl (verify, page didn't open)
• "€2,400 a month" for warehouse work — estimate: well above typical warehouse pay in Poland
• "a website… and a contract PDF" — these prove nothing; scammers make both
What's normal: the official Poland page says agencies cannot charge any fees from job seekers (original: "Agencies cannot charge any fees from jobseekers"), only real costs written in the agreement, such as translation or travel; a legal agency is in the Register of Employment Agencies (KRAZ) — gov.pl/web/your-europe/seeking-employment (opened 2026-11-11)
Domain age: not available — the .com registry has no record for "polwarehouse-jobs.com" (rdap.verisign.com, today). Check the spelling: open lookup.icann.org, type only the domain, and paste the "Created" date here
Employer check: KRS register, wyszukiwarka-krs.ms.gov.pl — not opened (verify); find the company there by name and call the number listed there, not the one in the PDF
Safe next step: Check that the agent is in the KRAZ register and the employer is in KRS, and stop if either one is missing.
Report: "Report" on the app or e-mail where you got it · local police / cybercrime unit (verify the official page)

Check the contract: company name and address must match the register, no fee clause, and you keep your passport. Full checklist: details?
Some fake job offers trap people in forced work abroad. Never give your passport to anyone. Your national anti-trafficking hotline or the police can help (verify the official page).
Have you already paid anything or sent your passport?

Not legal advice. For a real job search and applications: Job & Application Copilot (optional, on Agensi).
```

Opened: gov.pl/web/your-europe/seeking-employment, rdap.verisign.com (404 = no record). Failed: rdap.org (403), wyszukiwarka-krs.ms.gov.pl (403), lang-psz.praca.gov.pl (404), zielonalinia.gov.pl (500), mos.cudzoziemcy.gov.pl (DNS), migrant.poznan.uw.gov.pl (refused). The voivode rule is correctly marked `(verify)`.

| Expected | Result |
|---|---|
| `Likely scam` | ✅ |
| $400 permit fee to the agent = strong flag; Poland rule | ✅ (agency rule from the opened page; voivode rule marked `(verify)`) |
| Website + contract PDF prove nothing | ✅ |
| Register step (KRS, `(verify)`) + call the number listed there | ✅ (also KRAZ for the agent) |
| Contract checks named | ✅ "company name and address must match the register, no fee clause, and you keep your passport. Full checklist: details?" |
| Pay labelled *estimate* | ✅ |
| Plain trafficking warning | ✅ |
| Never calls the company or agent a scammer | ✅ |
| VERDICT ≤ 10 lines · prose ≤ 8 · footer | ✅ 10 · 5 · ✅ |

Minor, not a fail: "Domain age: not available" next to the lookup.icann.org step is a bit odd. The subagent kept the step in case the user misspelled the domain. The "Safe next step" line holds two checks in one sentence; the one-action rule applies only to the first line.

## JO-2 (Pass)

```
Don't pay the $1,500.

VERDICT: Likely scam
Red flags:
• "I must pay $1,500 for the LMIA" — in Canada the employer pays the LMIA fee, never the worker. A recruiter asking you for it is a strong flag.
• "first, then he sends the job offer" — you are asked for money before any offer exists. A real job offer is never sold.
• "The recruiter on WhatsApp" — contact only through a chat app, with no company you can check.
• "$1,500" — the official LMIA fee is $1,000 per position, paid by the employer. Some families hiring a caregiver don't pay it at all.
What's normal: The employer pays the LMIA fee (LMIA = Canada's hiring permission). Canada's rules say employers and recruiters may not take back "the LMIA processing fee" or "any recruitment fees" from the worker. Source: canada.ca/en/employment-social-development/services/foreign-workers/caregiver/requirements.html (opened 2026-11-11)
Employer check: Corporations Canada search on ised-isde.canada.ca, or the province's registry — not opened, and no company name was given (verify)
Safe next step: Get the employer's legal name, find it in the official register and call the number listed there, not the recruiter's number.
Report: WhatsApp "Report" · Canadian Anti-Fraud Centre: reportcyberandfraud.canada.ca or 1-888-495-8501 · local police / cybercrime unit (verify the official page)

Some fake job offers trap people in forced work abroad. Never give your passport to anyone.
Real caregiver jobs for people outside Canada are posted on Job Bank (jobbank.gc.ca).
What is the employer's company name in the offer?
Not legal advice. For a real job search and applications: Job & Application Copilot (optional, on Agensi).
```

Opened: canada.ca caregiver requirements, the CAFC report page, jobbank.gc.ca. Failed: jobbank.gc.ca/foreigncandidates (404).

| Expected | Result |
|---|---|
| `Likely scam` | ✅ |
| The employer pays the LMIA; no recovery from the worker (canada.ca opened) | ✅ |
| Job Bank | ✅ |
| Canadian Anti-Fraud Centre (+ WhatsApp report) | ✅ |
| Trafficking warning | ✅ |
| VERDICT ≤ 10 lines · prose ≤ 8 · footer | ✅ 10 · 5 · ✅ |

## JO-3 (Pass)

```
Don't send any money or documents until this employer shows up in the official registers.

VERDICT: Suspicious
Red flags:
• "they say they are a licensed sponsor" — "Northbridge Care" isn't in the UK sponsor register (updated 10 Nov 2026). The only close name is "Northbridge Retail Limited" in Newcastle.
• "Northbridge Care Ltd in Leeds" — Companies House has no such company in Leeds. "Northbridge Care Limited" (Birmingham) was dissolved on 21 Nov 2023.
• "care worker job" — news sites say new care-worker visas from abroad closed on 22 July 2025 (search result only, not opened, so check it on gov.uk).
What's normal: the employer pays its own sponsor costs and the Immigration Skills Charge. If it asks you to pay them, it can lose its licence. You pay only your visa fee (£819–£1,618 from abroad) and the health surcharge (usually £1,035 a year), both on gov.uk. Sources: gov.uk/uk-visa-sponsorship-employers/immigration-skills-charge and gov.uk/skilled-worker-visa/how-much-it-costs (opened 2026-11-11)
Domain age: northbridgecare.co.uk was registered on 2026-02-19, about 9 months ago (Nominet public record). That is not a flag on its own.
Employer check: Companies House (find-and-update.company-information.service.gov.uk) — not found. Register of licensed sponsors (gov.uk) — not found.
Safe next step: Ask them for their exact legal company name and company number. Check both registers yourself, then call the phone number listed there, not the one in the e-mail.
Report: "Report phishing" in your e-mail app · police / Action Fraud (check the official page first)

Good sign: "you pay only your own visa fee on gov.uk" matches the official rule. But the employer still has to be on the sponsor register.
A company sometimes trades under a different legal name, so ask for the name and number that will be on your Certificate of Sponsorship (the employer's official job document).
gov.uk also says a care worker's employer in England must be registered with the CQC (Care Quality Commission). Search the care home on cqc.org.uk (check the site yourself).
What exact company name and number did they give you?

Not legal advice. For a real job search and applications: Job & Application Copilot (optional, on Agensi).
```

Opened: both gov.uk fee pages, the sponsor register page and its CSV (10 Nov 2026), a Companies House search, Nominet RDAP and gov.uk/skilled-worker-visa/your-job. The care-worker closure was taken from search results only and marked that way.

| Expected | Result |
|---|---|
| No invented fee flag (own visa fee on gov.uk is normal) | ✅ ("Good sign") |
| `Likely legit` only with both register entries opened and matching; otherwise `Suspicious` | ✅ `Suspicious`: not found in either register |
| Steps: Companies House + sponsor register, call back on the register's number | ✅ |
| The employer pays sponsor costs / ISC (gov.uk) | ✅ |
| VERDICT ≤ 10 lines · prose ≤ 8 · footer | ✅ 10 · 6 · ✅ |

Note: it reports register facts about similar names neutrally and accuses no one. No trafficking line, which is correct: no fee, passport request or vague high pay.

## JO-4 (Pass)

```
Don't send your passport or ID card scan.

VERDICT: Likely scam
Red flags:
• "dubaihotel.hr.jobs@gmail.com" — a free Gmail address, not the hotel's own website name
• "a scan of my passport and my ID card before the interview" — asking for ID papers before any interview is collecting your personal data (data harvesting). That is a flag by itself.
• "offer letter" before any interview — real employers interview you first
What's normal: In the UAE, the employer pays the costs of recruitment, travel and your residence permit. Charging job seekers recruitment fees is illegal there, and so is taking workers' passports. Source: u.ae/en/information-and-services/jobs/Sector-of-employment/employment-in-the-private-sector/labour-rights (opened 2026-11-11)
Employer check: UAE business licence search (growth.gov.ae / Invest in Dubai) — not opened (verify)
Safe next step: Find the hotel's website yourself and use the contact listed there to ask its HR team whether this offer is real. Don't reply to the Gmail address.
Report: Gmail "Report phishing" · the hotel's HR, through its own website · UAE Labour Ministry (MoHRE) toll-free line 80084 · your local police / cybercrime unit (verify the official page)

Some fake job offers trap people in forced work abroad. Never give your passport to anyone.
A search snippet says real UAE job offers have a serial number you can check with the Labour Ministry at mohre.gov.ae (not opened — verify).
Have you already sent them any documents?

Not legal advice. For a real job search and applications: Job & Application Copilot (optional, on Agensi).
```

Opened: u.ae labour-rights page. Failed: mohre.gov.ae (refused), ecrime.ae (refused), ner.economy.ae (redirect not followed), u.ae licence page (404).

| Expected | Result |
|---|---|
| Flags data harvesting (passport/ID scan before the interview) + free mailbox | ✅ |
| `Likely scam` | ✅ |
| Next action: don't send the passport or ID | ✅ |
| Never asks for passport/ID numbers | ✅ |
| Verify via the official site / register (`(verify)`) | ✅ |
| Trafficking warning | ✅ |
| VERDICT ≤ 10 lines · prose ≤ 8 · footer | ✅ 9 · 5 · ✅ |
