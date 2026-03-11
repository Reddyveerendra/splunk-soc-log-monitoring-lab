# Ubuntu 24.04.4 LTS Server Installation

## Overview

After installing VirtualBox, the next step in the SOC lab setup is installing an operating system that will generate system and security logs. In this project, **Ubuntu 24.04.4 LTS Server** was used as the primary system to simulate a Linux server environment for log collection and monitoring with Splunk.

---

## What is Ubuntu Server?

Ubuntu Server is a Linux-based operating system designed for servers, cloud environments, and network services. Unlike the desktop version, Ubuntu Server focuses on performance, stability, and command-line management.

### Key Features of Ubuntu Server

- Lightweight and optimized for server environments  
- Long Term Support (LTS) versions provide security updates for **5 years**  
- Widely used for hosting applications, web servers, and security monitoring tools  
- Supports command-line management which is ideal for SOC environments  

---

# Ubuntu Server Setup Process

## Step 1: Navigate to Ubuntu Website

Open your browser and go to the official Ubuntu download page:

https://ubuntu.com/download/server

This page provides the latest Ubuntu Server ISO files.

<img width="964" height="481" alt="image" src="https://github.com/user-attachments/assets/f06cad6f-9e96-408a-bbb4-a6bbcb146580" />


---

## Step 2: Download Ubuntu Server

Download the **Ubuntu 24.04.4 LTS Server ISO image**.

This file will be used to install Ubuntu inside the VirtualBox virtual machine.

<img width="964" height="441" alt="image" src="https://github.com/user-attachments/assets/5ea1b731-2d34-4f96-9feb-04fa06c08207" />


---

## Step 3: Create a New Virtual Machine

Open **Oracle VirtualBox** and click **New**.

Provide the following details:

- **Name:** Ubuntu-SOC-Lab  
- **Type:** Linux  
- **Version:** Ubuntu (64-bit)

<img width="1206" height="832" alt="image" src="https://github.com/user-attachments/assets/26ba4f2d-7db5-416c-bf73-55e619e2a803" />


---

## Step 4: Allocate System Resources

Assign hardware resources to the virtual machine.

### Recommended Configuration

- **RAM:** 4 GB  
- **CPU:** 2 Processors  
- **Storage:** 40 GB (VDI, Dynamically Allocated)

These resources are sufficient for running Ubuntu Server and Splunk.

<img width="1192" height="816" alt="image" src="https://github.com/user-attachments/assets/a4f41720-b71a-419c-bced-4d6447eecb33" />


---

## Step 5: Attach Ubuntu ISO File

Go to **Storage Settings** and attach the downloaded **Ubuntu Server ISO file** to the virtual optical drive.

This allows VirtualBox to boot the installer.

<img width="484" height="195" alt="image" src="https://github.com/user-attachments/assets/1692e518-6197-47a0-afc3-535ebd787308" />


---

## Step 6: Start the Virtual Machine

Click **Start** to boot the virtual machine.

The Ubuntu installer will start automatically.

<img width="961" height="503" alt="image" src="https://github.com/user-attachments/assets/01b4db07-1345-4f1d-b38f-e81fac24b762" />


---

## Step 7: Install Ubuntu Server

Follow the installation steps:

1. Select **English language**
2. Choose **Install Ubuntu Server**
3. Configure **Keyboard Layout**
4. Configure **Network Settings**
5. Set **Username and Password**
6. Configure **Disk Partition** (Use Default Option)
7. Complete the installation

After installation finishes, restart the virtual machine.

---

## Step 8: Login to Ubuntu Server

After rebooting, log in using the credentials created during installation.

You will now have a **fully functional Ubuntu 24.04.4 LTS Server environment** ready for:

- Installing **Splunk Enterprise**
- Configuring **log monitoring**
- Creating **SOC detection rules**
<img width="961" height="506" alt="image" src="https://github.com/user-attachments/assets/351651da-2b90-438f-b319-e7e5a9dac4f4" />
