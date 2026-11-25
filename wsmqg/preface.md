Oracle Database Gateway for WebSphere MQ provides access to WebSphere MQ services. This gateway requires a system that is capable of running 64‐bit applications.

### Intended Audience

This guide is intended for anyone responsible for installing, configuring, or administering the Oracle Database Gateway for WebSphere MQ. It is also for developers writing applications that access message queuing systems, particularly those developers who need to access queues owned by both WebSphere MQ and other non-Oracle message queuing systems as well as queues owned by Oracle Advanced Queuing (AQ).

Read this guide if you are responsible for tasks such as:

- Administering the gateway

- Setting up gateway security

- Using the gateway

- Diagnosing gateway errors

Before using this guide, you must understand the fundamentals of your operating system, the Oracle Database Gateways, PL/SQL, the Oracle database, and WebSphere MQ software before using this guide to install, configure, or administer the gateway.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Product Name

The complete name for this product is Oracle Database Gateway for WebSphere MQ, also called DG4MQ.

### Typographic Conventions

The following typographic conventions are used in this guide:

| Convention        | Description                                                                                                                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `monospace`       | Monospace type indicates commands, directory names, user names, path names, and file names.                                                                                              |
| italics           | Italic type indicates variables, including variable portions of file names. It is also used for emphasis and for book titles.                                                            |
| UPPERCASE         | Uppercase letters indicate Structured Query Language (SQL) reserved words, initialization parameters, and environment variables.                                                         |
| Bold              | Bold type indicates screen names and fields.                                                                                                                                             |
| SQL\*Plus prompts | The SQL\*Plus prompt, SQL\>, appears in SQL statement and SQL\*Plus command examples. Enter your response at the prompt. Do not enter the text of the prompt, "SQL\>", in your response. |

### Command Syntax

Command syntax appears in `monospace` font. The dollar character (\$), number sign (#), or percent character (%) are UNIX command prompts. Do not enter them as part of the command. The following command syntax conventions are used in this guide:

| Convention       | Description                                                                                                                                                                                                                                                                                                 |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| backslash \\     | A backslash is the UNIX command continuation character. It is used in command examples that are too long to fit on a single line. Enter the command as displayed (with a backslash) or enter it on a single line without a backslash:<br>`dd if=/dev/rdsk/c0t1d0s6 of=/dev/rst0 bs=10b \ `<br>`count=10000` |
| braces { }       | Braces indicate required items:<br>`.DEFINE {macro1}`                                                                                                                                                                                                                                                       |
| brackets \[ \]   | Brackets indicate optional items:<br>`cvtcrt termname [outfile]`                                                                                                                                                                                                                                            |
| ellipses ...     | Ellipses indicate an arbitrary number of similar items:<br>`CHKVAL fieldname value1 value2 ... valueN`                                                                                                                                                                                                      |
| italics          | Italic type indicates a variable. Substitute a value for the variable:<br>`library_name`                                                                                                                                                                                                                    |
| vertical line \| | A vertical line indicates a choice within braces or brackets:<br>`FILE filesize [K|M]`                                                                                                                                                                                                                      |

### Related Publications

See the [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md) for information common to all Oracle Database Gateways, including important information about functions, parameters, and error messages.

### Related Documents

The guide includes references to the following documents:

[Oracle Call Interface Programmer's Guide](../lnoci/index.md)

[Oracle Database Administrator's Guide](../admin/index.md)

[Oracle Database Error Messages](../errmg/index.md)

[Oracle Database Reference](../refrn/index.md)

[Oracle Database Utilities](../sutil/index.md)

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md)

[Oracle Database Net Services Administrator's Guide](../netag/index.md)

[Oracle Database Net Services Reference](../netrf/index.md)

[Oracle Database Security Guide](../dbseg/index.md)

[Oracle Database SQL Language Quick Reference](../sqlqr/index.md)

[Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md)

[Oracle Database PL/SQL Language Reference](../lnpls/index.md)

[Oracle Database Installation Guide](../install-and-upgrade.md)
