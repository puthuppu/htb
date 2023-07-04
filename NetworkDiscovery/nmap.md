# nmap

`nmap` is an extensible network mapping tool that is used extensively for enumerating open ports and services.  Some scans can take a long time and hitting any key will display the current progress of the scan.

## Common parameters

There are several common parameters that can be used to manage scope and discovery when running `nmap`.

- `-p` - Scan specific ports.  Ranges can be used and the start (1) and end (65535) can be omitted if necessary.  Therefore `-p 1-65535`, `-p -65535`, `p1-` and `-p-` are all equivalent and scan all ports instead of the default most common 1,000 ports.  Specific protocols can be specified by prefixing `T:` or `U:` for TCP and UDP respectively.
- `-sV` - Service/Version detection
- `-sC` - Default script scan
- `-sS` - TCP SYN scan
- `-sU` - UDP Scan
