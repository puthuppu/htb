# Redis Command Line Interface (CLI)

Redis is a popular in-memory data store that is used for caching, as a database, or as a message-broker.  Data in Redis is stored as key-value pairs.

## Useful Parameters for the `redis-cli` Tool

- `-h` - Specify the hostname to connect to.

## Useful Commands Once Connected to a Server

- `help @server` - Lists commands available in the `server` command group.
- `info` - Get information and statistics about the server.  The `Keyspace` section lists the databases and number of enteries in each.
- `select <db index>` - Connects to a database.
- `keys <pattern>` - Find all keys matching the given pattern.
- `get <key>` - Returns the value of the specified key.
