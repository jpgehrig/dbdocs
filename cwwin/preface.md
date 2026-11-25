## Preface

This guide explains how to configure a server in preparation for installing and configuring an Oracle Grid Infrastructure installation (Oracle Clusterware and Oracle Automatic Storage Management).

This guide also explains how to configure a server and storage in preparation for an Oracle Real Application Clusters (Oracle RAC) installation.

- Audience
- Documentation Accessibility
- Diversity and Inclusion
- Set Up Java Access Bridge to Implement Java Accessibility
  Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.
- Related Documentation
- Conventions

### Audience

Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows provides configuration information for network and system administrators, and database installation information for database administrators (DBAs) who install and configure Oracle Clusterware and Oracle Automatic Storage Management in an Oracle Grid Infrastructure for a cluster installation.

For customers with specialized system roles who intend to install Oracle Real Application Clusters (Oracle RAC), this book is intended to be used by system administrators, network administrators, or storage administrators to configure a system in preparation for an Oracle Grid Infrastructure for a cluster installation, and complete all configuration tasks that require Administrator user privileges. When the Oracle Grid Infrastructure installation and configuration is successfully completed, a system administrator should only provide configuration information and grant access to the database administrator to run scripts that require Administrator user privileges during an Oracle RAC installation.

This guide assumes that you are familiar with Oracle Database concepts. For additional information, refer to books in the Related Documents list.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=docacc).

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=info) or visit [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=trs) if you are hearing impaired.

**Parent topic:** Preface

### Diversity and Inclusion

Oracle is fully committed to diversity and inclusion. Oracle respects and values having a diverse workforce that increases thought leadership and innovation. As part of our initiative to build a more inclusive culture that positively impacts our employees, customers, and partners, we are working to remove insensitive terms from our products and documentation. We are also mindful of the necessity to maintain compatibility with our customers' existing technologies and the need to ensure continuity of service as Oracle's offerings and industry standards evolve. Because of these technical constraints, our effort to remove insensitive terms is ongoing and will take time and external cooperation.

**Parent topic:** Preface

### Set Up Java Access Bridge to Implement Java Accessibility

Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.

Java Access Bridge is a technology that enables Java applications and applets that implement the Java Accessibility API to be visible to assistive technologies on Microsoft Windows systems.

Refer to Java Platform, Standard Edition Accessibility Guide for information about the minimum supported versions of assistive technologies required to use Java Access Bridge. Also refer to this guide to obtain installation and testing instructions, and instructions for how to use Java Access Bridge.

**Related Topics**

- [Java Platform, Standard Edition Java Accessibility Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwwin&id=JSACC-GUID-7890D37B-16F2-48EC-B45F-2A6CF0613EE5)

**Parent topic:** Preface

### Related Documentation

#### Oracle Clusterware and Oracle Real Application Clusters Documentation

For more information, refer to the following Oracle resources.

This installation guide reviews steps required to complete an Oracle Clusterware and Oracle Automatic Storage Management installation, and to perform preinstallation steps for Oracle RAC.

Installing Oracle RAC or Oracle RAC One Node is a multi-step process. Perform the following steps by reviewing the appropriate documentation:

| Installation Task                                                                  | Documentation to Use                                                                                        |
|:-----------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| Preinstallation setup for Oracle Grid Infrastructure and Oracle RAC                | Oracle Grid Infrastructure Installation Guide for Microsoft Windows x64 (64-Bit) (this guide)               |
| Install Oracle Grid Infrastructure and configure Oracle Clusterware and Oracle ASM | Oracle Grid Infrastructure Installation Guide for Microsoft Windows x64 (64-Bit) (this guide)               |
| Install Oracle Database software and configure Oracle RAC                          | [Oracle Real Application Clusters Installation Guide for Microsoft Windows x64 (64-Bit)](../riwin/index.md) |

You can install the Oracle Database software for standalone databases or Oracle RAC databases on servers that run Oracle Grid Infrastructure. You cannot install Oracle Restart on servers that run Oracle Grid Infrastructure. To install an Oracle Restart deployment of Oracle Grid Infrastructure, see [Oracle Database Installation Guide](../install-and-upgrade.md).

#### Installation Guides for Microsoft Windows

- [Oracle Database Installation Guide for Microsoft Windows x64 (64-Bit)](../ntdbi/index.md)

- [Oracle Real Application Clusters Installation Guide for Microsoft Windows x64 (64-Bit)](../riwin/index.md)

- [Oracle Database Client Installation Guide for Microsoft Windows](../ntcli/index.md)

#### Operating System-Specific Administrative Guides

- [Oracle Database Platform Guide for Microsoft Windows](../ntqrf/index.md)

#### Oracle Clusterware and Oracle Automatic Storage Management Administrative Guides

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/index.md)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/index.md)

#### Oracle Real Application Clusters Administrative Guides

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md)

#### Generic Documentation

- [Oracle Database 2 Day DBA](../admqs/index.md)

- [Oracle Database Administrator’s Guide](../admin/index.md)

- [Oracle Database Concepts](../cncpt/index.md)

- [Oracle Database New Features Guide](../newft/index.md)

- [Oracle Database Reference](../refrn/index.md)

- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/index.md)

#### Error Messages

Oracle error message documentation is available only in HTML. You can browse the error messages by range in  [Oracle Database Error Messages Reference](../errmg/index.md). When you find a range, use your browser's “find in page” feature to locate a specific message. When connected to the Internet, you can search for a specific error message using the error message search feature of the Oracle online documentation.

#### Other Documentation

For any other documentation, you can access the documentation library at Oracle Help Center:

<http://docs.oracle.com>

**Parent topic:** Preface

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

**Parent topic:** Preface
