# Catalogue of central Acts

One row per Act in `acts.jsonl` (848 Acts, from India Code). Fields: short_title, act_number, year, act_id, ministry, date_of_assent, commencement (date or "by notification"), long_title, no_of_sections, no_of_chapters, repealed, amendments (list of amending Acts from India Code's ACT_AMENDMENT collection), amendment_count, sources.

## Method

- Source of truth: India Code's DSpace API harvest (`raw/india-code/acts.jsonl`), 848 Acts.
- Amendments merged from `act_amendments.jsonl` (918 records) by matching `dc.identifier.act_name` to the Act's short title.
- Repeal status from `repeal_acts.jsonl` (200 records) plus India Code's `dc.identifier.repealed` flag.
- Sorted by year then Act number.

## Counts per decade

| Decade | Acts |
|---|---:|
| 1830s | 3 |
| 1840s | 5 |
| 1850s | 18 |
| 1860s | 12 |
| 1870s | 22 |
| 1880s | 25 |
| 1890s | 19 |
| 1900s | 11 |
| 1910s | 15 |
| 1920s | 14 |
| 1930s | 16 |
| 1940s | 35 |
| 1950s | 109 |
| 1960s | 86 |
| 1970s | 69 |
| 1980s | 89 |
| 1990s | 63 |
| 2000s | 93 |
| 2010s | 81 |
| 2020s | 63 |
| **Total** | **848** |

## Checks

See `run/CHECKS.md` (Stage 2): counts per year against the Gazette index; 20 random rows against their Gazette text (seed 1).
