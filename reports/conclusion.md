# Conclusion: Answering the Brief

This document exists to answer the three questions from the Zion Tech Hub Data Challenge brief directly, in one place, pulling together the strongest evidence from `findings_summary.md`, `recommendations.md`, and `assumptions.md` into a single set of final answers. Read this first if you only have time to read one document.

---

## 1. Where should we put our ad budget, and on whom?

**Channel split:**

| Channel | Share | Why |
|---|---|---|
| X (Twitter) | 55% | Only channel with genuine spike-adjusted growth between cohorts. Strongest reach outside Nigeria. |
| LinkedIn | 30% | Most stable channel across both cohorts. Disproportionately strong for Healthcare Data Analytics. |
| Facebook / Instagram (test budget) | 10% | Registrations vanished in Cohort 10. A small test answers cheaply whether that was a real drop-off or just inactivity. |
| Referral incentive | 5% | Small, steady organic signal already present in both cohorts, worth actively encouraging rather than ignoring. |

No budget is recommended for WhatsApp as an acquisition channel, given its spike-adjusted decline from 28.9% to 7.0% of registrations.

**Who to target:**

Cohort 10's occupation breakdown (the only cohort with usable occupation data) shows the registrant base is not dominated by any single professional group:

| Occupation | Count | Share |
|---|---|---|
| Student / Graduate | 38 | 22.8% |
| Tech / Data | 22 | 13.2% |
| Business / Entrepreneurship | 19 | 11.4% |
| Finance / Accounting | 15 | 9.0% |
| Administrative / Management | 14 | 8.4% |
| Other / Skilled Trade | 13 | 7.8% |
| Sales / Marketing / Customer Service | 10 | 6.0% |
| Unemployed | 10 | 6.0% |
| Healthcare | 9 | 5.4% |

Together, Students/Graduates, Tech/Data professionals, and Business/Entrepreneurship registrants make up 45.4% of Cohort 10, nearly half the cohort. This is the audience the budget above should actually be reaching: early-career and career-transition professionals looking to build a technical or business skill, not a niche specialist audience. It also puts the LinkedIn/Healthcare pattern in perspective: Healthcare professionals are only 5.4% of registrants by occupation, so LinkedIn's skew toward the Healthcare Data Analytics *course* is better read as a course-interest signal tied to the founder's personal brand (see Recommendation 7), not evidence that healthcare workers are the primary audience to target broadly.

**Timing:** both cohorts show heavy conversion clustering near the registration deadline. Ad spend should be weighted toward the final week of the registration window rather than spread evenly, to meet demand where it already concentrates.

---

## 2. What should we do differently to grow the community and fill Cohort 11?

Seven specific, actionable moves (full detail in `recommendations.md`):

1. **Clarify course selection upfront.** 64.9% of repeat registrants switched their course choice between cohorts, a real source of friction a short guide would fix.
2. **Investigate the WhatsApp decline.** A drop from 28.9% to 7.0% of registrations is too steep to be routine and needs a direct explanation before deciding whether to keep investing there.
3. **Plan a deliberate deadline push.** Both cohorts convert heavily near the close date. Build a campaign around that instead of letting it happen by accident.
4. **Build a referral program on LinkedIn's base.** LinkedIn's stability across cohorts suggests a loyal, returning audience, exactly the kind referral programs work best on.
5. **Look into the Healthcare Data Analytics decline.** Down 6.7 points even after controlling for new course additions in Cohort 10.
6. **Treat international growth as an X and LinkedIn problem, not a WhatsApp one** (expanded in Question 3 below).
7. **Lean into the founder's personal LinkedIn brand.** Godsent's own background as a healthcare data analyst plausibly explains LinkedIn's Healthcare skew, and more consistent story-sharing there is a zero-cost lever.

---

## 3. Where and how should we grow organically outside Nigeria?

**The specific country: Kenya.**

Country data across both cohorts:

| Country | Cohort 9 | Share | Cohort 10 | Share |
|---|---|---|---|---|
| Nigeria | 621 | 56.3% | 103 | 61.3% |
| South Africa | 106 | 9.6% | 11 | 6.5% |
| Ghana | 106 | 9.6% | 9 | 5.4% |
| Kenya | 91 | 8.2% | 20 | 11.9% |
| Uganda | 30 | 2.7% | 6 | 3.6% |

South Africa and Ghana were tied for the strongest international markets in Cohort 9, but both fell sharply in Cohort 10, Ghana in particular dropped from a tie for first to nearly last among international markets. Kenya moved the opposite direction: from third place in Cohort 9 to the clear leading international market in Cohort 10, nearly double South Africa's share and more than double Ghana's. Kenya is the only international market that grew, in both absolute registrants and share of cohort, while every other international market contracted.

**What would move the needle in Kenya:** the channel data already shows the answer. X (Twitter) and LinkedIn, not WhatsApp, are what reach registrants outside Nigeria (see `findings_summary.md`), so the same 55/30 channel weighting from Question 1 applies directly to a Kenya-focused push, no new channel strategy is needed, just geographic targeting layered onto the existing plan. Beyond ad targeting, the referral program recommended in Question 2 (item 4) is worth testing specifically among Kenyan LinkedIn registrants first, since a loyal, stable channel in a growing market is exactly where referral loops compound fastest.

---

*Every figure above is pulled directly from the cleaned datasets in `data/processed/`. Full methodology and judgment calls are documented in `reports/assumptions.md`.*