# How to Force DDNS Updates on Unifi Controller
**Overview**

This guide explains how to force the Unifi Controller to update DDNS using built-in configurations. I encountered this issue during my initial setup of DDNS and several times after rebooting or editing A records.

**Prerequisites**

Knowledge of the following:
- DDNS
- Linux structure
- Domain management
- A records
- Unifi Controller
- SSH

**Disclaimer**

This guide is based on research, and I recommend exercising caution when working with the Unifi Controller.

# Step 1: SSH Into The Controller

SSH (Secure Shell) is a protocol used to securely access and manage network devices. To begin, open your terminal or command prompt and use the following command to SSH into the Unifi Controller:

    ssh username@controller-ip-address

Replace **username** with your actual username and **controller-ip-address** with the IP address of your Unifi Controller. You will be prompted to enter your password.

Once logged in, you will have access to the command line interface of the Unifi Controller.

# Step 2: Change To The Run Dir & List Contents

    cd /run
    ls

It should look something like this:

![image](https://github.com/user-attachments/assets/bc61c298-4572-4de0-8d9d-28da2fb9e506)

# Step 3: Find The DDNS Config file

The configuration file should look something like this: **ddns-eth9-inadyn.conf** The "eth9" can vary.

Use the following command to force the configurations in your DDNS settings

    inadyn -n -1 --force -f /run/"Your-Config-File"

Replace **"Your-Config-File"** with the configuration file you located **Step 2** Based on the picture provided above the command would look like this: **"inadyn -n -1 --force -f /run/ddns-eth9-inadyn.conf"**

It should look something like this:

![image](https://github.com/user-attachments/assets/39e9d85d-e3c3-44f5-b068-e72cc770153b)

The output should look something like this:

    inadyn[55425]: In-a-dyn version 2.12.0 **(Version can be different)** -- Dynamic DNS update client.
    
    inadyn[55425]: Update forced for alias **(Hostname)**, new IP# **(Your-WAN-IP)**
    
    inadyn[55425]: Updating cache for **(Hostname)**

# Troubleshooting

If you are running into issues, then open a second ssh terminal and run this commmand in the new terminal

    tail -n 1000 /var/log/messages | grep dyn

This will give a line-by-line view of potential errors for the last 1000 entries. The command running will look something like this:

![image](https://github.com/user-attachments/assets/d000f577-ce99-4313-8ccc-b523a268e4e0)

One last command that you can run is to debug and it's as follows:

     /usr/sbin/inadyn -n -s -C -f /run/iadyn.conf -1 -1 debug --force
