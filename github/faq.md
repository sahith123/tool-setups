 

# What should I do when my local folder is out of synch with the repo?  
In this section we will cover basic steps for updating local folder with master from Git. Can try below mentioned option1 if still having documents out of synch then try option2.    

## First try a fetch all
* `git fetch --all`  
* `ls --al`  

## Try checkout master and verify  
* `git checkout master`  
* `git pull upstream master`  
* `ls -al`  

# How do I update my origin or upstream URLs?  
The good news is you can still communicate to the new repo name. So short term you shouldn't experience any issues. But this needs to be cleaned up.  

## First I would recommend checking the status of your origin and upstream:  
* `git remote -v`  
   * You should see a "fetch" and "push" for origin and upstream so 4 items total  
   * The general format for origin is:  
      * `git@github.deere.com:[YourRACF]/[REPO_NAME].git`  
      * Ex: `git@github.deere.com:jw17731/deere-tool-setups.git`  
   * The general format for upstream is:  
      * `git@github.deere.com:[OrgName]/[REPO_NAME].git`  
      * Ex: `git@github.deere.com:deeredocs/deere-tool-setups.git`  
* If things look good you do not need to change anything  

## If something does not look correct you can update it  
Using the command git remote we can update either the origin or upstream. NOTE, be careful and make sure you are changing the right folder/repo.  

* `git remote set-url [origin/upstream] [git SSH URL]`  
* ex: `git remote set-url upstream git@github.deere.com:deeredocs/deere-opa-resources.git`  
   * This command will update the upstream to a new git URL  

# What if the repo name changed and now I have an old name in bench?  
One of the admins updated a repo name and your fork is outdated. The good news is you can still continue to push updates. But things will get confusing if you dont make an update.  

* Using Git Bash, lets rename your local folder in bench:  
   * `mv [LocalFolderName] zz-old-[LocalFolderName]`  
   * This renames your folder and will add "zz-old-" to the beginning of it  
* Go to [GitHub](http://github.deere.com) and click your profile in the upper right  
* Click on "Settings" and then click on "Repositories" on the left  
* Choose the repository which has a name mis-match  
   * This view of your repositories is nice because it will easily show anything that does not match.  
* Click on the repository with your RACF ID that has a name mis-match  
* Click on Settings toward the right side of your screen  
* Scroll down to the bottom to delete this repository  
   * Before doing anything else look at your URL and make sure your RACF is there  
   * This ensures you are deleting a fork  
* Follow the directions  
* Once done you can now go back to the [setup-git.md webpage](https://github.deere.com/deeredocs/deere-tool-setups/blob/master/setup-git.md)  
   * Follow the directions starting with creating a fork.  
* Once you get to the "Do some work" step you should be back in sync  

# What do I do if I'm ahead or behind the origin/master by "x" commits?  
First it should be noted that it is easy to get ahead of of origin/master if you are not cleaning up after making changes. The high level process is, Pull, Create a new branch, do work, commit and push, wait for merge, checkout master, pull, delete your branch, and push origin.  
   * Everytime this author of this section got ahead it was because I didn't do all of these steps and rushed my changes.  

## Determine if you are behind or ahead  
Run the commands below and review the output.  
* `git status`  
* If you are ahead or behind you should receive a message about this from the status command. Lets try a quick fix.  
* `git fetch --all`  
* `git rebase upstream/master`  
* `git status`  

If you are still ahead a simple pull may fix your issues.  
* `git pull`  
* `git status`  

If your status looks good then you should start over with a new branch. If you have changes to commit and push do that first and wait for a merge. Then delete your branch. This should ensure you dont run into the same problems. Follow [Setup-git.md](https://github.deere.com/opadocs/deere-tool-setups/blob/master/setup-git.md)  

## Still having issues?  
Go visit your cloned repo on Git Hub  
* `https://github.deere.com/[YOUR_RACF]/[REPO_NAME]`  
* ex: https://github.deere.com/jw17731/deere-tool-setups  
   * Notice the RACF ID...  
* After visiting the site if you are behind or ahead the site will tell you. There will be a message that appears right above the file list.  
   * If you dont see this message check your URL and that you are in the right place.  
* Change your branch to the name of the branch you created for your work.  
* Click the little compare button. This will take you to a separate page to help review your situation.  
   * If you get the message, "There isn't anything to compare" you can click the link.  
* From here you can create a pull request and wait for a merge. 

# SSH Key not working?  
If you have added the SSH key but still getting access denied error then execute below command & try to connect again -  
* `eval "$(ssh-agent)" && ssh-add '<SSH file location>\id_rsa'`  

# What if my branch is not fully merged?  
First take a look at what the situation is and understand where you are at. Run the following commands and review the output.  

* `git status`  
* `git log --graph --left-right --cherry-pick --oneline master...experiment`  
* If you do not feel as though you are really far behind you can delete your local branch using this command which will force the delete.  
* `git branch -D [BRANCH_NAME]`  
* The push to Origin to sync the delete  
* `git push origin :jon`  

## What if deleting my branch is not an option?  
* More help to come...  

# Error: Your local changes to the following files would be overwritten by merge  
You may receive this when trying to pull from upstream master. In some cases you may want to overwrite what you have because of new changes you dont have or other reasons.

* NOTE: this will overwrite your local folder for your repo  
   * If you are concerned about losing something copy your files first

## Stash your local repo files  
* `git checkout master`  
* `git stash save`  
* `git stash drop`  
* This saves and indexes the working state and then drops it.  
* `git pull upstream master`  
* You should now be back to the same state as github.  