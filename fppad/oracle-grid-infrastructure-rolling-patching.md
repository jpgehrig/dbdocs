## Patching Oracle Grid Infrastructure Using the Rolling Method

The rolling method for patching Oracle Grid Infrastructure is the default method.

You use the `rhpctl move gihome` command (an atomic operation), which returns after the Oracle Grid Infrastructure stack on each node has been restarted on the new home. Nodes are restarted sequentially, so that only one node at a time will be offline, while all other nodes in the cluster remain online.

- Move the Oracle Grid Infrastructure home to a working copy of the same release level, as follows:
      $ rhpctl move gihome –sourcewc Grid_home_1 –destwc Grid_home_2

  The preceding command moves the running Oracle Grid Infrastructure home from the current managed home (the `sourcewc`) to the patched home (`destwc`) on the specific client cluster. The patched home must be provisioned on the client.
- If the move operation fails at some point before completing, then you can rerun the operation by running the command again and the operation will resume where it left off. This enables you to fix whatever problem caused the failure and resume processing from the point of failure. Or you can undo the partially completed operation and return the configuration to its initial state, as follows:
      $ rhpctl move gihome -destwc destination_workingcopy_name -revert | -forcecomplete [authentication_option]

  You cannot use the `-revert` parameter with an un-managed home.

**Notes:**

- You cannot move the Grid home to a home that Fleet Patching and Provisioning does not manage. Therefore, rollback (to the original home) applies only to moves between two working copies. This restriction does not apply when using the independent automaton since it operates on unmanaged homes only.

- You can delete the source working copy at any time after moving a Grid home. Once you delete the working copy, however, you cannot perform a rollback. Also, use the `rhpctl delete workingcopy` command (as opposed to `rm`, for example) to remove the source working copy to keep the Fleet Patching and Provisioning inventory correct.

- If you use the `-abort` parameter to terminate the patching operation, then Fleet Patching and Provisioning does not clean up or undo any of the patching steps. The cluster, databases, or both may be in an inconsistent state because all nodes are not patched.

- Use the `-forcecomplete` parameter to mark the move operation as complete after completing it manually.

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
