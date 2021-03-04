# Directions for Setting up Git
In this doc we will cover basic steps for setting up Git on Windows or Mac at Deere. The only difference is the initial steps you take. Once your software is ready, connecting SSH to Git is the same for both.

## Getting started with Windows  
First we need to setup [Git Bash](https://git-scm.com/) on Windows so we can run the commands to setup SSH.  

### Downdload the software  
Lets go to [JDSRS](http://jdsrs.deere.com) and download the software we need. Go there and search for: "Git Bash". Add it to your cart and wait for the install.  

### Create an SSH directory  
`mkdir ~/.ssh`  
`cd ~/.ssh`  
`chmod 700 ~/.ssh`  

This will create the directory but also put you in that directory. Now you are ready. Please jump down to "Getting started with Git" to setup your key.  

## Getting started with Mac  
More to come...  

## Getting started with Git
* First you need to make sure you can login to [Deere Enterprise GitHub](https://github.deere.com).  
   * If you cannot, resolve that first by creating a helpdesk ticket at [Service Now](http://johndeere-servicenow.com/ep)  
* Next we want to setup an SSH key to use with GitHub.  
* Here are the instructions you will use:  
   1. [Create the key](https://help.github.com/enterprise/2.12/user/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)  
   2. [Add the SSH key to your GitHub Account](https://help.github.com/enterprise/2.12/user/articles/adding-a-new-ssh-key-to-your-github-account)  
   3. Validate your connection  
      * `ssh -T git@github.deere.com`  

# Time to celebrate, you are ready to Git

* We need to setup a user name and email that will be used to track your changes in GitHub.  
*  Using GitBash enter the below commands:  
   * `cd ~/`  
   * `git config --global user.name "[FIRST] [LAST]"`  
   * `git config --global user.email [YOUR_EMAIL]@johndeere.com`  
* We also need to ensure you have a space for all your work:  
   * `mkdir ~/bench`  
   * `cd ~/bench`  
   * From here on out, it is recommended you put all your work into bench. Each time you follow the steps below you will have a working directory in bench.
   
1. Fork: [Enterprise GitHub](https://github.deere.com)  
    * Go here for the [GitHub fork documentation](https://help.github.com/articles/fork-a-repo/)  
    * From your main repo you will click fork in the upper right and then click your RACF ID  

2. Clone: (Git Bash)
   * Open up Git Bash application  
   * `git clone git@github.deere.com:[YOUR_RACF_ID]/deere-tool-setups.git`  
   * The 'git clone url' can be found on your forked repo's github enterprise page; you want to use the SSH url.  
   * You now have the repository on your local workstation and can begin making your improvements. A few notes:  
      * By default, your forked repository on github is known to your workstation as the remote 'origin'  
      * By default, you have one local branch named 'master' which is tracking 'origin/master'  
   * Once you have cloned a repo you do not need to do it again.  

3. Change Directory: (Git Bash)  
   * Right now you are still in your "bench" folder. We need to switch to the new one you just cloned  
   * `cd [FOLDER_NAME]`  
   * FYI, if you are following this doc verbatim then your "FOLDER_NAME" will be "deere-tool-setups"  

4. Remote Add: (Git Bash)  
   * Now you are ready to add your upstream, follow the below  
   * `git remote add upstream git@github.deere.com:deeredocs/deere-tool-setups.git`  
   * `git fetch --all`  
   * This just polls your remotes for any changes that have occurred, and updates your local refs for remote branches.  

5. Branch: (Git Bash)  
   * It is a good idea to have a local (custom) branch.  
   * `git checkout -b [BRANCH_NAME] upstream/master`  
   * To list all the local and remote branches available:  
   * `git branch -a`  

6. Do some work  
   * Now you have a branch and Git Bash is checked into it. Create a new file if you need to.  
   * `touch [NEW_FILE_NAME]`  
   * You can also modify an existing file in your IDE. If you do, ensure you have a ".gitignore" file.  
   * `.idea/*`
   * Adding this to your ".gitignore" file will ensure your IDE files are not uploaded to Git. We dont need your IDE files, we have our own so do not sync them.
   * Be sure to save your work and head to step 6 below when ready.
   
7. Commit: (Git Bash)  
   * When you are ready to push to GitHub come here and follow these steps.  
   * `git add .`  
   * `git commit -am "this is my test commit"`  

8. Push: (Git Bash)  
   * `git push origin`

## How to Clean your commits  
* Rebase: (Git Bash)  
   * NOTE: If necessary... Some time may have passed since you originally created the branch.  Its time to catch up your branch to the master:  
   * `git fetch --all`  
   * `git rebase upstream/master`  
* Squash: (Git Bash)  
   * Sometimes you need to clean up your commits if you go overboard.  
   * `git rebase -i HEAD~<# of commits>`  
   * This will start an interactive process where you select which commits to keep, and which to squash. Further usage is outside the scope of this article.  
