## Patching Oracle Database Using Local-Mode Configuration

The independent local-mode automaton updates Oracle Database homes, including Oracle Database single-instance databases in a cluster or standalone (with no Oracle Grid Infrastructure), an Oracle RAC database, or an Oracle RAC One Node database.

- The local-mode (independent automaton) configuration for Oracle Database patching performs all of the steps necessary to switch from one home to another. Because the automaton is not aware of gold images, moving the database requires two home paths, as follows:
      $ rhpctl move database -sourcehome Oracle_home_path -desthome destination_oracle_home_path

  **Note:**

  If multiple databases are running from the same Oracle home, then you can use the `-dbname` parameter to specify all the database for the move. If the databases are running from different Oracle homes, then you need to patch all the databases separately.

Use the `rhpctl move database` command parameters for the patching operation.

**Note:**

The `rhpctl move database` command is Oracle Data Guard-aware, and will not run Datapatch if the database is an Oracle Data Guard standby.

**Related Topics**

- [rhpctl move database](database-commands.md)

**Parent topic:** [Oracle Fleet Patching and Provisioning Local Mode](oracle-fpp-local-mode.md)
