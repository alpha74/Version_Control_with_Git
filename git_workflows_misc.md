# GIT 
__Author: alpha74__


## GIT WORKFLOWS:
	
#### Centralized Workflow:
- Uses a single branch.
- Team members have local copies of project.

- *Cons*:
	- Features related to branching and PRs are not used.

#### Feature Branch Workflow:
- Work is done on feature/topic branches.
- feature branch is merged in base branch.
- Uses a single remote repo.

- *Pros*:
	- Uses branching and PRs.
		
#### Forking Workflow:
- Involves multiple remote repos.
- One of the remote repo is considered `upstream` from all, and is considered __source of truth__ .
- Work is transfered from `remote` repo to `upstream` repo using PR.
- Mostly used in OSS.

- *Pros*:
	- User of forked repo does not need to have `write-access` to `upstream` repo.

- *Cons*:
	- Forked repo can become un-sync with `upstream`. 


#### Gitflow Workflow:
- Allows safe continues releases of project.
- Involves two or more long running branches like: `release`, `master`, `develop`.
- And short duration branches like: `featureX`, `topicA`, `hotfix-1`.

- *Some Rules*:
	- Only merge commit on `master`.
	- Commit to `master` only from `release` or `hotfix` branch.
	- `develop` branch then adds a merge commit from `release` branch, if committed to `master`.


### LIST OF PLUMBING COMMANDS IN GIT:
- `cat file`
- `check-ignore`
- `commit-tree`
- `count-objects`
- `diff-index`
- `for-each-ref`
- `hash-object`
- `ls-files`
- `merge-base`
- `read-tree`
- `rev-list`
- `rev-parse`
- `show-ref`
- `symbolic-ref`
- `update-index`
- `update-ref`
- `verify-pack`
- `write-tree`

### LEFT:	
- `git diff` : See the difference of changes made to the directory(shows only when commits are not made after changes).
- `git diff <filename>` : Same for specific file.
- `git diff -staged` : See all difference of changes made to the directory, after staging is done.2
