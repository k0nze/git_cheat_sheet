# Git Cheat Sheet


## Branching
### Create new Local Branch
```bash
git checkout -b [new_branch_name] 
```

### Push Branch to Remote
```bash
git push [remote_name] [new_branch_name] 
```

### Show all Branches on Remote
```bash
git remote show [remote_name] 
```

### Pull Remote Branch
```bash
git fetch [remote_name] [remote_branch_name]:[local_branch_name]
git checkout [local_branch_name]
```

### Merge Branches
Merge branch `[B]` into branch `[A]`
```bash
git checkout [A]
git merge [B]
```

### Merge Single Files
```bash
git checkout [A]
git checkout [B] [files_to_merge]
git add [files_to_merge]
git commit -m [commit_message]
```

### Clone a Specific Branch
```bash
git clone --branch [remote_branch_name] [URL]
```

### Delete a Branch
Local:
```bash
git branch -d [local_branch_name]
```
On Remote:
```bash
git push origin --delete [remote_branch_name]
```

## Compare two Branches
Show files that differ in current branch from branch `[branch_name_a]`:
```bash
git diff --names-only [branch_name_a]
```
With `diff` (compares all files, add the file name after the command to only compare a single file):
```bash
git diff [branch_name_a]..[branch_name_b]
```
With `difftool` (compares all files, add the file name after the command to only compare a single file):
```bash
git difftool [branch_name_a]..[branch_name_b]
```


## Merge Conflicts

### Show Difference With Remote
```
git fetch
git diff [local_branch_name] [remote_name]/[remote_branch_name]
```

### Merge
```
git fetch
git merge
```


## Stashing
When you want to switch to a different branch and don't want to commit your changes you can stash them.

### Push Current Project State Onto the Stack
```bash
git stash
```

### Show Stack
```bash
git stash list
```

### Pop Most Recent Stash From the Stack
```bash
git stash apply
```

### Pop a Different State From the Stack
```bash
git stash apply stash@{[number]}
```


## Tagging
### List all Tags
```bash
git tag
```

### Show a Specific Tag
```bash
git tag [tag_name]
```

### Create a new Tag at the Current Commit 
```bash
git tag -a [tag_name] -m "[message]"
```

### Create a new Tag at a Previous Commit
```bash
git tag -a [tag_name] [commit_hash] 
```

### Delete a Local Tag
```bash
git tag --delete [tag_name]
```

### Delete a Remote Tag
```bash
git push --delete [remote_name] [tag_name]
```

### Pushing Tag to a Remote
By default `git push` does not push tags onto a remote. This is done by:
```bash
git push [remote_name] [branch_name] --tags
```

### Checkout a Specific Tag
```bash
git checkout [tag_name] 
```

### Checkout a Specific Tag on a New Branch
```bash
git checkout [tag_name] 
git checkout -b [new_branch_name]
```
or
```bash
git checkout -b [new_branch_name] [tag_name] 
```

### Clone a Specific Tag
```bash
git clone --branch [tag_name] [URL]
```

## Submodules
### Add a Submodule
```bash
git submodule add [URL_of_submodule] [directory_of_submodule] 
```

### Clone a Repository with Submodules
```bash
git clone [URL]
git submodule init
git submodule update
```
or
```bash
git clone [URL] --recursive
```

### Tie a Submodule to a Specific Branch
```bash
git submodule add [URL_of_submodule] [directory_of_submodule]
cd [directory_of_submodule]
git checkout -b [submodule_branch] [submodule_remote]/[remote_submodule_branch]
cd -
git commit -am "[message]"
git push [remote] [branch]
```
Clone it:
```bash
git clone [URL] --recursive
```
or:
```bash
git clone [URL]
git submodule update --init -recursive
```

### Tie a Submodule to a Specific Tag
```bash
git submodule add [URL_of_submodule] [directory_of_submodule]
cd [directory_of_submodule]
git checkout [tag_name] 
cd -
git commit -am "[message]"
git push [remote] [branch]
```
Clone it:
```bash
git clone [URL] --recursive
```
or:
```bash
git clone [URL]
git submodule update --init -recursive
```

### Delete a Submodule
1. Delete the relevant section from `.gitmodules`
2. Delete the relevant section from `.git/config`
3. Delete the submodule from the repository `git rm --cached [directory_of_submodule]`
4. Delete the submodule from the config `rm -rf .git/modules/[directory_of_submodule]`
5. Commit the changes `git commit -m "Removed submodule [submodule_name]"`
6. Delete the submodule from the local drive `rm -rf [directory_of_submodule]` 


## Delete Files
### Delete a File from the Repsitory and your File System
```bash
git rm [file]
```

### Delete a File only from the Repsitory
```bash
git rm --cached [file]
```


## Config
### Show Whole Config
```bash
git config --list
```

### Get Location of Config File
```bash
git config --list --show-origin
```

### Set User Name and E-Mail
```bash
git config --global user.name [user_name]
git config --global user.email [email]
```

### Setup Vim as diff Tool
```bash
git config --global diff.tool vimdiff
git config --global difftool.prompt false
```
Open vim as diff tool:
```bash
git difftool
```

### Setup Vim as merge Tool
```bash
git config merge.tool vimdiff
git config merge.conflictstyle diff3
git config mergetool.prompt false
```

### Delete a Config Entry
```bash
git config --global --unset [config_name]
```

## Miscellaneous
### Show Files that are Tracked
```bash
git ls-tree -r master --name-only
```

## Helpful Links
* [Forks and Pull Requests on GitHub](https://gist.github.com/Chaser324/ce0505fbed06b947d962) 
* [Delete a Git Submodule](https://stackoverflow.com/a/1260982)
* [Setting up vim as diff Tool](https://stackoverflow.com/a/3713865)
* [Setting up vim as merge Tool](http://www.rosipov.com/blog/use-vimdiff-as-git-mergetool/)


