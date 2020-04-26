# GIT 


## ADVANCED-II

### MERGE CONFLICTS:
	- Occurs when multiple branches change same: part of a file(a hunk).
	- Merge is also successful if different hunks of files are changed.
	- A modular code has less merge conflicts.
	
	- *Resolving*:
		- Involves 3 commits.
		- When attempting to merge, files with conflicts are modified by Git and placed in working tree of current branch.
		- Fix these files before attempting a successful merge.
		- Git will prompt to fix the conflicts and create a new commit.
		- `git merge --abort` : To abort the current merge operation.
		
	- In the conflicted files:
		- `<<<<<<< HEAD` denotes `ours`.
		- `>>>>>>> <topicbranch>` denotes `theirs`.
		- `=======` separates these lines.
		
		- Lines not enclosed by arrow symbols are cleanly resolved by Git.


### TRACKING BRANCHES:
	- Its name starts with the remote name then a / and then branch name.
	- Eg: `origin/master`.
	- It is pointed to latest commit after clone from remote.
	- It not moves when a new commit is made locally.
	- It only moves with network commands.
	
	- `git branch --all` : Shows local and tracking branches. 
		
	- `git remote set-head <remote> <branch>` : Change default remote tracking branch.
	
	- `git status` : List tracking branch status also.
	
	- `git log --all` : Lists combined log of all local and tracking branches.
	

### NETWORK COMMANDS:
	- Network commands interact with remote repo.
	- List:
		- *Clone* : Copies a remote repo.
		- *Fetch* : Retrieves new objects and references from remote repo.
		- *Pull* : Fetches and merges locally.
		- *Push* : Adds new objects and references to remote repo.
		
### FETCH:
	- `git fetch <repo>` : 
		- Default: origin.
		- Can specify other tracking branch.
		- We can use `git log` to see changes fetched.
		
	- Retrieves new objects and references from remote repo.
	- Tracking branches are updated.
	- Changes are not immdiately merged. 
	- After fetch:
		- `HEAD` points to last local commit.
		- Tracking branch points to remote's last commit.
	
	
### PULL:
	- `git pull`:
		- Combines `git fetch` and `git merge FETCH_HEAD`.
		- If new changes are fetched, tracking branch is merged into current local branch.
		- Similiar to merging topic branch to base branch.
		
	- *Flags used*:
		- `--ff` : Performs a FF-merge if possible.
		- `--no-ff` : Always include a merge commit.
		- `--ff-only` : Cancel if FF merge is not possible.
		` `--rebase [--preserve-merges]` : SEE REBASE.
	
	- If pull executes with merge commit, tracking branch not points to new merge commit, but to last commit of remote.


### PUSH:
	- `git push [-u] [<repo>] [<branch>]`
		- `-u` : Track this branch (--set-upstream); Sets up local tracking branch with this branch.
		- Push fails if remote tracking branch is ahread of local branch.
	
	- *Flags*:
		- `--ff` : Always performs a FF merge.


### DIFF:
	- Each commit contains a snapshot of complete project.
	- Git calculates difference between commits, called `diff` or `patch`.


### REBASE:
	- Can rewrite history.
	- Moves commits to new parent(base).
		- The unique commits of topic branch are reapplied to tip of master branch.
		- topic branch didn't point to tip previously.
		- Becasue the ancestor chain is different, eahc of reapplied commuts has different commit ID.
		- Merge commit is no longer needed. FF merge will work.

	- When rebasing, Git applies diffs to new parent commit, called *reapplying commit*.
	- `Diffs` between the tip and `topic` branch commit, and following commits in `topic` branch are recalculated. 
	
	- *Pros*:
		- Can incorporate changes from parent branch.
		- Can use new bugs/features.
		- Makes eventual merge into master FF-able.
		- Allows to shape clean commit histories.
	
	- *Cons*:
		- Merge conficts.
		- Problems if commits have been shared.
		- Not preserving commit history.

	- `git rebase <upstream>`:
		- `<upstream>` is generally `master` branch.
		- Changes parent of currently checked out branch to `<upstream>`.
	
	- `git rebase <upstream> <branch>`:
		- Checks out `<branch>` and changes its parent to `<upstream>`.

	- `git am --show-current-patch` : View failed patch in merge conflict.


### REBASE: MERGE CONFLICTS:
	- Files with merge conflicts are modified by Git.
	- Resolve the conflicts manually.
	- Use `git status --all` to view conflicts.
	
	- After resolve, use commands:
		- `git add .` : To add the changes after resolving.
		- `git rebase --skip` : Skip the current patch.
		- `git rebase --abort` : Stop rebasing and checkout the `topic` branch in pre-rebase state.
		- `git rebase --continue` : Continue after merge conflict resolve.
		

### REWRITING HISTORY:

	- *Ammeding Recent Commit*:
		- Can change commit message.
		- Change project files.
		- `git commit --amend -m "new-message"`:
			- Changes the message of last commit.
			- `SHA-1` of this commit changes.
			
	- *Changing Commited Files`:
		- `git add <file>` : Add new file to included in recent commit.
		- `git commit --amend [--no-edit]` : Commits new files.
		- `--no-edit` : Reuse the old commit message.
		- `SHA-1` of the commit changes.

	- *INTERACTIVE REBASE*:
		- Edit commits using commands.
		- Commits can belong to any branch.
		- Commit history is changed.
		
		- git rebase -i <commit>`:
			- Commits in current branch after `<commit>` are listed in editor to edit.
			
		- *Interactive Rebase options*:
			- Use commit as is.
			- Edit the commit message.
			- Stop and edit the commit.
			- Drop/delete the commit.
			- Squash
			- Fixup
			- Reorder commits
			- Execute shell commands 


### SQUASH MERGE:
	- Rewrites commit history.
	
	- Merges tip of `topic` branch onto tip of `base` branch.
	- Chance of merge conflict.
	- Places result in `staging area`, which can then be commited.
	- All commits of `topic` branch are no longer in commit graph, and only one new `merge commit` is created in `base` branch.
	
	- *Steps*:
		- `git checkout <base-branch>`
		- `git merge --squash <topic-branch>`
		- `git commmit`
			- accept or modify the `squash message`.
		- `git branch -D <topic-branch>`
		

## ADVANCED-III


### FORKING:
	- It is a feature of Git hosting website.
	- It means : Copying a remote repo to our own online account.
	- Both are remote repo.
	- `upstream` repo is considered the __source of truth__ .
	- Can be used to create a new __source of truth__ .
	
	
### PULL REQUESTS:
	- It is a feature of Git hosting sites.
	- Goal is to merge a branch into project.
	- Enable team communication.
	- Need not edit the PR if new commits are added.
	
	- *Single Repo PR*:
		- A remote repo and its clone is needed.
		
		- *Steps*:
			- Create a `topic` branch from `base` branch locally.
			- Work and push to remote repo using `git push --set-upstream origin topic`.
			- A `PR` will be created.
		
		- `git push -d origin <topic>`: Deletes `topic` branch from remote repo.

	- *Multi Repo PR*:
		- A `remote repo` and a `fork` is needed.
		
		- *Steps*:
			- Fork the `upstream` repo.
			- Create a branch.
			- Create a PR.
