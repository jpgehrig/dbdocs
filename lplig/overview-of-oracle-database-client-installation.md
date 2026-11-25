This chapter describes the different installation types of Oracle Database Client and issues to consider before you install Oracle Database Client:

- Planning Your Installation

- Installation Considerations

- Oracle Database Client Installation Types

- Oracle Database Client and Oracle Database Interoperability

- Simplified Patching of Timestamp with Time Zone Data Type

### Planning Your Installation

The Oracle Database Client installation process consists of the following phases:

1.  Read the release notes: Read the [Oracle Database Client Release Notes for IBM: Linux on POWER Little Endian Systems](../lplrn/index.md) before you begin the installation.
2.  Review the licensing information: Although the installation media in your media pack contain many Oracle components, you are permitted to use only those components for which you have purchased licenses.
    Oracle Support Services does not provide support for components for which licenses have not been purchased.

    **See Also:**

    [Oracle Database Licensing Information](../dblic/Licensing-Information.md)
3.  Plan the installation: This chapter describes the Oracle products that you can install and issues that you must consider before starting the installation.
4.  Complete preinstallation tasks: [Oracle Database Client Preinstallation Tasks](oracle-database-client-preinstallation-tasks.md) describes preinstallation tasks that you must complete before installing the product.
5.  Install the software: [Installing and Removing Oracle Database Client](installing-and-removing-oracle-database-client.md) describes how to install Oracle Database Client.
6.  Complete postinstallation tasks: [Oracle Database Client Postinstallation Tasks](oracle-database-client-postinstallation-tasks.md) describes recommended and required postinstallation tasks.

### Installation Considerations

This section contains hardware and software certification information that you should consider before deciding to install this product.

The platform-specific hardware and software requirements included in this guide were current when this guide was published. However, because new platforms and operating system software versions might be certified after this guide is published, review the certification matrix on the My Oracle Support website for the most up-to-date list of certified hardware platforms and operating system versions. The My Oracle Support website is available at

[`https://support.oracle.com/`](https://support.oracle.com/)

You must register online before using My Oracle Support. After logging in, from the menu options, select the Certifications tab. On the Certifications page, use the Certification Search options to search by Product, Release, and Platform. You can also search using the Certification Quick Link options such as Product Delivery and Lifetime Support.

### Oracle Database Client Installation Types

The Instant Client Enables you to install only the shared libraries required by Oracle Call Interface (OCI), Oracle C++ Call Interface (OCCI), Pro\*C, or Java Database Connectivity (JDBC) OCI applications. This installation type requires much less disk space than the other Oracle Database Client installation types.

For more information about Instant Client, see [Oracle Call Interface Programmer's Guide](../lnoci/instant-client.md) or[ Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-OCI-features.md).

Included in the Instant Client installation is Instant Client Light. You may want to use this version of Instant Client if the applications generate error messages in American English only. Instant Client Light is beneficial to application that use one of the supported character sets and can accept error messages in American English. The following are the supported character sets:

- `US7ASCII`

- `WE8DEC`

- `WE8MSWIN1252`

- `WE8ISO8859P1`

- `WE8EBCDIC37C` for EBCDIC platforms only

- `WE8EBCDIC1047` for EBCDIC platforms only

- `UTF8`

- `AL32UTF8`

- `AL16UTF16`

  The advantage of using Instant Client Light is that it has a smaller footprint than the regular Instant Client. The shared libraries, which an application must load, are only 34 MB as opposed to the 110 MB that regular Instant Client uses. Therefore, the applications use less memory.

### Oracle Database Client and Oracle Database Interoperability

For information about interoperability between Oracle Database Client and Oracle Database releases, see Note 207303.1 on the My Oracle Support website at

[`https://support.oracle.com/`](https://support.oracle.com/)

### Simplified Patching of Timestamp with Time Zone Data Type

Starting with Oracle Database 11g Release 2 (11.2), the patching process of `TIMESTAMP WITH TIMEZONE` data type values is simplified.

[Changes in This Release for Oracle Database Globalization Support Guide](../nlspg/changes-in-this-release.md)

[Clients and Servers Operating with Different Versions of Time Zone Files](../nlspg/datetime-data-types-and-time-zone-support.md)
