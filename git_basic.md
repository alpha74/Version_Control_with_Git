# GIT 
__Author: alpha74__

## BASICS

### COMPONENTS OF GIT.
1. *Working tree:*
	- All the physical files present in the project.
		
2. *Staging Area:* 
	- Place where changes to be included in next commit are stored.
		
3. *Local Repository:* 
	- Contains all the commits. 
	- A commit is snapshot of the project.
		
4. *Remote Repository:* 
	- Remotely located repository. 
	- Serves as global truth.
	- Not has Staging Area and Working tree, only repo with commit hostory.
	- It is often a "bare" repo. Names generally ends with `.git`.

5. *Terms:*
	- `HEAD` : It points to last commit node on the branch. It is a `git id`. A Git Id is the name of Git object.



### VERSION:
- `git --version` : Tells version of git.


### INIT:
- `git init` : Initializes the current directory into Git local repository.
- `ls -la` : Lists hidden files in the git repository.
- `git init --bare` : Creates remote repo.


### CONFIGURE
- `git config --global user.name "<name>" ` : To set the global user name
- `git config --global user.email "<email address>" ` : To set global email address.

- `git config --list` : Lists all configurations settings

- All flags:
	- `-- system`
	- `--local`
	- `--global`


### HELP:	
- `git help <command>` : Displays help menu. Displays large documentation.
- `git <command> -h` : Displays short description in cmd.
	

### DIRECTORY: 	
- `pwd` : Current path of working directory.
- `cd ~` : Change directory to home(of bash).
- `#` : Used for comments.


### ADD FILES TO STAGING AREA:
- `git add .` : Add all the changes in current dir to staging area.
- `git add --a` : Same as aboves
- `git add <file>` : Makes changes made to that file ready for commiting.


### CREATING AND REMOVING FILES:
- `touch <filename>` : Creates new file.
- `echo "<text>" >> <filename> ` : Store text in filename.
- `git rm <filename>` : Removes file(can only do after staging and commiting).


### STATUS:
- `git status` : Displays changes made to files in that directory which are/not yet commited.
- `git status -s` : Displays short online status of each file in staging area.


### COMMIT :
- `git commit -m "message" ` : To commit with a message
- `-m` flag is optional, and is used for writing a short message with commit.


### CLONE:
1. *If no local repo exists:*
	- `git clone <link> [local repo name] ` : 
		- To clone a git repository using link. 
		- `[local repo name]` is optional.
	- `git push -u origin <branch>` : 
		- Push commits to remote.
		- Here, origin is an alias for URL of remote repo.
		

2. *If local repo exists and some commits are in staging area:*
	- `git remote add origin <link of remote .git>` : Add remote repo to local repo.
	- `git remote -v`  or  `git remote --verbose` : See details of remote repo. 
	- `git push -u origin <branch> ` : 
		Push commits to remote.
		- `-u` : track this branch aka `--set-upstream`.
		- Here, `<branch>` set up to track remote `<branch>` from origin.


### GIT LOG & SHOW:
- `git log` : See all the commits.
- `git log --oneline` : Condensed version of log.
- `git log --online -2` : Will return only last two logs.
- `git log --author="<user.name>" ` : Lists all the commits done by a specific user.

- `git log <git id> -1` : See one liner log associated with given commit hash. `git id` is 4 or more chars of hash value of commit.
- `git show <git id> ` : Shows detailed changes associated with this commit along with author and differences.

- *Graphs:* `git log --online --graph` : Graphical view of commits on local branch with comparison.
