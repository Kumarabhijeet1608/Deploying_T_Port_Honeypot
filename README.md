# T-POT Honeypot Setup: Ultimate VPS Guide

## Introduction

In this documentation, I will guide you through the process of setting up a T-POT Honeypot on a VPS (Virtual Private Server) using the VULTR VPS service provider. T-POT is an open-source honeypot framework designed to capture and analyze malicious traffic in a network environment.

A honeypot serves as an intentionally vulnerable system designed to attract potential attackers, thereby enabling the collection of valuable information to analyze and mitigate cyber threats. The step-by-step instructions detailed herein cover the installation of T-Pot on a Debian Linux instance in VULTR VPS, along with the necessary network configurations and firewall settings to ensure seamless operation and data security. Additionally, the document explores the significance of honeypots in cybersecurity, potential use cases, and the insights gleaned from monitoring honeypot data.

## Keywords

T-Pot, Honeypot, VULTR VPS, Debian Linux, Network Security, Cybersecurity, SSH Authentication, Monitoring, Access Control, Threat Detection, Kibana Dashboard.

## Understanding Honeypots

A honeypot is a cybersecurity tool designed to deceive attackers by simulating vulnerable systems or services. It operates by attracting adversaries to interact with the decoy, thereby revealing their methodologies and objectives. Honeypots serve multiple purposes, including research, threat intelligence gathering, and detection of malicious activities that evade traditional security measures.

## Prerequisites

- VULTR VPS account (signup [here](https://www.vultr.com/?ref=8718802) to get free $100 credits)
- Basic knowledge of Linux and server administration

You can use any other VPS provider as well; steps will be almost the same on every platform.

## Step 1: Deploy a New Server

1. Log in to your VULTR account and navigate to the “Deploy” section.
2. Click on “Deploy a new server” and select the “Cloud Compute” option.
3. Choose a location closest to you for better performance.
4. Click on Add, and choose "Debian 11".
5. Select a plan for your server, preferably a regular cloud computing plan for cost-effectiveness.
6. Disable auto backups and IPv6 to streamline your setup.
7. Add a server hostname and label whatever you want and finally deploy now.
8. After a couple of minutes, you will see the status as running. Click on the machine, and you will see a "View Console" icon on the top.

## Install T-Pot

1. Update Debian installation:
    ```sh
    sudo apt update && sudo apt upgrade -y
    ```
2. Install Git:
    ```sh
    sudo apt install git
    ```
3. Clone T-Pot repository:
    ```sh
    sudo git clone https://github.com/telekom-security/tpotce
    ```
4. Run the installer:
    ```sh
    sudo tpotce/iso/installer/install.sh --type=user
    ```

## Step 2: Configure Firewall

1. Go to the server settings and select the “Firewall” option.
2. Click on “Manage” and then “+ Add firewall group.”
3. Add a Firewall Group:
    - Set the SSH option to TCP.
    - Add TCP and UDP protocols with port range 1:65535, and set the source IP to your own (my IP for security).
    - Click the + button for Inbound IPv4 Rules.
4. Go back to the honeypot:
    - Click on Compute, and you will see your honeypot there.
    - Go to settings, firewall, and in the drop-down select the firewall you created earlier.
5. Click on the "View Console" again and select the location accordingly.

## Access Your Honeypot

1. After the installation, create a password. The console username is `tsec`, which you can use to access your admin panel.
2. Access T-Pot’s web interface via a web browser using the provided URL and port (e.g., `https://<PUBLIC_IP>:64297`).
3. Authenticate with the provided credentials and access the Kibana dashboard to monitor honeypot activity.

## Monitor and Analyze Honeypot Data

To effectively monitor and analyze honeypot data, leverage monitoring tools such as Kibana, which interfaces with Elasticsearch to visualize and analyze data collected by T-Pot. Kibana offers a user-friendly interface for exploring and understanding the incoming data, enabling us to detect potential cyber threats and formulate appropriate responses.

### Kibana Dashboard

- Kibana provides a centralized dashboard that aggregates and presents honeypot data in a visually appealing format.
- The dashboard offers various visualizations, including charts, graphs, and tables, to represent different aspects of the data, such as attack types, source IPs, and attack frequencies.
- By monitoring these visualizations, security practitioners can identify patterns, anomalies, and trends in the data, which may indicate potential cyber threats or suspicious activities.
- Kibana also supports real-time monitoring, allowing users to continuously monitor honeypot activity and respond promptly to emerging threats.

### Data Analysis

- Through Kibana, users can perform in-depth analysis of honeypot data to gain insights into attacker tactics, techniques, and procedures (TTPs).
- Advanced search and filtering capabilities enable users to focus on specific types of attacks or entities, facilitating targeted analysis.
- Statistical analysis and correlation can be applied to identify relationships between different attack vectors or to detect coordinated attacks from multiple sources.
- By analyzing honeypot data, security teams can enhance their understanding of the threat landscape and prioritize mitigation efforts based on the severity and frequency of detected threats.

## Additional Resources

- [Setup Video - Newer](https://www.youtube.com/watch?v=FtR9sFJlkSA&t=241s)
- [Setup Video - Older](https://www.youtube.com/watch?v=TCTMR77c0dk&t=936s&pp=ygUWdC1wb3QgaG9uZXlwb3QgcHJvamVjdA%3D%3D)
- [TPot Main Repository](https://github.security.telekom.com/2024/04/honeypot-tpot-24.04-released.html#first-start)
