# NETWORKWALKS-BO83-WK2--PM1--Penetration-Testing-Report-
A practical penetration testing project covering different types of footprinting in Kali Linux and Nmap-based network scanning techniques. Includes reconnaissance methods, information gathering, host discovery, port scanning, service enumeration and basic scan analysis.

## Footprinting & Network Scanning Phases

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

| **Field**                                       | **Detail**                                                                                                            |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Pentester Name (Cybersecurity Professional)** | **Afrose Banu**                                                                                                     |
| **Program/Batch**                               | B083-Networkwalks                                                                                                     |
| **Date**                                        | 19 SEPTEMBER 2026                                                                                                        |
| **Modules completed**                           | W2-PM1 (Multiple Kali Tools)<br>W2-PM4 ( The Harvester)<br>W2-PM5 (Zenmap Scanning)                                                              |
| **Client/Target**                               | 1. Networkwalks (secured written permission already)<br>2. My own local LAN Network                                   |
| **Permission secured from client?**             | Yes                                                                                                                   |
| **Phases covered**                              | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery<br>**Phase 3-5:** In Progress |

# 1. Liability Disclaimer

I have performed these activities only on systems and devices where I had secured written permission or on devices and systems that I own myself. All materials are for educational and research purposes only.

Do not use anything from this report to access or compromise systems without authorization. The instructor, authors and Networkwalks are not responsible for misuse of this knowledge. Every action taken is the responsibility of the individual performing it.

Unauthorized access and security testing may violate applicable laws and regulations. Security testing should always be performed within an approved scope and with appropriate authorization.

# 2. Introduction

This report covers footprinting and reconnaissance activities using multiple Kali Linux tools and network scanning using Zenmap.

The footprinting activities included **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, DNSRecon and theHarvester**. These tools were used to collect different types of publicly available information about domains, web technologies, DNS infrastructure and other externally observable information.

The second activity involved using **Zenmap** to perform network discovery on my own local network.

Together, these activities demonstrate how a security professional can move from passive information gathering and reconnaissance toward identifying hosts and understanding the structure of a network.

All activities were performed as part of Week 2 of my ongoing cybersecurity internship program at Networkwalks.

# 3. Tools Used

The table below lists the tools used in this report and their purpose.

| **Tool**             | **Purpose**                                                                                     |
| -------------------- | ----------------------------------------------------------------------------------------------- |
| Kali Linux & Windows | Operating systems used for reconnaissance and scanning activities                               |
| WHOIS                | Find publicly available domain registration information, dates and name servers                 |
| WhatWeb              | Fingerprint web technologies such as CMS platforms, servers and plugins                         |
| Nslookup             | Resolve domain names to IP addresses using DNS                                                  |
| Curl -I              | Inspect HTTP response headers from a web server                                                 |
| Wafw00f              | Identify whether a Web Application Firewall is protecting a website                             |
| DNSRecon             | Enumerate DNS records such as NS, MX, SPF, TXT and SRV records                                  |
| theHarvester         | Gather publicly available information related to a target domain using supported search sources |
| Zenmap (Nmap GUI)    | Discover live hosts and identify IP and MAC address information on a local network              |
| Windows CMD          | Identify local IP address, subnet and MAC address information                                   |

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

I performed reconnaissance activities using several Kali Linux tools: **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, DNSRecon and theHarvester**.

Each tool was used for a different purpose, allowing me to understand how multiple sources of information can be combined during the reconnaissance phase.

### 4.1.1 WHOIS

I used **WHOIS** to obtain publicly available domain registration information and identify information such as domain registration details and name servers.

The results provided information that can be useful for understanding the publicly visible aspects of a domain and its associated infrastructure.

### 4.1.2 WhatWeb

I used **WhatWeb** to identify technologies used by the website.

The results identified **WordPress 7.0.4** and **WP Download Manager 3.3.58**, along with other information exposed by the website.

Technology fingerprinting can help a security professional understand the technologies present on a target before performing further authorized security testing.

### 4.1.3 Nslookup

Using **Nslookup**, I resolved the domain name to its IP address.

The provided result identified:

`192.232.216.135`

This demonstrates how DNS information can be used during reconnaissance to identify the IP address associated with a domain.

### 4.1.4 Curl

I used **Curl** with the `-I` option to inspect the HTTP response headers returned by the website.

The response provided additional technical information about the web application and exposed the WordPress REST API endpoint:

`/wp-json/`

HTTP headers can sometimes reveal information about the underlying web server or application and can therefore contribute to technology fingerprinting.

### 4.1.5 Wafw00f

I used **Wafw00f** to determine whether a Web Application Firewall was protecting the website.

The result identified:

**ModSecurity (SpiderLabs)**

This provided information about the security technology deployed in front of the web application.

### 4.1.6 DNSRecon

I used **DNSRecon** to enumerate DNS records associated with the target domain.

The results provided information relating to:

* Name servers
* Mail servers
* SPF/TXT records
* Service records
* DNS-related information

DNS reconnaissance can help build a broader understanding of the publicly exposed infrastructure associated with a domain.

### 4.1.7 theHarvester

I also used **theHarvester** as part of the reconnaissance phase to gather publicly available information associated with a domain.

For this activity, I used the following command:

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
```

Where:

* `-d microsoft.com` specifies the target domain.
* `-l 1000` sets the result limit to 1000.
* `-b baidu` specifies Baidu as the data source.

The purpose of this exercise was to understand how **theHarvester** can be used to collect publicly available information from search sources during the reconnaissance phase.

TheHarvester can be useful during early-stage reconnaissance because it can help security professionals identify information that is already publicly available about a target.

**Note:** The results obtained from this command should be documented using the actual output and screenshots collected during the practical exercise. No additional findings are assumed in this report.

## 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network.

The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet.

I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.

The example results provided in the practical identified four live hosts:

* `10.0.2.2`
* `10.0.2.3`
* `10.0.2.15`

The example results also included 2 MAC addresses.

10.0.2.15 - 08-00-27-AB-8A-49 ( own pc)
10.0.2.2 - 52-54-00-12-35-00 ( QEMU virtual NAC)
10.0.2.3 - 52-54-00-12-35-00 ( QEMU virtual NAC)

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.

**Note:** The actual subnet, number of hosts, IP addresses and MAC addresses should be replaced with the results from my own network when submitting the final report.

# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks and security observations.

| **#** | **Risk / Finding**                                                 | **Evidence / Observation**                                                  | **Potential Impact**                                                                                            | **Risk Level** |
| ----- | ------------------------------------------------------------------ | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | -------------- |
| 1     | Web technology information exposed                                 | WhatWeb identified WordPress and WP Download Manager                        | Attackers may use exposed technology/version information to identify software requiring further security review | **Medium**     |
| 2     | Server IP address identifiable                                     | Nslookup resolved the domain to `192.232.216.135`                           | Provides information about the network location of the web service                                              | **Low**        |
| 3     | HTTP technical information exposed                                 | Curl returned HTTP response headers and exposed `/wp-json/`                 | May assist technology fingerprinting and further enumeration                                                    | **Low**        |
| 4     | WAF technology identifiable                                        | Wafw00f identified ModSecurity (SpiderLabs)                                 | Reveals information about the web application's security architecture                                           | **Low**        |
| 5     | DNS infrastructure information exposed                             | DNSRecon identified DNS, mail and service-related records                   | DNS information can help build a broader infrastructure profile                                                 | **Medium**     |
| 6     | Publicly available information discoverable through search sources | theHarvester was used against `microsoft.com` with Baidu as the data source | Publicly available information may assist reconnaissance and further information gathering                      | **Low**        |
| 7     | Multiple live hosts visible on local network                       | Zenmap identified live hosts in the example network                         | Unknown or unauthorized devices may potentially be present on a network                                         | **Medium**     |

**Risk level key:** Critical | Medium | Low

The risks above are observations from the footprinting and scanning exercises and should not automatically be interpreted as confirmed vulnerabilities.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these modules.

The presence of information such as a software version, IP address, DNS record or publicly available search result does not by itself mean that a system is vulnerable. Further authorized security testing would be required to confirm an actual vulnerability.

# 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

1. **Review publicly exposed technology information**

   Organizations should regularly review what information about their web technologies, CMS platforms and plugins is publicly visible.

2. **Keep software updated**

   CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.

3. **Review HTTP headers**

   HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

4. **Review DNS records regularly**

   DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

5. **Properly configure and monitor the WAF**

   The Web Application Firewall should remain enabled, properly configured and regularly monitored.

6. **Review publicly available information**

   Organizations should periodically review information available through search engines and other public sources to understand what information about their infrastructure may be discoverable.

7. **Perform regular internal network discovery**

   Organizations should periodically scan their own networks to identify active devices.

8. **Investigate unknown devices**

   Any unexpected device discovered during network scanning should be investigated and verified.

9. **Maintain network documentation**

   Network topology and device information should be documented and updated regularly.

10. **Perform security testing with authorization**

    Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization and scope have been established.

# 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering **footprinting, reconnaissance and network scanning**.

In the footprinting activity, I used multiple Kali Linux tools to collect different types of information about domains and web infrastructure.

I learned how **WHOIS** can provide domain registration information, **WhatWeb** can identify web technologies, **Nslookup** can resolve domain names, **Curl** can inspect HTTP headers, **Wafw00f** can identify a WAF, **DNSRecon** can provide additional DNS information, and **theHarvester** can collect publicly available information from search sources.

For the theHarvester exercise, I used:

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
```

This helped me understand how publicly available information can be collected from external sources during the reconnaissance phase.

In the network scanning activity, I used **Zenmap** to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

These exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information, DNS records, web responses and network activity.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create and what can be done to reduce that risk.

Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

# 8. Evidences Collected

<img width="1236" height="986" alt="Whois" src="https://github.com/user-attachments/assets/10915afc-ac01-4e51-a0da-28ff50333e39" />
<img width="1912" height="992" alt="Whatweb" src="https://github.com/user-attachments/assets/6f3daad8-1282-4ca0-a226-b6cbe4d666a5" />
<img width="1917" height="926" alt="nslookup" src="https://github.com/user-attachments/assets/54b38a7d-07d2-4848-9e21-bf5f65bdd124" />
<img width="1902" height="931" alt="curl" src="https://github.com/user-attachments/assets/c59b3f11-296a-4441-839a-1216392b3529" />
<img width="1915" height="870" alt="DNS" src="https://github.com/user-attachments/assets/d6dcdcde-5780-4958-85d7-0ae07f763ec9" />
<img width="1887" height="990" alt="Harvester" src="https://github.com/user-attachments/assets/747093f1-9d73-4207-9a1a-0100da05ed4f" />
<img width="1916" height="850" alt="WAF" src="https://github.com/user-attachments/assets/f724479a-5bdf-4afd-8388-b9ba709741ee" />
<img width="1057" height="717" alt="Zenmap installation" src="https://github.com/user-attachments/assets/57de5b00-1a02-4de1-b19e-d7218b1d2dfb" />
<img width="1157" height="677" alt="zenmap - ping scan" src="https://github.com/user-attachments/assets/15ae41f4-8146-4937-9a69-c06cd2502c20" />
<img width="1020" height="717" alt="Zenmap - topology" src="https://github.com/user-attachments/assets/5c13e190-dbed-4625-856d-7c7b48ead5b8" />

