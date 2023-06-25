# MySQL

## Help

```bash
mysql> help
```

## List of all MySQL commands

Note that all text commands must be first on line and end with `;`

```bash
? (\?) Synonym for `help'.
clear (\c) Clear command.
connect (\r) Reconnect to the server. Optional arguments are db
and host.
delimiter (\d) Set statement delimiter.
edit (\e) Edit command with $EDITOR.
ego (\G) Send command to mysql server, display result
vertically.
exit (\q) Exit mysql. Same as quit.
go (\g) Send command to mysql server.
help (\h) Display this help.
nopager (\n) Disable pager, print to stdout.
notee (\t) Don't write into outfile.
pager (\P) Set PAGER [to_pager]. Print the query results via
PAGER.
print (\p) Print current command.
prompt (\R) Change your mysql prompt.
quit (\q) Quit mysql.
rehash (\#) Rebuild completion hash.
source (\.) Execute an SQL script file. Takes a file name as an
argument.
status (\s) Get status information from the server.
system (\!) Execute a system shell command.
tee (\T) Set outfile [to_outfile]. Append everything into given
outfile.
use (\u) Use another database. Takes database name as argument.
charset (\C) Switch to another charset. Might be needed for processing
binlog with multi-byte charsets.
warnings (\W) Show warnings after every statement.
nowarning (\w) Don't show warnings after every statement.
```

### For server side help

```bash
’help contents’.
```

## Connect

```bash
mysql -u USERNAME -pPASSWORD;
```

## Create a database

```bash
mysql> create database DB_NAME;
```

## Switch to a database

```bash
mysql> use DB_NAME;
```

## Show Tables

```bash
 mysql> show tables;
```

## Drop Table

```bash
 mysql> drop table [table name];
```

## Drop Multiple Tables

```bash
mysql> drop table table_name, second_table_name, [etc];
```

## Restore a previous backup

```bash
mysql -u USER -p dbname < path-to-backup.mysql;
```

## List all the dbs

Once logged in, the bash turns to `mysql >`

```bash
 mysql> SHOW DATABASES;
```

## Export DB

```bash
mysqldump --add-drop-table -uUSERNAME -pPWD DB_NAME > DBdump.sql;
```

## Real example

```bash
mysqldump --add-drop-table --skip-comments --compatible=mysql4 -
uroot -proot nothsblog_qa_box > QA_box_db.sql
```

## Import DB

```bash
mysql DB_NAME -u USERNAME -p < DBdump.sql;
```

## Local DB to remote

```bash
mysqldump --add-drop-table DB_NAME | ssh user@site "mysql -u
USERNAME -pPASSWORD DB_NAME"
```

## Remote DB to local

```bash
ssh user@site "mysqldump --add-drop-table -u USERNAME -pPASSWORD
DB_NAME" | mysql DB_NAME
```

---

### More Commands

- [https://www.pantz.org/software/mysql/mysqlcommands.html](https://www.pantz.org/software/mysql/mysqlcommands.html)

---

#Bash #CommandLine