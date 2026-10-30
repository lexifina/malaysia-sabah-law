# Sabah: law history in git

The law of the State of Sabah (Malaysia) as a git history: the Constitution of the State of Sabah and the Sabah Ordinances and Enactments, one file per Article or section, one paragraph per line, so `git blame`, `git log` and `git diff` work line by line. The text is the English text published by the State Attorney-General's Chambers on Sabah Lawnet.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

**Current text only, not yet a history.** Sabah Lawnet publishes each law as one PDF stamped "FOR REFERENCE ONLY (<month> <year>)", with no earlier consolidated text. So each law is one commit holding its whole text as of that month, credited to the State Attorney-General's Chambers ("oldest version available"), not to an amending law.

| Folder | What |
| --- | --- |
| `constitution/` | the Constitution of the State of Sabah: `000-title.md`, one file per Article, one per Schedule |
| one folder per Ordinance or Enactment (by its short title) | the law: `000-title.md`, one file per section, one per Schedule |

The Constitution comes first; the Ordinances and Enactments follow in parts of about fifty, in the order of Lawnet's "Sabah Laws" list. Subsidiary legislation and laws Lawnet lists as repealed or not yet in force are not included. A law is left out until it can be read reliably: PDFs with tables or forms the independent check below does not find in the same order, and PDFs without a "FOR REFERENCE ONLY" month.

## Source

[Sabah Lawnet](https://sagc.sabah.gov.my/?q=en/law-type/sabah-laws), on the official website of the State Attorney-General's Chambers, Sabah: "Constitution of the State of Sabah" and "Sabah Laws" (PDF). Each PDF's sha256 is recorded with its version in `data/versions.json`.

## Dates

Each law's version is dated by the month of its "FOR REFERENCE ONLY" stamp, on the first day of that month, at noon in Kota Kinabalu. The stamp gives no day; it is the month of Lawnet's text, not the day of the last amendment.

## How it is built

Lexifina reads the sources listed here and records each act's dated versions, and the laws that made each change, in one corpus file. `tools/build.py` writes this repository from that file, and the same corpus always gives the same commit hashes; `REPRODUCE.md` gives the details and the checks. A model (Claude) wrote Lexifina's code; it wrote no legal text, and no model runs when the history is built.

The text layer of each PDF (no OCR) becomes one file per Article or section. The cover, the arrangement of sections or articles, the "FOR REFERENCE ONLY" stamp, the "Sabah Lawnet" watermark, page numbers, footnotes and the "List of Amendments" tables are left out. Amendment notes printed in the text stay as printed. Part and Chapter headings stand above the first provision under them; each provision's heading is the line before its text.

## How it is checked

Every version is read back from git on the day it took effect and must match the corpus. A second, independent reading of every PDF (a different PDF engine) must contain every letter and digit of each law in the same order, with nothing in the body left out. Results are in `REPRODUCE.md`.

## What "author" means

The author of each commit is the publisher (the State Attorney-General's Chambers, Sabah), with an e-mail address that cannot exist; the committer is always Lexifina.

## Limits

Only the text as of each stamp's month is here: no earlier versions, and not the laws as enacted. The texts are marked "FOR REFERENCE ONLY"; the laws as published in the Sabah Government Gazette are authoritative. Footnotes are left out.

## Licence

See [LICENSE](LICENSE): official texts of a legislative nature are excluded from copyright by the Copyright Act 1987 [Act 332], s. 3. Source: State Attorney-General's Chambers, Sabah (Sabah Lawnet).
