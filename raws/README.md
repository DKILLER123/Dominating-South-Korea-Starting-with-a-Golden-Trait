# raws/ — source custody

Every raw the reader pastes is saved here **first**, before recon, drafting or image work, and
never edited afterwards.

| Convention | Rule |
|---|---|
| Chapter raw | `chNNN_raw.txt` — three digits, matching `work_epub/OEBPS/text/chNNN.xhtml` |
| Front-matter raw | named for its page: `Synopsis_raw.txt`, `Characters_raw.txt`, `Glossary_raw.txt` … |
| Re-pasted raw | keep the original, save the new one as `chNNN_raw_v2.txt`, then diff. Never overwrite. |
| Content | verbatim, including ads, OCR junk, stray numerals and glyph garbage. Debris is dropped only in the draft. |
| Language | whatever the reader supplies (this book's raw is Simplified Chinese) |

`workspace_audit.py` hashes every file here into `reports/source_inventory.tsv`, and
`legacy_firewall.py` uses this folder as the provenance corpus: a real-person name is cleared
only when it is named in one of these files. Do not delete a raw to make a report quieter, and do
not invent a raw for a chapter that was never supplied.
