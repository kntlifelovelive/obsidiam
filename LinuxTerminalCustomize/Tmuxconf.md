


```bash

# Bluelight Theme for tmux (Updated for tmux 3.2+)

set -g status-position top
set -g status-bg colour235     # dark gray background
set -g status-fg colour110     # soft blue foreground


# Left side: Session name
set -g status-left "#[fg=colour117,bg=colour235,bold] #S #[default]"

# Right side: Time + Date
set -g status-right "#[fg=colour110] %I:%M:%S %p #[fg=colour117]| %Y-%m-%d "

# Window titles
setw -g window-status-style fg=colour244,bg=default
setw -g window-status-current-style fg=colour117,bg=colour235,bold


# Refresh interval
set -g status-interval 1



```