# MySQL Client

MySQL/MariaDB is a popular SQL database that runs on port 3306 by default.  The `mysql` tool is used to connect to MySQL servers.

## Useful Parameters

- `-h|--host` - Connect to host
- `-P|--port` - Connect to host on specified port
- `-u|--user` - Connect as the specified user

## Useful Commands Once Connected to a Server

Once connecte to a MySQL server you can use SQL to interact with the server.  All commands must end in a `;`.  Some common commands when doing discovery:

- `SHOW databses;` - Lists databases available on the server
- `USE <database>;` - Changes to `<database>`
- `SHOW tables;` - Lists the tables in the database
