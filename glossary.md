# git glossary
> [source (git-scm.com)](https://git-scm.com/book/en/v2)

## table of contents
* [home](README.md)
* [common commands](common_commands.md)
* [branching strategies](branching_strategies.md)
* [troubleshooting](troubleshooting.md)
* [ssh setup](ssh_setup.md)
* [external resources](README.md#external-resources)

---

## [branch](https://git-scm.com/book/en/v1/Git-Branching-What-a-Branch-Is)
To really understand the way Git does branching, we need to take a step back and examine how Git stores its data. As you may remember from Chapter 1, Git doesn’t store data as a series of changesets or deltas, but instead as a series of snapshots.

Running [`git commit`](common_commands.md#commit) checksums all project directories and stores them as tree objects in the Git repository. Git then creates a commit object that has the metadata and a pointer to the root project tree object so it can re-create that snapshot when needed.

A branch in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is master. As you initially make commits, you’re given a master branch that points to the last commit you made. Every time you commit, it moves forward automatically.


## [checkout](common_commands.md#checkout)
Checking out is the operation of switching the working tree to the state at a given snapshot, which is usually the HEAD of another branch.


## commit
A commit is a snapshot of all tracked files in the repo.


## directory
Also known as a folder.


## dirty
> [source](https://stackoverflow.com/questions/20642980/does-git-dirty-mean-files-not-staged-or-not-committed-glossary-conflict)

The "right" definition is, I think, that your tree is "clean" if there are no changes to commit and no changes between "tree staged for commit" (contents of index) and "work directory". However, it's reasonable to ask separately whether the index is clean (i.e., there is nothing staged for commit) and/or the work-tree is clean (unchanged) with respect to "the staging area" or "the HEAD commit".


## distributed version control system
A Distributed Version Control System (DVCS) differs from traditional VCS systems in that every user has a copy of the entire repo, including the history and all branches.

A connection to a central server is not required to work on a project. Changes and conflicts can be resolved later when the diverging histories are [`merge`](common_commands.md#merge)d later on.


## [gitignore](https://git-scm.com/docs/gitignore)
Specifies intentionally untracked files to ignore.

A `.gitignore` file in the root of the repository contains a list of patterns that should not be tracked.

See the documentation for more information on ignore patterns.

Tracked files that you would like to ignore can be deleted with `git rm --cached .` and then re-added with `git add .`


## [hash](https://git-scm.com/docs/gitglossary#def_SHA1)
The unique identifier of an object. The object name is usually represented by a 40 character hexadecimal string. Also colloquially called SHA-1.


## master
Master is the name given to the default branch of a repository.

Whenever you create a Git repository, a branch named "master" is created, and becomes the active branch. In most cases, this contains the local development, though that is purely by convention and is not required.


## origin
Origin is the name given to the default remote. It is set automatically when using [`git clone`](common_commands.md#clone), and recommended when setting up the remote for an existing repo.


## [pathspec](https://git-scm.com/docs/gitglossary#gitglossary-aiddefpathspecapathspec)
Pattern used to limit paths in Git commands.

Pathspecs are used on the command line of `git ls-files`, `git ls-tree`, `git add`, `git grep`, `git diff`, `git checkout`, and many other commands to limit the scope of operations to some subset of the tree or worktree. See the documentation of each command for whether paths are relative to the current directory or toplevel. The pathspec syntax is as follows:

* any path matches itself

* the pathspec up to the last slash represents a directory prefix. The scope of that pathspec is limited to that subtree.

* the rest of the pathspec is a pattern for the remainder of the pathname. Paths relative to the directory prefix will be matched against that pattern using fnmatch(3); in particular, * and ? can match directory separators.

For example, Documentation/*.jpg will match all .jpg files in the Documentation subtree, including Documentation/chapter_1/figure_1.jpg.

A pathspec that begins with a colon : has special meaning. In the short form, the leading colon : is followed by zero or more "magic signature" letters (which optionally is terminated by another colon :), and the remainder is the pattern to match against the path. The "magic signature" consists of ASCII symbols that are neither alphanumeric, glob, regex special characters nor colon. The optional colon that terminates the "magic signature" can be omitted if the pattern begins with a character that does not belong to "magic signature" symbol set and is not a colon.

In the long form, the leading colon : is followed by a open parenthesis (, a comma-separated list of zero or more "magic words", and a close parentheses ), and the remainder is the pattern to match against the path.

A pathspec with only a colon means "there is no pathspec". This form should not be combined with other pathspec.


## [refspec](https://git-scm.com/docs/gitglossary#gitglossary-aiddefrefaref)
A name that begins with refs/ (e.g. refs/heads/master) that points to an object name or another ref (the latter is called a symbolic ref). For convenience, a ref can sometimes be abbreviated when used as an argument to a Git command; see gitrevisions[7] for details. Refs are stored in the repository.

The ref namespace is hierarchical. Different subhierarchies are used for different purposes (e.g. the refs/heads/ hierarchy is used to represent local branches).

There are a few special-purpose refs that do not begin with refs/. The most notable example is HEAD.


## [remote](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)
Remote repositories are versions of your project that are hosted on the Internet or network somewhere. You can have several of them, each of which generally is either read-only or read/write for you. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.


## [repository](https://git-scm.com/docs/gitglossary#def_repository)
A collection of refs together with an object database containing all objects which are reachable from the refs, possibly accompanied by meta data from one or more porcelains. A repository can share an object database with other repositories via alternates mechanism.


## [staging area](https://softwareengineering.stackexchange.com/questions/119782/what-does-stage-mean-in-git)
source: [stack exchange](https://softwareengineering.stackexchange.com/questions/119782/what-does-stage-mean-in-git)

To stage a file is simply to prepare it finely for a commit. Git, with its index allows you to commit only certain parts of the changes you've done since the last commit. Say you're working on two features - one is finished, and one still needs some work done. You'd like to make a commit and go home (5 o'clock, finally!) but wouldn't like to commit the parts of the second feature, which is not done yet. You stage the parts you know belong to the first feature, and commit. Now your commit is your project with the first feature done, while the second is still in work-in-progress in your working directory.

## [working tree](https://git-scm.com/docs/gitglossary#gitglossary-aiddefworkingtreeaworkingtree)
The tree of actual checked out files. The working tree normally contains the contents of the HEAD commit’s tree, plus any local changes that you have made but not yet committed.

