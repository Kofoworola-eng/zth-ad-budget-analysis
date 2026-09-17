# Zion Tech Hub: Data Cleaning, Assumptions & Findings

This document covers two things together: every judgment call made while cleaning and preparing the Cohort 9 and Cohort 10 registration data (so every number in this project is checkable), and the full findings those decisions made possible. Read the assumptions first if you want to know how trustworthy a number is before you see it; read the findings first if you want the story and want to check the methodology after. For the direct answers to the three brief questions and the full recommendations, see `conclusion.md`.

---

## Part One: Assumptions and Data Cleaning Decisions

This section brings together every judgment call made while cleaning and analyzing the Cohort 9 and Cohort 10 registration data, and the reasoning behind each one. Nothing here was guessed silently; every decision below was made only after checking what the data actually showed, and each one is something a stakeholder could reasonably question and get a defensible answer to.

**1. The 55 rows with no Name (Cohort 9) were kept, not dropped.**
At first glance, 55 missing names look like a data quality problem. But every one of those rows had an email address with a username exactly 4 characters long, with zero variation across all 55, compared to the normal, varied-length email usernames everywhere else in the dataset. That's not what random missing data looks like; it's what a deliberate, systematic redaction looks like, consistent with how the challenge brief already told us phone numbers had been de-identified elsewhere in the dataset.
*Decision:* These rows were kept. Every field actually used in this analysis (Channel, Course, Country, Timing) was fully present on them. Name was never needed for any part of the analysis, so its absence has no effect on the findings.

**2. Duplicate registrants were identified using Phone + Email together, not Phone alone.**
Phone number alone flagged 729 "duplicate" rows in Cohort 9, an enormous and suspicious number. Investigating why revealed that the de-identified phone numbers in this dataset are mostly only 5-6 digits long, short enough that unrelated people collide on the same number purely by chance. This was confirmed directly: rows sharing a phone number showed completely different names, different countries, and registrations months apart.
*Decision:* A registration was only treated as a genuine duplicate when both Phone Number and Email Address matched together. This reduced the count to 43 confirmed duplicate rows (37 distinct people) in Cohort 9, and 3 in Cohort 10, a far more defensible standard for what counts as "the same person."

**3. Duplicate registrants were resolved by keeping their most recent submission.**
Of the 37 people who registered more than once in Cohort 9, 24 (65%) chose a different course the second time. This rules out simple form resubmission or typo correction as the explanation; most of this reflects genuine reconsideration.
*Decision:* For each duplicate registrant, only their most recent submission was kept, on the assumption that their final registration reflects their actual, considered decision. Earlier submissions from the same person were removed from the row count to avoid inflating registration numbers, but the course-switching behavior itself was kept as a separate, reported finding rather than discarded.

**4. Country field: confident corrections vs. left ambiguous.**
After cleaning spacing, casing, and obvious typos in the Country field, a small number of entries were still not safely resolvable. Examples: "Niger" (the country Niger, or a truncated "Nigeria"?), "Sout" (South Africa or South Sudan?), and a small number of rows where a phone number or the form's own placeholder text ("e.g.") had been typed into the Country field by mistake.
*Decision:* Confident typos and truncations (e.g. "Ghan" → Ghana, "RSA"/"SA" → South Africa) were corrected via an explicit mapping. Entries that could not be safely resolved were labeled "Ambiguous," and non-country entries were labeled "Invalid Entry." Both categories were kept in the dataset but excluded from any country-specific breakdown, since including a guess would misrepresent the data. Combined, these affected under 1% of rows in both cohorts, small enough not to distort any conclusion.

**5. Cohort 9's missing Occupation field was not estimated or filled in.**
The challenge brief describes Cohort 9's occupation data as having been estimated by borrowing Cohort 10's distribution. In the actual file provided, no Occupation column exists at all for Cohort 9.
*Decision:* Rather than recreate an estimate ourselves, this was documented as a genuine limitation. All occupation-based analysis in this project uses Cohort 10 only, and is clearly labeled as such wherever it appears.

**6. Occupation values (Cohort 10) were grouped into broad categories.**
Cohort 10's free-text Occupation field produced over 100 distinct raw values across only 168 people, most appearing only once or twice, too sparse to analyze individually.
*Decision:* Occupations were grouped into 12 broader categories (e.g. Tech/Data, Healthcare, Business/Entrepreneurship) based on clear, defensible groupings of the raw text. Locations and non-answers typed into the field by mistake (e.g. "Kenya," "Nairobi," "Nil," "No") were labeled "Invalid Entry" rather than forced into a category.

**7. The Jan 22–23 (Cohort 9) and May 14–15 (Cohort 10) spikes were flagged, not removed.**
Both cohorts showed one short, extremely concentrated registration window, 41.8% of Cohort 9 and 74.4% of Cohort 10 respectively, overwhelmingly on a single channel (X (Twitter), 91% and 96% of each spike). This is not consistent with steady, organic growth; it points to a specific, short-lived event.
*Decision:* These rows were not deleted; they are real registrations and real people. Instead, every channel analysis in this project is shown two ways, with the spike included and with it excluded, so the reader can see both the full picture and the steady, everyday pattern underneath it. The interactive dashboard makes this same toggle available live.

**8. The course catalog was not force-matched between cohorts.**
Cohort 10 introduced two courses not offered in Cohort 9 (Supply Chain Analytics, AI Automation), and Cohort 9's "Data Science and AI" may or may not be the same track as Cohort 10's "Data Science and ML."
*Decision:* These were treated as distinct labels rather than merged, since there was no way to confirm from the data alone whether this was a simple rename or a genuinely different course. Where a cohort-over-cohort course comparison was made, it was explicitly limited to the four courses common to both cohorts, to avoid conflating a rename with a real shift in interest.

**9. A founder-brand explanation was included as context, not as a data finding.**
The recommendation to lean on the founder's personal LinkedIn presence for Healthcare Data Analytics growth is based on outside context (the CEO's professional background), not something the registration dataset itself can prove.
*Decision:* It is presented as a plausible explanation for an observed pattern (LinkedIn's skew toward Healthcare registrants), not as a data-backed conclusion on its own.

**Summary:** every decision above followed the same principle: where the data gave a confident, checkable answer, it was used directly. Where it didn't, the uncertainty was labeled and preserved rather than smoothed over with a guess. This is what makes every finding and recommendation in this project traceable back to something real in the data, rather than an assumption dressed up as a conclusion.

---

## Part Two: Findings

### The short version

Zion Tech Hub is about to spend its first ad naira, and this analysis is built to tell you where that money actually has the best shot at working, not where it feels like it should go.

The honest answer is more layered than "put it all on the channel with the biggest number." When I looked past the raw totals, two things became clear. First, a large chunk of what looks like organic growth in this data was really driven by short, one-off spikes, one on X (Twitter) near the end of Cohort 9, and an even bigger one at the start of Cohort 10. Once those spikes are set aside, a different, steadier story shows up underneath: X (Twitter) is genuinely growing as a channel, LinkedIn is quietly the most dependable one, and WhatsApp is fading fast. Second, the people coming through these channels are not the same kind of person. LinkedIn brings in a heavier share of people interested in Healthcare Data Analytics. X (Twitter) reaches Nigeria and four consistent international markets almost equally well, while WhatsApp barely reaches anyone outside Nigeria at all.

None of this came from assuming the data was clean. It came from checking almost everything twice before trusting it, because a lot of what first looked like a straightforward number turned out to have a story behind it once I looked closer. (The full reasoning behind every cleaning decision below is in Part One, above.)

### The channel picture, and why the raw numbers are misleading

If you looked at Cohort 9's channel numbers as they came in, X (Twitter) looks unbeatable at 62.7% of all registrations. But when I sorted registrations by date, something jumped out: 41.8% of the entire cohort registered within a single 2-day window, January 22 to 23, just 11 days before the cohort closed. Within that window, 91% of registrations came through X (Twitter) specifically. That is not what organic, steady growth looks like. That's a concentrated event, most likely a deliberate late push to fill remaining seats, or a post that caught fire at just the right time.

Cohort 10 told an even more extreme version of the same story. 74.4% of that entire cohort, 125 out of 168 people, registered on a single Thursday and Friday in mid-May, and 96% of that came through X (Twitter) too.

So I recalculated everything with both spikes removed, to see what these channels do on an ordinary day, not their best day. That's where the real, useful picture is:

- **X (Twitter) is still growing, spikes aside.** Even with the spike days stripped out, its steady share grew from 39.6% in Cohort 9 to 62.8% in Cohort 10. This isn't just a channel that spikes well, it's one that's building real organic momentum underneath the spikes.
- **LinkedIn is the most dependable channel you have.** It barely moved, 24.8% to 23.3%, while every other channel swung wildly. If you want a channel you can count on delivering roughly the same result every single cohort, this is it.
- **WhatsApp is fading, and fading fast.** It went from 28.9% to just 7.0% with the spikes removed. Something changed in how well this channel is working, and it's worth understanding why before deciding whether to keep investing in it.
- **Facebook and Instagram have essentially disappeared.** Both were present at low levels in Cohort 9 and completely absent in Cohort 10.

### Who each channel actually reaches

Channels don't just differ in volume, they bring in different kinds of people, and this matters as much as the raw numbers for deciding how to spend.

LinkedIn registrants are nearly twice as likely to choose Healthcare Data Analytics as X (Twitter) registrants are, 37.3% versus 19.1%. If Healthcare is a course you want to fill, LinkedIn is punching above its overall registration share and shouldn't be deprioritized just because its total volume looks smaller than X (Twitter)'s.

X (Twitter) and Instagram, on the other hand, skew hardest toward Data Science and AI, which also happens to be the most consistently popular course across both cohorts regardless of channel.

On occupation, I want to be honest about a limit in the data. Cohort 9's file has no occupation field at all, so this part of the analysis only covers Cohort 10, and even there, most channels have too few people behind them to draw a real conclusion. Facebook's numbers are based on 2 people. WhatsApp and Referral are based on 4 each. Those percentages are not patterns, they're noise, and I'm not going to pretend otherwise. The one channel with enough volume to trust, X (Twitter) at 147 people, shows a broad, mixed audience rather than one dominant profession, with Students and recent graduates as the single largest group at 20.5%, followed by a spread across entrepreneurship, tech, and finance backgrounds. That tells me X (Twitter) works as a wide net, not a narrow spear, which matters for how you'd write ad copy for it.

Looking at Cohort 10's occupation categories overall (all channels combined, 167 people), the picture holds: Students/Graduates lead at 22.8%, followed by Tech/Data at 13.2% and Business/Entrepreneurship at 11.4%. Together those three make up 45.4% of the cohort, by far the largest identifiable audience, and Healthcare workers specifically are only 5.4% of registrants. That matters for how the LinkedIn/Healthcare pattern above should be read: it's a course-interest signal tied to LinkedIn specifically, not evidence that healthcare professionals are the primary audience across the program as a whole.

### Where the international audience actually is

Nigeria, South Africa, Ghana, and Kenya show up as the top four countries in both cohorts, consistently, together making up roughly 84 to 85% of all registrants each time. That consistency across two completely separate cohorts tells me this isn't random scatter, it's a real, repeatable pattern of interest from these four markets specifically.

And here's the part that matters for spending: international registrants and Nigerian registrants don't use the same channels. WhatsApp is close to a Nigeria-only channel, 25.8% of Nigerian registrants used it in Cohort 9 versus only 7.7% of international ones. X (Twitter) is the channel actually reaching people outside Nigeria, used by 72.9% of international registrants in Cohort 9, and LinkedIn skews slightly international in both cohorts as well. If growing outside Nigeria matters to you, WhatsApp community building won't get you there. X (Twitter), and to a smaller extent LinkedIn, already have a track record of reaching exactly the four markets showing up organically.

Looking closer at those four markets individually, one stands out. South Africa and Ghana were tied as the strongest international markets in Cohort 9 (106 registrants each, 9.6% of the cohort), but both fell sharply by Cohort 10 (11 and 9 registrants respectively, roughly 5-6%). Kenya moved the opposite direction, from 91 registrants (8.2%) in Cohort 9 to 20 registrants (11.9%) in Cohort 10, becoming the clear leading international market in the most recent cohort. Of the four consistent international markets, Kenya is the only one that grew, in both absolute registrants and share of cohort, while the others contracted. That makes it the single strongest candidate for a deliberate, focused international push next.

### What's changing in what people want

Once I accounted for the fact that Cohort 10 simply offers more courses than Cohort 9 did (so some of the shift is just dilution, not changing interest), a real pattern emerged. Data Science and AI or ML held completely steady as the most popular choice in both cohorts, just under half of all registrants both times. Sales and Marketing Analytics grew meaningfully, up about 8.5 percentage points. Healthcare Data Analytics genuinely declined, down about 6.7 points, and that's not just new courses splitting the pie, the drop is real even after controlling for that.

That Healthcare decline is worth sitting with for a moment, because LinkedIn, your steadiest channel, is also the channel that most reliably brings in Healthcare-interested registrants. If interest in that course keeps softening, it's worth knowing whether that's a course content issue, a positioning issue, or just market saturation, before assuming LinkedIn itself is underperforming.

### Where this leaves you

I've built this analysis to survive being questioned, so every number above ties back to something checkable in the data, not a hunch, and every cleaning decision behind those numbers is documented in Part One. The specific ad budget allocation and the numbered growth recommendations built on these findings are in `conclusion.md`. If any of the reasoning above doesn't add up when you dig into it yourself, that's exactly the kind of pushback this was built to hold up against.