This guide provides instructions about installing and configuring Oracle Database Client for Linux on POWER Systems. This guide also describes about installing and configuring database using response files, globalization support, ports, and troubleshooting.

The preface contains the following topics:

- Audience

- Documentation Accessibility

- Command Syntax

- Related Documentation

- Typographic Conventions

### Audience

This guide is intended for anyone responsible for installing Oracle Database Client. Additional platform-specific installation guides for Oracle Database, Oracle Real Application Clusters, Oracle Clusterware, Oracle Database Examples, and Oracle Enterprise Manager Grid Control are available at

[`http://docs.oracle.com/en/database/database.html`](http://docs.oracle.com/en/database/database.html)

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Set Up Java Access Bridge to Implement Java Accessibility

Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.

Java Access Bridge is a technology that enables Java applications and applets that implement the Java Accessibility API to be visible to assistive technologies on Microsoft Windows systems.

Refer to Java Platform, Standard Edition Accessibility Guide for information about the minimum supported versions of assistive technologies required to use Java Access Bridge. Also refer to this guide to obtain installation and testing instructions, and instructions for how to use Java Access Bridge.

**Related Topics**

- [Java Platform, Standard Edition Java Accessibility Guide](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lplig&id=JSACC-GUID-7890D37B-16F2-48EC-B45F-2A6CF0613EE5)

### Command Syntax

UNIX command syntax appears in `monospace` font. The dollar character (\$), number sign (#), or percent character (%) are UNIX command prompts. Do not enter them as part of the command. The following command syntax conventions are used in this guide:

| Convention       | Description                                                                                                                                                                                                                                                                                                 |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| backslash \\     | A backslash is the UNIX command continuation character. It is used in command examples that are too long to fit on a single line. Enter the command as displayed (with a backslash) or enter it on a single line without a backslash:<br>`dd if=/dev/rdsk/c0t1d0s6 of=/dev/rst0 bs=10b \ `<br>`count=10000` |
| braces { }       | Braces indicate required items:<br>`.DEFINE {macro1}`                                                                                                                                                                                                                                                       |
| brackets \[ \]   | Brackets indicate optional items:<br>`cvtcrt termname [outfile]`                                                                                                                                                                                                                                            |
| ellipses ...     | Ellipses indicate an arbitrary number of similar items:<br>`CHKVAL fieldname value1 value2 ... valueN`                                                                                                                                                                                                      |
| italics          | Italic type indicates a variable. Substitute a value for the variable:<br>`library_name`                                                                                                                                                                                                                    |
| vertical line \| | A vertical line indicates a choice within braces or brackets:<br>`FILE filesize [K|M]`                                                                                                                                                                                                                      |

### Related Documentation

The product-specific and platform-specific documentation for Oracle Database products are available in both, PDF and HTML formats. You can view and download the documentation at

[`http://docs.oracle.com/en/`](../../../../..)

See [Oracle Database Client Release Notes for IBM: Linux on POWER Little Endian Systems](../lplrn/index.md) for important information that was not available when this book was released.

### Typographic Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
