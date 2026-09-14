# extracted/ — unpacked snapshot of the delivered archive

Created in cycle 2 at the reader's request: "extract all the files from the given epub for future
use." This folder holds the **complete unpacked contents of the delivered v1 package**
(`Dominating_South_Korea_Starting_with_a_Golden_Trait.epub` as shipped at sha256 `acc78690…`,
43 entries), extracted entry for entry, `mimetype` included.

| Fact | Value |
|---|---|
| Source archive | v1 ship, 43 entries, 1,495,148 B, sha256 `acc7869055cfe5092595d0658a423dc2a14885f03b396c7b273f1d2d18178af7` |
| Parity at extraction | archive == `extracted/` == `work_epub/` on all 43 payloads (verified by sha256) |
| Role | read-only reference snapshot of what v1 shipped — cover, front matter, chapters, styles, fonts, images exactly as delivered |
| Not | a second live tree. Gates, the packer and every edit read `work_epub/` only |

When the root deliverable is rebuilt (cycle 2 onward: 47 entries, sha256 `d4c044f3…`), this folder is
**not** refreshed — it keeps the v1 contents so any future cycle can diff what changed against what
the reader actually received. To unpack a newer archive instead, extract it into a new folder named
for its ship (e.g. `extracted-v3/`) and record it in worklog §8; never overwrite an existing
snapshot.
