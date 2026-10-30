# india-law

India's law as a git history: one commit per Act or amending Act taking effect, starting with the Acts of Parliament.

## Install

Nothing to install yet. When the first corpus lands, reading it will be:

```sh
git clone https://github.com/indiavotes/india-law.git
cd india-law
git log --format='%ad %an' --date=short -- central/
```

## What this is

A corpus in the law-as-git convention used by lexifina's corpora, so the same tools read it:

- one Markdown file per section, under one folder per Act (`central/<act>/<section>.md`);
- one commit per law taking effect, authored by that law and dated the day it came into force;
- trailers on every commit: `Law:` (the Act and year), `In-force:` (the date), `Source:` (where the text came from);
- a `corpus.json` at the root describing coverage, history mode and sources.

Scope, in order: Acts of Parliament (Lok Sabha and Rajya Sabha) and the Constitution with its amendments; then State legislatures; then subordinate legislation.

## Sources

- The Central Gazette of India (weekly and extraordinary issues from 1947), where every Act and amending Act is first published.
- India Code, for the current consolidated text of each central Act.
- Bill texts from Lok Sabha and Rajya Sabha.

Each commit names its source. Where a version is rebuilt by applying an amending Act to the earlier text, the commit says so, and the rebuilt text is checked against a published consolidated version wherever one exists.

## Status

Scaffolded 2026-10-31. No corpus yet.

## Context

Built for [Lexaeva](https://lexaeva.naklitechie.com), which shows how law changes, law by law, and reads this corpus for India at `/in/`.

## Licence

Reproducing or publishing the text of an Indian Act is not an infringement of copyright (Copyright Act 1957, s. 52(1)(q)). The arrangement of this history is released under CC0.
