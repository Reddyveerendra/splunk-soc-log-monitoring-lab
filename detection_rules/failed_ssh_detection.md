# SSH Brute Force Attack Simulation and Detection

## Overview

In this step of the SOC lab, an **SSH brute force attack** is simulated against the Ubuntu server. The purpose of this activity is to generate multiple failed login attempts that are recorded in the authentication logs and ingested into Splunk for analysis.

This helps demonstrate how a **Security Operations Center (SOC)** analyst can detect suspicious login activity using log monitoring.

---

## What is an SSH Brute Force Attack?

An SSH brute force attack occurs when an attacker repeatedly attempts to log in to a server using different username and password combinations until valid credentials are discovered.

Common indicators of a brute force attack include:

- Multiple failed login attempts
- Repeated login attempts within a short period
- Login attempts from the same IP address

These events are recorded in the system authentication logs located at:


/var/log/auth.log


---

## Step 1: Generate Failed SSH Login Attempts

To simulate brute force behavior, attempt multiple SSH logins using incorrect credentials.

Example:

ssh wronguser@localhost

Enter incorrect passwords several times to generate failed authentication logs.

Repeat this process multiple times to simulate attack activity.

Screenshot

Insert screenshot showing failed SSH login attempts from terminal.

![Failed SSH Attempts](ADD_IMAGE_LINK_HERE)

## Step 2: Verify Logs on the Ubuntu Server

SSH authentication activity is recorded in the system authentication log.

Run the following command to view SSH-related logs:

sudo cat /var/log/auth.log | grep ssh

This command filters and displays SSH login activity including failed authentication attempts.

Screenshot

Insert screenshot showing SSH log entries in the terminal.

![SSH Log Entries](ADD_IMAGE_LINK_HERE)

## Step 3: Search Authentication Logs in Splunk

Open the Splunk Search & Reporting interface and run the following query:

index=main sourcetype=linux_secure "Failed password"

This search retrieves failed SSH login attempts collected from the authentication logs.

Screenshot

Insert screenshot showing failed login events in Splunk.

![Splunk Failed Login Events](ADD_IMAGE_LINK_HERE)

## Step 4: Identify Suspicious Login Patterns

To identify potential brute force activity, count failed login attempts from each source IP.

Run the following query in Splunk:

index=main "Failed password"
| stats count by src_ip
| sort -count

This query helps identify IP addresses generating a high number of failed login attempts.

Screenshot

Insert screenshot showing statistics results in Splunk

![Brute Force Detection Results](ADD_IMAGE_LINK_HERE)
Result

The simulated SSH brute force activity generated multiple failed authentication events in the system logs. These logs were successfully ingested into Splunk and analyzed using search queries.

Using Splunk, it was possible to identify:

Multiple failed login attempts

Suspicious login activity

Source IP addresses associated with the attack

This demonstrates how SOC analysts can detect brute force attacks using log monitoring and SIEM tools.