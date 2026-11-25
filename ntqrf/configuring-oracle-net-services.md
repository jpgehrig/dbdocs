During database server installation, Oracle Net Configuration Assistant configures `listener.ora` and `tnsnames.ora` files for external procedure calls.

When an application calls an external procedure, Oracle Net Listener starts an external procedure agent called `EXTPROC`. By default, the `extproc` process communicates directly through the server process. Using a network connection established by the listener, the application passes the following information to `EXTPROC`:

- DLL name

- External procedure name

- Parameters (if necessary)

`EXTPROC` then loads the DLL, runs the external procedure, and passes back any values returned by the external procedure.

If you overwrite default `listener.ora` and `tnsnames.ora` files, then you must manually configure the following files for the external procedure behavior described previously to occur:

- `ORACLE_HOME``\network\admin\listener.ora`

- `ORACLE_HOME``\network\admin\tnsnames.ora`

  **Note:**

  Additional security may be required for the listener in a production environment.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md)

**Parent topic:** [Installing and Configuring Oracle Database and Oracle Net Services](installing-and-configuring-oracle-database-and-oracle-net-services.md)
