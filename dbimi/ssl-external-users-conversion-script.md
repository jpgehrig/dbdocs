You should run the SSL external users conversion script after upgrading to Oracle Database 12c Release 1 (12.1) and later, in case you were using SSL-authenticated external users in a pre-Oracle Database 10g Release 2 (10.2) release. The script converts SSL-authenticated external users in pre-Oracle Database 10g Release 2 (10.2) releases into SSL-authenticated external users in Oracle Database 12c Release 1 (12.1) and later.

**Note:**

The SSL external users conversion script needs to be run only if you have upgraded from a pre-Oracle Database 10g Release 2 (10.2) release.

### About Using a Secure External Password Store

If you want to use a secure external password store, then configure the Oracle wallet as described in the information that follows; otherwise, passwords can be provided interactively and you can skip this section.

Before you run the `extusrupgrade` script, configure a client-side Oracle wallet as a secure external password store so that your applications can use password credentials stored in the wallet to connect to databases. Storing database password credentials in a client-side Oracle wallet eliminates the need to embed passwords in application code, batch jobs, or scripts. This reduces the risk of exposing passwords in the clear in scripts and application code, and allows you to more easily manage password policies for user accounts without changing application code or scripts whenever passwords change.

See [Configuring a Client to Use the External Password Store](../dbseg/configuring-authentication.md) for steps to configure a client to use the external password store by using the `mkstore` command-line utility.

**Note:**

The external password store of the wallet is separate from the area where public key infrastructure (PKI) credentials are stored. Consequently, you cannot use Oracle Wallet Manager to manage credentials in the external password store of the wallet. Instead, use the command-line utility `mkstore` to manage these credentials.

Using the `mkstore CreateCredential` command, configure the following `dbuser` credential by providing information for `<alias, username, ``password``>`, in which you will be prompted to enter the password for the user:

- `dbalias`, `dbuser`, `password`

Configuring this user credential allows you to use the following parameter on the `extusrupgrade` script command line:

- `-dbalias=<db-password-alias>`

Conversion script examples use the following wallet credential information for user `dbuser` that was provided for the alias name, user name, and password. The wallet location is specified as shown.

- `dbmanager1`, `system`, `password`

- `wallet_location=``/oracle/product/db_1/wallets`

Conversion script examples use the following entries on the command-line:

- `-dbalias=dbmanager1`

- `wallet_location=``/oracle/product/db_1/wallets`

After configuring the client-side wallet, enable auto-login for Oracle Wallets to allow the administrator running the `extusrupgrade` script to access and perform `extusrupgrade` services without having to supply the necessary credentials.

**See Also:**

- [Managing the Secure External Password Store for Password Credentials](../dbseg/configuring-authentication.md) for more information about creating a client-side password store wallet to store alias, user name, and password credentials for users

- [About Using Auto Login for Oracle Wallets](using-oracle-wallet-manager.md) for information about enabling auto login for Oracle wallets that enables PKI-based access to services without requiring human intervention to supply the necessary user name passwords required to run the `extusrupgrade` script

This chapter covers the following topics:

- Using the SSL External Users Conversion Script

- Converting Global Users into External Users

### B.1 Using the SSL External Users Conversion Script

The SSL external users conversion script has the following syntax:

    $ORACLE_HOME/rdbms/bin/extusrupgrade
    --dbconnectstring database connect string
    --dbuser database user
    [-dbalias database user password alias]
    [-wallet_location wallet location]
    [-a]
    [-l username1,username2,...]
    [-f filename]
    [-o]
    [-h]
    note:          -a upgrade all qualified users
                   -l upgrade list of users seperated by comma
                   -f upgrade list of users specified by the file. One user name per line
                   -o output all qualified users to standard out. Not combine with other options
                   -h show this help.

The `database connect string` should be in the format `hostname`:`port_no`:`sid`, where `hostname` is the name of the host on which the database is running, `port_no` is the listener port number and `sid` is the system identifier for the database instance.

If you have created a secure external password store using the `mkstore` command-line utility, then create the `dbuser` credential in the wallet using the `mkstore CreateCredential` command using the syntax `<alias, username, password>`. For example, `dbmanager1, system, ``password`.

Next, enable auto login for Oracle wallets. This allows the administrator user running the `extusrupgrade` script access to`extusrupgrade` services without having to supply the necessary credentials.

Now you can use the database alias parameter `-dbalias <database user password alias>` and the wallet location parameter `-wallet_location <wallet location>` on the command line for running the `extusrupgrade` conversion script.

The following examples assume that the wallet has a `dbuser` credential defined using the syntax `<alias, username, password>` as `dbmanager1, system, ``password`. For examples, the wallet location is shown as `/oracle/product/19.1.0/db_1/wallets`.

Use the `-a` option to convert all SSL-authenticated external users. Here is an example:

    extusrupgrade --dbconnectstring mymachine:1521:ORA001 --dbuser system -dbialis dbmanager1 -wallet_location /oracle/product/db_1/wallets -a

Use the `-l` option to specify a comma-delimited list of users to be converted. For example:

    extusrupgrade --dbconnectstring mymachine:1521:ORA001 --dbuser system -dbialis dbmanager1 -wallet_location /oracle/product/db_1/wallets -l user1,user2,user3

Use the `-f` option to specify a file that has the list of users to be converted. For example:

    extusrupgrade --dbconnectstring mymachine:1521:ORA001 --dbuser system -dbialis dbmanager1 -wallet_location /oracle/product/db_1/wallets -f usernames.txt

There should be one user name in each line in the specified file. Here is a sample `usernames.txt` file:

    user#1
    user>2
    user,3
    user4
    user5

You must use the `-f` option to convert users who have special characters (such as \#) in their user names.

**Note:**

You can combine the `-l` and `-f` options in the same command. The script combines the list of users from both the `-l` and `-f` options. If you use the `-a` option along with the `-l option` and the `-f` option, then the `-a` option is ignored.

You can use the `-o` option to print a list of SSL-authenticated external users to the standard output device. The output lists the users you can convert using the extusrupgrade script. The `-o` option cannot be combined with any other option.

    extusrupgrade --dbconnectstring mymachine:1521:ORA001 --dbuser system -dbialis dbmanager1 -wallet_location /oracle/product/db_1/wallets -o

A sample output for this could be:

    user1
    user2
    user3

**Tip:**

You can redirect the command output to a file to get a list of users who can be converted. You can then edit the file and use it with the `-f` option.

### B.2 Converting Global Users into External Users

Oracle Database 10g and later allows SSL-authenticated external users and SSL-authenticated global users to coexist in the database. Previous releases had the restriction that all SSL users must be either global users or external users, depending on whether Oracle Internet Directory is being used or not for authenticating the users.

If you want a user to be able to connect to the database even when Oracle Internet Directory is not available, then the user should be configured as an external user. You can convert SSL-authenticated global users into SSL-authenticated external users by using the SSL external users conversion script.

If you have created a secure external password store using the `mkstore` command-line utility and have created the `dbuser` credential in the wallet using the `mkstore CreateCredential` command using the syntax `<alias, username, password>`. For example, `dbmanager1, system, ``password`. For examples, the wallet location is shown as `/oracle/product/db_1/wallets`. Now you can use the database alias parameter `-dbalias <database user password alias>` and the wallet location parameter `-wallet_location <wallet location>` on the command line when running the `extusrupgrade` conversion script. Note that if you have enabled auto login for Oracle wallets, then the administrator user running the `extusrupgrade` script can access extusrupgrade services without having to supply the necessary credentials.

For example:

    extusrupgrade --dbconnectstring mymachine:1521:ORA001 --dbuser system -dbialis dbmanager1 -wallet_location /oracle/product/db_1/wallets -l user1,user2

The preceding example converts two global users into external users.
