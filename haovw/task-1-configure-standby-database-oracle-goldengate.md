## Task 1: Configure the Standby Database for Oracle GoldenGate

The standby database initialization parameters should match those of the primary database.

See [Task 1: Configure the Oracle Database for Oracle GoldenGate](task-1-configure-oracle-database-oracle-goldengate.md) for details. This includes the following parameters:

- `ENABLE_GOLDENGATE_REPLICATION=TRUE`

- For Oracle GoldenGate source databases, enable `FORCE LOGGING` mode and enable minimal supplemental logging.

- If a GoldenGate source database, or running integrated Replicat (parallel or non-parallel), configure the `STREAMS_POOL_SIZE`.
