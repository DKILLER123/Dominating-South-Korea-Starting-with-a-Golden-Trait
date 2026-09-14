# Workspace ready — *Dominating South Korea: Starting with a Golden Trait*

**Setup date:** September 14, 2026 (Asia/Kolkata) · **Repository:** `DKILLER123/Dominating-South-Korea-Starting-with-a-Golden-Trait`
**Session branch:** `arena/01a09e8b-dominating-south-korea-startin` (from `main` @ `538eb5f`) —
cycle 2 continues on `arena/01a0a030-dominating-south-korea-startin`; this report describes the
setup cycle only, current state lives in `worklog.md` §0
**Workspace root:** `/home/user/Dominating-South-Korea-Starting-with-a-Golden-Trait`
**Deliverable when built:** `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub`

This is a **setup report, not a production report**: no chapter has been translated and **no EPUB has
been built**, per the reader's instruction ("No need to create epub file for now until I provide the
raws"). Everything the next cycle needs to run is installed, gated and documented.

## 1 · What the reader supplied, and how each piece is used

| Supplied | Used as | Status |
|---|---|---|
| Title + "MC's Name is Bae Do-yoon" | book identity and every naming decision | pinned in worklog §1 |
| `SKILL.md`, `worklog.md`, `WORKSPACE_SETUP.md`, `AGENTS.md` from the previous novel | **skills and process only** | moved byte-for-byte to `reference/peninsula-inherited/`; boundary stated in `reference/README.md` |
| `fonts.css`, `stylesheet.css` | this book's fonts and styles | kept untouched at the root as references; tree copies installed by `sync_styles.py` with rule identity asserted |
| `raws/Synopsis_raw.txt` | the synopsis page's only source, and the firewall's provenance corpus | untouched, hashed in `reports/source_inventory.tsv` |
| Instructions: folder roles, book order, no-bleed rule, GitHub push after every final EPUB | encoded as gates and standing directives | SKILL §16, §2 step 8 |

## 2 · Layout

```text
Dominating-South-Korea-Starting-with-a-Golden-Trait/
├── AGENTS.md                  read-first handoff (this book)
├── SKILL.md                   the playbook: pipeline, voice, canon, blocks, gates, traps
├── worklog.md                 state: §0 summary · §1 canon pins · §2 open decisions · §8 cycle log
├── WORKSPACE_SETUP.md         this report
├── fonts.css / stylesheet.css reader's reference assets — never edited
├── build_epub.py              packer (overwrites the deliverable; not run at setup)
├── validate_tree.py            XHTML / classes / quotes / CJK(with lang="ko" gloss exemption)
├── punct_quotes.py repeat_check.py audit_marks.py
├── legacy_firewall.py          reference-novel bleed gate (hard) + raw-provenance clearing (soft)
├── sync_styles.py              installs the tree's stylesheets and proves rule identity
├── install_fonts.py            rebuilds the 20 WOFF faces from @fontsource
├── style_index.py              section/class vocabulary index; --check-skill audits SKILL §5
├── workspace_audit.py          read-only full audit → reports/
├── .sl.json                    stylelint 16 core config (21 active rules)
├── package.json                scripts: fonts / styles / lint / gates / audit / index / build
├── raws/                       source custody: chNNN_raw.txt (+ README with the rules)
├── image-search/               image workbench: searches, generation originals, coding spec (+ README)
├── reports/                    generated audit output (rebuildable)
├── reference/peninsula-inherited/  the previous novel's four files, archived for process only
└── work_epub/
    ├── mimetype                exact application/epub+zip, no trailing byte
    ├── META-INF/container.xml
    └── OEBPS/
        ├── content.opf         EPUB 3 + NCX hook; numeric image ids from id-01
        ├── toc.ncx             five leading navPoints, chapter anchor comment
        ├── text/               cover · synopsis · nav(Contents) · characters · introductions · glossary
        ├── images/             cover-bg.jpg (1200×1800, 258,247 B)
        ├── fonts/              20 WOFF faces
        └── styles/             fonts.css · stylesheet.css (this book's forked copies)
```

**Reading order of the book, enforced in the spine:** Cover → Synopsis → Contents → Character Info →
Introductions → Glossary → Chapter 1 → … `workspace_audit.py` fails the package if the spine opens with
anything else, so the order cannot drift silently.

## 3 · Verified numbers (measured, not asserted)

| Property | Value |
|---|---:|
| Payload files in tree | 33 |
| Chapters | 0 (awaiting raws) |
| XHTML documents | 6 (5 reference pages + nav) |
| Manifest items | 30 |
| Spine entries | 6 |
| NCX navPoints | 5 |
| nav list items (incl. 3 landmarks) | 8 |
| Embedded WOFF faces (all decode) | 20 |
| Images declared / installed | 1 / 1 |
| Character cards · introduction cards · glossary cards | 3 · 4 · 27 |
| Stylesheet rule lines vs the reader's reference | 4,205 identical |
| fonts.css rule lines vs the reader's reference | 140 identical |
| Reference checks resolved (hrefs, srcs, CSS `url()`, fragments) | 112 |
| Structural errors | 0 |
| Straight double quotes / CJK in prose | 0 / 0 (56 Hangul glosses exempted as `lang="ko"`) |
| Hard firewall hits | 0 |

Formulas for the next cycle, one chapter and no new assets: tree 34 · manifest 31 · spine 7 ·
navPoints 6 (`num_6`, playOrder 6) · nav li 9 · `next_ncx_play_order` and `next_nav_li_after_chapters`
are printed by the audit so they are never guessed.

## 4 · Gate results at setup

| Gate | Result |
|---|---|
| `python3 validate_tree.py` | **PASS** — 6/6 parsed, 0 undefined classes, 0 unresolved refs, 0 straight quotes, 0 CJK outside sanctioned glosses |
| `python3 punct_quotes.py` | **PASS** — 0 files to rewrite |
| `python3 legacy_firewall.py --json reports/firewall.json` | **PASS** — 0 hard hits; 1 soft name (Lee Boo-jin) cleared by `raws/` |
| `python3 sync_styles.py` | **PASS** — installed, and comment-stripped CSS proven identical |
| `python3 install_fonts.py` (+ `--verify` under `.venv`) | **PASS** — 20 faces, `fonts.css` fully resolved, critical glyphs present, lining digits confirmed for Cardo |
| `python3 style_index.py --check-skill` | **PASS** — 297 class tokens cited in SKILL §5 all exist in the sheet |
| `node_modules/.bin/stylelint --config .sl.json "work_epub/OEBPS/styles/*.css"` | **PASS** — 0 errors (2 config deviations recorded in worklog §2.7) |
| `.venv/bin/python workspace_audit.py --assets` | **structural_errors: []**; `package_state: "not built yet (setup cycle)"` |
| `repeat_check` / `audit_marks` | not applicable at setup — no chapter file exists yet, and the audit no longer invokes them on an empty tree |
| `build_epub.py` | **not run** — deliberate |

**Not performed:** EPUBCheck, rendering proofs in real reader engines, accessibility conformance,
per-glyph fallback verification, likeness review of the cover by the reader. Nothing here certifies
typographic behavior on a device; it certifies structure, references and asset integrity.

## 5 · Standing rules carried into every cycle

1. **Raw first**, verbatim, into `raws/chNNN_raw.txt`, before recon or drafting. A re-paste becomes
   `_v2` and gets diffed; custody is never overwritten.
2. **Deep Scan + Deep Thinking**, and **style-block maximalism**: every context the raw gives owns a
   block, and a thin context is filled from understanding instead of being dropped as plain prose.
3. **The tree is canon**; the raw is input. Nothing in a front-matter page or in SKILL.md licenses a
   fact a chapter has not yet stated.
4. **No bleed.** The previous novel's characters, companies, labels, songs and chapter map may not
   appear in this book — the firewall gate blocks a build, and the stylesheet fork carries a token
   check of its own.
5. **Reader files are read-only.** `fonts.css`, `stylesheet.css` and `raws/Synopsis_raw.txt` keep
   their bytes; forks and translations are derived by script.
6. **GitHub after every final EPUB:** commit + push to this session branch, verify the remote HEAD
   matches, hand over the download link. Never force-push, never `main`.

## 6 · Resume

```bash
cd /home/user/Dominating-South-Korea-Starting-with-a-Golden-Trait
npm ci --ignore-scripts --no-audit --no-fund
python3 -m venv .venv && .venv/bin/pip install -r requirements-audit.txt   # optional, for --assets
.venv/bin/python workspace_audit.py --assets
python3 legacy_firewall.py
```

Then supply Chapter 1's raw and the production cycle in SKILL §2 begins: `raws/ch001_raw.txt` first,
draft → images (search files into `image-search/`) → wire-up → gates → worklog → build → seal →
push → present. Dependencies are git-ignored and must be reinstalled after a sandbox reset;
`work_epub/`, `raws/`, `image-search/` and `reports/` are kept in history.
