# Mi Body Composition Scale 2

## 1. Introduction
- This project is based on the following projects:
  - https://github.com/RobertWojtowicz/miscale2garmin
- It allows you to fetch information of the Mi Body Composition Scale 2 (model: XMTZC05HM) and post the information to a given URL

## 2. Getting the MAC address of Mi Body Composition Scale 2 / disable weigh small object
- Install Zepp Life App on your mobile device, user manual: https://files.xiaomi-mi.com/files/smart_scales/smart_scales-EN.pdf
- Configure your scale with Zepp Life App on your mobile device
- Retrieve scale's MAC Address from Zepp Life App (Profile > My devices > Mi Body Composition Scale 2);
- Turn off weigh small object in Zepp Life App (Profile > My devices > Mi Body Composition Scale 2) for better measurement quality:

![alt text](https://github.com/RobertWojtowicz/miscale2garmin/blob/master/pic/settings.png)

## 3. Preparing your linux system
- Minimum hardware requirements are: 1 CPU, 512 MB RAM, 2 GB HDD, network connection;
- Update your system and then install following modules:
```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install wget python3 bluetooth python3-pip libglib2.0-dev -y
sudo pip install bluepy
```
- Modify file ```sudo nano /etc/systemd/system/bluetooth.target.wants/bluetooth.service```:
```
ExecStart=/usr/lib/bluetooth/bluetoothd --noplugin=sap
```

### 4. Configuring scripts
- Edit scan_xiaomi_scale.py by updating the scale_mac_addr
