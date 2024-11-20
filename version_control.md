# Version control
* Version control - also known as source control or revision control - is an important software development 
practice for tracking  and managing changes made to code and other files.


## types of versin control
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

