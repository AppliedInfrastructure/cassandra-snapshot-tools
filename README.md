This repository fixes issues that [the original snapshot tool](https://travis-ci.org/AppliedInfrastructure/cassandra-snapshot-tools) has:

* It searches and replaces the original keyspace name even the name appears in the path and are not meant to be replaced.
* It does not match the dot literal correctly.
* If a table name contains a string which happens to be the original keyspace name, the table name is replaced silently.

This repository solves the above problems by doing the following:

* It searches in the current working temporary directory, so the replacement doesn't affect path.
* It introduces a new command line argument -t|--table-keyspace-name to control if the string in table names should be replaced, which defaults to true to keep compatible with the old behavior.
* Fix a bug in the sed command that matches the literal dot.
