# extracted-v10/ — unpacked snapshot of the cycle-10 delivered archive

Created 2026-09-15 in the workspace-restore cycle at the reader's request ("Extract all the files
from the given epub for future use."), following the standing convention set by `extracted/`:
each delivered archive keeps its complete unpacked contents in a folder named for its ship, and an
existing snapshot is never overwritten. `extracted/` (v1, 43 entries, sha256 `acc78690…`) stays
untouched.

| Fact | Value |
|---|---|
| Source archive | cycle-10 ship of `Dominating_South_Korea_Starting_with_a_Golden_Trait.epub`, 91 entries, 5,177,796 B, sha256 `715f6bea294a058440b775e434a89844cc5f058a551442aa9001b68ecaca1012` |
| Contents | `mimetype` + `META-INF/container.xml` + `OEBPS/` — `content.opf`, `toc.ncx`, 6 front-matter pages + chapters `ch001`–`ch031` in `text/`, 27 images in `images/` (id-01…id-27), 20 WOFF faces in `fonts/`, 3 stylesheets in `styles/` |
| Parity at extraction | archive == `extracted-v10/` == `work_epub/` on all 91 payloads, verified by sha256 per entry |
| Ship state | 31 chapters · 88 manifest items · 37 spine entries · 36 NCX navPoints · 39 nav list items · 27 images · 20 fonts · 17 character cards · 17 introduction cards · 54 glossary cards · stamps `Chapters 1–31` |
| Role | read-only reference snapshot of what cycle 10 shipped — the complete 31-chapter package exactly as delivered |
| Not | a second live tree. Gates, the packer and every edit read `work_epub/` only |

To unpack a newer archive, create the next ship's folder (e.g. `extracted-v11/`) and record the
extraction in worklog §8; never refresh or overwrite an existing snapshot.
