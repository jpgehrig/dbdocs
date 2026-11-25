## Patching Oracle Grid Infrastructure Using Oracle FPP Local Mode Configuration

When you install Oracle Grid Infrastructure or when you upgrade an older version to the current version, the Oracle FPP Server is configured automatically as Oracle FPP Local Mode.

**Note:**

You must enable and start the Fleet Patching and Provisioning Server using the following commands before you can use the Oracle FPP Local Mode patching operation:

    $ srvctl enable rhpserver
    $ srvctl start rhpserver

To switch Oracle FPP from Oracle FPP Local Mode to the regular, central mode (to manage remote targets), you must delete the current Oracle FPP Local Mode configuration, as follows:

    $ srvctl stop rhpserver
    $ srvctl remove rhpserver

Proceed with the steps described in "Creating a Fleet Patching and Provisioning Server" to create the central-mode Oracle Fleet Patching and Provisioning Server.

- Oracle FPP Local Mode for patching Oracle Grid Infrastructure performs all of the steps necessary to switch from one home to another. Because Oracle FPP Local Mode is not aware of gold images, moving the database requires two home paths, as follows:
      $ rhpctl move gihome –sourcehome Oracle_home_path -destinationhome Oracle_home_path

Use the following `rhpctl move gihome` command parameters for the patching operation:

- `-node`: If the home you are moving is an Oracle Grid Infrastructure home installed on more than one node, then the default operation is a rolling update on all nodes. To apply a patch to just one node, specify the name of that node with this parameter.

- `-nonrolling`: If the home you are moving is an Oracle Grid Infrastructure home installed on more than one node, then the default operation is a rolling update on all nodes. To patch all nodes in a nonrolling manner, use this parameter instead of the `-node` parameter.

- `-ignorewcpatches`: By default, Fleet Patching and Provisioning will not perform the move operation if the destination home is missing any patches present in the source home. You can override this functionality by using this parameter, for example, to move back to a previous source home if you must undo an update.

**Related Topics**

- [Creating a Fleet Patching and Provisioning Server](creating-oracle-fleet-patching-and-provisioning-server.md)

**Parent topic:** [Oracle Fleet Patching and Provisioning Local Mode](oracle-fpp-local-mode.md)
