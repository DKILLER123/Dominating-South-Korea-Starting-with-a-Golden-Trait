# Project handoff — *Dominating South Korea: Starting with a Golden Trait*

This repository is an EPUB translation/production workspace, not a web app. No dev server belongs
here; nothing in it should be started with a process tool.

**Read in this order:** `SKILL.md` (the rules) → `worklog.md` §0 and newest §8 entry (the state) →
`WORKSPACE_SETUP.md` (what has been verified) → `reference/README.md` (what is inherited process
and why it is walled off).

## Non-negotiables

- **This book only.** Protagonist **Bae Do-yoon**. No character, nickname, company, label, song,
  system name, ship or established date from the reader's previous novel
  (*Peninsula: Going Viral After a Dating Scandal with Kim Taeyeon*) may appear anywhere in this
  book. That novel's files are kept in `reference/` for **process** only. `python3 legacy_firewall.py`
  is a build gate, not advice.
- **Book order is fixed:** Cover → Synopsis → Contents → Character Info → Introductions → Glossary
  → Chapter 1 → … The spine carries exactly that order; `workspace_audit.py` fails it otherwise.
- **Raw-first.** The untouched chapter raw is saved to `raws/chNNN_raw.txt` before anything else
  happens, and is never edited afterwards (`raws/README.md`).
- **Reader's reference CSS/fonts stay untouched.** `fonts.css` and `stylesheet.css` at the repo root
  are the reader's supplied references — never edit their bytes. The tree's copies come from
  `python3 sync_styles.py`, which proves rule-for-rule identity, and `python3 install_fonts.py`,
  which rebuilds the 20 WOFF faces from npm.
- **Deep Scan + Deep Thinking, style-block maximalism, question-mark and phone-call audits** remain
  mandatory on every touched chapter (SKILL.md §2–§5, §9).
- **Folders:** `raws/` = source custody; `image-search/` = image workbench (source files stay there,
  coded files get installed into the tree); `work_epub/` = the book; `reports/` = audit output.
- **No EPUB without raws.** Nothing has been translated yet: do not invent Chapter 1, do not build a
  package to "see what it looks like" (`build_epub.py` overwrites the deliverable).
- **Publication rule (reader directive):** after **every final EPUB**, commit and push to this
session branch `arena/01a0a030-dominating-south-korea-startin`, verify the remote commit equals
local HEAD, and provide the GitHub download link. Never force-push, never touch `main`.
  Setup cycles that produce no EPUB are committed locally and pushed as tooling/state checkpoints.

## Tooling in this repo

| Command | Purpose |
|---|---|
| `python3 validate_tree.py` | XHTML parse, undefined classes, straight quotes, CJK scan (with the documented `lang="ko"` gloss exemption), internal refs |
| `python3 punct_quotes.py` | curly-quote integrity (dry run by default) |
| `python3 repeat_check.py chNNN.xhtml` | 8-gram repetition, bare filename |
| `python3 audit_marks.py work_epub/OEBPS/text/chNNN.xhtml` | question marks + phone-call structure (real paths) |
| `python3 legacy_firewall.py` | reference-novel bleed check (hard/soft), writes `reports/firewall.json` with `--json` |
| `python3 sync_styles.py` | install the tree's stylesheets from the reader's references (asserts identical rules) |
| `python3 install_fonts.py` | rebuild the 20 embedded WOFF faces (`--verify` with `.venv/bin/python`) |
| `python3 style_index.py [--check-skill]` | regenerate `reports/style_index.tsv` / `.md` — every section and class the sheet defines; `--check-skill` proves SKILL §5 cites only classes that exist |
| `.venv/bin/python workspace_audit.py --assets` | full read-only audit (structure, refs, assets, gates, indexes) |
| `node_modules/.bin/stylelint --config .sl.json "work_epub/OEBPS/styles/*.css"` | CSS lint; run `npm ci --ignore-scripts --no-audit --no-fund` first (node_modules is not persisted) |
| `python3 build_epub.py` | packages the tree into `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub` |

`npm run gates` chains the three fast gates; `npm run audit:assets` runs the full audit.

## Current state (cycle 4, 2026-09-14)

Tree: 15 chapters (`ch001`–`ch015`) · 67 payload entries · 64 manifest items · 21 spine entries ·
20 NCX navPoints · 23 nav list items · 20 WOFF faces · 19 images (repaired cover plate · cards
`id-02`…`id-06`, `id-10` reader-provided Boram master, `id-14` Kim Mi-joo, `id-17` Bae Suzy,
`id-19` Park Jin-young · plates `wd_*`, all photographic-real, Boram plates v2 re-locked to the new
master) · 13 character cards · 13 introduction cards · 39 glossary cards. Package built and pushed:
67 entries · 3,743,733 B · sha256 `48d6bce0…`. `extracted/` holds the unpacked archive snapshot.
All gates green. Next chapter slot `ch016` (NCX `num_21`/playOrder 21, nav li 24, next image id
`id-20`). Reserved: `uploads/Irene.jpg` (Irene) and `uploads/Jiyeon.jpg` (Jiyeon) for their first
prose appearance; `uploads/600.webp` reference-only (never cover/chapter art).
