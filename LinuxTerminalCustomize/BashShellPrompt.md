

```bash 

# ~/.bashrc
# clear && myfetch -c 8 -C " █"
# clear && fastfetch --logo ~/Pictures/.bubu/sweetylife.png --logo-width 23
clear && fastfetch --logo ~/Pictures/.bubu/bubulove.png --logo-width 43
# clear && fastfetch --logo ~/Pictures/sweet.png --logo-width 35
[[ $- != *i* ]] && return
alias update='sudo pacman -Syu'
alias pacup='sudo pacman -Rns $(pacman -Qdtq)'
alias grep='grep --color=auto'
alias pool='clear && asciiquarium'
alias f='clear && myfetch -i e -f -c 16 -C "  "'
alias bye='sudo shutdown -h now'
alias loop='sudo reboot'
alias h='dbus-launch Hyprland'
alias fonts='fc-list -f "%{family}\n"'
alias Docs="cd ~/Documents && nvim"
alias Settings="cd ~/.config/hypr && nvim"
alias untar="tar -xf"
alias n="nvim"

# Myconfig alias ===
# ==================
alias ls='eza --icons'
alias tree='tree -C'
alias love='clear && fastfetch --logo ~/Pictures/.bubu/sweetylife.png --logo-width 23'
alias bubu='clear && fastfetch --logo ~/Pictures/.bubu/bubulove.png --logo-width 45'
alias hyprconfig="cd ~/.config/hypr/UserConfigs && nvim"
alias mywaybarconfig="cd ~/.config/waybar && nvim"

# Pacman install package
alias pacup='sudo pacman -Syu'                    # update system
alias pacupf='sudo pacman -Syyu'                  # force update system
alias pacrm='sudo pacman -Rns'                    # remove package with configs
alias pacclean='sudo pacman -Rns $(pacman -Qdtq)' # remove orphans
alias pacs='pacman -Ss'                           # search package in repo
alias paci='sudo pacman -S'                       # install package
alias pacq='pacman -Q'                            # list installed packages
alias pacql='pacman -Ql'                          # list files of a package
alias pacinfo='pacman -Si'                        # show package info

# Yay (AUR helper)
alias yupdate='yay -Syu' # update all (AUR + repo)
alias yinstall='yay -S'  # install package from AUR/repo
alias yremove='yay -Rns' # remove with configs
alias yclean='yay -Yc'   # clean unneeded packages
alias ysearch='yay -Ss'  # search

export NVM_DIR="$HOME/.nvm"
export TERM=xterm-256color
export TERM=xterm-kitty

[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
# PS1='[\u@\h \W]\$ '
PS1="\[\e[1;33m\]\u\[\e[0m\]\[\e[1;31m\]@\[\e[0m\]\[\e[1;34m\]\h\[\e[0m\] \[\e[1;32m\]\W\[\e[0m\]\$ "

function set_bubu_prompt() {
  local exit_code=$? # last command exit code
  local git_branch=""
  local prompt_symbol=">"
  local in_git_repo=false
  local venv_name=""
  local eza_status=""

  # Detect active virtual environment (Python venv / Conda)
  if [[ -n "$VIRTUAL_ENV" ]]; then
    venv_name="(\[\e[1;32m\] $(basename "$VIRTUAL_ENV")\[\e[0m\]) " # ( env)
  elif [[ -n "$CONDA_DEFAULT_ENV" ]]; then
    venv_name="(\[\e[1;32m\] $CONDA_DEFAULT_ENV\[\e[0m\]) "
  fi

  # Git branch & dirty check
  if git rev-parse --git-dir >/dev/null 2>&1; then
    in_git_repo=true
    local branch_name=$(git branch --show-current 2>/dev/null)
    git_branch=" \[\e[38;5;45m\]\[\e[0m\] \[\e[1;36m\]$branch_name\[\e[0m\]"

    if ! git diff --quiet 2>/dev/null; then
      prompt_symbol="\[\e[0;31m\]>\[\e[0m\]" # Git dirty = red >
    fi
  fi

  # eza check → show 📂 count (BLUE)
  if command -v eza &>/dev/null; then
    local files_count=$(eza -1 | wc -l)
    eza_status=" \[\e[1;35m\] 📂 $files_count \[\e[0m\]"
  fi

  # Command error check
  if [[ $exit_code -ne 0 ]]; then
    prompt_symbol="\[\e[0;31m\]>\[\e[0m\]"
  fi

  # Build PS1
  PS1="\n\[\e[1;35m\]╭─$venv_name[\[\e[1;33m\]\u\[\e[0m\]\[\e[1;31m\]@\[\e[0m\]\[\e[1;34m\]\h\[\e[0m\]\\[\e[1;35m\]]-[\[\e[1;33m\]\W\[\e[1;35m\]]$git_branch$eza_status\n\[\e[1;35m\]╰─$prompt_symbol \[\e[0m\]"
}
PROMPT_COMMAND=set_bubu_prompt

```

![[-2025-09-18_14-16-19.png]]**Bashshell prompt**

