# Restore MySQL Crash in MAMP

If you have a problem to start MySQL because of crash with following error message, you can restore it with next steps.

Error log
```
2018-01-31 10:09:47 3502 [Note] InnoDB: Starting crash recovery.
2018-01-31 10:09:47 3502 [Note] InnoDB: Reading tablespace information from the .ibd files...
2018-01-31 10:09:47 3502 [ERROR] InnoDB: Attempted to open a previously opened tablespace. Previous tablespace www/access_logs uses space ID: 2 at filepath: ./www/access_logs.ibd. Cannot open tablespace mysql/innodb_index_stats which uses space ID: 2 at filepath: ./mysql/innodb_index_stats.ibd
2018-01-31 10:09:47 7fff97f97340  InnoDB: Operating system error number 2 in a file operation.
InnoDB: The error means the system cannot find the path specified.
InnoDB: If you are installing InnoDB, remember that you must create
InnoDB: directories yourself, InnoDB does not create them.
InnoDB: Error: could not open single-table tablespace file ./mysql/innodb_index_stats.ibd
InnoDB: We do not continue the crash recovery, because the table may become
InnoDB: corrupt if we cannot apply the log records in the InnoDB log to it.
InnoDB: To fix the problem and start mysqld:
InnoDB: 1) If there is a permission problem in the file and mysqld cannot
InnoDB: open the file, you should modify the permissions.
InnoDB: 2) If the table is not needed, or you can restore it from a backup,
InnoDB: then you can remove the .ibd file, and InnoDB will do a normal
InnoDB: crash recovery and ignore that table.
InnoDB: 3) If the file system or the disk is broken, and you cannot remove
InnoDB: the .ibd file, you can set innodb_force_recovery > 0 in my.cnf
InnoDB: and force InnoDB to continue crash recovery here.
```

## Recovery steps (using MAMP v4.2.1)
1. Create `my.cnf` file in `/Applications/MAMP/conf/`
2. Add recovery option to the cnf file.
```
[mysqld]
innodb_force_recovery = 1
```
3. Start mysql 
```
./Applications/MAMP/bin/startMysql.sh
```
4. Stop mysql
```
./Applications/MAMP/bin/stopMysql.sh
```
5. delete the my.cnf file
6. start MAMP

## References
[Stackoverflow](https://stackoverflow.com/questions/33829888/innodb-attempted-to-open-a-previously-opened-tablespace/40039043#40039043)
