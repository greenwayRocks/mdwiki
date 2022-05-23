### _ Unix Library 101 _

** NOTE ** - Stuffs that I `want here` are `there in youtube projects and book projects.
** e.g. ** - Luke smith's content.

>  Need a `ssh-session` connection for some script work:

```bash
    eval $(ssh-agent)
    ssh-add ~user/.ssh/id_rsa

    # do stuff e.g. git push using ssh

    eval $(ssh-agent -k)
```
> Tmux `zoom-in` & `zoom-out` scripts:

```bash
    #!/bin/bash

    # Zoom in the current pane ONLY if it is not currently zoomed.
    tmux list-panes -F '#F' | grep -q Z || tmux resize-pane -Z

    # Zoom out the current pane ONLY if it is not currently zoomed.
    tmux list-panes -F '#F' | grep -q Z && tmux resize-pane -Z
```

> Tmux `workflow automation` script:

```bash
  #!/bin/bash

  # Phase One : Project Creation -- if necessary --
  # Phase Two : TMUX automation

  session="dev"
  tmux has-session -t "$session" 2> /dev/null
   
  if [ $? != 0 ] ; then
    # Set up my session
   
    ## Session 'dev' creation 
    tmux new-session -d
    tmux rename "$session"

    # 1. "media-browser" window
    tmux renamew 'media'
    tmux send-keys -t 'media' 'cd /var/shared/ws && ranger' C-m

    # 2. "src" window
    tmux new-window -n 'src' -c /var/shared/ws/src -d
    tmux split-window -l 10 -t 2. -c /var/shared/ws/src -d
    tmux send-keys -t 'src.1' 'vi .' C-m
    # tmux list-panes -F '#F' | grep -q Z || tmux resize-pane -Z

    # 3. "wiki" window
    tmux new-window -n 'wiki' -c /var/shared/wiki -d
    tmux send-keys -t 'wiki' 'vi index.md' C-m

  fi

  tmux attach -t $session

  # Phase Three : There's no phase three, well done!
```

> Capitalize `1st letter` in a string ?

```bash
  foo="bar"
  echo "$(tr '[:lower:]' '[:upper:]' <<< ${foo:0:1})${foo:1}"
  #returns 'Bar'
```

> **More to go :v**
