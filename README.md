This repository is developed in Fish-IoT project

https://www.tequ.fi/en/project-bank/fish-iot/ 

---

# tequ-jetson-setup
Basic steps to configure Jetson Board

# Actions

## 1. Configure system & Install Jetpack & Software

Installation steps depends of your Jetson board. Install latest Jetpack that is supported.

- https://developer.nvidia.com/embedded/jetpack

Neousys NRU-120S
- Official guide: https://neousys.gitbook.io/nru-series/nru-series/3.-reflash-nru-110v-or-nru-120s
- Prepare host machine with Ubuntu Linux 18.04 
  - Get external SSD drive ~256 GB or bigger
  - Download Linux Ubuntu 18.04 image and flash it to usual USB-stick
  - Boot your system from USB-stick and install Ubuntu to external SSD drive
  - Boot your system from external SSD drive
  - Contact your dealer for access to Neousys FTP server and download "NRU-100_JetPack4.6.1_AGX64GBor32GB)" system image
- Install updates 
  - sudo apt-get update && sudo apt-get upgrade
- Flash official Jetpack 4.6.1
  - Install NVIDIA SDK Manager https://developer.nvidia.com/drive/sdk-manager
  - Launch NVIDIA SDK Manager and prepare Jetpack 4.6.1 for Jetson AGX Xavier Dev kit
  - Flash from command line from folder ```$HOME/nvidia/nvidia_sdk/JetPack_4.6.1_Linux_JETSON_AGX_XAVIER/Linux_for_Tegra```
    - sudo ./flash.sh jetson-agx-xavier-devkit mmcblk0p1
- Flash Neousys Jetpack 4.6.1
  - Copy ```NRU_JetPack4.6.1_v1.1.dtb``` to ```$HOME/nvidia/nvidia_sdk/JetPack_4.6.1_Linux_JETSON_AGX_XAVIER/Linux_for_Tegra```
  - Copy ```system.img``` to ```$HOME/nvidia/nvidia_sdk/JetPack_4.6.1_Linux_JETSON_AGX_XAVIER/Linux_for_Tegra/bootloader```
  - Flash from command line from folder ```$HOME/nvidia/nvidia_sdk/JetPack_4.6.1_Linux_JETSON_AGX_XAVIER/Linux_for_Tegra```
    - sudo ./flash.sh -r -d NRU_JetPack4.6.1_v1.1.dtb jetson-agx-xavier-devkit mmcblk0p1

## 2. Disable GUI (optional)

```
sudo systemctl stop display-manager
```

```
sudo systemctl set-default multi-user.target
```

Back to gui
```
sudo systemctl start display-manager
```

```
sudo systemctl set-default graphical.target
```

## 3. Run update & upgrade

```
sudo apt update && sudo apt upgrade
```

## 4. Install jtop for analyzing (optional)

```
sudo apt-get install python3-pip
```

```
sudo -H pip3 install -U jetson-stats
```

```
jtop
```

## 5. Install Node-RED 

```
sudo apt-get install curl
```

```
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
```

```
node-red admin init
```

```
sudo systemctl enable nodered.service
```

```
sudo systemctl start nodered.service
```

## 6. Upgrade Node.js (optional)

```
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
```

```
sudo apt-get install -y nodejs
```

## 7. Enable jetson-clocks at boot (optional)
```
sudo apt install nano -y
```

```
sudo nano /etc/rc.local
```

Add to file:
```
#!/bin/sh -e
# rc.local
#Maximize performances
( sleep 60 && /usr/bin/jetson_clocks )&


exit 0
```

Save and exit
```
sudo chmod +x /etc/rc.local
```

Jetson clocks will be enabled after 60 seconds since boot.

## 8. Reboot

```
sudo reboot
```

# Changing Python version

For example in Jetson Nano install Python 3.7

```
sudo apt install python3.7-dev
```

```
sudo rm /usr/bin/python3
```

```
sudo ln -s /usr/bin/python3.7 /usr/bin/python3
```

```
python3
```

# Next steps

## Tensorflow 2 & Node-RED with Jetson Nano / Xavier NX

https://github.com/Lapland-UAS-Tequ/tequ-jetson-nodered-tensorflow

## Triton Inference Server

https://github.com/Lapland-UAS-Tequ/tequ-setup-triton-inference-server

## Basler CV cameras with Jetson Nano / Xavier NX

https://github.com/Lapland-UAS-Tequ/tequ-jetson-basler










