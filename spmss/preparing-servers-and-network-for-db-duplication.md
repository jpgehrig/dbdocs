Create a standby database by duplicating the active database. RMAN copies the datafiles directly from the primary database to the standby database.

You must mount or open the primary database before running the `RMAN DUPLICATE FROM ACTIVE DATABASE` command.

- [Prerequisites Specific to Active Database Duplication](prerequisites-specific-to-active-database-duplication.md)
  When you execute `DUPLICATE` with `FROM ACTIVE DATABASE`, at least one normal target channel and at least one `AUXILIARY` channel are required.
- [Checklist for Preparing Active Database Duplication](checklist-for-preparing-active-db-duplication.md)
  Ensure that you prepare source and target databases before using RMAN to carry out active database duplication.
- [Configuring RMAN Channels for Use in Oracle Database Duplication](configuring-rman-channels-for-use-in-duplication.md)
  RMAN channels perform the primary job of database duplication
- [Configuring Automatic Channels Across File Systems](configuring-automatic-channels-across-file-systems.md)
  Configure a set of persistent, automatic channels for use in all RMAN sessions.
- [Configuring Channels for Active Database Duplication](configuring-channels-for-activedb-duplication.md)
  With active database duplication, you need not change your source database channel configuration or configure auxiliary channels. However, you may want to increase the parallelism setting of the source database disk channels so that RMAN copies files over the network in parallel.
