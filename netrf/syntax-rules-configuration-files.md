## 3 Syntax Rules for Configuration Files

Learn how to follow the syntax configuration rules for Oracle Net Services parameters, keywords, addresses, and naming methods.

- Overview of Configuration File Syntax
  Construct your Oracle Net Services configuration files in accordance with syntax rules and standard conventions.
- Syntax Rules for Configuration Files
  Follow the structure, hierarchy, and character requirements for configuration files.
- Network Character Set for Keywords
  Use the permitted character set for keyword values and network character sets.
- Character Set for Listener and Net Service Names
  Learn how to create listener names and net service names for clients that comply with character set requirements.

### 3.1 Overview of Configuration File Syntax

Construct your Oracle Net Services configuration files in accordance with syntax rules and standard conventions.

The Oracle Net Services configuration files consist of parameters that include keyword-value pairs. Keyword-value pairs are surrounded by parentheses:

    parameter=(keyword=value)

Some keywords have other keyword-value pairs as their values:

    (keyword=
        (keyword1=value1)
        (keyword2=value2))

For example, the address portion of a local naming configuration file (`tnsnames.ora`) can include lines such as the following:

    (ADDRESS=
       (PROTOCOL=tcp)
       (HOST=sales-server)
       (PORT=1521))

Set up your configuration files so that indentation reflects what keyword is the parent or owner of other keyword-value pairs. If you do not choose to indent your files in this way, then you must still indent a wrapped line by at least one space, or it will be misread as a new parameter. The following syntax is acceptable:

    (ADDRESS=(PROTOCOL=tcp)
      (HOST=sales-server)(PORT=1521))

The following syntax is not acceptable:

    (ADDRESS=(PROTOCOL=tcp)
    (HOST=sales-server)(PORT=1521))

**Parent topic:** Syntax Rules for Configuration Files

### 3.2 Syntax Rules for Configuration Files

Follow the structure, hierarchy, and character requirements for configuration files.

The following rules apply to the syntax of configuration files:

- Any keyword in a configuration file that begins a parameter that includes one or more keyword-value pairs must be in the far left column of a line. If it is indented by one or more spaces, then it is interpreted as a continuation of the previous line.

- All characters must belong to the network character set.

- Keywords are not case sensitive. However, values can be case-sensitive, depending on your operating system and protocol.

- In keyword-value pairs, spaces around the equal sign (`=`) are optional.

- There is a hierarchy of keywords, which requires that some keywords are always followed by others. At any level of the hierarchy, keywords can be listed in any order. For example, the following entries are equally valid:

      (ADDRESS=
         (PROTOCOL=TCP)
         (HOST=sales-server)
         (PORT=1521))

      (ADDRESS=
         (PROTOCOL=tcp)
         (PORT=1521)
         (HOST=sales-server))

- Keywords cannot contain spaces.

- Values must not contain spaces, unless the values with spaces are enclosed within double quotation marks (`"`) or single quotation marks (`'`).

- If the keyword-value pair consists of a single word, or a concatenation of words on either side of the equal sign, then no parentheses are needed.

- The maximum length of a connect descriptor is 4 KB.

- You can include comments by using the number sign (`#`) at the beginning of a line. Anything following the number sign to the end of the line is considered a comment.

**Parent topic:** Syntax Rules for Configuration Files

### 3.3 Network Character Set for Keywords

Use the permitted character set for keyword values and network character sets.

The network character set for keyword values consists of the following characters. Connect descriptors must be made up of single-byte characters.

    A-Z, a-z
    0-9
    ( ) < > / \
    , . : ; ' "=- _
    $ + * # & ! % ? @

Within this character set, the following symbols are reserved:

    ( ) = \ " ' #

Reserved symbols are used as delimiters, not as part of a keyword or a value, unless the keyword or value has quotation marks. If you have a value that contains reserved symbols, then use either single or double quotation marks to enclose the value. To include a quotation marks within a value that is surrounded by quotation marks, use different quotation marks. The backslash (`\`) is used as an escape character.

You can use the following characters within a connect descriptor, but not in a keyword or value:

- Space

- Tab

- Carriage return

- Newline

**Parent topic:** Syntax Rules for Configuration Files

### 3.4 Character Set for Listener and Net Service Names

Learn how to create listener names and net service names for clients that comply with character set requirements.

Listener names and net service names are limited to the following character set:

    [a...z] [A...Z] [0...9] _

The first character in the listener name or net service name must be an alphanumeric character. In general, names up to 64 characters in length are acceptable. In addition, a database service name must match the global database name defined by the database administrator, which consists of a database name, and the database domain. Both net service names and global database names are not case-sensitive.

**Parent topic:** Syntax Rules for Configuration Files
