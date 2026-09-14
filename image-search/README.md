# image-search/ — image workbench

Per the reader's directive this folder stores the image-search files. It is where source material
for character portraits, wardrobe plates and cover art lands, and where it stays.

| Path | Contents |
|---|---|
| `search-NNN-*.jpg/png` | files returned by web image search, kept under a chapter-scoped name: `ch007-search-01-jessica.jpg` |
| `gen_*.png` | commissioned/generated artwork before it is coded (e.g. `cover_gen_original.png`) |
| `_scratch/` | throwaway crops and contact sheets (git-ignored) |

## Rules carried over from the inherited playbook

1. **Identity first, plate second.** A plate is only made for a person whose identity source
   exists: this folder (reader-supplied or reader-searched), else nothing. Fabricating a likeness
   for a real person is a breach, not a shortcut.
2. **Real people are photographed, fictional figures are illustrated.** An illustration is
   labelled as an illustration on the card that carries it; a photograph is never invented.
3. **Coding spec before install.** Portrait cards: 4:5 center-crop, 736×920, JPEG q85 optimize.
   Wardrobe plates: 4:5 center-crop, 1120×1400, JPEG q85. Cover background: 1200×1800, JPEG q85
   progressive. Install only the coded file into `work_epub/OEBPS/images/`; the raw source stays here.
4. **Inspect what got installed**, not what got generated: open the tree file and check crop,
   edge artifacts, aspect and legibility under the text overlay.
5. **Register every install**: `<item id="id-NN">` in `content.opf` (numeric image ids climb by
   one), manifest-before-spine order, and the byte size recorded in the worklog entry.
6. Nothing in this folder is printed into the book — no provenance line, no search URL.
