# Lab Guide

Step-by-step record of the lab. Commands use plain hyphens (`-i`). The Cisco PDF uses en dashes (`–i`), which fail if pasted into a terminal.

**VM login (from the lab):** user `analyst`, password `cyberops`.

---

## Part 1: Capture and View HTTP Traffic

### Step 1: Identify the interface

```bash
ip address
```

Record each interface and its IP address in `OBSERVATIONS.md`. The lab example uses `enp0s3`. Use your own interface name if it differs.

### Step 2: Start the capture

```bash
sudo tcpdump -i enp0s3 -s 0 -w httpdump.pcap
```

| Option | Meaning |
|---|---|
| `-i enp0s3` | Capture on this interface only |
| `-s 0` | Use the default maximum snapshot length (262144 bytes), so whole packets are saved |
| `-w httpdump.pcap` | Write packets to a file instead of printing them |

Expected result: `tcpdump: listening on enp0s3, link-type EN10MB (Ethernet), capture size 262144 bytes`. The terminal then appears to hang. This is normal, because it is capturing.

### Step 3: Generate HTTP traffic

1. Open the browser in the VM and go to `http://www.altoromutual.com/login.jsp`.
2. Click the **Password** field. The browser shows a warning because the site uses HTTP, not HTTPS.
3. Log in with the lab's demonstration credentials: username `Admin`, password `Admin`.
4. Close the browser.

Altoro Mutual is a deliberately insecure practice site, and `Admin` / `Admin` are the public demo credentials given in the lab. Never use real credentials here.

### Step 4: Stop the capture

Return to the terminal and press `CTRL+C`. tcpdump prints how many packets were captured.

### Step 5: Open the capture in Wireshark

Open the File Manager, go to `/home/analyst/`, and open `httpdump.pcap` with Wireshark.
(Alternative from the terminal: `wireshark httpdump.pcap &`)

### Step 6: Inspect the POST request

1. In the filter bar enter `http` and click **Apply**.
2. Select the **POST** message.
3. In the lower pane expand **HTML Form URL Encoded: application/x-www-form-urlencoded**.
4. Record the two items shown in `OBSERVATIONS.md`.
5. Take a screenshot.
6. Close Wireshark.

---

## Part 2: Capture and View HTTPS Traffic

### Step 1: Start the capture

```bash
sudo tcpdump -i enp0s3 -s 0 -w httpsdump.pcap
```

### Step 2: Generate HTTPS traffic

1. Open the browser and go to `www.netacad.com`.
2. **If you see "Secure Connection Failed"**, the VM clock is wrong. Set it, then reload:

   ```bash
   sudo date -s "17 OCT 2026 12:00:00"
   ```

   Use the current date and time.
3. Note the website URL (look at the beginning of the address and the padlock).
4. The lab then has you click **Log in** and sign in with your own NetAcad account.
   - This uses a **real account**. The traffic is encrypted, but `httpsdump.pcap` still records your activity, so keep it private. Never screenshot the login form with your details filled in.
   - Merely loading the page generates the same TLS Application Data traffic, so you can skip the login if you prefer.
5. Close the browser.

### Step 3: Stop the capture

Press `CTRL+C` in the terminal.

### Step 4: Inspect the HTTPS capture

1. Open `httpsdump.pcap` in Wireshark.
2. Enter the filter `tcp.port==443` and click **Apply**.
3. Select an **Application Data** packet.
4. Compare the lower pane with the HTTP capture: what replaced the HTTP section?
5. Expand the TLS (Transport Layer Security) section completely.
6. Click **Encrypted Application Data** and check whether it is readable.
7. Take screenshots, then close all windows and shut down the VM.

---

## Key Point to Remember

HTTPS protects the data in transit, but it does not prove a website is trustworthy. Threat actors also use HTTPS to hide their activity.

## Notes From My Run

- Interface used: `enp0s3`
- "The page loaded without any clock errors." 