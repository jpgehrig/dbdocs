Run the `tnsping` command from the source and destination servers.

    [oracle @ ora12c-prm admin] $ tnsping standby-db-unique-name
    [oracle @ ora12c-dup admin] $ tnsping primary-db-unique-name

Oracle recommends that you connect remotely as `sysdba` to ensure that the communication is established properly.

Start SQL\*Plus using a command in the following format:

    sqlplus {username | /} [as sysdba]

For example:

    $ sqlplus / AS SYSDBA
    Enter password: password

Alternatively, to start SQL\*Plus connected to a database other than the default, enter the SQL\*Plus command in the format:

    $> sqlplus username/password@connect_identifier

**Parent topic:** [Configuring the Network Between Source and Target Oracle Databases](configuring-the-network-between-source-and-target-dbs.md)
