

---






```bash 

#!/bin/bash

# ========== Reusable Color Function ==========
color_text() {
    local color_code="$1"
    local text="$2"
    echo -e "\033[${color_code}m${text}\033[0m"
}

# ========== Display Title ==========
display_title() {
    clear
    figlet -c "RAM Cleaner" | lolcat
    printf "                     \e[0m\e[5m\e[1;93m💞 welcom to my Script-cut world. 💞\e[25m\e[0m\n"
    printf "                  \e[0m\e[1m\e[1;96mCreate By\e[0m\e[1;33m Kyaw Nyein Thant\e[0m-\e[1;37mDate,1,Sep,2024.\e[0m\e[1;96m\e[0m\n"
}

# ========== Display RAM Info ==========
fh_banner_title() {
    free -h | awk '
    BEGIN { 
        printf "\033[1;37m\033[1mMemory Info::\033[0m\n\n"
    }
    NR==1 { next }
    NR==2 {
        split($0, data, " ")
        printf "\033[1;35m%-12s\033[0m \033[1;36m|||| \033[1;33m%-10s\033[0m\n", "-Total", data[2]
        printf "\033[1;35m%-12s\033[0m \033[1;36m|||| \033[1;33m%-10s\033[0m\n", "-Used", data[3]
        printf "\033[1;35m%-12s\033[0m \033[1;36m|||| \033[1;33m%-10s\033[0m\n", "-Free", data[4]
        printf "\033[1;35m%-12s\033[0m \033[1;32m|||| \033[1;33m%-10s\033[0m\n", "-Shared", data[5]
        printf "\033[1;35m%-12s\033[0m \033[1;32m|||| \033[1;33m%-10s\033[0m\n", "-Buff/Cache", data[6]
        printf "\033[1;35m%-12s\033[0m \033[1;32m|||| \033[1;33m%-10s\033[0m\n", "-Available", data[7]
    }
    NR==3 {
        split($0, data, " ")
        printf "\033[1;35m%-12s\033[0m \033[1;34m|||| \033[1;33m%-10s\033[0m\n", "-Swap Total", data[2]
        printf "\033[1;35m%-12s\033[0m \033[1;34m|||| \033[1;33m%-10s\033[0m\n", "-Swap Used", data[3]
        printf "\033[1;35m%-12s\033[0m \033[1;34m|||| \033[1;33m%-10s\033[0m\n", "-Swap Free", data[4]
    }'
}

# ========== Display RAM Usage ==========
display_ram_usage() {
    display_title
    local state="$1"
    local color="$2"
    echo -e "                    \033[1;37m===== \033[1;34mRAM Usage\033[0m (\033[5m\033[1m\033[${color}m${state}\033[0m) \033[1;37m=====\033[0m\n"
    fh_banner_title
    echo
}

# ========== RAM Cleaner ==========
clean_ram() {
    sync
    sudo sh -c 'echo 3 > /proc/sys/vm/drop_caches'
    echo "$(date '+%F %T') - RAM cache cleaned" >> "$HOME/Desktop/ramcleanlog/cleaning.log"
    echo -e "$(color_text "1;32" "[✔] RAM Cache and Buffer have been cleaned!")"
}

# ========== External Terminal Launcher ==========
run_in_external_terminal() {
    local script_path="$1"
    if command -v gnome-terminal >/dev/null 2>&1; then
        gnome-terminal -- bash -c "$script_path; exec bash"
    elif command -v xterm >/dev/null 2>&1; then
        xterm -e "$script_path"
    else
        echo "Neither gnome-terminal nor xterm is installed. Please install one of them."
    fi
}

# ========== Self-relaunch in external terminal ==========
if [ -z "$RUNNING_IN_TERMINAL" ]; then
    export RUNNING_IN_TERMINAL=true
    run_in_external_terminal "$0"
    exit 0
fi

# ========== Log Directory Setup ==========
mkdir -p "$HOME/Desktop/ramcleanlog"

# ========== Main Loop ==========
while true; do
    display_ram_usage "Before Cleaning" "1;31"
    read -r -p "$(color_text '1;36' '🔄 Clean RAM Cache and Buffer? Press Enter to continue (or type exit): ')" choice
    [[ "$choice" == "exit" ]] && echo -e "$(color_text '1;33' '👋 Exiting... Bye bye! babby bubu..')" && exit 0

    clean_ram
    sleep 2

    display_ram_usage "After Cleaning" "1;32"
    read -r -p "$(color_text '1;34' '🔁 Press Enter to refresh or type exit to quit: ')" again
    [[ "$again" == "exit" ]] && echo -e "$(color_text '1;33' '👋 Exiting... Bye bye! babby bubu..')" && exit 0
done

```