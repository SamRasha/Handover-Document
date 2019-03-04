# Handover-Document
Document that gives a step-by-step tutorial on how to set up and use Github and JIRA/Gerrit, how to contribute and how to keep your local repository up-to-date. Also contains useful Git commands.

# A Guide to Git and Contributing to Fabric

## **Contributing through Gerrit/JIRA (and Github!)**

**Linux** Foundation ID: Create a Linux Foundation ID, you will need it.

[https://identity.linuxfoundation.org/](https://identity.linuxfoundation.org/)

When developing and contributing to Fabric, there are two important websites you need to use:

**Jira** : Where all the issues for fabric are created and maintained. This is where you will find issues to fix/create new issues for tasks you have been asked to do which currently don&#39;t have one open. You will maintain the issues created throughout development.

[https://jira.hyperledger.org/secure/Dashboard.jspa](https://jira.hyperledger.org/secure/Dashboard.jspa)

**Gerrit** : This is where the code you will be working on lies. There are many components to Fabric, all of which are available to clone through this site.

[https://gerrit.hyperledger.org/r/#/admin/projects/](https://gerrit.hyperledger.org/r/#/admin/projects/)

> ⚠ **IMPORTANT** : This cannot be stressed enough. Once having cloned a package, make sure to find the Github mirror repository (simple google search: &#39;fabric [insert] Github repo&#39;), follow the readme and do all the pre-requisites. If you do not, your code will **not** work when it is time to build your finished code to send it up, and if you are faced with &#39; **cannot find ns of null&#39;** errors, that is entirely on you (speaking from personal experience!!!).

## **Starting an issue**

**1.** Make sure you assign the issue to yourself on GitHub/Jira. Click on the issue you&#39;re picking up and add yourself as an assignee, if that has not already been done.

### **For Github:**

**2.** Go to the repository that you want to clone, and click **Fork** in the top right of the page.\
**3.** Go to **your fork** of the repository on Github and create a new branch for the issue you're picking up – the name doesn&#39;t really matter as long as you know what it means. You should be opening a new branch for every issue. Now click **clone or download* in the top right and copy the text (you can either clone with ssh or using https it doesn't matter).\
**4.** On a terminal window, use the cd command to point to the directory where you want to store your clone (e.g. cd Desktop/Repository to store it in a Repository folder on your desktop. Make sure to create the Repository folder beforehand too!). Now write **git clone** and paste the text after (e.g **git clone https://github.com/hyperledger/fabric-chaincode-node.git**)\
**5.** If you already have it cloned, it is important to keep it up to date with master as your local copy of the package most likely would have fallen behind. Refer to **Keeping in sync with master**

### **For Gerrit:**

**2.** Navigate to Gerrit, select Projects --> List, and click on the package you want to clone. Once redirected to the component&#39;s page, **make sure to select &#39;Clone with commit-msg-hook**&#39; (makes life when at the submission phase **so** much easier).\
**3.** On a terminal window, use the cd command to point to the directory where you want to store your clone (e.g. cd Desktop/Repositoriesto store it in a Repositories folder on your desktop. Make sure to create the folder beforehand too!) Copy and paste the command under **&#39;Clone with commit-msg-hook&#39;** into your terminal.\
**4.** If you already have it cloned, it is important to keep it up to date with master as your local copy of the package most likely would have fallen behind (Unless you are contributing to Composer then you don&#39;t have to worry about that!) Refer to **Keeping in sync with master**\
**5.** To create a new branch in Sync with master, which helps prevent further problems in the future when rebasing (mixed up commit hashes, some may call it coder&#39;s hell) git checkout -b newBranchName origin/nameOfMainBranch\
**6.** Open your favourite text editor, make sure you are switched to the newly created branch and start writing some code!!!

### **Opening a pull request to submit your code**

**1.** First thing I like to do is review my changes myself just to make sure I haven&#39;t left anything silly in my code. Most editors have a git view where you can see all the changed files you haven&#39;t committed yet.\
**2.** It&#39;s also good practice to make sure all the tests are still passing after making your changes. If they&#39;re not then the Travis/Jenkins build will fail, and you&#39;ll be blocked from merging your changes, so make sure to fix any broken tests.\
**3.** When you&#39;re ready to commit your changes, stage all the files you want to commit by either doing **git add nameOfFile** in Terminal or by using the git options in your editor. To stage them all, do **git add .**\
**4.** In Terminal, do git commit -s -m &#39;your commit message here&#39; (including quotations).

- **-s** signs your commit, which is important for contributing to Fabric (and contributing in general). It allows maintainers and logs to document and find out who is responsible for certain commits, should the situation arise where they need to find out/discuss something with you.
- **-m** adds a commit message to your commit. It&#39;s good to include a very brief description of what your changes include.

**5.** Make sure you code has all of master&#39;s changes, refer to **Keeping in sync with master.** Make sure to do a git commit –amendif there are any changes rather than a brand-new commit each time. This helps keep all changes under one commit, making it easier to review changes, and also keeps the commit logs clean for clarity.

### **For Github:**

**6.** When everything has been committed, do **git push** to push those changes to your fork on GitHub.

- If you&#39;ve done a rebase or amended a commit that has already been pushed, you&#39;ll get a warning saying that the remote branch and local branch have diverged. To get around this you&#39;ll have to do a force push in Terminal, by doing **git push –f**.

**7.** Go to GitHub, where it&#39;ll probably show you your recently pushed branch/branches with a big green &quot;open a pull request&quot; button. You can also open a PR by going to the Pull Requests tab and clicking the &quot;new pull request&quot; button.\
**8.** The text boxes will autofill with a title based on your branch/commits, and a template of how to write up PRs. Generally, you won&#39;t need all of that, so delete it and provide an overview of the work that you&#39;ve done and why you&#39;ve done it. It&#39;s also good practise to reference the issue that this PR addresses, by doing # followed by the issue number.\
**9.** You can request a reviewer using the dropdown on the right-hand side. GitHub will suggest reviewers to you, based on who else has contributed to the area of code that you&#39;ve been working on. Alternatively, you can ask someone in the team to review your PR for you. Either way you&#39;ll want to tell/ping the reviewer to let them know your PR is open, as it&#39;s easy to miss the email notification they&#39;ll receive if you request them.\
**10.** Once you&#39;re happy, click &quot;create pull request&quot;. Your code will at least one approving review and to pass a few checks before it can be pushed to the master branch, but your PR is now open!\

### **For JIRA and Gerrit:**

**6.** When contributing to Fabric, your message must start with the JIRA issue ID e.g. **git commit -s -m &#39;[FAB-00000] Added tests to example file&#39;**\
**7.** Once everything has been committed, simply enter git review into your terminal, and then copy paste the Gerrit link it feeds back to you in terminal into your browser to track the review.\
**8.** Make sure to add reviewers for your Code Review so that they can verify the changes you have made so they can be merged in.\
**9.** As you go through development, make sure to update your issue with the stages you are at (not the most important thing to do, but helps track progress). Make sure to accept and click **Begin Work** when starting the issue (assign to yourself if you have not already), and as you go through the development life cycle, update the status.\
**10.** Once your code has been merged in, make sure to close the issue.

### **Keeping in sync with master**

**1.** Keep an eye on how many commits are going into the master branch while you&#39;re working on your issue. If you fall too far behind, you&#39;ll find yourself in merge hell when you try catch up.\
**2.** In Terminal, do **git remote -v** to see the name of the main repository, and then do a **git fetch** from that repository's master to get the latest code (e.g. **git fetch origin master** for the **fabric-sdk-node package** ). When you do **git remote -v**, it will show the title as &#39;origin&#39;, so we get the code from the master branch in origin). To create a branch in sync with master, do **git checkout -b newBranchName origin/masterBranchName;**\
**3.** You can only do a **git rebase** if your branch is clean, i.e. there are no uncommitted changes on it.

- If you&#39;re happy with the change set you&#39;ve got you can just commit the changes that you&#39;ve made.
- If you&#39;re not ready to commit, you can do a git stashto temporarily get rid of your changes. You&#39;ll be able to get them back in a minute so don&#39;t worry

**4.** Once your branch is clean, do a **git fetch origin master**, to get the latest code from master. Once this has been done, do **git rebase origin/master**. This command gets rid of your commits that aren&#39;t on master, adds the commits that you&#39;re missing, and then adds your stuff on top of it at the end.\
**5.** You may run into merge conflicts during this process. To overcome these, view the conflicts in your editor and edit the code as necessary. Save these changes and stage the files (either through the editor or using **git add .**), and then in Terminal do **git rebase --continue** to finish the rebase.\
**6.** If you have stashed changes, do **git stash apply** to get them back. Again, there may be merge conflicts to deal with.\
**7.** Congratulations, after doing all that you&#39;re now all caught up with master.

### **Useful commands:**

- **git commit --amend** is useful if you have committed and are still working on the same issue. Again, it is good practice to not multiple commits, so amending a previous commit instead of adding a new one is pretty common.
- **git status** will show you what branch you&#39;re currently working on, how many commits ahead and behind of the remote branch you are, and how many uncommitted files you currently have.
- **git log** shows the commit log of the current branch. Useful to check that all your commits are signed before opening a PR.
- **git stash** temporarily removes all your changes, which is handy when you&#39;re rebasing or if you just want to remind yourself what the code was like before you started.
- **git stash apply** reapplies the most recently stashed change set. To apply a specific change set, use git stash apply \&lt;ID of the change set you want to apply\&gt;.
- **git stash list** shows you IDs and descriptions of all the change sets that you have stashed.
- **git add .** Stages all your changes
- **git branch** Lists all a Git project&#39;s branches.
- **git branch branchName** Creates a new branch.
- **git checkout branchName** Used to switch from one branch to another.
- **git checkout -b branchName origin/master**  Creates a new branch which is up to date with the repositories master.
- **git merge branchName** Used to join file changes from one branch to another.
- **git branch -d branchName** Deletes the branch specified.
- **git reset –-soft HEAD~** Allows you to undo the commit and change nothing more. This means getting back your staged changes you just committed, without losing anything.
- **git reset HEAD~** Similar to the above command, but on resetting it uncommits **and** unstages your changes.
- **git reset --hard HEAD~** This uncommits and gets rid of all your changes, returning it to the state it was at before you started coding on top of it.
- **git review** This is not a standard Git Command but is used when contributing to Fabric. This sends your committed changes up for code review, where maintainers and reviewers will look over your code, before deciding to merge it in or not (as long as the build passes).