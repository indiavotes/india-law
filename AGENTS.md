# AGENTS.md — india-law

Rules for any agent working in this repository.

## What the corpus must look like

- One folder per body of law: `constitution/`, `central/<act-slug>/`, later `states/<state>/<act-slug>/`.
  `<act-slug>` is the short title in lower case with hyphens and the year, for example `indian-contract-act-1872`.
- One Markdown file per section (`central/<act-slug>/<section>.md`; articles for the Constitution:
  `constitution/article-21.md`). First line `# <Act short title>, section <n>`; then the text, one paragraph or
  clause per line, indented by level; last line the section's history note where the source gives one.
- One commit per law taking effect, dated (author and committer date, 12:00:00+05:30) the day it came into force.
  The commit's author name is the law, for example `The Constitution (Forty-second Amendment) Act, 1976`.
- Trailers on every commit:
  - `Law:` the Act's short title, number and year (`Act No. 52 of 1976`).
  - `In-force:` YYYY-MM-DD.
  - `Source:` the URL or archive identifier the text came from.
  - `Date-basis:` how the date was found (`commencement notification`, `date of assent`, `stated in the Act`).
  - `Kind:` `enacted`, `amendment`, `replayed`, `snapshot` or `correction`.
- Commit body: one line per section changed, `- section 5 substituted` / `inserted` / `omitted` / `amended`.
- `corpus.json` at the root: name, coverage, `history` (`replayed`, `in-force` or `current-only` per folder),
  sources and their terms, and the date of the last build.

## How to work

- Fetch from public sources only, slowly, with randomised waits between requests; respect robots.txt and any
  stated rate limit. Keep raw downloads outside the repository.
- Every number in a report comes from a command that ran; say which checks did not run.
- A rebuilt (replayed) version is checked against a published consolidated text wherever one exists; list
  mismatches, never hide them.
- Commit locally in small, meaningful commits. Do not push, and do not rewrite history that is already pushed.
- Do not add process tooling unless a corpus feature needs it.

## Verification budget

- No tests or checks between implementation steps; build the whole batch, then check it once at the batch boundary.
- Run only the checks that cover the changed batch.
- Generated test data goes to one temporary directory, at most 5,000 files and 500 MB, deleted at the end.
- One diagnostic batch per failure, with a written hypothesis first.
