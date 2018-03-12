Database Tips
====
Hello.  Here are some database commands and steps I use when importing/exporting.

- [MySQL](#mysql)
  * [Create a Database](#create-a-database)
  * [Import a Dump](#import-a-dump)
  * [Export a Dump](#export-a-dump)
- [PostgreSQL](#postgresql)
  * [Create a Database](#create-a-database-1)
  * [Import a Dump](#import-a-dump-1)
  * [Create a Role](#create-a-role)

MySQL
-----
### Create a Database
1. Log into the MySQL Prompt.
2. Use the `create database` command to create:
* `create database <databaseName>;`

### Import a Dump

1. Log into the MySQL Prompt.
2. Select the database to be used:

`use <databaseName>`

3. Use `source` to import the dump into the selected database:

`source <filePathToDump>`

### Export a Dump
The command, `mysqldump` is used to create dump files:

`mysqldump -u [username] -p[password] [dbname] > [filePath/to/backupfile.sql]`

In case the packet sizes are too small for the export to complete:

`mysqldump -u [username] -p[liferay] --max_allowed_packet=2147483648 [dbname] > [filePath/to/backupfile.sql]`

Note: There is **no** space between the `-p` flag and the password.


PostgreSQL
-----

### Create a Database
1. Open a command prompt and log into Postgres (psql.exe):
`psql.exe --username=postgres`
2. In the PSQL prompt:
`create database <database-name>;`

### Import a Dump
1. Open a command prompt and log into Postgres (psql.exe):

`psql.exe --username=postgres`
2. In the command prompt:

`psql.exe --username=postgres (database-name) < FilePathToDump.dmp`

Some imports may fail based on how the export was created.  In this case, the following are some alternatives that can be used for import attempts.

```
psql.exe -U postgres -d <database-name> -a -f <dump-file name>

pg_restore -U postgres -d dbname filename
```

### Create a Role
During some imports, the logs may indicate that a role does not exist.  In this case, we will create a new role:

`create role <role-name>;`
