# SSH Brute Force Attack Simulation

## Overview

In this phase of the SOC lab, an **SSH brute force attack** is simulated against the Ubuntu server. The goal is to generate multiple failed authentication attempts that will be captured in the system logs and ingested into Splunk for analysis.

This simulation helps demonstrate how a **Security Operations Center (SOC)** analyst can detect suspicious login activity using log monitoring.

---

## What is an SSH Brute Force Attack?

An SSH brute force attack occurs when an attacker repeatedly attempts to log in to a system using different username and password combinations until the correct credentials are found.

Common indicators of a brute force attack include:

- Multiple failed login attempts
- Rapid authentication failures
- Repeated login attempts from the same IP address

These events are recorded in the authentication log file:


/var/log/auth.log


---

# Step 1: Generate Failed SSH Login Attempts

To simulate brute force activity, attempt multiple SSH logins using incorrect credentials.

Example command:

ssh wronguser@localhost

Enter incorrect passwords multiple times to generate failed authentication logs.

Repeat this process several times to simulate attack behavior.


## Step 2: Verify Logs on the Ubuntu Server

SSH login attempts are recorded in the authentication logs.

Run the following command to view SSH-related logs:

sudo cat /var/log/auth.log | grep ssh

This command filters and displays SSH login activity including failed authentication attempts.

## Step 3: Verify Logs in Splunk

Open the Splunk Search & Reporting application and run the following query:

index=main sourcetype=linux_secure "Failed password"

This search retrieves failed SSH login attempts collected from the authentication logs.


## Step 4: Identify Suspicious Login Activity

To identify potential brute force activity, count failed login attempts from each source IP.

Run the following query in Splunk:

index=main sourcetype=linux_secure "Failed password"
| stats count by src_ip
| sort -count

This query highlights IP addresses generating the highest number of failed login attempts.

# Result

The simulated SSH brute force activity generated multiple failed authentication events in the system logs. These logs were successfully ingested into Splunk and analyzed using search queries.

Using Splunk, it was possible to identify:

Failed login attempts

Suspicious login patterns

Source IP addresses associated with the attack

This demonstrates how SOC analysts can detect brute force attacks using log monitoring and SIEM tools.