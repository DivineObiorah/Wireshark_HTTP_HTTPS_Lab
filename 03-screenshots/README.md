# Screenshots and Evidence

Add your own screenshots here using these filenames. Each one is referenced from `05-findings/FINDINGS.md`.

| File | What it should show |
|---|---|
| `01-network-interface.png` | Output of `ip address` with the capture interface visible |
| `02-http-tcpdump.png` | tcpdump running for the HTTP capture |
| `03-http-filter.png` | Wireshark with the `http` filter applied |
| `04-http-post-analysis.png` | The POST message with the form-data section expanded |
| `05-https-tcpdump.png` | tcpdump running for the HTTPS capture |
| `06-https-filter.png` | Wireshark with `tcp.port==443` applied |
| `07-encrypted-application-data.png` | The TLS Application Data packet with Encrypted Application Data selected |

## Before you commit a screenshot

Check that it does not show:

- Your real NetAcad username, email or password
- Session tokens or cookies
- Personal information or other open tabs and windows

The lab's demo login (`Admin` / `Admin`) on the practice site is public and acceptable to show.

Only screenshots you actually took from your own lab run belong here.

## About These Screenshots

All screenshots were taken during my own run of the lab in the CyberOps Workstation VM. Screenshots 04 and 07 are the most important: they show the readable HTTP form data and the encrypted HTTPS application data side by side.