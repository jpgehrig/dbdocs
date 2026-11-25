Complete the following procedure to deploy HACMP and MDNDHP for Oracle Clusterware.

Ensure that your versions of HACMP and AIX meet the system requirements as listed in this guide.

1.  Start HACMP.
2.  Enter the following command to ensure that the HACMP clcomdES daemon is running:
        # lssrc -s clcomdES

    If the daemon is not running, then start it using the following command:

        # startsrc –s clcomdES
3.  Create HACMP cluster and add the Oracle Clusterware nodes. For example:
        # smitty cm_add_change_show_an_hacmp_cluster.dialog
        * Cluster Name [mycluster]
4.  Create an HACMP cluster node for each Oracle Clusterware node. For example:
        # smitty cm_add_a_node_to_the_hacmp_cluster_dialog
        * Node Name [mycluster_node1]
        Communication Path to Node []
5.  Create HACMP Ethernet heartbeat networks. The HACMP configuration requires network definitions. Select `NO` for the IP address takeover for these networks, since they are used by Oracle Clusterware.
    Create at least two network definitions: one for the Oracle public interface and a second one for the Oracle private (cluster interconnect) network. Additional Ethernet heartbeat networks can be added if desired. For example:

        # smitty cm_add_a_network_to_the_hacmp_cluster_select
        - select ether network
        * Network Name [my_network_name]
        * Network Type ether
        * Netmask [my.network.netmask.here]
        * Enable IP Address Takeover via IP Aliases [No]
        IP Address Offset for Heart beating over IP Aliases []
6.  For each of the networks added in the previous step, define all of the IP names for each Oracle Clusterware node associated with that network, including the public, private and VIP names for each Oracle Clusterware node. For example:
        # smitty cm_add_communication_interfaces_devices.select
        - select: Add Pre-defined Communication Interfaces and Devices / Communication Interfaces / desired network
        * IP Label/Address [node_ip_address]
        * Network Type ether
        * Network Name some_network_name
        * Node Name [my_node_name]
        Network Interface []
7.  Create an HACMP resource group for the enhanced concurrent volume group resource with the following options:
        # smitty config_resource_group.dialog.custom
        * Resource Group Name [my_resource_group_name]
        * Participating Nodes (Default Node Priority) [mynode1,mynode2,mynode3]
        Startup Policy Online On All Available Nodes
        Fallover Policy Bring Offline (On Error Node Only)
        Fallback Policy Never Fallback
8.  Create an AIX enhanced concurrent volume group (Big VG, or Scalable VG) using either the command `smitty mkvg`, or using command lines. The VG must contain at least one hard disk for each voting disk. You must configure at least three voting disks.
    In the following example, where you see default, accept the default response:

        # smitty _mksvg
        VOLUME GROUP name [my_vg_name] PP SIZE in MB
        * PHYSICAL VOLUME names [mydisk1,mydisk2,mydisk3]
        Force the creation of a volume group? no
        Activate volume group AUTOMATICALLY no at system restart?
        Volume Group MAJOR NUMBER []
        Create VG Concurrent Capable? enhanced concurrent
        Max PPs per VG in kilobytes default
        Max Logical Volumes default
9.  Under "Change/Show Resources for a Resource Group (standard)", add the concurrent volume group to the resource group added in the preceding steps.
    For example:

        # smitty cm_change_show_resources_std_resource_group_menu_dmn.select
        - select_resource_group_from_step_6
        Resource Group Name shared_storage
        Participating Nodes (Default Node Priority) mynode1,mynode2,mynode3
        Startup Policy Online On All Available Nodes
        Fallover Policy Bring Offline (On Error Node Only)
        Fallback Policy Never Fallback
        Concurrent Volume Groups [enter_VG_from_step_7]
        Use forced varyon of volume groups, if necessary false
        Application Servers []
10. Using the following command, ensure that one MNDHB network is defined for each Oracle Clusterware voting disk. Each MNDHB and voting disk pair must be collocated on a single hard disk, separate from the other pairs. The MNDHB network and Voting Disks exist on shared logical volumes in an enhanced concurrent logical volume managed by HACMP as an enhanced concurrent resource. For each of the hard disks in the VG created in step 8 on which you want to place a voting disk logical volume (LV), create a MNDHB LV.
        # smitty cl_add_mndhb_lv
        - select_resource_group_defined_in_step_6
        * Physical Volume name enter F4, then select a hard disk
        Logical Volume Name []
        Logical Volume Label []
        Volume Group name ccvg
        Resource Group Name shared_storage
        Network Name [n]

    When you define the LVs for the Oracle Clusterware voting disks, they should be defined on the same disks: one for each disk, as used in this step for the MNDHB LVs.
11. Configure MNDHB so that the node is halted if access is lost to a quorum of the MNDHB networks in the enhanced concurrent volume group. For example:
        # smitty cl_set_mndhb_response
        - select_the_VG_created_in_step_7
        On loss of access Halt the node
        Optional notification method []
        Volume Group ccvg
12. Verify and Synchronize HACMP configuration. For example:
        # smitty cm_initialization_and_standard_config_menu_dmn  -
        select Verify and Synchronize HACMP Configuration

    Enter Yes if prompted: `"Would you like to import shared VG: ccvg, in resource group my_resource_group onto node: mynode to node: racha702 [Yes / No]:"`
13. Add the HACMP cluster node IP names to the file `/usr/es/sbin/cluster/etc/rhosts`.

**Parent topic:** [Configuring HACMP Multinode Disk Heartbeat (MNDHB)](configuring-multi-node-disk-heartbeat.md)
