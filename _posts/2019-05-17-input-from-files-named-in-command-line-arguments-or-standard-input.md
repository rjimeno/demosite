---
title:  Input from files named in command line arguments or standard input.
date: 2019-05-30 12:00
image: http://placehold.it/900x300
lead: "We pay a huge price for the underlying complexity of dynamic code 
running on a server for every request - a price we could avoid paying 
entirely when this kind of complexity is not needed."
subtitle: create a ultra fast, secure blog that is easy to maintain and easy to scale
category: Python
---

Earlier today, I finished writing a script that required two arguments being passed on the command line. The script was, in essence, a *reducer* or some form of filter that would summarize information. Its input would be taken exclusively from standard input.

Once the script was done, I realized the script would be more useful and comfortable to handle if input could be read from files with names provided in the command line. Anything after the first pair of arguments would be assumed to be the name of a file and an open() operation would be attempted immediately followed by the reading of all of their contents. Last but not least, an attempt to read from actual stdin until no more input is available.

Since I was in no mood to carefully change significant parts of my code, I searched the Internet for Python libraries to help me and found `fileinput` which provided me with functionality similar to the one I usually enjoy from the diamond operator when programming Perl.

An excerpt of my code using it follows:

```python
import fileinput

for line in fileinput.input(argv[3:]):
        tmp = line.rstrip().split(',')
        if 10 != len(tmp):
            continue  # That line was probably malformed.
```