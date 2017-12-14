# learngit

This is a compilation of notes, tips and a getting started guide to [`git`](https://git-scm.com). Please feel free to open a pull request or fork it for yourself!

### table of contents
**[home](README.md)** &bull;
[glossary](glossary.md) &bull;
[common commands](common_commands.md) &bull;
[branching strategies](branching_strategies.md) &bull;
[troubleshooting](troubleshooting.md) &bull;
[ssh setup](ssh_setup.md)

---

### on this page
* [getting set up](README.md#getting-set-up)
* [making your first repo](README.md#making-your-first-repo)
* [syncing your changes with others](README.md#syncing-your-changes-with-others)
* [external resources](README.md#external-resources)

---


# here we go!

This is not meant to be a complete guide to git. Just some notes that I've gathered over the years of using git that might be helpful to share with others.

## getting set up

1. Download [`git`](https://git-scm.com) and install it.
    * Some OSes/distros have `git` available through a package manager like `brew`, `apt`, or `pacman`. That will be the easiest option.
1. Windows: open git bash (or any command prompt if you chose to install git system-wide) all other systems: open a terminal of your choice
1. Make sure that the install worked correctly by typing `git --version`
1. Configure git with your name and email address:
    * `git config --global user.name "Your Name Here"`
    * `git config --global user.email "youremail@domain.tld"`

You're ready to `git` gud!

![git gud](img/gitgud.jpeg)


## making your first repo

1. Create a new, empty folder ([directory](glossary#directory) in git and unix speak)
    * the command to make a new folder is `mkdir <directory_name>`
1. Open or move to that folder in a command prompt that has git (look for git bash in the start menu if you're having trouble with this one)
    * the command to move between directories is `cd <directory_name>`
1. Once you're in that directory, execute `git init`. this command creates a `.git` folder inside the current folder, which is where `git` stores all the information and history for the repo.
1. Create and edit some files
    * for example: `echo "foo bar" >> foobar.txt`
1. Check `git status` you should see something like this:
    ![status of new repo](img/new-repo-status.png)
    * at this point, our [working tree](glossary#working-tree) is ["dirty"](glossary#dirty), meaning that there are unsaved changes in the directory.
1. At this point, you need to add the changes to the [staging area](glossary#staging-area) with the `git add` command
    * you can add individual files by name (`git add foobar.txt`) or all changes to the working tree with the command option `--all`
1. Once the files are staged, you are now ready to [`commit`](common_commands#commit) the changes. every commit requires a message, which can be specified with the `-m` option. if you don't give a message with the [`commit`](common_commands#commit) command, `git` will open your file editor and ask you to enter one.
    ![add and commit changes](img/add-and-commit.png)

Now you have a repo with one commit in it!


## syncing your changes with others

Now we get to have some real fun. The whole point of a distributed version control system is to allow many people to be working on the same code at once.

There are many ways to collaborate on a `git` repo. The simplest way to share a repo is to use the `--bare` option with the [`init`](common_commands#init) command.

> Bare repos are generally stored on a server that all users have SSH access to: once the repo is created on the server, each person can [`clone`](common_commands#clone) a copy to their local machine like this: `git clone user@servername:path/to/repo`

Otherwise, there are dozens of git hosting options, the most popular of which is [github](https://github.com), which hosts the majority of all open source projects.

Let's take a look at syncing your repo with github (or any other git hosting location - just swap out the URLs).

1. [Create the repo](https://github.com/new) (this assumes you're using GitHub)
1. Set up the [`remote`](glossary#remote)s
    * This depends on whether you have already created the repository locally. once you have created the repo on github, it will display some tips for which commands to use
    * For an existing repo: `git remote add origin git@github.com:username/reponame` OR `git remote add origin https://github.com/username/reponame` depending on your [SSH key setup](ssh_setup)
    * If the repo doesn't exist yet, [`clone`](common_commands#clone) the repo like this: `git clone git@github.com:username/reponame`
    * A repo can have and use more than one remote. you can see the current remotes with this command: `git remote -v`
1. Before you can sync you changes, there needs to be at least one commit in the repo (not a problem for pre-existing repos). Create one now if you haven't.
1. Now you can [`push`](common_commands#push) your commit history to the remote repo! use this command: `git push origin --all` to push all branches and commits to the remote (assuming that the remote is named `origin`)

To get changes that have other people have pushed the the repo while you were away, use the [`fetch`](common_commands#fetch) and [`merge`](common_commands#merge) commands. since this is such a common operation, [`pull`](common_commands#pull) was created as a shortcut for `git fetch` immediately followed by `git merge`.

If you haven't made any changes since the last time you `pull`ed the latest changes, it's usually a good idea to [`rebase`](common_commands#pull). This will replay all of the work that has been done on top of the current repo state, avoiding extra merge commits in the repo history. Just use `git pull --rebase`.



---

## external resources
So you want to learn more?
Here are some more resources!

* [progit book](https://git-scm.com/book/en/v2)
* [github interactive tutorial](https://try.github.io)
* [learn enough git to be dangerous](https://www.learnenough.com/git-tutorial)
* [atlassian git tutorials](https://www.atlassian.com/git/tutorials)
* [github documentation](https://help.github.com)
* [sourcetree app](https://sourcetreeapp.com) (a visual GUI tool for working with git repos: great for people who don't feel quite at home on the command line)
* [github desktop](https://desktop.github.com) (an alternate GUI by github)


---

## contact me
Shoot me a message somewhere on the interwebz

* [email](mailto:ben@tilde.team)
* [my site](https://tilde.team/~ben/)
* [twitter](https://twitter.com/nebsirrah)
* [github](https://github.com/benharri)

Thanks for checking out my git guide!
