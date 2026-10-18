# Reflection

Answer in your own words after completing the lab.

## Cisco Reflection Questions

### 1. What are the advantages of using HTTPS instead of HTTP?

**Answer:**

>   HTTPS encrypts data in transit, so passwords and other private information cannot be read by someone capturing the traffic. It also protects against changes to the data in transit, and its certificate helps confirm the website's identity.

### 2. Are all websites that use HTTPS considered trustworthy?

**Answer:**

>   No. HTTPS only means the connection is encrypted. Attackers can also get certificates for harmful or phishing sites, so the site still has to be judged by its domain and context.

## My Questions

### 3. What did the HTTP POST request reveal, and why does that matter?

>   It revealed the login details in plain text. That matters because anyone on the path between me and the server could read them.

### 4. What changed when I inspected HTTPS traffic?

>   The HTTP section was replaced by TLS, and the content became encrypted and unreadable.

### 5. What difficulties did I face, and how did I solve them?

> No difficulties was faced

### 6. What would I do differently or explore next?

>I would like to look at the TLS handshake in Wireshark and at how certificates are checked.

## Portfolio Summary

Write 3 to 5 sentences describing what you did, the tools you used, and what you learned. Write it after the lab, based only on your real work.

>In this lab I used tcpdump to capture HTTP and HTTPS traffic and analysed it in Wireshark. The HTTP capture showed login details in plain text, while the HTTPS capture showed only encrypted data. This showed me why encryption matters for data in transit, and also that HTTPS alone does not make a site trustworthy.
