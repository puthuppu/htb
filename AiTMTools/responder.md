# Responder

[Responder](https://github.com/lgandx/Responder "Responder") is a tool used to poison link-local multicast name resolution (LLMNR), multicast DNS (mDNS), and NetBios Name Service (NBT-NS) in order to gather hashes and credentials from the local network.  MITRE provides some [information on Responder](https://attack.mitre.org/software/S0174/ "MITRE Responder Documentation"), including an ATT&CK Navigator layer.

Responder is a python script, and on Kali, the configuration file is located at `/usr/share/responder/Responder.conf`.

Useful parameters:

- `-I|--interface` - Interface to listen on
