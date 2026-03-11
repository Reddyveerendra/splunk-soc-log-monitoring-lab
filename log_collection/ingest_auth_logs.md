# Ingest Authentication Logs into Splunk

## Overview

In this step, authentication logs from the Ubuntu server are ingested into Splunk. These logs contain important security events such as login attempts, failed authentication attempts, and SSH access activity.

Monitoring authentication logs helps security analysts detect suspicious behavior such as brute force attacks or unauthorized access attempts.

---

## What are Authentication Logs?

Authentication logs record events related to user login and authentication on a system.

These logs typically include:

- Successful login attempts
- Failed login attempts
- SSH login activity
- User session creation
- Privilege escalation events

In Ubuntu, these logs are stored in the following file:


/var/log/auth.log


These logs will be monitored by Splunk for security analysis.

---

# Steps to Ingest Authentication Logs into Splunk

## Step 1: Access Splunk Web Interface

Open a browser on the host machine and navigate to:


http://localhost:8000


Login using the Splunk **admin credentials** created during installation.

---

## Step 2: Navigate to Add Data

After logging in:

1. Click **Settings**
2. Select **Add Data**

This allows Splunk to ingest new log sources.

---

## Step 3: Select Monitor Data Source

Choose **Monitor** as the data input type.

This option allows Splunk to continuously monitor a file for new log entries.

---

## Step 4: Specify Log File Path

Enter the authentication log file path:


/var/log/auth.log


This file contains system authentication and SSH login activity.

---

## Step 5: Configure Input Settings

Configure the following settings:

**Source Type**


linux_secure


**Host**


localhost


**Index**


main


Click **Review** and then **Submit**.

---

## Step 6: Verify Log Ingestion

Go to the Splunk **Search & Reporting** app and run the following search:


index=main sourcetype=linux_secure


You should start seeing authentication logs appearing in Splunk.

---

## Step 7: Generate Test Logs

To generate authentication logs, attempt an SSH login to the server.

Example:

```bash
ssh username@localhost