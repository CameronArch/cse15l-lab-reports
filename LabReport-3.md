# Lab Report 3 - `grep` Command-line Options

## How to use `grep`

**Formatting:** `grep <Options> <Pattern> <FileName>`

`grep` is used to print out lines within designated file that match the given pattern.

## Option 1 - `-i`

This command-line option ignores the case of the letters, so the pattern given will match with the same characters regardless if their cases match or not. This could be useful when needing to find lines that match a pattern but you are unsure if the pattern in the lines have capital letters or not.

[Citation}(https://man7.org/linux/man-pages/man1/grep.1.html)

**Example 1:**                                                                                                          
```
[cs15lsp23qx@ieng6-203]:technical:236$ grep -i "iv" government/Media/5_Legal_Groups.txt 
Five independent Salt Lake organizations that provide legal
last Wednesday their board members were given a tour of the
Community Legal Center hosted by staff members of the five
building and not paying rent times five will save the non-profit
desperate for a protective order, for example, have to run all over
explained, and so it was important who would be living there. I
Stewart Ralphs, the executive director of the Legal Aid Society,
cost received so far. There still needed to be furnishings and
```

**Example 2:**                                                                           
