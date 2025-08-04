




```bash 
mkdir -p ~/full_termux_backup

# Go to home  
cd ~

# Use tar (better for dotfiles/folders) ✅  
tar --exclude='./full_termux_backup' -czvf ~/storage/downloads/ADM/full_termux_backup.tar.gz \  
.bashrc \  
.bash_history \  
.config \  
.termux \  
.local \  
.cache \  
.ssh \  
.suroot \  
.mpd \  
.npm \  
.npmrc \  
.wget-hsts \  
.vim \  
CamPhish \  
lua-language-server \  
test.sh


```


---


```bash 
# Termux storage permission ပေး
termux-setup-storage

# Go to Downloads
cd ~/storage/downloads/ADM 

# Extract backup
tar -xzvf full_termux_backup.tar.gz -C ~/

echo "✅ Restore Complete! Restart Termux to apply all configs."

```