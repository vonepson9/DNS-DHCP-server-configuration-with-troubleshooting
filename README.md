# 😎 DNS-DHCP Server Configuration with Troubleshooting

In this lab, I configured a DNS server using **Active Directory Domain Services (AD DS)** and deployed a **DHCP server**. The project includes setting up a reverse lookup zone, configuring a DHCP scope, and troubleshooting both DNS and DHCP services to ensure proper network functionality.

---

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
- Reboot if required.

### ✅ Step 2: Configure Reverse Lookup Zone

- Open **DNS Manager**.
- Right-click **Reverse Lookup Zones** → select **New Zone**.
- Choose **Primary Zone**, enter the first 3 octets of your IP (e.g., `192.168.1`).
- Complete the wizard.

### ✅ Step 3: Enable PTR Record Creation

- Go to **Forward Lookup Zone**.
- Right-click your domain → **Properties**.
- Ensure **“Automatically create PTR record”** is checked.

### ✅ Step 4: Configure DHCP Server and Scope

- Install the DHCP role.
- Create a new scope:
  - Set the IP range.
  - Subnet mask.
  - Default gateway.
  - DNS servers.
- Add **exclusions** if necessary.

---

## 🔍 DNS Troubleshooting

1. Open Command Prompt and run:
   ```bash
   ipconfig
   nslookup google.com
   ping 8.8.8.8
   ping google.com
   ```

2. If `nslookup` fails or pinging google.com doesn’t resolve:
   - Confirm the DNS server is running in `services.msc`.
   - Make sure **port 53** isn’t blocked by your firewall.
   - Check the adapter’s IPv4 settings:
     - Set to **Obtain DNS server address automatically**, or manually set to:
       - `127.0.0.1` (loopback for internal)
       - Local DNS server IP
       - `8.8.8.8` (for external testing)
   - Go to the DNS server settings and configure **Forwarders**:
     - Primary: `8.8.8.8`
     - Alternate: `8.8.4.4`
   - Then flush and register the DNS:
     ```bash
     ipconfig /flushdns
     ipconfig /registerdns
     ```

---

## 🧪 DHCP Troubleshooting

1. Run:
   ```bash
   ipconfig
   ```

2. If you get a `169.x.x.x` APIPA address:
   - Run:
     ```bash
     ipconfig /release
     ipconfig /renew
     ```

3. Still broken? Check:
   - IPv4 settings → set to **Obtain IP address automatically**.
   - Go to `services.msc`:
     - Ensure **DHCP Client** and **DHCP Server** are **Running** and **Automatic**.
   - Verify firewall isn’t blocking **UDP ports 67 & 68**.
   - Finally, ping the **default gateway** to confirm connectivity.

---

## 🧠 Final Thoughts

This lab sharpened my skills in configuring and debugging two essential services. I now understand how DNS and DHCP interact within an AD DS environment — and how to keep them running smooth like butter on a hot biscuit. 🧈🔥

---

## 🚀 Author

**Von** — Future Cloud Security Engineer in the making.  
_Lab complete. Logs clean. Let’s move to the next challenge._

