This guide provides platform-specific information about administering and configuring Oracle Database 19c on the following platforms:

- Oracle Solaris

- Linux

- IBM AIX on POWER Systems (64-Bit)

- HP-UX Itanium

This guide supplements the [Oracle Database Administrator's Guide](../admin/index.md).

### Audience

This guide is intended for anyone responsible for administering and configuring Oracle Database 19c. If you are configuring Oracle RAC, then refer to [Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md).

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Diversity and Inclusion

Oracle is fully committed to diversity and inclusion. Oracle respects and values having a diverse workforce that increases thought leadership and innovation. As part of our initiative to build a more inclusive culture that positively impacts our employees, customers, and partners, we are working to remove insensitive terms from our products and documentation. We are also mindful of the necessity to maintain compatibility with our customers' existing technologies and the need to ensure continuity of service as Oracle's offerings and industry standards evolve. Because of these technical constraints, our effort to remove insensitive terms is ongoing and will take time and external cooperation.

### Set Up Java Access Bridge to Implement Java Accessibility

Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.

Java Access Bridge is a technology that enables Java applications and applets that implement the Java Accessibility API to be visible to assistive technologies on Microsoft Windows systems.

Refer to Java Platform, Standard Edition Accessibility Guide for information about the minimum supported versions of assistive technologies required to use Java Access Bridge. Also refer to this guide to obtain installation and testing instructions, and instructions for how to use Java Access Bridge.

**Related Topics**

- [Java Platform, Standard Edition Java Accessibility Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/unxar&id=JSACC-GUID-7890D37B-16F2-48EC-B45F-2A6CF0613EE5)

### Related Documentation

For important information, refer to your platform-specific Release Notes, Installation Guides, and Examples Installation Guide in the [Oracle Database Documentation Library](../books.md).

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

### Command Syntax

UNIX command syntax appears in `monospace` font. The dollar character (\$), number sign (#), or percent character (%) are UNIX command prompts. Do not enter them as part of the command. The following command syntax conventions are used in this guide:

| Convention       | Description                                                                                                                                                                                                                                                                                                 |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| backslash \\     | A backslash is the UNIX command continuation character. It is used in command examples that are too long to fit on a single line. Enter the command as displayed (with a backslash) or enter it on a single line without a backslash:<br>`dd if=/dev/rdsk/c0t1d0s6 of=/dev/rst0 bs=10b \ `<br>`count=10000` |
| braces { }       | Braces indicate required items:<br>`.DEFINE {macro1}`                                                                                                                                                                                                                                                       |
| brackets \[ \]   | Brackets indicate optional items:<br>`cvtcrt termname [outfile]`                                                                                                                                                                                                                                            |
| ellipses ...     | Ellipses indicate an arbitrary number of similar items:<br>`CHKVAL fieldname value1 value2 ... valueN`                                                                                                                                                                                                      |
| italic           | Italic type indicates a variable. Substitute a value for the variable:<br>`library_name`                                                                                                                                                                                                                    |
| vertical line \| | A vertical line indicates a choice within braces or brackets:<br>`FILE filesize [K|M]`                                                                                                                                                                                                                      |

### Terminology

The names of some UNIX operating systems have been shortened in this guide. These are:

| Operating System                                                          | Abbreviated Name                                                                                                                       |
|:--------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| • Oracle Solaris on SPARC (64-Bit)<br>• Oracle Solaris on x86-64 (64–Bit) | Oracle Solaris<br>Note: Where the information for Oracle Solaris is different on a particular architecture, this is noted in the text. |
| • Linux x86-64                                                            | Linux<br>Note: Where the information for Linux is different on a particular architecture, this is noted in the text.                   |

### Accessing Documentation

The documentation for this release includes platform-specific documentation and generic product documentation. Platform-specific documentation includes information about installing, configuring, and using Oracle products on a particular platform. The documentation is available in Adobe portable document format (PDF) and HTML format.

All Oracle documentation is available at the following URL:

[http://docs.oracle.com/en/](http://www.oracle.com/technetwork/indexes/documentation/index.html)

**Note:**

Platform-specific documentation is current at the time of release. For the latest information, Oracle recommends you to go to Oracle Technology Network website.
