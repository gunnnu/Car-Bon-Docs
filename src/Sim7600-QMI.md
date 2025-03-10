# Setting Up SIM7600 for Internet Using QMI Interface on Raspberry Pi

This guide provides step-by-step instructions to configure the SIM7600 module to provide internet access via the QMI interface on a Raspberry Pi.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Step 1: Update and Install Required Packages](#step-1-update-and-install-required-packages)
- [Step 2: Check USB Connection](#step-2-check-usb-connection)
- [Step 3: Enable QMI Mode](#step-3-enable-qmi-mode)
- [Step 4: Verify Module Status](#step-4-verify-module-status)
- [Step 5: Configure Network Settings](#step-5-configure-network-settings)
- [Step 6: Create a Systemd Service for Automatic Connection](#step-6-create-a-systemd-service-for-automatic-connection)
- [License](#license)

---

## Prerequisites
- Raspberry Pi with Raspberry Pi OS
- SIM7600 module connected via USB
- Active SIM card with a data plan

---

## Step 1: Update and Install Required Packages

Update your Raspberry Pi:
```bash
sudo apt update && sudo apt upgrade -y
```

Install necessary packages:
```bash
sudo apt install libqmi-utils udhcpc minicom -y
```

---

## Step 2: Check USB Connection

List connected USB devices:
```bash
lsusb
```
Expected output:
```
Bus 001 Device 004: ID 1e0e:9001 Qualcomm / SimTech SIM7600
```

Check available USB interfaces:
```bash
ls /dev/ttyUSB*
```
Expected output:
```
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3
```

Identify the QMI device:
```bash
ls /dev/cdc-wdm*
```
Expected output:
```
/dev/cdc-wdm0
```

---

## Step 3: Enable QMI Mode

Open Minicom:
```bash
sudo minicom -D /dev/ttyUSB2 -b 115200
```

Set QMI mode:
```bash
AT+CNMP=38
```

Restart the module:
```bash
AT+CFUN=1,1
```
(Wait for the module to reboot.)

Exit Minicom:  
Press `CTRL + A`, then `X`, and select `Yes`.

---

## Step 4: Verify Module Status

Check if the module is online:
```bash
sudo qmicli -d /dev/cdc-wdm0 --dms-get-operating-mode
```

Check signal strength:
```bash
sudo qmicli -d /dev/cdc-wdm0 --nas-get-signal-strength
```

Check the home network:
```bash
sudo qmicli -d /dev/cdc-wdm0 --nas-get-home-network
```

---

## Step 5: Configure Network Settings

Set the interface to use raw-ip:
```bash
sudo ip link set wwan0 down
echo 'Y' | sudo tee /sys/class/net/wwan0/qmi/raw_ip
sudo ip link set wwan0 up
```

Connect to the mobile network:
```bash
sudo qmicli -p -d /dev/cdc-wdm0 --device-open-net='net-raw-ip|net-no-qos-header' --wds-start-network="apn='jionet',ip-type=4" --client-no-release-cid
```

Assign an IP address:
```bash
sudo udhcpc -i wwan0
```

---

## Step 6: Create a Systemd Service for Automatic Connection

Create a systemd service file:
```bash
sudo nano /etc/systemd/system/sim7600-qmi.service
```
Paste the following:
```ini
[Unit]
Description=SIM7600 QMI Internet Connection
After=network.target

[Service]
ExecStart=/usr/local/bin/sim7600-qmi.sh
Restart=always
User=root

[Install]
WantedBy=multi-user.target
```
Save and exit (`CTRL+X`, then `Y`, then `Enter`).

### Create the Startup Script
```bash
sudo nano /usr/local/bin/sim7600-qmi.sh
```
Paste the following:
```bash
#!/bin/bash

# Set raw-ip mode
sudo ip link set wwan0 down
echo 'Y' | sudo tee /sys/class/net/wwan0/qmi/raw_ip
sudo ip link set wwan0 up

# Connect to mobile network
sudo qmicli -p -d /dev/cdc-wdm0 --device-open-net='net-raw-ip|net-no-qos-header' --wds-start-network="apn='jionet',ip-type=4" --client-no-release-cid

# Assign an IP
sudo udhcpc -i wwan0
```
Save and exit.

Give execution permissions:
```bash
sudo chmod +x /usr/local/bin/sim7600-qmi.sh
```

Enable and start the service:
```bash
sudo systemctl enable sim7600-qmi.service
sudo systemctl start sim7600-qmi.service
```

---

## License
This project is open-source and available under the MIT License.

---

## Contributions & Issues
Feel free to contribute or raise issues if you encounter any problems.

