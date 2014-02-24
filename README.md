STC
===

STC (daemon) written in REXX to perform SQL queries and planify tasks

The main module (STCRXPPL) is loaded as STC. Then it loops, sleeping for 15 secs per iteration,
checking for command rows when awoken.

There are two kinds of command rows:

- PLANIFIED: Commands to be exectued certain days a week, at a specified time.
- NOT PLANIFIED: Commands to be executed on demand. Less-privileged users load these rows using 
an utility crafted for this purpose.

The GUI module allows to perform CRUD operations on the DB2 table, acting like an interface to the main module.
It can also wake the STC up by sending SIGCONT to its PID.
