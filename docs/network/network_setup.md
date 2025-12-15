# Networking Setup on Client Side

This guide explains how to configure networking on the **client side** for communication with the **Inference System (IS)** on the internal network.

---

## 1. Connect the Inference System (IS) to the Internal Network

Currently, connecting the IS requires a **USB network interface**, since the **Realtek 2.5 Gbit network card** does not yet have a native Ubuntu driver in the package repositories.

If this card is used without a compatible driver, the network connection may be lost after each system update.

> **Note:**  
> Always ensure the IS remains connected to the same internal network segment as the client machines.

---

## 2. Assign a Static IP Address to the IS

The IS must have a **static IP address** that persists across reboots or power outages.

If the IS IP changes, clients configured with static host entries will no longer be able to reach it.

Once configured, refer to this IP as:

```
IS_STATIC_IP
```

> **Example:**  
> If the IS static IP is `192.168.1.50`, then `IS_STATIC_IP = 192.168.1.50`.

---

## 3. Configure Client Computers

All client computers that should access the Chat UI or other IS-hosted services must be configured to resolve the IS hostname locally.

Configuration differs by operating system.

---

### **Linux**

1. Open the hosts file in a text editor with root privileges:

   ```bash
   sudo nano /etc/hosts
   ```

2. Verify the file contains the default entries:

   ```
   127.0.0.1   localhost
   127.0.1.1   system_hostname
   
   # IPv6 entries
   ::1     ip6-localhost ip6-loopback
   fe00::0 ip6-localnet
   ff00::0 ip6-mcastprefix
   ff02::1 ip6-allnodes
   ff02::2 ip6-allrouters
   ```

3. Add a new line under the `system_hostname` entry:

   ```
   IS_STATIC_IP   CLIENTDNSNAME.secmed.org
   ```

   Replace `CLIENTDNSNAME` with the client’s designated name.

   **Example:**

   ```
   192.168.1.50   portal10.secmed.org
   ```

4. Save and exit (`Ctrl+O`, `Enter`, then `Ctrl+X`).

5. Verify connectivity:

   ```bash
   ping CLIENTDNSNAME.secmed.org
   ```

---

### **Windows**

1. Open **Notepad** as Administrator:

   - Click **Start**, type “Notepad”, right-click it, and select **Run as administrator**.

2. Open the hosts file:

   ```
   C:\Windows\System32\drivers\etc\hosts
   ```

3. Add the IS mapping at the bottom:

   ```
   IS_STATIC_IP   CLIENTDNSNAME.secmed.org
   ```

   **Example:**

   ```
   192.168.1.50   portal10.secmed.org
   ```

4. Save the file and close Notepad.

5. Test the setup:

   - Open **Command Prompt** and run:

     ```cmd
     ping CLIENTDNSNAME.secmed.org
     ```

   You should see replies from the IS static IP.

---

### **macOS**

1. Open **Terminal**.

2. Edit the hosts file:

   ```bash
   sudo nano /etc/hosts
   ```

3. Add the following line:

   ```
   IS_STATIC_IP   CLIENTDNSNAME.secmed.org
   ```

   **Example:**

   ```
   192.168.1.50   portal10.secmed.org
   ```

4. Save and exit (`Ctrl+O`, `Enter`, `Ctrl+X`).

5. Flush the DNS cache:

   ```bash
   sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
   ```

6. Verify connectivity:

   ```bash
   ping CLIENTDNSNAME.secmed.org
   ```

---

## 4. Verification

After configuration, ensure each client can reach the IS.

- **Ping Test:**

  ```bash
  ping CLIENTDNSNAME.secmed.org
  ```

- **Browser Test:**
  Open a browser and navigate to:

  ```
  http://CLIENTDNSNAME.secmed.org
  ```

If successful, the Chat UI or other IS services should load correctly.

---

## 5. Notes and Best Practices

- Document each client’s `CLIENTDNSNAME` and verify uniqueness.  
- If DHCP is used for other devices, **reserve the IS static IP** in your DHCP configuration to prevent conflicts.  
- Update all client host files if the IS static IP changes.  
- Test connectivity after any system update, network reconfiguration, or hardware change.

---

## 6. Troubleshooting

| Issue                                | Possible Cause                   | Solution                                                    |
| ------------------------------------ | -------------------------------- | ----------------------------------------------------------- |
| Client cannot ping IS                | Incorrect IP or hostname mapping | Check `/etc/hosts` or `hosts` file entries                  |
| Connection lost after reboot         | IS IP not static                 | Reassign static IP on the IS                                |
| Realtek 2.5 Gbit adapter not working | Missing driver                   | Use USB Ethernet adapter or install Realtek driver manually |
| Browser cannot open Chat UI          | Firewall or port issue           | Check IS firewall and ensure correct port access            |

---
