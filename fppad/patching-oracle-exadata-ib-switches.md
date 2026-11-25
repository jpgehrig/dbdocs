## Updating Oracle Exadata InfiniBand Switches

Update Oracle Exadata InfiniBand switches to a higher InfiniBand switch firmware version.

1.  Evaluate the current configuration and perform pre-upgrade checks for InfiniBand switches.
    The following command evaluates the current configuration and performs pre-upgrade checks. In the example, `image` specifies the name of the Oracle Exadata InfiniBand switch image that you want to use for update, and `client` specifies the name of the cluster in which you want to update database nodes.

        rhpctl update exadata -ibswitches comma_separated_list_of_IB_nodes -image image_name
        -client client_cluster_name -eval
2.  Update Oracle Exadata InfiniBand switches with the new image.
        rhpctl update exadata -ibswitches comma_separated_list_of_IB_nodes -image image_name
        -client client_cluster_name

**Parent topic:** [Updating Oracle Exadata Infrastructure](patching-oracle-exadata.md)
