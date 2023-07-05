# Network Discovery

Network discovery is the gateway to all the HTB challenges since there is no physical device to compromise.  My install of Kali didn't allow the `cap_net_raw` capability to `ping` so I needed to enable it using:

```bash
sudo setcap cap_net_raw+ep /bin/ping
```

Other network discovery tools include:

- ['gobuster'](gobuster.md "gobuster notes") - Brute-force enumerator for URIs, DNS subdomains, web server virtual hosts, Amazon S3 and Google Cloud buckets, and TFTP servers
- [`nmap`](nmap.md "nmap notes") - Network Mapper
- [`smbclient`](../NetworkClients/smbclient.md "smbclient notes") - Server Message Block (SMB) Client
