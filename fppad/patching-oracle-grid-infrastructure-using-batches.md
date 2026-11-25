## Patching Oracle Grid Infrastructure Using Batches

The third patching method is to sequentially process batches of nodes, with a number of nodes in each batch being restarted in parallel.

This method maximizes service availability during the patching process. When you patch Oracle Grid Infrastructure 12c release 2 (12.2.x) software homes, you can define the batches on the command line or choose to have Fleet Patching and Provisioning generate the list of batches based on its analysis of the database services running in the cluster.

There are two methods for defining batches:

- User-Defined Batches

- Fleet Patching and Provisioning-Defined Batches

### User-Defined Batches

When you use this method of patching, the first time you run the `rhpctl move gihome` command, you must specify the source home, the destination home, the batches, and other options, as needed. The command terminates after the first node restarts.

To patch Oracle Grid Infrastructure using batches that you define:

1.  Define a list of batches on the command line and begin the patching process, as in the following example:

        $ rhpctl move gihome -sourcewc wc1 -destwc wc2 -batches "(n1),(n2,n3),(n4)"

    The preceding command example initiates the move operation, and terminates and reports successful when the Oracle Grid Infrastructure stack restarts in the first batch. Oracle Grid Infrastructure restarts the batches in the order you specified in the `-batches` parameter.

    If your batches do not include all the nodes in the cluster, then Oracle FPP automatically adds the excluded nodes as a new batch group at the end of the list of batches. For example, if your cluster has four nodes n1, n2, n3, n4, and you create two batches as "(n1),(n2)", then Oracle FPP automatically adds a third batch group at the end as "(n1),(n2),(n3,n4)".

    In the command example, node `n1` forms the first batch, nodes `n2` and `n3` form the second batch, and node `n4` forms the last batch. The command defines the source working copy as `wc1` and the patched (destination) working copy as `wc2`.

    **Notes:**

    You can specify batches such that singleton services (policy-managed singleton services or administrator-managed services running on one instance) are relocated between batches and non-singleton services remain partially available during the patching process.

2.  You must process the next batch by running the `rhpctl move gihome` command, again, as follows:

        $ rhpctl move gihome -destwc wc2 -continue

    The preceding command example restarts the Oracle Grid Infrastructure stack on the second batch (nodes `n2` and `n3`). The command terminates by reporting that the second batch was successfully patched.

3.  Repeat the previous step until you have processed the last batch of nodes. If you attempt to run the command with the `-continue` parameter after the last batch has been processed, then the command returns an error.

    If the `rhpctl move gihome` command fails at any time during the above sequence, then, after determining and fixing the cause of the failure, rerun the command with the `-continue` option to attempt to patch the failed batch. If you want to skip the failed batch and continue with the next batch, use the `-continue` and `-skip` parameters. If you attempt to skip over the last batch, then the move operation is terminated.

    Alternatively, you can reissue the command using the `-revert` parameter to undo the changes that have been made and return the configuration to its initial state.

    You can use the `-abort` parameter instead of the `-continue` parameter at any point in the preceding procedure to terminate the patching process and leave the cluster in its current state.

    **Notes:**

    - Policy-managed services hosted on a server pool with one active server, and administrator-managed services with one preferred instance and no available instances cannot be relocated and will go OFFLINE while instances are being restarted.

    - If a move operation is in progress, then you cannot initiate another move operation from the same source home or to the same destination home.

    - After the move operation has ended, services may be running on nodes different from the ones they were running on before the move and you will have to manually relocate them back to the original instances, if necessary.

    - If you use the `-abort` parameter to terminate the patching operation, then Fleet Patching and Provisioning does not clean up or undo any of the patching steps. The cluster, databases, or both may be in an inconsistent state because all nodes are not patched.

    - Depending on the start dependencies, services that were offline before the move began could come online during the move.

### Fleet Patching and Provisioning-Defined Batches

Using Fleet Patching and Provisioning to define and patch batches of nodes means that you need only run one command, as shown in the following command example, where the source working is `wc1` and the destination working copy is `wc2`:

    $ rhpctl move gihome -sourcewc wc1 -destwc wc2 -smartmove -saf Z+ [-eval]

If the move operation fails at some point before completing, then you can either rerun the operation by running the command again, or you can undo the partially completed operation, as follows:

    $ rhpctl move gihome -destwc destination_workingcopy_name -revert [authentication_option]

You can use the `-revert` parameter with an un-managed home.

The parameters used in the preceding example are as follows:

- `-smartmove`: This parameter restarts the Oracle Grid Infrastructure stack on disjoint sets of nodes so that singleton resources are relocated before Oracle Grid Infrastructure starts.
  **Note:**

  If the server pool to which a resource belongs contains only one active server, then that resource will go offline as relocation cannot take place.
  The `-smartmove` parameter:

  - Creates a map of services and nodes on which they are running.

  - Creates batches of nodes. The first batch will contain only the Hub node, if the configuration is an Oracle Flex Cluster. For additional batches, a node can be merged into a batch if:

    - The availability of any non-singleton service, running on this node, does not go below the specified service availability factor (or the default of 50%).

    - There is a singleton service running on this node and the batch does not contain any of the relocation target nodes for the service.

  - Restarts the Oracle Grid Infrastructure stack batch by batch.

- Service availability factor (`-saf ``Z+`): You can specify a positive number, as a percentage, that will indicate the minimum number of database instances on which a database service must be running. For example:

  - If you specify `-saf 50` for a service running on two instances, then only one instance can go offline at a time.

  - If you specify `-saf 50` for a service running on three instances, then only one instance can go offline at a time.

  - If you specify `-saf 75` for a service running on two instances, then an error occurs because the target can never be met.

  - The service availability factor is applicable for services running on at least two instances. As such, the service availability factor can be 0% to indicate a non-rolling move, but not 100%. The default is 50%.

  - If you specify a service availability factor for singleton services, then the parameter will be ignored because the availability of such services is 100% and the services will be relocated.

- `-eval`: You can optionally use this parameter to view the auto-generated batches. This parameter also shows the sequence of the move operation without actually patching the software.

**Related Topics**

- [rhpctl move gihome](gihome-commands.md)

**Parent topic:** [Advanced Oracle Fleet Patching and Provisioning Configurations](advanced-oracle-fpp-configurations.md)
