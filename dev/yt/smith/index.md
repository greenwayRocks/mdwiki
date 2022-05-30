## _ Luke you gotta teach me somethings _

* e.g. `mounting devices script`

### _ Windows Manager Swallows  _

    Without the `patch for dwm` ;; I would:
    
    $ setsid -f sxiv pix.jpeg
    
    to fork process in a new session.

> I remember using `$ nohup sxiv pix.jpeg &` to background a process first,
and then kill the terminal.

> Yet, it swallows and it's great!

### _ Webcamming and screencasting _

> Webcamming made easy with `$ mpv /dev/video0` --
A scratchpad terminal with swallowing feature could `toggle` a webcam window --
-- let it `float` or `tile` with the others --

> Or I could script it in `one line`:

```bash
#!/bin/bash
# camtoggle v1.0

pkill -f /dev/video || mpv --geometry=-0-0 --autofit=30% /dev/video0
```

### _ Automatic Colorschemes _

> **pywal** is great. Install with `$ p -S python-pywal`

Use it like:
```bash
$ wal -i img.jpg
```

I can use equivalent wallpaper and colorscheme for a selected random image every time in .xinitrc.
To make a range shortcut to change colorscheme ... I add in rc.conf ::
```
    map bw shell wal -i %s
```
to make "bw" the keybinding

### _ Bash vs Posix-shell scripts _

Bash has these enormous features of **process substitution** e.g.
```bash
diff <(pacman -Q) <(pacman -Qn)

[[ "$EDITOR" == "nvim" ]] && echo "Neovim rules" # bash compliant
[ "$EDITOR" = "nvim ] && echo "Neovim rules" # posix-shell compliant

shellcheck script_name # to check if it's POSIX compliant
```

WHen necessary, use process subsitution effectively to create your bash shell specific scripts.
You could even link `/bin/sh` to dash or ksh or some POSIX compliant shell and work your way out!
Use shellcheck sometimes, you'll be fine I swear.

### _ Minimalism ? _
Use **grep** for grepping without a **cat** prepended and piped.
Test efficiency of _awk, sed, grep, cat, head, tail_ in the command line.

```bash
time ( for x in $(seq 1000); do
sed 11q /etc/passwd
done )
```

Time out things to see their efficiency yourself.
**sed 11q** is _stupid_. Use **head** instead, well time it out!

**TIP:** Grep with awk? Go `awk /dexter/ /etc/passwd`
