# tequ-jetson-nano-setup
Basic steps to configure Jetson Nano.

## Actions

### 1. Download latest official Jetson Nano image file
- https://developer.nvidia.com/jetson-nano-sd-card-image

### 2. Flash image to SD card
- Use for example Raspberry PI imager tool
- https://downloads.raspberrypi.org/imager/imager_latest.exe

### 3. Boot Jetson with SD card
- Plug SD card
- Connect mouse, keyboard and display for graphical setup
- Setup Micro-USB connection for terminal setup
- https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit


### 4. Disable GUI

```
sudo service gdm stop
```

```
sudo systemctl set-default multi-user.target
```

### 5. Run update & upgrade

```
sudo apt update && sudo apt upgrade
```

### 6. Install jtop and check that everything is installed correctly

```
sudo apt-get install python3-pip
```

```
sudo -H pip3 install -U jetson-stats
```

```
jtop
```

### 7. Install Node-RED 

```
sudo apt-get install curl
```

```
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
```

```
sudo systemctl enable nodered.service
```

```
sudo systemctl start nodered.service
```

### 8. Upgrade Node.js 

```
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
```

```
sudo apt-get install -y nodejs
```



