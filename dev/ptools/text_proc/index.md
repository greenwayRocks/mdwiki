## _ Plaintext data in Linux _

> _ Learn how to _process and filter text data_ in Bash + Zsh shell

### _ Linux User Roles _

* DevOps
* Software
* Operations
* Data

### _ When ? _

* Searching logs
* Comparing files for latest changes
* Transform data
* Tweak output

### _ Learning Outcomes _

* Finding files, reading files, searching for text
* Basic text handling with _cut, sort, transform, merge_
* Advanced text processing with _sed and awk_
* Reading + Writing to files using _shell scripting_

### _ Finding things .. find v\s locate .. _

Find searches directories in _real time_.
```
find ~ -type f -name *.log
find / -type d -name www
find / -type d -perm 777
find / -type d -empty

find . -type f -name '.*'
find /var -user apache
find /var -group wheel

find /var/log -type f -amin -60 # last hour access
find /var/log -type f -cmin -10 # changed in last 10 minutes

find /var/log -type f -size +1024M
```

Locate searches its _internal database_ therefore **quicker**.
However, needs to keep its database updated!
**TIP** Daily cron job can run "$ sudo updatedb"

### _ Reading files now ? Cat it! _

_Cat_ can combine multiple files into one.
It can also read files easy.

For _paging view_, use **more** or **less**.

```bash
cat -b weekdays1 weekdays2 > weekdays
```

For getting _first or last_ few lines of the file, use **head** and **tail**.

To follow a updating file:
```bash
tail -f /var/log/pacman.log
tail -v /var/log/messages /var/log/wtmp
```

### _ Pattern matching through every line? Grep it! _

grep "pattern" text-file

Learn regex for advanced usage. Or use options.

```
grep -i -w -n "shut*down" /var/log/messages
# i = case-insensitive
# w = whole word
# n = line numbers
# v = invert (not-match)
# -A 2 -B 3 = lines after/before matching text
# c = count
# R = recursively in files
# l = just the file names of those matched
```

**Follow:**
  [Basic Text Handling](basics.md)
_-- covers_ **diff, wc, nl, tr, sort, uniq, cut, paste, join**
  
