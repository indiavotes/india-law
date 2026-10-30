# Sources

Survey of sources used for the india-law corpus. Raw downloads live under `/Volumes/Models/india-law/raw/` (outside the repo). Counts below come from the cloned snapshots as of 2026-10-30.

## Central Gazette (sansadsaar-gazettes)

- Repo: `NakliTechie/sansadsaar-gazettes` (cloned depth 1 to `raw/sansadsaar-gazettes`).
- Content: metadata + bilingual English/Hindi extracted text for central Gazette items; PDFs live at archive.org (`gazetteofindia` collection, populated by Sushant Sinha's egazette project).
- Snapshot held here: 31,335 central records, issue dates 2022-09-30 to 2026-10-28 (29,762 extraordinary, 1,573 weekly).
- Acts of Parliament appear as Extraordinary Gazette, Part II, Section 1; the snapshot's subjects mentioning "Act" number 6,467 but most are notifications made under Acts, not the Acts themselves. Legislative Department (Ministry of Law and Justice) records: 141.
- Fetch: archive.org PDFs; metadata already harvested in the repo's `docs/gazettes/*.json`. No additional fetching done here; fetch slowly with 2-6 s waits if extending.
- Licence/terms: government publication; no rights claimed by the mirror (CC0 arrangement metadata). PDFs remain at archive.org.

## India Code (indiacode.nic.in)

- Access: works (DSpace API `https://indiacode.gov.in/server/api/discover/search/objects`). Harvested by `raw/../bin/harvest_india_code.py` into `raw/india-code/*.jsonl`.
- Counts: acts 848 (central Acts); sections 35,444; act_amendments 918; repeal_acts 200; spent_acts 14; acts_not_enforced 4; statute 131.
- Each section carries its text in metadata `dc.identifier.section_page_note` (HTML), act in `dc.identifier.act_id` / `act_name`, number in `section_number`, order in `order_number`. Act metadata includes enact date, enforcement date, act number, ministry, long title, legislation history.
- Quality: born-digital HTML text, section-level. This is the backbone for Stage 4.
- Licence/terms: Government of India publication; free public access; no stated reuse restriction found.

## Lok Sabha / Rajya Sabha bills (sansad.nic.in, parliamentwatch-data)

- Repo: `NakliTechie/parliamentwatch-data` (cloned depth 1 to `raw/NakliTechie-parliamentwatch-data`).
- Content: 9,928 bills (1952-2026), 3,458 of which became law (status "Assented"); 7,332 with extracted text; 717 with gazette links.
- Fetch: `sansad.in/api_rs/legislation/getBills`; PDFs via the mirror. Scraper in `bills/sansad/scraper.py`.
- Licence/terms: Parliament of India public records.

## Legislative Department (legislative.gov.in)

- Holds the list of central Acts, the Constitution, amendment Acts, and consolidated texts. Probed via `raw/leg-central.html` (saved sample). Legislative Department PDFs are the authoritative consolidated source referenced by vijaya22.
- Fetch: polite, 2-6 s waits; many PDFs.

## vijaya22/constitution-history

- Repo: `vijaya22/constitution-history` (cloned to `raw/vijaya22-constitution-history`).
- Content: Constitution of India as git history: text as adopted (1950-01-26) plus one commit per Constitution (Amendment) Act and other Acts/Orders that changed the text (153 commits total). Layout `constitution/part-*/article-*.md` plus schedules and preamble, with YAML frontmatter.
- Licence: text published by Government of India (no rights claimed); arrangement under CC0 1.0. Used for Stage 3.
- Note: commit subjects are sometimes "null" for intermediate version steps; trailers give `Effective:` dates (sometimes null).

## Vaquill-AI/open-india-law

- Repo: `Vaquill-AI/open-india-law` (cloned to `raw/Vaquill-AI-open-india-law`).
- Content: structured Indian primary law at scale (12.8M court judgments, 813K tribunal matters, 22,265 enactments, 1.1M sections) plus scrapers. Useful as a cross-check and for state legislation; not used directly for the central corpus (India Code is preferred for consolidated central text).
- Licence: see repo LICENSE (open data).

## States (Stage 6)

- Not yet surveyed. To be added: which States publish Acts/amendments (State Codes, State Gazettes). India Code state collections exist but coverage varies.

## Quality notes

- India Code text is born-digital HTML; converted to Markdown per section.
- Gazette text is OCR'd (English + Hindi) from scanned PDFs.
- vijaya22 text is rebuilt from Legislative Department footnotes; `Verified: false` in its commits.
