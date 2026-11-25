## Updating Environment Variables on Remote Nodes

Changes made to registry and environment variables are not immediately visible to user sessions on remote notes.

During the installation, the Windows registry and environment variables are modified on each node on which you installed Oracle RAC. The new registry entries and environment variable settings are visible on the node where the installation was performed (the local node). However, the new settings on the remote nodes are not immediately available to your user session. Attempting to run scripts or applications from the newly installed Oracle home can produce errors similar to the following:

- `ORACONFIG.exe - Unable to Locate Component`

- `OCI.dll not found`

To make the modified environment variables available on the remote nodes, you can do either of the following actions:

1.  Close your current session on the remote nodes (log off) and then log on to the remote nodes to create a new session.
2.  Make the environment variables available to the remote nodes:
    1.  From the Start menu, right-click My Computer, then select Properties
        Alternatively, you can enter `SYSDM.CPL` in the Run window.
    2.  Select the Advanced tab.
    3.  Click Environment Variables.
        The modified environment variables are now visible.
    4.  Click OK to close the System Properties window.

**Parent topic:** [Installing Oracle RAC and Oracle RAC One Node](installing-oracle-rac-and-oracle-rac-one-node.md)
