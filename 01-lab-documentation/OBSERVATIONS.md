# Lab Observations

Fill this in from your own VM and captures. Write only what you actually saw.

## Date completed

`18th october,2026`

## Part 1: Network Interface

| Interface | IP address |
|enp0s3|172.20.10.3


**Interface used for capture:** `enp0s3`

## Part 1: HTTP Capture

**Capture file:** `httpdump.pcap`  
**Wireshark filter:** `http`

**What did you observe in the HTTP messages?**

>  With the `http` filter, I could see the browser's GET requests for the login page and the server's responses. When I submitted the login form, a POST request appeared in the list.

**Question: What two pieces of information are displayed in the HTML Form URL Encoded section?**

>  The two form fields: [field name 1] = [admin] and [field name 2] = [admin]. In my capture these were my username and password, shown in plain text.

**What does this show about HTTP?**

>  HTTP does not encrypt form data. Anyone who can capture the traffic can read login details directly, which is why login pages should not use HTTP.

## Part 2: HTTPS Capture

**Capture file:** `httpsdump.pcap`  
**Wireshark filter:** `tcp.port==443`

**Question: What do you notice about the website URL?**

>  The URL starts with `https://` and the browser shows a padlock, which means the connection is encrypted.

**Question: What has replaced the HTTP section that was in the previous capture file?**

>  A Transport Layer Security (TLS) section, shown as TLSv1.2 or TLSv1.3. The packets were labelled Application Data.

**Question: Is the application data in a plaintext or readable format?**

>  No. The Encrypted Application Data was a long string of hexadecimal characters that I could not read.

## Problems Encountered

Describe anything that went wrong and how you fixed it (for example, the clock error or a wrong interface name).

> No major problems.

## Evidence Checklist

- [ ] 01 Network interface
- [ ] 02 tcpdump HTTP capture
- [ ] 03 HTTP filter
- [ ] 04 HTTP POST analysis
- [ ] 05 tcpdump HTTPS capture
- [ ] 06 HTTPS filter
- [ ] 07 Encrypted Application Data
