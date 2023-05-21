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
I use the `|` as a pipe here to also include the `head -n 5` to only print the first five matches. There were many matches so I wouldn't be able to fit all of them on this screen if I hadn't included the pipe. The left side of the pipe is the grep command and a few options; the `-r` recursively searches through the `technical/*` to find matches. The `*` after /technical is a pattern so the grep command will look through all possible paths that might match the `*` depth. `"pattern"` is the search term we want to match all of the lines too so no lines without "pattern" are printed. Finally, the `include=` dictate which type of files should be included in the search. I found this command by asking GPT-4 "Come up with 4 interesting variations of using the grep (bash command)" and taking the most interesting command I found.
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
Here we change the search term to be `"money"` so grep finds all the files that have lines that include "money". We also changed the included file names by including `b*.*` and `c*.*`. This command is from the same source as the previous, I simply altered a few of the values because ChatGPT explained what each value changes so I knew what to change to create the result I wanted.

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
The `-c` after the `grep` counts the number of times `"example"` appears in a file matching the pattern `technical/*/*` and displays the count to the right of the file. We again use `| head -n 5` to only print the first five examples. Again, I found this command by asking GPT-4 "Come up with 4 interesting variations of using the grep (bash command)" and taking the second most interesting command I found.

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

We can change the `"_what we want to search for_"` after `-c` to any pattern we'd like to search for and we see the count of the pattern in the file printed to the right of the colon after the filename. I changed the value of the search from the explanantion ChatGPT gave.

## Grep -B -A
We can use grep to show us the context of the line we are searching for:
```
$ grep -B 1 -A 1 "important" technical/911report/chapter-11.txt | head -n 5
                sufficiently on the minds of the public to warrant asking a question about it in a
                major national survey. Bin Ladin, al Qaeda, or even terrorism was not an important
                topic in the 2000 presidential campaign. Congress and the media called little
--
```
Here we use `-B` after `grep` to denote how many lines before matches of "important" are found in `technical/911report/chapter-11.txt`.
We then use `-A` to signify how many lines after we'd like to include which for both `-A` and `-B` we set the amount of lines to 1. I again used GPT-4 to come up with a new command by asking it "Come up with 4 interesting variations of using the grep (bash command)" and this time I regenerated the response because I didn't find the rest of the four commands interesting.

```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -B 2 -A 1 "soon" technical/911report/chapter-11.txt | he
ad -n 6
            If the government's leaders understood the gravity of the threat they faced and
                understood at the same time that their policies to eliminate it were not likely to
                succeed any time soon, then history's judgment will be harsh. Did they understand
                the gravity of the threat?
--
                Ladin was a danger. But given the character and pace of their policy efforts, we do
```

Here we change the word we are searching for to "soon" and change the `-B` quantity to `2`. I also altered the `head -n` to `6` to includ e more lines. The command is from the same source as the previous one.

## grep -v
We can also use grep to search for lines in files that do **not** match a certain pattern:
```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -v "secret" technical/911report/chapter-11.txt | head -n
 6



            FORESIGHT-AND HINDSIGHT
            In composing this narrative, we have tried to remember that we write with the benefit
                and the handicap of hindsight. Hindsight can sometimes see the past clearly-with
```
The `-v` after grep states which patterns we want exclude from our search. I exclude the term secret and again use the `head -n` command to only print the first 6 lines. We can see the difference by using "composing" as our pattern search which will exclude the fifth line from the search. I found this last command by asking GPT-4 "Come up with 4 interesting variations of using the grep (bash command)" and taking the most interesting command I found. This command was from the regenerated response.

```
mboyk@DESKTOP-VFONE4K MINGW64 ~/CSE15L/docsearch-main
$ grep -v "composing" technical/911report/chapter-11.txt | head
 -n 6



            FORESIGHT-AND HINDSIGHT
                and the handicap of hindsight. Hindsight can sometimes see the past clearly-with
                20/20 vision. But the path of what happened is so brightly lit that it places
```

No we can see a different line appears in our print rather than the line that began with "In composing...". This occurs because we still read the first 6 lines of the text; however, we choose different patterns to exclude. This command is the same as the previous with altered values.
