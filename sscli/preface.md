This guide explains how to install and configure Oracle Database Client.

This guide also provides information about postinstallation tasks and how to remove the database client software.

- Audience
  This guide is intended for anyone responsible for installing Oracle Database Client 19c.
- Documentation Accessibility
- Diversity and Inclusion
- Set Up Java Access Bridge to Implement Java Accessibility
  Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.
- Command Syntax
  Refer to these command syntax conventions to understand command examples in this guide.
- Related Documentation
  The related documentation for Oracle Database products includes the following manuals:
- Conventions

### Audience

This guide is intended for anyone responsible for installing Oracle Database Client 19c.

Additional installation guides for Oracle Database, Oracle Real Application Clusters, Oracle Clusterware, Oracle Database Examples, and Oracle Enterprise Manager Cloud Control are available at the following URL:

[http://docs.oracle.com](http://docs.oracle.com/)

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface

### Diversity and Inclusion

Oracle is fully committed to diversity and inclusion. Oracle respects and values having a diverse workforce that increases thought leadership and innovation. As part of our initiative to build a more inclusive culture that positively impacts our employees, customers, and partners, we are working to remove insensitive terms from our products and documentation. We are also mindful of the necessity to maintain compatibility with our customers' existing technologies and the need to ensure continuity of service as Oracle's offerings and industry standards evolve. Because of these technical constraints, our effort to remove insensitive terms is ongoing and will take time and external cooperation.

**Parent topic:** Preface

### Set Up Java Access Bridge to Implement Java Accessibility

Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.

Java Access Bridge is a technology that enables Java applications and applets that implement the Java Accessibility API to be visible to assistive technologies on Microsoft Windows systems.

Refer to Java Platform, Standard Edition Accessibility Guide for information about the minimum supported versions of assistive technologies required to use Java Access Bridge. Also refer to this guide to obtain installation and testing instructions, and instructions for how to use Java Access Bridge.

**Related Topics**

- [Java Platform, Standard Edition Java Accessibility Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/sscli&id=JSACC-GUID-7890D37B-16F2-48EC-B45F-2A6CF0613EE5)

**Parent topic:** Preface

### Command Syntax

Refer to these command syntax conventions to understand command examples in this guide.

| Convention       | Description                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `$`              | Bourne or BASH shell prompt in a command example. Do not enter the prompt as part of the command.                                                                                                                                                                                                                |
| `%`              | C Shell prompt in a command example. Do not enter the prompt as part of the command.                                                                                                                                                                                                                             |
| `#`              | Superuser (root) prompt in a command example. Do not enter the prompt as part of the command.                                                                                                                                                                                                                    |
| `monospace`      | UNIX command syntax                                                                                                                                                                                                                                                                                              |
| backslash \\     | A backslash is the UNIX and Linux command continuation character. It is used in command examples that are too long to fit on a single line. Enter the command as displayed (with a backslash) or enter it on a single line without a backslash:<br>`dd if=/dev/rdsk/c0t1d0s6 of=/dev/rst0 bs=10b \  count=10000` |
| braces { }       | Braces indicate required items:<br>`.DEFINE {macro1}`                                                                                                                                                                                                                                                            |
| brackets \[ \]   | Brackets indicate optional items:<br>`cvtcrt termname [outfile]`                                                                                                                                                                                                                                                 |
| ellipses ...     | Ellipses indicate an arbitrary number of similar items:<br>`CHKVAL fieldname value1 value2 ... valueN`                                                                                                                                                                                                           |
| italic           | Italic type indicates a variable. Substitute a value for the variable:<br>`library_name `                                                                                                                                                                                                                        |
| vertical line \| | A vertical line indicates a choice within braces or brackets:<br>`FILE filesize [K|M]`                                                                                                                                                                                                                           |

**Parent topic:** Preface

### Related Documentation

The related documentation for Oracle Database products includes the following manuals:

[Oracle Database Concepts](../cncpt/index.md)

[Oracle Database New Features Guide](../newft/index.md)

[Oracle Database Licensing Information](../dblic/index.md)

[Oracle Database Release Notes](../rnrdm/index.md)

[Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md)

[Oracle Database Client Installation Guide for Oracle Solaris](index.md)

[Oracle Database Examples Installation Guide](../exmpl/index.md)

[Oracle Real Application Clusters Installation Guide for Linux and UNIX](../rilin/index.md)

[Oracle Database Administrator's Reference for Linux and UNIX-Based Operating Systems](../unxar/index.md)

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/index.md)

[Oracle Database Upgrade Guide](../upgrd/index.md)

[Oracle Database 2 Day DBA](../admqs/index.md)

[Oracle Application Express Installation Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/sscli&id=HTMIG)

**Parent topic:** Preface

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

**Parent topic:** Preface
