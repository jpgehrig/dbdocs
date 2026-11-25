Use the `chactl config` command to list all the targets being monitored, along with the current model of each target.

If the specified target is a multitenant container database (CDB) or a cluster, then the `chactl config` command also displays the configuration data status.

### Syntax

    chactl config {cluster|database -db db_unique_name}[-help]

### Examples

To display the monitor configuration and the specified model of each target:

    $ chactl config
    Databases monitored: prodDB, hrDB

    $ chactl config database –db prodDB
    Monitor: Enabled
    Model: GoldDB

    $ chactl config cluster
    Monitor: Enabled
    Model: DEFAULT_CLUSTER

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
