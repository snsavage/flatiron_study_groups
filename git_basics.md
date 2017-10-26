# Git Basics
#flatiron school/teaching assistant#

**Always be committing!**

## Git Configuration
Make sure to have these set.  This is how you will be identified in your commits.
```bash
$ git config --global user.name "<username>"
$ git config --global user.email "<email>"
$ git config --list
```

## Git Basics
### Help
Getting help.
```bash
$ git help <command | alias>		# View help information or expand alias.
```

### Init
Create a new repo in a new or existing director.
```bash
$ git init <project name>		# New git repo in new directory.
$ git init						# New git repo in existing directory.
```

### Status
See the status of the working and stating areas.
```bash
$ git status						# Show the status of the working and staging areas.
```

### Add
Manage files in the staging area.  These are the files that will be committed. 
```bash
$ git add .						# Places files in "staging".
$ git add <filename>				# Add a specific file to the staging area.
```

### Commit
Create a new commit.
```bash
$ git commit						# Create a new commit from files in staging area.
$ git commit -m					# Commit with message provided on command line.
$ git commit -am					# Stating all files for commit.
```

#### The seven rules of a great Git commit message.
1. Separate subject from body with a blank line.
2. Limit the subject line to 50 characters.
3. Capitalize the subject line.
4. Do not end the subject line with a period.
5. Use the imperative mood in the subject line (“spoken or written as if giving a command or instruction”).
6. Wrap the body at 72 characters.
7. Use the body to explain what and why vs. how.

Example `~/.gitmessage`
```md

#
# Answer this question in the 50-character subject line:
# If applied, this commit will...
#
# Include two sections in longer commits with 72-char wrapped lines:
# Why:
# This change addresses the need by:
#
```

## Viewing Changes & History
### Diff
View differences between versions of files.
```bash
$ git diff						# How working files are different from staging area.
$ git diff --staged				# How staged files are different from most recent commit.
$ git diff HEAD					# Compared working tree to the HEAD commit.
$ git diff --word-diff			# Shows changed words instead of changed lines.
$ git diff --color-words
$ git diff --stat					# Shows files with changes. 
```

### Log
View repo history.
```bash
$ git log												# Newest at top.
$ git log --oneline									# Single line summary of commits 
$ git log --stat										# Commit message and files changed.
$ git log --patch										# Shows the diff between commits.
$ git log --graph										# ASCII art commit history.
$ git log --graph --all --decorate --oneline
$ git shortlog										# Groups by user.
$ git log --stat -- <filename>						# Shows commits for just that file. 
$ git log --state -M --follow -- <filename>			# Follows file history across moves.
```

Advanced log settings.
```bash
$ git config --global alias.sla 'log --oneline --decorate --graph --all'
$ git sla
```

Advanced log searching.
```bash
$ git log -E -i --grep '<search term>'	# git config --global alias.glog 'log -E -i --grep'  
$ git log -S <string in code>			# Searches for string changes in commits.
$ git log --oneline -- <filename>		# Commits that changed the file.
$ git blame <filename>					# See who made changes to a file.
$ git show <commit ref>					# Show information about a specific commit.
```

## Moving & Deleting Files
### Removing Files
Remove files from future commits.
```bash
$ git rm <filename>				# Remove file from future commits.
$ git add -u .					# Stage removed files as new deletions.
$ git rm --cached	 <filename>		# Removes from git tracking, but not from filesystem.
```

### Moving Files
Move files.  In git renaming and moving are the same thing.  *Git uses a 50% similarly threshold to determine if a file has been moved.  This works with merges too.*
```bash
$ git mv <old filename> <new filename>
$ git add -A .					# Finds new files and deletes old files.  Shows changes as moves.
```

## Ignoring Files
Files can be ignored by git.  These settings are kept in the `.gitignore` file in your project root.
```
*.log		# Ignore files with a ".log" extension.
tmp/		# Ignore files in the "tmp/" directory.	
```

* Ignore patterns apply to director and subdirectories.
* Use `!` to negate pattern.
* `.gitignore` files in subdirectories take precedence.

```bash
$ git ls-files --others --ignored --exclude-standard		# View ignored files. 
```

## Managing Workflow
### Branch
The master branch should be the representation of what is on production.  Branches should be used for any new features or bug fixes.  **When changing branches, uncommitted changes will travel to the new branch.  Unless those changes conflict with files on the branch to be opened.**

```bash
$ git branch <new branch name>				# Create new branch.
$	git branch -d <branch to delete>			# Delete a branch.
$ git checkout <branch name>					# Change to branch.
```

### Stash
Use `stash` to temporarily store files without committing. 
```bash
$ git stash -u			# Stash unstaged files.
$ git stash pop			# Get most recent stash.
$ git stash list			# List available stashes.
$ git stash drop			# Remove a stash.
```

### Checkout
Change the current working code.
```bash
$ git branch									# List branches.
$ git checkout <commit ref>					# View files at that point in time.  DO NOT make changes.
$ git checkout -- <filename>					# Write files contense from the last commit.
$ git checkout -b <new branch>				# Create branch and checkout that new branch.
$ git checkout <commit ref> 					# Enter detached `HEAD` mode.  Only for viewing code.
```

### Merge
Combines two or more branches together.
```bash
$ git checkout master
$ git branch
$ git merge <branch to merge with master>
```

When there is a conflict.
```bash
$ git status						# View list of conflicting files.
$ vim <file with conflict>		# Open file with conflicts to fix.
```

Look for `<<<<<<<HEAD`, `========`, and `>>>>>>>> <branch name>`.  These denote the conflicting lines on the current branch and the branch to be merged.  Edit file to remove conflict markers and fix conflicting code.  Then save the file.  Check `git status` for other conflicts.  Stage all fixed files with `git add`.  Then commit with `git commit`.

```bash
$ git merge --abort				# Stops merge and cleans up working and staging areas.
```  

Brings in commits, but not histories.
```bash
$ git merge --squash <branch to merge>
```

Delete branches.
```bash
$ git branch -b <branch name>		# Removes branch and branch label.
```

## Remotes
Work with code on remote machines, such as GitHub.com
```bash
$ git remote add <destination name> <url>	# Add new remote.
$ git remote set-uri <name> <new url>		# Change remote url.
$ git remote rm <name>						# Remove remote.
$ git remote -v								# View list of remotes.
$ git branch -r								# View remote tracking branches.
$ git fetch									# Gets remote data and places in remote tracking branch.
$ git pull									# Gets and merges into current branch from remote.
$ git push <name> <branch>					# Sends local version to remote.
```

**Don’t mess with commits that have already been pushed up to GitHub!**

# Git Flow
#### Pull Request Process
1. Create new feature branch.
2. Work on feature and always be committing!
3. Push branch to GitHub.
4. Create pull request on GitHub.
5. Wait for feedback.
6. Rebase with master.
7. Squash commits into one single commit.
8. Use `git push -f` to force update with final commit.
9. Merge branch back to master.
10. Push master back to GitHub.  

#### Tips for Pull Requests:
* Pull requests should be as small as possible.  This way it’s easy for reviewer to read.
* Changes should be related.
* Provide additional context about the changes.
* Include screenshots for anything that changes UI.
* Animated gifs can be helpful to show workflow.
* Use tasks lists showing the current completion of a pull request.

#### Forking
* Copies a repo under your own account.  Changes can be made safely.
* Offer changes back to original with a Pull Request.

#### Pull Requests
* Way to submit changes to a project.
* Pull requests can include conversations, code revisions, and approval/denial of the changes.
* Pull requests have unique urls.
* Can integrate with Continuous Integration (CI) services. 
* Delete the branch to prevent future development in that branch.

## Changing History
### Reset
* Mixed - Alters history and working directory.
* Soft - Commits are added to staging area.
* Hard - Destructive operation to delete changes.

```bash
$ git reset HEAD				# Moves changes from staging to working changes.
$ git reset <filename>  				# Remove file from staging.
$ git reset							# Remove all files from staging.
$ git checkout .						# Set all files back to last commit.  Dangerous!
$ git reset --soft HEAD^				# Reset back to previous commit.
$ git reset --soft HEAD~5	# Squashes last five commits into staging area to be committed as one.
$ git reset --hard HEAD~3	# Remove the last three commits from the history.
$ git checkout <commit ref> <filename> 		# ???
```

### Reflog
Revisions to revisions.  Rolling 30 day buffer.
```bash
$ git reflog				# All changes on current branch.
$ git reset --hard <commit ref>
```

### Rebase
Allows a branch to be relocated down the history track.  For instance, you’re working on a new feature and during that time, changes have been made to the master branch.  Rebase allows you to reincorporate those other changes from master.  Better than a reverse merge from Master.

`rebase` alters all of the commits in the branch.  Not for branches that are used by others.

```bash
$ git rebase <master>
```

Break up changes into related commits.  (For example if one file has unrelated changes.)
```bash
$ git add --patch						# For file specific adds.
$ git diff --cached					# View all staged changes.
$ git diff							# Unstaged changes.
```

Move commits to current branch.
```bash
$ git diff <ref>..<ref>
$ git cherry-pick <ref>..<ref>
$ git checkout master
$ git reset --hard <ref>
```

Move commits ahead in history.  From feature branch…
```bash
$ git rebase master
```

Interactive rebase.  Revise history.  Often used for squashing.  Never revise published history!
```bash
$ git rebase -i <branch>
```

# Resources
* [Git](https://git-scm.com/)
* [Oh, shit, git!](http://ohshitgit.com/)
* [Mastering Git | Online Tutorial by thoughtbot](https://thoughtbot.com/upcase/mastering-git)
* [Code Sleuthing with Git](https://robots.thoughtbot.com/code-sleuthing-with-git)
* [Git Tutorial - Try Git](https://try.github.io/levels/1/challenges/1)
* [Learn Git- Git tutorials, workflows and commands | Atlasssian Git Tutorial](https://www.atlassian.com/git)
* [Git Interactive Rebase, Squash, Amend and Other Ways of Rewriting History](https://robots.thoughtbot.com/git-interactive-rebase-squash-amend-rewriting-history)
* [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
* [Better Commit Messages with a .gitmessage Template](https://robots.thoughtbot.com/better-commit-messages-with-a-gitmessage-template)
* [Git Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
* [Introduction • GitHub & Git Foundations - YouTube](https://www.youtube.com/watch?v=FyfwLX4HAxM&list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-)

# GUI Clients
* [GitHub Desktop | Simple collaboration from your desktop](https://desktop.github.com/)
* [Git GUI for Windows, Mac & Linux | GitKraken](https://www.gitkraken.com/)
* [Tower - The most powerful Git client for Mac and Windows](https://www.git-tower.com/mac/)