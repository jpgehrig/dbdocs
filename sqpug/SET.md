## 12.40 SET

Sets a system variable to alter the SQL\*Plus environment settings for your current session, for example, to:

- customize HTML formatting

- enable or disable the printing of column headings

- set the number of lines per page

- set the display width for data

### Syntax

    SET system_variable value

where system_variable and value represent one of the clauses shown in the [SET System Variable Summary](SET-system-variable-summary.md) table following.

### Usage

SQL\*Plus maintains system variables (also called SET command variables) to enable you to set up a particular environment for a SQL\*Plus session. You can change these system variables with the SET command and list them with the SHOW command. The default value for each system variable is underlined in the following sections.

SET ROLE and SET TRANSACTION are SQL commands (see [SQL Statements: MERGE to UPDATE](../sqlrf/SQL-Statements-MERGE-to-UPDATE.md) for more information). When not followed by the keywords TRANSACTION or ROLE, SET is assumed to be a SQL\*Plus command.
