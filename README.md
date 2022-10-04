This repository is developed in Fish-IoT project

https://www.tequ.fi/en/project-bank/fish-iot/ 

---

# tequ-jetson-setup
Basic steps to configure Jetson Board

# Actions

## 1. Install Jetpack & Software
- https://developer.nvidia.com/embedded/jetpack

## 2. Disable GUI (optional)

```
sudo service gdm stop
```

```
sudo systemctl set-default multi-user.target
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

https://forumvolt.com/magic/make-jetson-clocks-start-at-boot.84/

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

# Next steps

## Tensorflow 2 & Node-RED with Jetson Nano / Xavier NX

https://github.com/Lapland-UAS-Tequ/tequ-jetson-nodered-tensorflow

## Triton Inference Server

https://github.com/Lapland-UAS-Tequ/tequ-setup-triton-inference-server

## Basler CV cameras with Jetson Nano / Xavier NX

https://github.com/Lapland-UAS-Tequ/tequ-jetson-basler











