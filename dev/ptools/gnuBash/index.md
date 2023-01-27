## GNU Bash Advanced Usage

> Opportunities to use Bash everyday? Learn this.

Bash is the **shell that you use everyday anyways**!
    * Administrative tasks
    * DevOps

Not about the **Unix Powertools**, but about **the shell that glues them together!**
Now let's start this.

----

**Surf through these:**

  [Basics](basics.md)

### _ Tests _

Test things and branch into different possibilities.
**Make sure everything's sane before we proceed.**

Parts that you match with regexs, get pulled out into an array.
**Back references for later processing?**

```bash
# the old way --
$ [ expression ] 
$ test expression

# now -- word splitting is now performed
$ [[ expresion ]]
$ [[ "abc" == ?bc ]]

# For == & != ; RHS is treated as a string if quoted!
# else, it's a pattern - pattern matching as in globbing - not regex perhaps.

# refs ::

[[ -n string ]] [[ -z string ]] # non-empty and empty
[[ string1 == string2 ]] [[ string1 != string2 ]]
[[ string =~ regex ]]

[[ -e file ]]
[[ -f file ]]
[[ -d file ]]

[[ -t fd ]]
# check if input we're working with, is coming from a terminal.
# if it's a script that's running, or an interpreter session.
# pretty important if builing a MENU SYSTEM.

$ echo fd = 0:stdin, 1:stdout, 2:stderr

$ [[ -t 0 ]]
# return 0 because taking input from KEYBOARD.

$ [[ -t 0 ]] < /etc/os-release
# fails.
```

### _ Conditionals _

