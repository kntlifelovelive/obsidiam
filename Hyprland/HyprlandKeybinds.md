

```bash 

bind = $mainMod SHIFT, F, fullscreen # whole full screen
bind = $mainMod CTRL, F, fullscreen, 1 # fake full screen
bind = $mainMod, SPACE, togglefloating, #Float Mode
bind = $mainMod ALT, SPACE, exec, hyprctl dispatch workspaceopt allfloat #All Float Mode
bind = $mainMod SHIFT, Return, exec, $scriptsDir/Dropterminal.sh $term # Dropdown terminal

# Desktop zooming or magnifier
bind = $mainMod ALT, mouse_down, exec, hyprctl keyword cursor:zoom_factor "$(hyprctl getoption cursor:zoom_factor | awk 'NR==1 {factor = $2; if (factor < 1) {factor = 1}; print factor * 2.0}')"
bind = $mainMod ALT, mouse_up, exec, hyprctl keyword cursor:zoom_factor "$(hyprctl getoption cursor:zoom_factor | awk 'NR==1 {factor = $2; if (factor < 1) {factor = 1}; print factor / 2.0}')"

# ====== My Config ==================
bind = $mainMod, B, exec, brave # browser
bind = $mainMod CTRL, T, exec, Telegram # Multi Media
bind = $mainMod, Z, exec, zoom
bind = $mainMod CTRL, V, exec, code # Vscode Editor
bind = $mainMod CTRL, S, exec, subl # Sublime-text Editor
bind = $mainMod, X, exec, firefox # browser
bind = $mainMod CTRL, O, exec, outline-client # Outline-Client Vpn
bind = $mainMod CTRL, G, exec, google-chrome-stable # Google-Chrome-stable Browser
bind = $mainMod ALT, O, exec, obsidian # Note-taking for best  
bind = $mainMod, C, exec, celluloid # Move Player 
bind = $mainMod ALT, G, exec, ghostty # Terminal 
# ------------------------------
#  Screenshot Keybindings (No $mainMod)
# ------------------------------

#  PrintScreen = Select Area & Save to ~/Pictures
bind = , Print, exec, grimblast copysave area ~/Pictures/Screenshots/-$(date +%Y-%m-%d_%H-%M-%S).png

#  Shift+PrintScreen = Fullscreen Screenshot & Save
bind = SHIFT, Print, exec, grimblast copysave screen ~/Pictures/Screenshots/-$(date +%Y-%m-%d_%H-%M-%S).png

#  Ctrl+PrintScreen = Select Area & Copy to Clipboard (no file saved)
bind = CTRL, Print, exec, grimblast copy area

#  Alt+PrintScreen = Active Window Screenshot & Save
bind = ALT, Print, exec, grimblast copysave active ~/Pictures/Screenshots/-$(date +%Y-%m-%d_%H-%M-%S).png

# ========================
# 🎥 Video Recording
# ========================

#  Region Select + System Sound (Bluetooth / Speakers)
bind = , F7, exec, wf-recorder -g "$(slurp)" -a bluez_output.41_42_94_97_08_57.1.monitor -f ~/Videos/screencast/record-system-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🎥 Recording Started (System Sound)"

#  Region Select + Microphone (Voice)
bind = SHIFT, F10, exec, wf-recorder -g "$(slurp)" -a alsa_input.pci-0000_00_1f.3.analog-stereo -f ~/Videos/screencast/record-mic-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🎤 Recording Started (Mic)"

#  Fullscreen + System Sound
bind = , F8, exec, wf-recorder -a bluez_output.41_42_94_97_08_57.1.monitor -f ~/Videos/screencast/fullscreen-system-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🖥️ Recording Fullscreen (System Sound)"

#  Fullscreen + Microphone
# bind = SHIFT, F9, exec, wf-recorder -a alsa_input.pci-0000_00_1f.3.analog-stereo -f ~/Videos/screencast/fullscreen-mic-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🖥️ Recording Fullscreen (Mic)"

#  Fullscreen (No Audio)
bind = SHIFT, F5, exec, wf-recorder -f ~/Videos/screencast/fullscreen-$(date +%Y-%m-%d_%H-%M-%S).mp4 && notify-send "🖥️ Recording Fullscreen (No Audio)"

#  Stop Recording
bind = , F11, exec, pkill -SIGINT wf-recorder && notify-send "⏹ Recording Stopped" "Saved to ~/Videos/screencast"

#==============================#

```