## Downgrading Oracle Grid Infrastructure Using Online Abort Upgrade

If upgrade of Oracle Grid Infrastructure fails before setting the active version of Oracle Clusterware, then follow these steps to downgrade Oracle Grid Infrastructure to the earlier release.

Run this procedure to downgrade Oracle Clusterware only when the upgrade fails before root script runs the `crsctl set crs activeversion` command on the last node. Use this procedure for downgrading Oracle Grid Infrastructure if there is a need to avoid downtime of the whole cluster. This procedure downgrades the cluster to the previous release. Because Oracle ASM and database operations are limited in this state, it is required to downgrade the cluster as soon as possible. Complete the downgrade of Oracle Grid Infrastructure as per the procedure documented in Downgrading Oracle Grid Infrastructure after Upgrade Fails.

1.  Shut down the Oracle Grid Infrastructure stack on the node that you are downgrading.
        crsctl stop crs
2.  If you are upgrading from 11.2.0.4, then apply the latest available patches on all nodes in the cluster. If the pre-upgrade version is 12.1.0.2 or later, then patch is not required.
    1.  On all other nodes except the first node, where the earlier release Grid Infrastructure stack is running, apply the latest patch using the `opatchauto` procedure.
    2.  On the first node where the earlier release Grid Infrastructure stack is stopped, apply the latest patch using the `opatch apply` procedure.
        For the list of latest available patches, see My Oracle Support at the following link:

        [https://support.oracle.com/](http://support.oracle.com/)

        1.  Unlock the Grid Infrastructure home from the earlier release:

                rootcrs.pl -unlock -crshome pre-upgrade-grid-home

            pre-upgrade-grid-home is the previous release Grid home.

        2.  Apply the patch:

                opatch apply -local -oh pre-upgrade-grid-home

        3.  Relock the Grid home from the earlier release:

                rootcrs.pl -lock
    3.  From any other node where the Grid Infrastructure stack from the earlier release is running, unset the Oracle ASM rolling migration mode as explained in step 2.
3.  Run the following command on all cluster nodes on which Oracle Grid Infrastructure is running, but not on the node that you are downgrading.
        clscfg -nodedowngrade -h hostname

    hostname is the name of the node that you are downgrading.
4.  From the later release Grid home, run the following command on all cluster nodes, which are successfully upgraded, to downgrade Oracle Clusterware.
        rootcrs.sh -downgrade -online

    If `rootcrs.sh` is not present, then use `rootcrs.pl`.
5.  Start Oracle Grid Infrastructure stack on all the nodes from the earlier release Grid home.
        crsctl start crs

    **Note:**

    You can downgrade the successfully upgraded cluster nodes in any sequence.
6.  On the last node where the Grid Infrastructure stack from the earlier release is running, unset the Oracle ASM rolling migration mode as follows:
    1.  Log in as `grid` user, and run the following command as SYSASM user on the Oracle ASM instance:
            SQL> ALTER SYSTEM STOP ROLLING MIGRATION;

**Related Topics**

- [Downgrading Oracle Grid Infrastructure to 12c Release 2 (12.2) when Upgrade Fails](downgrading-oracle-grid-infrastructure-using-oui.md)

**Parent topic:** [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
