# Create your first repo

## Requirements

- You have a github account (or a gitlab account if you prefer).
- If you are using Windows, you have installed Git Bash or WSL2. (If you're using Linux or MacOS, git is probbaly already installed.)
- You have generated your SSH keys and added the public key to your github account. (If you haven't done this yet, please follow the instructions in the previous section.)

## Creating a new repository

Let's create a repo called **"my_first_repo"** on github.com.

There are two ways to create a new repository :

- Starting on your computer (the local way) or starting on github.com (the remote way). In this exercise, we will use the remote way and start on github.com because it's slightly easier to do it this way.

1. **Create a new remote repository**:
   Go to your github account and click on the "+" icon in the top right corner. Then:

   - Select "New repository".
> [!NOTE]
> A "repository" is a "place" where your project lives. It can be public or private. A public repository is visible to everyone, while a private repository is only visible to you and the people you choose to share it with.

   - Fill in the repository name, description (optional), and choose public.
   - Choose to initialize the repository with a README file
>[!NOTE]
> Initializing the repository with a README file means that the repository will not be empty because one file will be created. It is easier to manipulate.

   - Choose a license (optional).
   - Choose the python .gitignore template.

1. **Copy the SSH URL**:
   Once the repository is created, you will be redirected to the repository page. You will see a green button that says "Code". Click on it and copy the SSH URL (it should look like `git@github.com:username/my_first_repo.git`).

2. **Clone the repository**:
   Open your terminal (Linux/MacOS) or Git Bash (Windows) and navigate to the directory where you want to clone the repository. You don't have to create a new directory, git will do it for you. If you have "code" directory, you can just go to "code" and run the following command (of course, replace `<SSH_URL>` with the SSH URL you copied in the previous step):

   ```bash
   git clone <SSH_URL>
   ```  
> [!NOTE]
> It is a good practice to have a "code" directory where you put all your code projects. Make sure this repo is not in the scope of tools such as Google Drive, OneDrive, Dropbox, ICloud, etc. because they can interfere with git. A common place is `~/code` on Linux/MacOS or `C:\Users\<username>\code` on Windows.

   Nice! You have just created your first repository on github.com and cloned it to your computer. Now you can start working on your project!

> [!TIP]
> If you are struggling with ssh keys, you can use the HTTPS URL instead of the SSH URL.

1. **Navigate to the cloned repository**:
   Once the repository is cloned, navigate to the newly created directory:

   ```bash
   cd my_first_repo
   ```

   And then open the folder using your favorite code editor (VSCode, PyCharm, etc.). If you are using VSCode, you can run the following command:

   ```bash
   code . 
   ```
   But, of course, you can also just launch VSCode and open the folder manually (File > Open Folder... or ctrl+K ctrl+O).

2. **Create a new file**:
   Create a new file called `hello.py` and add the following code:

   ```python
   print("Hello, world!")
   ```

> [!NOTE]
> To create a new file in VSCode, you can right-click on the folder in the Explorer panel and select "New File", or you can use the shortcut `Ctrl+N` (Windows/Linux) or `Cmd+N` (MacOS) and then save the file with the desired name.
> Or you can also use the terminal to create a new file using the `touch` command (Linux/MacOS) or `type nul >` command (Windows).

1. **Modify the README file**:
   Open the `README.md` file and add a description of your project. For example:

   ```markdown
   # My First Repo

   This is my first repository on GitHub. It contains a simple Python script that prints "Hello, world!".
   Also I modified the README file locally, so there are two versions of the file now. One is stored on github.com and the other is stored locally.
   ```

1. **Check the status of the repository**:
   Now that you have created a new file and modified the README file, you can check the status of the repository using the following command:

   ```bash
   git status
   ```

   You should see something like this:

   ```text
   On branch main
   Your branch is up to date with 'origin/main'.

   Changes not staged for commit:
     (use "git add <file>..." to update what will be committed)
     (use "git restore <file>..." to discard changes in working directory)
           modified:   README.md

   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           hello.py

   no changes added to commit (use "git add" and/or "git commit -a")
   ```
   Git says you have files which is tracked  and has been modified (the README file) and files which is not tracked (the hello.py file). Let's add both to the stagin area.

> [!NOTE]
> The staging area is a place where you can prepare your changes before committing them. You can add files to the staging area using the `git add` command. You can also remove files from the staging area using the `git restore --staged` command.

1. **Add the files to the staging area**:
   To add the files to the staging area, run the following command:

   ```bash
   git add README.md hello.py
   ```
   Don't forget you can use the autocomplete feature of your terminal to avoid typing the full file names. 

   Now do `git status` again and you should see something like this:

   ```text
   On branch main
   Your branch is up to date with 'origin/main'.
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
              modified:   README.md
              new file:   hello.py
    ```
> [!NOTE]
> You can also add all the files in the current directory and its subdirectories to the staging area using the following command `git add .` (the dot means "current directory"). But be careful, this will add all the files, including the ones you don't want to commit. So it's not considered a good practice to use this command. It's better to add the files one by one or use a pattern to add only the files you want to commit.

1. **Commit the changes**:
   Now that the files are in the staging area, you can commit the changes using the following command:

   ```bash
   git commit -m "First commit"
   ```

   The `-m` flag allows you to add a commit message inline. The commit message should be a short description of the changes you made.

> [!NOTE]
> A commit is like a snapshot of your project at a specific point in time. It allows you to go back to that point in time if you ever need to. You can also think of a commit as a save point in a video game. You can have multiple commits in your project, and each commit has a unique identifier (a hash) that allows you to refer to it later.

1. **Push the changes to the remote repository**:
   Now that you have committed the changes, you can push them to the remote repository using the following command:

   ```bash
   git push
   ```
   But the first time you push to a remote repository, you sometimes need to specify the remote name and the branch name. The default remote name is `origin` and the default branch name is `main`. So the command should be:

   ```bash
   git push origin main
   ```

   The `origin` is the default name for the remote repository and `main` is the name of the branch you are pushing to. If you are using a different branch, replace `main` with the name of your branch.

   Also maybe git its going to prompt you saying you need to configure your username and email. If so, run the following commands:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```
   (Of course, replace "Your Name" and "your.email@example.com" with your actual name and email.)

1. **Check the remote repository**:
   Now that you have pushed the changes to the remote repository, you can check the repository on github.com. You should see the `hello.py` file and the modified `README.md` file!

   ## Create a new branch and make changes

   Working with git is not only about creating a new repository and pushing changes to it. It's also about creating branches, making changes, and merging them back to the main branch. Let's create a new branch and make some changes to the `hello.py` file.

   Branches are useful when you want to work on a new feature or fix a bug without affecting the main branch. You can create a new branch, make changes, and then merge the changes back to the main branch when you're done.

1. **Create a new branch**:
   To create a new branch, run the following command:

   ```bash
   git checkout -b my_new_branch
   ```
   The `-b` flag tells git to create a new branch and switch to it. The name of the new branch is `my_new_branch`. You can choose any name you want for your branch, but it's a good practice to use a descriptive name that reflects the purpose of the branch.

1. **Make changes to the `hello.py` file**:
   Now that you are on the new branch, open the `hello.py` file and modify it to print your name instead of "Hello, world!". For example:

   ```python
   print("Hello, this line has been added from the new branch!")
   ```

1. **Add and commit the changes**:
   Now that you have made changes to the `hello.py` file, you can add and commit the changes using the following commands:

   ```bash
   git add hello.py
   git commit -m "Modified hello.py to print my name"
   ```

1. **Push the changes to the remote repository**:
   Now that you have committed the changes, you can push them to the remote repository using the following command:

   ```bash
   git push origin my_new_branch
   ```

   This will create a new branch on the remote repository with the same name as your local branch. Once you've run this command once, you can just run `git push` in the future to push changes to the same branch.

## Make a modification on the main branch

Now that you have made changes to the `hello.py` file on the `my_new_branch` branch, let's switch back to the main branch and make a modification to the `hello.py` file. This will create a conflict when we try to merge the changes from the `my_new_branch` branch to the main branch.

```bash
git checkout main
```

Now edit the file `hello.py` to print "Hello from the main branch!" instead of "Hello, this line has been added from the main branch!". For example:

```python
print("Hello from the main branch!")
```

Then, add and commit the changes using the following commands:

```bash
git add hello.py
git commit -m "Modified hello.py on the main branch"
git push
```

It's time to create conflict!

## Merge the changes back to the main branch

You have two main options to merge the changes back to the main branch: you can either create a pull request on github.com or you can merge the changes locally and then push them to the remote repository.

In this exercise, we will use the method we've seen in the first chapter and let github doing it for us. (Open the image in a new tab to see it better.)

1. **Create a pull request**:
   Go to your repository on github.com and you should see a message saying "Compare & pull request". Click on it and then click on the "Create pull request" button. You can add a description of the changes you made and then click on the "Create pull request" button again.

1. **Merge the pull request**:
   Once the pull request is created, you can merge it by clicking on the "Merge pull request" button and then click on the "Confirm merge" button. This will merge the changes from your branch to the main branch.

1. **Update your local main branch**:
   Now that you have merged the changes to the main branch on github.com, you need to update your local main branch. To do this, switch to the main branch and pull the changes using the following commands:

   ```bash
   git checkout main
   git pull
   ```

1. **Update and/or delete the branch**:

   Now that your local main branch is up to date with the remote main branch, you have the choice to delete the branch or keep it to keep working on it.
   
   - If you still want to use it, you can just switch to it using the following command:

   ```bash
   git checkout my_new_branch
   ```

   And then keep working on it.

   - If you want to delete the branch, you can do it on github.com by clicking on the "Delete branch" button. This will delete the branch from the remote repository, but it will still exist on your local machine. You can delete it locally using the following command:

   ```bash
   git branch -d my_new_branch
   ```
   
> [!NOTE]
> Should we delete the branch? Not really, it depends on the working conventions of your team. Sometimes we like to keep the branch around for future reference or to continue working on it. But, at some point, it's a good practice to delete branches that are no longer needed to keep the repository clean and organized. When you delete a branch, you are not deleting the commits that were made on that branch. The commits will still exist in the main branch after the merge.

## Resolving conflicts

The last thing we will see in this exercise is how to resolve conflicts. A conflict occurs when two branches have made changes to the same line of code or when one branch has deleted a file that another branch has modified. When this happens, git will not be able to automatically merge the changes and will ask you to resolve the conflict manually.

1. **Create a conflict**:
   To create a conflict, we will modify the `hello.py` file on the main branch and then try to merge the changes from the `my_new_branch` branch. First, switch to the main branch (using the command `git checkout main`) and modify the `hello.py` file to print "Hello from the main branch!". For example:

   ```python
   print("Hello from the main branch!")
   ```

   Then, add and commit the changes using the following commands:

   ```bash
   git add hello.py
   git commit -m "Modified hello.py on the main branch"
   git push
   ```

   Then, switch to the `my_new_branch` branch (using the command `git checkout my_new_branch`) and modify the `hello.py` file to print "Hello from the new branch!". For example:

   ```python
   print("Hello from the new branch!")
   ```

   Then, add and commit the changes using the following commands:
   
   ```bash
    git add hello.py
    git commit -m "Modified hello.py on the new branch"
    git push
    ```

You have now created a conflict because both branches have modified the same line of code in the `hello.py` file. Now, let's try to merge the changes from the `my_new_branch` branch to the main branch on github.com.

1. **Create a pull request**:
   Go to your repository on github.com and you should see a message saying "Compare & pull request". Click on it and then click on the "Create pull request" button. You can add a description of the changes you made and then click on the "Create pull request" button again.

    The pull request will show a message saying "This branch has conflicts that must be resolved". Click on the "Resolve conflicts" button and you will see the conflicting file with the changes from both branches. You can either :
    - edit the file to resolve the conflict and then click on the "Mark as resolved" button. 
    - Or resolve locally by editing the file and then committing the changes.

   Most of the time, you will want to resolve the conflict locally because it gives you more control over the changes.

1. **Resolve the conflict locally**:
   To resolve the conflict locally, switch to the main branch and pull the changes from the remote repository using the following commands:

   ```bash
   git checkout main
   git pull
   ```

   Then, merge the changes from the `my_new_branch` branch using the following command:

   ```bash
   git merge my_new_branch
   ```

   Git will show a message saying "Automatic merge failed; fix conflicts and then commit the result." This means that there is a conflict that needs to be resolved. Open the `hello.py` file and you will see something like this:

   ```python
   <<<<<<< HEAD
   print("Hello from the main branch!")
   =======
   print("Hello from the new branch!")
   >>>>>>> my_new_branch
   ```
   To resolve the conflict you can use vim, nano, or any other text editor you like. But it's way easier to use a code editor like VSCode because it has a built-in merge tool that makes it easy to resolve conflicts. In VSCode, you will see the conflicting lines highlighted and you can choose which version of the code you want to keep. You can also edit the file to create a new version of the code that combines the changes from both branches.

   Once you have resolved the conflict, save the file and then commit the changes using the following commands:

   ```bash
   git add hello.py
   git commit -m "Resolved conflict in hello.py"
   git push
   ```
1. **Check the remote repository**:
   Now that you have resolved the conflict and pushed the changes to the remote repository, you can check the repository on github.com. You should see the `hello.py` file with the changes from both branches.

# Conclusion

Through this exercise, you have learned how to create a new repository on github.com, clone it to your local machine, create a new branch, make changes, and merge the changes back to the main branch. You have also learned how to resolve conflicts when two branches have made changes to the same line of code.

Working with git seems a bit overwhelming at first, but with practice, it will become second nature. The more you use git, the more comfortable you will become with its commands and workflows. Don't be afraid to experiment and make mistakes, because that's how you learn.

In this tutorial we used the command line interface (CLI) to interact with git, but there are also graphical user interfaces (GUIs) that make it easier to work with git. Some popular GUIs are GitHub Desktop, Sourcetree, and GitKraken. You can also use the built-in git support in VSCode or PyCharm.

But a good data scientist or developer should know how to use git from the command line because it gives you more control over the changes you make, allows you to automate tasks using scripts and can be used if you are working on a remote server without a GUI.