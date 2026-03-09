
---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=7AA2F7&background=1E1E2E&fontWeight=bold&vCenter=true&width=450&height=35&lines=EZA Advanced Commands" width="450"/>
</div>

---


|Command|Meaning|Example|
|---|---|---|
|`eza -l`|long format list|`eza -l`|
|`eza -lh`|human readable size|`eza -lh`|
|`eza -a`|show hidden files|`eza -a`|
|`eza -la`|long + hidden|`eza -la`|
|`eza --header`|show column header|`eza -lh --header`|
|`eza --icons`|show file icons|`eza --icons`|
|`eza --icons=always`|force icons|`eza --icons=always`|
|`eza --tree`|directory tree view|`eza --tree`|
|`eza --tree -L 2`|tree depth limit|`eza --tree -L 2`|
|`eza -R`|recursive listing|`eza -R`|
|`eza -s size`|sort by size|`eza -s size`|
|`eza -s modified`|sort by modified time|`eza -s modified`|
|`eza -s name`|sort by name|`eza -s name`|
|`eza -r`|reverse sorting|`eza -s size -r`|
|`eza -t`|sort by time|`eza -t`|
|`eza -S`|sort by size shortcut|`eza -S`|
|`eza -X`|sort by extension|`eza -X`|
|`eza -d`|list directories only|`eza -d */`|
|`eza -D`|directories only (no files)|`eza -D`|
|`eza --group-directories-first`|dirs first|`eza --group-directories-first`|
|`eza --git`|show git status|`eza --git`|
|`eza --git-ignore`|hide git ignored files|`eza --git-ignore`|
|`eza --binary`|show binary size|`eza --binary`|
|`eza --bytes`|show exact bytes|`eza --bytes`|
|`eza --inode`|show inode number|`eza --inode`|
|`eza --links`|show hard link count|`eza --links`|
|`eza --mounts`|show mount points|`eza --mounts`|
|`eza --no-permissions`|hide permissions column|`eza --no-permissions`|
|`eza --no-user`|hide user column|`eza --no-user`|
|`eza --no-time`|hide time column|`eza --no-time`|
|`eza --long`|same as `-l`|`eza --long`|
|`eza --all`|same as `-a`|`eza --all`|
|`eza --color=always`|force color output|`eza --color=always`|
|`eza --color=never`|disable color|`eza --color=never`|
|`eza --time=modified`|show modified time|`eza --time=modified`|
|`eza --time=created`|show creation time|`eza --time=created`|

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=7AA2F7&background=1E1E2E&fontWeight=bold&vCenter=true&width=450&height=35&lines=Power Examples Real usage" width="450"/>
</div>


---

<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=1 Best daily command" width="450"/>
</div>


```bash
eza -lh --icons --header
```

Example output

```
Permissions User Size Modified Name
drwxr-xr-x kyaw 4.0K Mar 9 folder
-rw-r--r-- kyaw 1.3K Mar 9 script.sh
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=2 Developer View" width="450"/>
</div>


```bash
eza -lh --git --icons --header
```

Git status ပါပြတယ်

```
M script.py
? newfile.js
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=3 Tree Explorer" width="450"/>
</div>


```bash
eza --tree --icons
```

```
.
├── 📄 file.txt
├── 🐍 script.py
└── 📂 project
    └── index.html
```

---



<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=4 Folder first sorting " width="450"/>
  </div>


```bash
eza -lh --group-directories-first
```

Output

```
📂 folders
📂 projects
📄 file.txt
📄 script.sh
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=5 Hidden files inspection" width="450"/>
</div>


```bash
eza -lah --header
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=Crazy power combo" width="450"/>
</div>


```bash
eza -lah --icons --git --group-directories-first --header
```

ဒါက Linux users တော်တော်များများ alias ထားကြတဲ့ command ပါ။

Example alias

```bash
alias ls="eza -lah --icons --git --group-directories-first --header"
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=Tree + size explorer" width="450"/>
</div>


```bash
eza --tree -L 2 -lh
```

Output

```
.
├── project
│   ├── main.py
│   └── config.json
└── notes.txt
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=Directory size analysis" width="450"/>
</div>


```bash
eza -lhS
```

size အကြီးဆုံးက အပေါ်မှာပြမယ်။

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=Only directories" width="450"/>
</div>


```bash
eza -D
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=Git project overview" width="450"/>
</div>


```bash
eza --git --icons --tree
```


---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=EZA 15 Killer Combos" width="450"/>
</div>


|#|Use Case|Command|
|---|---|---|
|1|Best daily ls replacement|`eza -lah --icons --header`|
|2|Developer project view|`eza -lah --icons --git --header`|
|3|Directory tree explorer|`eza --tree --icons`|
|4|Limited depth tree|`eza --tree -L 2`|
|5|Folder first sorting|`eza -lh --group-directories-first`|
|6|Biggest files first|`eza -lhS`|
|7|Recently modified files|`eza -lht`|
|8|File extension sorting|`eza -lhX`|
|9|Hidden file inspection|`eza -lah`|
|10|Only directories view|`eza -D`|
|11|Recursive file scan|`eza -lR`|
|12|Disk usage overview|`eza -lh --total-size`|
|13|Git repository overview|`eza --git --icons`|
|14|Clean minimal output|`eza --icons --no-user --no-time`|
|15|Full system audit view|`eza -lah --git --icons --group-directories-first --header`|

---

<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=1 Best daily command" width="450"/>
</div>


```bash
eza -lah --icons --header
```

Output example

```
Permissions User Size Modified Name
drwxr-xr-x kyaw 4.0K Mar 9 📂 project
-rw-r--r-- kyaw 1.2K Mar 9 📄 notes.txt
```

✔ hidden files  
✔ icons  
✔ header

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=2 Developer project view" width="450"/>
</div>


```bash
eza -lah --icons --git --header
```

Git status ပါပြမယ်။

Example

```
M main.py
? newfile.js
```

✔ git modified  
✔ untracked files

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=3 Project tree explorer" width="450"/>
</div>


```bash
eza --tree --icons
```

Output

```
.
├── 📄 notes.txt
├── 🐍 script.py
└── 📂 project
    ├── index.html
    └── style.css
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=465&height=25&lines=4 Large directory tree limit" width="480"/>
</div>


```bash
eza --tree -L 2
```

Depth 2 အထိပဲပြမယ်။

---

<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=5 Folder first layout" width="450"/>
</div>


```bash
eza -lh --group-directories-first
```

Output

```
📂 projects
📂 downloads
📄 notes.txt
📄 script.sh
```

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=485&height=25&lines=6 Bigger files finder" width="480"/>
</div>


```bash
eza -lhS
```

Output

```
5.2G movie.mkv
1.2G backup.tar
200M iso.img
```

✔ storage analysis

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=7 Recently modified files" width="450"/>
</div>


```bash
eza -lht
```

Output

```
Mar 9 script.sh
Mar 8 notes.txt
Mar 6 archive.tar
```

✔ newest first

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=8 File extension sorting" width="450"/>
</div>


```bash
eza -lhX
```

Output

```
file.txt
notes.txt
script.sh
archive.tar
```

✔ extension grouping

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=9 Hidden file audit" width="450"/>
</div>


```bash
eza -lah
```

Output

```
.bashrc
.gitconfig
.zshrc
```

✔ dot files inspection

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=10 Only directories" width="450"/>
</div>

```bash
eza -D
```

Output

```
Documents
Downloads
Pictures
```

✔ folder overview

---



<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=485&height=25&lines=11 Recursive directory scan" width="450"/>
</div>


```bash
eza -lR
```

Output

```
./project
main.py
config.json

./project/assets
logo.png
```

✔ recursive listing

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=12 Disk usage overview" width="450"/>
</div>


```bash
eza -lh --total-size
```

Output

```
file1.txt 2K
file2.txt 3K

Total: 5K
```

✔ folder size summary

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=13 Git repository overview" width="450"/>
</div>


```bash
eza --git --icons
```

Output

```
M main.py
? test.py
```

✔ git status

---

<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=14 Minimal clean view" width="450"/>
</div>


```bash
eza --icons --no-user --no-time
```

Output

```
📂 project
📄 notes.txt
```

✔ minimal output

---


<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=465&height=25&lines=15 Ultimate power command" width="450"/>
</div>


```bash
eza -lah --icons --git --group-directories-first --header
```

Output

```
Permissions User Size Modified Name
drwxr-xr-x kyaw 4.0K Mar 9 📂 project
-rw-r--r-- kyaw 1.2K Mar 9 🐍 script.py
```

✔ icons  
✔ git  
✔ header  
✔ folder first  
✔ hidden files

---



<div align="left">
  <img src="https://readme-typing-svg.herokuapp.com?font=Lexend+Giga&size=25&pause=1000&color=F5C2E7&fontWeight=bold&vCenter=true&width=435&height=25&lines=Crazy useful command" width="450"/>
</div>


### Project structure viewer

```bash
eza --tree --icons --git-ignore
```

✔ `.gitignore` files မပြဘူး  
✔ clean project view

---

