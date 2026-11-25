## Updating Oracle Exadata Storage Server

Update Oracle Exadata storage servers to a higher Oracle Exadata software version.

1.  Create an Oracle Exadata storage server image.
    The following command creates an Oracle Exadata storage server image. In the example, `image` specifies the name of the storage server image that you want to add, `imagetype` specifies `EXAPATCHSOFTWARE` for Oracle Exadata software, `version` specifies the version of the Oracle Exadata software, and `path` specifies the absolute path location of the storage server image that you want to import.

        rhpctl import image -image image_name -imagetype EXAPATCHSOFTWARE
        -version software_version -path absolute_path

    When you import a storage server image with this command, the `version` parameter must be the version of the storage server software required by the `patchmgr` on the node. The `path` parameter should contain storage server update zip files.
2.  Deploy the Oracle Exadata storage server image to the client cluster.
    The following command deploys an Oracle Exadata storage server image to a client cluster. In the example, `image` specifies the name of the Oracle Exadata storage server image that you want to deploy, `client` specifies the name of the cluster to which you want to deploy the image, and `path` specifies the absolute path location for deploying the Oracle Exadata storage server image on the `rhpclient`-less target or client side.

        rhpctl deploy image -image image_name
        -client client_cluster_name -path image_file_path
3.  Evaluate the current configuration and perform pre-upgrade checks.
    The following command evaluates the current configuration and performs pre-upgrade checks. In the example, `cells` specifies the list of storage servers, `image` specifies the name of the Oracle Exadata storage server image that you want to use for updating, `client` specifies the name of the cluster in which you want to update the storage server, and `batches` specifies a comma-delimited list of batches of nodes where each batch is a comma-delimited list of node names enclosed in parentheses and node names are enclosed in double quotation marks (`""`) in the format: `"(nA,nB,...),(...,nY,nZ)"`.

        rhpctl update exadata -cells comma_separated_list_of_cells -image image_name -client client_cluster_name
         [-patchmgrargs "-patch_manager_arguments"] -eval
4.  Update Oracle Exadata storage server with the new image.
        rhpctl update exadata -cells comma_separated_list_of_cells -image image_name -client client_cluster_name
         [-patchmgrargs "-patch_manager_arguments"]

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
