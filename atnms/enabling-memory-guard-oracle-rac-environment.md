Memory Guard is automatically enabled when you install Oracle Grid Infrastructure for an Oracle Real Application Clusters (Oracle RAC) or an Oracle RAC One Node database.

Run the `srvctl` command to query the status of Memory Guard as follows:

    srvctl status qosmserver

Example 11-1 Verifying that Memory Guard is Running on a Node

The following example shows sample output of the status of Memory Guard on `qosmserver`.

    $ srvctl status qosmserver
    QoS Management Server is enabled.
    QoS Management Server is running on node nodeABC

**Parent topic:** [Resolving Memory Stress](purpose-memory-guard.md)
