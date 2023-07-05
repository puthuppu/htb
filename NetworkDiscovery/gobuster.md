# Gobuster

[Gobuster](https://github.com/OJ/gobuster "Gobuster") is a brute-force enumeration tool for URIs, DNS subdomains, web server virtual hosts, Amazon S3 and Google Cloud buckets, and TFTP servers.

Useful commands:

- `dir` - Run in directory/file enumeration mode
  - `u|--url` - Scan a target URL
  - `a|--useragent` - Set a user-agent string
  - `x|--extensions` - File extension(s) to search for
- `vhost` - Run in virtual host brute-forcing mode
  - `u|--url` - Scan a target URL
  - `--append-domain` - This will append the main domain from the URL specified (usually want this when targeting a domain)
- `-w|--wordlist` - Specify a [wordlist](https://github.com/danielmiessler/SecLists "SecLists") to use for brute-forcing
