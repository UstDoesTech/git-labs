# Working with Git Collaboratively

The labs are broken down under the following headers:
- [Working with Git Collaboratively](#working-with-git-collaboratively)
  - [Branching](#branching)
    - [Creating a Branch in the UI](#creating-a-branch-in-the-ui)
    - [Creating a Branch in the CLI](#creating-a-branch-in-the-cli)
    - [Remaining tasks](#remaining-tasks)
    - [Questions](#questions)
  - [Keeping It Fresh](#keeping-it-fresh)
    - [Fetch](#fetch)
      - [Fetch in the UI](#fetch-in-the-ui)
      - [Fetch in the CLI](#fetch-in-the-cli)
      - [Questions](#questions-1)
    - [Merge](#merge)
      - [Merge in the UI](#merge-in-the-ui)
      - [Merge in the CLI](#merge-in-the-cli)
      - [Questions](#questions-2)
    - [Pull](#pull)
      - [Pull in the UI](#pull-in-the-ui)
      - [Pull in the CLI](#pull-in-the-cli)
  - [Merge Branches](#merge-branches)
    - [Merging using the UI](#merging-using-the-ui)
    - [Merging using the CLI](#merging-using-the-cli)
    - [Questions](#questions-3)
  - [PR](#pr)
    - [Creating a Pull Request](#creating-a-pull-request)
    - [Reviewing a Pull Request](#reviewing-a-pull-request)
    - [Complete a Pull Request](#complete-a-pull-request)
    - [Questions](#questions-4)
  - [And Repeat](#and-repeat)
  - [Conclusion](#conclusion)

The file(s) we'll be working with can be found in the Co-Lab folder. Make sure you've cloned the Repo to your local environment. If you've forgotten how to clone a repo, do refer to the lab that deals with [cloning repos](GitSolo.md#cloning-a-repo).

## Branching
Git branches are references that keep a history of commits. Creating a branch does not affect other branches, and you can share branches with others without merging back into the main project. Create new branches to isolate changes for a feature or a bug fix from your master branch.

Adatis works with trunk based branching with the aim to get code into master as quickly as possible from the feature branches. The aim is to encourage small chunks of code to be developed at any one time. This makes it:
* Easier to code review
* Simpler to ship

### Creating a Branch in the UI
1. Open Visual Studio
2. Open up Team Explorer and go to the **Branches** view.
3. Right-click the master branch to base your changes and choose **New Local Branch From**
4. Supply a branch name in the required field and click **Create Branch**. Visual Studio automatically performs a checkout to the newly created branch.

### Creating a Branch in the CLI
1. Open up your CLI editor of choice - This Lab has been put together on VS Code
2. Use `git branch feature1` - where 'feature1' is the name of your branch
3. Use `git checkout feature1` to swap to your newly created branch

### Remaining tasks
To complete this lab, complete the following tasks:
* Make a change
* Commit the change
* Push the change to the remote server
  * For CLI users, it may be safer to use additional parameters in your command: `git push --set-upstream origin feature1`

### Questions
* What is the benefit of using `checkout`?
* What benefit does automatic checkout provide? Are there any risks?
* Why might you want to specify the branch name in the CLI push?

## Keeping It Fresh
When working as part of a team, it's important to keep your code fresh and not let it get stale. Staleness is the first sign of decay.

To keep your code fresh and up-to-date, we're going to employ help from the Git concepts of:
* Fetch - grabs changes from the remote but doesn't apply changes
* Merge - applies changes from Fetch to your local repo (not to be confused with Branch Merging)
* Pull - Does a Fetch and a Merge

### Fetch
Fetch downloads the code from the remote to your local branch. It also grabs all the commits and new branches that others have pushed and downloads them into your local repo (creating local branches as needed).

Remember, Fetch doesn't apply any changes - it just retreives them for you to review. Who's a good boy? Fetch is a good boy!

#### Fetch in the UI
1. In Team Explorer, open up the **Synchronisation** page by selecting the **Sync** icon under the **Project** header
2. Choose **Fetch** from the **Incoming Commits**
3. Review the changes

#### Fetch in the CLI
1. Fetch the changes using `git fetch`
2. Review the changes

#### Questions
* What does the other **Fetch** do in the UI?
* What would happen if there's a change that doesn't look right?

### Merge
Merge applies the changes that were retreived from Fetch. Merge takes the commits and tries to add them to your local branch. Merge will keep the commit history of local changes so that when you push your changes, Git will know how others should merge your changes. 

#### Merge in the UI
1. In Team Explorer, open up the **Synchronisation** page by selecting the **Sync** icon under the **Project** header
2. Choose **Sync** from the tab at the top of the page

#### Merge in the CLI
1. Use `git merge` to bring in the changes

#### Questions
* What other action does **Sync** perform, other than merge?
* How can we replicate **Sync** in the CLI?

### Pull
Pull does a Fetch and a Merge, updating your local repo in one command rather than two. Use **Pull** to quickly update your repo if you aren't worried about not reviewing the changes. 

#### Pull in the UI
1. In Team Explorer, open up the **Synchronisation** page by selecting the **Sync** icon under the **Project** header
2. Choose **Pull** to fetch remote changes and merge them into your local branch - there are two options, you can use either

#### Pull in the CLI
1. Use `git pull` to fetch and merge the changes

## Merge Branches
You've made all your changes in your feature branch and you're confident that it all works. How do you get it into the master branch - knowing that the master branch has moved on since you took a branch off it?

There are two approaches - rebasing and merging - to keep things simple, we're going to start by introducing you to merge. Merge, unsuprisingly, merges changes from a source branch (master) into a target branch (e.g. feature1) using a merge commit, which becomes part of your commit history.

### Merging using the UI
1. Open the **Branches** view in **Team Explorer**. Ensure your desired target branch is checked out, right-click the target branch, and choose **Merge From**
2. Specify the desired **Merge from branch**, which is `master` in this example, and choose Merge
3. Enter a commit message and select **Commit Staged**
4. When you are ready to push your local commits, including your new merge commit, to the remote server, choose **Push** from the Synchronization view

### Merging using the CLI
1. Use `git checkout feature1` to ensure your feature branch is checked-out
2. Pull the latest code from master with `git pull origin master`
3. Push the merge commit changes using `git push`

### Questions
* What happens if you get a conflict when you merge?
* How would you go about resolving a conflict?

## PR
Have you ever experienced the shame of sharing code that doesn't work and ultimately breaks the solution? Has this ever caused you bad PR?

With Git, you can reduce bad PR by using Pull Requests (PR) to get your code reviewed and approved before it is pulled into the `master` branch and realises its potential as shippable code. 

A PR, once it's been reviewed and approved, will issue a Pull (Merge Commit) to the `master` branch.

### Creating a Pull Request
1. Open up Azure DevOps and navigate to **Repos** 
2. Create a PR for the branch. You can do this in the Code view on the web from either the Pull Requests tab or the Files tab
3. Give a clear title for the PR that describes the changes in the branch
4. In the description field give a clear explanation of how the changes are implemented along with any resources that might help reviewers understand the changes. You can include work items and hyperlinks to allow others to have as much context as possible when reviewing your changes
5. Add any team member who you would like to review the changes

### Reviewing a Pull Request
PR reviewers will see the proposed updates to the branch in the form of file differences between the two branches. Reviewers can add comments on any of the changes and include notifications for other team members to answer a question or give other feedback. You can make changes and push commits to resolve issues brought up in the feedback and these changes are immediately reflected in the PR.

If the changes need much more development to complete, you can abandon the PR. You can later open up a new PR to revisit the changes and link to the conversations that took place in the abandoned PR.

You can also open up a PR on a very early version of your code to ask for feedback from others, even if the code isn't ready to merge yet. Once you get the team's feedback, you can keep the PR open to continue the conversation or abandon the PR until your code is ready to be shared again.

### Complete a Pull Request
1. Complete the PR by selecting **Complete** in the upper right of the Pull Request window. 
2. Enter the message used for the merge commit and update the PR description as needed in the dialog that follows

### Questions
* What options are available to you when you complete the PR?

## And Repeat
Repeat this exercise until every member of the team has shared and reviewed code. 

## Conclusion
Congratulations! You've just completed the Co-Lab and can now go out into the big bad world and dominate it by working with others. 

![Collabocats](https://octodex.github.com/images/collabocats.jpg)

The world is your oyster and there's a couple of labs you can continue to work on, if you so wish. 
* Figure out what to do when the [Grim Repo](GrimRepo.md) comes for your code and things go wrong...
* You've got the basics of Git under your belt and you are growing in strength in Git. But how do you become a [Git Master](GitMaster.md)?

