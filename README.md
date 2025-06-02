# 🔧 DNS & DHCP Server Configuration Lab with Troubleshooting  
> Full setup of DNS via AD DS, DHCP server/scope creation, and step-by-step troubleshooting  

## 🎥 Video Walkthrough  
- 📺 [**Watch DNS/DHCP Lab in Action**](https://drive.google.com/file/d/1CccqnvOKeAjWPxsRc6aCztyR5D-ZHB56/view?usp=sharing)

---

![OS](https://img.shields.io/badge/Windows_Server_2022-blue?logo=windows&logoColor=white)
![Tools](https://img.shields.io/badge/AD_DS-grey?logo=microsoft&logoColor=white)
![Tools](https://img.shields.io/badge/DNS_Server-blue?logo=windows&logoColor=white)
![Tools](https://img.shields.io/badge/Reverse_Lookup_Zone-yellow?logo=windows&logoColor=black)
![Tools](https://img.shields.io/badge/DHCP_Server-orange?logo=microsoft&logoColor=white)
![Tools](https://img.shields.io/badge/DNS_Troubleshooting-red?logo=powershell&logoColor=white)
![Tools](https://img.shields.io/badge/DHCP_Troubleshooting-green?logo=windows&logoColor=white)

---

## 🔧 What’s Inside  

- 🧱 **AD DS Setup & Domain Controller Promotion**  
- 🧭 **DNS Server Configuration**  
- 🔁 **Reverse Lookup Zone Creation**  
- 📡 **DHCP Server Setup + Scope Configuration**  
- 🛠️ **Troubleshooting for DNS and DHCP Services**

---

## 💼 Lab Overview

This lab demonstrates how to properly configure core network services in a Windows Server environment. It walks through the complete setup and validation of a DNS server, reverse lookup zone, and DHCP scope, followed by practical troubleshooting methods for resolving common issues. These are foundational skills essential for both system administration and cybersecurity roles.

---

## 🧩 Step-by-Step Configuration Guide

### ✅ Step 1: AD DS Installation and Domain Controller Setup

- Install the **Active Directory Domain Services** role  
- Promote the server to a **Domain Controller**  
- Reboot as needed

---

### 🔁 Step 2: DNS Reverse Lookup Zone

- Launch **DNS Manager**  
- Right-click **Reverse Lookup Zones** → **New Zone**  
- Choose **Primary Zone** → Enter network prefix (e.g., `192.168.1`)  
- Complete the wizard to finalize setup

---

### 📌 Step 3: Enable PTR Record Creation

- In **DNS Manager**, right-click the **Server Name**  
- Go to **Properties**  
- Check **Enable automatic PTR record creation**

---

### 📡 Step 4: DHCP Configuration & Scope Setup

- Install the **DHCP Server** role  
- Open **DHCP Management Console**  
- Create a **New Scope**:
  - IP Range: `192.168.1.100 – 192.168.1.200`  
  - Exclusions: `192.168.1.110 – 192.168.1.115`  
  - Configure router (default gateway), DNS server IP, and lease time  
  - Activate the scope

---

## 🛠️ DNS Troubleshooting

### 🔍 Verify Settings

```bash
ipconfig /all
nslookup google.com
ping 8.8.8.8
ping google.com
```

### 🔧 Common Fixes

- **Firewall**: Port 53 (DNS) must be open  
- **IPv4 Config**: Use loopback (`127.0.0.1`) or internal DNS server IP  
- **DNS Service**: Ensure **DNS Server** is **Running** and **Automatic**  
- **DNS Forwarders**: Add `8.8.8.8` and `8.8.4.4` in DNS Manager  

```bash
ipconfig /flushdns
ipconfig /registerdns
```

---

## 🧪 DHCP Troubleshooting

### 🔍 Verify IP Assignment

```bash
ipconfig /all
```

- Check if **DHCP Enabled = Yes**  
- If IP is `169.x.x.x` → DHCP not working

### 🔧 Fixes

- Ensure adapter is set to **Obtain IP Automatically**  
- Start **DHCP Client** and **DHCP Server** services  
- Open firewall ports **67** and **68**

```bash
ipconfig /release
ipconfig /renew
```

Then verify by pinging the DHCP gateway as a cherry on top 🍒
