## Net Services Profile File (sqlnet.ora)

Use Oracle NETCA to create the Oracle Net Services profile, or the `sqlnet.ora` file.

In an Oracle Grid Infrastructure installation, the `sqlnet.ora` file is located in the following directory by default:

    Grid_home/network/admin

For the local listener for the Oracle RAC database instance, the default location of the `sqlnet.ora` file is `$ORACLE_HOME/network/admin` directory. In this directory there is a default `sqlnet.ora` file. Also, you can find a sample `sqlnet.ora` file in the subdirectory `sample`.

Oracle Net Configuration Assistant (NETCA) creates the following entry in the `sqlnet.ora` file:

    NAMES.DIRECTORY_PATH=(TNSNAMES, EZCONNECT)

The parameter `NAMES.DIRECTORY_PATH` specifies the priority order of the naming methods to use to resolve connect identifiers to connect descriptors.

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-profiles.md) for more information about the` sqlnet.ora` file

**Parent topic:** [Oracle Net Services Configuration Files and Parameters](oracle-net-services-configuration-files-and-parameters.md)
