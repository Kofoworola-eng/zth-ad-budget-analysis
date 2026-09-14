## Git Workflow

### Branching Strategy

This project uses a single `main` branch with direct, sequential commits, rather than the `main`/`develop`/feature-branch structure used on [sales-data-pipeline](https://github.com/kofoworola-eng/sales-data-pipeline).

That is a deliberate choice, not a shortcut. `sales-data-pipeline` was built specifically to demonstrate team-based Git practice: branching, pull requests, a deliberately triggered and manually resolved merge conflict, and recovering from a base-branch mistake. This project has a different purpose. It is a one-week solo analysis challenge with a single contributor and no parallel workstreams, so a branching workflow would add process for its own sake rather than solving a real problem. Knowing when a lighter workflow is the right call, and not defaulting to the heaviest process available, is itself part of working like an analyst rather than performing one.

Every commit here is still a complete, meaningful unit of work with a message that explains what changed and why, so the commit history reads as a build log on its own, alongside the reasoning captured in the notebooks.

### Commit History

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
This file.

This table (and the narrative above) is updated as the project moves through EDA, visualization, and the final recommendation, so the log stays current with the actual state of the project rather than becoming a stale changelog.