# Installation

# Configuration
`$ git config --global user.name "John Doe"`
`$ git config --global user.email johndoe@example.com`
Run these commands without --global to apply changes only for local repository.

Change from default editor by executing `$ git config --global core.editor emacs`

Check the configuration by `$ git config --list`

# Getting started

## Create an directory
Select an directory of your choice e.g. ~/Desktop/git-training/, 
open the terminal there and type `git init`.
Congratulations you have your first git repository!

## Committing files
Create some text files e.g. `hallo.txt` or  `hello\_world.py`.
To start version-controlling them add the file to git by using the command `git add filename`.
You can also add multiple files. E.g. you want to add all text files the do `git add *.txt`
Now we can commit these changes by typing `git commit`. This will open your preferred text editor
where you can type in a commit message.
### Commit messages

*Commit messages are important*

Why are the so important? Because it is much easier to track bugs with it,
they describe the process of development, make it easier for others to work
with your code (e.g. code review) and will help you in two years to understand what you did.
They to some extend replace your labbook in its function.

#### How to write commit messages
* Use present tense and use imperative
* Tell why you did changes.
* Limit yourself to 50 characters in the first line.
* Wrap the body at 72 characters

#### Good commit messages

1. Short commit message
"Fix typo in introduction to user guide"
for short commits it is easier to use `git commit -m "Commit message"`

2. Long commit message

```
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

```

#### Hall of shame

* “bug fix”, "more work”, “minor changes”
Bad  because it contains no useful information

* “Change X constant to be 10”
Bad as it does not tell why. What was changed is easy to find out by
  git diff.

* “super long commit message goes here, something like 100 words and lots of characters woohoo!”
Bad because it is unreadable.

## Storing changes on remote server
To store changes on a remote server e.g. Github you need to push your repository there.
If you are doing this for the first time you first need to define where to push your repository to.
Use `git remote add origin https://github.com/GerJuli/introduction-to-git.git` The URL can be
replaced with any URL that points to an existing repository. This can even be a USB drive!
Now push by using `git push -u origin master`. With this command you created an upstream to your
remote 'origin' where you branch 'master' will be pushed.
As this is set up you can use `git push` from now on.

# Cloning existing repositories
Downloading existing repositories is called 'cloning'. You can do this by using
`https://github.com/GerJuli/introduction-to-git.git`.
That is it. Now you can start working on it.

# Workflow

## Check status
With 'git status' you can check the status of your current directory.
This will look like this:

```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

If you now add a file to the repository e.g. README then the status changes.

```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```


Now track the file by adding it to the staging area.
It is now ready to be committed
```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

      new file:   README
```
Now commit this change with a suitable commit message.
Push this now to your repository.


## Gitignore
Sometimes you do not want git to track every file in your repository.
Typically this applies for log files, configuration files (where maybe passwords are stored)
and compiled sources. For this purpose you can create the file  `.gitignore` in your repository.
This file will be read by git. An example `.gitignore` looks like this:

```
# ignore all .log files
*.log

# ignore all files in any directory named config
build/

# but do track sample.log, even though you're ignoring .log files above
!sample.log

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/
```
You can generate gitignore files ![here](https://www.gitignore.io/).
