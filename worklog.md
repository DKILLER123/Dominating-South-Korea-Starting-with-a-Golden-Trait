# Dominating South Korea: Starting with a Golden Trait
## Worklog — Version 1 English Publisher's Edition

Purpose: the single state file for this book — what exists, what has been decided, what the raws
have pinned, what is still open, and how to verify any of it. `SKILL.md` owns the rules; this file
owns the history. Read §0 and the newest §8 entry before touching the tree.

---

## 0 · Cycle summary (read this first on resume)

**Cycle 1 complete: Chapters 1–5 translated, gated, packaged, and pushed.** The reader's gate
("no EPUB before the raws") lifted when `raws/ch001_raw.txt` … `raws/ch005_raw.txt` arrived; the five
chapters were drafted from those files only, scanned twice (style-block coverage, interrogative
fidelity), and built. The cover plate and the four character cards are in place, and the front matter
is fully wired.

**Tree state (measured, `reports/workspace_audit.json`):** 5 chapters (`ch001`–`ch005`, next slot
`ch006`) · 11 XHTML documents · 40 manifest items · 11 spine entries in the mandated order ·
10 NCX navPoints · 13 nav items · 5 images (`cover-bg.jpg` 1200×1800 + four 736×920 cards `id-02`…`id-05`)
· 20 embedded WOFF faces · 6 character cards · 6 introduction cards · 35 glossary cards ·
165 reference checks resolved · 16,472 body words · 0 structural errors.
**Package:** `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub` · 43 entries · 1,495,148 B ·
sha256 `acc7869055cfe5092595d0658a423dc2a14885f03b396c7b273f1d2d18178af7` · mimetype STORED first, zip test clean.

**Gates this cycle:** `validate_tree` PASS (11/11 parsed, 0 undefined classes, 0 unresolved refs, 0 Han
outside 61 `lang="ko"` glosses) · `punct_quotes --check --max-para-en 12` PASS · `audit_marks` all five
chapters clean of hard flags (NO-QM? triaged: every survivor is an imperative or an exclamatory
statement the raw itself punctuates with 。/！) · `repeat_check` PASS ×4, REVIEW ×1 (the deliberate
refrain, see the cycle entry below) · `style_audit` PASS (11–14 distinct block types per chapter,
3–6 blocks per 1k words, no repeated device outside the allowlist) · `check_classes` PASS (11 pages,
`edition.css` included) · `legacy_firewall` PASS (0 hard bleed; every soft token cleared by `raws/`
provenance — nothing was allowlisted or weakened) · `sync_styles` PASS · `install_fonts --verify` PASS
· stylelint 0 errors · `style_index --check-skill` PASS · `workspace_audit --assets`:
0 structural errors, `metrics-band` ×3 triaged (the counter includes block furniture; prose-only
measurement is 4.0 em-dashes/1k words max and 71 words longest paragraph, both in band).

**Canon pins:** see §1. Chapter 5 ends on Jessica's silence and the "blade" bargain; Bae Do-yoon holds
two purple entries, one blue, one gold, and no rank he can spend yet.

**Standing directives:** raw-first custody · Deep Scan + Deep Thinking · style-block maximalism (now
machine-gated by `style_audit.py`) · QM/phone-call audits every touched chapter · the reference novel's
content stays out (firewall gate) · book order Cover → Synopsis → Contents → Character Info →
Introductions → Glossary → Ch1 · `raws/` and `image-search/` as the two file stores · reader's
`fonts.css`/`stylesheet.css` preserved exactly · stage names (Jessica/Yoona/Krystal) in prose with the
legal name once on the card · cover carries book name + DKILLER1 + genre, MC visible, no version
strings · **after every final EPUB: commit, push to `arena/01a09e8b-dominating-south-korea-startin`,
verify remote HEAD, deliver the GitHub download link.**

**Next cycle (when the reader supplies Chapter 6):** save `raws/ch006_raw.txt` first → recon greps →
draft `work_epub/OEBPS/text/ch006.xhtml` → wire-up (manifest `ch006`, NCX `num_11`/playOrder 11, one
nav `<li>` at 14, cover `#chapters-stamp` and both OPF stamps → `Chapters 1–6`, glossary header/footer
and the card append as needed) → all of SKILL §9 → worklog §8 entry + §0 refresh → only then
`build_epub.py`, in-archive asserts, seal, push, present. New glossary candidates already promised by
the text: `geomsa-nim` usage in address, `sunbae`/`hubae` on set, `chaebol` in the press voice, and the
营业 (yŏngŏp / "business-mode") register the characters keep calling 营业.

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

1. **Author line — settled in cycle 1.** The reader named the pen **DKILLER1**; it is in `dc:creator`
   and set live on the cover. Nothing from the previous novel's byline survives in the tree.
2. **Trait wording.** "Favor of Rich Women" is my rendering of the raw's `金色天賦詞條【富婆的青睐】`.
   If the raw's Chapter 1 (or a preferred translation) uses different words, that wording wins and
   every later occurrence follows it.
3. **Hangul.** Allowed only as `lang="ko"` glosses on the glossary/character pages (27 glosses now),
   exempted by name in `validate_tree.py`; zero tolerance inside a chapter file. Cycle 1 shipped 29
   `gl-hangul` glosses inside 61 exempted nodes. Say the word if you want Hangul banned outright from
   the glossary too.
4. **Cover art.** v1 (night Han River, faceless) was replaced by the reader-approved plate: the MC in
   frame on the Shilla hillside at dusk, gold seal motif, genre chips, all type live in `cover.xhtml`.
   The pseudo-lettering in the hillside signage was scrubbed with a local feathered blur, verified by
   pixel diff (max 35, mean 3.2). A swap is still a one-cycle change because the plate carries no text.
5. **Portraits — shipped in cycle 1.** `id-02` Bae Do-yoon (commissioned illustration), `id-03`
   Jessica, `id-04` Lee Boo-jin, `id-05` Krystal (real editorial photography, sourced from
   `image-search/`, cropped to 4:5 736×920). The search round was run in the cycle that put them on
   page, per the rule; no likeness was invented for a real person. Next id: `id-06`.
6. **Chapter numbering width.** `chNNN` is three digits, so the tree holds 999 chapters per volume
   under the current pattern. Volume 2 (or a wider pattern) is a decision to make long before ch999.
7. **Stylelint deviations, recorded.** `no-extra-semicolons` no longer exists in stylelint 16, and
   `declaration-block-no-redundant-longhand-properties` is off because the reader's sheet ships one
   longhand block that must not be rewritten. Both are config decisions, not CSS edits.
8. **Sandbox egress.** npm registry and PyPI are reachable; jsdelivr, GStatic and GitHub raw are not.
   Font faces therefore come from `@fontsource` npm packages via `install_fonts.py`.
9. **Repo weight.** The reader's directive keeps every image-search file in `image-search/`, so generation originals stay as delivered (cover original = 1.8 MB PNG). Booked as a decision, not a drift: if history size becomes a problem, the fix is a prune rule for `image-search/*_original.*` agreed with the reader — never a silent deletion of their files.
10. **Not performed this cycle either:** EPUBCheck (no network install in the sandbox), rendering
    proofs in real reader engines, accessibility conformance, and per-glyph fallback rendering. The
    archive was verified structurally instead: mimetype STORED first, zip test, spine/manifest/NCX/nav
    parity, image decode, and 165 resolved references.
11. **Read before flagging the next cycle:** ch004's single internal 8-gram is a deliberate refrain
    (see §8), and `workspace_audit`'s three `metrics-band` hits are furniture-inclusive counters — the
    prose-only measurements sit inside the bands. Both are documented, not open.

---

## 8 · Cycle log (Version 1, newest first)

### Chapters 1–5 translation, art, and first package — September 14, 2026 — complete, EPUB built

**Custody.** `raws/ch001_raw.txt` … `raws/ch005_raw.txt` written verbatim (full-width spacing and all)
before any drafting, alongside the earlier `Synopsis_raw.txt`. Nothing was drafted from recency: each
chapter was drafted with its raw file open, then re-read against it line by line.

**Chapters.** `work_epub/OEBPS/text/ch001.xhtml` … `ch005.xhtml` (2,681 / 3,640 / 3,422 / 3,379 /
3,766 words — `style_audit.py`'s counts, which include block furniture). Two drafting rules earned their keep: never draft from memory (the first pass, written
from recall, invented a café scene and a phone-count detail — both files were rewritten from the raws),
and never let a plausible micro-detail stand unless the raw owns it.

**Second-pass de-invention.** Three invented beats were cut in review: the invented number of missed
calls, a timestamp the raw never gives, and a specific lie Jessica tells her sister (the raw gives her
*silence*, so the chapter now gives her silence, and the closing author-aside was rewritten to argue
about concealment rather than about a fabricated falsehood).

**Style-block dressing (per `reports/style_audit.json`).** ch001: 11 types / 15 blocks (system-block
carries the four entry cards plus the mechanism panel; app-screen, checklist, whisper, dev-quest,
memory, status-panel, lecture, author-aside, char-intro, location-stamp). ch002: 14 types / 14 blocks
(adds pitch-deck for her three options, recording-block for the playback, contract-block, dossier,
briefing, wardrobe). ch003: 11 types / 11 blocks (app-screen, hand-note, contract, dossier, briefing,
checklist, lecture, memory). ch004: 11 types / 11 blocks (briefing/checklist carry the coercion lists,
status-panel carries the "rate she is being quoted", wardrobe the read of the other woman). ch005:
12 types / 13 blocks (hand-letter for the card, app-screen for the phone exchange, memory for the
sister, wardrobe for the shoot). `system-block` and `location-stamp` recur by design; every other device
is used once per chapter, which is what `style_audit.py` enforces.

**Interrogative fidelity sweep.** Raw `？` counts per chapter: 3 / 20 / 21 / 24 / 6. Every one of those
now carries an English `?`. Restored in this pass: ch002 `但她是谁？` → a new beat line "But who is she?";
`所以你觉得我与众不同？`, `所以您就替我规划人生？`, `你以为那是人生规划？` → question marks; the three
options `报警？ 逃跑？ 威胁？` → `pd-firm` titles set as questions (the accepted fourth option
"Take it" stays flat, because it is a decision, not a question). ch003 `昨晚那个女人，也是你规划的一部分？`
→ em-dash re-cast with `?`; `你觉得，我是在给三星集团培养刀？` → `?`. ch004 `可是现在呢？` →
"And where is she now?". ch005 `刀？` → "A blade?"; the sister's `怎么打你电话也打不通？` split into its
own question line. Approved as statements because the raw punctuates them with 。/！, not ？: ch002
`孤儿活该受你欺负啊`, ch004 `你们把我当成什么了`.
Also caught: two span-adjacent punctuation marks that `audit_marks` reads as ` ?` (SPACE-QM) — the mark
now sits inside the `highlight2` span.

**Front matter rebuilt from the seeded stubs.** `introductions.xhtml` is now the cast showcase
(6 `char-intro-block`s; five photographed, the assistant and "the entries" text-only) and
`glossary.xhtml` runs 35 cards across six sections — suffixes, seniority, workplace, family, social
register, expressions — with `lang="ko"` Hangul on the 29 genuine Korean terms and no Han anywhere.
Two glossary slips were fixed on the spot: a half-inserted duplicate card (the insertion helper matched
an indented marker that did not exist — HTML surgery needs regex or exact line targets, not `split`),
and two Han glosses quoted into card text.

**Art.** Cover plate: `image-search/gen_cover_plate_v2.png`, patched locally (feathered streak-blur
over pseudo-lettering in the hillside signage — one image-model pass did not scrub it), resized to
1200×1800 and written to `images/cover-bg.jpg`; all type is live XHTML per SKILL §35, so the plate
carries no baked text and no version strings. Cards: `id-02` Bae Do-yoon (commissioned illustration,
approved by the reader), `id-03` Jessica (Dazed Korea editorial), `id-04` Lee Boo-jin (Yonhap press
editorial), `id-05` Krystal (Urbänlike editorial) — every one cropped to the 4:5 house spec 736×920 at
q90, sources retained in `image-search/`. Getty/Shutterstock hits were rejected for watermarking.

**Reconciliation the reader should know about.** "Editorial-level, never a crop" and "cropped to house
spec" pull against each other for press photography: a magazine editorial is already an editor's crop.
Resolution applied: pick sources shot for print at full resolution, crop only to the 4:5 card frame
(head and shoulders held, no recomposed detail lost), and keep the untouched originals in
`image-search/` for audit.

**Delivery.** Pushed to `arena/01a09e8b-dominating-south-korea-startin` at `9fddac7`; remote HEAD
verified equal to local, and `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub` confirmed present
at that ref (1,495,148 B). The first push attempt of this cycle failed on an expired sandbox GitHub token
— the work stayed committed and was pushed once the connection was refreshed, which is now written into
SKILL §16.8 as the standing rule rather than a note to remember.

**Tooling added this cycle.** `style_audit.py` (root) — counts the §5 block vocabulary per chapter,
floors distinct types at 8, caps blocks/prose at 0.25, and rejects a repeated device outside the
allowlist; wired into SKILL §9. `check_classes.py` now unions `styles/edition.css` into the legal class
set, because the cover's §35 classes live there.

**Repeat-check note.** ch004 reports one internal 8-gram twice: "the one place on her that no one is
allowed to touch". That is the raw's own line `妹妹是她的逆鳞`, which chapter 4 states twice on purpose.
Kept as written; documented here per the gate's REVIEW branch.

**Cross-book hygiene.** `legacy_firewall.py` was *not* modified. `Im Yoon-a` stays a HARD token — that
string never appears in this book, so it costs nothing; every romanization this cycle does use
(Krystal, Lee Boo-jin, Jessica) is a soft token cleared by `raws/` provenance. Seeded front matter was
also re-scanned and de-bleed: two epithets imported with the reference book's cards ("wolf",
"Yama's judge") were cut from `characters.xhtml` before packaging.

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
genericized, and the script **asserts comment-stripped rule identity** (4,205 stylesheet lines +
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

**Finishing pass.** The gate scripts' own docstrings still carried the reference novel's chapter numbers as examples (`ch298.xhtml`, `ch287.xhtml`, a `ch297 cycle` attribution) and `validate_tree.py` justified the Jamo exemption with the other book's four fan blocks: all restated for this book, since process may be inherited but a stray provenance line teaches a future cycle the wrong chapter map. `workspace_audit.py` no longer runs `repeat_check` on an empty tree either, so `reports/` holds no zero-input transcripts. `legacy_firewall.py` now reads only `raws/*.txt` as the provenance corpus, so no README can launder a real-name token into canon. `install_fonts.py --verify` measures digit style and GSUB features per face and fails if the title face is not lining — the inherited "oldstyle figure" folklore is now a measurement (Cardo lining; Cormorant and IM Fell oldstyle; IM Fell has no `lnum` at all).

**Polish pass.** Rereading the seeded pages caught two of the book's own rules being broken by its front matter: the raw's closing rhetorical question (怎么搞起事业来了？) had been flattened to a period on the synopsis page — the exact tell SKILL §3 forbids — and British spellings (colour, labelled, licence, romanisation, apologising) sat next to the sheet's US comments. Both corrected across the tree and the docs, a US-spelling rule added to SKILL §3, and a flattened-interrogative sweep over every quote in the tree now returns 0.

 · `punct_quotes` PASS · `legacy_firewall` PASS ·
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
python3 check_classes.py                               # class tokens vs stylesheets (incl. edition.css)
python3 style_audit.py --json reports/style_audit.json  # block vocabulary coverage per chapter
python3 audit_marks.py work_epub/OEBPS/text/ch001.xhtml # real path
node_modules/.bin/stylelint --config .sl.json "work_epub/OEBPS/styles/*.css"
.venv/bin/python workspace_audit.py --assets            # read-only; rebuilds reports/

python3 build_epub.py                                  # ONLY after an authorized cycle + §8 entry
```

## 10 · Reports index

`reports/workspace_audit.json` (authoritative machine summary) · `archive_inventory.tsv` ·
`source_inventory.tsv` (raws + image-search hashes) · `chapter_index.tsv` · `character_index.tsv` ·
`glossary_index.tsv` · `style_index.tsv` / `.md` · `name_variants.tsv` · `asset_validation.tsv` ·
`editorial_review.tsv` · `fonts_install.json` · `firewall.json` · `style_audit.json` ·
`workspace_audit.json` also carries the package state (sha256, entry count) once built · `validate_tree.txt` ·
`punct_quotes.txt` · `audit_marks.txt` · `repeat_check.txt` · `stylelint.txt` · `legacy_firewall.txt`.
Per-cycle proof goes in `reports/chNNN/`. Empty `stylelint.txt` means no errors.
