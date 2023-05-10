# CS15L Lab Report 3
<br />
## Grep command
<br />
An interesting use of a grep command could be to list out the contents of a file who's filename begins with `a` or `s`.
```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -r "pattern" --include='a*.*' --include='s*.*' technical/* |  head -n 5
technical/biomed/ar118.txt:          patterns in populations of females with multiple
technical/biomed/ar118.txt:          X-chromosome inactivation patterns. The AR gene contains
technical/biomed/ar118.txt:          We examined X-chromosome inactivation patterns in
technical/biomed/ar118.txt:          patterns in peripheral blood mononuclear cells, and the
technical/biomed/ar118.txt:          patterns between buccal mucosa (an ectodermally derived
```
<br />
I use the `|` as a pipe here to also include the `head -n 5` to only print the first five matches. There were many matches so I wouldn't be able to fit all of them on this screen if I hadn't included the pipe. The left side of the pipe is the grep command and a few options; the `-r` recursively searches through the `technical/*` to find matches. The `*` after /technical is a pattern so the grep command will look through all possible paths that might match the `*` depth. `"pattern"` is the search term we want to match all of the lines too so no lines without "pattern" are printed. Finally, the `include=` dictate which type of files should be included in the search.
<br />
```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -r "money" --include='b*.*' --include='c*.*' technical/*
 |  head -n 5
technical/911report/chapter-12.txt:                where a little money might have a large effect. Defenses also complicate the plans
technical/911report/chapter-12.txt:                Moussaoui as a participant and Ramzi Binalshibh's transfer of money to him. The U.S.
technical/911report/chapter-12.txt:                    authority and contacts to assemble needed people, money, and materials;
technical/911report/chapter-12.txt:                    money, and transport resources (like explosives) where they need to go;
technical/911report/chapter-12.txt:                concern. Millions of families, especially those with little money, send their
```
<br />

