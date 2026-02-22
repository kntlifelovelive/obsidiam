
- Text animation sucess 

```bash

print_banner() {

	echo -e "\033[1;35m
██████╗ ██╗   ██╗██████╗ ██╗   ██╗
██╔══██╗██║   ██║██╔══██╗██║   ██║
██████╔╝██║   ██║██████╔╝██║   ██║
██╔══██╗██║   ██║██╔══██╗██║   ██║
██████╔╝╚██████╔╝██████╔╝╚██████╔╝
╚═════╝  ╚═════╝ ╚═════╝  ╚═════╝ 
\033[0m"

    local text="💞  welcom to my Script-cut world Dream. 💞"
    local padding=50   # slide distance
    local speed=0.02

    tput civis   # hide cursor
    echo

    # Slide from right
    for ((i=padding; i>=0; i--)); do
        printf "\r%*s\e[1;36m%s\e[0m" "$i" "" "$text"
        sleep $speed
    done

    # Keep full text and enable blink
    printf "\r\e[5m\e[1;36m%s\e[25m\e[0m\n" "$text"

    tput cnorm   # restore cursor
}


```


```bash 

	local text=" 🌺 Trust your heart if the sea catch fire,live by love though the stars walk backwack. 🌸🌾 "


```

- `~/.bashrc file setup complete`
```bash 

# ~/.bashrc
[[ $- != *i* ]] && return
# clear && myfetch -i A -f -c 16 -C " █ "
# clear && fastfetch --logo ~/Pictures/.terminalogo/butilove.png --logo-width 28
# clear && fastfetch --logo ~/Pictures/.terminalogo/butilove.png --logo-width 28
alias love='clear && myfetch -i A -f -c 16 -C " █ "'
alias update='sudo pacman -Syu'
alias pacorphans='sudo pacman -Rns $(pacman -Qdtq)'
alias grep='grep --color=auto'
alias bye='sudo shutdown -h now'
alias loop='sudo reboot'
alias fonts='fc-list -f "%{family}\n"'
alias n="nvim"
alias hr="hyprctl reload"

# Myconfig alias ===
# ==================
alias ls='ls --color=auto'
alias tree='tree -C'

# Pacman install package
alias pacupf='sudo pacman -Syyu'  # force update system
alias pacmanrm='sudo pacman -Rns' # remove package with configs
alias pacmanss='pacman -Ss'       # search package in repo
alias pacmani='sudo pacman -S'    # install package
alias pacq='pacman -Q'            # list installed packages
alias pacql='pacman -Ql'          # list files of a package
alias pacinfo='pacman -Si'        # show package info

# Yay (AUR helper)
alias yupdate='yay -Syu' # update all (AUR + repo)
alias yinstall='yay -S'  # install package from AUR/repo
alias yremove='yay -Rns' # remove with configs
alias yclean='yay -Yc'   # clean unneeded packages
alias ysearch='yay -Ss'  # search

export TERM=xterm-kitty
export HISTSIZE=80000
export HISTFILESIZE=100000

function set_bubu_prompt() {
	local exit_code=$? # last command exit code
	local git_branch=""
	local prompt_symbol=">"
	local venv_name=""

	# Detect active virtual environment (Python venv / Conda)
	if [[ -n "$VIRTUAL_ENV" ]]; then
		venv_name="\[\e[0m\](\[\e[1;32m\] $(basename "$VIRTUAL_ENV")\[\e[0m\]) " # ( env)
	elif [[ -n "$CONDA_DEFAULT_ENV" ]]; then
		venv_name="\[\e[0m\](\[\e[1;32m\] $CONDA_DEFAULT_ENV\[\e[0m\]) "
	fi

	# Git branch & dirty check
	if git rev-parse --git-dir >/dev/null 2>&1; then
		local branch_name
		branch_name=$(git branch --show-current 2>/dev/null)

		git_branch=" \[\e[38;5;45m\]\[\e[0m\] \[\e[1;36m\]$branch_name\[\e[0m\]"

		if [[ -n $(git status --porcelain 2>/dev/null) ]]; then
			prompt_symbol="\[\e[31m\]>\[\e[0m\]"
		fi
	fi

	# Command error check
	if [[ $exit_code -ne 0 ]]; then
		prompt_symbol="\[\e[0;31m\]>\[\e[0m\]"
	fi

	if [[ $EUID -eq 0 ]]; then
		user_color="\[\e[1;31m\]" # Root = red color
	else
		user_color="\[\e[1;33m\]"
	fi

	# PS1="\n\[\e[1;35m\]╭($venv_name${user_color}\u\[\e[0m\]\[\e[1;31m\]@\[\e[0m\]\[\e[1;34m\]\h\[\e[0m\]\[\e[1;35m\])-[\[\e[1;33m\]\w\[\e[1;35m\]]$git_branch\n\[\e[1;35m\]╰─$prompt_symbol \[\e[0m\]"
	PS1="\n\[\e[1;35m\]╭($venv_name${user_color}\u\[\e[0m\]\[\e[1;35m\])-[\[\e[1;33m\]\w\[\e[1;35m\]]$git_branch\n\[\e[1;35m\]╰─$prompt_symbol \[\e[0m\]"
}
PROMPT_COMMAND=set_bubu_prompt

title_banner() {
	echo -e "\033[1;35m  
▄▄   ▄▄ ▄▄▄▄▄ ▄▄     ▄▄▄▄  ▄▄▄  ▄▄   ▄▄   ▄▄▄▄▄▄ ▄▄▄    ████▄  ▄▄▄▄  ▄▄▄▄▄  ▄▄▄  ▄▄   ▄▄ 
██ ▄ ██ ██▄▄  ██    ██▀▀▀ ██▀██ ██▀▄▀██     ██  ██▀██   ██  ██ ██▄█▄ ██▄▄  ██▀██ ██▀▄▀██ 
 ▀█▀█▀  ██▄▄▄ ██▄▄▄ ▀████ ▀███▀ ██   ██     ██  ▀███▀   ████▀  ██ ██ ██▄▄▄ ██▀██ ██   ██
\033[0m"
	local text=" 🌺 Trust your heart if the sea catch fire,live by love though the stars walk backwack. 🌸🌾 "

	local padding=35 # slide distance
	local speed=0.03

	tput civis # hide cursor

	# Slide from right
	for ((i = padding; i >= 0; i--)); do
		printf "\r%*s\e[1;36m%s\e[0m" "$i" "" "$text"
		sleep $speed
	done

	# Keep full text and enable blink
	printf "\r\e[5m\e[1;36m%s\e[25m\e[0m\n" "$text"

	tput cnorm # restore cursor

}

# Define the banner function
print_banner() {

	local text=" 🌺 Trust your heart if the sea catch fire,live by love though the stars walk backwack. 🌸🌾 "

	# Keep full text and enable blink
	printf "\r\e[1;36m%s\e[0m\n" "$text"
	# printf "\r\e[5m\e[1;36m%s\e[25m\e[0m\n" "$text"

}

# Custom clear command to include banner
function clear {
	command clear
	print_banner
}

title_banner

```