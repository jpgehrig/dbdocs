This chapter focuses on writing user exits for your Oracle Tools applications. You learn how C subroutines can do certain jobs more quickly and easily than SQL\*Forms and Oracle Forms. This chapter contains the following topics:

- What Is a User Exit?

- Why Write a User Exit?

- About Developing a User Exit

- About Writing a User Exit

- EXEC TOOLS Statements

- About Calling a User Exit

- About Passing Parameters to a User Exit

- About Returning Values to a Form

- An Example of Using User Exits

- About Precompiling and Compiling a User Exit

- Example Program: A User Exit

- About Using the GENXTB Utility

- About Linking a User Exit into SQL\*Forms

- Guidelines

This chapter is supplemental. For more information about user exits, refer to the SQL\*Forms Designer's Reference, the Oracle Forms Reference Manual, Vol. 2, and your system-specific Oracle documentation.

### 20.1 What Is a User Exit?

A user exit is a C subroutine written by you and called by Oracle Forms to do special-purpose processing. You can embed SQL statements and PL/SQL blocks in your user exit, then precompile it as you would a host program.

When called by an Oracle Forms V3 trigger, the user exit runs, then returns a status code to Oracle Forms. Your exit can display messages on the Oracle Forms status line, get and set field values, do high-speed computations and table lookups, and manipulate Oracle data.

### 20.2 Why Write a User Exit?

SQL\*Forms provides the ability to use PL/SQL blocks in triggers. So, in most cases, instead of calling a user exit, you can use the procedural power of PL/SQL. If the need arises, you can call user exits from a PL/SQL block with the USER_EXIT function. User exits are harder to write and implement than SQL, PL/SQL, or SQL\*Forms commands. So, you will probably use them only to do processing that is beyond the scope of SQL, PL/SQL, and SQL\*Forms. Some common uses follow:

- Operations more quickly or easily done in a third generation languages like C (numerical integration, for instance)

- Controlling real time devices or processes (issuing a sequence of instructions to a printer or graphics device, for example)

- Data manipulations that need extended procedural capabilities (recursive sorting, for example)

- Special file I/O operations

### 20.3 About Developing a User Exit

This section outlines the way to develop a SQL\*Forms user exit; later sections go into more detail.

To incorporate a user exit into a form, you take the following steps:

- Write the user exit in Pro\*C.

- Precompile the source code.

- Compile the. c file from step 2.

- Use the GENXTB utility to create a database table, IAPXTB.

- Use the GENXTB form in SQL\*Forms to insert your user exit information into the table.

- Use the GENXTB utility to read the information from the table and create an IAPXIT source code module. Then compile the source code module.

- Create a new SQL\*Forms executable by linking the standard SQL\*Forms modules, your user exit object, and the IAPXIT object created in step 6.

- In the form, define a trigger to call the user exit.

- Instruct operators to use the new IAP when running the form. This is unnecessary if the new IAP replaces the standard one. For details, see the Oracle installation or user's guide for your system.

**Related Topics**

- EXEC TOOLS Statements

### 20.4 About Writing a User Exit

You can use the following kinds of statements to write your SQL\*Forms user exit:

- C code

- EXEC SQL

- EXEC ORACLE

- EXEC TOOLS

This section focuses on the EXEC TOOLS statements, which let you pass values between SQL\*Forms and a user exit.

#### 20.4.1 Requirements for Variables

The variables used in EXEC TOOLS statements must correspond to field names used in the form definition.

### 20.5 EXEC TOOLS Statements

EXEC TOOLS statements support the basic Oracle Toolset by providing a generic way to handle get, set, and exception callbacks from user exits. The following discussion focuses on Oracle Forms but the same concepts apply to Oracle Report.

#### 20.5.1 About Writing a Toolset User Exit

Besides EXEC SQL, EXEC ORACLE, and host language statements, you can use the following EXEC TOOLS statements to write an Oracle Forms user exit:

- SET

- GET

- SET CONTEXT

- GET CONTEXT

- MESSAGE

The EXEC TOOLS GET and SET statements replace the EXEC IAF GET and PUT statements used with earlier versions of Oracle Forms. Unlike IAF GET and PUT, however, TOOLS GET and SET accept indicator variables. The EXEC TOOLS MESSAGE statement replaces the message-handling function sqliem. Now, let us take a brief look at all the EXEC TOOLS statements. For more information, see the Oracle Forms Reference Manual, Vol 2.

#### 20.5.2 EXEC TOOLS SET

The EXEC TOOLS SET statement passes values from a user exit to Oracle Forms. Specifically, it assigns the values of host variables and constants to Oracle Forms variables and items. Values passed to form items display after the user exit returns control to the form. To code the EXEC TOOLS SET statement, you use the syntax

    EXEC TOOLS SET form_variable[, ...]
         VALUES ({:host_variable :indicator | constant}[, ...]);

where form_variable is an Oracle Forms field, block.field, system variable, or global variable, or a host variable (prefixed with a colon) containing the value of one of the foregoing items. In the following example, a user exit passes an employee name to Oracle Forms:

    char ename[20];
    short ename_ind;

    ...

        strcpy(ename, "MILLER");
        ename_ind = 0;
        EXEC TOOLS SET emp.ename VALUES (:ename :ename_ind);

In this example, emp.ename is an Oracle Forms block.field.

#### 20.5.3 EXEC TOOLS GET

The EXEC TOOLS GET statement passes values from Oracle Forms to a user exit. Specifically, it assigns the values of Oracle Forms variables and items to host variables. As soon as the values are passed, the user exit can use them for any purpose. To code the EXEC TOOLS GET statement, you use the syntax

    EXEC TOOLS GET form_variable[, ...]
        INTO :host_variable:indicator[, ...];

where form_variable is an Oracle Forms field, block.field, system variable, or global variable, or a host variable (prefixed with a colon) containing the value of one of the foregoing items. In the following example, Oracle Forms passes an item name from a block to your user exit:

    ...
    char     name_buff[20];
    VARCHAR  name_fld[20];

    strcpy(name_fld.arr, "EMP.NAME");
    name_fld.len = strlen(name_fld.arr);
    EXEC TOOLS GET :name_fld INTO :name_buff;

#### 20.5.4 EXEC TOOLS SET CONTEXT

The EXEC TOOLS SET CONTEXT statement saves context information from a user exit for later use in another user exit. A pointer variable points to a block of memory in which the context information is stored. With SET CONTEXT, you need not declare a global variable to hold the information. To code the EXEC TOOLS SET CONTEXT statement, you use the syntax

    EXEC TOOLS SET CONTEXT :host_pointer_variable
        IDENTIFIED BY context_name;

where context_name is an undeclared identifier or a character host variable (prefixed with a colon) that names the context area.

    ...
    char  *context_ptr;
    char  context[20];

    strcpy(context, "context1")
    EXEC TOOLS SET CONTEXT :context IDENTIFIED BY application1;

#### 20.5.5 EXEC TOOLS GET CONTEXT

The EXEC TOOLS GET CONTEXT statement retrieves context information (saved earlier by SET CONTEXT) into a user exit. A host-language pointer variable points to a block of memory in which the context information is stored. To code the EXEC TOOLS GET CONTEXT statement, you use the syntax

    EXEC TOOLS GET CONTEXT context_name
        INTO :host_pointer_variable;

where context_name is an undeclared identifier or a character host variable (prefixed with a colon) that names the context area. In the following example, your user exit retrieves context information 1saved earlier:

    ...
    char  *context_ptr;

    EXEC TOOLS GET CONTEXT application1 INTO :context_ptr;

#### 20.5.6 EXEC TOOLS MESSAGE

The EXEC TOOLS MESSAGE statement passes a message from a user exit to Oracle Forms. The message is displayed on the Oracle Forms message line after the user exit returns control to the form. To code the EXEC TOOLS MESSAGE statement, you use the syntax

    EXEC TOOLS MESSAGE message_text [severity_code];

where message_text is a quoted string or a character host variable (prefixed with a colon), and the optional severity_code is an integer constant or an integer host variable (prefixed with a colon). The MESSAGE statement does not accept indicator variables. In the following example, your user exit passes an error message to Oracle Forms:

    EXEC TOOLS MESSAGE 'Bad field name! Please reenter.';

### 20.6 About Calling a User Exit

You call a user exit from a SQL\*Forms trigger using a packaged procedure named USER_EXIT (supplied with SQL\*Forms). The syntax you use is

    USER_EXIT(user_exit_string [, error_string]);

where user_exit_string contains the name of the user exit plus optional parameters and error_string contains an error message issued by SQL\*Forms if the user exit fails. For example, the following trigger command calls a user exit named LOOKUP:

    USER_EXIT('LOOKUP');

Notice that the user exit string is enclosed by single (not double) quotes.` `

### 20.7 About Passing Parameters to a User Exit

When you call a user exit, SQL\*Forms passes it the following parameters automatically:

| Parameters           | Description                                                                        |
|:---------------------|:-----------------------------------------------------------------------------------|
| Command Line         | Is the user exit string.                                                           |
| Command Line Length  | Is the length (in characters) of the user exit string.                             |
| Error Message        | Is the error string (failure message) if one is defined.                           |
| Error Message Length | Is the length of the error string.                                                 |
| In-Query             | Is a Boolean value indicating whether the exit was called in normal or query mode. |

However, the user exit string provides the ability to pass additional parameters to the user exit. For example, the following trigger command passes two parameters and an error message to the user exit LOOKUP:

Notice that the user exit string is enclosed by single (not double) quotes.

    USER_EXIT('LOOKUP 2025 A', 'Lookup failed');


You can use this feature to pass field names to the user exit, as the following example shows:

    USER_EXIT('CONCAT firstname, lastname, address');


However, it is up to the user exit, not SQL\*Forms, to parse the user exit string.

### 20.8 About Returning Values to a Form

When a user exit returns control to SQL\*Forms, it must also return a code indicating whether it succeeded, failed, or suffered a fatal error. The return code is an integer constant defined by SQL\*Forms (see the next section). The three results have the following meanings:

| Results     | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| success     | The user exit encountered no errors. SQL\*Forms proceeds to the success label or the next step, unless the Reverse Return Code switch is set by the calling trigger step.                                                                                                                                                                                                                                                                                                                                                     |
| failure     | The user exit detected an error, such as an invalid value in a field. An optional message passed by the exit appears on the message line at the bottom of the SQL\*Forms screen and on the Display Error screen. SQL\*Forms responds as it does to a SQL statement that affects no rows.                                                                                                                                                                                                                                      |
| fatal error | The user exit detected a condition that makes further processing impossible, such as an execution error in a SQL statement. An optional error message passed by the exit appears on the SQL\*Forms Display Error screen. SQL\*Forms responds as it does to a fatal SQL error. If a user exit changes the value of a field, then returns a failure or fatal error code, SQL\*Forms does not discard the change. Nor does SQL\*Forms discard changes when the Reverse Return Code switch is set and a success code is returned. |

#### 20.8.1 The IAP Constants

SQL\*Forms defines three symbolic constants for use as return codes. Depending on the host language, they are prefixed with IAP or SQL. For example, they might be IAPSUCC, IAPFAIL, and IAPFTL.

#### 20.8.2 About Using WHENEVER

You can use the WHENEVER statement in an exit to detect invalid datatype conversions (SQLERROR), truncated values PUT into form fields (SQLWARNING), and queries that return no rows (NOT FOUND).

### 20.9 An Example of Using User Exits

The following example shows how a user exit that uses the EXEC TOOLS GET and PUT routines, as well as the EXEC TOOLS MESSAGE function, is coded.

    int
    myexit()
    {
        char field1[20], field2[20], value1[20], value2[20];
        char result_value[20];
        char errmsg[80];
        int errlen;

        #include sqlca.h
        EXEC SQL WHENEVER SQLERROR GOTO sql_error;
        /* get field values into form */
        EXEC TOOLS GET :field1, :field2 INTO :value1, :value2;
        /* manipulate the values to obtain result_val */
        ...
        /* put result_val into form field result */
        EXEC TOOLS PUT result VALUES (:result_val);
        return IAPSUCC;   /* trigger step succeeded */

    sql_error:
        strcpy(errmsg, CONCAT("MYEXIT", sqlca.sqlerrm.sqlerrmc);
        errlen = strlen(errmsg);
        EXEC TOOLS MESSAGE :errmsg ; /* send error msg to Forms */
        return IAPFAIL;

### 20.10 About Precompiling and Compiling a User Exit

User exits are precompiled like standalone host programs. For instructions on compiling a user exit, see the Oracle installation or user's guide for your system.

**Related Topics**

- [Precompiler Options](precompiler-options.md)

### 20.11 Example Program: A User Exit

The following example shows a user exit.

    /**************************************************************
    Sample Program 5:  SQL*Forms User Exit

    This user exit concatenates form fields.  To call the user
    exit from a SQL*Forms trigger, use the syntax

       user_exit('CONCAT field1, field2, ..., result_field');

    where user_exit is a packaged procedure supplied with SQL*Forms
    and CONCAT is the name of the user exit.  A sample form named
    CONCAT invokes the user exit.
    **************************************************************/

    #define min(a, b) ((a < b) ? a : b)
    #include <stdio.h>
    #include <string.h>

    /* Include the SQL Communications Area, a structure through which
     * Oracle makes runtime status information such as error
     * codes, warning flags, and diagnostic text available to the
     * program.
     */
    #include <sqlca.h>

    /* All host variables used in embedded SQL in this example
     * appear in the Declare Section.
     */
    EXEC SQL BEGIN DECLARE SECTION;
        VARCHAR   field[81];
        VARCHAR   value[81];
        VARCHAR   result[241];
    EXEC SQL END DECLARE SECTION;

    /* Define the user exit, called "concat". */
    int concat(cmd, cmdlen, msg, msglen, query)
    char *cmd;     /* command line in trigger step ("CONCAT...") */
    int  *cmdlen;  /* length of command line */
    char *msg;     /* trigger step failure message from form */
    int  *msglen;  /* length of failure message */
    int  *query;   /* TRUE if invoked by post-query trigger,
                      FALSE otherwise */
    {
        char *cp = cmd + 7;    /* pointer to field list in
                                  cmd string; 7 characters
                                  are needed for "CONCAT " */
        char *fp = (char*)&field.arr[0];  /* pointer to a field name in
                                             cmd string */
        char  errmsg[81];      /* message returned to SQL*Forms
                                  on error */
        int   errlen;          /* length of message returned
                                  to SQL*Forms */

    /* Branch to label sqlerror if an ORACLE error occurs. */
        EXEC SQL WHENEVER SQLERROR GOTO sqlerror;

        result.arr[0] = '\0';

    /* Parse field names from cmd string. */
        for (; *cp != '\0'; cp++)
        {
           if (*cp != ',' && *cp != ' ')
               /* Copy a field name into field.arr from cmd. */
           {
               *fp = *cp;
               fp++;
           }
           else
               if (*cp == ' ')
               {   /* Have whole field name now. */
                   *fp = '\0';
                   field.len = strlen((char *) field.arr);
                   /* Get field value from form. */
                   EXEC TOOLS GET :field INTO :value;
                   value.arr[value.len] = '\0';
                   strcat((char *) result.arr, (char *) value.arr);
                   fp = (char *)&field.arr[0];  /* Reset field pointer. */
               }
        }

    /* Have last field name now. */
        *fp = '\0';
        field.len = strlen((char *) field.arr);
        result.len = strlen((char *) result.arr);

    /* Put result into form. */
        EXEC TOOLS PUT :field VALUES (:result);

    /* Trigger step succeeded. */
        return(IAPSUCC);

    sqlerror:
        strcpy(errmsg, "CONCAT: ");
        strncat(errmsg, sqlca.sqlerrm.sqlerrmc, min(72,
            sqlca.sqlerrm.sqlerrml));
        errlen = strlen(errmsg);
    /* Pass error message to SQL*Forms status line. */
         EXEC TOOLS MESSAGE :errmsg ;
        return(IAPFAIL);  /* Trigger step failed. */
    }

### 20.12 About Using the GENXTB Utility

The IAP program table IAPXTB in module IAPXIT contains an entry for each user exit linked into IAP. IAPXTB tells IAP the name, location, and host language of each user exit. When you add a new user exit to IAP, you must add a corresponding entry to IAPXTB. IAPXTB is derived from a database table, also named IAPXTB. You can modify the database table by running the GENXTB form on the operating system command line, as follows:

    RUNFORM GENXTB username/password

A form is displayed for you to enter the following information for each user exit you define:

- Exit name

- C-language code

- Date created

- Date last modified

- Comments

After modifying the IAPXTB database table, use the GENXTB utility to read the table and create an Assembler or C source program that defines the module IAPXIT and the IAPXTB program table it contains. The source language used depends on your operating system. The syntax you use to run the GENXTB utility is

    GENXTB username/password outfile

where outfile is the name you give the Assembler or C source program that GENXTB creates.

**Related Topics**

- Guidelines

### 20.13 About Linking a User Exit into SQL\*Forms

Before running a form that calls a user exit, you must link the user exit into IAP, the SQL\*Forms component that runs a form. The user exit can be linked into your standard version of IAP or into a special version for those forms that call the exit.

To produce a new executable copy of IAP, link your user exit object module, the standard IAP modules, the IAPXIT module, and any modules needed from the Oracle and C link libraries.

The details of linking are system-dependent. Check the Oracle installation or user's guide for your system.

### 20.14 Guidelines

The guidelines in this section will help you avoid some common problems.

#### 20.14.1 About Naming the Exit

The name of your user exit cannot be an Oracle reserved word. Also avoid using names that conflict with the names of SQL\*Forms commands, function codes, and externally defined names used by SQL\*Forms. The name of the user exit entry point in the source code becomes the name of the user exit itself. The exit name must be a valid C function name, and a valid filename for your operating system.

SQL\*Forms converts the name of a user exit to upper case before searching for the exit. Therefore, the exit name must be in upper case in your source code.

#### 20.14.2 About Connecting to Oracle

User exits communicate with Oracle using the connection made by SQL\*Forms. However, a user exit can establish additional connections to any database using Oracle Net Services.

**Related Topics**

- [Advanced Connection Options](database-concepts.md)

#### 20.14.3 About Issuing I/O Calls

File I/O is supported but screen I/O is not.

#### 20.14.4 About Using Host Variables

Restrictions on the use of host variables in a standalone program also apply to user exits. Host variables must be prefixed with a colon in EXEC SQL and EXEC TOOLS statements. The use of host arrays is not allowed in EXEC TOOLS statements.

#### 20.14.5 About Updating Tables

Generally, a user exit should not UPDATE database tables associated with a form. For example, suppose an operator updates a record in the SQL\*Forms work space, then a user exit UPDATEs the corresponding row in the associated database table. When the transaction is COMMITted, the record in the SQL\*Forms work space is applied to the table, overwriting the user exit UPDATE.

#### 20.14.6 About Issuing Commands

Avoid issuing a COMMIT or ROLLBACK command from your user exit because Oracle will commit or roll back work begun by the SQL\*Forms operator, not just work done by the user exit. Instead, issue the COMMIT or ROLLBACK from the SQL\*Forms trigger. This also applies to data definition commands (such as ALTER, CREATE, and GRANT) because they issue an implicit COMMIT before and after executing.
