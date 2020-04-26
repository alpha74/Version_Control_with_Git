# GIT
__Author: alpha74__

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
