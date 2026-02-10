

# 1  
- configjsonc - file 

```bash 

{
  "reload_style_on_change": true,
  "layer": "top",
  "position": "top",
  "spacing": 0,
  "height": 28,
  "modules-left": ["hyprland/workspaces"],
  "modules-center": ["clock", "custom/brightness"],
  "modules-right": [
    "group/tray-expander",
    "bluetooth",
    "custom/netspeed",
    "network",
    "pulseaudio",
    "battery",
    "custom/power"
  ],
  "custom/colorpicker": {
    "format": "{}",
    "exec": "cat /tmp/current_color.txt 2>/dev/null || echo '-----'",
    "on-click": "~/.config/waybar/colorscript/colorpicker.sh",
    "interval": 2,
    "tooltip": "Click to pick color"
  },
  "custom/netspeed": {
    "exec": "~/.config/waybar/script/netspdall.sh",
    "interval": 1,
    "format": "{}",
    "markup": "pango",
    "tooltip": true
  },
  "hyprland/workspaces": {
    "on-click": "activate",
    "on-scroll-up": "hyprctl dispatch workspace -5",
    "on-scroll-down": "hyprctl dispatch workspace +5",
    "format": "{icon}",
    "format-icons": {
      "default": "",
      "1": "1",
      "2": "2",
      "3": "3",
      "4": "4",
      "5": "5",
      "6": "6",
      "7": "7",
      "8": "8",
      "9": "9",
      "active": "󱓻"
    },
    "persistent-workspaces": {
      "1": [],
      "2": [],
      "3": [],
      "4": [],
      "5": [],
      "6": [],
      "7": []
    }
  },
  "cpu": {
    "interval": 5,
    "format": "󰍛",
    "on-click": "kitty -e btop"
  },
  "clock": {
    "format": "{:%A :%I:%M %p}",
    "format-alt": "{:%d %B W%V %Y}",
    "tooltip": true
  },
  "custom/brightness": {
    // "format": "{percent}% {icon}",
    // "format-icons": ["", "", "", "", "", "", "", "", ""]
    "format": "",
    "exec": "brightnessctl | grep -oP '\\d+(?=%)'",
    "interval": 5,
    "on-click": "brightnessctl | grep -oP '\\d+(?=%)'",
    "on-scroll-up": "brightnessctl set +5%",
    "on-scroll-down": "brightnessctl set 5%-",
    "tooltip": true

  },
  "network": {
    "format-icons": ["󰤯", "󰤟", "󰤢", "󰤥", "󰤨"],
    "format": "{icon}",
    "format-wifi": "{icon}",
    "format-ethernet": "",
    "format-disconnected": "󰖪",
    "tooltip-format-wifi": "{essid} ({frequency} GHz)\n⇣{bandwidthDownBytes}  ⇡{bandwidthUpBytes}",
    "tooltip-format-ethernet": "⇣{bandwidthDownBytes}  ⇡{bandwidthUpBytes}",
    "tooltip-format-disconnected": "Disconnected",
    "interval": 3,
    "spacing": 1,
    "on-click": "kitty --class=Impala -e impala"
  },
  "battery": {
    "format": "{capacity}% {icon}",
    "format-discharging": "{icon}",
    "format-charging": "{icon}",
    "format-plugged": "",
    "format-icons": {
      "charging": ["󰢜", "󰂆", "󰂇", "󰂈", "󰢝", "󰂉", "󰢞", "󰂊", "󰂋", "󰂅"],
      "default": ["󰁺", "󰁻", "󰁼", "󰁽", "󰁾", "󰁿", "󰂀", "󰂁", "󰂂", "󰁹"]
    },
    "format-full": "󰂅",
    "tooltip-format-discharging": "{power:>1.0f}W↓ {capacity}%",
    "tooltip-format-charging": "{power:>1.0f}W↑ {capacity}%",
    "interval": 5,
    "states": {
      "warning": 20,
      "critical": 10
    }
  },
  // ───────────────────────────────────────────────────────┤ power button ├───
  "custom/power": {
    "format": " ",
    "tooltip": false,
    "on-click": "~/.config/waybar/script/power-menu.sh"
  },
  // ────────────────────────────────────────────────────────────┤ padding ├───
  "bluetooth": {
    "format": "",
    "format-disabled": "󰂲",
    "format-connected": "",
    "tooltip-format": "Devices connected: {num_connections}",
    "on-click": "blueberry"
  },
  "pulseaudio": {
    "format": "{icon}",
    "on-click": "alacritty --class=Wiremix -e wiremix",
    "on-click-right": "pamixer -t",
    "tooltip-format": "Playing at {volume}%",
    "scroll-step": 2,
    "format-muted": "󰝟",
    "format-icons": {
      "default": ["", "", ""]
    }
  },
  "group/tray-expander": {
    "orientation": "inherit",
    "drawer": {
      "transition-duration": 600,
      "children-class": "tray-group-item"
    },
    "modules": ["custom/expand-icon", "tray"]
  },
  "custom/expand-icon": {
    "format": "󰧚",
    "tooltip": false
  },
  "tray": {
    "icon-size": 18,
    "spacing": 16
  }
}

```

# 2 
- Style.css

```bash 

@define-color bg    #1a1b26;
@define-color fg    #a9b1d6;
@define-color blk   #32344a;
@define-color red   #f7768e;
@define-color grn   #9ece6a;
@define-color ylw   #e0af68;
@define-color blu   #7aa2f7;
@define-color mag   #ad8ee6;
@define-color cyn   #0db9d7;
@define-color brblk #444b6a;
@define-color wht   #ffffff;

* {
    font-family: "JetBrainsMono Nerd Font", "Noto Color Emoji";
    font-size: 14px;
    font-weight: bold;
}

window#waybar {
    background: rgba(26, 27, 38, 0.25); /* 조금 더 visible */
    color: @fg;
}

/* ---------- Workspaces ---------- */
#workspaces button {
    padding: 2px 10px;
    margin: 0 3px;
    border-radius: 8px;
    color: @cyn;
    background: transparent;
    border-bottom: 2px solid @bg;
    border: 1px solid alpha(@cyn, 0.35); 
}

#workspaces button.active {
    border-bottom: 2px solid @mag;
    border: 1px solid alpha(@cyn, 0.35); 
}

#workspaces button.empty {
    color: @wht;
}

#workspaces button.empty.active {
    border-bottom: 2px solid @mag;
}

/* ---------- Common Modules ---------- */
#clock,
#pulseaudio,
#battery,
#bluetooth,
#network,
#custom-netspeed,
#custom-power,
#custom-brightness,
#tray {
    padding: 5px 12px;     /* padding ↑ */
    margin: 0 5px;         /* spacing ↑ */
    border-radius: 12px;   /* round ↑ */
    background: alpha(@blk, 0.95); 
}

/* ---------- Individual tuning ---------- */
#pulseaudio {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}
#custom-expand-icon {
    color: @blk;
}

#clock {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}

#battery {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}

#network {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}

#bluetooth {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}
#custom-netspeed {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}

#custom-power {
    color: @red;
    border: 1px solid alpha(@cyn, 0.35); 
}

#custom-brightness {
    color: @blu;
    border: 1px solid alpha(@cyn, 0.35); 
}


```

