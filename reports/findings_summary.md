# Zion Tech Hub: Ad Budget and Growth Analysis — Findings Summary

## The short version

Zion Tech Hub is about to spend its first ad naira, and this analysis is built to tell you where that money actually has the best shot at working, not where it feels like it should go.

The honest answer is more layered than "put it all on the channel with the biggest number." When I looked past the raw totals, two things became clear. First, a large chunk of what looks like organic growth in this data was really driven by short, one off spikes, one on X (Twitter) near the end of Cohort 9, and an even bigger one at the start of Cohort 10. Once those spikes are set aside, a different, steadier story shows up underneath: X (Twitter) is genuinely growing as a channel, LinkedIn is quietly the most dependable one, and WhatsApp is fading fast. Second, the people coming through these channels are not the same kind of person. LinkedIn brings in a heavier share of people interested in Healthcare Data Analytics. X (Twitter) reaches Nigeria and four consistent international markets almost equally well, while WhatsApp barely reaches anyone outside Nigeria at all.

None of this came from assuming the data was clean. It came from checking almost everything twice before trusting it, because a lot of what first looked like a straightforward number turned out to have a story behind it once I looked closer.

## How I approached the data

Before I share what the data says, it's worth being upfront about what I had to decide along the way, because a few of those decisions shape everything downstream.

Cohort 9 arrived with 1,147 rows, but 55 of them had no name at all. My first instinct was to treat that as missing data and either drop the rows or ignore the gap. But when I looked at the email addresses on those same rows, every single one had a username exactly 4 characters long, no variation at all. That's not what random missing data looks like. It's what a deliberate, systematic redaction looks like, similar to how phone numbers in this dataset were already de-identified but consistently mapped. So I kept those 55 rows. Every field I actually needed for this analysis, channel, course, country, timing, was still fully present on them. Only the name was gone, and I never needed the name.

Duplicates were trickier than they first appeared. Phone number alone flagged 729 "duplicate" rows, which would have been an enormous chunk of the dataset to explain away. But when I required both phone and email to match together, that number dropped to 43. I checked why, and found that most of the de-identified phone numbers in this dataset are only 5 or 6 digits long. With that few digits, unrelated people collide on the same number by pure chance, and I could see it directly: two completely different people in two different countries sharing a number, months apart. So I only treated something as a genuine duplicate registration when both phone and email matched. That gave me 37 real repeat registrants across 80 rows, some of whom had registered three times or more.

What I found inside those 37 repeat registrations turned out to matter more than I expected. 24 of them, nearly two thirds, chose a different course the second time around. That's not someone fixing a typo. That's someone reconsidering. It suggests people aren't always confident about which course fits them the first time they land on the form, which becomes one of the more actionable findings below.

I also had to make a judgment call on country data. After cleaning up spacing, casing, and obvious typos, a small number of entries were still not safely resolvable, things like "Niger" (is that the country Niger, or a cut off "Nigeria"?) or a raw phone number typed into the country field by mistake. Rather than guess, I labeled these "Ambiguous" or "Invalid Entry" and excluded them from country specific breakdowns. It's a small number of rows either way, under 1% of the dataset, but I'd rather tell you what I don't know than quietly paper over it.

## The channel picture, and why the raw numbers are misleading

If you looked at Cohort 9's channel numbers as they came in, X (Twitter) looks unbeatable at 62.7% of all registrations. But when I sorted registrations by date, something jumped out: 41.8% of the entire cohort registered within a single 2 day window, January 22 to 23, just 11 days before the cohort closed. Within that window, 91% of registrations came through X (Twitter) specifically. That is not what organic, steady growth looks like. That's a concentrated event, most likely a deliberate late push to fill remaining seats, or a post that caught fire at just the right time.

Cohort 10 told an even more extreme version of the same story. 74.4% of that entire cohort, 125 out of 168 people, registered on a single Thursday and Friday in mid May, and 96% of that came through X (Twitter) too.

So I recalculated everything with both spikes removed, to see what these channels do on an ordinary day, not their best day. That's where the real, useful picture is:

- **X (Twitter) is still growing, spikes aside.** Even with the spike days stripped out, its steady share grew from 39.6% in Cohort 9 to 62.8% in Cohort 10. This isn't just a channel that spikes well, it's one that's building real organic momentum underneath the spikes.
- **LinkedIn is the most dependable channel you have.** It barely moved, 24.8% to 23.3%, while every other channel swung wildly. If you want a channel you can count on delivering roughly the same result every single cohort, this is it.
- **WhatsApp is fading, and fading fast.** It went from 28.9% to just 7.0% with the spikes removed. Something changed in how well this channel is working, and it's worth understanding why before deciding whether to keep investing in it.
- **Facebook and Instagram have essentially disappeared.** Both were present at low levels in Cohort 9 and completely absent in Cohort 10.

## Who each channel actually reaches

Channels don't just differ in volume, they bring in different kinds of people, and this matters as much as the raw numbers for deciding how to spend.

LinkedIn registrants are nearly twice as likely to choose Healthcare Data Analytics as X (Twitter) registrants are, 37.3% versus 19.1%. If Healthcare is a course you want to fill, LinkedIn is punching above its overall registration share and shouldn't be deprioritized just because its total volume looks smaller than X (Twitter)'s.

X (Twitter) and Instagram, on the other hand, skew hardest toward Data Science and AI, which also happens to be the most consistently popular course across both cohorts regardless of channel.

On occupation, I want to be honest about a limit in the data. Cohort 9's file has no occupation field at all, so this part of the analysis only covers Cohort 10, and even there, most channels have too few people behind them to draw a real conclusion. Facebook's numbers are based on 2 people. WhatsApp and Referral are based on 4 each. Those percentages are not patterns, they're noise, and I'm not going to pretend otherwise. The one channel with enough volume to trust, X (Twitter) at 147 people, shows a broad, mixed audience rather than one dominant profession, with Students and recent graduates as the single largest group at 20.5%, followed by a spread across entrepreneurship, tech, and finance backgrounds. That tells me X (Twitter) works as a wide net, not a narrow spear, which matters for how you'd write ad copy for it.

## Where the international audience actually is

Nigeria, South Africa, Ghana, and Kenya show up as the top four countries in both cohorts, consistently, together making up roughly 84 to 85% of all registrants each time. That consistency across two completely separate cohorts tells me this isn't random scatter, it's a real, repeatable pattern of interest from these four markets specifically.

And here's the part that matters for spending: international registrants and Nigerian registrants don't use the same channels. WhatsApp is close to a Nigeria only channel, 25.8% of Nigerian registrants used it in Cohort 9 versus only 7.7% of international ones. X (Twitter) is the channel actually reaching people outside Nigeria, used by 72.9% of international registrants in Cohort 9, and LinkedIn skews slightly international in both cohorts as well. If growing outside Nigeria matters to you, WhatsApp community building won't get you there. X (Twitter), and to a smaller extent LinkedIn, already have a track record of reaching exactly the four markets showing up organically.

## What's changing in what people want

Once I accounted for the fact that Cohort 10 simply offers more courses than Cohort 9 did (so some of the shift is just dilution, not changing interest), a real pattern emerged. Data Science and AI or ML held completely steady as the most popular choice in both cohorts, just under half of all registrants both times. Sales and Marketing Analytics grew meaningfully, up about 8.5 percentage points. Healthcare Data Analytics genuinely declined, down about 6.7 points, and that's not just new courses splitting the pie, the drop is real even after controlling for that.

That Healthcare decline is worth sitting with for a moment, because LinkedIn, your steadiest channel, is also the channel that most reliably brings in Healthcare-interested registrants. If interest in that course keeps softening, it's worth knowing whether that's a course content issue, a positioning issue, or just market saturation, before assuming LinkedIn itself is underperforming.

## Where this leaves you

I've built this analysis to survive being questioned, so every number above ties back to something checkable in the data, not a hunch. The specific ad budget allocation and the numbered growth recommendations are covered separately, this document is meant to be the plain language foundation those recommendations are built on. If any of the reasoning above doesn't add up when you dig into it yourself, that's exactly the kind of pushback this was built to hold up against.