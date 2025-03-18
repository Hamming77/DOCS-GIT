# DOCS-GIT

## SECTION 3 - COMMAND LINE
```sh
ls (~ HOME DIRECTORY)
"start ." (open windows explorer)
"ls DirectoryName"
"pwd"
"cd NameFolder/"
"cd .." (move backwards one level)
"touch fileName.ext" (create 1 or + files)
"mkdir directoryName"
"rm fileName.ext"
"rmdir directoryName" "rm -rf directoryName"
```

PASTE IN GIT BASH: (Shift + Ins)
cd /c/SRC/COURSES/UDEMY/GIT/
 
 code .					=>		Opens in the text editor (namely VS Code) the working directory and the branch you are currently working on

## SECTION 3 - CONFIGURE USER
```sh
git config --l
git config user.name
git config user.email
git config --global user.name "Firstname Lastname"
git config --global user.email user@email.com
```

## SECTION 4 - ADD & COMMIT
```sh
	WORKING DIRECTORY		=>		STAGING AREA		=> 		LOCAL REPOSITORY	=> 		REMOTE REPOSITORY

git status		=>	gives information on the current status of a git repository and its contents
git init		=>	Initialize a new Git repository: workspace that tracks and manages files within a folder, with its own history

git add			=> 	from WORKING DIRECTORY, send to STAGING AREA the changes to be commited later: "git addd file1 file2", "git add ."

git commit 		=>	commit changes from the STAGING AREA to the LOCAL REPOSITORY: git commit -m "My message when commiting"
git commit -a -m "msg"	=> 	add and commit in one command

git log			=> 	log of the commits for a given repository
```

## SECTION 5 - COMMITS IN DETAIL
```sh
git log --oneline		=>	log all the commits, with information of each commit formatted in just one line

git commit --amend		=>	"redo" the previous commit (modifying the files or the message) but only THE PREVIOUS COMMIT!
git commit -m "Some commit"
git add forgottenFile.txt
git commit --amend

.gitignore			=>	file with a list of directories and files that will be ignored in a given repository, so they will never be commited
	.fileName		=> 	ignore files named "fileName"
	folderName/		=> 	will ignore entire directoryName
	*.log			=> 	ignore any files with .log extension
```

## SECTION 6 - BRANCHES
```sh
HEAD			=>	pointer that refers to a particular branch reference
git branch		=>	shows existing branches in the repository; * indicates the branch we are currently on
git branch branchName	=>	creates a new branch based on the current HEAD, but does not switch to it
git branch -d brnchName	=>	deletes a branch (-D forces deletion even if content is not merged), but we mustn't be on the branch to be deleted
git branch -m 		=> 	move/rename a branch, and you must be on the branch to be renamed: git branch -m newName
git branch -r 		=>	view the remote repositories our local repository knows about

git switch branchName	=>	switches HEAD pointing to branchName
git switch -c brnchName	=>	creates a new branch upon the current HEAD, and switches HEAD pointing to the newly created branchName
git checkout -b brnchNm	=>	(similar to switch, older version doing more things than just switch, it creates new branch and switches to it)
git commit -a -m "msg"	=>	add and commit in one command
```

## SECTION 7 - MERGE BRANCHES
```sh
git branch -v 		=>	shows existing branches in the repository with latest commit info for each one; * indicates the branch we are currently on
git merge branchName	=>	merges the changes from branchName to the branch where HEAD is pointing to
	Fast Forward merge: Main branch does not have any new commit in comparison to the new branch; just to move Main branch pointer to the last commit
	Merge without conflicts: when there is new stuff in Main but doesn't conflict with the branch; git performs a merge commit with 2 different parents
	Merge conflicts: git automatically changes the contents of the files to indicate the conflicts from both branches that must be manually resolved. 
```

## SECTION 8 - DIFF
Used in order to compare differences between files, commits or branches

```sh
git diff 			=> 	changes in our working directory not staged for the next commit
git diff HEAD			=> 	all changes in working directory since your last commit, including staged and unstaged changes
git diff --staged		=> 	changes between our staging area and our last commit
git diff HEAD [filename]	
git diff --staged [filename]
git diff branch1..branch2
git diff commit1..commit2	=>	git diff 4a9da7b..bfb0cc2
```

## SECTION 9 - STASH
Preserve changes made in the WORKING DIRECTORY or the STAGING AREA without commiting them
	
## SECTION 11 - GITHUB BASICS

```sh
git clone <url>		=>	get a local copy of an existing remote repository with its history; git creates and initializes the repo destination folder

1. Log into Github account: check that that matches with account set locally in Git: git config user.email
2. Generate and configure SSH key: 
	2.1. Check in case there is a previously existing SSH key: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
	2.2. If not, generate a new one: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
	2.3. Probably it will necessary to configure "Auto-launching ssh-agent on Git for Windows" https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases
	2.4. Add the new SSH key to your GitHub account
		https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
		
	How to get local code on Github?
	OPTION 1: EXISTING LOCAL REPOSITORY
		1.1. 	Create a new repository on GITHUB
		1.2. 	Connect local repo (add a REMOTE	=> git remote)
		1.3. 	Push changes to GITHUB
			git push <remote> <branch>	=>	push work up to Github from the entire local <branch>

		Usual sequence once remote repository has been created:
			git remote add origin https://github.com/Hamming77/PlaylistTake2.git
			git branch -M main
			git push -u origin main
		
	OPTION 2: START FROM SCRATCH, NO LOCAL NOR REMOTE REPOS
		2.1. 	Create a brand new repo on Github
		2.2.	Clone it down to the local machine
		2.3.	Do some local work
		2.4.	Push changes to Github
		
git remote			=>	view any existing remotes for the current repository
git remote -v			=>	verbose mode
git remote add <name> <url>	=>	add a new remote repository, to a URL that will be given the alias <name>
git remote set-url <name> <url>	=>	git remote set-url origin https://github.com/Hamming77/remote-branches-demo.git
		
git push <remote> <localBranch>:<remoteBranch>	=>	push a local branch to a remote branch with a different name; it will create it if it doesn't exist
git push -u origin main		=>	sets the upstream connection of the local main branch, tracking the main branch on the remote origin repository
		Establece una conexión directa entre la rama local y la remota, de forma que a partir de ahí ya solo es necesario "git push" para subir a la rama
```
		
## SECTION 12 - FETCH & PULL

```sh
REMOTE TRACKING BRANCH (origin/branchName): reference to the state of the homonimous branch on the remote; it can't moved by the user.
git branch -r			=>	view the remote repositories our local repository knows about

git checkout origin/branchName 	=>	checkout the remote branch pointer (usually it is one or more commits behind the pointer to the local repository)
	This is called DETACHED HEAD mode; to return to the previous situation: git switch -

git switch <remoteBranch>	=>	When we clone a project with several branches, we might only have main branch in local. In order to work locally with any of those branches, git switch will create a new local branch from the remote branch of the same name.

git fetch <remote>		=>	download changes from remote repository to the local one, but they won't be automatically integrated into our working directory
without having to merge those changes to your local repo, not screwing it up.

git checkout origin/branchName	=>	This allows you to see what others have done, but entering into detached HEAD mode
git fetch <remote> <branch>	=>	fetch a specific branch from a remote		

git pull <remote> <branch>	=> retrieve changes from a remote repository, updating our working directory (equal to: git fetch + git merge). Whatever branch we run this command from is where the changes will be merged into. Pulls can result in merge conflicts.

git pull			=> short syntax: remote defaults to origin & branch defaults to the tracking connection just configured for current local branch
```

## SECTION 13 - .md, GISTS & PAGES
### MARKDOWN (.md)
	https://daringfireball.net/projects/markdown/
	https://markdown-it.github.io/

### GISTS
A simple way to share code snippets and useful fragments with others
### PAGES
Public client-side static pages hosted and published via Github, so the website can be created simply pushing up the HTML/JS/CSS code to Github
	https://pages.github.com
	USER SITE: 1 user site per Github account, to host a portfolio site or some form of personal website: https://username.github.io
	PROJECT SITE: A Github repo can have a corresponding hosted website (index.html), set the branch with the web content: https://username.github.io/repoName
		Github repo / Settings / Github Pages / Source / Select branch / Save
