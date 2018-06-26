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
Merge branch `[A]` into branch `[B]`
```bash
git checkout A
git merge B
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
git tag v[version_number]
```

### Create a new Tag at the Current Commit 
```bash
git tag -a v[version_number] -m "[message]"
```

### Create a new Tag at a Previous Commit
```bash
git tag -a v[version_number] [commit_hash] 
```

### Pushing Tag to a Remote
By default `git push` does not push tags onto a remote. This is done by:
```bash
git push [remote_name] [branch_name] --tags
```

### Checkout a Specific Tag
```bash
git checkout v[version_number] 
```

### Checkout a Specific Tag on a New Branch
```bash
git checkout v[version_number] 
git checkout -b [new_branch_name]
```
or
```bash
git checkout -b [new_branch_name] v[version_number] 
```

### Clone a Specific Tag
```bash
git clone --branch v[version_number] [URL]
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
git checkout v[version_number] 
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
4. Delete the submodule from the config `rm -rf .git/submodule/[directory_of_submodule]`
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



## Helpful Links
[Forks and Pull Requests on GitHub](https://gist.github.com/Chaser324/ce0505fbed06b947d962)
[Delete a Git Submodule](https://stackoverflow.com/a/1260982)



