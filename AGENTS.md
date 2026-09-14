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
  session branch `arena/01a09e8b-dominating-south-korea-startin`, verify the remote commit equals
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

## Current state (setup cycle, 2026-09-14)

Tree: 33 files · 30 manifest items · 6 spine entries · 5 NCX navPoints · 8 nav list items · 20 WOFF
faces · 1 image (`cover-bg.jpg`, generated plate, v1) · 3 character cards · 4 introduction cards ·
27 glossary cards · 0 chapters. All gates green; nothing packaged yet — awaiting the reader's raws.
Next cycle is Chapter 1: `raws/ch001_raw.txt` → `work_epub/OEBPS/text/ch001.xhtml` → wire-up
(manifest `ch001`, NCX `num_6`/playOrder 6, one nav `<li>`, cover + OPF stamps → `Chapters 1–1`,
glossary footer → Chapter 1).
