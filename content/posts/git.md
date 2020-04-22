---
title: "Git or: How You Will Learn to Stop Worrying and Love Programming"
date: 2020-04-23
draft: false
---

## Intro

Since you’re reading this, I’m going to assume you already know a thing or two about writing computer code. And if you know that, you’re also know that it can break down at any time because of some minor change. 

But changes are necessary. Software needs updates, be it bug fixes, performance improvements, or some cool new features. While making these changes, we’ve all broken code that was working just fine and now we worry about reverting the code back to its working state because we don’t how the code exactly was.

This is something that Git can help you with. Git has many more uses, but this may be the simplest to introduce you to it with.

## But what *is* Git?

The [official website](https://git-scm.com/) says, Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and delivery.

Okay, that’s too many big words in a single sentence. In simple terms, it is a software that keeps track of your own software project by saving a snapshot of what your project looks like at different times. This ‘snapshot’ in Git terms is called a commit.

By saving snapshots of your projects at different times, it is basically saving versions of your project. And you are free to view and go to any version of your project. Hence the term, “Version Control System”.

The source code for Git is available to all public on GitHub (more on this below), making it “Open Source”.

## Time to go hands-on

Git can be downloaded from its official website. Once you’ve downloaded and installed it, you’re ready to create you first Git project or to be more precise, your first Git repository.

Open up a new terminal and enter the command: 
    
    git --version

If it’s installed correctly, it should print version of Git you downloaded.

`cd` into the directory where you keep all your projects, and create a new directory `my-first-repo` for this test project. 

    cd my-first-repo

Now you’re ready to turn this directory into your first repository with this simple command:

    git init

You’ll notice that this has created a hidden directory .git, this is where git stores all the snapshots.

Alright, time to write some code. We’ll keep this simple, 2 files and less than 15 lines of code.

Let’s create a simple ‘Hello World’ program. Create a new text file in your favourite language (I’ll go with Python):

`my-first-repo/test.py`:

    print("Hello World")

and save it. Let’s go back to the terminal and check on what git has to say. Enter the command

    git status

It should show something like this:

    On branch master

    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)

            test.py

    nothing added to commit but untracked files present (use "git add" to track)

This means that Git knows we have created a new file but it is still untracked. We need to tell Git to track this file. To do this, use the command:

    git add test.py

Note: 
You can add multiple files with `git add file1 file2 file3 …` or simply every file with `git add .`

Check `git status` once again. You'll see that it has change, `new file: test.py`, ready to be committed. Commit this change using

    git commit -m "Inital Commit"

Here the `-m` flag stands for 'message' which in this case is `"Initial Commit"`

Let’s make some changes to the file. A simple for loop perhaps?

`my-first-repo/test.py`:

    print(“Hello World”)
	for i in range(5):
		print(i)

If you check `git status` again it’ll show that there’s been a modification to the file. Stage and commit this change with

	git add test.py
    git commit -m “Second commit”

To view what the recent modification was, do

    git show -1 test.py

You’ll see the lines you added highlighted and with a + sign at the beginning indicating that these are additions. Here the 1 represents ‘show just the last 1 change’

To see the list of all commits you’ve made, use

    git log –oneline

To revert the last changes you made, try
	
    git revert HEAD

This creates another commit (3rd commit) that is the reverse of the previous commit (2nd commit). That is, this commit deletes any additions and adds any deletions from the 2nd commit.

Note: There are also other ways to go back, such as `git reset` but we can’t cover everything here.

There are a LOT more things Git can do, I’ll link some learning resources at the bottom of this article. 

Also, which Git is originally a command-line tool, I highly recommend using a GUI tool to use Git. Favourites are [GitHub Desktop]( https://desktop.github.com/) and [GitKraken]( https://www.gitkraken.com/).

## GitHub

Apart from just version control, Git is also distributed. Meaning there can be one ‘main’ copy of the repository stored on some server, while multiple other copies can be stored on the developers’ computer. That’s right, developers with an s. Git makes it possible multiple developers to work on the same project, and it does so while making sure two developers don’t make different changes to the same block of code. To learn how, you’ll need to know about branches and merges.

GitHub is the most common place where the ‘server’ repository is stored. This repository is called the ‘remote repository’.

To get started, let’s create a GitHub account. Visit [GitHub]( https://github.com/). When that’s done, create a new repository [here](https://github.com/new).  Name it the same as your local repository, `my-first-repo`. Copy the URL, which should be of the form `https://github.com/username/my-first-repo.git`. Remember that .git towards the end is important.

Go back to your terminal and add this remote repository:
    
    git remote add origin <paste-url-here>

Now you’re ready to push (upload) your code to GitHub for your fellow developers to see:
	
    git push -u origin master 

Congratulations, you made your first Git repository online! Visit GitHub and you’ll see that your code is now live!

## Some resources to learn Git:
-	[Official Documentation]( https://git-scm.com/doc)
-	[Pro Git Book](https://git-scm.com/book/en/v2)
-	[Some More Resources](https://try.github.io/)

