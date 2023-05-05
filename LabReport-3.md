# Lab Report 3 - `grep` Command-line Options

## How to use `grep`

**Formatting:** `grep <Options> <Pattern> <FileName>`

`grep` is used to print out lines within a designated file that match the given pattern.

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
```
[cs15lsp23qx@ieng6-203]:technical:238$ grep -i "IV" government/Media/5_Legal_Groups.txt
Five independent Salt Lake organizations that provide legal
last Wednesday their board members were given a tour of the
Community Legal Center hosted by staff members of the five
building and not paying rent times five will save the non-profit
desperate for a protective order, for example, have to run all over
explained, and so it was important who would be living there. I
Stewart Ralphs, the executive director of the Legal Aid Society,
cost received so far. There still needed to be furnishings and
```

## Option 2 - `-v`

This command-line option inverts the matching of the lines to print out non-matching lines. This could be useful in wanting to find lines in a file without a certain word or pattern.

[Citation}(https://man7.org/linux/man-pages/man1/grep.1.html)

**Example 1:**
```
[cs15lsp23qx@ieng6-203]:technical:240$ grep -v "l" government/Media/5_Legal_Groups.txt





BY EDWARD MCDONOUGH
parking, something that's hard to find downtown and which has been
agencies about $375,000 each year. My assistant, Charity
town trying to find the right agency.
become one of the major supporters of the project.



```

**Example 2:**
```
[cs15lsp23qx@ieng6-203]:technical:252$ grep -v "a" government/Media/Disaster_center.txt





Published July 11, 2002
process."


in relief in the form of emergency housing.
questions.
this trying time."



```

## Option 3 - `-w`

This command-line option finds lines that have only whole words matching the pattern. The substring in the line will only match if there is a non-word constituent character infront and behind it. Word-constituent characters are letters, digits, and the underscore. This could be useful in finding lines in a file the have a specific stand-alone word in it. 

[Citation}(https://man7.org/linux/man-pages/man1/grep.1.html)

**Example 1:**
```
[cs15lsp23qx@ieng6-203]:technical:257$ grep -w "them" government/Media/Disaster_center.txt
to receive aid from them, too.
registered them for Red Cross services. That's incorrect, Andreas
```

**Example 2:**
```
[cs15lsp23qx@ieng6-203]:technical:256$ grep -w "s" government/Media/Disaster_center.txt
residents and business owners impacted by last week's floods.
registered them for Red Cross services. That's incorrect, Andreas
```

## Option 3 - `-c`

This command-line option finds the lines in the given file with the pattern in them and prints the number of lines matching. This is useful if you only need to know the amount of lines that match the pattern but you do not want to count the lines printed manually.

[Citation}(https://man7.org/linux/man-pages/man1/grep.1.html)

**Example 1:**
``` 
[cs15lsp23qx@ieng6-203]:technical:264$ grep -c "FEMA information officer Bill Lindsay announced Wednesday that" government/Media/Disaster_center.txt
1
```

**Example 2:**
```
[cs15lsp23qx@ieng6-203]:technical:268$ grep -c "a" 911report/chapter-1.txt 
350
```





