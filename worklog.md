# Dominating South Korea: Starting with a Golden Trait
## Worklog — Version 1 English Publisher's Edition

Purpose: the single state file for this book — what exists, what has been decided, what the raws
have pinned, what is still open, and how to verify any of it. `SKILL.md` owns the rules; this file
owns the history. Read §0 and the newest §8 entry before touching the tree.

---

## 0 · Cycle summary (read this first on resume)

**Setup cycle complete; no chapters translated yet.** The workspace is built, gated and documented,
and it deliberately contains **no EPUB** (reader directive: nothing is packaged until the raws
arrive). `raws/` holds one file so far — `Synopsis_raw.txt`, the reader's untouched Chinese synopsis.

**Tree state (measured, `reports/workspace_audit.json`):** 32 payload files · 0 chapters ·
6 XHTML documents (cover, synopsis, nav, characters, introductions, glossary) · 30 manifest items ·
6 spine entries in the mandated order · 5 NCX navPoints · 8 nav list items · 1 image
(`cover-bg.jpg`, 1200×1800, 258,247 B) · 20 embedded WOFF faces (all decode) · 3 character cards ·
4 introduction cards · 27 glossary cards · 112 reference checks resolved · 0 structural errors.

**Gates at setup:** `validate_tree` PASS (6/6 parsed, 0 undefined classes, 0 unresolved refs, 0 CJK
outside 56 `lang="ko"` glossary glosses) · `punct_quotes` PASS (0 files) · `legacy_firewall` PASS
(0 hard bleed; the one soft token, Lee Boo-jin, cleared by `raws/` provenance) ·
`sync_styles` PASS (4,205 + 140 rule lines byte-identical to the reader's references) ·
`install_fonts` PASS (20/20 faces; all carry `‘ ’ “ ” – — … ·`; measured figure table: Cardo/Lora/Crimson Pro/Inter/Courier Prime/Libre Baskerville/EB Garamond lining, Cormorant Garamond + IM Fell English oldstyle, Caveat n/a-by-design — title face asserted lining by the script itself) · stylelint PASS (0 errors, 21 active rules) ·
`style_index.py --check-skill` PASS (all 297 class tokens cited in SKILL §5 exist in the sheet).

**Canon pins:** see §1. Nothing else is settled.

**Standing directives:** raw-first custody · Deep Scan + Deep Thinking · style-block maximalism ·
QM/phone-call audits every touched chapter · the reference novel's content stays out (firewall gate)
· book order Cover → Synopsis → Contents → Character Info → Introductions → Glossary → Ch1 ·
`raws/` and `image-search/` as the two file stores · reader's `fonts.css`/`stylesheet.css` preserved
exactly · **after every final EPUB: commit, push to `arena/01a09e8b-dominating-south-korea-startin`,
verify remote HEAD, deliver the GitHub download link.**

**Next cycle (when the reader supplies Chapter 1):** save `raws/ch001_raw.txt` first → recon greps →
draft `work_epub/OEBPS/text/ch001.xhtml` → wire-up (manifest `ch001`, NCX `num_6`/playOrder 6, one
nav `<li>`, cover `#chapters-stamp` and both OPF stamps → `Chapters 1–1`, glossary footer →
Chapter 1, card/glossary appends as needed) → all of SKILL §9 → worklog §8 entry + §0 refresh →
only then `build_epub.py`, in-archive asserts, seal, push, present.

Repository root: this checkout. Session branch: `arena/01a09e8b-dominating-south-korea-startin`.

## 1 · Canon pins

| Item | Pinned value | Source / status |
|---|---|---|
| Title | *Dominating South Korea: Starting with a Golden Trait* | reader directive |
| Protagonist | **Bae Do-yoon** (family name Bae; Korean name order) | reader directive; the raw writes him `裴云` and that rendering never reaches the page |
| Premise at opening | reborn senior → two options → SNU law → prosecutor | `raws/Synopsis_raw.txt` |
| Golden trait | **Favor of Rich Women**, grade Golden, unique to the owner | `raws/Synopsis_raw.txt`; wording may be superseded by the Chapter 1 raw, which then becomes the pin |
| Patron | **Lee Boo-jin**, who demands "a blade of my own" and pays in money, power, beautiful women | raw |
| Third figure | **Jessica Jung**, just out of Girls' Generation, delivered into his path | raw |
| Agency named | SM Entertainment (as the raw has it) | raw |
| Real-name policy | real public figures keep real romanizations **only when this book's raw names them**; no fictionalisation by default | reader choice, 2026-09-14 |
| Character imagery | web-searched real photographs for real people, coded to 736×920 4:5; search files kept in `image-search/` | reader choice |
| Introductions page | cast showcase cards in the section-46 vocabulary (first-look voice, not a fact sheet) | reader choice |
| Cover | generated illustrated plate (no likeness of any real person), v1 installed | reader choice; `image-search/cover_gen_original.png` → `OEBPS/images/cover-bg.jpg` |
| Book order | Cover → Synopsis → Contents → Character Info → Introductions → Glossary → Ch1… | reader directive; enforced by `workspace_audit.py` |
| Typography | the reader's reference sheet, rules untouched: Cardo 700 titles, Lora body, EB Garamond italic pullquotes, Courier Prime system voice | `fonts.css` + `stylesheet.css` at the root, preserved |

**Deliberately NOT pinned** (each is a raw's business, not this file's): Do-yoon's age, DOB, height,
family, office, the trait's exact wording, any song/title/date/relationship, roster counts, or which
real figures recur. The front-matter pages say only what the synopsis says.

## 2 · Open decisions & flags

1. **Author line.** `dc:creator` is the placeholder "Original Korean web serial · English edition"
   and the cover carries no author name. Give me a pen name (or "leave it") and it is a one-line
   metadata + cover edit before the first ship.
2. **Trait wording.** "Favor of Rich Women" is my rendering of the raw's `金色天賦詞條【富婆的青睐】`.
   If the raw's Chapter 1 (or a preferred translation) uses different words, that wording wins and
   every later occurrence follows it.
3. **Hangul.** Allowed only as `lang="ko"` glosses on the glossary/character pages (27 glosses now),
   exempted by name in `validate_tree.py`; zero tolerance inside a chapter file. Say the word if you
   want Hangul banned outright from the glossary too.
4. **Cover art v1.** The plate is a night Han River skyline with a faceless silhouette; its gold seal
   motif sits under the title band, and the overlay's scrim keeps the words legible. Regenerating with
   a clear title band or a different motif is a one-cycle change.
5. **Portraits.** All three character cards ship with no image on purpose: nothing about a real
   person's likeness is invented before a search round, which happens in the same cycle as the chapter
   that first puts them on page.
6. **Chapter numbering width.** `chNNN` is three digits, so the tree holds 999 chapters per volume
   under the current pattern. Volume 2 (or a wider pattern) is a decision to make long before ch999.
7. **Stylelint deviations, recorded.** `no-extra-semicolons` no longer exists in stylelint 16, and
   `declaration-block-no-redundant-longhand-properties` is off because the reader's sheet ships one
   longhand block that must not be rewritten. Both are config decisions, not CSS edits.
8. **Sandbox egress.** npm registry and PyPI are reachable; jsdelivr, GStatic and GitHub raw are not.
   Font faces therefore come from `@fontsource` npm packages via `install_fonts.py`.
9. **Repo weight.** The reader's directive keeps every image-search file in `image-search/`, so generation originals stay as delivered (cover original = 1.8 MB PNG). Booked as a decision, not a drift: if history size becomes a problem, the fix is a prune rule for `image-search/*_original.*` agreed with the reader — never a silent deletion of their files.
10. **Not performed at setup:** EPUBCheck, visual proofs in real reader engines, accessibility
   conformance, per-glyph fallback rendering, and any literary proofreading of chapters that do not
   exist yet.

---

## 8 · Cycle log (Version 1, newest first)

### Workspace setup — September 14, 2026 — complete, no build

**Source & scope.** Reader supplied: the book title, the protagonist's name, the four inherited
process files, the two reference stylesheets, `raws/Synopsis_raw.txt`, and the instruction to set up
the workspace only (no EPUB until raws arrive). Four decisions were taken from the reader in this
cycle: Introductions = cast showcase; cover = generated illustration; real names kept as the raw has
them; character images = web-searched real photographs. No chapter raw was supplied and none was
invented.

**Tree created.** `work_epub/` with `mimetype` (exact `application/epub+zip`, no trailing byte),
`META-INF/container.xml`, `OEBPS/content.opf` (EPUB 3 + `dcterms:modified`, numeric image ids
starting at `id-01`), `OEBPS/toc.ncx` (five leading navPoints, chapter anchor comment),
`OEBPS/text/{cover,synopsis,nav,characters,introductions,glossary}.xhtml`,
`OEBPS/styles/{fonts,stylesheet}.css`, `OEBPS/fonts/` (20 WOFF), `OEBPS/images/cover-bg.jpg`.
Spine order is the reader's mandated structure order and is now machine-checked.

**Assets.** Stylesheets installed by `sync_styles.py`, which rewrites only comments: the top banner
now brands this book, the reference novel's proper nouns and chapter-map provenance lines were
genericised, and the script **asserts comment-stripped rule identity** (4,205 stylesheet lines +
140 fonts lines). Fonts installed by `install_fonts.py` from `@fontsource` v5 packages, latin subsets,
mapped to the house file names `fonts.css` already declares; 20/20 verified for `‘ ’ “ ” – — … ·`.
Cover: `generate_image` original kept at `image-search/cover_gen_original.png`, then 1.4 % top-edge
artefact trimmed, side padding from blurred darkened edge strips (so a reader page cannot slice off
the palace or the tower), resized 1200×1800, JPEG q85 progressive → 258,247 B, and **the installed
file was opened and inspected**, not just the generation.

**Tooling adapted (not copied blind).** `build_epub.py` → new deliverable name.
`workspace_audit.py` → this book's package name, front-matter order check, per-chapter spine slot
check, `image-search/` in the source inventory, this book's name-variant list, `legacy_firewall`
added as a gate, and two fresh-workspace crashes fixed (missing archive now records
`package-not-built`; empty numeric-image set no longer breaks `max()`; `audit_marks` skipped when
there are no chapters). `validate_tree.py` → CJK gate gained the documented `lang="ko"` gloss exemption,
never applied to chapter files, and reports the exempted count. New: `legacy_firewall.py`
(hard/soft bleed gate + raw-provenance clearing), `sync_styles.py`, `install_fonts.py`,
`style_index.py` (section/class vocabulary index; `--check-skill` proves SKILL §5 cites only real
classes), `package.json` scripts, `.sl.json`, `.gitignore`, `raws/README.md`, `image-search/README.md`.

**Firewall.** The reference novel's own inventions (protagonist and aliases, invented companies and
products, its ships/songs/tour, its cast) are hard-blocked everywhere in the tree. Real public
figures shared by both books are soft-flagged and cleared only when `raws/` names them. Setup result:
0 hard hits; 4 soft hits on one name, cleared by the synopsis raw. Inherited docs moved to
`reference/peninsula-inherited/` byte-for-byte with `reference/README.md` stating the boundary; the
installed stylesheet additionally has to pass the same token list.

**Content authored (seeded, marked as seeded).** Synopsis page translated from `Synopsis_raw.txt`
with its own structure (pullquote, `dev-quest` ultimatum, `system-block` trait ledger, `dossier-block`
edition facts); three character cards; four introduction cards; 27 glossary cards across all six
sheet variants; a Contents page with the five reference entries, the chapter anchor comment and three
landmarks. No age, date, height, song, title or relationship was invented anywhere.

**Verification.** `validate_tree` PASS · `punct_quotes` PASS · `legacy_firewall` PASS ·
`sync_styles` PASS · `install_fonts` PASS · stylelint PASS · `style_index --check-skill` PASS ·
`workspace_audit.py --assets` → `structural_errors: []` after the cover plate was installed,
`package_state: not built yet (setup cycle)`, 112 reference checks, 20 assets decoded.
`repeat_check` has nothing to compare (0 chapters) and `audit_marks` is not invoked at setup.

**Ship.** None. No EPUB was built, so nothing was sealed and `build_epub.py` was not run. This cycle
is committed and pushed as a tooling/state checkpoint on the session branch, which the reader's rule
requires after every **final EPUB** and which this workspace also honours for setup checkpoints.

---

## 9 · Verification commands

```bash
npm ci --ignore-scripts --no-audit --no-fund          # stylelint + @fontsource faces
python3 -m venv .venv && .venv/bin/pip install -r requirements-audit.txt

python3 sync_styles.py                                # tree stylesheets from the references
python3 install_fonts.py                              # 20 WOFF faces from npm
.venv/bin/python install_fonts.py --verify             # glyph coverage
python3 style_index.py --check-skill                  # vocabulary index + playbook self-check

python3 validate_tree.py
python3 punct_quotes.py
python3 legacy_firewall.py --json reports/firewall.json
python3 repeat_check.py ch001.xhtml                    # bare filename, one chapter at a time
python3 audit_marks.py work_epub/OEBPS/text/ch001.xhtml # real path
node_modules/.bin/stylelint --config .sl.json "work_epub/OEBPS/styles/*.css"
.venv/bin/python workspace_audit.py --assets            # read-only; rebuilds reports/

python3 build_epub.py                                  # ONLY after an authorized cycle + §8 entry
```

## 10 · Reports index

`reports/workspace_audit.json` (authoritative machine summary) · `archive_inventory.tsv` ·
`source_inventory.tsv` (raws + image-search hashes) · `chapter_index.tsv` · `character_index.tsv` ·
`glossary_index.tsv` · `style_index.tsv` / `.md` · `name_variants.tsv` · `asset_validation.tsv` ·
`editorial_review.tsv` · `fonts_install.json` · `firewall.json` · `validate_tree.txt` ·
`punct_quotes.txt` · `audit_marks.txt` · `repeat_check.txt` · `stylelint.txt` · `legacy_firewall.txt`.
Per-cycle proof goes in `reports/chNNN/`. Empty `stylelint.txt` means no errors.
