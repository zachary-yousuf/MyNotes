#===Basic information regarding git and github===

###===Installation Procedure===
sudo pacman -S git
============================

###===Working with git in local repository===
1. "cd" to the project folder for which we are creating the git repository.
2. "git init" command, which will initialize the local git repository.
3. To add the user name and email id to git use the following commands:
    * git config --global user.name "your name"
    * git config --global user.email "your email"
4. "git add <file>" to add the files to the git.
5. "git add ." will add all the new files inc hat folder to the git tracking.
6. "git status" is ued to check status of the working tree.
7. "git commint -m "give the reason for the commit"" will commit the changes.
8. "git push" will be used to push the files from local repository to the remote repo.
9. "git pull" will be used to get the latest from the remote repository.
10. "git clone" will be used to clone the repository into a new directory.
11. "git rm --cached <file name>" will removed the staging area (git add applied).
12. ".gitignore" file can be used to list the files/folder that are not be added to git.
13. "git barnch <branch name>" will add a new branch to the tree.
14. "git checkout <barnch name>" will switch to the new barnch.
15. "git merge <branch name>" will merge the branch with master. Make sure you are in master before running the command.
=================================

###===Add new repository in github===
1. Login to github
2. Click on "+" at the top right side to create a new repository.
3. Give a name and description to the new repository.
4. Select public or private and click create repository.
5. Copy the repository address and execute below commands:
	* git add README.md )(Optional)
	* git remote add origin <repository address>
	* git push -u origin master
	* provide the username and password to github
==================================

======================================================
More details : https://www.youtube.com/watch?v=SWYqp7iY_Tc
======================================================
