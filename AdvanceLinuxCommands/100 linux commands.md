
Linux ကို အသုံးပြုရာတွင် အသုံးများသော commands 100 ခုကို ဥပမာများနှင့် အောက်ပါအတိုင်း စုစည်းဖော်ပြထားပါသည်။

---

### **1. File & Directory Management**
1. **`ls`** – Directory ထဲမှ file များကို ကြည့်ရန်  
   `ls -l` (အသေးစိတ်), `ls -a` (hidden files ပါကြည့်)

2. **`cd`** – Directory ပြောင်းရန်  
   `cd /var/www`, `cd ..` (အထက်တစ်ဆင့်)

3. **`pwd`** – Current directory လမ်းကြောင်းကို ပြရန်  
   `pwd`

4. **`mkdir`** – အသစ် directory ဖန်တီးရန်  
   `mkdir new_folder`, `mkdir -p dir1/dir2` (Path အပြည့်ဖန်တီး)

5. **`rmdir`** – အလွတ် directory ဖျက်ရန်  
   `rmdir empty_dir`

6. **`touch`** – အလွတ် file အသစ်ဖန်တီးရန်  
   `touch file.txt`

7. **`cp`** – File/directory ကော်ပီကူးရန်  
   `cp file.txt backup/`, `cp -r dir1 dir2` (directory ကူး)

8. **`mv`** – File/directory ရွှေ့ရန်/နာမည်ပြောင်း  
   `mv old.txt new.txt`, `mv file.txt ~/Documents`

9. **`rm`** – File/directory ဖျက်ရန်  
   `rm file.txt`, `rm -rf dir` (အားလုံးဖျက်)

10. **`cat`** – File content ကို terminal တွင် ဖတ်ရန်  
    `cat notes.txt`, `cat file1.txt file2.txt > combined.txt`

---

### **2. File Content & Text Processing**
11. **`more` / `less`** – File ကို page လိုက်ဖတ်ရန်  
    `more large_file.log`, `less -N code.py`

12. **`head`** – File ရဲ့ ထိပ်ဆုံး 10 လိုင်းကို ဖတ်ရန်  
    `head -n 5 data.csv`

13. **`tail`** – File ရဲ့ နောက်ဆုံး 10 လိုင်းကို ဖတ်ရန်  
    `tail -f live_log.log` (real-time update)

14. **`grep`** – Text pattern ရှာရန်  
    `grep "error" log.txt`, `grep -i "warning" *.log`

15. **`sed`** – Stream editor (text replace)  
    `sed 's/old/new/g' file.txt`, `sed -i 's/foo/bar/g' file.txt`

16. **`awk`** – Text processing အတွက် programming tool  
    `awk '{print $1}' data.txt`, `awk -F',' '/search/ {print $2}' file.csv`

17. **`nano` / `vim`** – Terminal-based text editors  
    `nano notes.txt`, `vim script.sh`

18. **`echo`** – Text/Variable ကို ပြရန်  
    `echo "Hello World"`, `echo $PATH`

19. **`sort`** – File content ကို စီရန်  
    `sort names.txt`, `sort -r numbers.txt` (ပြောင်းပြန်)

20. **`uniq`** – ထပ်နေသော လိုင်းများကို ဖယ်ရန်  
    `uniq data.txt`, `sort file.txt | uniq -c`

---

### **3. Permissions & Ownership**
21. **`chmod`** – File permissions ပြောင်းရန်  
    `chmod 755 script.sh`, `chmod +x executable`

22. **`chown`** – File owner ပြောင်းရန်  
    `chown user:group file.txt`, `chown -R www-data /var/www`

23. **`chgrp`** – File group ပြောင်းရန်  
    `chgrp developers app.py`

24. **`sudo`** – Admin အခွင့်နဲ့ command ကို run  
    `sudo apt update`, `sudo nano /etc/hosts`

25. **`su`** – User account ပြောင်းရန်  
    `su - username`, `sudo su -`

26. **`passwd`** – Password ပြောင်းရန်  
    `passwd`, `sudo passwd username`

---

### **4. System & Process Management**
27. **`ps`** – Running processes များကို ကြည့်ရန်  
    `ps aux`, `ps -ef | grep nginx`

28. **`top` / `htop`** – Real-time system monitor  
    `top`, `htop` (interactive)

29. **`kill`** – Process ကို သတ်ရန် (PID သုံး)  
    `kill 1234`, `kill -9 5678` (အင်အားသုံး)

30. **`systemctl`** – Services များကို စီမံရန်  
    `systemctl start nginx`, `systemctl enable docker`

31. **`journalctl`** – System logs ကြည့်ရန်  
    `journalctl -u nginx`, `journalctl --since "2023-01-01"`

32. **`df`** – Disk space ကြည့်ရန်  
    `df -h`, `df -hT /home`

33. **`du`** – Directory size ကြည့်ရန်  
    `du -sh /var`, `du -ah --max-depth=1`

34. **`free`** – Memory usage ကြည့်ရန်  
    `free -m`, `free -h`

35. **`uname`** – System info ကြည့်ရန်  
    `uname -a`, `uname -r` (kernel version)

---

### **5. Networking**
36. **`ping`** – Network connection စမ်းရန်  
    `ping google.com`, `ping -c 4 192.168.1.1`

37. **`ifconfig` / `ip`** – Network interfaces ကြည့်ရန်  
    `ifconfig`, `ip addr show`

38. **`curl`** – Web data download/upload  
    `curl -O https://example.com/file.zip`, `curl -I example.com`

39. **`wget`** – File download လုပ်ရန်  
    `wget https://example.com/image.jpg`

40. **`ssh`** – Remote server ကို ချိတ်ရန်  
    `ssh user@192.168.1.100`, `ssh -p 2222 user@host`

41. **`scp`** – File ကို SSH နဲ့ ကူးရန်  
    `scp file.txt user@remote:/path`, `scp -r dir user@remote:/path`

42. **`netstat`** – Network connections ကြည့်ရန်  
    `netstat -tulpn`, `netstat -an | grep ESTABLISHED`

43. **`nslookup` / `dig`** – DNS query လုပ်ရန်  
    `nslookup example.com`, `dig +short example.com`

44. **`traceroute`** – Network path ကို စစ်ရန်  
    `traceroute google.com`, `traceroute -I 8.8.8.8`

45. **`nc` (netcat)** – Networking tool for TCP/UDP  
    `nc -zv example.com 80`, `nc -l 8080`

---

### **6. Package Management**
46. **`apt` (Debian/Ubuntu)**  
    `sudo apt update`, `sudo apt install nginx`

47. **`yum` (RHEL/CentOS)**  
    `sudo yum install httpd`, `sudo yum update`

48. **`dnf` (Fedora)**  
    `sudo dnf install git`, `sudo dnf upgrade`

49. **`pacman` (Arch)**  
    `sudo pacman -Syu`, `pacman -Qs python`

50. **`snap`**  
    `sudo snap install chromium`, `snap list`

---

### **7. Compression & Archives**
51. **`tar`** – Archive files  
    `tar -cvf archive.tar dir/`, `tar -xvf backup.tar`

52. **`gzip` / `gunzip`**  
    `gzip file.txt`, `gunzip file.txt.gz`

53. **`zip` / `unzip`**  
    `zip archive.zip file1.txt`, `unzip data.zip -d output/`

54. **`rsync`** – Sync files/directories  
    `rsync -av source/ user@remote:/dest/`

---

### **8. Searching & Filters**
55. **`find`** – Files ရှာရန်  
    `find /home -name "*.txt"`, `find / -type f -size +100M`

56. **`locate`** – Database မှ လျင်မြန်စွာ ရှာရန်  
    `locate .bashrc`, `sudo updatedb`

57. **`which`** – Command path ကို ပြရန်  
    `which python`, `which git`

58. **`whereis`** – Command နဲ့ဆိုင်သော files များ  
    `whereis node`, `whereis -b java`

---

### **9. User & Group Management**
59. **`useradd` / `adduser`** – User အသစ်ထည့်ရန်  
    `sudo useradd john`, `sudo adduser sarah`

60. **`usermod`** – User settings ပြောင်းရန်  
    `sudo usermod -aG sudo john` (sudo access ပေး)

61. **`groupadd`** – Group အသစ်ထည့်ရန်  
    `sudo groupadd devs`

---

### **10. Miscellaneous**
62. **`history`** – ရှေးက run ခဲ့သော commands များ  
    `history`, `!100` (history ID 100 ကို ပြန် run)

63. **`crontab`** – Scheduled tasks  
    `crontab -e`, `*/5 * * * * /path/script.sh`

64. **`alias`** – Command shortcuts သတ်မှတ်ရန်  
    `alias ll='ls -alF'`, `alias update='sudo apt update'`

65. **`date`** – လက်ရှိ ရက်စွဲနှင့် အချိန်  
    `date`, `date +"%Y-%m-%d %H:%M:%S"`

66. **`cal`** – Calendar ပြရန်  
    `cal`, `cal -y 2024`

67. **`bc`** – Calculator  
    `echo "5 + 3" | bc`, `bc -l` (သင်္ချာ function များ)

68. **`shutdown`** – System ကို ပိတ်ရန်/restart  
    `sudo shutdown -h now`, `sudo reboot`

69. **`watch`** – Command output ကို update လုပ်ပြရန်  
    `watch -n 2 free -m` (အချိန် 2စက္ကန့်တိုင်း update)

70. **`man`** – Command manual ကြည့်ရန်  
    `man ls`, `man grep`

---

### **အဆင့်မြင့် Commands များ**
71. **`lsof`** – Open files များကို စစ်ဆေးရန်  
    `lsof -i :80`, `lsof /var/log`

72. **`strace`** – System calls များကို trace လုပ်ရန်  
    `strace -e trace=open,read ls`

73. **`dd`** – Disk/image operations  
    `dd if=/dev/sda of=backup.img bs=4M`

74. **`mount` / `umount`** – Disk ချိတ်ရန်/ဖြုတ်ရန်  
    `sudo mount /dev/sdb1 /mnt`, `sudo umount /mnt`

75. **`diff`** – File differences ကို ကြည့်ရန်  
    `diff file1.txt file2.txt`, `diff -r dir1 dir2`

76. **`tee`** – Output ကို file နဲ့ screen မှာ ပြရန်  
    `echo "Hello" | tee output.txt`

77. **`xargs`** – Command output ကို input အဖြစ်သုံးရန်  
    `find . -name "*.log" | xargs rm`

78. **`screen` / `tmux`** – Terminal multiplexers  
    `screen -S session1`, `tmux new -s dev`

79. **`ln`** – Hard/Soft links ဖန်တီးရန်  
    `ln -s /path/file link_name` (symbolic link)

80. **`stat`** – File details ကြည့်ရန်  
    `stat file.txt`, `stat -c "%U %G" /etc/passwd`

---

### **Scripting & Automation**
81. **`bash`** – Bash script run ရန်  
    `bash script.sh`, `chmod +x script.sh && ./script.sh`

82. **`source`** – Script ကို current shell တွင် run  
    `source ~/.bashrc`

83. **`export`** – Environment variable သတ်မှတ်ရန်  
    `export PATH=$PATH:/new/path`, `export VAR=value`

84. **`cron`** – Scheduled jobs  
    `crontab -e` ဖြင့် `0 3 * * * /backup.sh`

85. **`at`** – One-time scheduled task  
    `echo "shutdown -h now" | at 23:00`

---

### **Development Tools**
86. **`git`** – Version control  
    `git clone https://repo.url`, `git commit -m "message"`

87. **`docker`** – Container management  
    `docker ps -a`, `docker build -t myapp .`

88. **`python3`** – Python interpreter  
    `python3 script.py`, `python3 -m http.server 8000`

89. **`node` / `npm`** – JavaScript runtime & package manager  
    `node app.js`, `npm install express`

90. **`gcc`** – C code compile  
    `gcc hello.c -o hello`, `g++ program.cpp -o output`

---

### **Security & Monitoring**
91. **`ufw`** – Firewall management  
    `sudo ufw enable`, `sudo ufw allow 22/tcp`

92. **`fail2ban`** – Intrusion prevention  
    `sudo fail2ban-client status sshd`

93. **`openssl`** – SSL/TLS tools  
    `openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -out cert.pem`

94. **`nmap`** – Network scanning  
    `nmap -sV 192.168.1.1`, `nmap -p 80,443 example.com`

95. **`tcpdump`** – Network traffic capture  
    `tcpdump -i eth0 port 80`, `tcpdump -w capture.pcap`

---

### **Hardware Info**
96. **`lshw`** – Hardware details  
    `sudo lshw -short`, `lshw -html > hardware.html`

97. **`lsblk`** – Block devices များကို ပြရန်  
    `lsblk`, `lsblk -o NAME,SIZE,MOUNTPOINT`

98. **`lspci`** – PCI devices များ  
    `lspci`, `lspci -v | grep VGA`

99. **`dmidecode`** – System hardware info (DMI)  
    `sudo dmidecode -t memory`, `sudo dmidecode -s system-serial-number`

100. **`sensors`** – CPU/System temperatures  
    `sensors`, `sudo apt install lm-sensors` (အရင်တပ်ဆင်ရန်)

---

