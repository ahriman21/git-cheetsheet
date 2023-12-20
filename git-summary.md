## add your name and email to git :
```
git config --global user.name "x"
git config --global user.email "x"
```

## how to see the configs on your git :
```git config --list```

## if you want git to track your files or a project (add git to your project) :
```git init```

## 3 stages of git :
* unstage : firstlyl in your project, when a files is added or a something is changed git marks them as untracked files.
* staging area : if you want git to track the new files or new changes, you can use `git add file_name`.
* commit : if you want to submit(commit) the new files or the new changes, yo can use `git commit -m "the description you want to write about the new files or new changes"`.

## to see the status of tracked files (the status of files):
```git status```

## send files from stagin area back to unstage :
if you want to send back the files which are in staging area to the unstage area you can use this command:
```git restore --staged file_name```

## list the commits :
if you want to see the details info of your past commits :
```
git log
git log --oneline
git log --stat

```
note : in the result of these commands, if you see the word `HEAD` infront of a commit it means that commit is tha last commit

## branch :
it is common that if you want to add changes to your project, you should make a copy of it and work on the copy not the main file.
in git we can do this by making a new branch of project and work on the branch and if it was satisfying you can merge it with the main file (main branch), 
ohterwise you can delete the branch.

* to list all branches :
  ```
  git branch
  git branch --list
  ```

* to make a new branch :
    ```
    git branch branch_name
    ```

* to go into another branch (go from main branch to the new one ):
  ```
  git checkout branch_name
  ```  
> !!note!! : if you are in the branch 'a' and you have not commited yet and change the branch to 'b' the new changes will go from branch 'a' to branch 'b'. so becareful not todo that.  
  
* edit a branch's name :
```
git  branch  -m  branch_name  new_branch_name
``` 

* delete a branch :
```
git  branch  -d  branch_name
```

## merging branches :
if you are satisfied with the changes, you can merge them with the main branch. to do that you must first active the main branch and then merge with other branches.
```
git merge branch_name  
```

## checkout (a weak command to back to past commits) :
if you want to goback to review a commit in the past through your logs (for instance you want to review two previous versions of a file thaat you have commited).
you can even make changes in the commit that you are reviewing by checkout command and commit it, but when you go to main again, the changes will be discard.
```
git checkout commit_id
```
after done reviewing, you can go back to the main by following command
```
git checkout main
```

## revert (another command to go back to past commits) :
by using this command you can discard the changes of a commit. for instance you have 4 commits, you don't want the last one so you can get the ID of the commit and use it in this following command :
```
git revert commit_id
```
> this command won't remove the selected commit. it only discads the changes of the commit. so the commit will be shown on the result of log command.  
> when you utilize revert command to go several commits backc, more likely you will encounter with conflicts. so you should use it when you want to revert the last commit.

if you encounter conflicts you will have two choises :
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
* --soft ==> it is going to move the files from commit area to staging eara.
* --mixed ==> it is going to move the files from commit and staging area to unstaged area.
* --hard ==> it is going to remove the changes compeletely. so you won't access those changes again.

```
git reset commit_id --soft
```
note that the commit's id or commit's hash you choose is the last commit you want to keep and all commits that are on top of the chosen commit will be impacted.


