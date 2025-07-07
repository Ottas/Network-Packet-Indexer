![arkim1](https://github.com/user-attachments/assets/a8c45c2f-aa7e-46d3-9457-0a1b8af7240e)
# Network-Packet-Indexer 

## Objective

Our goal with this project is to show how an analyst can work with multiple PCAPs in a more organized way, without getting lost in thousands of packets.`Arkime` groups packets between source and destination, while Wireshark shows every single one. So for the same event, Arkime might show 
10 events, but Wireshark could display 20,000 events.That’s why we decided to go deeper into Arkime to show how it can help make analysis clearer and more manageable.


### Skills Learned

- Analyzed and interpreted network logs to identify relevant events.
- Used graphs to visualize IPs and network activity, gaining a clearer and more comprehensive overview.
- Developed skills in generating and recognizing attack signatures and patterns.
- Improved understanding of network protocols and common security vulnerabilities. 
- Integrated OSINT tools into our environment for efficient data ingestion and enhanced threat analysis.

### Tools Used

- Arkime - Network capture analysis tool for examining network traffic.
- OSINT tools - Used `urlscan.io` to check IP and URL reputation
- MaxMind - Used MaxMind to retrieve GeoIP data and enrich IP-based analysis with geolocation information.
- Malware-Traffic-Analysis - Utilized Malware Traffic Analysis for creating and studying network traffic and malware behavior.
- Wireshark - Used Wireshark to capture and analyze relevant network packets
---

## Steps Taken

#### 1-> Begin by setting up the Arkime server:
- Spin up an Ubuntu Server 22.04 instance with 8 GB of RAM and 50 GB of disk space, then connect via SSH using PowerShell.
- Download Arkime machine from `https://github.com/arkime/arkime/releases/tag/v5.7.0`

![11111111](https://github.com/user-attachments/assets/698d9dec-43ce-478a-8a10-27cfe54910c4)

- After the file has been downloaded and is visible, it can be executed.

![2](https://github.com/user-attachments/assets/0d476979-6914-409b-ab9b-3b7c59b07322)

            `Arkime` is stored unter the /opt/ directory -> sudo /opt/arkime/bin/

- We will perform some basic configurations, such as creating a password and enabling MaxMind, which will enrich some of the IP addresses as MaxMind provides you with geolocation based.

![33](https://github.com/user-attachments/assets/8c9e6e20-058f-4b70-aca3-2b736c534531)

![5](https://github.com/user-attachments/assets/d402361b-269b-44f0-8e4b-54c0f6e07553)

-Once the configuration is complete, I should be able to access Arkime using my IP address on port 8005. But first, we need to create an account on MaxMind and obtain both the license key and the account ID.

![maxnind](https://github.com/user-attachments/assets/236a1ace-9a5e-400f-9808-47f07dccdb0f)

- And then install the geoipupdate` tool via our SSH connection.

![66](https://github.com/user-attachments/assets/39370fec-9c02-4a8e-a793-ee3008d81bf3)

- Now I can start ingesting PCAP files from (https://www.malware-traffic-analysis.net/)`

![malware traffic](https://github.com/user-attachments/assets/bb334dff-5cae-422b-8195-c2dd6e64a72d)


![malware-analysis](https://github.com/user-attachments/assets/dd6308b9-3e88-4b99-aed9-e7e7f08721e7)


### 2-> Secondly, let’s jump into Arkime and take a look at the data.

![arkimeeeeeeeeeeeeeeeeeeeeeeee](https://github.com/user-attachments/assets/d4b1adc7-4e63-4eb4-aa9c-9e5a3007af38)

- Looking at graphs like this can help you focus on interesting or relevant traffic.

![12](https://github.com/user-attachments/assets/b7323ad3-dc77-4f34-8087-b69164366495)

- SpiView provides us with a clear overview, showing how well-organized and powerful this tool is.

![Screenshot 2025-07-07 165124](https://github.com/user-attachments/assets/8783d532-30f4-488d-bc18-a00739a40e83)


### 3-> We can enrich our data using OSINT tools built into Arkime

-Enable service within Arkime  -> sudo /opt/arkime/bin/Configure --cont3xt
-Configuration file located here -> sudo nano /opt/arkime/etc/cont3xt.ini

![adasdasd](https://github.com/user-attachments/assets/be83d205-61cc-404d-a34f-598f59bbc299)

-Restart -> systemctl restart arkimecont3xt.service and go on our localhost:3218

![Screenshot 2025-07-07 172808](https://github.com/user-attachments/assets/865cf29e-e5b3-466c-9e82-4774458b3d33)

-To connect OSINT to Arkime, you need an API key, provided you have created an account on one of the OSINT tools mentioned above.


![last](https://github.com/user-attachments/assets/2264ebbf-81bc-47b3-a777-6e4472015e39)





   
---
---
## Summary
`Arkime` is a powerful network capture and analysis tool that ingests, indexes, and allows fast searching of PCAP data using Elasticsearch.Elasticsearch is the search database technology that feeds Arkime.
