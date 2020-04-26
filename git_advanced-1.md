# GIT 
__Author: alpha74__

## ADVANCED-I

### HASH GENERATION:
- `git hash-object <file>`: 
 - Create a SHA-1 hash for any file. 
 - Returns a 40char log string of hash.
 - Same file returns same hash, and vice versa.


### GIT REFERENCES ~ and ^ :
- Git references are short names for SHA-1 hashes.
- `git show HEAD` 
	- Shows commit pointed by HEAD(generally the last commit on the branch). 
	- Here `HEAD` is a reference of a SHA-1 hash.

- `~` :
	- `git show HEAD~1`
		- Shows detailed commit information of immediate parent of HEAD.
		- `~` is assumed to be `~1`. `~~` is same as `~2`.
		- `~#` : Use different values of `#` to get different commit information.

- `^` :
	- Used in case of `merge` commits, where two branches merge into one.
	- `^` or `^1` : Refers to first parent of commit.
	- `^2` : Refers to second parent of merge commit.
	- `^^` : Refers to first parent's first parent.
	- `^2^` : Refers to second parent's first parent.


### GIT TAGS:
- Tags can be used instead of branch labels or Git IDs in git commands.
- Tags are simple text messages associated with labels, and they are NOT git objects. `Annotated tags` are.
- `git tag` : Shows all tags in repo.
- `git tag v0.1` : Shows tag with name `v0.1`.
- `git tag <tagname> [<commit>]` : Creates tag with `<tagname>`. `<commit>` defaults to `HEAD`.


### ANNOTATED TAGS:
- `git tag -a  [-m <msg> | -F <file>] <tagname> [<commit>]` : Creates an annotated tag.

- Annotated tags are git objects which store:
	- Message: 
		- `[-m <msg>]` 
		- Optional. 
		- Provide a short message in cmd itself.

	- Message from file:
		- `[-F <file>]` : 
		- Optional. 
		- Provide a message in a file.

 - Commit:
   - Optional.
   - `[<commit>]` defaults to `HEAD`.

- `git tag -a -m "new release" v2.0` : 
	- Creates an annotated tag with message "new release" using reference from another tag `v2.0`.
	- This type of reference is called `Symbolic reference`.

- *Pushing Tags:*
	- Tags are automatically pushed to remote.
	- `git push <remote> <tagname>` : Pushes tag `<tagname>` to remote(origin).
	- `git push <remote> --tags` : Pushes all tags to remote.


## GIT BRANCHES & REFLOG:
- `git branch` : List all the branches in local repo. Current branch has asterisk on it.
- `git branch <newbranch>` : Creates a new branch from HEAD of current branch. Current branch is still the same.
- `git checkout <branch_or_commit>` : 
	- Checkout to a branch or commit.
	- Checkout commit is used to temporarily view an older version of project.
	- Checkout commit leads to detached HEAD state, as HEAD points directly to SHA-1 label.
	- To edit files here, a new branch should be created.

- `git branch -d <branchname>` : 
	- Deletes the branch label. 
	- Works if no commits are made to that branch, and branch is not merged.
- `git branch -D <branchname>` : 
	- Deletes branch label even if some commits are made and branch is not merged.

- `git checkout -b <newbranch>` : Combines `git branch` and `git checkout`. Works only for new branches.

- `git reflog`: 
	- Returns a local list of recent HEAD commits with SHA-1.
	- Works locally only.
	- `git checkout -b <newbranch> <SHA-1>` : Creates a branch from reflogged dangling commit.


### GIT MERGE:
- Merges a topic branch in a base branch.

- *Types of merge:*

	- *Fast Forward (FF)*:
		- Moves `base` branch label to tip of `topic` branch.
		- Moves `base` branch label from its latest commit to latest commit of `topic` branch.
		- Only `base` branch label moves.
		- Possible only if no other commits were made to `base` branch since branching.
		- Attempting a FF merge is default.

		- *Steps to merge `topic` branch to `base` branch*:
			- `git checkout base`
			- `git merge topic`

	- *Merge commit*:
		- Combines commits at the tips of merged branches.
		- Places result in a new merge commit.
		- A merge commit always has multiple parents.

		- *Steps to merge `topic` branch to `base` branch:
			- `git checkout base`
			- `git merge topic`
			- In case of merge commit, `Git` will open default editor to edit the merge message.

		- *Steps to create a Merge commit even if a FF commit is possible*:
			- `git checkout base`
			- `git merge --no-ff topic`

	- *Squash merge*:
		- It is a type of option in `Interactive Rebase`.
		- Combines the `selected commit` with `older commit` creating a single commit.
		- The work of both commits in included.
		- SEE REBASE & SQUASH MERGE.

		- *Delete(vs Squash)*:
			- No changes from this commit are applied.
			- `diff` is discarded.
			- Work of this commit is lost.
			- Greater chance of merge conflict.

	- *Rebase*:
		- SEE REBASE.

