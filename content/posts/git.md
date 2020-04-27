---
title: "Git or: How You Will Learn to Stop Worrying and Love Programming"
date: 2020-04-24T01:40:00+05:30
draft: false
---

Since you’re reading this, I’m going to assume you already know a thing or two about writing computer code. And if you know that, you also know that it can break down at any time because of some minor change. 

But changes are necessary. Software needs updates, be it bug fixes, performance improvements, or some cool new features. With all these constant changes happening, we need some way to track them. And while making these very changes, we tend to break code that was working just fine which leads to us worrying about reverting the code back to its working state, except it’s a tedious task and(or) we don’t remember how the code exactly was because there’s usually just so much of it. 

This is something that Git can help you with. Git has many more uses, collaboration being one of them, but this may be the simplest to introduce you to it with.

## But what *is* Git?

The [official website](https://git-scm.com/) says, *Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and delivery.*

Okay, that’s too many big words in a single sentence. In simple terms, it is a software that keeps track of your own software project by saving a snapshot of what your project looks like at different times. This ‘snapshot’ in Git terms is called a **commit**. Think of it as creating a checkpoint.

By saving snapshots of your projects at different times, it is basically saving versions of your project. And you are free to view and go to any version of your project. Hence the term, “Version Control System”.

The source code for Git is available to all public on their [GitHub](https://github.com/git/git) *(more on GitHub below)*, making it “Open Source”.

Also, as I mentioned above, collaboration. Git allows multiple developers to work on the same project without having to worry about another person’s code changes affecting them.

## Time to go hands-on

Git can be downloaded from its official website. Once you’ve downloaded and installed it, you’re ready to create you first Git project or to be more precise, your first Git repository.

**Note**: I highly recommend using a GUI application to use Git for the most part. These make life a lot easier, especially for new users. Favourites are 
-   [GitHub Desktop]( https://desktop.github.com/)
-   [GitKraken]( https://www.gitkraken.com/).

However, since Git is originally a command-line tool, we'll stick with that for now.

Open up a new terminal and enter the command: 
    
    git --version

If it’s installed correctly, it should print version of Git you downloaded.

`cd` into the directory where you keep all your projects, and create a new directory `my-first-repo` for this test project. 

    mkdir my-first-repo
    cd my-first-repo

Now you’re ready to turn this directory into your first repository with this simple command:

    git init

You’ll notice that this has created a hidden directory .git, this is where git stores all the snapshots.

Alright, time to write some code. We’ll keep this simple. Let’s create a simple ‘Hello World’ program. Create a new text file in your favourite language (I’ll go with Python):

Let’s create a simple ‘Hello World’ program. Create a new text file in your favourite language (I’ll go with Python):

`my-first-repo/hello-world.py`:

    print("Hello World")

and save it. Let’s go back to the terminal and check on what git has to say. Enter the command

    git status

It should show something like this:

    On branch master

    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)

            hello-world.py

    nothing added to commit but untracked files present (use "git add" to track)

This means that Git knows we have created a new file but it is still untracked. We need to tell Git to track this file. To do this, use the command:

    git add hello-world.py

**Note**: You can add multiple files with `git add file1 file2 file3 …` or simply every file with `git add .`

Check `git status` once again. You'll see that it has change, `new file: hello-world.py`, ready to be committed. Commit this change using

    git commit -m "Inital Commit"

Here the `-m` flag stands for 'message' which in this case is `"Initial Commit"`. A message is a must while making a commit.

Let’s make some changes to the file. A simple `for` loop perhaps?

`my-first-repo/hello-world.py`:

    print(“Hello World”)
	for i in range(5):
		print(i)

If you check `git status` again it’ll show that there’s been a modification to the file. Stage and commit this change with

	git add hello-world.py
    git commit -m “Second commit”

To view what the recent modification was, do

    git show -1 hello-world.py

You’ll see the lines you added are highlighted and have a `+` sign at the beginning indicating that these are additions. In the command, the `1` means ‘show just the last 1 change’

To see the list of all commits you’ve made, use

    git log –oneline

To revert the last changes you made, try
	
    git revert HEAD

This creates another commit (3rd commit) that is the reverse of the previous commit (2nd commit). That is, this commit deletes any additions and adds any deletions from the 2nd commit.

A more common case is that you've made some changes that have messed up the code, but haven't committed these (and you should generally never commit when the code isn't working), you can simply use 

    git checkout -- filename
    
where `filename` is the file that you've modified and want to undo these modifications, or 

    git checkout . 

to undo changes to *all* the files and go back to the way things were when you last committed.

This may seem complicated at first, but trust me, you will get the hang of it soon enough. 

**Note**: There are also other ways to go back, such as `git reset` but we can’t cover everything here.

There are a LOT more things Git can do, I’ll link some learning resources at the bottom of this article. 

## GitHub

Apart from just version control, Git is also distributed. Meaning there can be one ‘main’ copy of the repository stored on some server, while multiple other copies can be stored on the developers’ computer. Git makes it possible multiple developers to work on the same project, and it does so while making sure two developers don’t make different changes to the same block of code. To learn how, you’ll need to know about **branches** and **merges**.

GitHub is the most common place where the ‘server’ repository is stored. This repository is called the ‘remote repository’.

To get started, let’s create a GitHub account. Visit [GitHub]( https://github.com/). When that’s done, create a new repository [here](https://github.com/new).  Name it the same as your local repository, `my-first-repo`. Copy the URL, which should be of the format `https://github.com/<username>/<repo-name>.git`. Remember that `.git` towards the end is important.

Go back to your terminal and add this remote repository:
    
    git remote add origin <paste-url-here>

Now you’re ready to push (upload) your code to GitHub for your fellow developers to see:
	
    git push -u origin master 

Congratulations, you made your first Git repository online! Visit GitHub and you’ll see that your code is now live!

## Some resources to learn Git
-	[Official Documentation]( https://git-scm.com/doc)
-	[Pro Git Book](https://git-scm.com/book/en/v2) (it's a free eBook)
-	[Some More Resources](https://try.github.io/)

