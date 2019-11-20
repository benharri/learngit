# learngit

This is a compilation of notes, tips and a getting started guide to [`git`](https://git-scm.com). Please feel free to open a pull request or fork it for yourself!

---

# here we go!

This is not meant to be a complete guide to git. Just some notes that I've gathered over the years of using git that might be helpful to share with others.

## getting set up

1. Download [`git`](https://git-scm.com) and install it.
    * Some OSes/distros have `git` available through a package manager like `brew`, `apt`, or `pacman`. That will be the easiest option.
1. Windows: open git bash (or any command prompt if you chose to install git system-wide).
    All other systems: open a terminal of your choice.
1. Make sure that the install worked correctly by typing `git --version`
1. Configure git with your name and email address:
    * `git config --global user.name "Your Name Here"`
    * `git config --global user.email "name@domain.tld"`

You're ready to `git` gud!

![git gud](img/gitgud.jpeg)


## making your first repo

1. Create a new, empty folder ([directory](glossary.md#directory) in git and unix speak)
    * the command to make a new folder is `mkdir <directory_name>`
1. Open or move to that folder in a command prompt that has git (look for git bash in the start menu if you're having trouble with this one)
    * the command to move between directories is `cd <directory_name>`
1. Once you're in that directory, execute `git init`. this command creates a `.git` folder inside the current folder, which is where `git` stores all the information and history for the repo.
1. Create and edit some files
    * for example: `echo "foo bar" >> foobar.txt`
1. Check `git status` you should see something like this:
    ![status of new repo](img/new-repo-status.png)
    * at this point, our [working tree](glossary.md#working-tree) is ["dirty"](glossary.md#dirty), meaning that there are unsaved changes in the directory.
1. At this point, you need to add the changes to the [staging area](glossary.md#staging-area) with the `git add` command
    * you can add individual files by name (`git add foobar.txt`) or all changes to the working tree with the command option `--all`
1. Once the files are staged, you are now ready to [`commit`](common_commands.md#commit) the changes. every commit requires a message, which can be specified with the `-m` option. if you don't give a message with the [`commit`](common_commands.md#commit) command, `git` will open your file editor and ask you to enter one.
    ![add and commit changes](img/add-and-commit.png)

Now you have a repo with one commit in it!


## syncing your changes with others

Now we get to have some real fun. The whole point of a distributed version control system is to allow many people to be working on the same code at once.

There are many ways to collaborate on a `git` repo. The simplest way to share a repo is to use the `--bare` option with the [`init`](common_commands.md#init) command.

> Bare repos are generally stored on a server that all users have SSH access to: once the repo is created on the server, each person can [`clone`](common_commands.md#clone) a copy to their local machine like this: `git clone user@servername:path/to/repo`

Otherwise, there are dozens of git hosting options, the most popular of which is [github](https://github.com), which hosts the majority of all open source projects.

Another cool option is [gitlab](https://gitlab.com). They offer unlimited private repos in addition to public ones.

Let's take a look at syncing your repo with github (or any other git hosting location - just swap out the URLs).

1. [Create the repo](https://github.com/new) (this assumes you're using GitHub)
1. Set up the [`remote`](glossary.md#remote)s
    * This depends on whether you have already created the repository locally. once you have created the repo on github, it will display some tips for which commands to use
    * For an existing repo: `git remote add origin git@github.com:username/reponame` OR `git remote add origin https://github.com/username/reponame` depending on your [SSH key setup](ssh_setup)
    * If the repo doesn't exist yet, [`clone`](common_commands.md#clone) the repo like this: `git clone git@github.com:username/reponame`
    * A repo can have and use more than one remote. you can see the current remotes with this command: `git remote -v`
1. Before you can sync your changes, there needs to be at least one commit in the repo (not a problem for pre-existing repos). Create one now if you haven't.
1. Now you can [`push`](common_commands.md#push) your commit history to the remote repo! use this command: `git push origin --all` to push all branches and commits to the remote (assuming that the remote is named `origin`)

To get changes that have other people have pushed the the repo while you were away, use the [`fetch`](common_commands.md#fetch) and [`merge`](common_commands.md#merge) commands. since this is such a common operation, [`pull`](common_commands.md#pull) was created as a shortcut for `git fetch` immediately followed by `git merge`.

If you haven't made any changes since the last time you `pull`ed the latest changes, it's usually a good idea to [`rebase`](common_commands.md#pull). This will replay all of the work that has been done on top of the current repo state, avoiding extra merge commits in the repo history. Just use `git pull --rebase`.



---

## external resources
So you want to learn more?
Here are some more resources!

### articles and documentation
* [git flight rules](https://github.com/k88hudson/git-flight-rules)
* [progit book](https://git-scm.com/book/en/v2)
* [github interactive tutorial](https://try.github.io)
* [learn enough git to be dangerous](https://www.learnenough.com/git-tutorial)
* [atlassian git tutorials](https://www.atlassian.com/git/tutorials)
* [github documentation](https://help.github.com)

### tools and apps
* [sourcetree app](https://sourcetreeapp.com) (a visual GUI tool for working with git repos: great for people who don't feel quite at home on the command line)
* [github desktop](https://desktop.github.com) (an alternate GUI by github)


---

## contact me
Shoot me a message somewhere on the interwebz

* [email](mailto:ben@tilde.team)
* [my site](https://tilde.team/~ben/)
* [github](https://github.com/benharri)
* irc (ben on [tilde.chat](https://tilde.chat/), benharri on [freenode](https://freenode.net/))

Thanks for checking out my git guide!
