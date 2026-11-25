## Downgrading Oracle Exadata InfiniBand Switches

Downgrade successfully updated Oracle Exadata InfiniBand switches to the older InfiniBand switch firmware version as determined by the current Oracle Exadata release.

1.  Check the current version of the Oracle Exadata InfiniBand switch patch.
2.  Evaluate the current configuration and perform pre-downgrade checks for InfiniBand switches.
        rhpctl update exadata -ibswitches comma_separated_list_of_IB_nodes -image image_name
        -client client_cluster_name [-patchmgrargs "-patch_manager_arguments"] -downgrade -eval
3.  Downgrade the Oracle Exadata InfiniBand switch patch.
        rhpctl update exadata -ibswitches comma_separated_list_of_IB_nodes -image image_name
        -client client_cluster_name [-patchmgrargs "-patch_manager_arguments"] -downgrade
4.  Check the current version of the Oracle Exadata InfiniBand switch patch to make sure that the downgrade is successful.

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
