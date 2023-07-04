# Server Message Block (SMB) Client

Server Message Block (SMB) is a network protocol that is commonly used for network file and printer sharing.  It is most often used in Windows, but can also be found regularly in Linux and MacOS.

The `smbclient` tool can be used to enumerate shares on a host as well as to transfer files to/from a server with an accessible SMB share.

Useful parameters:

- `-L|--list` - Lists services available on an SMB server.
- `-U|--user` - Specify the username to connect to the share with.
- `--password` - Specify the password to connect to the share with.
- `-N|--no-pass` - Connect without a password
- `-m|--max-protocol` - Specify the highest protocol version to try.  Using `NT1` will test for SMBv1 availabilty.
