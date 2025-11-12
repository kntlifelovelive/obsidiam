
---

## Lesson 7 – Searching & Finding Files (Advanced Mastery Level)

---

## 1  `find` – The File Hunter 

**Syntax Review:**

```bash
find [path] [criteria] [action]
```

➡ path = where to start  
➡ criteria = what to look for  
➡ action = what to do with found files


###  1.1 Find by Name (Pattern Matching)

**Example 1 – Exact match:**

```bash
find /home -name "notes.txt"
```

**Example 2 – Wildcard match:**

```bash
find ~/Documents -name "*.pdf"
```

**Example 3 – Case-insensitive search:**

```bash
find /etc -iname "*.CONF"
```

 **Tip**  
`-iname` က case-insensitive;  
`-name` က case-sensitive.



###  1.2 Find by Type

|Type|Description|
|---|---|
|`-type f`|Regular file|
|`-type d`|Directory|
|`-type l`|Symlink|

**Example:**

```bash
find /usr -type d -name "bin"
```

➡ `/usr` အောက်က “bin” directory တွေရှာတယ်။



### 1.3 Find by Size

|Option|Description|
|---|---|
|`+`|Greater than|
|`-`|Less than|
|No sign|Exactly|

**Examples:**

```bash
find / -size +500M        # 500MB ထက်ကြီး
find ~/Downloads -size -10k  # 10KB ထက်ငယ်
find . -size 100M         # 100MB တိတိ
```

 _Tip_ Size unit တွေ – `c` (bytes), `k`, `M`, `G`.



###  1.4 Find by Date & Time

|Option|Description|
|---|---|
|`-mtime`|Modified days ago|
|`-atime`|Accessed days ago|
|`-ctime`|Changed (metadata) days ago|

**Examples:**

```bash
find /home -mtime -1    # modified within 1 day
find /var/log -atime +10 # not accessed for 10+ days
find /etc -ctime 0       # changed today
```

---

###  1.5 Find by Permission / Owner

```bash
find / -user root
find / -group www-data
find /var -perm 644
find /var -perm -u=w
```

 **Advanced Permission Find**

```bash
find / -perm /222
```

➡ writable by _anyone_ (dangerous security check!)


###  1.6 Find & Execute Actions

####   `-exec` (Classic Method)

**Example – delete old `.log` files:**

```bash
find /var/log -name "*.log" -mtime +7 -exec rm -f {} \;
```

**Example – count lines in each `.conf`:**

```bash
find /etc -name "*.conf" -exec wc -l {} \;
```

 `{}` is placeholder for file name  
`\;` means command end



####  `-exec ... +` (Batch Mode)

```bash
find . -name "*.jpg" -exec mv -t ~/Pictures {} +
```

➡ run command once for many files (faster).

####  Combine with Pipe & xargs

```bash
find . -name "*.mp3" | xargs ls -lh
```

➡ list all found mp3 files with details.

 **Performance Tip:**  
`xargs` သုံးတာက `-exec` ထက်မြန်တယ် (batch mode).



###  1.7 Find by Content (With grep combo)

```bash
find /etc -type f -name "*.conf" -exec grep -H "network" {} \;
```

➡ “network” ပါတဲ့ `.conf` files တွေရှာတယ်။

 `-H` = show filename with match.



###  1.8 Find & Delete Empty Files or Dirs

```bash
find /tmp -type f -empty -delete
find ~/Downloads -type d -empty -delete
```



 **Data Flow Diagram**

```
[Find criteria] → matched files → [action: exec / xargs / delete]
```



## 2 `locate` – Instant Search 

 Database-based search system (`mlocate.db`)  
Speed:  Super fast (but may be outdated)

###  2.1 Examples

```bash
locate nginx.conf
locate -i wallpaper.jpg
locate --regex '.*\.mp3$'
```

###  2.2 Update Database

```bash
sudo updatedb
```

 Pro Tip: Run weekly cron to refresh.



 Diagram:

```
locate → search in /var/lib/mlocate/mlocate.db → show result
```



## 3 `grep` – Text Pattern Search Master 



###  3.1 Basic Patterns

```bash
grep "bash" /etc/passwd
grep -i "linux" /var/log/syslog
```



###  3.2 Recursive Search

```bash
grep -r "network" /etc/
```

➡ search inside all files in `/etc`.



###  3.3 Exclude Matches

```bash
grep -v "nologin" /etc/passwd
```

➡ Exclude users with “nologin”.



###  3.4 Show Line Numbers

```bash
grep -n "root" /etc/passwd
```



###  3.5 Regex Patterns (Advanced)

**Emails:**

```bash
grep -E "[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}" users.txt
```

**IP Addresses:**

```bash
grep -E "([0-9]{1,3}\.){3}[0-9]{1,3}" logs.txt
```

**URLs:**

```bash
grep -E "https?://[a-zA-Z0-9./?=_-]*" webdata.txt
```



###  3.6 Highlight Matches

```bash
grep --color=always "error" /var/log/syslog
```



 Diagram:

```
File → [grep regex filter] → Matching lines only
```



## 4 `xargs` – Command Chain Linker 

-  Transform standard input (pipe output) into command arguments.



###  4.1 Basic Example

```bash
find . -name "*.png" | xargs ls -lh
```

➡ Pass list of `.png` files to `ls -lh`.



###  4.2 Safer (Spaces in filenames)

```bash
find . -name "*.mp3" -print0 | xargs -0 ls -l
```

➡ `-print0` & `-0` = handle spaces safely.



###  4.3 Use with grep

```bash
cat filelist.txt | xargs grep "Linux"
```

###  4.4 Delete files (confirmation)

```bash
find . -name "*.bak" | xargs -p rm
```

➡ ask before deleting each.



 Diagram:

```
[find output] → [pipe] → [xargs] → [target command]
```



## 5 Combined Real-world Power Examples 



###  Example 1 – Find large log files older than 7 days and compress them

```bash
find /var/log -type f -name "*.log" -mtime +7 -exec gzip {} \;
```




###  Example 2 – Search for `.py` files containing “socket” keyword

```bash
find ~/projects -type f -name "*.py" -exec grep -H "socket" {} \;
```



###  Example 3 – Delete empty dirs & count remaining

```bash
find ~/Downloads -type d -empty -delete
find ~/Downloads -type d | wc -l
```



###  Example 4 – Backup only `.conf` files

```bash
find /etc -name "*.conf" | tar -czvf conf_backup.tar.gz -T -
```



###  Example 5 – System-wide search for writable files

```bash
find / -perm -002 -type f 2>/dev/null
```

➡ Find world-writable files (potential vulnerabilities )



###  Example 6 – Search for recently modified scripts

```bash
find ~/scripts -name "*.sh" -mtime -2 -exec ls -lh {} \;
```



## 6 Bonus Tools for Pro Level

|Tool|Purpose|Example|
|---|---|---|
|`ag`|The Silver Searcher (faster grep)|`ag network /etc`|
|`ripgrep (rg)`|ultra-fast recursive search|`rg "error" /var/log`|
|`fd`|modern find replacement|`fd --type f ".conf"`|



##  Summary Table

|Command|Description|Example|
|---|---|---|
|`find`|Real-time file search|`find /home -name "*.txt"`|
|`locate`|Instant search (cached)|`locate nginx.conf`|
|`grep`|Pattern text search|`grep -r "error" /var/log`|
|`xargs`|Chain commands|`find . -name "*.jpg"|
|`-exec`|Execute per file|`find . -exec wc -l {} \;`|



##  Homework (Mastery Challenge )

1. Find all `.sh` files edited in the last 2 days and show line count.
2. Search `/etc` for “password” keyword (case-insensitive).
3. Find all writable files owned by non-root users.
4. Combine `find` + `tar` to backup `.log` files only.
5. Create a `grep` regex that detects IP addresses and highlight them.
6. Bonus  – Write one-liner that finds `.conf` files with “Listen” inside and lists size sorted descending:

```bash
   find /etc -name "*.conf" -exec grep -l "Listen" {} \; | xargs du -h | sort -hr
```


“`find`, `grep`, `xargs`” သုံးတတ်သူတစ်ယောက်ဆိုရင်   — data searching ကို SQL မရှိပေမယ့် Linux filesystem ပေါ်မှာ direct run နိုင်တယ်။   ဒါကြောင့် သူ့ရဲ့ logic နဲ့ pattern control skill ကတော့ Hacker-grade ဖြစ်သွားတယ် 

---
