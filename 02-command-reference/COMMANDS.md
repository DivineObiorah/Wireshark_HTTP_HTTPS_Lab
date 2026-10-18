# Command Reference

## Terminal commands

| Purpose | Command |
|---|---|
| List interfaces and IPs | `ip address` |
| HTTP capture | `sudo tcpdump -i enp0s3 -s 0 -w httpdump.pcap` |
| HTTPS capture | `sudo tcpdump -i enp0s3 -s 0 -w httpsdump.pcap` |
| Stop a capture | `CTRL+C` |
| Confirm the files exist | `ls -lh *.pcap` |
| Open a capture in Wireshark | `wireshark httpdump.pcap &` |
| Fix a wrong VM clock | `sudo date -s "17 OCT 2026 12:00:00"` |
| Read the tcpdump manual | `man tcpdump` |

Replace `enp0s3` with the interface shown by `ip address` on your system.

## tcpdump options used

| Option | Purpose |
|---|---|
| `-i` | Select the capture interface. Without it, tcpdump picks a default interface. |
| `-s 0` | Capture whole packets (default snapshot length of 262144 bytes). |
| `-w` | Write raw packets to a file. Use a `.pcap` extension so Wireshark can open it. |

## Wireshark display filters used

| Filter | Shows |
|---|---|
| `http` | HTTP messages (requests and responses) |
| `tcp.port==443` | TCP traffic on port 443, used by HTTPS |

## Troubleshooting

| Problem | Likely cause and fix |
|---|---|
| `tcpdump: No such device exists` | Wrong interface name. Run `ip address` and use the real one. |
| `Permission denied` | Run tcpdump with `sudo`. |
| `invalid option` after pasting | The command contains an en dash (`–`) instead of a hyphen (`-`). Retype it. |
| No POST message in Wireshark | The login did not happen during the capture. Repeat Part 1. |
| "Secure Connection Failed" in the browser | VM clock is wrong. Fix it with `date -s` (above). |
| Empty `.pcap` file | The capture was stopped too early or used the wrong interface. |
