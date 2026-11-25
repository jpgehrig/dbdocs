The `ojvmjava` tool is an interactive interface to the session namespace of a database instance. You specify database connection arguments when you start the `ojvmjava` tool. It then presents you with a prompt to indicate that it is ready for commands.

The shell can launch an executable, that is, a class with a `static main()` method. This is done either by using the command-line interface or by calling a database resident class. If you call a database resident class, the executable must be loaded with the `loadjava` tool.

This section covers the following topics:

- ojvmjava Tool Syntax

- ojvmjava Tool Argument Summary

- ojvmjava Tool Example

- ojvmjava Tool Functionality

### 12.8.1 ojvmjava Tool Syntax

The syntax of the `ojvmjava` tool command is:

    ojvmjava {-user user[/password@database ] [options]
      [@filename]
      [-batch]
      [-c | -command command args]
      [-debug]
      [-d | -database conn_string]
      [-fileout filename]
      [-o | -oci | -oci8]
      [-oschema schema]
      [-t | -thin]
      [-version | -v]
     -runjava [server_file_system]
     -jdwp port [host]
     -verbose

### 12.8.2 ojvmjava Tool Argument Summary

Table 12-4 summarizes the `ojvmjava` tool arguments.

Table 12-4 ojvmjava Argument Summary

| Argument                       | Description                                                                                                                                                                                                                                                                                                   |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-user | -u`                   | Specifies user name for connecting to the database. This name is not case-sensitive. The name will always be converted to uppercase. If you provide the database information, then the default syntax used is OCI. You can also specify the default database.                                                 |
| `-password | -p`               | Specifies the password for connecting to the database.                                                                                                                                                                                                                                                        |
| `@``filename`                  | Specifies a script file that contains the `ojvmjava` tool commands to be run.                                                                                                                                                                                                                                 |
| `-batch`                       | Disables all messages displayed to the screen. No help messages or prompts will be displayed. Only responses to commands entered are displayed.                                                                                                                                                               |
| `-command`                     | Runs the desired command. If you do not want to run the `ojvmjava` tool in interpretive mode, but only want to run a single command, then run it with this option followed by a string that contains the command and the arguments. Once the command runs, the `ojvmjava` tool exits.                         |
| `-debug`                       | Displays debugging information.                                                                                                                                                                                                                                                                               |
| `-d | -database ``conn_string` | Provides a database connection string.                                                                                                                                                                                                                                                                        |
| `-fileout ``file`              | Redirects output to the provided file.                                                                                                                                                                                                                                                                        |
| `-o | -oci | -oci8`            | Uses the JDBC OCI driver. The OCI driver is the default. This flag specifies the syntax used in either the `@``database` or `-database` option.                                                                                                                                                               |
| `-o schema ``schema`           | Uses this schema for class lookup.                                                                                                                                                                                                                                                                            |
| `-t | -thin`                   | Specifies that the database syntax used is for the JDBC Thin driver. The database connection string must be of the form `host``:``port``:``SID` or an Oracle Net Services name-value list.                                                                                                                    |
| `-verbose`                     | Displays the connection information.                                                                                                                                                                                                                                                                          |
| `-version`                     | Shows the version.                                                                                                                                                                                                                                                                                            |
| `-runjava`                     | Uses `DBMS_JAVA.runjava` when executing Java commands. With no argument, interprets `-classpath` as referring to the client file system. With argument `server_file_system` interprets `-classpath` as referring to the file system on which Oracle server is running, as `DBMS_JAVA.runjava` typically does. |
| `-jdwp`                        | Makes the connection listen for a debugger connection on the indicated port and host. The default value of host is `localhost.`                                                                                                                                                                               |

### 12.8.3 ojvmjava Tool Example

Open a shell on the session namespace of the database `orcl` on listener port `2481` on the host `dbserver`, as follows:

    ojvmjava -thin -user HR@dbserver:2481:orcl
    Password: password

### 12.8.4 ojvmjava Tool Functionality

The `ojvmjava` tool commands span several different types of functionality, which are grouped as follows:

- ojvmjava Tool Command-Line Options

- ojvmjava Tool Shell Commands

#### 12.8.4.1 ojvmjava Tool Command-Line Options

This section describes the following options available with the `ojvmjava` tool command:

- Scripting the ojvmjava Tool Commands in the @filename Option

- -runjava

- -jdwp

##### Scripting the ojvmjava Tool Commands in the @filename Option

This `@``filename` option designates a script file that contains one or more `ojvmjava` tool commands. The specified script file is located on the client. The `ojvmjava` tool reads the file and runs all commands on the designated server. In addition, because the script file is run on the server, any interaction with the operating system in the script file, such as redirecting output to a file or running another script, occurs on the server. If you direct the `ojvmjava` tool to run another script file, then this file must exist in `$ORACLE_HOME` on the server.

You must enter the `ojvmjava` tool command followed by any options and any expected input arguments. The script file contains the `ojvmjava` tool command followed by options and input parameters. The input parameters can be passed to the `ojvmjava` tool on the command line. The `ojvmjava` tool processes all known options and passes on any other options and arguments to the script file.

The following shows the contents of the script file, `execShell`:

    java myclass a b c

To run this file, use the following command:

    ojvmjava -user HR -thin -database dbserver:2481:orcl @commands
    Password: password

The `ojvmjava` tool processes all options that it knows about and passes along any other input parameters to be used by the commands that exist within the script file. In this example, the parameters are passed to the `java` command in the script file.

You can add any comments in your script file using the hash sign (`#`). Comments are ignored by the `ojvmjava` tool. For example:

    #this whole line is ignored by ojvmjava

##### -runjava

This option controls whether or not the `ojvmjava` tool shell command Java runs executable classes using the command-line interface or database resident classes. When the `-runjava` option is present the command-line interface is used. Otherwise, the executable must be a database resident class that was previously loaded with the `loadjava` tool. Using the optional argument `server_file_system` means that the `-classpath` terms are on the file system of the machine running Oracle server. Otherwise, they are interpreted as being on the file system of the machine running the `ojvmjava` tool.

##### -jdwp

This option specifies a debugger connection to listen for when the shell command `java` is used to run an executable. This allows for debugging the executable. The arguments specify the port and host. The default value of the host argument is `localhost.` These are used to execute a call to `DBMS_DEBUG_JDWP.CONNECT_TCP` from the RDBMS session, in which the executable is run.

**Related Topics**

- [About Using the Command-Line Interface](invoking-Java-methods.md)

#### 12.8.4.2 ojvmjava Tool Shell Commands

This section describes the following commands available within the `ojvmjava` shell:

- echo

- exit

- help

- java

- version

- whoami

- connect

- runjava

- jdwp

**Note:**

An error is reported if you enter an unsupported command.

The following table summarizes the commands that share one or more common options:

Table 12-5 ojvmjava Command Common Options

| Option           | Description                           |
|:-----------------|:--------------------------------------|
| `-describe | -d` | Summarizes the operation of the tool. |
| `-help | -h`     | Summarizes the syntax of the tool.    |
| `-version`       | Shows the version.                    |

##### echo

This command displays to `stdout` exactly what is indicated. This is used mostly in script files.

The syntax is as follows:

    echo [echo_string] [args]

`echo_string` is a string that contains the text you want written to the screen during the shell script invocation and `args` are input arguments from the user. For example, the following command displays out a notification:

    echo "Adding an owner to the schema" &1

If the input argument is `HR`, then the output would be:

    Adding an owner to the schema HR

##### exit

This command terminates `ojvmjava`. The syntax is as follows:

    exit

For example, to leave a shell, use the following command:

    $ exit
    %

##### help

This command summarizes the syntax of the shell commands. You can also use the help command to summarize the options for a particular command. The syntax is as follows:

    help [command]

##### java

This command is analogous to the JDK `java` command. It calls the static `main()` method of a class. It does this either by using the command-line interface or using a database resident class, depending on the setting of the `runjava` mode. In the latter case, the class must have been previously loaded with the `loadjava` tool. The command provides a convenient way to test Java code that runs in the database. In particular, the command catches exceptions and redirects the standard output and standard error of the class to the shell, which displays them as with any other command output. The destination of standard out and standard error for Java classes that run in the database is one or more database server process trace files, which are inconvenient and may require `DBA` privileges to read.

The syntax of the command with `runjava` mode `off` is:

    java [-schema schema] class [arg1 ... argn]

The syntax of the command with `runjava` mode `on` is:

    java [command-line options] class [arg1 ... argn]

where, command-line options can be any of those mentioned in [Table 3-1](invoking-Java-methods.md).

The following table summarizes the arguments of this command.

Table 12-6 java Argument Summary

| Argument            | Description                                                                                                              |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------|
| `class`             | Names the Java class schema object that is to be run.                                                                    |
| `-schema`           | Names the schema containing the class to be run. The default is the invoker's schema. The schema name is case-sensitive. |
| `arg1`` ... ``argn` | Arguments to the `static main()` method of the class.                                                                    |

Consider the following Java file, `World.java`:

    package hello;
    public class World
    {
      public World()
      {
        super();
      }

      public static void main(String[] argv)
      {
        System.out.println("Hello from Oracle Database");
        if (argv.length != 0)
          System.out.println("You supplied " + argv.length + " arguments: ");
        for (int i = 0; i < argv.length; i++)
          System.out.println(" arg[" + i + "] : " + argv[i]);
      }
    }

You can compile, load, publish, and run the class, as follows:

    % javac hello/World.java

    % loadjava -r -user HR@localhost:2481:orcl hello/World.class
    Password: password
    % ojvmjava -user HR -database localhost:2481:orcl
    Password: password
    $ java hello.World alpha beta
    Hello from Oracle Database
    You supplied 2 arguments:
    arg[0] : alpha
    arg[1] : beta

##### version

This command shows the version of the `ojvmjava` tool. You can also show the version of a specified command. The syntax of this command is:

    version [options] [command]

For example, you can display the version of the shell, as follows:

    $ version
    1.0

##### whoami

This command displays the user name of the user who logged in to the current session. The syntax of the command is:

    whoami

##### connect

This command enables the client to drop the current connection and connect to different databases without having to reinvoke the `ojvmjava` tool with a different connection description.

The syntax of this command is:

    connect [-service service] [-user user][-password password]

You can use this command as shown in the following examples:

    connect -s thin@locahost:5521:orcl -u HR/<password>
    connect -s oci@locahost:5521:orcl -u HR -p <password>

The following table summarizes the arguments of this command.

Table 12-7 connect Argument Summary

| Argument        | Description                                                                                  |
|:----------------|:---------------------------------------------------------------------------------------------|
| -service \| -s  | Any valid JDBC driver URLS, namely, oci @\<connection descriptor\> and thin@\<host:port:db\> |
| `-user | -u`    | User to connect as                                                                           |
| -password \| -p | Password to connect with                                                                     |

##### runjava

This command queries or modifies the `runjava` mode. The `runjav`a mode determines whether or not the `java` command uses the command-line interface to run executables. The `java` command:

- Uses the command-like interface when `runjava` mode is `on`

- Uses database resident executables when `runjava` mode is `off`

Using the `runjava` command with no arguments displays the current setting of `runjava` mode.

The following table summarizes the arguments of this command.

Table 12-8 runjava Argument Summary

| Argument             | Description                                                                                                                                                                                                                                   |
|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `off`                | Turns `runjava` mode off.                                                                                                                                                                                                                     |
| `on`                 | Turns `runjava` mode on.                                                                                                                                                                                                                      |
| `server_file_system` | Turns `runjava` mode on. Using this option means that `-classpath` terms are on the file system of the machine running Oracle server. Otherwise, they are interpreted as being on the file system of the machine running the `ojvmjava` tool. |

##### jdwp

This command queries or modifies whether and how a debugger connection is listened for when an executable is run by the Java command.

**Note:**

The RDBMS session, prior to starting the executable, executes a `DBMS_DEBUG_JDWP.CONNECT_TCP` call with the specified port and host. This is called Listening.

Using this command with no arguments displays the current setting.

The following table summarizes the arguments of this command.

Table 12-9 jdwp Argument Summary

| Argument | Description                                                                                              |
|:---------|:---------------------------------------------------------------------------------------------------------|
| off      | Stops listening in future executables.                                                                   |
| `port`   | Enables listening and specifies the port to be used.                                                     |
| host     | Enables listening and specifies the host to be used. The default value for this argument is `localhost.` |
