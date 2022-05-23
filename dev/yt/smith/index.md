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

