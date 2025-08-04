
## Step 1 . docker Kali run 

```
sudo docker run -d --name kali-vnc \
  -p 9020:8080 \    # Web GUI (optional)
  -p 9021:5901 \    # VNC port
  iphoneintosh/kali-docker:latest
  
```

```
sudo docker run -d --name kali-gui -p 9020:8080 -p 9021:5901 iphoneintosh/kali-docker:latest 
```

## step 2 . Host terminal run command 

```
sudo docker exec -it kali-gui bash
vncserver :1
```

###  step 3 . Vncserver or Browser call localhost for Gui mode 

- **Ubuntu  VNC Viewer မှာ localhost:9021ချိပ်ပါ**

```
localhost:9021
```

