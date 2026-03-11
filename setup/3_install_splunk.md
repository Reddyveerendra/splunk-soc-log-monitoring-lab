# Splunk SOC Lab Setup – Splunk Enterprise Installation

This section explains how Splunk Enterprise was installed on Ubuntu 24.04.4 LTS Server using the command line.
Splunk is used as the SIEM platform in this SOC lab to collect, analyse, and monitor system logs generated from the Ubuntu server.

## Step 1: Update the System

Update the package repository and upgrade existing packages before installing Splunk.

sudo apt update
sudo apt upgrade -y

## Step 2: Download Splunk Enterprise

Download the Splunk .deb installation package directly using wget.

wget -O splunk.deb https://download.splunk.com/products/splunk/releases/9.2.0/linux/splunk-9.2.0.deb

Verify the download:

ls -lh

<img width="966" height="506" alt="image" src="https://github.com/user-attachments/assets/ad647675-b029-4fe7-abe4-bd477f66a77e" />

## Step 3: Install Splunk

Install the downloaded package using dpkg.

sudo dpkg -i splunk.deb

Splunk will be installed in the following directory:

/opt/splunk


## Step 4: Start Splunk

Start the Splunk service.

sudo /opt/splunk/bin/splunk start

During the first startup:

Accept the Splunk license agreement

Create an admin username

Create an admin password

## Step 5: Enable Splunk at System Boot

Enable Splunk to start automatically when the server boots.

sudo /opt/splunk/bin/splunk enable boot-start

<img width="918" height="107" alt="image" src="https://github.com/user-attachments/assets/e5a6c8ca-617c-42a0-b9bd-186fd3711a56" />


## Step 6: Verify Splunk Service

Check whether Splunk is running.

sudo /opt/splunk/bin/splunk status

Expected output:

splunkd is running
Screenshot Required

<img width="798" height="88" alt="image" src="https://github.com/user-attachments/assets/ccbe0828-4075-4436-bbde-d3313f8825c4" />


## Step 7: Configure Port Forwarding in VirtualBox

Since the virtual machine uses NAT networking, port forwarding must be configured to access Splunk from the host machine.

Configuration Steps

Open VirtualBox

Select the Ubuntu Virtual Machine

Go to Settings → Network

Ensure Adapter 1 = NAT

Click Advanced → Port Forwarding

Add the following rule:

Name	Protocol	Host Port	Guest Port
Splunk	TCP	8000	8000

This forwards traffic from the host machine to the Splunk web interface running inside the VM.

Screenshot Required

📸 VirtualBox Port Forwarding configuration

<img width="1923" height="1001" alt="image" src="https://github.com/user-attachments/assets/6dd42489-a353-497f-8270-edab8359ef11" />


## Step 8: Access Splunk from Host Machine

After configuring port forwarding, open a browser on the host machine and navigate to:

http://localhost:8000

Log in using the admin credentials created during installation.

<img width="1923" height="1083" alt="image" src="https://github.com/user-attachments/assets/176cc061-3c2c-4313-95de-b93db4cfeea7" />


📸 Splunk Home Dashboard after login

<img width="1923" height="1021" alt="image" src="https://github.com/user-attachments/assets/eaa13b96-c6a2-4b3a-b07f-c4fde271831b" />
