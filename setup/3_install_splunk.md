## Splunk SOC Lab Setup – Splunk Enterprise Installation

This section explains how Splunk Enterprise was installed on Ubuntu 24.04.4 LTS Server using the command line.
Splunk is used as the SIEM platform in this SOC lab to collect, analyse, and monitor system logs generated from the Ubuntu server.

# Step 1: Update the System

Update the package repository and upgrade existing packages before installing Splunk.

sudo apt update
sudo apt upgrade -y

# Step 2: Download Splunk Enterprise

Download the Splunk .deb installation package directly using wget.

wget -O splunk.deb https://download.splunk.com/products/splunk/releases/9.2.0/linux/splunk-9.2.0.deb

Verify the download:

ls -lh
Screenshot Required

📸 Terminal showing the Splunk .deb file downloaded successfully

Example location to store screenshot:

images/splunk_download.png
# Step 3: Install Splunk

Install the downloaded package using dpkg.

sudo dpkg -i splunk.deb

Splunk will be installed in the following directory:

/opt/splunk
Screenshot Required

📸 Terminal showing Splunk installation process

Example:

images/splunk_installation.png

# Step 4: Start Splunk

Start the Splunk service.

sudo /opt/splunk/bin/splunk start

During the first startup:

Accept the Splunk license agreement

Create an admin username

Create an admin password

Screenshot Required

📸 Terminal showing Splunk license agreement and startup

Example:

images/splunk_first_start.png
# Step 5: Enable Splunk at System Boot

Enable Splunk to start automatically when the server boots.

sudo /opt/splunk/bin/splunk enable boot-start
Screenshot Required

📸 Terminal showing boot-start enabled

Example:

images/splunk_boot_start.png
# Step 6: Verify Splunk Service

Check whether Splunk is running.

sudo /opt/splunk/bin/splunk status

Expected output:

splunkd is running
Screenshot Required

📸 Terminal showing Splunk status running

Example:

images/splunk_status.png
# Step 7: Configure Port Forwarding in VirtualBox

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

Example:

images/virtualbox_port_forwarding.png
# Step 8: Access Splunk from Host Machine

After configuring port forwarding, open a browser on the host machine and navigate to:

http://localhost:8000

Log in using the admin credentials created during installation.

Screenshot Required

📸 Splunk Login Page

Example:

images/splunk_login.png

📸 Splunk Home Dashboard after login

Example:

images/splunk_dashboard.png