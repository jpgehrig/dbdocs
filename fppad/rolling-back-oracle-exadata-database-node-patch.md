## Rolling Back Oracle Exadata Database Node Patch

Rollback Oracle Exadata database servers to their previous Oracle Exadata software version.

1.  Check the current version of the Oracle Exadata database node patch.
2.  Roll back the Oracle Exadata database node patch.
        rhpctl update exadata -dbnodes comma_separates_list_of_nodes -image image_name
        -client client_cluster_name -patchmgrloc patch_mgr_loc -rollback
3.  Check the current version of the Oracle Exadata database node patch to make sure that the rollback is successful.

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
