Review the following information if you are installing Oracle Grid Infrastructure on SPARC processor servers.

If you use Oracle Solaris Cluster 4.0 or later, then refer to the Oracle Solaris Cluster Documentation library before starting Oracle Grid Infrastructure installation and Oracle RAC installation. In particular, refer to [Oracle Solaris Cluster Data Service for Oracle Real Application Clusters Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwsol&id=CLRAC).

For use cases on installing Oracle Real Application Clusters (Oracle RAC) in a zone cluster, review the information in the appendix Deploying Oracle RAC on Oracle Solaris Cluster Zone Clusters in this guide.

Review the following additional information for UDLM and native cluster membership interface:

- With Oracle Solaris Cluster 3.3, Oracle recommends that you do not use UDLM. Instead, Oracle recommends that you use the native cluster membership interface functionality (native SKGXN), which is installed automatically with Oracle Solaris Cluster 3.3 if UDLM is not deployed. No additional packages are needed to use this interface.

- Oracle UDLM is not supported for Oracle RAC 12.1 release or later. If you are upgrading from a prior release with UDLM, you first need to migrate to Oracle Solaris Cluster native SKGXN and then upgrade. The steps to migrate to Oracle Solaris Cluster native SKGXN are documented at the following URL:

  <http://docs.oracle.com/cd/E18728_01/html/821-2852/gkcmt.html#scrolltoc>

- With Oracle Solaris Zones, it is possible for one physical server to host multiple Oracle RAC clusters, each in an isolated zone cluster. Those zone clusters must each be self-consistent in terms of the membership model being used. However, because each zone cluster is an isolated environment, you can use zone clusters to create a mix of ORCLudlm and native cluster membership interface Oracle RAC clusters on one physical system.

**Related Topics**

- [Deploying Oracle RAC on Oracle Solaris Cluster Zone Clusters](deploying-oracle-rac-on-oracle-solaris-cluster-zone-clusters.md)

**Parent topic:** [Configuring Oracle Solaris Operating Systems for Oracle Grid Infrastructure](configuring-operating-systems-for-oracle-grid-infrastructure-on-oracle-solaris.md)
