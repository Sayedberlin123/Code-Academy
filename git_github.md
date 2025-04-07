# Git & GitHub

## Git

**Git** is what is known as a **version control system**. When you're working on a project, Git will keep track of all your **commits**, ie. changes. If something goes terribly wrong, you can revert back to a previous version without much issue. When working collaboratively, Git will let you create branches off of a main project so you can make changes in a private, safe environment where you won't affect any of your collaborators. When your feature is ready, you can merge it back into the main branch and everyone will be able to pull those changes into their own environments! It also makes working from multiple devices possible: push your changes from your work/school device, and pull them to your home device to continue working. For more info, you can visit the [Git Docs](https://git-scm.com/doc).

If it isn't already installed on your computer, you'll need to do that first. [Here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) are some in-depth instructions. I will assume you've already created a GitHub account.

---

### Creating a Repository

Let's track your first project using Git! [Here](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository) is a great beginners' guide. Let's follow the steps:

1. **Initialize a Repository**: open your project in VSCode, make sure you're in the root folder. You can use `cd` ("change directory") command from the terminal to navigate between folders, then type into the terminal:

   ```shell
   git init
   ```

   Your project folder is now being **tracked** by Git. Check the status by typing into the terminal:

   ```shell
   git status
   ```

2. **Stage files**: to track new files, or update an existing file, you use the `git add` command to add it to the staging queue. You can be specific by giving the name/s of file/s you would like to add, or you can be general by typing:

   ```shell
   git add .
   ```

   The period indicates to Git to **stage** _all_ new/updated files.

---

### GitIgnore

Not all of your files need to be pushed to GitHub - large files, or sensitive information, should be omitted from the tracker. You can achieve this with a `.gitignore` file, you will give it the names of the files and folders you wish to be ignored. The gitignore [documentation](https://git-scm.com/docs/gitignore) shows that there can be some complicated ways to refer to very specific files in a massive project folder.

---

3. **Commit changes**: once your changed files have been staged, you're ready to **commit**. Think of commits as a record of the project at that point in time. A commit needs to have a **message** attached to it, just a short description of the updates you made. Commit your changes by typing the terminal command:

   ```shell
   git commit -m "Short description of my changes"
   ```

Staging and committing can also be achieved through the VSCode **Source Control** menu. It is possible to skip the staging step: if you add `-a` before your message in your commit command, it will do both steps in one. There are settings in VSCode to preference this behaviour for your Source Control.

To view all your previous commits, you can use the command:

```shell
git log
```

You can use `q` to exit.

---

### Undo! Undo!!

To revert a file back to the state of the last commit (permanently deleting all _uncommitted_ changes), you can use the terminal command:

```shell
git restore .
```

Restore can also be triggered through the source control.

If you have already committed your changes but now need to revert back to an earlier version, check for the commit ID you want to revert back to in your commit log. Once you have the ID, you can run:

```shell
git reset commitIDGoesHere
```

Git reset is only recommended if you **haven't** already pushed your changes to GitHub!! GitHub will get very upset if you try to just... go back in time. If you have already synchronized your local Git and GitHub, you will need to instead use:

```shell
git revert commitIDGoesHere
```

What this does is instead of going back in time, it will look at the older version and overwrite your new files with the old files. This means we're making a _new_ commit, but with _old_ data. The commit history will reflect this, but this way, GitHub stays happy.

## GitHub

Note that so far, all of this has occurred **locally**, ie. only on your computer.

**GitHub** is one of a few large remote repository collections. We will ask you to make an account at [https://github.com/](https://github.com/). Having a remote repository for your project will mean you can clone and access it from anywhere. Your mentors (and potential employers!) can also do the same to review and test your code. It's important to keep the remote repository of your projects up-to-date during the course as it makes preparing for your appointments much easier for the mentors if they can have a quick look at what you're doing ahead of time.

To connect your GitHub directly to VSCode, you must give permission to access your GitHub account locally. You can enter your credentials into the command line:

```shell
git config user --global user.name "yourGitHubUserName"
```

```shell
git config user --global user.email "yourGitHubEmail"
```

You'll be prompted to give VSCode access to your GitHub account, as it will be updating your remote repositories on your behalf.

### Creating a _Remote_ Repository

A remote repository simply refers to a copy of your Git repo saved somewhere online. There is no automatic updates, however. When you commit changes locally, they are only local until you **push** those changes and synchronize the local and remote repositories.

If you're happy to use the Source Control, you can go ahead and click **publish**. This will automatically create a remote repository, connect it to the open git repo, and push all changes. You will be prompted to name your remote repository and specify if it is to be published publicly or privately. All future commits can be **pushed** online by using the **sync** button in the Source Control, or the terminal command:

```shell
git push
```

If you're more of a terminal purist, you'll have to manually create the remote repository on GitHub before you can connect it. From your GitHub profile, navigate to the **Repositories** sub-menu and click the green button to create a new one. Once you've named and confirmed it, GitHub will offer some instructions to connect your local and remote repositories. Since we've already used the **init**, **add** and **commit** commands, we can skip to **push an existing repository**. You can tell Git where to find its online "copy" by adding the URL of the remote repo as the origin:

```shell
git remote add origin "your-repository-url"
```

Now we **push** our changes. There is a little bit of disagreement between GitHub and VSCode as to whether your initial project branch should be called **main** or **master**. Your branch is probably already called **master** (the branch you're currently on will be indicated at the very bottom left on VSCode) so in our terminal we're going to type:

```shell
git push -u origin master
```

Make sure to push your changes at the end of each school day! Feel free to keep reading more about Git in the [Git Basics Guide](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository).

### README.md

This file is a recommended addition to any project. It acts as documentation for your project, the formatted content of which will be displayed when you open any repository on GitHub. The `.md` file extension stands for [**Markdown**](https://www.markdownguide.org/), which is a lightweight markup language you can use to easily format and structure documentation for your project. Documentation can include a summary of the goals for the project, instructions on how to clone and run it locally, links to resources, screenshots, and any future plans.

### GitHub Pages

GitHub Pages is a service provided by GitHub that will let you deploy a simple static website directly from a _public_ repository. In the **Settings** of your repo, under **Code and automation**, select **Pages**. Here, select **Deploy from a branch** under **Source**, and then select your main or master branch from the **Branch** select input. Save, and wait a few minutes.

Your project can then be previewed from `<your-github-username>.github.io/<your-repo-name>`.
