
### ✅ Prepration Command

```
curl -fsSL https://get.docker.com | sh
```
or

```
apt/yum install docker.io
```

### Now we are creating following base on docker image 
 - Chrom
 - Firefox
 - Linux desktop
and then endpoint will be available at (http(s)://IP:Port)

-----------------------------------------------------------------------------------

### Variables

you can change these variables as you wish before running docker (PORT, NAME, USERNAME, PASSWORD)

          -e TITLE=NAME \
          -e CUSTOM_USER=USERNAME \
          -e PASSWORD=PASSWORD \
          -p PORT:3000 \
          -p PORT:3001 \

          
### ✅ Chromium
```
    docker run -d \
        --name=chromium \
        --security-opt seccomp=unconfined \
        -e PUID=1000 \
        -e PGID=1000 \
        -e TZ=Etc/UTC \
        -e CUSTOM_USER=admin \
        -e PASSWORD=admin#admin \
        -e CHROME_CLI=OPIran \
        -p 5000:3000 \
        -p 5001:3001 \
        -v /path/to/config:/config \
        --shm-size="1gb" \
        --restart unless-stopped \
        lscr.io/linuxserver/chromium:latest
```

### ✅ Firefox
```
     docker run -d \
          --name=firefox \
          --security-opt seccomp=unconfined \
          -e PUID=1000 \
          -e PGID=1000 \
          -e TZ=Etc/UTC \
          -e CUSTOM_USER=admin \
          -e PASSWORD=admin#admin \
          -p 4000:3000 \
          -p 4001:3001 \
          -v /path/to/config:/config \
          --shm-size="1gb" \
          --restart unless-stopped \
          lscr.io/linuxserver/firefox:latest
```

### ✅ Desktop
```
      docker run -d \
          --name=webtop \
          --security-opt seccomp=unconfined \
          -e PUID=1000 \
          -e PGID=1000 \
          -e TZ=Etc/UTC \
          -e SUBFOLDER=/ \
          -e TITLE=OPIran \
          -e CUSTOM_USER=admin \
          -e PASSWORD=admin#admin \
          -p 3000:3000 \
          -p 3001:3001 \
          -v /path/to/data:/config \
          -v /var/run/docker.sock:/var/run/docker.sock \
          --device /dev/dri:/dev/dri \
          --shm-size="1gb" \
          --restart unless-stopped \
          lscr.io/linuxserver/webtop:latest
```


Your dashboard will be available at http://IP:Port 
