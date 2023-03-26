# add-git-username-to-terminal
Add git name along with branch name in terminal

I found this below function on stackoverflow for adding colorized branch name in terminal when you are in project directory.
```
function parse_git_branch () {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
 
RED="\[\033[01;31m\]"
YELLOW="\[\033[01;33m\]"
GREEN="\[\033[01;32m\]"
BLUE="\[\033[01;34m\]"
NO_COLOR="\[\033[00m\]"

PS1="$GREEN\u@\h$NO_COLOR:$BLUE\w$YELLOW\$(parse_git_branch)$NO_COLOR\$ "
```
While working on a common laptop that was being used by more than one person,
It was difficult to identify which username has been set for the project.
And wrote this small function to display username before branch name like
> abc@xyz:~/Desktop/project-directory\[Jonhn Doe\](feature-branch)$
```
function parse_git_username () {
  git config user.name
}

RED="\[\033[01;31m\]"
YELLOW="\[\033[01;33m\]"
GREEN="\[\033[01;32m\]"
BLUE="\[\033[01;34m\]"
NO_COLOR="\[\033[00m\]"

PS1="$GREEN\u@\h$NO_COLOR:$BLUE\w$RED[\$(parse_git_username)]$YELLOW\$(parse_git_branch)$NO_COLOR\$ "
```
