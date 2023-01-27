### _ Command Types _

    Files (executables, scripts)
    Builtins (commands compiled as part of Bash)
    Keywords (reserved syntatic words)
    
    == Your own commands on the fly? ==
    
    Functions (user definable, compound command)
    Aliases (user definable, simple command substitution)
    
**Write your own builtins as modules?**
```bash
$ type -a \
> ls cd while genpass

# genpass() comes with Ubuntu
genpass() {
  tr -dc 'a-zA-Z0-9_#@.-' < /dev/urandom | head -c ${1:-14};
  echo
}
```
Init scripts almost always have a library of bash functions to help themselves.

### _ Getting Help _

    % type - determine type of command, list contents of aliases & functions.
    % help - usage for bash builtins & keywords.
    % apropos - search man pages.
    % man - system manual.
    % info - advanced manual for GNU programs.
    
**Keywords**: word(chars), list(sequences of commands/pipelines), name(make vars), ..
________  parameters(entity that stores values e.g. vars)
There are also **positional & special parameters.**

Everytime I run a command in bash, --
it **going to give a return status that indicates** success or failure.
0 (success) and Non-zero (failure) return statuses.

Let's download the slides here and refer to it.
I'm gonna learn on the fly.

### _ Compound commands _

**1: Iteration**
Continously loop over a list of commands delineated by keywords **do and done**.
e.g. while, until, for, select.

**2: Conditionals**
Execute list of commands only if certain conditions are met.
e.g. if, case.

**3: Command Groups**
Grouped list of commands.
Sharing any external redirections, return value is of that list.
e.g. (list) {list; }

```bash
## Iterate based on an external resource --

$ while list1; do list2; done
# while list1 succeeds, execute list2 and repeat until list1 fails.

$ until list1; do list2; done
# until list1 succeeds, execute list2 and repeat until list1 succeeds.

$ while read # ...
# construct for processing lines of text.

$ while read var1 var2
do
  echo $var2 $var1
done

$ echo "The last variable specified for read, grabs whole rest of line."
# if expecting more words (inputs), they get dumped in there!

# to make sure i don't accidentally grab extra inputs, I add a junk variable that I don't use.
# e.g. while read var1 var2 yadayada

## --
```

```bash
## iterate based on command-line args

$ for name in words; do list; done
# assign each time name = (next word) in words, and execute list until all words are exhausted.

$ for item in one two "three four five"
do
  echo "_-_- $item _-_-"
done

# The C-style for loop
$ for (( expr1; expr2; expr3 )); do list; done

$ for (( i=0; i<5; i++ ))
do
  echo $i
done

# Hatkey select loop
## typically for user input (little menu system of choices)
select choice in one two "three four"
do
  echo "$REPLY: $choice"
done
## reply is assigned the index no. of the selection.

```
**for loop can easily iterate over all files in a dir, using wildcards.**
