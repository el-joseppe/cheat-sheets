# Git

# config

- set global user.name: `git config --global user.name "John Doe"`
- set global user.mail: `git config --global user.email "me@example.com"`
- set global credential.helper: `git config --global credential.helper [cache, store, osxkeychain]`
    - `git config --global credential.helper store` → git saves credential in plaintext to `~/.git-credentials`
    - see [Link](https://techexpertise.medium.com/storing-git-credentials-with-git-credential-helper-33d22a6b5ce7)
- show global config: `git config --global -l`

# use
- create a readme-file: `touch README.md`
- init local repository: `git init`
- add something to index: `git add README.md`
- commit something: `git commit -m "first commit"`
- add remote repo: `git remote add origin https://<url>/<user>/repo.git`
- change remote repo: `git remote set-url origin https://<url>/<user>/repo.git``
- push to specific branch: `git push -u origin master`
- show status: `git status`
- show diff for staged changes: `git diff --staged`
- remove file only from index: `git rm --cached some.file`
- revert changes to file: `git restore some.file`
- pull and rebase: `git pull --rebase`

# advanced
- howto rebase feature-branch with master?
- delete local branches that got deleted remote: `git branch --merged | egrep -v "<exclude-1>|<exclude-2>|..." | xargs git branch -d`
    - see [Link](https://dillionmegida.com/p/delete-outdated-branches/)