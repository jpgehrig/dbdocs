The enhanced `ojvmjava` commands enable you to manipulate and browse the OJDS. This section describes the following commands:

- ls Command

- cd Command

- pwd Command

- chown Command

- mkdir Command

- rm Command

- ln Command

- mv Command

- chmod Command

- bind Command

- bindds Command

- bindurl Command

### 11.3.1 ls Command

The `ls` command displays the contents of a context.

#### Syntax

`ls [options] [context1] [context2] [obj|context]...`

#### Options

The following table describes the `ls` command options:

| Option        | Description                                                                                                          |
|:--------------|:---------------------------------------------------------------------------------------------------------------------|
| `Context obj` | Specifies the name of the context or object to be listed                                                             |
| `-l`          | Shows contents in long format including name, creation time, owner, rights, and so on. Shows the class of an object. |
| `dir`         | Shows only contexts, similar to the Unix `ls –d` command                                                             |
| `ldir`        | Shows contents in long format like the `–l` command, but ignores bound objects, similar to Unix –ld                  |
| `R`           | Recursively lists though child contexts                                                                              |

#### Example

The following command displays contents of the root Context in short format:

    $ ls /

    etc/      public/

The following command displays contents of the root Context in long format:

    $ ls -l
    Read      Write    Exec        Owner    Date       Time      Type       Name
    PUBLIC    SYS      PUBLIC      SYS      Dec 14     14:59     Context    etc
    PUBLIC    PUBLIC   PUBLIC      SYS      Dec 14     14:59     Context    public

### 11.3.2 cd Command

The `cd` command changes the working context. This command is similar to the Unix `cd` command to change directories.

#### Example

The following command changes the context to root Context

    $ cd /

### 11.3.3 pwd Command

The pwd command lists the current working context.

#### Example

If the current context is `/test/alpha`, then the output of the `pw`d command is the following:

    $ pwd

    /test/alpha/

### 11.3.4 chown Command

The `chown` command changes the ownership of the context or the object.

**Note:**

You can change ownership of a context or an object only if you are the `SYS` user.

#### Syntax

`chown [options] {user | role} <object name>`

#### Options

The following table describes the `chown` command options:

| Option          | Description                                                                                                                                                                 |
|:----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `User role`     | Specifies the name of the user or role to become the owner                                                                                                                  |
| `<object name>` | Specifies the name of the context or object to be changed                                                                                                                   |
| `-R`            | Recursively changes ownership of the following:<br>• Context<br>• All the subcontexts in the context<br>• All the objects that are contained in the context and subcontexts |

#### Example

The following command makes `HR` the owner of the `/alpha/beta/gamma` command:

    $ chown HR /alpha/beta/gamma

### 11.3.5 mkdir Command

The `mkdir` command creates a context with the given name.

**Note:**

You must have the Write permission for the target context to create the new context.

#### Options

The following table describes the `mkdir` command options:

| Option       | Description                                        |
|:-------------|:---------------------------------------------------|
| `<name>`     | Specifies the name of the context to be created    |
| `-path | -p` | Creates intermediate contexts if they do not exist |

#### Example

The following command creates a Context called `/test/alpha`, where the `/test` context exists already:

    mkdir /test/alpha

The following command creates a Context called `/test/alpha/beta/gamma`, where the `/test/alpha/beta` context does not exist:

    $ mkdir -path /test/alpha/beta/gamma

### 11.3.6 rm Command

The `rm` command is analogous to the `rm` UNIX shell command. This command removes an object or a context, including its contents.

**Note:**

To remove an object, you must have the Write right for the context that contains the object.

#### Options

The following table describes the `rm` command options:

| Option          | Description                                                            |
|:----------------|:-----------------------------------------------------------------------|
| `<Object>`      | Specifies the name of the context or the object to be removed          |
| `-recurse | -r` | Assumes a context and removes the context and its contents recursively |

#### Examples

The following command removes the object `/test/bank`:

    rm /test/bank

The following command removes the context `/test/release3` and its contents:

    rm -r /test/release3

### 11.3.7 ln Command

The `ln` command is analogous to the UNIX `ln` command. A link is a synonym for a context or an object. When you move a context or an object, the reference to the context or object may become invalid. The `ln` command creates a link with the old name and makes the object accessible by both the old and the new name.

#### Syntax

`ln [-symbolic | -s] <object> <link>`

#### Options

The following table describes the `ln` command options:

| Option     | Description                                                                |
|:-----------|:---------------------------------------------------------------------------|
| `-s`       | Create a soft link of `<object>` to `<link>`                               |
| `<object>` | Specifies the name of a context or an object                               |
| `<link>`   | Specifies the name of the synonym to which you link a context or an object |

#### Example

The following command preserves access to the `old` object even after the name of the object is changed to `new`:

    $ mv old new
    $ ln new old

### 11.3.8 mv Command

The `mv` command changes the name (or rebinds old names) of a context or an object to a new name.

#### Syntax

`mv <old> <new>`

#### Example

The following command changes the name of the context `/test/foo` to `/test/bar`:

    $ mv /test/foo /test/bar

### 11.3.9 chmod Command

The `chmod` command is analogous to the `chmod` UNIX shell command. This command changes the rights of a user or a role on a context or an object.

**Note:**

You can change the rights on an object only if you are the `SYS` user or the owner of the object.

#### Syntax

`chmod [options] {+|-} {r|w|x} {<user> | <role>, ...} <objectname>`

#### Options

The following table describes the `chmod` command options:

| Option            | Description                                        |
|:------------------|:---------------------------------------------------|
| `+/-rwx`          | Add (+) or remove (-) read, write, or execute      |
| `<user> | <role>` | The user or role whose rights are added or removed |
| `<objectname>`    | The context or object for which rights are changed |
| `-R`              | Changes rights recursively                         |

#### Example

The following example changes rights for the `/alpha/beta/gamma` context to `HR` and `NANCY`:

    $ chmod +x HR,NANCY /alpha/beta/gamma

**Note:**

The schemas are separated by only a comma.

The following example removes the Write rights of `HR` for the `/alpha/beta/gamma` context:

    $ chmod -w HR /alpha/beta/gamma

**Related Topics**

- [Object permissions](JNDI-support-requirement.md)

### 11.3.10 bind Command

The `bind` command binds an object reference or context into the JNDI namespace.

#### Syntax

`bind <objectname> [options] [-context] [-rebind] {-class | -c <classname>} [-factory | -f <factory>] [-location | -l <URL>][-string <type_name>`

`<string_value> [-string <type_name> <string_value> ...]] [-binary <type_name> <string_value> [-binary <type_name> <string_value> ...]]`

#### Options

The following table describes the `bind` command options:

| Option                               | Description                                                                                                                                        |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `<objectname>`                       | Name object is to be bound to                                                                                                                      |
| `-context`                           | The object to be bound is a Context or InitialContext                                                                                              |
| `-rebind`                            | If the JNDI name already exists, replaces the object that it is bound to with this object                                                          |
| `-class <classname>`                 | Specifies the class name for the bound object                                                                                                      |
| `-factory <factory>`                 | Specifies the factory class name for creating the object. JNDI uses this for creating the object.                                                  |
| `-location <URL>`                    | Specifies the factory location if the default location is not used. This takes a JNDI URL.                                                         |
| `-string <type_name> <string_value>` | Specifies a String reference attribute for the object by the type name and value.                                                                  |
| `-binary <type_name> <string_value>` | Specifies a Binary reference attribute for the object by the type and a binary value. The given Hexidecimal string value is converted into binary. |

#### Example

The following binds an object reference into the name space. A string and binary attribute is supplied to the reference.

    bind /tmp/myprinter  -class gen.Inkjet  -factory gen.InkjetFactory  -string PRINTERNAME co2  -binary DPI  0X12C

### 11.3.11 bindds Command

This command binds a `DataSource` object in the JNDI namespace. This command binds general, XA, or pooled data sources depending on specified options.

**Note:**

Oracle JVM supports only kprb drivers and thin drivers.

#### Syntax

`bindds <object_name> [options] [-help | -h] [-describe | -d] [-version | -v] [-dstype <datasource>]`

`[-host <hostname> -port <portnum> -sid <SID> -driver <driver_type>] [-url <db_url>]`

` [-g | -grant {<user> | <role>} [,{<user> | <role>}]...] [-recursiveGrant | -rg {<user> |<role>}`

`[,{<user> | <role>}]...] [-rebind] [-user | -u <user>]`

#### Options

The following table describes the `bindds` command options:

| Option                                                           | Description                                                                                                                                                                                                                                                                                                        |
|:-----------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<objectname>`                                                   | Specifies the name to which the object is to be bound                                                                                                                                                                                                                                                              |
| `-help`                                                          | Specifies the help message                                                                                                                                                                                                                                                                                         |
| `-describe`                                                      | Summarizes the tools operation                                                                                                                                                                                                                                                                                     |
| `-version`                                                       | Specifies the version number                                                                                                                                                                                                                                                                                       |
| `-dstype <type>`                                                 | Specifies the data source type from one of the following types:<br>• None for `OracleDataDource`<br>• `xa` for `OracleXADatasource`<br>• `pool` for `OracleConnectionPoolDataSource`                                                                                                                               |
| `-host <hostname> -port <portnum> -sid <SID> -driver <drv_type>` | Specify the location of the database and driver type for the connection to the database. You can alternatively specify this information in a URL format within the `-url` option. The default value for the `-sid` option is `ORCL`. The `-driver` option can have the following values: `thin`,` oci`, or `kprb`. |
| `-url <db_url>`                                                  | This JDBC URL specifies the location of the database.                                                                                                                                                                                                                                                              |
| `-grant <user|role>, <user|role>…`                               | Grants Read and Execute rights to the sequence of `<user>` and `<role>` names. When rebinding, replace the existing users or roles that have read or execute rights with the `<user>` and `<role>` names.                                                                                                          |
| `-recursiveGrant <user|role>, <user|role>….`                     | Recursively grants Read and Execute permission to the designated object and all the contexts in which the object exists. If the context has a permission level of SYS, the grant for that context is ignored.                                                                                                      |
| `-rebind`                                                        | If the `DataSource` object already exists, then you must specify this option to overwrite the existing data source with this new object. Otherwise, no bind occurs for this option.                                                                                                                                |
| `-user <user>`                                                   | Specifies the user name for connecting to the database. Stores the user name within the `DataSource` object. If you do not supply a user name within the JNDI Context while creating the database connection, then this user name is used.                                                                         |

#### Example

The following example binds the `ds1` data source into the namespace:

    bindds /test/ds1 -host localhost -port 1522 -sid orcl -driver thin
    bindds /test/ds1 -url jdbc:oracle:thin:@localhost:1522:orcl

The example uses the JDBC thin driver with a general data source, that is, `OracleDataSource`.

### 11.3.12 bindurl Command

The `bindurl` command binds a URL object in the namespace.

#### Options

The following table describes the `bindurl` command options:

| Option                                        | Description                                                                                                                                                                                                             |
|:----------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<objectname>`                                | Specifies the name of the object to be bound                                                                                                                                                                            |
| `-help`                                       | Specifies the help message                                                                                                                                                                                              |
| `-describe`                                   | Summarizes the tools operations                                                                                                                                                                                         |
| `-version`                                    | Prints the version of the `bindurl` command                                                                                                                                                                             |
| `-rebind`                                     | If the JNDI name already exists, then you must specify this option to overwrite the existing JNDI name with this new object. Otherwise, no bind occurs for this option.                                                 |
| `-grant <user|role>, <user|role>…`            | Grants Read and Execute rights to the sequence of `<user>` and `<role>` names. When rebinding, you can replace the existing users or roles that have read or execute rights with the `<user>` and `<role>` names.       |
| `-recursiveGrant <user|role>, <user|role>...` | Recursively grants Read and Execute permission to the designated object and to all contexts within which the object exists. If the context has a permission level of `SYS`, then the grant for that context is ignored. |

#### Example

The following example binds the URL string [`http://www.oracle.com`](http://www.oracle.com) to a URL reference `/test/myURL` within the namespace:

    bindurl /test/myURL http://www.oracle.com -rebind

The `-rebind` option is used to make sure that if the `/test/myURL` reference previously exists, then it is rebound with the string [`http://www.oracle.com`](http://www.oracle.com).
