# 🔧 DNS-DHCP Server Configuration with Troubleshooting

In this lab, I configured DNS using **Active Directory Domain Services (AD DS)** and set up a **DHCP server**. I also created a DNS reverse lookup zone, configured a DHCP scope, and performed troubleshooting for both DNS and DHCP services to ensure everything ran smoothly like butter on a warm biscuit. 🧈🧠

---

## 🌐 DNS & DHCP Lab Setup ⚙️

This project walks through the process of:

- Configuring a DNS server via AD DS  
- Creating a reverse lookup zone  
- Setting up a DHCP server and scope  
- Troubleshooting DNS and DHCP  
- Making sure your network isn’t running on duct tape and prayers 🙏

---

## 🎥 Video Walkthrough

📺 [Click here to watch the lab in action](https://drive.google.com/file/d/1CccqnvOKeAjWPxsRc6aCztyR5D-ZHB56/view?usp=sharing)

---

## 🔧 What’s Inside

- 🧱 AD DS Setup & Domain Controller  
- 🧭 DNS Server Configuration  
- 🔁 Reverse Lookup Zone  
- 📡 DHCP Server Configuration + Scope Setup  
- 🛠️ DNS/DHCP Troubleshooting Techniques  

---

## 📚 Why This Matters

Foundational services like **DNS** and **DHCP** are the *heart* of network infrastructure. Whether you're diving into cybersecurity or chasing cloud dominance, these skills are non-negotiable.

This lab gave me real-world experience configuring and fixing these services — because reading the book is one thing, but watching that DNS service crash mid-test? Different story. 😮‍💨💻

---

## 🧩 Step-by-Step Configuration Guide

### ✅ Step 1: Configure AD DS and Promote to Domain Controller

- Install the **Active Directory Domain Services** role  
- Promote your server to a **Domain Controller**  
- Restart when prompted  

---

### 🔁 Step 2: Create a DNS Reverse Lookup Zone

- Open **DNS Manager**  
- Right-click **Reverse Lookup Zones** > **New Zone**  
- Select **Primary Zone**  
- Enter the first three octets of your network IP (e.g., `192.168.1`)  
- Complete the wizard to finish the zone creation  

---

### 📌 Step 3: Enable Automatic PTR Record Creation

- In **DNS Manager**, right-click the **Domain Controller name**  
- Click **Properties**  
- Check the box for **“Enable automatic PTR record creation”**  

---

### 📡 Step 4: Configure DHCP Server + Scope

- Install the **DHCP Server** role  
- Open the **DHCP Management Console**  
- Create a **New Scope**:
  - Set IP range (e.g., `192.168.1.100 - 192.168.1.200`)
  - Add Exclusions (e.g., `192.168.1.110 - 192.168.1.115`)
  - Configure lease duration, router, and DNS options  
- **Activate** the scope  

---

## 🛠️ Step 5: Troubleshooting DNS Issues

### 🔍 Basic Checks

```bash
ipconfig /all
nslookup google.com
ping 8.8.8.8
ping google.com
```

- If `ping 8.8.8.8` works but `ping google.com` fails → **DNS problem confirmed**

---

### 🔧 Fixes

- **Firewall**: Ensure **Port 53** (DNS) isn’t blocked  
- **IPv4 Settings**:
  - Set DNS to **Obtain automatically**, or
  - Use:
    - `127.0.0.1` (loopback) for internal DNS
    - Local DNS server IP
    - `8.8.8.8` (Google public DNS for test)

- **Services App**:
  - Make sure **DNS Server** service is **Running** and **Automatic**

- **DNS Forwarders**:
  - In **DNS Manager**, set forwarders to:
    - `8.8.8.8`
    - `8.8.4.4`

- Refresh DNS settings:

```bash
ipconfig /flushdns
ipconfig /registerdns
```

Then re-test with:

```bash
ping google.com
nslookup google.com
```

---

## 🧪 Step 6: Troubleshooting DHCP Issues

### 🔍 Basic Checks

```bash
ipconfig /all
```

- Confirm **DHCP Enabled = Yes**
- If your IP starts with `169.x.x.x` (APIPA), that means DHCP failed 😬

Run:

```bash
ipconfig /release
ipconfig /renew
```

---

### 🔧 Fixes

- **IPv4 Settings**: Ensure it's set to **Obtain IP address automatically**
- **Services App**:
  - Ensure both **DHCP Server** and **DHCP Client** services are **Running** and **Automatic**
- **Firewall**:
  - Make sure **Ports 67 and 68** (DHCP) aren’t blocked

After changes, run:

```bash
ipconfig /release
ipconfig /renew
```

Then verify by pingin

