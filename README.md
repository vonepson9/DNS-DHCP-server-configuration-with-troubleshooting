# 🧠 DNS-DHCP Server Configuration with Troubleshooting

In this lab, I configured a DNS server using **Active Directory Domain Services (AD DS)** and deployed a **DHCP server**. The project includes setting up a reverse lookup zone, configuring a DHCP scope, and troubleshooting both DNS and DHCP services to ensure proper network functionality.

## 🌐 DNS & DHCP Lab Setup ⚙️

This setup simulates foundational services in a Windows Server environment that are critical for both enterprise networks and cloud-based infrastructure.

---

## 🎥 Video Walkthrough  
[Watch the lab demo](https://drive.google.com/file/d/1CccqnvOKeAjWPxsRc6aCztyR5D-ZHB56/view?usp=sharing)

---

## 🔧 What’s Inside

- 🧱 **AD DS Setup & Domain Controller**  
- 🧭 **DNS Server Configuration**  
- 🔁 **Reverse Lookup Zone**  
- 📡 **DHCP Server Configuration + Scope Setup**  
- 🛠️ **Troubleshooting (DNS/DHCP)**

---

## 📚 Why This Matters

Mastering services like **DNS** and **DHCP** is non-negotiable for anyone stepping into cybersecurity or cloud roles. This lab gave me real-world experience in configuring and troubleshooting these key components.

---

## 🪛 Step-by-Step Configuration

### ✅ Step 1: Set up AD DS & Promote to Domain Controller
- Install the AD DS role.
- Promote the server to a domain controller.
- Reboot if necessary.

### ✅ Step 2: Configure Reverse Lookup Zone in DNS
- Open DNS Manager → Right-click **Reverse Lookup Zones** → Select **New Zone**.
- Choose **Primary Zone** and enter the first 3 octets of your network (e.g. `192.168.1`).
- Finish the wizard.

### ✅ Step 3: Enable PTR Record Creation
- Go to **Forward Lookup Zone** → Right-click your domain → **Properties**.
- Ensure **"Automatically create PTR record"** is checked.

### ✅ Step 4: Configure the DHCP Server
- Install DHCP role.
- Create a new scope with:
  - IP range
  - Subnet mask
  - Default gateway
  - DNS servers
- Add **exclusions** if needed.

---

## 🔍 Step 5: Troubleshooting DNS

1. Open Command Prompt:
   ```bash
   ipconfig
   nslookup google.com
   ping 8.8.8.8
   ping google.com

