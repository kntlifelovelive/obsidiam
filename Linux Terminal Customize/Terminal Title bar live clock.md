
---

## Ghostty ui title bar live clock 

```bash 


# Start Live Title Clock
clock_title_loop() {
    while true; do
        echo -ne "\033]0;🕒 $(date '+%I:%M:%S %p') | Welcome bubu\007"
        sleep 1
    done
}


# Only for interactive shell
if [[ $- == *i* ]]; then
    clock_title_loop &
fi


```


---

```bash


# Start Live Title Clock and Title Name 
clock_title_loop() {
    while true; do
        #echo -ne "\033]0; $(date '+%I:%M:%S %p') \007"
         echo -ne "\033]0; 💠 Babby BuBu, I love you .. more than 💠\007"
        sleep 1
    done
}


# Only for interactive shell
if [[ $- == *i* ]]; then
    clock_title_loop &
fi


```


---

![[Pasted image 20250729195508.png]]