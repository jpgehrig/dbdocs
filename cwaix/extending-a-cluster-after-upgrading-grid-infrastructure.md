Review this information to convert to an Oracle Extended Cluster after upgrading Oracle Grid Infrastructure. Oracle Extended Cluster enables you to deploy Oracle RAC databases on a cluster, in which some of the nodes are located in different sites.

Ensure that you have upgraded to Oracle Grid Infrastructure 19c as described in this chapter.

1.  As `root` user, log in to the first node, and run the command:
        rootcrs.sh -converttoextended -first -sites list_of_sites -site node_site

    list_of_sites is the comma-separated list of sites in the extended cluster, and node_site is the node containing the site.

    For example:

        rootcrs.sh -converttoextended -first -sites newyork,newjersey,conn -site newyork
2.  As `root` user, on all other nodes, run the following command:
        rootcrs.sh -converttoextended -site node_site

    node_site is the node containing the site.

    For example:

        rootcrs.sh -converttoextended -site newjersey
3.  Delete the default site after the associated nodes and storage are migrated.
        crsctl delete cluster site site_name

    For example:

        [root@node4]#crsctl delete cluster site mycluster

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
