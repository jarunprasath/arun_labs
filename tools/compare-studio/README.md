# Compare Studio

A browser-based file comparison tool for text, folders, spreadsheets and binaries. It is a single HTML file: open `index.html` in any modern browser. Files are read locally in the browser and are never uploaded.

## Modes

| Mode | What it compares | Highlights |
|---|---|---|
| **Text** | Source code, logs, configs, any text file | Side-by-side view, character-level highlights inside changed lines, similar lines paired across a block, ignore whitespace / case, collapse identical lines, jump between differences (F7 / F8 or Alt+↓ / Alt+↑), copy a block left ↔ right, edit either side, copy a unified diff |
| **Folders** | Two folder trees | Matches files by relative path, compares contents byte by byte, filters for different / left only / right only / identical; click a pair to open it in the right mode |
| **Tables** | CSV, TSV and Excel (`.xlsx`, `.xls`, `.ods`) | Matches rows by a key column (e.g. requirement ID) or by row number, aligns columns by header name, shows old → new per cell, flags added / removed rows and columns, optional numeric comparison by value |
| **Hex** | Any binary file | 16 bytes per row with ASCII, highlights differing and extra bytes, jump to next / previous difference or to an offset |

## How it works

- The text diff uses the Myers O(ND) algorithm with linear-space bisection, the same family of algorithm used by `git diff`. Inside a changed block, removed and added lines are paired by token similarity so each line sits next to its real counterpart.
- Folder comparison checks file size first and then compares contents, so timestamps alone never mark a file as different.
- Hex comparison is position based (byte *n* on the left against byte *n* on the right); it does not re-align inserted bytes.
- Excel files are read with [SheetJS](https://sheetjs.com/) 0.18.5, loaded from cdnjs only when an Excel file is opened. Everything else has no dependencies.

## Limits

- Text files up to about 30 MB; binary files up to about 200 MB (the browser holds both in memory).
- Very different large files fall back to marking whole regions as changed after a few seconds, to keep the page responsive.

## Licence and credits

Written from scratch by Arun Prasath J. It is an independent tool inspired by the features of desktop comparison tools such as Beyond Compare; it contains no code or assets from them.
