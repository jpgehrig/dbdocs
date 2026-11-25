Oracle Real Application Clusters Administration and Deployment Guide describes the Oracle Real Application Clusters (Oracle RAC) architecture.

This publication provides an overview of the product, including Oracle Real Application Clusters One Node (Oracle RAC One Node). This publication also describes administrative and deployment topics for Oracle RAC.

Information in this manual applies to Oracle RAC as it runs on all platforms, unless otherwise noted. In addition, the content of this manual supplements administrative and deployment topics for noncluster Oracle Database that appear in other Oracle documentation. Where necessary, this publication refers to platform-specific documentation.

### Audience

The Oracle Real Application Clusters Administration and Deployment Guide is intended for database administrators, network administrators, and system administrators who perform the following tasks:

- Install and configure an Oracle RAC database

- Administer and manage Oracle RAC databases

- Manage and troubleshoot clusters and networks that use Oracle RAC

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

This book, the Oracle Real Application Clusters Administration and Deployment Guide, provides administration and application deployment information that is specific to Oracle RAC. The discussions herein assume a knowledge of Oracle Clusterware.

For more information, see the Oracle resources listed in this section.

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/index.md)

  This is an essential companion book that describes Oracle Clusterware components such as the voting disks and the Oracle Cluster Registry (OCR).

- Platform-specific Oracle Clusterware and Oracle RAC installation guides

  Each platform-specific Oracle Database installation media contains a copy of an Oracle Clusterware and Oracle RAC platform-specific installation and configuration guide in HTML and PDF formats. These installation books contain the preinstallation, installation, and postinstallation information for the various UNIX, Linux, and Windows platforms on which Oracle Clusterware and Oracle RAC operate.

- [Oracle Database 2 Day DBA](../admqs/index.md)

- [Oracle Database Administrator's Guide ](../admin/index.md)

- [Oracle Database Net Services Administrator's Guide](../netag/index.md)

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/index.md)

- [Oracle Database Administrator's Reference for Linux and UNIX-Based Operating Systems](../unxar/index.md)

- Oracle Database 11g Administrator's Reference Release 1 (11.1) for UNIX Systems: AIX Systems, HP-UX, Linux, and the Solaris Operating System (SPARC)

**Note:**

Additional information for this release may be available in the Oracle Database 12c README or Release Notes. If these documents are available for this release, then they are on your Oracle product installation media.

Database error messages descriptions are available online or by way of a Tahiti documentation search.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
