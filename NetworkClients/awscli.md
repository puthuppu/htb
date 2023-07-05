# Amazon Web Services Command-line Interface (awscli)

The awscli is a command-line tool to manage Amazon Web Services (AWS).  Usage: `aws <command> <subcommand>`.

Useful commands:

- `configure` - Prompts for configuration values if no subcommands are specified
- `s3` - Runs commands against an S3 bucket
  - `ls` - Lists the contents of the bucket\
  - `cp <src> <dst>` - Copies files to/from the bucket

Useful parameters:

- `--endpoint-url` - Overrides the default AWS URL (useful when targeting S3 compatible APIs)
