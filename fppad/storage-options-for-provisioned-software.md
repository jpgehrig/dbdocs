## Storage Options for Provisioned Software

Choose one of two storage options where Fleet Patching and Provisioning stores working copies of gold images.

When you provision software using the `rhpctl add workingcopy` command, you can choose from two storage options where Fleet Patching and Provisioning places that software:

- In an Oracle ACFS shared file system managed by Fleet Patching and Provisioning (for database homes only)

- In a local file system not managed by Fleet Patching and Provisioning

Using the `rhpctl add workingcopy` command with the `–storagetype` and `–path` parameters, you can choose where you store provisioned working copies. The applicability of the parameters depends on whether the node (or nodes) to which you are provisioning the working copy is a Fleet Patching and Provisioning Server, Fleet Patching and Provisioning Client, or a non-Fleet Patching and Provisioning client. You can choose from the following values for the `–stroragetype` parameter:

- `RHP_MANAGED`: Choosing this value, which is available for Fleet Patching and Provisioning Servers and Fleet Patching and Provisioning Clients, stores working copies in an Oracle ACFS shared file system. The `–path` parameter is not used with this option because Fleet Patching and Provisioning manages the storage option.

  **Notes:**

  - You cannot store Oracle Grid Infrastructure homes in `RHP_MANAGED` storage.

  - Oracle recommends using the `LOCAL` storage type, which is available on Fleet Patching and Provisioning Servers, and on Clients configured with an Oracle ASM disk group.

  - If you provision working copies on a Fleet Patching and Provisioning Server, then you do not need to specify the `-storagetype` option because it will default to `RHP_MANAGED`.

  - If you choose to provision working copies on a Fleet Patching and Provisioning Client, and you do not specify the `-path` parameter, then the storage type defaults to `RHP_MANAGED` only if there is an Oracle ASM disk group on the client. Otherwise the command will fail. If you specify a location on the client for the `-path` parameter, then the storage type defaults to `LOCAL` with or without an Oracle ASM disk group.

- `LOCAL`: Choosing this value stores working copies in a local file system that is not managed by Fleet Patching and Provisioning. You must specify a path to the file system on the Fleet Patching and Provisioning Server, Fleet Patching and Provisioning Client, or non-Fleet Patching and Provisioning client, or to the Oracle ASM disk group on the Fleet Patching and Provisioning Client.

In cases where you specify the `–path` parameter, if the file system is shared among all of the nodes in the cluster, then the working copy gets created on this shared storage. If the file system is not shared, then the working copy gets created in the location of the given path on every node in the cluster.

**Note:**

The directory you specify in the `-path` parameter must be empty.

**Related Topics**

- [rhpctl add workingcopy](workingcopy-commands.md)

**Parent topic:** [Provisioning Copies of Gold Images](provisioning-gold-image-copies.md)
