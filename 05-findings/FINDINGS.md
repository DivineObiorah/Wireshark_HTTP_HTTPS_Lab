# Findings

Complete this file after finishing the lab. Describe only what you captured and saw in your own screenshots.

## HTTP

**What I captured:**

>I captured traffic on `enp0s3` with tcpdump while logging in to altoromutual.com over HTTP, and saved it as `httpdump.pcap`.


**What was visible in the POST request:**

>The submitted form data was readable in plain text: [field] = [value] and [field] = [value].


**Evidence:** `03-screenshots/03-http-filter.png`, `03-screenshots/04-http-post-analysis.png`

## HTTPS

**What I captured:**

>I captured traffic on `enp0s3` while visiting www.netacad.com over HTTPS, and saved it as `httpsdump.pcap`.


**What was different from the HTTP capture:**

>There was no HTTP section. The data was inside TLS and showed only as encrypted hexadecimal, so I could not read any page content.


**Evidence:** `03-screenshots/06-https-filter.png`, `03-screenshots/07-encrypted-application-data.png`

## Security Interpretation

What does this lab show about the risk of sending data over HTTP, and about what HTTPS does and does not protect?

>This lab shows that HTTP exposes what is sent, including passwords, to anyone who can capture the traffic. HTTPS encrypts the content in transit, so a capture shows only unreadable data. However, HTTPS only protects the connection. It does not prove the website itself is honest or safe.


## Limitations

What this lab did not cover (for example, certificate validation, or the trustworthiness of the destination site).

>This lab used one site for each protocol and one capture each. I did not decrypt the TLS traffic, inspect the certificates, or check how trustworthy the sites were.
