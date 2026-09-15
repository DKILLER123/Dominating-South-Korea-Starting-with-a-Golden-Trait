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
session branch `arena/01a0a43e-dominating-south-korea-startin` (the branch each Arena session is
tied to — the 2026-09-15 restore continues on `arena/01a0a43e-…` after
`arena/01a0a030-…`), verify the remote commit equals local HEAD, and provide the GitHub download
link. Never force-push, never touch `main`.
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

## Current state (cycle 10, 2026-09-15 · restored workspace)

Tree: 31 chapters (`ch001`–`ch031`, next slot `ch032`) · 91 payload entries · 88 manifest items ·
37 spine entries · 36 NCX navPoints · 39 nav list items · 20 WOFF faces · 27 images
(`id-01`…`id-27`: repaired cover plate · cards `id-02`…`id-06` with `id-03` reader-provided
Jessica, `id-10`, `id-14`, `id-17`, `id-19`, `id-20`, `id-21`, `id-23` reader-provided Irene ·
plates `wd_*` incl. `id-25 wd_jiyeon_loungewear`, `id-26 wd_leeboojin_tea`, `id-27
wd_jessica_suite`, all photographic-real) · 17 character cards · 17 introduction cards · 54
glossary cards. Package built and verified: 91 entries · 5,177,796 B · sha256 `715f6bea…` —
`work_epub/` byte-identical to the archive on all 91 payloads (re-proven at restore). Delivered
archive snapshots: `extracted/` (v1, 43 entries) and `extracted-v10/` (91 entries). All gates green
(firewall PASS: 0 hard hits, every soft token cleared by `raws/` or the two documented homonym
clearances in `firewall_allowlist.txt`: Park Ji-yeon ← ch017 raw, Bae Joo-hyun ← ch020 raw —
legal name once on card; never for reference content). `repeat_check` exits REVIEW on the
documented shipped-chapter pairs (worklog §2.16). Next chapter slot `ch032` (NCX `num_37`/
playOrder 37, nav li 40; next image id `id-28`). Reserved portraits: `uploads/Ha-Jiwon.png`
(bottom-right watermark crop on adoption) and `uploads/Son-Yejin.jpg` — live the cycle their names
enter prose. `uploads/600.webp` reference-only.
