This manual provides information about installing, administering, maintenance, and usage of Oracle Database and related products. It also provides information for BS2000 end users of Oracle products. Certain topics in this manual apply to both users and database administrators. This manual describes the following:

- How Oracle Database operates under BS2000
- How to install Oracle Database
- How to create or upgrade an Oracle Database
- How to administer an Oracle Database
- How to use Oracle Database utilities
- How to build and run Oracle Database applications

This section contains the following topics:

- Audience
- Documentation Accessibility
- Using Oracle Database Documentation
- Related Documents
- Conventions Used in this Manual

### Audience

This manual is intended for:

- Database Administrators (DBAs)

- Users of Oracle Database

- Oracle Database Support

The reader is assumed to have a fundamental knowledge of BS2000. No attempt is made to document features of BS2000, except as they affect or are affected by Oracle Database.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Using Oracle Database Documentation

Oracle Database products that run on BS2000 principally offer the same functionality as Oracle Database products on other operating systems. However, because of the diversity of operating systems, the use of applications may differ slightly between different operating systems. As a result of this, Oracle provides two types of documentation:

| Type            | Meaning/Usage                                                                                                                                                                                                                        |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Generic         | This is the primary Oracle Database documentation, which describes how the product works and how it is used. Use this type of documentation to learn about product functions and how to use any Oracle Database product or utility.  |
| System Specific | This documentation provides the information required to use the product on a specific operating system. Use this type of documentation to determine whether there are any system-specific deviations from the generic documentation. |

This manual is written for users of Oracle Database for BS2000, providing them with BS2000-specific information about using Oracle Database products. It does not describe how to use a product unless its use is different than that is described in the generic documentation.

### Related Documents

For more information, refer to the Fujitsu documentation at:

<https://bs2manuals.ts.fujitsu.com>

All Oracle documentation is available at the following URL:

[http://docs.oracle.com/en/](../../../../..)

### Conventions Used in this Manual

The following conventions are used in this manual:

#### Typographic Conventions

The following text conventions are used in this manual:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |

#### Command Syntax

| Item             | Syntax                                                                                                              |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------|
| Commands         | This font identifies text that must be entered exactly as shown:<br>`set echo off`                                  |
| Variables        | Variables appear in italics. Substitute an appropriate value, for example:<br>arg1                                  |
| Required Items   | Required items are enclosed in braces { }. You must choose one of the alternatives.<br>`DEFINE { macro1 | macro2 }` |
| Optional Items   | Optional items are enclosed in square brackets \[\].<br>\[options\] formname \[userid/password\]                    |
| Repetitive Items | An ellipsis, ... represents an arbitrary number of similar items.<br>CHKVAL fieldname value1 value2... valueN       |

#### Punctuation

The following symbols should always be entered as they appear in the command format:

| Name                  | Symbol |
|:----------------------|:-------|
| ampersand             | &      |
| backslash             | \\     |
| colon                 | :      |
| comma                 | ,      |
| double quotation mark | "      |
| equal sign            | =      |
| hyphen                | \-     |
| number sign           | \#     |
| parentheses           | ()     |
| period                | .      |
| semicolon             | ;      |
| single quotation mark | '      |
