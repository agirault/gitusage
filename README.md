#Git Usage

All useful git commands

##Start

###Install Git
- Download the latest stable release on http://git-scm.com/downloads

###Setup Git ([Git doc](http://git-scm.com/book/en/Getting-Started-First-Time-Git-Setup))
- Configure username `$ git config --global user.name <username>`
- Configure email address `$ git config --global user.email <email>`
- Check the configuration `$ git config --list`

###Create repository

#####From Github
- Create repository on `github.com`
- Clone repository: `$ git clone git@github.com:<username>/<RepoName>.git`

#####From Local
- Move to code directory `$ cd <RepoName>`
- Initialize a new Git repository `$ git init`
- Create repository on `github.com`
- Link local directory to remote github repository `$ git remote add origin git@github.com:<username>/<RepoName>.git`

##Commit changes

<img width="40%" src="http://git-scm.com/figures/18333fig0106-tn.png"/>

- Add or remove all modified files to the staging area `$ git add/rm <file1> <file2>`
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

###Create a tag ([Git doc](http://git-scm.com/book/en/Git-Basics-Tagging))
To create a tag for the current commit, just use git tag. To tag a given commit, give the commit id to git tag:  
```
$ git tag -a vX.X -m 'Version X.X' [commit]
$ git push --tags

$ git show vX.X
```

To remove a tag locally and remotely: ([link](http://wptheming.com/2011/04/add-remove-github-tags/))  
```
$ git tag -d vX.X
$ git push origin :vX.X
```

To apply a tag from a repository to a fork or any other repository: ([link](http://stackoverflow.com/questions/1357086/git-how-do-i-pull-a-tagged-revision-into-my-fork))
```
$ git clone git@github.com:<ForkUsername>/<RepoName>.git
$ cd <RepoName>
$ git fetch git@github.com:<BaseUsername>/<RepoName>.git "refs/tags/*:refs/tags/*"
$ git push --tags
```

###Create diff info from last commit to current working directory
```
$ git diff
```


###See list of all commits
```
$ git log [-1] [--pretty=oneline]
```

###Apply 1 commit from another branch ([link](http://wiki.koha-community.org/wiki/Using_Git_Cherry_Pick))
```
$ git cherry-pick <commit>
```
To apply a commit from another repository:
```
$ git remote add upstream <repo>
$ git fetch upstream
-> After fetching the other repository, all its commits will be usable by cherry-pick
```

###Display Git GUI
```
$ gitk
```
###Remove a commit
Be careful, this action will remove ALL commits done after the one to reset to, as well as ALL changes in work directory  
IT CAN NOT BE UNDONE
```
$ git reset --hard <commit>
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
$ cd <Code Dir>
$ sh /path/to/gistfile1.sh
$ git push -f
```
**Warning:** Rewrite the history by changing author/committer info will **change the tag** of all the modified commits

##Issues

###Errors when pushing
- Access denied
```
$ git push
```
You should always use `git@github.com:<username>/<RepoName>.git`  
If you get the access denied error when pushing, you probably need to set up a SSH public key to link your computer to your github account, so github allows this computer to push commits using your name.  
To set up a public key, see [github doc](http://help.github.com/articles/generating-ssh-keys).  

- Non Fast-Forward commit
```
$ git push
To git@github.com:<username>/<RepoName>.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:<username>/<RepoName>.git'
To prevent you from losing history, non-fast-forward updates were rejected
Merge the remote changes before pushing again.  See the 'Note about
fast-forwards' section of 'git push --help' for details.
```
In simple words, this means that the commits you are trying to push contain something else than just new commits (changes in or removal of existing commits...), and pushing these changes will make the remote repository go backwards and not forward.  
If it is OK to do this (if it will not have any consequences on other people's local clones), then you can force the push:  
```
$ git push -f
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
$ git add/rm <file1> <file2>
$ git commit -m '<comment>'
$ git push
$ git push -f
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
$ git tag -a vX.X -m 'Version X.X' [commit]
$ git push --tags
$ git show vX.X
$ git tag -d vX.X
$ git push origin :vX.X

$ git clone git@github.com:<ForkUsername>/<RepoName>.git
$ cd <RepoName>
$ git fetch git@github.com:<BaseUsername>/<RepoName>.git "refs/tags/*:refs/tags/*"
$ git push --tags
```
```
$ git diff
$ git log [-1] [--pretty=oneline]
$ git cherry-pick <commit>
$ gitk
$ git reset --hard <commit>
```
```
$ git remote add upstream git@github.com:<username>/<repository>
$ git fetch upstream
$ git checkout master
$ git reset --hard upstream/master
$ git push origin master
```
