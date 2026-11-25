Use the `chactl status` command to check monitoring status of the running targets.

If you do not specify any parameters, then the `chactl status` command returns the status of all running targets.

The monitoring status of an Oracle Cluster Health Advisor target can be either `Monitoring`  or  `Not Monitoring`. The `chactl status` command shows four types of results and depends on whether you specify a target and `-verbose` option.

The `-verbose` option of the command also displays the monitoring status of targets contained within the specified target and the names of executing models of each printed target. The `chactl status` command displays targets with positive monitoring status only. The `chactl status` command displays negative monitoring status only when the corresponding target is explicitly specified on the command-line.

### Syntax

    chactl status {cluster|database [-db db_unique_name]} [-verbose][-help]

### Examples

- To display the list of cluster nodes and databases being monitored:

      #chactl status
      Monitoring nodes rac1Node1, rac1Node2
      Monitoring databases SalesDB, HRdb

  **Note:**

  A database is displayed with **Monitoring** status, if Oracle Cluster Health Advisor is monitoring one or more of the instances of the database, even if some of the instances of the database are not running.

- To display the status of Oracle Cluster Health Advisor:

      $ chactl status
      Cluster Health Advisor service is offline.

  No target or the `-verbose` option is specified on the command-line. Oracle Cluster Health Advisor is not running on any node of the cluster.

- To display various Oracle Cluster Health Advisor monitoring states for cluster nodes and databases:

      $ chactl status database -db SalesDB
      Monitoring database SalesDB

      $ chactl status database -db bogusDB
      Not Monitoring database bogusDB

      $ chactl status cluster
      Monitoring nodes rac1,rac2
      Not Monitoring node rac3

  or

      $ chactl status cluster
      Cluster Health Advisor is offline

- To display the detailed Oracle Cluster Health Advisor monitoring status for the entire cluster:

      $ chactl status –verbose
      Monitoring node(s) racNd1, racNd2, racNd3, racNd4 using model MidSparc

      Monitoring database HRdb2, Instances HRdb2I1, HRdb2I2 in server pool SilverPool using model M6
      Monitoring database HRdb, Instances HRdbI4, HRdbI6 in server pool SilverPool using model M23
      Monitoring database testHR, Instances inst3 on node racN7 using model TestM13
      Monitoring database testHR, Instances inst4 on node racN8 using model TestM14

  When the target is not specified and the `–verbose` option is specified, the `chactl status` command displays the status of the database instances and names of the models.

**Parent topic:** [chactl Command Reference](chactl-command-reference.md)
