# PCAP Analysis

Capture files generated in this lab:

```text
httpdump.pcap
httpsdump.pcap
```

## Why they are not committed

The `.gitignore` excludes `*.pcap`. A capture records everything on the interface while it runs, so it can contain URLs, hostnames, IP addresses, cookies and credentials. This repository documents the analysis through screenshots and written findings instead.

If you ever decide a capture is safe to share (for example, a short capture of only the demo-site login), review it in Wireshark first, then force-add it:

```bash
git add -f 04-pcap-analysis/httpdump.pcap
```

Never force-add `httpsdump.pcap` if you logged in to a real account.

## Analysis checklist

### HTTP (`httpdump.pcap`)

- [ ] Opened in Wireshark
- [ ] Applied the `http` filter
- [ ] Located the POST request
- [ ] Expanded the form-data section
- [ ] Recorded what was visible
- [ ] Screenshot saved

### HTTPS (`httpsdump.pcap`)

- [ ] Opened in Wireshark
- [ ] Applied `tcp.port==443`
- [ ] Selected an Application Data packet
- [ ] Expanded the TLS section
- [ ] Recorded whether the data was readable
- [ ] Screenshot saved

## Packet notes

Add short notes here on specific packets you examined.

| Frame | Source | Destination | Protocol | Note |
|125|172.20.10.3|146.75.89.91|TLSv1.3|---|
| | | | | |
