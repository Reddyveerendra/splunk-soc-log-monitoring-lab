# Port Scan Attack Simulation using Nmap

To test the detection capabilities of the Splunk SOC lab environment, a port scanning attack simulation was performed using Nmap.

Port scanning is commonly used by attackers during the reconnaissance phase to identify open ports and services running on a target system.

In this simulation, a scan was executed against the Ubuntu server to generate network activity logs that could later be analyzed in Splunk.

## Objective

The objective of this simulation is to:

Generate port scanning activity

Ingest the generated logs into Splunk

Detect the scan using Splunk searches and alerts

Visualize the activity in the SOC dashboard

Lab Environment
Component	Description
Attacker Machine	Host machine running Nmap
Target Server	Ubuntu Server (Virtual Machine)
SIEM	Splunk Enterprise
Virtualization	Oracle VM VirtualBox

## Step 1: Install Nmap on Attacker Machine

If Nmap is not installed, install it using the following commands.

Ubuntu / Linux
sudo apt update
sudo apt install nmap
Windows

Download Nmap from the official website and install it.

## Step 2: Identify Target IP Address

Find the IP address of the Ubuntu server.

ip a

Example output:

10.0.2.15

This IP address will be used as the scan target.

## Step 3: Run a TCP SYN Port Scan

Execute a SYN scan against the target machine.

nmap -sS 10.0.2.15
Explanation
Option	Description
-sS	Performs a TCP SYN (stealth) scan

This command scans the most common ports to identify open services.

## Step 4: Generate More Scan Activity

To generate more logs for detection testing, perform a full port scan.

nmap -p- 10.0.2.15
Explanation
Option	Description
-p-	Scans all 65535 ports

This creates more network activity that can be detected in Splunk.

## Step 5: Verify Logs in Splunk

After performing the scan, search for the generated logs in Splunk.

index=*
| stats count by src_ip port

This query helps identify the source IP that attempted connections to multiple ports.

## Step 6: Detect Port Scanning Activity

Use the following query to detect scanning behaviour.

index=*
| stats dc(port) as unique_ports by src_ip
| where unique_ports > 10
Detection Logic

If a single IP address attempts connections to many different ports, it may indicate port scanning activity.


## Result

The Nmap scan successfully generated multiple connection attempts to different ports on the target system. These events were collected and analyzed in Splunk, enabling detection of potential port scanning behaviour.