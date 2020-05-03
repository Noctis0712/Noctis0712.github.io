---
title: "Git or: How You Will Learn to Stop Worrying and Love Programming"
date: 2020-04-28T22:00:00+05:30
# categories:
tags: 
- Git
- GitHub
draft: false
---

Since you’re reading this, I’m going to assume you already know a thing or two about writing computer code. And if you know that, you also know that it can break down at any time because of some minor change. 

But changes are necessary. Software needs updates, be it bug fixes, performance improvements, or some cool new features. With all these constant changes happening, we need some way to track them for a multitude of reasons. And while making these very changes, we tend to break code that was working just fine which leads to us worrying about reverting the code back to its working state, except it’s a tedious task and(or) we don’t remember how the code exactly was because there’s usually just so much of it. 

Also, one cannot write the entire code for a medium to large sized project on one's own. Software development is usually done in teams. When a team member is working on a particular part of the project, changes made to that part might have consequences in other parts on which other team members are working. Hence, there needs to be a way to enable collaboration between team members working on a project.   

This is something that Git can help you with. Git has many more uses, but these may be the simplest to introduce you to it with.

## So what is Git, really?

The [official website](https://git-scm.com/) says, 
> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and delivery.

Okay, that’s too many big words in a single sentence. In simple terms, it is a software that keeps track of your own software project by saving a 'snapshot' of what your project looks like at different times. This ‘snapshot’ in Git terms is called a **commit**. Think of it as creating a checkpoint.

By saving snapshots of your projects at different times, it is basically saving different *versions* of your project. And you are free to view and go to any version of your project. Hence the term, **Version Control System**.

The source code for Git is available to all public on their [GitHub](https://github.com/git/git) *(more on GitHub below)*, making it “Open Source”.

Git is also the most popular VCS out there right now. Currently, 71% of all Open Source Repositories indexed by Open Hub use Git. Needless, to say, it is an important skill to know if you're looking for a job in the software field. 

## Time to go hands-on

Git can be downloaded from its official website. Once you’ve downloaded and installed it, you’re ready to create you first Git project or to be more precise, your first Git repository.

Open up a new terminal and enter the command: 

```    
git --version
```

If it’s installed correctly, it should print version of Git you downloaded.

**Note**: There are GUI applications to use Git which make life a lot easier, especially for new users. When I need to see a GUI version of everything Git can show me, I use [GitHub Desktop]( https://desktop.github.com/). However, since Git is originally a command-line tool, we'll stick with that for now.

`cd` into the directory where you keep all your projects, and create a new directory `my-first-repo` for this test project. 

```
mkdir my-first-repo
cd my-first-repo
```

Now you’re ready to turn this directory into your first repository with this simple command:

```
git init
```

You’ll notice that this has created a hidden directory .git, this is where git stores all the snapshots.

Alright, time to write some code. We’ll keep this simple. Let’s create a simple ‘Hello World’ program. Create a new source file in your favourite language (I’ll go with Python):

Let’s create a simple ‘Hello World’ program. Create a new text file in your favourite language (I’ll go with Python):

`my-first-repo/hello-world.py`:

```python
print("Hello World")
```

Once you've saved it go back to the terminal and check on what Git has to say. Enter the command

```
git status
```

It should show something like this:

```
On branch master

No commits yet

Untracked files:
(use "git add <file>..." to include in what will be committed)

        hello-world.py

nothing added to commit but untracked files present (use "git add" to track)
```

This means that Git knows we have created a new file but it is still untracked. We need to tell Git to track this file. To do this, use the command:

```
git add hello-world.py
```

This processing of `add`-ing a file is called **staging**. The file `hello-world.py` is now 'staged'.

**Note**: You can add multiple files with `git add file1 file2 file3 …` or simply add every file with `git add .`

Check `git status` once again. You'll see that it has a change, `new file: hello-world.py`, ready to be committed. Commit this change using

```
git commit -m "Inital Commit"
```

Here the `-m` flag stands for 'message' which in this case is `"Initial Commit"`. A message is a must while making a commit. At this point Git must've asked you to enter an username. Git needs this because it associates each commit with an **author** so that when working in teams, you know exactly who made which changes.

**Tip**: Always make sure that the commit message is meaningful in the sense that it can explain in not more than 10 words what the changes are.

Once you've set up your name, you can verify it using `git config user.name`. This will print the name you have just entered.

Let’s make some changes to the file. A simple `for` loop, perhaps?

`my-first-repo/hello-world.py`:

```python
print("Hello World")
for i in range(5):
    print(i)
```

If you check `git status` again, it’ll show that there’s been a modification to the file. Stage and commit this change with 

```
git add hello-world.py
git commit -m “Added a for loop” 
```

Notice that the commit message here explains in short the changes made.

**Tip:** Commit different features differently. For example, say you're working on a website and you've made changes to a HTML template and to some backend logic. Commit these two changes seperately with relevant commit messages instead of committing everything at once. 

To view what the recent modification was, do

```
git show -1 hello-world.py
```

Here the `1` means ‘show just the last 1 change’. In the output, you’ll see the lines you added are highlighted and have a `+` sign at the beginning indicating that these are additions. 

To see the list of all commits you’ve made, use

```
git log –oneline
```

To revert the lastest commit, try

```	
git revert HEAD
```

This creates another commit (3rd commit) that is the reverse of the previous commit (2nd commit). That is, the 3rd commit removes everything the 2nd commit added, and adds back everything the 2nd commit removed.

A more common case is that you've made some changes that have messed up the code, but haven't committed these modifications (and you should generally never commit when the code isn't working). You can undo these modifications by going back to the lastest commit using 

```
git checkout -- filename
```

where `filename` is the file that you've modified and want to undo these modifications, or 

```
git checkout . 
```

to undo changes to *all* the files and go back to the way things were when you last committed.

This may seem complicated at first, but trust me, you'll get the hang of it soon enough. 

**Note**: There are also other ways to go back, such as `git reset` but we can’t cover everything here.

There are a LOT more things Git can do, I’ll link some learning resources at the bottom of this article. 

## GitHub

Apart from just version control, Git is also distributed. Meaning there can be one ‘main’ copy of the repository stored on some server, while multiple other copies can be stored on the developers’ computer. Git makes it possible multiple developers to work on the same project, and it does so while making sure two developers don’t make different changes to the same block of code. To learn how, you’ll need to know about **branches** and **merges**.

GitHub is the most common place where the ‘server’ repository is stored. This repository is called the *remote repository*.

![git-gh-p-ph](/images/git-gh-p-ph.jpg)

<img src="/images/git-gh-p-ph.jpg" width="200">

To get started, let’s create a GitHub account. Visit [GitHub]( https://github.com/). When that’s done, create a new repository [here](https://github.com/new).  Name it the same as your local repository, `my-first-repo`. Copy the URL, which should be of the format `https://github.com/<username>/<repo-name>.git`. Remember that `.git` towards the end is important.

Go back to your terminal and add this remote repository:
    
```
git remote add origin <paste-url-here>
```

`origin` is the name given to the remote copy of the repository. Now you’re ready to push (upload) your code to GitHub for your fellow developers to see:
	
```
git push -u origin master 
```

You may see a browser window open up, asking you to log in to GitHub. This is so that GitHub can verify that it really is you so is pushing the commit. The `push` command is used to 'upload' the repository to a remote location. It's also the command you use to update it incrementally with commits. Congratulations, you made your first Git repository online! Visit GitHub and you’ll see that your code is now live!

Alright, now what if you wanted to *download* a repository from GitHub? Maybe you're on a new machine and want to carry over your work from the previous machine. Or perhaps you're working in a team and want to get the project that your teammate has put up on GitHub (remember Git is also about collaboration)?. To download a remote repository, you use the `git clone` command. 

For example, let's try cloning your own repository that you just created but in another directory. `cd` into any folder other than the one that contains `my-first-repo`. The remote URL is used for cloning, so the command to clone the repository into the present working directory would be:

```
git clone <paste-same-url-as-above-here>
```

When you clone a project from a remote location such as GitHub, it comes with the remote URL, so if you make any changes to this cloned repository and want to push them to GitHub, you can just do 

```
git push origin master
```

Here, `master` is a **branch**. 

**Note:** You can push changes directly to remote only if you have the authority to do so (you own the repository or you're an authorized member in the organization that does). To contribute your changes to someone else's repository, you would need to **fork** their project and create a **pull request** ([more on that here](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests)).  

## Branching and Merging

For starters, you can think of a branch as a parallel copy of your repository that has doesn't affect the 'main' code. By default, when you initialize a repository, you're working in the `master` branch. 

The `master` branch is generally seen as the 'production' branch, meaning that it is the code that is currently being used live by the users. For this reason, it is always a good idea to keep this branch clean, and work on all updates and bug fixes in other branches.

![git-branches](/images/git_branch_merge.png) 
*Image Source: https://gitbookdown.site/branching-git-branch.html*

As the above image illustrates, a branch is a deviation from the parent branch (in this case, the `master` branch). To understand better, let's create a branch in the `my-first-repo` repository with the command

```
git branch test-branch
```

We have created a branch called `test-branch`. This branch is based on the `master` branch, since that's the branch we are working in. This has created a duplicate snapshot of everything Git was tracking in `master`. To switch to the branch we created, use

```
git checkout test-branch
```

You can see the list of all the branches with typing just `git branch`. You can create multiple branches. Actually, you can created branches of branches. It is quite literally a tree. 

Now let's try making some changes in our created branch. Create a new file called `new.py`. You can type some code in it or leave it empty, doesn't matter to us right now. Once you're done, stage and commit it. 

```
git add new.py
git commit -m "commit in test-branch"
```

Now switch back to `master` with 

```
git checkout master
```

Notice anything strange? The `new.py` file is gone! This is because the file was created and committed in the `test-branch` and not `master`. Switch back to `test-branch` and you'll see that the file has come back. Magic right!? 

To see the difference between two branches, use

```
git diff master..test-branch
```

Imagine that the addition of `new.py` is a new feature that you've been working on and is now complete and ready to be used. Meaning, we have to bring it over to the `master` branch now.

This act of updating a parent branch (master) with commits from a child branch (test-branch) is called **merging**. To merge `test-branch` into `master`, use this command while in `master`, use

```
git merge test-branch
```

You'll notice that the `new.py` has been brought over to `master` from `test-branch`. You can either add new changes to `test-branch` every time and then merge into `master`, but it's good practice to create a new branch for every new major feature or patch. Since `test-branch`'s job is done for now, let's delete it with

```
git branch -d test-branch
```

This is a safe operation, that is, if you have unmerged changes in the branch you are trying to delete, it will warn you saying the same.

**Tip:** When working in a team, every member should try to work in their own branch. This ensures that changes made by one don't mess with another's code. When all changes are made, they can all be merged at the end.

[Read more about Branching and Merging here](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

## Ignoring files with .gitignore

There are some files that don't need to be tracked and(or) more importantly, should not be committed, especially if your repository is going to be visible to others. Files such as 
-   Application Files (such as the `.idea` folder if you use a JetBrains IDE or `.vscode` in case of Visual Studio Code)
-   Compiled Binaries (`.exe` files) or Cached Bytecode (`.pyc` files in case of Python projects)
- And most importantly, **credentials** such as passwords and API keys. 

When you do a `git add .`, these files get staged too. To avoid this from happening, you can add a file in the root of your repository called `.gitignore`. This is a text file that contains names of files and directories that Git should 'ignore' and not stage for commits, each on a different line.

[Read more on .gitignore here](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#_ignoring)

## Conclusion

I hope this was helpful, and that you've learned something new or revised what you already knew! 

There is definitely more to learn about Git (and GitHub) than what I've talked about here, but this was after all an introductory article. So this will be all for now. I've linked some good material to learn more about Git below.

## Some resources to learn Git
-	[Official Documentation](https://git-scm.com/doc)
-	[Pro Git Book](https://git-scm.com/book/en/v2) (it's a free eBook)
-   [Atlassian's Git Tutorials](https://www.atlassian.com/git/tutorials)
-   [This Git & GitHub Tutorial](https://gitbookdown.site/)
-	[Some More Resources](https://try.github.io/)
