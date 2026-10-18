# GitHub Push Guide

Follow these steps from inside the project folder, only after the lab documentation is complete.

## 1. Pre-push safety check

```bash
# Make sure no capture files are about to be committed
git status

# Search for anything that looks like a secret
grep -rniE "password|passwd|token|cookie|secret" --include="*.md" .
```

Review every match. The lab's public demo login is fine to mention. Anything real is not.

Also open each screenshot and confirm it shows no real username, password, email, session token or cookie.

## 2. Create the repository on GitHub

1. Go to GitHub and select **New repository**.
2. Name: `wireshark-http-https-lab`
3. Leave it empty (no README, no .gitignore, no license), because this project already has them.
4. Choose **Public** and click **Create repository**.

## 3. Push

```bash
git init
git add .
git status          # confirm no .pcap files are listed
git commit -m "Add Wireshark HTTP and HTTPS traffic analysis lab"
git branch -M main
git remote add origin https://github.com/DivineObiorah/wireshark-http-https-lab.git
git push -u origin main
```

## 4. After pushing

- Open the repository page and check that the README displays correctly.
- Click through each screenshot link in `05-findings/FINDINGS.md`.
- Add a short repository description and the topics `wireshark`, `tcpdump`, `network-analysis`, `cybersecurity`.
