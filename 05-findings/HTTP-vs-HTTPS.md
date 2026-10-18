# HTTP vs HTTPS

General reference comparison.

| Feature | HTTP | HTTPS |
|---|---|---|
| Encryption of application data | None | Yes, using TLS |
| Default port | 80 | 443 |
| What a passive observer can read | Requests, form fields, cookies, page content | Mostly IP addresses, timing and sizes; the content is encrypted |
| Server identity | Not verified | Verified through a certificate |
| Tampering in transit | Possible without detection | Detected, because TLS provides integrity |
| Wireshark filter used in this lab | `http` | `tcp.port==443` |

## Important

HTTPS means the connection is encrypted. It does **not** mean the website is safe or honest. Attackers also obtain certificates for malicious sites, so always consider the domain, the certificate and the context.

## What I observed in my own captures

> In my HTTP capture, the POST request showed the form data in plain text. In my HTTPS capture, the same kind of traffic appeared only as encrypted TLS Application Data. This matched the comparison in the table above.