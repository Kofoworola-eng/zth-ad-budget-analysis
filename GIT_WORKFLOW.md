# Branching Strategy

This project uses a single `main` branch with direct, sequential commits, rather than the `main`/`develop`/feature-branch structure used on [sales-data-pipeline](https://github.com/kofoworola-eng/sales-data-pipeline).

That is a deliberate choice, not a shortcut. `sales-data-pipeline` was built specifically to demonstrate team-based Git practice: branching, pull requests, a deliberately triggered and manually resolved merge conflict, and recovering from a base-branch mistake. This project has a different purpose. It is a one-week solo analysis challenge with a single contributor and no parallel workstreams, so a branching workflow would add process for its own sake rather than solving a real problem. Knowing when a lighter workflow is the right call, and not defaulting to the heaviest process available, is itself part of working like an analyst rather than performing one.

Every commit here is still a complete, meaningful unit of work with a message that explains what changed and why, so the commit history reads as a build log on its own, alongside the reasoning captured in the notebooks.

# Commit History

**`Initial project structure with raw cohort data`**
Set up the base folder structure (`data/raw`, `data/processed`, `notebooks`, `outputs`) and added the two original registration exports exactly as received from Zion Tech Hub. Nothing in `data/raw` is ever edited after this commit. It exists as a fixed reference point so every later cleaning decision can be checked against the true original.

**`Add project README`**
Documented the project's purpose before any analysis began: what the challenge was, why the data matters as real, unpolished business data rather than a practice dataset, and the two business questions the analysis needs to answer. Writing this first, before touching the data, forced clarity on what the project was actually for.

**`Fix project structure tree formatting`**
A markdown formatting mistake caused the folder-tree diagram in the README to render as plain text instead of a code block on GitHub. Fixed by isolating the tree in its own fence rather than nesting it inside the outer fence wrapping the full README. Small, but it is the kind of formatting detail that affects how professional a repo looks to anyone skimming it.

**`Add requirements.txt`**
Locked every installed package to its exact version using `pip freeze`, so the environment is fully reproducible for anyone who clones the repo.

**`Clean Cohort 9 and Cohort 10: timestamps, duplicates, country standardization`**
The main cleaning pass across both datasets. Converted both Timestamp columns to proper datetime (each cohort used a different raw format). Investigated 55 Cohort 9 rows with a missing Name and confirmed, rather than assumed, that this was a deliberate de-identification pattern (every affected email username was exactly 4 characters, zero variation) rather than random missing data, so those rows were kept, not dropped. Identified and removed 43 duplicate Cohort 9 registrations and 3 in Cohort 10, matched on Phone plus Email rather than Phone alone, after confirming Phone alone produced hundreds of false-positive matches due to short, de-identified numbers colliding by chance. Standardized the Country field in both cohorts against a checked, documented mapping, explicitly separating confident corrections from genuinely unresolvable entries rather than guessing.

**`Add git workflow documentation`**
This file, written once the cleaning pass was done and the shape of the project was clear enough to explain honestly, rather than drafted speculatively before there was anything real to document.

**`EDA: channel performance, spike analysis, course and occupation patterns`**
The core exploratory pass, and where the project's most important discovery happened. A close look at Cohort 9's registration timing surfaced a two-day cluster, January 22 to 23, that turned out to be 422 rows (42% of the entire cohort) arriving through X (Twitter) alone. Left unadjusted, that spike would have made X look dominant everywhere it was actually a single event. Built a raw-versus-spike-removed comparison for every channel so the rest of the analysis is judging real, steady performance rather than a two-day anomaly. Also mapped the shift in course interest between cohorts, controlling for the fact that Cohort 10 added two new courses Cohort 9 never had (so a raw share comparison would have made Cohort 10's original courses look like they lost more ground than they actually did), and grouped Cohort 10's Occupation field into 12 readable categories, since Cohort 9's actual export had no Occupation column to compare against.

**`Add plain-language findings summary`**
`reports/findings_summary.md`. Everything found during cleaning and EDA, written the way it would actually be explained to the marketing lead in conversation, not as a technical readout. This exists separately from the recommendations document because the reasoning behind a finding and the action it leads to are two different things, and collapsing them into one document would have made both harder to use.

**`Add ad budget allocation and growth recommendations`**
`reports/recommendations.md`. The first translation of findings into decisions: a specific percentage split for the ad budget across channels, and six numbered, actionable growth recommendations for Cohort 11. This is the point where the project stopped being descriptive and started being prescriptive.

**`Build dashboard: channel, geography, course, and timing visuals`**
Four static matplotlib charts covering channel comparison, geographic channel mix, course interest shift, and the spike timeline, plus a combined 2x2 dashboard image built with GridSpec. This was the first visual deliverable, built before the live dashboard existed, so there was always something shareable even while the interactive version was still in progress.

**`Export combined dataset for Tableau dashboard`**
Built a single combined export, `tableau_combined.csv` (1,272 rows across both cohorts), shaped specifically for Tableau to consume: Channel, Course, Country, Gender, Cohort, a spike-event flag, and derived date fields. Kept separate from `data/processed` cleaning outputs because this file's structure serves one purpose only, feeding the dashboard, and reshaping it further for that purpose isn't a cleaning decision, it's a presentation one.

**`Add live Tableau dashboard link and preview to README`**
Published the interactive Tableau Public dashboard, three linked sheets (channel performance, geographic reach, course trends) plus a combined dashboard view with cohort and spike-day filters, styled in Zion Tech Hub's own brand colors, and added the public link and a preview screenshot to the README so it's visible without leaving GitHub.

**`Add founder-brand growth recommendation for LinkedIn/Healthcare`**
A seventh recommendation, added after the first six, once a piece of founder context came into view: the CEO's own background as a healthcare data analyst plausibly explains LinkedIn's disproportionate pull toward Healthcare Data Analytics registrants. Written explicitly as founder context rather than a data-proven finding, so it's clear which claims in the document are backed by the dataset and which one is informed judgment layered on top of it.

**`Add detailed assumptions and data cleaning writeup`**
`reports/assumptions.md`. Every judgment call made across the whole project, laid out individually and explained in plain terms: what was decided, what evidence supported it, and what the alternative would have changed. Written last, once every other decision in the project had actually been made, so it documents what really happened rather than what was planned to happen.

**`Add final presentation deck`**
A PowerPoint deck built to walk a stakeholder through the entire project in slide form: the brief, the approach, all four findings, the ad budget recommendation, the growth recommendations, the assumptions, and the live dashboard.

**`Add presentation deck as PDF`**
Exported the deck to PDF and added it alongside the PowerPoint file. GitHub renders PDFs inline in the browser, so anyone visiting the repo can view the presentation directly without downloading it first.

**`Remove pptx, replaced with PDF version`**
Removed the original `.pptx` once the PDF was confirmed as the version people would actually view. Keeping both would have meant two files to keep in sync for no real benefit, the PDF is the one that's actually usable from the repo page.

**`Update project structure tree to reflect final repo`**
Updated the folder-tree diagram in the README to match the real, final layout, deliberately left until this point rather than edited every time a new folder appeared, so it only needed to be written once, correctly, against the finished project.

This log reflects the project as it actually happened, in the order it happened, rather than a cleaned-up version of events after the fact.