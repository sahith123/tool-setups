# Git Cheat sheet to help you git more  
The following is a list of commands you can run daily to do git commits.  

## Just the commands please  
Please note explanations are below. This section is meant to be short and sweet.  

1. First you need to checkout  
   * `git checkout master`  
   * `git pull upstream master`  
   * `git checkout -b <BRANCH_NAME> upstream/master`  

2. Now that you created your local branch its time to work.  

3. Are you done working?  
   * `git add . && git commit -am "<YOUR COMMIT NOTES>" && git push origin <BRANCH_NAME> --force`  
  
4. Now its time to create a PR wait for merge.  

5. Now its time to cleanup  
   * `git checkout master`  
   * `git pull upstream master`  
   * `git branch -d <BRANCH_NAME>`  
   * `git push origin :<BRANCH_NAME>`  

6. If you fall behind you can run this command string to catchup.  
   * `git checkout upstream/master -b <BRANCH_NAME> || true;git fetch --all;git reset --hard upstream/master;git clean -xf`  

### When ready start from #1 and commit again  

## High level explanation  
There is a flow we want you to get used to.  

* First you are going to checkout and pull. Next you create a local branch.  
   * The idea behind this is you work from from your local branch and push to upstream.  
   * This enables collaboration and ensures the master stays clean.    
* Once you are done working you commit and push to upstream, and then pull to master.  
   * This submits your work and ensures peer review can take place.  
* Once your changes are merged you need to clean up your work.  
   * This is an important step that ensures you never fall behind of upstream.  
   * It can also prevent you from getting ahead of upstream.  

## The commands with further explanation  
Follow the steps below and run the commands to commit.  

1. First you need to checkout, pull, and create a local branch to work with.  
   * The purpose here is to do your work from a local branch and push that to upstream. You should never work directly on upstream.    
   * `git checkout master`  
   * `git pull upstream master`  
   * `git checkout -b <branchname> upstream/master`  

2. Now that you created your local branch its time to work.  

3. Are you done working? If so its time to commit and push.  
   * These commands are going to combine 3 steps into one. You can run them either way.  
   * `git add . && git commit -am "<COMMIT_NOTES>" && git push origin <BRANCH_NAME> --force`  
   * Or you can run each command seperately.  
   * `git add files`  
   * `git commit -am "<COMMIT_NOTES>"`  
   * Note the quotes are required above.  
   * `git push origin master`

4. Now its time to create a PR wait for merge.  
   * Go to your Github repo
   * You should see a new link which is a green button to create the Pull Request.  
   * Once you click that you need to wait for the merge.  

5. Now its time to cleanup.  
   * Run these once your changes have been merged.  
   * `git checkout master`  
   * `git pull upstream master`  
   * `git branch -d <BRANCH_NAME>`  
   * `git push origin :<BRANCH_NAME>`  
   * Note you need that colon above, do not forget it.  

6. All done. Congrats!  

## When ready start from #1 and commit again!  