# Version control
* Version control - also known as source control or revision control - is an important software development 
practice for tracking  and managing changes made to code and other files.


## Types of Version control
* Centralized version control
* Distributed version control


# Git 
* A repository is a collection of files and directories that are stored together. 
* the staging area is the middle ground between what you have done to your files (also known as the working directory) and what you had last committed (the HEAD commit). 
* As the name implies, the staging area gives you space to prepare (stage) the changes that will be reflected 
on the next commit.

## commit objects
Each commit in the project is stored in .git folder in the form of a commit object. A commit object contains the following information:
    * Tree Object
    * Parent Commit Object
    * Author
    * Commiter
    * Commit Message

## Tree objects
Tree Object is a container for all the files and folders in the project. It contains the following information
    * File Mode
    * File Name
    * File Hash
    * Parent Tree Object

## Blobs
Blob Object is present in the tree object and contains the actual file content. This is the place where the file content is stored.

## Head
* The HEAD is a pointer to the current branch that you are working on. 

## Branches
* Branches are a way to work on different versions of a project at the same time.

```cmd
git branch
git branch bug-fix
git switch bug-fix
git log
git switch master
git switch -c dark-mode
git checkout orange-mode
```

## Merging branch
```cmd
git checkout main
git merge bug-fix
```

## Git diff
The git diff is an informative command that shows the differences between two commits. 
It is used to compare the changes made in one commit with the changes made in another commit.
How to read the diff
* a -> file A and b -> file B
* ---- indicates the file A
* +++ indicates the file B
* @@ indicates the line number

```cmd
git diff
git diff --staged
git diff <branch-name-one> <branch-name-two>
git diff <commit-hash-one> <commit-hash-two>
```


## Stash
Stash is a way to save your changes in a temporary location. It is useful when you want to make 
changes to a file but don’t want to commit them yet

```cmd
git stash
git stash save "work in progress on X feature"
git stash list
git stash apply
git stash apply stash@{0}
git stash drop
git stash clear
```

## Rebase
Git rebase is a powerful Git feature used to change the base of a branch.
It effectively allows you to move a branch to a new starting point, usually a different commit, by “replaying” 
the commits from the original base onto the new base. 
This can be useful for keeping a cleaner, linear project history.

```cmd
git checkout feature-branch
git rebase main
```

## Git reflog
Git reflog is a command that shows you the history of your commits.
It allows you to see the changes that you have made to your repository over time.


```cmd
git reflog
git reflog <commit-hash>
```

