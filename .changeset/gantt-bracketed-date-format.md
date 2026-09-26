---
'mermaid': patch
---

fix(gantt): accept square brackets around a `dateFormat`

`dateFormat [[YYYY-MM-DD]]` now parses tasks dated `[[2020-05-29]]` instead of throwing
`Invalid date`. dayjs uses square brackets to escape literal text and its tokenizer cannot
express a literal `[`, so wrapping a date in brackets — handy for wiki-style links — was
impossible to write. Formats dayjs already parses keep their meaning, so `YYYY-MM-DD[T]HH:mm`
still escapes the `T`.
