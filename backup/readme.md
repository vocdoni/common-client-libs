## Translation guide

First, set up the weblate remote repo:
`git remote add weblate https://hosted.weblate.org/git/vocdoni/backup-questions/`


The translation flow is an iterative loop that looks like:
- Lock the weblate repository
- `git checkout i18n`
- `git pull weblate i18n`   (update our local repo)
- `git push origin i18n`    (update the GitHub branch)
- `git checkout main`       (check out the latest code)
- `git merge i18n`          (integrate the latest translations)
- `git push origin main`    (update the GitHub branch)
- `git checkout i18n`
- `git merge main`          (integrate the latest code into i18n)
- Manually update new translation keys 
<!-- TODO use lang-parse script to parse translation keys -->
- `git add backup/i18n/*`   (stage the language files for commit)
- `git commit -m "Updated strings"`
- `git push origin i18n`    (push the new strings for Weblate)
- `git checkout main`
- Unlock the Weblate repository