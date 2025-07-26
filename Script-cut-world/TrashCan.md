

##  **TrashCan BashSrcipt**



```bash 

#!/bin/bash

# 🌈 Color Codes
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
CYAN='\033[0;36m'
MAGENTA='\033[0;35m'
BOLD='\033[1m'
NC='\033[0m' # No Color

trash_dir="$HOME/.local/share/Trash/files"

main_menu() {
  clear
  figlet -c "TrashCan" | lolcat
  printf "                     \e[0m\e[5m\e[1;93m💞 welcom to my Script-cut world. 💞\e[25m\e[0m\n"
  printf "                  \e[0m\e[1m\e[1;96mCreate By\e[0m\e[1;33m Kyaw Nyein Thant\e[0m-\e[1;37mDate,25,Jul,2025.\e[0m\e[1;96m\e[0m\n" 
  echo -e "${CYAN}=============================${NC}"
  echo -e "${MAGENTA}[${BOLD}1${NC}${MAGENTA}]${NC} ${GREEN}🗂️   Trash files from current directory${NC}"
  echo -e "${MAGENTA}[${BOLD}2${NC}${MAGENTA}]${NC} ${YELLOW}♻️   Retrash (restore) files to current directory${NC}"
  echo -e "${MAGENTA}[${BOLD}3${NC}${MAGENTA}]${NC} ${RED}${BOLD}🧨  Danger Zone${NC}"
  echo -e "${MAGENTA}[${BOLD}q${NC}${MAGENTA}]${NC} ${CYAN}❌  Quit${NC}"
  echo -e "${CYAN}=============================${NC}"
  read -p "Select an option [1, 2, 3 or q]: " option

  case "$option" in
    1) trash_files ;;
    2) restore_files ;;
    3) danger_zone ;;
    q|Q)
      echo -e "${YELLOW}👋 Exiting... Bye !!!  babby bubu.${NC}"
      exit 0
      ;;
    *) 
      echo -e "${RED}❌ Invalid option.${NC}"
      sleep 1
      main_menu
      ;;
  esac
}

trash_files() {
  echo -e "\n${BLUE}📁 Files in current directory:${NC}"
  files=(*)
  i=1
  for file in "${files[@]}"; do
    echo -e "${YELLOW}[$i]${NC} $file"
    ((i++))
  done

  echo -e "${MAGENTA}👉 Type number(s) (e.g. 1 2 3) or 'a' for all:${NC}"
  read -p "Choose files to trash: " -a choices

  if [[ "${choices[0]}" == "a" ]]; then
    for f in "${files[@]}"; do
      [[ -e "$f" ]] && trash-put "$f" && echo -e "${GREEN}✅ Trashed: $f${NC}"
    done
  else
    for index in "${choices[@]}"; do
      selected="${files[$((index-1))]}"
      [[ -e "$selected" ]] && trash-put "$selected" && echo -e "${GREEN}✅ Trashed: $selected${NC}"
    done
  fi
  read -p "↩️ Press Enter to return..." && main_menu
}

restore_files() {
  echo -e "\n${BLUE}🗃️ Files in Trash:${NC}"
  mapfile -t trash_files < <(ls -1 "$trash_dir")

  if [[ ${#trash_files[@]} -eq 0 ]]; then
    echo -e "${YELLOW}🚫 Trash is empty.${NC}"
    read -p "↩️ Press Enter to return..." && main_menu
    return
  fi

  i=1
  for file in "${trash_files[@]}"; do
    echo -e "${YELLOW}[$i]${NC} $file"
    ((i++))
  done

  echo -e "${MAGENTA}👉 Type number(s) (e.g. 2 4 5) or 'a' for all:${NC}"
  read -p "Choose files to restore: " -a restore_choices

  if [[ "${restore_choices[0]}" == "a" ]]; then
    for f in "${trash_files[@]}"; do
      mv "$trash_dir/$f" "./" && echo -e "${GREEN}✅ Restored: $f${NC}"
    done
  else
    for index in "${restore_choices[@]}"; do
      selected="${trash_files[$((index-1))]}"
      mv "$trash_dir/$selected" "./" && echo -e "${GREEN}✅ Restored: $selected${NC}"
    done
  fi
  read -p "↩️ Press Enter to return..." && main_menu
}

danger_zone() {
  echo -e "${RED}${BOLD}\n🧨 DANGER ZONE${NC}"
  echo -e "${YELLOW}This section affects your TRASH folder permanently.${NC}"
  echo -e "${MAGENTA}[1]${NC} Restore file(s) from Trash"
  echo -e "${MAGENTA}[2]${NC} Selectively Delete file(s) from Trash"
  echo -e "${MAGENTA}[3]${NC} Cancel and go back"
  read -p "Choose an option [1-3]: " danger_option

  case "$danger_option" in
    1)
      restore_files
      ;;
    2)
      mapfile -t trash_files < <(ls -1 "$trash_dir")
      if [[ ${#trash_files[@]} -eq 0 ]]; then
        echo -e "${YELLOW}🚫 Trash is already empty.${NC}"
        read -p "↩️ Press Enter to return..." && main_menu
        return
      fi

      echo -e "\n${RED}⚠️ Select files to permanently delete:${NC}"
      i=1
      for file in "${trash_files[@]}"; do
        echo -e "${YELLOW}[$i]${NC} $file"
        ((i++))
      done

      echo -e "${MAGENTA}👉 Type number(s) (e.g. 1 3 5) or 'a' for all:${NC}"
      read -p "Files to delete permanently: " -a del_choices

      if [[ "${del_choices[0]}" == "a" ]]; then
        for f in "${trash_files[@]}"; do
          rm -rf "$trash_dir/$f" && echo -e "${GREEN}🗑️ Deleted: $f${NC}"
        done
      else
        for index in "${del_choices[@]}"; do
          selected="${trash_files[$((index-1))]}"
          rm -rf "$trash_dir/$selected" && echo -e "${GREEN}🗑️ Deleted: $selected${NC}"
        done
      fi
      read -p "↩️ Press Enter to return..." && main_menu
      ;;
    3)
      echo -e "${CYAN}↩️ Back to main menu.${NC}"
      sleep 1
      main_menu
      ;;
    *)
      echo -e "${RED}❌ Invalid option.${NC}"
      sleep 1
      danger_zone
      ;;
  esac
}

# 🔁 Start the script
main_menu

```


---


