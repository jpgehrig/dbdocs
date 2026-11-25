Use the `chactl monitor` command to start monitoring all the instances of a specific Oracle Real Application Clusters (Oracle RAC) database using the current set model.

Oracle Cluster Health Advisor monitors all instances of this database using the same model assigned to the database.

Oracle Cluster Health Advisor uses Oracle-supplied gold model when you start monitoring a target for the first time. Oracle Cluster Health Advisor stores monitoring status of the target in the internal store. Oracle Cluster Health Advisor starts monitoring any new database instance when Oracle Cluster Health Advisor detects or redetects the new instance.

### Syntax

    chactl monitor database -db db_unique_name [-model model_name [-force]][-help]

    chactl monitor cluster [-model model_name [-force]]

### Parameters

Table D-1 chactl monitor Command Parameters

| Parameter        | Description                                                                                                                                                                                                         |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `db_unique_name` | Specify the name of the database.                                                                                                                                                                                   |
| `model_name`     | Specify the name of the model.                                                                                                                                                                                      |
| `force`          | Use the `-force` option to monitor with the specified model without stopping monitoring the target.<br>Without the `-force`  option, run `chactl unmonitor`  first, and then `chactl monitor`  with the model name. |

### Examples

- To monitor the `SalesDB` database using the `BlkFridayShopping` default model:

      $ chactl monitor database –db SalesDB -model BlkFridayShopping

- To monitor the `InventoryDB` database using the `Nov2014` model:

      $ chactl monitor database –db InventoryDB -model Nov2014

  If you specify the `model_name`, then Oracle Cluster Health Advisor starts monitoring with the specified model and stores the model in the Oracle Cluster Health Advisor internal store.

  If you use both the `–model` and `–force` options, then Oracle Cluster Health Advisor stops monitoring and restarts monitoring with the specified model.

- To monitor the `SalesDB` database using the `Dec2014` model:

      $ chactl monitor database –db SalesDB –model Dec2014

- To monitor the `InventoryDB` database using the `Dec2014` model and the `-force`  option:

      $ chactl monitor database –db InventoryDB –model Dec2014 -force

### Error Messages

Error: `no CHA resource is running in the cluster.`

Description: Returns when there is no hub or leaf node running the Oracle Cluster Health Advisor service.

Error: `the database is not configured.`

Description: Returns when the database is not found in either the Oracle Cluster Health Advisor configuration repository or as a CRS resource.

Error: `input string “xc#? %” is invalid.`

Description: Returns when the command-line cannot be parsed. Also displays the top-level help text.

Error: `CHA is already monitoring target <dbname>.`

Description: Returns when the database is already monitored.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
