---
layout: page
title: Git
permalink: /notes/command-library/git/
---

- View the changes you made to dtl.py in the current directory.
```bash
git diff dtl.py
git diff HEAD~ HEAD	# View all changes of the most recent commit
```

- Check the changes you've made after last update.
```bash
git status
```

- Stage all changes made to the files in the data folder.
```bash
git add data/*
```

- Stage all the changes
```bash
git add -A
git add --all
```

- Stage deleted files for commit
```bash
git add -u
git rm $(git ls-files --deleted)
git status | grep 'deleted:' | cut -d':' -f2 | xargs -t -I {} git add -u "{}"
```

- With remote repository specified, download the latest objects and refs from the remote.
```bash
git fetch
```

- Check the history of commits from all the developers.
```bash
git log
```

- Download the latest changes to the local repository.
```bash
git pull
```

- On your local, create a new branch called "my-branch" for your future development.
```bash
git checkout -b my-branch
```

- Merge changes in master branch to feature branch.
```bash
git checkout feature-branch
git merge master

git merge -s ours master	# To always keep the changes from the feature-branch
```

- Remove dtl.py from the added files.
```bash
git reset HEAD dtl.py	# remove last commit, keep the changes

git reset --hard HEAD^	# remove last commit, discard changes
```

- Commit the changes you have added with the label "Test program and raw data".
```bash
git commit -m "Test program and raw data"
```

- Push the committed changes to remote.
```bash
git push
git push origin <branch-name>
```

- Push a new local branch to a remote Git repository
```bash
git push -u origin <feature-branch-name>
```

- Check all the available tags of the project.
```bash
git tags
```

- Check the current tag of the project.
```bash
git describe --tags
```

- Clone the repository called "project" with tag "v0.0.3" to your local via this link: `git@gitlab.dtl:user/project.git`
```bash
git clone git@gitlab.dtl:user/project.git project.0.0.3
```

- Clone the repository using one's personal access token
```bash
git clone https://oauth-key-goes-here@github.com/username/repo.git
```

- Clone and update submodule
```bash
git submodule init
git submodule update
```

- Check out to a specific tag
```bash
git checkout <tag-name>
```

- Merge changes from feature branch to master branch
```bash
git checkout master
git pull origin master
git merge feature-branch
git push origin master
```

- Get url of remote repository
```bash
git remote -v
```

- Set up git credentials for Vertex AI notebook
```bash
mkdir ~/.ssh/
cp id_ed25519* ~/.ssh/
cd ~/.ssh/
chmod 600 id_ed25519
git config --global user.email "shenghao.wang@gojek.com"
```

- Migrate repo from BitBucket to GitHub
```bash
git clone https://Shenghao1993@bitbucket.org/Shenghao1993/coursera-introduction-to-data-science-in-python.git
git remote add upstream https://github.com/shenghaowang/udacity-ai-for-trading-nanodegree.git
git remote -v
git remote set-url origin git@github.com:shenghaowang/udacity-ai-for-trading-nanodegree.git
git push -u origin master
```

- Set up ssh to access remote site without password
	1. Generate private and public keys on the local machine by running `ssh-keygen`.
	2. Copy the public key.
	3. Go to the remote site. Under the directory ~/.ssh, create a text file called "authorized_keys" if it doesn't exist.
	4. Paste the public key into the file.
	5. Shortcut: `ssh-copy-id -i ~/.ssh/id_rsa.pub mahwah-dtltrad3` (Send generated public key from car8 to mw3)

- Copy public key of one machine to another machine
```bash
$ ssh-copy-id -i ~/.ssh/dat_prod1.pub dtl-data01
```

- Check the email address linked with repos
```bash
git config --global user.email	# for all repos on the computer

git config user.email	# for a single repo
```

- Set email address linked with repos
```bash
git config --global user.email <email-address>	# for all repos on the computer

git config user.email <email-address>	# for a single repo
```

- To fix the *git push* error: `Unable to append to .git/logs/refs/remotes/origin/master: Permission denied`. The owner and group might be set to root.

```bash
sudo chown -R "${USER:-$(id -un)}" .	# run this from the root of the git working tree
```

```bash
sudo chgrp {user} .git/logs/refs/remotes/origin/master
sudo chown {user} .git/logs/refs/remotes/origin/master
```

- To fix the *git push* error: `insufficient permission for adding an object to repository database`
```bash
sudo chown -R "${USER:-$(id -un)}" .
```

- Delete a feature branch from both local and remote
```bash
git checkout master
git branch -D <feature-branch>
git push origin --delete <feature-branch>
git branch --all
```

- Create a branch out of an existing branch
```bash
git checkout old_branch
git branch new_branch
```

```bash
git checkout -b new_branch old_branch
```

- Rename a git branch
```bash
git branch -m <newname>	# To rename the current branch

git branch -m <oldname> <newname>	# To rename a branch while pointed to any branch

git push origin -u <newname>	# To push the local branch and reset the upstream branch

git push origin --delete <oldname>	# To delete the remote branch
```

- Release a new version
```bash
git checkout master + git pull
git checkout staging + git pull
git checkout -b release-xxx
git merge master + resolve merge conflicts
git push origin release-xxx
# Create 2 MRs (1 for merging to staging, 1 for merging to master) using the release template.
```
