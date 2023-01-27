## Number your lines

But, by default it doesn't number empty(blank) lines.

```bash
$ file=/tmp/data
$ nl $file

$ nl -b a $file
# now the empty lines are numbered.

$ nl -v 10 -b a $file
# line numbering to start at 10
```
