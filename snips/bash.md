### _ Bash snippets that save my day -- _ 

> Need a ssh-session connected to do sth out there ?

```bash
eval $(ssh-agent)
ssh-add ~user/.ssh/id_rsa

# do stuff e.g. git push using ssh

eval $(ssh-agent -k)
```

> More to go :v
