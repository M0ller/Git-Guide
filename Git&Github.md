# Git and GitHub Summary

This is my own customized Git & GitHub "Cheat sheet/Guide" because my memory is like a goldfish. Feel free to use.

< some text > the “< >” is to illustrate what text that should be in that position.

## Sections
* [Create git repository](#create-git-repository)
* [Copy a remote branch repository from GitHub](#copy-a-remote-branch-repository-from-github)
* [Initialize the git repository](#initialize-the-git-repository)
* [Check the current state of the files in the folder](#check-the-current-state-of-the-files-in-the-folder)
* [Remove a file](#remove-a-file)
* [Add file before a commit](#add-file-before-a-commit)
* [Create a commit](#create-a-commit)
* [Changing Branch with checkout](#changing-branch-with-checkout)
* [Undo a commit](#undo-a-commit)
* [See last changes/history](#see-last-changes/history)
* [Git add+commit shortcut](#git-addcommit-shortcut)
* [Create new a branch (creates a branch and move to that branch)](#create-new-a-branch-creates-a-branch-and-move-to-that-branch)
* [Upload a repo to GitHub](#upload-a-repo-to-github)
* [Pull and Fetch to GitHub](#pull-and-fetch-to-github)
* [Push a branch to GitHub](#push-a-branch-to-github)
* [To push files to the connected repo](#to-push-files-to-the-connected-repo)
* [To connect a local repo to GitHub](#to-connect-a-local-repo-to-github)
* [Compare two branches](#compare-two-branches)
* [Compare & Pull request on GitHub](#compare--pull-request-on-github)
* [Delete a local branch](#delete-a-local-branch)
* [Delete a remote branch](#delete-a-remote-branch)
* [Replace a local branch with a remote branch](#replace-a-local-branch-with-a-remote-branch)
* [Merge](#merge)

## Create git repository
do it either with the terminal or manually.
Ex 
mkdir myProject
cd myProject

[Return to Top](#git-and-github-summary)
## Copy a remote branch repository (from GitHub)
Be in the folder where you want your repo to be created.

Write:
```
git clone <github repo URL/SSH>  <Optional, write the name you want your folder to have>
```
Clone(copy) a specific remote branch repository (from GitHub):
This will only copy the specific branch you want to work in.
write:
```
git clone -b <branch name you want to clone> <github url>
```
or:
```
git clone --branch <branch name you want to clone> <github url>
(“-b” is a short version of “--branch”. “-b” specify the specific branch to clone/copy.)
```

-----------------
If you have made a 
'git clone <GitHub url>'
already and is in the main branch you can run a 'git branch -a' (to see all branches locally and remote)
or 'git branch -r' (to see only remote branches)
Then just move into that branch by writing:
  
```
git checkout < Branch name > 
```

[Return to Top](#git-and-github-summary)
## Initialize the git repository
```
  git init
```

[Return to Top](#git-and-github-summary)
## Check the current state of the files in the folder
```
  git status
```

[Return to Top](#git-and-github-summary)
## Remove a file
```
  git rm -f <filename>
```

[Return to Top](#git-and-github-summary)
## Add file before a commit
Single file write:
```
  git add <file name >
```
example;
```
  git add myTextDoc.txt
```
Add multiple files:
```
git add .
```
(the “.” will add everything, including new, modified and deleted files)
You can also use:
  ```
git add –all
  ```
or:
  ```
git add -A
  ```
( “-A” is a short command for “--all” )

[Return to Top](#git-and-github-summary)
## Create a commit
  ```
git commit -m “my first commit”
```
But before doing a commit be sure that you have used “git add <file you want to add>” or “git add .” to add all files in the repo to be staged (“staged” meaning preparing which files you want to commit, so “git add” is just preparing the files.) 
Once a file is added with “git add” you can check the status of the files with “git status” and you will either see that new files have been added/created or that they have been modified.
If you have added a file but regret it you can revert it by writing 
“git reset <the file you added which you want to revert>”
Or just “git reset” and the changes will be reverted. So if you use a “git status” again you will see that changes haven't been staged again.

[Return to Top](#git-and-github-summary)
## Changing Branch with checkout
  
If you have local changes on your branch and want to change to another branch you have three options before changing to the new branch.
  1. Trash your local changes.
  2. Commit your local changes.
  3. Stash your local changes.
  
  To Trash your local changes you use the keyword ```-f```or ```--force``` after the checkout command.
  example:
  ```git checkout -f <Branch name>```
  
  To commit your changes you use the ```commit -m``` command.
  example: 
  ```git commit -m "My commit message"```
  
  To stash your changes you use the keyword ```stash```.
  example:
  ```git stash```
  git stash stores away the local changes in its own directory where you later can revisit a list of stashes. Generally not recommended to use.
  Can add more indent explanation for how to use the stash command.

[Return to Top](#git-and-github-summary)
## Undo a commit

If you have gone through a commit like the following.
```
  git add README.md
git commit -m add “readme file”
```
Now you regret going through these steps you can write
```
  git reset HEAD~1
```
What is happening here is that it will revert the changes, “HEAD” meaning the last command that have been done in git, but we did run two git commands, so we use the “~” and then add “1” so it will revert to the last one plus one extra step.
If you want to revert a specific change that have been done further back you can write: 
```
  git reset <hashcode of that change>
  ```
This will revert that specific change. In order to find the specific change run “git log” and find the change and copy its hashcode.

If you want to revert changes and have temp completely removed back to a certain time in the history you can write:
```
  git reset  -- hard <hashcode>
  ```
This will onstage all “git added files” and commits and remove everything back to that point in time.

[Return to Top](#git-and-github-summary)
## See last changes/history
If you want to see the last changes that have been made you can write:
  ```
  git log
  ```
and then click with space-bar to see further back in the history. Each change will have a long Hashcode which you can use to reset a specific change in the history.

To jump out of the log click “q”

[Return to Top](#git-and-github-summary)
## Git add+commit shortcut
A shortcut to use both git add and commit if it's a single file you can write “-am”
But it only works on modified files. And there must have been a “git add “ and “git commit” before.
TLDR, a “git commit -am ‘message’ “ can’t be the first commit done in the folder.

Write:
  ```
git commit -am “my message”
```

[Return to Top](#git-and-github-summary)
## Create new a branch (creates a branch and move to that branch)
To see display all existing branches use:
```
git branch
```
The “ * ” shows which branch you are in.

Create a new branch (you will still stay in your original branch):
```
git branch <new branch name>
```
To create and move directly into the new branch write:
```
git checkout -b <my branch name>
```
To move to specific branch use:
```
git checkout <branch name>
```

[Return to Top](#git-and-github-summary)
## Upload a repo to GitHub
Create a new repository on your GitHub and if you want to push an existing repo from your directory from your local computer (that you are currently on) use the second option on GitHub
”…or push an existing repository from the command line”

copy the git commands it provides example:
```
git remote add origin git@github.com:M0ller/new.git
git branch -M main
git push -u origin main
```

[Return to Top](#git-and-github-summary)
## Pull and Fetch to GitHub
Before you want to push your project to GitHub make sure you have med a:
```
git pull
```
this will tell that the local version is the latest version of that project in that branch compared to the one that exist on GitHub.
So when you do your git push it will overwrite the old version on GitHub.


-// Unsure
If you instead want to overwrite the version of the project you have locally you can run:
```
git fetch
```
it will overwrite your local version to the version that exist on GitHub.
(you can run a 
```
git diff ...origin 
```
to check the difference between the versions.)
-//

[Return to Top](#git-and-github-summary)
## Push a branch to GitHub
(branch name is the name you have created on your local computer. If you use ” main” as branch name which is usually the standard name of your branch)
You specify branch you want to push to in the <branch name>.
(If you have already established a connection with “git push -u origin <branch name>” you only need to write “git push”)
```
git push
```
(if connection is already made)
```
git push origin <branch name>
```
(push to specific branch in that repository)

You could replace “origin” to the address to your repo folder on GitHub for example.
```
git push git@github.com:M0ller/new.git <branch name>
```

[Return to Top](#git-and-github-summary)
## To push files to the connected repo
```
git push origin master
```
To avoid writing origin master every time we can write:
```
git push -u origin master
```
That will set this local repo to always push to this connected repo on GitHub in the future so after this you only need to write:
```
git push
```
If you try git push on a branch that doesn't have an upstream connection set you will usually get a message saying that like:
```
git push --set-upstream origin myOtherBranch
```
```
git push -u origin <branch name>
```
“--set-upstream” is the same as “-u” 

[Return to Top](#git-and-github-summary)
## To connect a local repo to GitHub
Create a new repo in GitHub and copy its ssh or http link. 
(example: git@github.com:M0ller/new.git )
Then write in the commandline
```
git remote add origin <ssh link>      
```
```
git remote add origin git@github.com:M0ller/demo-repo.git
```

To check the remote connection you have made write:
```
git remote -v
```

[Return to Top](#git-and-github-summary)
## Compare two branches
Display different between two branches. If you are in your master branch and want to look at the differences between it and another branch you write:
```
git diff <name of the other branch>
```

[Return to Top](#git-and-github-summary)
## Compare & Pull request on GitHub
On GitHub, you can do a “compare & pull request” to create a pull request, there you can compare two branches and then merge them together. Example; comparing myOtherBranch with master, there you can choose to create a “create pull request” and also with option to write a comment about changes.

After clicking the “create pull request” you can choose to “resolve conversation” before you click the “Merge pull request” which will finalize the merge onto master branch.

After doing that on GitHub, make sure to use a “git pull” on your local computer in the right branch, so it will also be updated.

[Return to Top](#git-and-github-summary)
## Delete a local branch
When you are done with the branch you can delete it by writing
“-d” is for delete.
```
git branch -d < name of branch to be deleted >
```

[Return to Top](#git-and-github-summary)
## Delete a remote branch
To delete a branch remotely (on your GitHub repository) you write:
```
git push origin --delete < branch name to be deleted >
```

[Return to Top](#git-and-github-summary)
## Replace a local branch with a remote branch
To replace a local branch with a remote branch you need to first 1.delete your local branch, then 2.fetch the remote branch, then 3.rebuild the local branch with the remote branch.
```
git branch -D <local branch>
git fetch origin <remote branch>
git checkout -b <local branch> origin/<remote branch>
```

[Return to Top](#git-and-github-summary)
## Merge;

If there is changes in the master branch you want to make a pull request to your local computer, so you master branch stays updated with the code that is on GitHub. Example use “git pull”.

Once you have the latest version of your master branch on your computer you might want to merge those changes into the branch that you are working on. For example, you are working on a branch called “myOtherBranch”.
You want to make sure you are in that branch first by either checking “git branch” or move to it with “git checkout myOtherBranch”.

You might want to inspect the differences between the two branches with “git diff master”
once you're done that you may want to merge the changes to your “myOtherBranch”.

Do the merge with master using. 
```
git merge master
```

If there is conflicts, you need to manually fix them. Which will be displayed, for example if you are using Vscode you can see the difference between the branches that is indicated by:
  
```
<<<<<<< HEAD
Code in your “myOtherBranch” branch
=======
Original code in your “master”  branch
>>>>>>> master
```
  
Once you have manually fixed the changes your merge is done. You can run a “git status” and see that both files are modified. You can also run a “git diff” to see the changes that is made onto both files.

Then you can do your commit to save these changes with: 
```
“git commit -am “merge with master branch”
```
After you are done you can go and check your master branch “git checkout master” and see it is still the same. If you go into your own branch “git checkout myOtherBranch” you can see you have the changes from the master branch in your “myOtherBranch” and can continue working on your project.

[Return to Top](#git-and-github-summary)
