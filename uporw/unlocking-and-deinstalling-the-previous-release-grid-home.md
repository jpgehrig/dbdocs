After upgrading from previous releases, you can deinstall the previous release Grid home.

Perform the following steps:

1.  Navigate to the `bin` directory of the previous release Grid home.
        C:\> cd C:\app\grid\product\18.0.0\grid\bin
2.  Use the `deinstall` command to remove the previous release of Oracle Grid Infrastructure installation.
        C:\app\grid\product\18.0.0\grid\bin:\> deinstall

    **Note:**

    Ensure that the services and directories of the older grid home are deleted.
    **Caution:**

    You must use the `deinstall` command from the same release to remove Oracle software. Do not run the `deinstall` command from a later release to remove Oracle software from an earlier release. For example, do not run the `deinstall` command from the 19.0.0.0.0 Grid home to remove Oracle software from an existing 18.0.0.0.0 Grid home.

**Parent topic:** [Upgrading and Patching Oracle Restart](upgrading-and-patching-oracle-restart.md)
