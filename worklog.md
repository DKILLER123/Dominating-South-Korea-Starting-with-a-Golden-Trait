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

**Cycle 2 complete: extraction, cover shoulder repair, realistic wardrobe plates, rebuild.** The v1
archive was unpacked entry-for-entry into `extracted/` (parity proven archive == extracted ==
work_epub); the beige blur rectangle left at the MC's left shoulder by cycle 1's lettering scrub was
repaired in place — Poisson-grafted rectangle only, every pixel outside it byte-identical to the
approved plate; four photographic-real images joined the book (the assistant's canonical portrait
`id-06`, and wardrobe plates `id-07`–`id-09` generated from the subjects' in-book card portraits so
each matches its character image 100%); the missing `#chapters-stamp` was implemented on the cover
with `edition.css` §58; the package was rebuilt, sealed and pushed.

**Cycle 3 complete: chapters 6–10, checklist/lecture/plain-block redesigns, Boram cast** (details in
§8). **Cycle 4 complete: chapters 11–15, reader-supplied portraits, JYP arc cast.** The reader
uploaded `uploads/Boram.jpg` (adopted as the authoritative Boram card master — `id-10` replaced in
place, and all Boram plates regenerated identity-locked to it), plus `uploads/Irene.jpg` and
`uploads/Jiyeon.jpg` (RESERVED for Irene and Jiyeon when they first appear in prose — do not use
early) and `uploads/600.webp` (the original serial cover; source reference only — watermarked and
CJK, never usable as our cover or chapter art). New masters: Kim Mi-joo `id-14`, Bae Suzy `id-17`
(approved `image-search/bae-suzy…pr-1`), Park Jin-young `id-19` (approved
`image-search/park-jin-young…-2`); plates `wd_boram_disguise`/`wd_boram_loungewear` (v2, re-locked),
`wd_boram_morning` (ch011), `wd_kim_miju_plain` (ch013), `wd_suzy_meeting` (ch014). Cast pages grown
8→13 cards/intros (Mi-joo, Suzy, Park Jin-young with portraits; Park Dae-jun, Park Jung-hwan
text-only); glossary 36→39 (`sasaeng`, `ganjang gejang`, `Nation’s First Love`); id-10 caption/alt
corrected to "Reader-provided portrait, street editorial" everywhere.

**Tree state (measured, `reports/workspace_audit.json`):** 15 chapters (`ch001`–`ch015`, next slot
`ch016`) · 21 XHTML documents · 67 payload entries · 64 manifest items · 21 spine entries ·
20 NCX navPoints · 23 nav list items · 19 images (`cover-bg.jpg` 1200×1800 repaired in place ·
cards `id-02`…`id-06`, `id-10`, `id-14`, `id-17`, `id-19` at 736×920 · wardrobe/scene plates
`wd_*` at 1120×1400) · 20 embedded WOFF faces · 13 character cards · 13 introduction cards ·
39 glossary cards · 296 reference checks resolved · 47,126 body words · 0 structural errors.
**Package:** `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub` · 67 entries · 3,743,733 B ·
sha256 `48d6bce0ee4b9373f197b89c353da2fdcbded27fd6f9fc76897b8fca44f808b8` · mimetype STORED first,
zip test clean. (Cycle-3 package it replaces: 56 entries · 2,884,650 B · sha256 `748469d4…`.)

**Gates this cycle:** `validate_tree` PASS (21/21 parsed, 0 unresolved refs, 0 Han outside the
`lang="ko"` glosses) · `audit_marks` all five new chapters RESULT: OK (NO-QM? survivors triaged:
every one an imperative or statement the raw punctuates with 。) · `repeat_check` reviewed (surviving
flags are raw-faithful refrains: pullquote echoes, the line the raw itself splits across ch014/ch015,
the EXO/“occasionally” beats) · `style_audit` PASS (15 chapters; ch011–ch015 at 8/8/10/8/8 distinct
block types) · `check_classes` PASS (21 pages) · `legacy_firewall` PASS (soft Lee Boo-jin ×33 cleared
by raws provenance) · `workspace_audit`: package built, parity archive == extracted == work_epub
(0/0/0), 0 structural errors · in-archive asserts: entries = manifest + 3, 27 image refs 0 broken,
stamps `Chapters 1–15` ×3, glossary 39, cards/intros 13/13, v2 plates byte-identical.

**Canon pins:** see §1. Chapter 5 ends on Jessica's silence and the "blade" bargain; Bae Do-yoon holds
two purple entries, one blue, one gold, and no rank he can spend yet.

**Standing directives:** raw-first custody · Deep Scan + Deep Thinking · style-block maximalism (now
machine-gated by `style_audit.py`) · QM/phone-call audits every touched chapter · the reference novel's
content stays out (firewall gate) · book order Cover → Synopsis → Contents → Character Info →
Introductions → Glossary → Ch1 · `raws/` and `image-search/` as the two file stores · reader's
`fonts.css`/`stylesheet.css` preserved exactly · stage names (Jessica/Yoona/Krystal) in prose with the
legal name once on the card · cover carries book name + DKILLER1 + genre, MC visible, no version
strings · **every AI-generated image photographic-real, never animatic** (reader, cycle 2) ·
**wardrobe/scene plates generated from the subject's in-book card portrait as identity source, and
labeled on their caption line** (reader, cycle 2) · `extracted/` keeps the unpacked snapshot of each
delivered archive · **after every final EPUB: commit, push to the session branch
(currently `arena/01a0a030-dominating-south-korea-startin`), verify remote HEAD, deliver the GitHub
download link.**

**Next cycle (when the reader supplies Chapter 16+):** next numeric image manifest id is `id-20`.
Save `raws/ch016_raw.txt` first → recon greps → draft `work_epub/OEBPS/text/ch016.xhtml` → wire-up
(manifest `ch016`, NCX `num_21`/playOrder 21, nav `<li>` 24, cover `#chapters-stamp` and both OPF
stamps → `Chapters 1–16`, glossary header/footer + cards as earned) → all of SKILL §9 → worklog §8
entry + §0 refresh → only then `build_epub.py`, in-archive asserts, seal, push, present. Reserved
portraits: `uploads/Irene.jpg` (Irene, Red Velvet) and `uploads/Jiyeon.jpg` (Jiyeon, T-ara) go live
the cycle their names first appear in prose. Name discipline for the JYP arc: 裴云 → Bae Do-yoon;
裴秀智 → Bae Suzy; 朴振英 → J.Y. Park / Park Jin-young; 金美珠 → Kim Mi-ju;
朴正焕 → Park Jung-hwan; 朴大俊 → Park Dae-jun; 全宝蓝 → Boram.

Repository root: this checkout. Session branch: `arena/01a0a030-dominating-south-korea-startin`.

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
12. **Realism directive (cycle 2, reader).** Every AI-generated image — portrait, wardrobe plate,
cover repair — must be photographic-real and natural-feeling; animatic or cartoon style is banned.
The reader-approved cover plate keeps its painterly treatment (approved cycle 1); the directive
governs what is generated, and any repair of the plate must match the plate's surrounding style.
13. **Per-block plates for one outfit (cycle 2, reader override).** SKILL §7's "same outfit twice =
no plate" yields to the reader's wardrobe-image directive: where one outfit carries two different
scene reads (the assistant standing in the corridor, ch002 / seated at the tea lounge, ch004), each
block keeps its own plate, both generated from one identity source so the woman is the same woman.
14. **`extracted/` snapshots (cycle 2).** The unpacked contents of each delivered archive live in
`extracted/` for future use — a read-only snapshot of what shipped, never a second live tree. The v1
snapshot (43 entries, sha256 `acc78690…`) stays there although the root deliverable has since been
rebuilt; `work_epub/` is the only tree the gates and the packer read.

---

## 8 · Cycle log (Version 1, newest first)

### Cycle 4 — chapters 11–15, reader-supplied portraits, JYP arc — September 14, 2026 — complete, EPUB built

Raws `ch011`–`ch015` saved verbatim before drafting. Reader uploads adopted: `uploads/Boram.jpg`
replaced `id-10` as the authoritative Boram master (ch009/ch010 plates regenerated as v2, identity-
locked to the new master; ch011 morning plate `wd_boram_morning` generated from it too); Irene and
Jiyeon uploads held in reserve; `600.webp` reference-only. New art: `id-14` Kim Mi-joo (generated
master), `id-17` Bae Suzy (pr-1 approved; cy 0.30), `id-19` Park Jin-young (pjy-2 approved; cy
0.25); plates `wd_kim_miju_plain` (ch013 plain-clothes block), `wd_suzy_meeting` (ch014 meeting-room
block). Chapters: ch011 gejang-night debt + morning hallway + prosecutor-hall file drop (menu-block;
8 distinct); ch012 file-speed wager with Mi-ju, lunch politics, petition arrives (checklist, memory,
dossier, briefing, official-statement; 8 distinct); ch013 JYP side-gate visit, escalation-ladder
lecture, Judicial Monster entry-note, practice-room whispers, Suzy intro (whisper-block; 10
distinct); ch014 originals disappoint, J.Y. Park enters, Suzy testimony + sealed-box memory, status-
panel scoreboard (8 distinct); ch015 the tour, EXO confession, SM-door story, the business card,
Mi-ju’s crossed-out headline (8 distinct). Author-aside labels this cycle: crab debts / soft
persimmons / PR-as-investigation / women-and-speed / “On occasionally”. Cast pages 8→13, glossary
36→39, stamps → Chapters 1–15. Four Han slips caught pre-build (ch012, ch013, ch015 ×2) — full-tree
CJK scan clean. Package: 67 entries · 3,743,733 B · sha256 `48d6bce0…`. Pushed to the session
branch; remote HEAD verified.

### Cycle 3 — chapters 6–10, style redesigns, Boram cast — September 14, 2026 — complete, EPUB built

Raws `ch006`–`ch010` saved verbatim to `raws/` before any drafting (reader's raw-first rule). Reader
asks this cycle: (1) `checklist-block` steps properly separated; (2) `lecture-block` and other plain
blocks redesigned colorful/stylist; (3) Deep Scan + Deep Thinking on everything; (4) pre-package deep
scan for missing style blocks and question-mark implementation.

Style work — `styles/edition.css` §59–§63 (overrides only, `fonts.css`/`stylesheet.css` untouched):
§59 dashed-cyan separators between `.ckl-step` items + gradient lit `.ckl-count` badge; §60 dark-slate
gradient lecture card with gold left border, rose header mark, cyan `.lect-q` chips; §61 violet-night
memory album with gold spine, lilac label, sepia voice, cyan `.bright` variant; §62 amber glowing
notification toast; §63 cream author-aside card with gold ribbon label. `<link … edition.css/>` added
to the heads of all 11 non-cover text pages (cover already carried it). stylelint 0 errors.

Art — Boram master chosen from image-search set (`image-search/ph-5`, clean); encoded `id-10.jpg`
736×920 (stage-era promotional crop; caption labels it). Wardrobe plates, all identity-locked and
visually checked against their card portraits: `id-11 wd_bae_doyoon_prosecutor.jpg` (ch008 mirror,
from `id-02`), `id-12 wd_boram_disguise.jpg` (ch009 supermarket line, cap + oversized coat + snacks,
from `id-10`), `id-13 wd_boram_loungewear.jpg` (ch010 doorway, pale blue loungewear; v1 rejected for
face drift, v2 generated from dual refs `id-10` + disguise plate and approved).

Chapters — ch006 (Krystal; whisper, bright memory, hand-note, dossier, Kwon text-only intro card,
unanswered phone-call, half-truths aside) · ch007 (relationship audit dossier, declined ring, the
connected call in a phone-call block, sisterhood hug, candidate-list checklist, unknown-number SMS in
app-screen, ledger demand in finance-block) · ch008 (mirror wardrobe read, career-ladder checklist,
3 a.m. library memory, recall status-panel, Training-Institute hand-note, appointment
official-statement, day-one briefing, prosecution-hierarchy lecture, movers next door) · ch009
(sunbae-hubae lecture, supermarket disguise wardrobe, stalking-case dossier, dropped-key standoff,
Boram intro card with `id-10`, Jeon Doo-ram name gag, Idol Killer system-block) · ch010 (search
app-screen, controversy news-digest with both sides hedged as the raw states them, archived
comment-thread, theft-file dossier, evidence-vs-emotion lecture, corridor memory, loungewear
wardrobe, bulb scene, her offer to help closing the chapter on its title). Distinct style types per
chapter: 8 / 8 / 10 / 8 / 9 (floor 8). Every raw interrogative carries “?” in English; imperative and
statement-shaped lines keep periods (triaged per audit_marks). No Han characters in chapter prose.

Wiring — manifest + spine ch006–ch010; NCX `num_11`–`num_15` playOrder 11–15; nav li ×5 (18 total);
cover stamp and both OPF descriptions → Chapters 1–10; glossary +1 card (“-ah / -ya”, earned by the
ch006 manager-mimic line) → 36, footer line updated; characters + introductions gain Boram (photo
`id-10`) and Kwon Young-il (text-only, “also written: Tyler Kwon (English press)”).

Gates — stylelint 0 · check_classes OK · validate_tree PASS · style_audit PASS (10 chapters) ·
legacy_firewall PASS · repeat_check triaged (deliberate pullquote echoes + the raw's repeated
dinner-lie) · structural container-child scan clean after fixing one `sys-line` missing its
`sys-value` span in ch009 · pre-package deep scan: no missing style blocks, all interrogatives
implemented with “?”.

Package — 56 entries · 2,884,650 B · sha256 `748469d471576c5a112643251c683cb55e59b5550015af2caa0dc1dd42612880`.
In-archive asserts: manifest 53 · spine 16 · navPoints 15 · nav li 18 · images 13 · char cards 8 ·
intro cards 8 · glossary 36 · cover stamp + both description stamps at Chapters 1–10 · all four new
images present. workspace_audit parity CLEAN after build. Committed and pushed to
`arena/01a0a030-dominating-south-korea-startin`.

### EPUB extraction, cover shoulder repair, realistic wardrobe plates — September 14, 2026 — complete, EPUB rebuilt

**Reader directives this cycle.** (a) extract every file of the delivered EPUB for future use;
(b) every AI-generated image must be realistic and natural-feeling — never animatic; (c) the
wardrobe blocks must carry AI-generated images that match each block's description **and** match the
subject's in-book character image 100% — no random look-alike generation; (d) fix the glitch near the
MC's shoulder on the cover.

**Extraction.** The shipped v1 archive (`sha256 acc78690…`, 43 entries) was unpacked, entry for
entry, into `extracted/` (`extracted/README.md`), and parity was proven three ways:
archive == `extracted/` == `work_epub/` on all 43 payloads. `extracted/` is kept as the immutable
snapshot of what v1 shipped; `work_epub/` remains the live tree. Nothing was moved or renamed.

**Cover repair.** The "glitch" was cycle 1's feathered streak-blur — applied then to scrub
pseudo-lettering out of the hillside signage — surviving as a flat beige rectangle at
x∈[374,496], y∈[804,866], flush against the MC's left shoulder. The pre-blur original
(`gen_cover_plate_v2.png`) still carries the pseudo-lettering, so it could not be restored from.
Repair chain: one image-model pass reconstructed the rectangle in the plate's own painterly style
(`gen_cover_plate_v3_shoulderfix.png`); the edit was proven pixel-aligned with the installed plate
(best shift (0,0)); **only the artifact rectangle** was grafted onto the approved plate by Poisson
cloning (`cv2.seamlessClone`, mask x∈[370,507], y∈[800,870]); the remaining straight borders were
melted with a raised-cosine-feathered 2 px Gaussian strip on top/bottom/left. Measured: changed bbox
(365–505, 795–875), max |Δ| ≤ 3/255 anywhere outside it; 5× zoom inspection shows the ridge, haze,
skyline and shoulder line running continuously through the old rectangle. Lossless master kept at
`image-search/gen_cover_plate_v3_fixed_master.png`; installed `images/cover-bg.jpg` re-encoded
1200×1800 q85 progressive, 324,774 B. Every pixel outside the rectangle is the reader-approved plate.

**Realistic art pass (no animatic generation anywhere).** Four new images, all photographic-real:
`id-06` the President's assistant — canonical portrait commissioned from the raw's own read of her
(twenty-seven/eight, black suit, hair pinned at the nape, polite smile applied like a uniform),
736×920 q85, 62,725 B, installed on her character card (`ci-photo` + provenance caption) and on her
introduction card (both were text-only before); `id-07` `wd_assistant_suit.jpg` — the ch002 wardrobe
plate (corridor greeting, hands empty and still in front, slight bow), 1120×1400 q85, 116,129 B;
`id-08` `wd_assistant_tealounge.jpg` — the ch004 wardrobe plate (seated at the tea-lounge table,
hands unhurried on the white cloth beside a cup and a closed folder), 130,492 B; `id-09`
`wd_jessica_trench.jpg` — the ch005 five-piece-armour plate (dark sunglasses, black mask, hair down,
belted trench, high heels, bright arrivals hall with press), 245,765 B. **Identity chain:** the
assistant's two plates were generated from her `id-06` original as the identity source, and Jessica's
plate from her in-book card photograph `id-03` — so every plate matches the character image on page
100%, per the reader's directive, instead of being a random outfit match. Each plate is embedded in
its wardrobe block as `wd-photo` with a `wd-sub` caption line ("Plate set from her card portrait —
…"), and the character-page `char-note` now states that scene plates set from a card portrait carry
the same labeling and never invent a likeness a card does not hold. The "same outfit twice = no
plate" default was overridden by the reader for the assistant: same suit, two different scene reads
(corridor standing / tea-lounge seated), so each block carries its own plate of the same woman.

**Doc drift fixed.** v1 shipped without the `#chapters-stamp` element SKILL §8.4/§12 mandate; the
cover page now carries `<p class="cover-stamp" id="chapters-stamp">Chapters 1–5</p>` and
`edition.css` gained §58 to style it (courier line inside the bottom veil, chapter range only, no
version strings). The in-archive assert set now checks it.

**Wire-up.** manifest `id-06`…`id-09` (image items 5 → 9); no spine / NCX / nav changes (no new
documents); reference checks 165 → 178; body words 16,472 → 16,502 (captions + stamp); tree payload
files 43 → 47.

**Gates.** `validate_tree` PASS (11/11 parsed, 0 undefined classes, 0 unresolved refs, 61 `lang="ko"`
glosses) · `check_classes` PASS · `punct_quotes` PASS · `legacy_firewall` PASS (every soft token
cleared by `raws/`) · `audit_marks` OK on ch002/ch004/ch005 · `repeat_check` PASS ×2 plus the
documented ch004 REVIEW refrain · `style_audit` PASS · stylelint 0 errors · `sync_styles` PASS ·
`install_fonts --verify` PASS · `workspace_audit --assets` → `structural_errors: []` (manifest 44 ·
spine 11 · navPoints 10 · nav li 13 · images 9 · cards 6/6/35 · metrics-band ×3 triaged as before).

**Ship.** `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub` rebuilt: **47 entries ·
2,032,683 B · sha256 `d4c044f3d069bfeb05c5065747509cff4cf2a8e21d811538a419b6779148cd08`**; mimetype
STORED first, zip test clean, tree↔archive name diff empty and every payload identical; in-archive
asserts pass (9 image items, the three plates present in the packed chapter bytes, `id-06` in card
and introductions, `#chapters-stamp` on the cover). Committed and pushed to the session branch with
the remote HEAD verified.

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
