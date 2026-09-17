# Assumptions and Data Cleaning Decisions

This document brings together every judgment call made while cleaning and analyzing the Cohort 9 and Cohort 10 registration data, and the reasoning behind each one. Nothing here was guessed silently; every decision below was made only after checking what the data actually showed, and each one is something a stakeholder could reasonably question and get a defensible answer to.

## 1. The 55 rows with no Name (Cohort 9) were kept, not dropped

At first glance, 55 missing names look like a data quality problem. But every one of those rows had an email address with a username exactly 4 characters long, with zero variation across all 55, compared to the normal, varied-length email usernames everywhere else in the dataset. That's not what random missing data looks like; it's what a deliberate, systematic redaction looks like, consistent with how the challenge brief already told us phone numbers had been de-identified elsewhere in the dataset.

**Decision:** These rows were kept. Every field actually used in this analysis (Channel, Course, Country, Timing) was fully present on them. Name was never needed for any part of the analysis, so its absence has no effect on the findings.

## 2. Duplicate registrants were identified using Phone + Email together, not Phone alone

Phone number alone flagged 729 "duplicate" rows in Cohort 9, an enormous and suspicious number. Investigating why revealed that the de-identified phone numbers in this dataset are mostly only 5-6 digits long, short enough that unrelated people collide on the same number purely by chance. This was confirmed directly: rows sharing a phone number showed completely different names, different countries, and registrations months apart.

**Decision:** A registration was only treated as a genuine duplicate when both Phone Number and Email Address matched together. This reduced the count to 43 confirmed duplicate rows (37 distinct people) in Cohort 9, and 3 in Cohort 10, a far more defensible standard for what counts as "the same person."

## 3. Duplicate registrants were resolved by keeping their most recent submission

Of the 37 people who registered more than once in Cohort 9, 24 (65%) chose a different course the second time. This rules out simple form resubmission or typo correction as the explanation; most of this reflects genuine reconsideration.

**Decision:** For each duplicate registrant, only their most recent submission was kept, on the assumption that their final registration reflects their actual, considered decision. Earlier submissions from the same person were removed from the row count to avoid inflating registration numbers, but the course-switching behavior itself was kept as a separate, reported finding rather than discarded.

## 4. Country field: confident corrections vs. left ambiguous

After cleaning spacing, casing, and obvious typos in the Country field, a small number of entries were still not safely resolvable. Examples: "Niger" (the country Niger, or a truncated "Nigeria"?), "Sout" (South Africa or South Sudan?), and a small number of rows where a phone number or the form's own placeholder text ("e.g.") had been typed into the Country field by mistake.

**Decision:** Confident typos and truncations (e.g. "Ghan" → Ghana, "RSA"/"SA" → South Africa) were corrected via an explicit mapping. Entries that could not be safely resolved were labeled "Ambiguous," and non-country entries were labeled "Invalid Entry." Both categories were kept in the dataset but excluded from any country-specific breakdown, since including a guess would misrepresent the data. Combined, these affected under 1% of rows in both cohorts, small enough not to distort any conclusion.

## 5. Cohort 9's missing Occupation field was not estimated or filled in

The challenge brief describes Cohort 9's occupation data as having been estimated by borrowing Cohort 10's distribution. In the actual file provided, no Occupation column exists at all for Cohort 9.

**Decision:** Rather than recreate an estimate ourselves, this was documented as a genuine limitation. All occupation-based analysis in this project uses Cohort 10 only, and is clearly labeled as such wherever it appears.

## 6. Occupation values (Cohort 10) were grouped into broad categories

Cohort 10's free-text Occupation field produced over 100 distinct raw values across only 168 people, most appearing only once or twice; too sparse to analyze individually.

**Decision:** Occupations were grouped into 12 broader categories (e.g. Tech/Data, Healthcare, Business/Entrepreneurship) based on clear, defensible groupings of the raw text. Locations and non-answers typed into the field by mistake (e.g. "Kenya," "Nairobi," "Nil," "No") were labeled "Invalid Entry" rather than forced into a category.

## 7. The Jan 22-23 (Cohort 9) and May 14-15 (Cohort 10) spikes were flagged, not removed

Both cohorts showed one short, extremely concentrated registration window, 41.8% of Cohort 9 and 74.4% of Cohort 10 respectively, overwhelmingly on a single channel (X (Twitter), 91% and 96% of each spike). This is not consistent with steady, organic growth; it points to a specific, short-lived event.

**Decision:** These rows were not deleted; they are real registrations and real people. Instead, every channel analysis in this project is shown two ways, with the spike included and with it excluded, so the reader can see both the full picture and the steady, everyday pattern underneath it. The interactive dashboard makes this same toggle available live.

## 8. The course catalog was not force-matched between cohorts

Cohort 10 introduced two courses not offered in Cohort 9 (Supply Chain Analytics, AI Automation), and Cohort 9's "Data Science and AI" may or may not be the same track as Cohort 10's "Data Science and ML."

**Decision:** These were treated as distinct labels rather than merged, since there was no way to confirm from the data alone whether this was a simple rename or a genuinely different course. Where a cohort-over-cohort course comparison was made, it was explicitly limited to the four courses common to both cohorts, to avoid conflating a rename with a real shift in interest.

## 9. A founder-brand explanation was included as context, not as a data finding

The recommendation to lean on the founder's personal LinkedIn presence for Healthcare Data Analytics growth is based on outside context (the CEO's professional background), not something the registration dataset itself can prove. It is presented as a plausible explanation for an observed pattern (LinkedIn's skew toward Healthcare registrants), not as a data-backed conclusion on its own.

## Summary

Every decision above followed the same principle: where the data gave a confident, checkable answer, it was used directly. Where it didn't, the uncertainty was labeled and preserved rather than smoothed over with a guess. This is what makes every finding and recommendation in this project traceable back to something real in the data, rather than an assumption dressed up as a conclusion.