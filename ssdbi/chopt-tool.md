Use the `chopt` tool after installation to add or remove Oracle Database options.

### Purpose

The `chopt` tool is a command-line utility that enables and disables database options.

**Note:**

If you install or clone an Oracle Database image, then all Oracle Database options are enabled by default.

### Prerequisites

You must complete installation before you can use the `chopt` tool.

### File Path

The tool is located in the `ORACLE_HOME``/bin` directory

### Syntax

`chopt` \[`enable` \| `disable`\] db_option

### Options

| Command Option | Description                     |
|:---------------|:--------------------------------|
| `olap`         | Oracle OLAP                     |
| `partitioning` | Oracle Partitioning             |
| `rat`          | Oracle Real Application Testing |

**Note:**

- When you enable or disable OLAP, you must run the `SYS.XOQ_VALIDATE` and `SYS.APS_VALIDATE` procedures to update the database registry. When you disable OLAP, its status in the database registry should be OPTION OFF and when you enable OLAP, its status in the database registry should be VALID.
- The Oracle Advanced Analytics (OAA) feature is enabled by default for Oracle Database. You cannot disable it using the `chopt` tool.

### Examples

To use the `chopt` tool to modify your Oracle Database, you must shut down the database before you run the `chopt` tool, and then start up the database after you add or remove database options.

Example 12-1 Enabling Oracle Real Application Testing Using chopt

The following example shows how to use the `chopt` tool to enable the Oracle Real Application Testing option in an Oracle Database called Sales:

    cd $ORACLE_HOME/bin
    srvctl stop database -d Sales
    chopt enable rat
    srvctl start database -d Sales

**Parent topic:** [Enabling and Disabling Oracle Database Options After Installation](enabling-and-disabling-oracle-database-options-after-installation.md)
