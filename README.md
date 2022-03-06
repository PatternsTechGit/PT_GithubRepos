# Setting up Project environment in Azure DevOps & interacting with its repositories

## 1) Setting up Project environment in Azure DevOps

### What is Azure Devops? 

Azure DevOps is a Software as a service (SaaS) platform from Microsoft that provides an end-to-end DevOps toolchain for developing and deploying software.  It also integrates with most leading tools on the market and is a great option for orchestrating a DevOps toolchain. [Read More](https://docs.microsoft.com/en-us/azure/devops/user-guide/what-is-azure-devops?view=azure-devops)

> ### **STEP 1: CREATING AZURE DEVOPS ACCOUNT**
> 
> - Signup at Azure Devops from https://dev.azure.com/
> - You can login from your existing **Microsoft** Account OR  login from existing **Github** account
>
--------------------
> ### **STEP 2: SETTING-UP AN ORGANIZATION** 
>
>### What is Organization in Azure DevOps?
>
>Organization is logical grouping of related projects, and help to scale up your enterprise.
>
>
> :arrow_right: There are 2 ways of creating an organization in Azure DevOps
>  
> 1. While signing-up you will be asked to create new organization
> ![](images/31.png)
>
>  OR
>
> 1. If you already have organization, select **New Organization**
> ![](images/32.png)
>
> 2. Confirm information/name of your organization, and select **Countinue**
>![](images/4.png)
>
>Congratulations, you're an organization owner!
>Sign in to your organization at any time, https://dev.azure.com/{yourorganization}



-------------------------


> ### **STEP 3: CREATING PROJECT IN ORGANIZATION**
>
>### What is Project in an Azure Organization?
>
>A project provides a repository for source code and a place for users to plan, track progress, and collaborate on building software solutions. A project represents a fundamental container where data is stored when added to Azure DevOps.
>
> :arrow_right: We are making project for a bank (*BBBank*)
>
>  1. Give a name to your project and click **Create Project** 
>![](images/5.png)
>
------------------
>
> ### **STEP 4: CREATING REPOSITORIES IN A PROJECT**
>Azure Repos is a set of version control tools that you can use to manage your code.
>
>  :arrow_right: In this project we will 2 repositories
> 
> - One for UI
> - One for API Code
>
> Let's create one of these as a part of this lab
>Click on **New Repositories** from the Repos tab
>
> ![](images/33.png)
>
>We will name this repo **BBBank_UI** and click **Create**
> 
> ![](images/34.png)
>
> :arrow_right: WE HAVE SUCCESSFULLY CREATED A PROJECT ENVIORNMENT!
>
> :arrow_right: NOW WE WILL MOVE ON TO SECOND PART OF OUR LAB
--------------------------------------
-------------------------------------

## 2) INTERACTING WITH REPOSITORIES

> ### **STEP 1: Git and Installing git**
>
>Git is a free and open source distributed version control system. [Learn more](https://www.nobledesktop.com/learn/git/what-is-git)
>
> - Navigate to the latest [Git for Windows installer](https://gitforwindows.org/) and download the latest version.
-----------------
> ### **STEP 2: Cloning Git repository in from CLI**
>
> 1. First we will create folder for the project
> 2. We will create another sub-folder for UI project (*BBBank_UI*)
> ![](images/35.png)
>
> 3. Right Click in the folder and open the PowerShell Terminal
>![](images/36.png)  
> 
> 4. To clone our repository we will first copy the **Clone URL** from Azure Devops Portal
>![](images/37.png)
>
>5. Add copied URL after **git clone** and Run this command in the terminal
>
> ```bash
> git clone <Paste your cloned URL>
>  ```
------------
> ### **STEP 3: Create a Local branch**
>
> Branches allow you to develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository. It is good practice to create a branch and start working on it rather than making changes to Main branch.
>
> :arrow_right: To create a local branch run this command in Code Editor terminal
>
>```powershell
> git checkout -b ＜your branch name＞
>```
> :arrow_right: New branch is successfully created 
>
>![](images/38.png)

----------------

> ### **STEP 4: Open VSCODE(Code Editor) and create HTML file**
>
>1. Right click and create file with the name *index.html*
>![](images/39.png)
>
>2. Now we will create a sample page by using this HTML code.
>```html
><h1>This is my first page</h1>
>```
>3. Save the file and you can see *index.html* file in folder where you created the repository.
>![](images/43.png)

----------------------

> ### **STEP 5: Stage Changes** 
>To stage a file is simply to prepare it finally for a commit. Git, with its index allows you to commit only certain parts of the changes you've done since the last commit.
>
> :arrow_right: Run this command in terminal to *Stage all Changes*
>
> ```powershell
> git add .
>```
>This will stage all your changes.
----------------
>### **STEP 6: Check the Git Status**
> To check the status we will use this command
>
>```powershell
>git status
>```
> The current status of our folder is showing that changes are **Stagged** but not **Commited** yet
>
>![](images/40.png)
>
> 
-------------------
>### **STEP 7: Commiting Changes**
> *Git Commit* creates a commit, which is like a snapshot of your repository. These commits are snapshots of your entire repository at specific times. You should make new commits often, based around logical units of change. 
>
>Over time, commits should tell a story of the history of your repository and how it came to be the way that it currently is. Commits include lots of metadata in addition to the contents and message, like the author, timestamp, and more. 
>
>To commit your changes run
>
>```powershell
>git commit -m yourmessage
>```
>here *-m* shows the message representing what we have commited.
>When we commit, we should always include a message.
>By adding clear messages to each commit, it is easy for yourself (and others) to see what has changed and when.

------------------------------
>### **STEP 8: Pushing Changes to Server**
>
>The git push command allows you to send (or push) the commits from your branch in your local Git repository to the remote repository.
>
>To push to local server we use this command in terminal
>
>```powershell
>git push --all
>```
>:arrow_right: Now if you goto your Azure DevOps portal you will see that all your changes are pushed into server successfully.
>And you can see our newly created *index.html* file in remote branch *(Development)* in Azure Devops repository.
>
> ![](images/41.png)
 -------------------------------

 >### **NOTE: :warning: ERROR WHILE PUSHING** 
 > Those who have recently installed git may face some unforeseen error.
 > Possible cause of it is that your **username** and **email-id** is not configured in git. 
 >
 > If you face error while pushing, follow these steps
 >
 >First check the configuration by running this command
 >```powershell
 >git config --golbal --list
 >```
 >Now configure username and email id
 >```powershell
 > git config --global user.name "username"
 > git config --golbal user.email "your email id"
 >```
 >
 >After configration you can run first command again to see if it is successfully configured or not.
----------------------------
 >### **STEP 9: Pull from repository**
 >The git pull command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows.
 >
 >To pull from the repository in which changes have been made, run this command
 >
 >```powershell
 >git pull --all
 >```
 >

----------------------
------------------------
:arrow_right: Read more about [git commads](https://git-scm.com/docs)


:arrow_right: If you want to start using [Visual Studio Blog](https://devblogs.microsoft.com/visualstudio/)
