# dima-cli

A command-line tool to list, inspect and kill database queries.

# Setup:

Either install on a mac using `brew install dima` or:

1. Clone this repo
2. Set up the credentials (see below)
3. Run: `sudo ./deploy.sh`

# Credential Setup

Database credentials can be provided in 2 ways - in a `~/.dima_creds` file or as environment variables.
DIMA will look first for the environment variables, and then to the creds file. You can set the following environment variables:

	DIMA_DB_DBNAME
	DIMA_DB_USER
	DIMA_DB_HOST
	DIMA_DB_PORT
	DIMA_DB_PASSWORD

or place them in a `~/.dima_creds` file (the prefix `~/` means that it should be in your home directory). A sample file `sample_creds` is in this repo.

# Usage:

	dima
Shows a list of running queries

	dima show [PID]
Inspects a specific running query

	dima rm [-f] [Lock / filter keyword / PID]	

Terminates queries either with `wait_event_type` "Lock" or according to a filter keyword or PID. Use -f to avoid the confirmation.

# Multiple credentials

The default credentials are all prefixed with `DIMA_DB_`.
You can add more credentials for different services underneath, as long as they use a different `DIMA_something` prefix. E.g.

	DIMA_DW2_DBNAME
	DIMA_DW2_USER

To inspect this DB, use the `-c` option, e.g. for a prefix `DIMA_DW2_something` use:

	dima -c DW2 show

# Screenshots

<img src="https://github.com/Frameio/dima-cli/raw/master/dima_cmd.png" alt="dima command" width="500"/>
<img src="https://github.com/Frameio/dima-cli/raw/master/dima_show_cmd.png" alt="dima show command" width="500"/>
<img src="https://github.com/Frameio/dima-cli/raw/master/dima_rm_cmd.png" alt="dima rm command" width="500"/>

