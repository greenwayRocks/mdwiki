### _ Bash Files _

* ,bash_profile is executed at login so that it configures our shell before \
getting the _initial prompt_ of our interpreter.

```bash
if [ -f ~/.bashrc ]; then
    . .~/.bashrc # or source
fi
```
Or nowadays,
```bash
[[ -f ~/.bashrc ]] && source ~/.bashrc
```

For user-specific environment ( functions, aliases), use .bashrc well.

For user-specific **executables**, use PATH well inside your shell.
Like PATH variables, there are **important ones** out there and create your own to store your _IP address_ in fact!
```
PATH=$PATH:$HOME/bin
export PATH
```

Consider updating PATH such that _this script is executable directly in your shell_.
??

**QUESTION** How do I globally create shell configuration for _all users_ in my system?
Well, I could **add this to start with users' bashrc**.

```bash
# Source global definitons

if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi
```

Then goes all the user specific ones once the globals are there!

### _ Where does this start to show? _

```bash
env # shows all environment variables currently available in my shell.
set # all settings for the shell, perhaps!
```

I can:
```bash
env | grep PORT
```
-- to check if PORT is set for my application --

If it's not,
* add it to ".bashrc" locally OR "/etc/bashrc" globally for all my users.
* Then I gotta _source it_ or I type it in my current shell.

----

**WHY?** Because the current shell exists already. You either gotta type and let it interpret or rather source it!

**Place here**: /etc/bashrc -> Source it in $HOME/.bashrc -> Source .bashrc in .bash_profile ?

----

### _ More bash files == History == _

.bash_history stores shell history.

```bash
env | grep HISTCONTROL

export HISTCONTROL=ignoredups:ignorespace
```

There is also a ".bash_logout" that executes commands after a shell session exits.
I can **reset** my shell environment or **always execute sth** when my session ends.
It's a TRAP. Learn **how TRAP works** for the same thing.
