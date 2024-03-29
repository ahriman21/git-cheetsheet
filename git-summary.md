## add your name and email to git :
```
git config --global user.name "x"
git config --global user.email "x"
```

## how to see the configs on your git :
```git config --list```

## If you want git to track your files or a project (add git to your project) :
```git init```

## 3 stages of git :
* unstaged(working directory): firstly in your project, when a file is added or something is changed git marks them as untracked files.
* staging area: if you want git to track the new files or new changes, you can use `git add file_name`.
* commit: if you want to submit(commit) the new files or the new changes, you can use `git commit -m "the description you want to write about the new files or new changes"`.

## to see the status of tracked files (the status of files):
```git status```

## Send files from the staging area back to unstaged :
if you want to send back the files that are in the staging area to the unstaged area you can use this command:
```git restore --staged file_name```

## List the commits :
if you want to see the details info of your past commits :
```
git log
git log --oneline
git log --stat

```
note: in the result of these commands, if you see the word `HEAD` in front of a commit it means that commit is the last commit

## branch :
it is common that if you want to add changes to your project, you should make a copy of it and work on the copy, not the main file.
in git, we can do this by making a new branch of the project and working on the branch and if it is satisfying you can merge it with the main file (main branch), 
otherwise you can delete the branch.

* to list all branches :
  ```
  git branch
  git branch --list
  ```

* to make a new branch :
    ```
    git branch branch_name
    ```

* to go into another branch (go from the main branch to the new one ):
  ```
  git checkout branch_name
  ```  
> !!note!! : if you are in branch 'a' and you have not committed yet and change the branch to 'b' the new changes will go from branch 'a' to branch 'b'. so be careful not to do that.  
  
* edit a branch's name :
```
git  branch  -m  branch_name  new_branch_name
``` 

* delete a branch :
```
git  branch  -d  branch_name
```

## merging branches :
if you are satisfied with the changes, you can merge them with the main branch. to do that you must first activate the main branch and then merge with other branches.
```
git merge branch_name  
```

## checkout (a weak command to back to past commits) :
if you want to go back to review a commit in the past through your logs (for instance you want to review two previous versions of a file that you have committed).
you can even make changes in the commit that you are reviewing by checkout command and commit it, but when you go to main again, the changes will be discarded.
```
git checkout commit_id
```
after reviewing, you can go back to the main by the following command
```
git checkout main
```

## revert (another command to go back to past commits) :
by using this command you can discard the changes of a commit. for instance, you have 4 commits, you don't want the last one so you can get the ID of the commit and use it in the following command :
```
git revert commit_id
```
> This command won't remove the selected commit. it only discards the changes of the commit.
> When you utilize the revert command to go several commits back, more likely you will encounter conflicts. so you should use it when you want to revert the last commit.

if you encounter conflicts you will have two choices:
* cancel revert :
```
git revert --abort
```
* continue revert :
```
git revert --continue
```

## reset (the last command to back to past commits) :
reset has 3 types.
* --soft ==> It is going to move the files from the commit area to the staging area.
* --mixed ==> It is going to move the files from the commit and staging area to the unstaged area.
* --hard ==> It is going to remove the changes completely. so you won't access those changes again.

```
git reset commit_id --soft
```
note that the commit's ID or commit's hash you choose is the last commit you want to keep and all commits that are on top of the chosen commit will be impacted.


## stash :
you can save your changes without committing. for example, you are working on a feature and you realize that you must have done another feature before that.
so you can make a stash (you don't need to add the changes to the staging area).

* how to stash your changes :
```
git stash save "your comment on the stash"
```

* See the list of stash :
```
git stash list
```

* go for the stored stash :
```
git stash apply stash_id
```

> stash id is displayed in `{}`

* Remove your stash list :
```
git stash clear
```

## gitignore (to determine some files not to track and not to commit) :
you can determine some files not to be tracked. to do that first, you create a file named `.gitignore` and then put the path of the files you want to ignore in the .gitignore
* linux
```
touch .gitignore
```
* windows
```
echo.> .gitignore
```
> you can use `https://www.toptal.com/developers/gitignore` to generate gitignore files related to the programming language you are using.
## ssh-key :
An SSH key, also known as a Secure Shell key, is a pair of cryptographic keys used for secure communication over the SSH protocol. SSH keys are widely used for accessing remote servers and repositories, such as GitHub, without having to enter your password every time.

## how to create a ssh key for your GitHub account :
linux :
* open your terminal and enter command `ssh-keygen`. it will ask you to enter a path and a passphrase, but you can leave them empty.
* by default it will be stored in `/home/uername`
* there is a hidden directory named `.ssh` in `/home/username`.
* there are 3 files in it. you can use the value of `id_rsa.pub` in web services like github. another file is `id_rsa` that is private.
* now you should add the private ssh-key to your ssh-agent :  1-enter command `eval "$(ssh-agent -s)"`  2- enter `ssh-add ~/.ssh/id_rsa`
* to use it in github go to `settings > ssh keys and gpg keys` click `on new ssh key` and put your ssh key.

  > you can see detailed information in `https://docs.github.com/authentication/connecting-to-github-with-ssh`


## push your files to github (upload your projects in github):
1- first way of pushing
```
git push url_of_your_project_in_github branch_name  
```
2- second way of pushing
```
git remote add origin url_of_your_project_in_github
git push -u origin branch_name
```
3- see the information about your origins :
```
git remote -v
```

## conflict (when two developers make changes in the same file)
for example we have dveloper1 and developer2 and a file named main.py
developer1 changes the first line of main.py to 'import x'
developer2 changes the first line of main.py to 'import y'

now they push the project and get into conflict. To solve the conflict, use `git pull origin main`. this command brings both changes to the local repository of developer and developer can decide which code should be there. after that developer should commit the change and push it to the repository.

## fork
when you want to contribute with other's repository you can fork their repository by clicking on `fork` option beside the name of repository name.
by forking another repository, the repository will be displayed in your github account.
now you can clone the repository from your github and apply your changes. remember, you must create a branch and make the changes in your own branch.
after that, you can commit the changes and push it to your forked repository. Remember you must push the new branch that you created.
finally you can click the `compare & pull request` option beside your forked repository, this will send the changes to the original owner of the repository.


## issue
if you have a question or suggestion for the owner of a repository in github you can make an issue by clicking on `issues` tab and then `new issue` button.
the owner can choose a label for your issue. and also he can close the issue after resolving it.


## detached head
* head :
head always points to the latest commit. the latest commit that has taken place in our branches.

* detached head :
when the head directly points to a commit that is not the latest commit. to do that you can use `git checkout <commit hash>`. why it is essential to know about it? because with this operation we can move back to old versions of a project.

the point is sometimes you need to go back to old versions and make some experimental changes, if you aren't satisfied with those changes in an old commit, you can leave it there and go to another commit. so those changes you made will disappear and won't be considered.

in other scenarios, you may want to go back to an old version or commit to your project and start to make changes and you want to keep them, so, in this case, you can make a branch out of it and later merge the main branch with that new branch by this command `git branch <new branch name>`


## git pull VS git fetch :
`git pull` will get the new files or modified files from the remote repository in your local repository and merge them to your main branch immediately.
On the other hand `git fetch` also gets the new files or modified files from your remote repository and puts those in your working directory, so in this case, you should decide to merge files.


## git cherry-pick command :
suppose you are working on a branch named `dev` and you realize that you need to transport one or some commits from branch `dev` to branch `main` and you don't want to use git merge. so you can select the `commit hash` of the wanted commit go to the branch `main`(the destination branch) and issue the command below :
`git cherry-pick <commit hash>`
