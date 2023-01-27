## Linux tr Command

> Translate or delete characters.

### _ Some translations _

```bash
$ file=/tmp/data
$ cat $file | tr \[:lower:\] \[:upper:\]

$ | tr \\t \,
# tabs to commas

$ | tr -s \\n i
```

#### **tr SETS** --
group of characters!
e.g. [:upper:] [:lower:]
-- remember to escape sets!

[*] Change tabs to csv?
[*] Remove blank lines
