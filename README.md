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

