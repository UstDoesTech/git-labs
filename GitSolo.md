# Starting with Git

The labs are broken down under the following headers:
- [Starting with Git](#starting-with-git)
  - [Repos](#repos)
    - [Creating a Repo](#creating-a-repo)
    - [Creating a repo in the UI](#creating-a-repo-in-the-ui)
      - [Questions](#questions)
    - [Creating a repo in the CLI](#creating-a-repo-in-the-cli)
      - [Questions](#questions-1)
    - [Cloning a Repo](#cloning-a-repo)
      - [Cloning a repo in the UI](#cloning-a-repo-in-the-ui)
      - [Cloning a repo in the CLI](#cloning-a-repo-in-the-cli)
      - [Questions](#questions-2)
  - [Ch-ch-ch-ch-changes](#ch-ch-ch-ch-changes)
    - [Making the change](#making-the-change)
    - [Staging the change](#staging-the-change)
      - [Staging in the UI](#staging-in-the-ui)
      - [Staging in the CLI](#staging-in-the-cli)
      - [Questions](#questions-3)
  - [Committing](#committing)
    - [Commit in UI](#commit-in-ui)
    - [Commit in CLI](#commit-in-cli)
    - [Questions](#questions-4)
  - [Pushing](#pushing)
    - [Push in UI](#push-in-ui)
    - [Push in CLI](#push-in-cli)
    - [Questions](#questions-5)
  - [Conclusion](#conclusion)

## Repos
A repo, or repository, is an entire collection of files and folders associated to a project, along with the revision of each file. The file history appears as development snapshots or *commits*. The *commits* exist as a linked-list relationship (insert image of linked-list) and organised into grouped lines of development called *branches*.
Repos are self-contained units and anyone with access to the repo owns a copy of the repo and the entire codebase and its history. Using the command line or a user interface allows for: 
* interaction with the history; 
* cloning;
* creating branches;
* committing;
* merging;
* comparing changes across versions of code;
* and more.

Working in repos helps keep projects organised and protected. Developers are encouraged to fix bugs, or create fresh features, without fear of interrupting development efforts. Git makes this happen through the use of branches: lightweight pointers to commits in history that can be easily created and deprecated when no longer needed.

### Creating a Repo
The are two ways of creating and initialising a repo:
* Using the User Interface in Azure DevOps
* Initialising a Repo in the Command Line Interface

### Creating a repo in the UI
1. Navigate to your project in Azure DevOps. 
2. Click **repos** and then **New repository** and give it a name. 

#### Questions
* What other options exist and why might they be used?

### Creating a repo in the CLI
1. Open up VS Code
2. Press `Ctrl+'` to open up the terminal
3. Navigate to your desired local location
4. Execute `git init my-repo` to create the repo locally where **my-repo** is the name of your repo, in your specified folder
5. Commit code into the local repo using `git add --all` and `git commit -m "commit comment`
6. Grab the URL fore the repo you created in the UI process and associate it with your local repo `git remote add origin https://Organisation@dev.azure.com/Organisation/Project/_git/Repository`
7. Push the changes from local to remote `git push origin master` 

#### Questions
* What does this approach achieve over others? 
* What could have been done differently?
* Could we have created the Repo programmatically? If so, how?

### Cloning a Repo
Cloning a repo allows you to contribute to an already initialised repo. Cloning creates a complete local copy of an existing Git repo, downloading all files, history and branches that are in the repo and establishes a named relationship with the existing repo. This means that you can interact with the existing repo, pushing and pulling changes and sharing code with your team. 

Like most of these labs, there are two ways of achieving the same result:
* Using the UI in either Visual Studio
* Programmatically through the CLI in VS Code

Which path you go down is up to you, but try to be consitent with the approach you adopt. The repo we'll be using for this is: `https://AdatisArtefactRepository@dev.azure.com/AdatisArtefactRepository/Research%20And%20Development/_git/Git-Labs.20190218` 
**NOTE: The repo mentioned is forked from Git-Labs. Please update it with a more up-to-date fork with each training** 

#### Cloning a repo in the UI
1. Open up Visual Studio
2. In Team Explorer, open up the **Connect** page by selecting the **Connect** icon, and then choose **Manage Connections**, **Connect to Project**
3. On the **Connect to a Project** dialog, select the repo you want to clone from the list and select **Clone**

#### Cloning a repo in the CLI
1. Open up VS Code
2. Press `Ctrl+'` to open up the terminal
3. Pass the URL mentioned above into the `git clone` command to make a local copy into the current active directory
   * `git clone https://Organisation@dev.azure.com/Organisation/Project/_git/Repository`
4. **Optional** To create a repo in a specific location you can pass in the folder name after the URL in the command
   * `git clone https://Organisation@dev.azure.com/Organisation/Project/_git/Repository C:\Repos\ProjectRepo` 

#### Questions
* What differences do there appear to be between the approaches?
* What benefits does one approach have over the other?

## Ch-ch-ch-ch-changes
With any development comes changes to the code base. In this section, we're going to learn how to make changes to a file; stage the changes; and commit the changes to your local repo. You can follow along using the UI or the CLI.

### Making the change
Open up your editor of choice, whether it is Visual Studio, VS Code or something else. Open up the solution folder and edit the **readme.md** file. Change the contents and save the file...

### Staging the change
Git tracks changes to a developer's codebase, but it's necessary to stage and take a snapshot of the changes to include them in the project's history. Staging is the first part of that two-step process. Any changes that are staged will become a part of the next snapshot and a part of the project's history. Staging and committing separately gives developers complete control over the history of their project without changing how they code and work.

#### Staging in the UI
1. In Team Explorer, open up the **Changes** page by selecting the **Changes** icon under the **Preoject** header
2. Under the **Changes** header, either click on the **+** or right-click on a change and select **Stage**

#### Staging in the CLI
1. Stage the change(s) using `git add .`

For a full list of `git add` commands, see the [Mastering Git Lab](GitMaster.md).

#### Questions
* What differences do there appear to be between the approaches?
* What benefits does one approach have over the other?

## Committing 
You've made a change and now you've got to commit to it. Just like any relationship, there's history. 

A Commit saves the snapshot to the project history and completes the change-tracking process. Anything that's been staged will become a part of the Commit snapshot.

### Commit in UI
1. In Team Explorer, open up the **Changes** page by selecting the **Changes** icon under the **Project** header
2. Enter in a meaningful commit comment in the **message box**
3. Click on the **Commit Staged** button

### Commit in CLI
1. Commit your staged changes using `git commit -m "meaningful comment"`

### Questions
* What differences do there appear to be between the approaches?
* What benefits does one approach have over the other?

## Pushing
Now that you've made your commitment, it's time to share it with the world. Make it public for all to see - a bit like a trashy RomCom. 

A Push takes the local commits and updates the remote repo with those changes

### Push in UI
1. In Team Explorer, open up the **Synchronisation** page by selecting the **Sync** icon under the **Project** header
2. Under the **Outgoing Commits** header, select **Push**

### Push in CLI
1. Push your committed changes using `git push`

### Questions
* What differences do there appear to be between the approaches?
* What benefits does one approach have over the other?
* What other options are available to you?

## Conclusion
Congratulations, you're now a Top Git Cat!

You're now ready to move on to the next lab and learn how to be a real team player and use [Git collaboratively](CollaborativeGit.md).
![TopGuntocat](https://octodex.github.com/images/topguntocat.png)
