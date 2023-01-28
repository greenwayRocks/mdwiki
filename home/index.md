```bash
#!/bin/bash

# Wiki update script --

# syntax: wiki-update "COMMIT message"

if [[ -z "$1" ]]; then
  echo "Pass a commit message!"
  exit 1
fi

wiki_dir=/var/shared/wiki

# SSH to github
eval $(ssh-agent)
ssh-add ~mario/.ssh/id_rsa

cd $wiki_dir || exit 1

echo "-- Updating files to github ... "
git add .

echo "-- Commiting your message ... "
git commit -m "$1"

echo "Finally, pushing! ... "
git push -u origin gh-pages && echo "-- Done, well scripted! --"

eval $(ssh-agent -k)
```
