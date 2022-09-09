# Mi Body Composition Scale 2

## 1. Introduction
- This project is based on the following projects:
  - https://github.com/RobertWojtowicz/miscale2garmin
- It allows you to fetch information of the Mi Body Composition Scale 2 (model: XMTZC05HM) and post the information securely to a given URL (using HTTP Authorization)

## 2. Acquire the MAC address of your Mi Body Composition Scale 2
- Install the Zepp Life App on your mobile device
- Configure your Mi Body Composition Scale 2 with the Zepp Life App on your mobile device
- Retrieve the scale's MAC Address from the Zepp Life App and (optionally) turn off weigh small object in the app for better measurement quality by going to:
   - _Profile -> My devices -> Mi Body Composition Scale 2_

![alt text](https://github.com/RobertWojtowicz/miscale2garmin/blob/master/pic/settings.png)

## 3. Preparing your linux system / Raspberry Pi
- Update your system and then install following modules which the script requires:

```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install wget python3 bluetooth python3-pip libglib2.0-dev -y
sudo pip install bluepy
```

- Then modify file ```sudo nano /etc/systemd/system/bluetooth.target.wants/bluetooth.service``` to disable SAP:

```
ExecStart=/usr/lib/bluetooth/bluetoothd --noplugin=sap
```

### 4. Configure and run the script

- Update the first few lines of the script with your MAC address and any HTTP Authroization
```
sudo nano scan_xiaomi_scale.py
```
Then try to run the script by executing it:
```
$ python3 scan_xiaomi_scale.py
```
- Finally, if everything works correctly schedule it using cron say every 3 minutes or so;
```
*/3 * * * * /home/martin/xiaomi-mi-body-composition-scale-2/scan_xiaomi_scale.sh
```
