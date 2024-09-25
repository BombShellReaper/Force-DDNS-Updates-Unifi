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

