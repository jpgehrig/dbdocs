Describes how to export all data from an existing database to a new database.

To export:

1.  Set `ORACLE_SID` to the database service of the database whose contents you intend to export. For example, if the database you intend to export is the starter database `orcl`, then enter the following at the command prompt. Note that there are no spaces around the equal sign (`=`) character.
        C:\> set ORACLE_SID=orcl
2.  If the existing database is Oracle Database 10g Release 1 (10.1) or later, then start Data Pump Export from the command prompt:
        C:\> expdp SYSTEM DUMPFILE=myexp.dmp FULL=y LOG=myexp.log
        Password: password

    You now have a full database export of the starter database `orcl` in the file `myexp.dmp`. All messages from Data Pump Export are logged in file `myexp.log`.
3.  If the existing database is earlier than Oracle Database 10g Release 1 (10.1), then start Export from the command prompt:
        C:\> exp SYSTEM FILE=myexp.dmp FULL=y LOG=myexp.log
        Password: password

    You now have a full database export of the starter database `orcl` in the file `myexp.dmp`. All messages from Export are logged in the file `myexp.log`.

**Parent topic:** [About Exporting an Existing Database](about-exporting-an-existing-database.md)
