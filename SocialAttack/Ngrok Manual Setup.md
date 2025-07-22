
## Step 1. Ngrok Download 

-  **Ngrok official site**
- [Ngrok download link ](https://ngrok.com/download)
- Linux 64-bit for zip download 
- Terminal direct link 

```
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-stable-linux-amd64.zip
```
## Step 2 . Unzip for Ngrok zip file 

```
unzip ngrok-stable-linux-amd64.zip
```

## Step 3 . Ngrok Auth Token input 

```
./ngrok config add-authtoken <YOUR_AUTHTOKEN_HERE>
```

# **Note**
**Ngrok official site on new Account , Auth Token  take it**

## Step 4 . Ngrok Port 3333 Expose 

```
./ngrok http 3333
```

# *Ngrok Shortcut* 
- **Terminal for everywhere call ngrok**
```
sudo chmod +x ngrok 
sudo mv or cp ngrok/usr/local/bin/
```

