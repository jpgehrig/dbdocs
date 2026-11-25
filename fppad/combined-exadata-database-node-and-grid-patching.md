## Combined Oracle Exadata Database Server and Grid Infrastructure Update

With combined Oracle Exadata database server and Oracle Grid Infrastructure update you can utilize the functionality of multiple independent capabilities.

Patching Grid Infrastructure and updating the Exadata database nodes both require a shutdown and startup of every database instance on that node. This can take considerable time, depending on the number of applications running and the time it takes to shutdown instances and start them up. Performing both of these patching actions independently doubles the downtime on production databases. Using the combined patching feature of Oracle FPP automates both of these patching actions into a single integrated patching process that requires only one sequence of shutdown and startup of database instances on each node. The combined patching on multiple nodes in batches further brings down the overall patching window.

Oracle FPP internally uses the `patchmgr` tool to patch Exadata database nodes. The combined patching method uses an integrated flow of the inherent Oracle FPP implementation for Oracle Grid Infrastructure patching and then invokes the `patchmgr` tool to patch each Exadata database node.

To complete combined Oracle Exadata database node and Oracle Grid Infrastructure patching, you must perform the operations discussed in the following:

- Creating the Oracle Exadata Image
- Deploying the Oracle Exadata Update Image
- Combined Oracle Grid Infrastructure Move and Database Node Update

**Note:**

Creating and deploying an Oracle Exadata image does not require any downtime and you can perform both these operations before patching Oracle Grid Infrastructure and Oracle Exadata database. You need to create an Oracle Exadata image on the Oracle FPP server only once in a patching cycle, however, you need to deploy Oracle Exadata image, and patch Oracle Grid Infrastructure and Oracle Exadata database node on each server.

### Creating the Oracle Exadata Image

Use the `rhpctl` `import` `image` command to create the Oracle Exadata update image by copying the entire software contents from the specified path to the Oracle Fleet Patching and Provisioning Server (FPPS).

Example 6-1 Creating an Oracle Exadata Update Image

The following command creates an Oracle Exadata image. In the example, `image` specifies the name of the Oracle Exadata image that you want to add, `path` specifies the absolute path location of the Oracle Exadata software home that you want to import, `imagetype` specifies `EXAPATCHSOFTWARE` for Oracle Exadata software, and `version` specifies the version of the Oracle Exadata software.

    $ rhpctl import image -image EXADATAIMAGEV1
       -path /tmp/ExadataPatchBundle -imagetype EXAPATCHSOFTWARE -version 19.2.2.0.0.190513.2

When you import an Oracle Exadata software home with this command, the `version` parameter must be the version of the Oracle Exadata software required by the `patchmgr` on the database node. The `path` parameter should contain Oracle Exadata update zip files.

**See Also:**

[rhpctl import image](image-commands.md) for the complete syntax of the `rhpctl` `import` `image` command

### Deploying the Oracle Exadata Update Image

Use the `rhpctl` `deploy` `image` command to propagate the Oracle Exadata update image to server.

Example 6-2 Deploying an Oracle Exadata image

The following command deploys an Oracle Exadata image to a client cluster. In the example, `image` specifies the name of the Oracle Exadata image that you want to deploy, `client` specifies the name of the cluster to which you want to deploy the image, and `path` specifies the absolute path location for deploying the Oracle Exadata software home on the `rhpclient`-less target or client side.

    $ rhpctl deploy image -image EXADATAIMAGEV1 -client CLUSTER1 -path /exadatasoftware

The `targetnode` parameter is required if the node hosting the home is not a Oracle Fleet Patching and Provisioning Client. If the `rhpclient`-less target or client option is not specified, then the Oracle Exadata image is deployed to the Oracle Fleet Patching and Provisioning Server.

**See Also:**

[rhpctl deploy image](image-commands.md) for the complete syntax of the `rhpctl` `deploy` `image` command

### Combined Oracle Grid Infrastructure Move and Database Node Update

Use the `rhpctl` `move` `gihome` command to move the Oracle Grid Infrastructure software stack from one home to another while updating the Oracle Exadata database node.

Example 6-3 Moving an Oracle Grid Infrastructure home and updating a database node

The following example performs a combined Oracle Grid Infrastructure move and database node update on client cluster. In the example, `sourcewc` specifies the name of the source working copy, `destwc` specifies the name of the destination working copy to which you want to move the Oracle Grid Infrastructure home, `image` specifies the name of the Oracle Exadata image, `batches` specifies a comma-delimited list of batches of nodes where each batch is a comma-delimited list of node names enclosed in parentheses and node names are enclosed in double quotation marks (`""`) in the format: `"(nA,nB,...),(...,nY,nZ)"`, `iso_repo` specifies the image in the ISO repository, and `pathmgrloc` specifies the patch manager location.

    $ rhpctl move gihome -sourcewc prodHomeV1 -destwc prodHomeV2 -image EXADATAIMAGEV1
        -batches “(rac07box1,rac07box2,rac07box3),(rac07box4)"
       -patchmgrargs “-ignore_alerts" -iso_repo p28802055_192000_Linux-x86-64.zip -client prodcluster
        -patchmgrloc /patchMgr/dbserver_patch_19.190306

With each invocation of the `rhpctl` `move` `gihome` command, FPP patches the database node first and then patches Oracle Grid Infrastructure. This is the processing order for each node in the specified batch.

If the first batch includes more than one database node, then FPP invokes `patchmgr` in parallel for all the nodes. As soon as a node completes the `patchmgr` operation, including the post `patchmgr` operations, FPP starts the Oracle Grid Infrastructure patching on that node. When the Oracle Grid Infrastructure patching completes on this node, FPP then begins patching with Oracle Grid Infrastructure patching on the other nodes when the database node patching completes on those nodes.

If rebooting a node is delayed because of a `patchmgr` failure or a `patchmgr` operation timeout, the `rhpctl` `move` `gihome` command can be resumed after the node is back up.

**See Also:**

[rhpctl move gihome](gihome-commands.md) for the complete syntax of the `rhpctl` `move` `gihome` command

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
