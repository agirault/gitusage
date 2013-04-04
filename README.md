#Git Usage

All useful git commands

##Start

###Install Git
- Download the latest stable release on `http://git-scm.com/downloads`

###Setup Git ([Git doc](http://git-scm.com/book/en/Getting-Started-First-Time-Git-Setup))
- Configure username `$ git config --global user.name <username>`
- Configure email address `$ git config --global user.email <email>`
- Check the configuration `$ git config --list`

###Create repository

#####From Github
- Create repository on `github.com`
- Clone repository: `$ git clone git@github.com:<username>/<RepoName>.git`

#####From Local
- Move to code directory `$ cd <Code Dir>`
- Initialize a new Git repository `$ git init`
- Create repository on `github.com`
- Link local directory to remote github repository `$ git remote add origin git@github.com:<username>/<RepoName>.git`

##Commit changes

<img width="40%" src="http://git-scm.com/figures/18333fig0106-tn.png"/>

- Add all modified files to the staging area `$ git add <file1> <file2>`
- Commit changes to these files with comment `$ git commit -m '<comment>'`
- Push local changes to remote repository `$ git push`

##Branching

###Create and commit branch
- Create branch `$ git checkout -b <branch name> origin`
- Push the branch to the remote repository `$ git push origin <branch name>`

- List existing branches `$ git branch`
- Switch branches `$ git checkout <branch name>`

###Merge and delete branch
- Merge branch with master `$ git merge <branch name> master`
- Delete branch `$ git branch -D <branch name>`

##Other features

###See list of all commits
```
$ git log
```

###Apply 1 commit from another directory ([link](http://wiki.koha-community.org/wiki/Using_Git_Cherry_Pick))
```
$ git cherry-pick <commit>
```

###Display Git GUI
```
$ gitk
```

###Synchronizing a repository with another remote repository ([example](http://www.slicer.org/slicerWiki/index.php/Documentation/Nightly/Developers/Tutorials/BuildTestPackageDistributeExtensions))
```
$ git remote add upstream git@github.com:<username>/<repository>
$ git fetch upstream
$ git checkout master
$ git reset --hard upstream/master
$ git push origin master
```

###Create a "compare view" link between 2 commits ([link](http://jbuckley.ca/2011/09/githubs-compare-view/))
```
http://github.com/<username>/<repository>/compare/<commit1>...<commit2>
```

###Modify username/email information of author/committer for one or several commits ([StakOverflow](http://stackoverflow.com/questions/750172/how-do-i-change-the-author-of-a-commit-in-git))
Use [this script](http://help.github.com/articles/changing-author-info)
```
$ sh /path/to/gistfile1.sh
$ git push -f
```

##Issues

###Errors when pushing
- Access denied
```
TODO
```

- Non Fast-Forward commit
```
To git@github.com:<username>/<RepoName>.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:<username>/<RepoName>.git'
To prevent you from losing history, non-fast-forward updates were rejected
Merge the remote changes before pushing again.  See the 'Note about
fast-forwards' section of 'git push --help' for details.
```

##All Commands

```
$ git config --global user.name <username>
$ git config --global user.email <email@email.com>
$ git config --list
```
```
$ git init
$ git remote add origin git@github.com:adrienkaiser/<RepoName>.git
$ git clone git@github.com:adrienkaiser/<RepoName>.git
```
```
$ git add <file1> <file2>
$ git commit -m '<comment>'
$ git push
```
```
$ git checkout -b <branch name> origin
$ git push origin <branch name>
$ git branch
$ git checkout <branch name>
$ git merge <branch name> master
$ git branch -D <branch name>
```
```
$ git log
$ git cherry-pick <commit>
$ gitk
```
```
git remote add upstream git@github.com:<username>/<repository>
git fetch upstream
git checkout master
git reset --hard upstream/master
git push origin master
```
