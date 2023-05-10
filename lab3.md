# CS15L Lab Report 3
<br />
## Grep --include
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
Here we change the search term to be `"money"` so grep finds all the files that have lines that include "money". We also changed the included file names by including `b*.*` and `c*.*`.

<br />

## Grep -c
Another interesting use of grep can be to find the number of times a certain pattern appears in a file:
```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -c "example" technical/*/* | head -n 5
grep: technical/government/About_LSC: technical/911report/chapter-1.txt:1
Is a directorytechnical/911report/chapter-10.txt:0
technical/911report/chapter-11.txt:9

technical/911report/chapter-12.txt:6
technical/911report/chapter-13.1.txt:6
```
<br />
The `-c` after the `grep` counts the number of times `"example"` appears in a file matching the pattern `technical/*/*` and displays the count to the right of the file. We again use `| head -n 5` to only print the first five examples.

```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -c "date" technical/*/* | head -n 5
greptechnical/911report/chapter-1.txt:8
:technical/911report/chapter-10.txt:1
 technical/911report/chapter-11.txt:4
technical/government/About_LSCtechnical/911report/chapter-12.txt:8
: technical/911report/chapter-13.1.txt:8
Is a directory
```

We can change the `""` after `-c` to any pattern we'd like to search for and we see the count of the pattern in the file printed to the right of the colon after the filename.
