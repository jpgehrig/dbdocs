This chapter describes how to create an environment on BS2000, where external C procedure calls can operate. External JAVA methods are not supported on BS2000.

This chapter complements the chapter about External Procedures in the [Oracle Database Development Guide](../adfns/design_basics.md).

**Note:**

The default configuration for external procedures does not require a network listener to work with Oracle Database and the `extproc` agent. The `extproc` agent is spawned directly by Oracle Database and eliminates the risks that the `extproc` agent might be spawned by Oracle Listener unexpectedly. This default configuration is recommended for maximum security.

You can change the default configuration for external procedures and have the `extproc` agent spawned by Oracle Listener. To do this, you must perform additional network configuration steps.

Having the `extproc` agent spawned by Oracle Listener is necessary if you use:

The `AGENT` clause of the LIBRARY specification or the `AGENT IN` clause of the PROCEDURE specification such that you can redirect external procedures to a different `extproc` agent.

### 15.1 Loading External Procedures

This section complements the corresponding part in [Oracle Database Development Guide](../adfns/external-procedures.md). It shows how to use an external C procedure stored in a dynamic load library (DLL) with Oracle on BS2000. In this context a DLL is specified as a LMS library in the BS2000 environment or a shared object in the POSIX environment.

Perform the following steps to load external procedures:

- Define C Procedures

- Set Up the Environment

- Identify the DLL

- Publish External Procedures

- Run External Procedures

#### 15.1.1 Define C Procedures

Define the C procedures using one of the prototypes.

Refer to [Oracle Database Development Guide](../adfns/external-procedures.md) for the prototypes. Compile the C procedures either in the BS2000 environment or in the POSIX program environment.

##### BS2000 Program Environment

Compile the program using the BS2000 C/C++ compiler. The created LLM object must be stored in a LMS library. You must consider the default settings `LOWER-CASE-NAMES=*NO` and `SPECIAL-CHARACTERS=*CONVERT-TO-DOLLAR` of the C/C++ compiler option `MODULE-PROPERTIES`. These default settings cause the conversion of all lowercase letters in the entry names to uppercase and of all underscores (\_) in the entry names to dollar signs (`$`).

##### POSIX Program Environment

Use the POSIX installation of the BS2000 C/C++ compiler to compile the program in the POSIX shell. You must consider that on default lower case letters in entry names will be translated to upper case letters and underscores in entry names will be translated to dollar signs. Use the option `–K llm_case_lower,llm_keep` to retain lower case letters and underscore characters when entry names are generated.

The example shows how to compile the source `C_concat.c`:

    $ /usr/bin/cc -c -K llm_case_lower,llmcase_lower -B extended_external_names -D_OSD_POSIX –I
    /u01/app/oracle/product/19.3.0/dbhome_1/rdbms/public C_concat.c

Use the tool `genso` to generate a shared object. The following example illustrates how to create the shared object `C_utils.so` for the C procedure,

`char *concat(ctx, str1, str1_i, str2, str2_i, ret_i, ret_l)`

in the source file `C_concat.c` :

    $ /usr/bin/genso -o lib/C_utils.so C_concat.o

Refer to [Oracle Database Development Guide](../adfns/external-procedures.md) for the C code example.

#### 15.1.2 Set Up the Environment

When you use the default configuration for external procedures, Oracle Database spawns `extproc` directly. You need not make configuration changes for `listener.ora` and `tnsnames.ora`. Define the environment variables to be used by external procedures in the file `extproc.ora` located at `$ORACLE_HOME/hs/admin` using this syntax:

    SET name=value (environment_variable_name=value)

If the load library is a BS2000 LMS library you must set the variable `EXTPROC_DLLS` to `ANY`, For example:

    SET EXTPROC_DLLS=ANY

If the load library is a POSIX shared object you can set the variable `EXTPROC_DLLS` as described in [Oracle Database Development Guide](../adfns/external-procedures.md). If you have not specified the full qualified file path for the shared object then you must set the variable `LD_LIBRARY_PATH`. Following is an example of an `extproc.ora` file for the shared object file `C_utils.so`, which resides in the `/home/oracle/lib` directory:

    SET EXTPROC_DLLS=ONLY:C_utils.so
    SET LD_LIBRARY_PATH=/home/oracle/lib

To change the default configuration for external procedures and have your `extproc` agent spawned by Oracle Listener, configure your `listener.ora` and `tnsnames.ora` as follows. The `listener.ora` file must have the following entries:

    EXTPLSNR=
      (DESCRIPTION=
        (ADDRESS_LIST=
          (ADDRESS=(PROTOCOL=ipc)(KEY=extp))))

    SID_LIST_EXTPLSNR=
      (SID_LIST=
        (SID_DESC=
          (SID_NAME=ep_agt1)
          (ORACLE_HOME=/u01/app/oracbase/product/19.3.0/dbhome_1)
          (ENVS=”EXTPROC_DLLS=ANY LD_LIBRARY_PATH=/home/oracle/lib”)
          (ORACLE_SID=extp)
          (PROGRAM= extproc)))

Assign the environment variables to be used by external procedures to the parameter `ENVS`. When `extproc.ora` is in use, it precedes the same environment variables of `ENVS` in `listener.ora` file.

The `tnsnames.ora` file must have the following entry:

    extproc_agent=
      (DESCRIPTION=
        (ADDRESS=PROTOCOL=ipc)(KEY=extp))
        (CONNECT_DATA=
          (PRESENTATION=RO)
          (SID=ep_agt1)))

Now, you can start the `extproc` listener.

**See Also:**

- [Oracle Database Development Guide](../adfns/external-procedures.md)

- [Oracle Database Data Cartridge Developer's Guide](../addci/implementing-data-cartridges-in-C-CPP-and-java.md)

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md)

#### 15.1.3 Identify the DLL

The objects in the DLL contain the functions called as external procedures. When `extproc` is loaded, these functions are dynamically linked to the program. Use the `CREATE LIBRARY` statement to create a schema object called an alias library, which represents the DLL. The name of the DLL must match the filename specified in the value of the `extproc.ora` variable `EXTPROC_DLLS`.

    CREATE LIBRARY [schema_name.]library_name
      {IS | AS} 'file_path'
      [AGENT 'agent_link'];

For the default configuration you must not specify the parameter `AGENT`. An example for a BS2000 LMS library is as follows:

    CREATE LIBRARY C_utils AS '[$extp_userid.]C.UTILS.MODLIB';

An example for a POSIX shared object is:

    CREATE LIBRARY C_utils AS '[path/]C_utils.so';

If you want to change the default configuration for external procedures and have your `extproc` spawned by an Oracle Listener, then you must define a database link which is used with the `AGENT` parameter of the `CREATE LIBRARY` statement.

    CREATE DATABASE LINK agent_link USING 'extproc_agent';
    CREATE OR REPLACE LIBRARY C_utils IS 'C.UTILS.MODLIB' agent 'agent_link';

**See Also:**

[Oracle Database Development Guide](../adfns/external-procedures.md)

#### 15.1.4 Publish External Procedures

Oracle Database can use only external procedures that are published through a call specification, which maps names, parameter types, and return types for your C external procedures to their SQL counterparts. It is written like any other PL/SQL stored procedure except that, in its body, instead of declarations and a `BEGIN END` block, you code the `AS LANGUAGE` clause.

The following example illustrates how you can publish an External Procedure as a PL/SQL function:

    CREATE OR REPLACE FUNCTION plsToC_concat_func (
       str1 IN VARCHAR2,
       str2 IN VARCHAR2)
    RETURN VARCHAR2 AS LANGUAGE C
    NAME "concat"
    LIBRARY C_utils
    WITH CONTEXT
    PARAMETERS (
    CONTEXT,
    str1   STRING,
    str1   INDICATOR short,
    str2   STRING,
    str2   INDICATOR short,
    RETURN INDICATOR short,
    RETURN LENGTH short,
    RETURN STRING);

**See Also:**

[Oracle Database Development Guide](../adfns/external-procedures.md)

#### 15.1.5 Run External Procedures

Calling an external C procedure depends on the type of publishing the external procedure as a PL/SQL procedure, package, or function.

An example of how to publish the external C procedure as a PL/SQL function is described in the [Oracle Database Development Guide.](../adfns/external-procedures.md)

You can also run this function within a select statement as follows:

    select plsToC_concat_func('hello ', 'world') from DUAL;

If your external procedure writes messages to `STDOUT`, then you can find these messages in the `L.``sid``.EXTP.SYSOUT.``tsn` file. Set the environment variable `BGJOUT` to `KEEP` to avoid the cleanup of the `L.``sid``.EXTP.SYSOUT.``tsn` file.
