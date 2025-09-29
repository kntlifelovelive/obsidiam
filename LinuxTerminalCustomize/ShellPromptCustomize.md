

```bash

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
  PS1="\n\[\e[1;35m\]╭─$venv_name[\[\e[1;36m\]\\[\e[0m\] 🌺 \[\e[1;32m\]\\[\e[1;35m\]]-[\[\e[1;33m\]\W\[\e[1;35m\]]$git_branch$eza_status\n\[\e[1;35m\]╰─$prompt_symbol \[\e[0m\]"
}
PROMPT_COMMAND=set_bubu_prompt

```

---

```bash

  # Build PS1
  PS1="\n\[\e[1;35m\]╭─[\[\e[1;1;36m\]\h\[\e[0m\] \[\e[1;36m\]🌺 \[\e[1;32m\]\w\[\e[1;35m\]]-[\[\e[1;33m\]\W\[\e[1;35m\]]$git_branch\n\[\e[1;35m\]╰─$prompt_symbol \[\e[0m\]"
}

```