# SIEM-in-Azure

### Tools Used
- Azure Cloud for creating resource groups, creating workbooks, writing custom logs, and visualizing data
- Security Information and Event Management (SIEM) system for log ingestion and analysis
- Virtual Machine to create a vulnerable environment that is an easy target for attackers
- Powershell for running scripts
- Windows Event Viewer for monitoring logs 


### Steps
1. Virtual Machine Setup:
Created a Virtual Machine (VM) in Azure, deliberately exposing it to the Internet by disabling its external and Windows firewalls. This involves making the VM vulnerable to pings and discovery from anywhere. This is NOT standard practice and is only being used to generate enough data to use for the world map.

2. Log Repository Establishment:
Set up a Log Analytics Workspace in Azure to store all the logs coming from our VM.

3. Azure Sentinel Configuration:
Implement Azure Sentinel (Microsoft's Cloud SIEM) within Azure. Used its capabilities to create a map visualizing diverse attacker data, offering insights into the countries of origin and other relevant information.

4. Geographic Data Extraction and Logging:
Employed PowerShell to run a script that extracts the IP address from a Windows failed logon attempt. This IP address is then sent to the third-party API (IPGeolocation) to derive geographic details such as latitude, longitude, country, and more. The results are sent back to the VM, creating a custom log (failed_rdp.log) before being ingested into Azure Sentinel for mapping.


Virtual Machine:

<img src="https://lh3.googleusercontent.com/pw/AP1GczM3U5zVga1u0dQJShBR4TbaSG_Tgj_Tk5iT-QCjlULLWk8f3VYfzff3EDenLfpQI7Qi8XvNJ26boxxfY82SLi1qpBypqnfXYVkv_lZDVGGvS3Spp6Y=w2400" width="500" length="500"/>

The plotted attack above shows on this instance of the VM, there seemed to have been a Brute Force attack from somewhere in Ukraine which produced most of the attacks as well as other attacks all from around the country of Ukraine. There are also 3 purposely failed login 
attempts recorded from my location in the US as well. 


Attack Logs Example:

<img src="https://lh3.googleusercontent.com/pw/AP1GczN7uds7c0UY5dWlzKtk1lX1_DGOUCOZ05-CCp5uhy8KdPT__NyNjlVLT6dmxGK1U41K56343w9v7tB7MYwPjjlZ1aTdN9vcy5UIhDokqlA52XVDD2M=w2400" width="700" length="1200"/>
Logs of attackers unsuccessfully trying to access the VM
