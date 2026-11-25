## Rolling Back Oracle Exadata Storage Server Patch

Rollback successfully updated Oracle Exadata storage servers to their previous Oracle Exadata software version.

1.  Check the current version of the Oracle Exadata storage server patch.
2.  Roll back the Oracle Exadata storage server patch.
        rhpctl update exadata -cells comma_separated_list_of_cells -image image_name -client client_cluster_name
         [-patchmgrargs "-patch_manager_arguments"] -rollback
3.  Check the current version of the Oracle Exadata storage server patch to make sure that the rollback is successful.

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
