
---

## Ghostty ui title bar live clock 

```bash 


# Start Live Title Clock
clock_title_loop() {
    while true; do
        echo -ne "\033]0;🕒 $(date '+%I:%M:%S %p') | Welcome bubu\007"
        sleep 1
    done
}


# Only for interactive shell
if [[ $- == *i* ]]; then
    clock_title_loop &
fi


```


---

```bash


# Start Live Title Clock and Title Name 
clock_title_loop() {
    while true; do
        #echo -ne "\033]0; $(date '+%I:%M:%S %p') \007"
         echo -ne "\033]0; 💠 Babby BuBu, I love you .. more than 💠\007"
        sleep 1
    done
}


# Only for interactive shell
if [[ $- == *i* ]]; then
    clock_title_loop &
fi


```


---

![[Pasted image 20250729195508.png]]



---

```bash


export PATH=$PATH:$(go env GOPATH)/bin
#eval "$(starship init bash)"
alias ls="lsd --icon auto "


# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

function set_bubu_prompt() {
    local exit_code=$?  # last command exit code
    local git_branch=""
    local prompt_symbol=">"
    local in_git_repo=false

    # Git branch & dirty check
    if git rev-parse --git-dir > /dev/null 2>&1; then
        in_git_repo=true
        # Git branch name with colored icon
        local branch_name=$(git branch 2>/dev/null | grep "^\*" | sed "s/^\* //")
        git_branch=" \[\e[38;5;45m\]\[\e[0m\] \[\e[1;36m\]$branch_name\[\e[0m\]"  # cyan icon + bold branch name

        # Dirty check → >
        if ! git diff --quiet 2>/dev/null; then
            prompt_symbol="\[\e[0;31m\]>\[\e[0m\]"  # Git dirty → red
        fi
    fi

    # Command error check (non-git directories)
    if [[ $exit_code -ne 0 ]]; then
        prompt_symbol="\[\e[0;31m\]>\[\e[0m\]"
    fi

    # Build PS1
    PS1="\n\[\e[1;35m\]╭─[\[\e[1;1;36m\]\h\[\e[0m\] \[\e[1;36m\]  \[\e[1;32m\]\w\[\e[1;35m\]]-[\[\e[1;33m\]\W\[\e[1;35m\]]$git_branch\n\[\e[1;35m\]╰─$prompt_symbol \[\e[0m\]"
}
PROMPT_COMMAND=set_bubu_prompt


# Start Live Title and Clock
clock_title_loop() {
    while true; do
        echo -ne "\033]0; 💠 "ပင်လယ်တွေမီးတောက်နေရင်တောင် စိတ်နှလုံးသားကို ယုံကြည်ပါ, ကြယ်စင်တွေနောက်ပြန်သွားတောင် မေတ္တာနဲ့ အသက်ရှင်ပါ" 💠\007"
        sleep 1
    done
}


# Only for interactive shell
if [[ $- == *i* ]]; then
    clock_title_loop &
fi


# ✅ Safe Auto Start tmux if not already inside tmux
if command -v tmux >/dev/null 2>&1 && [ -z "$TMUX" ] && [ -n "$PS1" ]; then
    exec tmux new-session -A -s main
fi

```
