This chapter provides information about creating OLAP DML programs. It includes the following topics:

- Programs Provided With the OLAP DML

- Creating OLAP DML Programs

- Specifying Program Contents

- Compiling Programs

- Testing and Debugging Programs

- Executing Programs

- Common Types of OLAP DML Programs

- User-Written Programs Looked For by Oracle OLAP

### 6.1 Programs Provided With the OLAP DML

The OLAP DML provides a number of programs that you can use to work with OLAP cubes and cube dimensions as previously defined in the Oracle Database data dictionary. These programs are listed in "[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)".

It also provides the following programs that work directly on the analytic workspace:

- [ALLCOMPILE](olap-dml-commands-a-g.md) which uses the COMPILE command to compile every compilable object in your current analytic workspace, one at a time.

- [ALLSTAT](olap-dml-commands-a-g.md) sets the status of all dimensions in the current analytic workspace to the default status list of the dimension.

- [AWDESCRIBE](olap-dml-commands-a-g.md) sends information about the current analytic workspace to the current outfile. After a summary page, it provides a report in two parts: An alphabetic list of analytic workspace objects showing name, type, and description; and a DESCRIBE of each object by object type.

- [COPYDFN](olap-dml-commands-a-g.md) defines a new object in the analytical workspace by copying the definition from an already-defined object in the current workspace or in an attached workspace.

- [FORECAST.REPORT](olap-dml-commands-a-g.md) produces a standard report of a forecast created using the FORECAST command. The report shows the parameters of the forecast, including the forecast formula and Mean Absolute Percent Error, followed by a display of the forecasted values.

- [FULLDSC](olap-dml-commands-a-g.md) produces a report that lists the definition of one or more workspace objects, including the properties and triggers of the object(s).

- [ISDATE](olap-dml-functions-a-k.md) determines whether a text expression to see if it can be converted to a DATE value It returns YES when the text expression represents a valid date; NO when it does not. (Note that, ISDATE does not actually make the conversion. You must use CONVERT to make the conversion.)

- [LISTBY](olap-dml-commands-h-z.md) produces a report of the names of all objects in an analytic workspace that are dimensioned by or related to one or more specified dimensions or composites. You can use LISTBY with a dimension or composite in any attached workspace.

- [LISTNAMES](olap-dml-commands-h-z.md) produces a report that lists the names of the objects in an analytic workspace. You can limit the list to particular types of objects, and you can have the names for each type of object listed in alphabetical order.

- [MODEL.COMPRPT](olap-dml-commands-h-z.md) produces a report that shows how model equations are grouped into blocks. For step blocks and for simultaneous blocks with a cross-dimensional dependence, the report lists the dimensions involved in the dependence.

- [MODEL.DEPRT](olap-dml-commands-h-z.md) produces a report that lists the variables and dimension values on which each model equation depends. When a dependence is dimensional, the report gives the name of the dimension.

- [MODEL.XEQRPT](olap-dml-commands-h-z.md) produces a report about the execution of the model. The report specifies the block where the solution failed and shows the values of the model options that were used in solving simultaneous blocks.

- [PAGE](olap-dml-commands-h-z.md), commonly used in report programs or with LISTNAMES, forces a page break in output when PAGING is set to `YES`. An optional argument to PAGE specifies a conditional page break based on how many lines are left on the page.

- [REGRESS.REPORT](olap-dml-commands-h-z.md) produces a standard report of a regression performed using the REGRESS command.

- [STATUS](olap-dml-commands-h-z.md) sends to the current outfile the status of one or more dimensions, dimension surrogates, or valuesets, or the status of all dimensions in an analytic workspace.

- [STDHDR](olap-dml-commands-h-z.md) generates the standard Oracle OLAP heading at the top of every page of report output.

- [VALSPERPAGE](olap-dml-functions-l-z.md) calculates the maximum number of values for a variable of a specified width that fits on one page. Pages are units of storage in the workspace.

Because the ISDATE and VALSPERPAGE programs are like simple functions, they are documented in alphabetical sequence along with OLAP DML functions in [OLAP DML Functions: A - K](olap-dml-functions-a-k.md) and [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md). The other programs provided with the OLAP DML are documented in alphabetical sequence along with the OLAP DML commands in [OLAP DML Commands: A-G](olap-dml-commands-a-g.md) and [OLAP DML Commands: H-Z](olap-dml-commands-h-z.md).

### 6.2 Creating OLAP DML Programs

An OLAP DML program is written in the OLAP DML. It acts on data in the analytic workspace and helps you accomplish some workspace management or analysis task. You can write OLAP DML programs to perform tasks that you must do repeatedly in the analytic workspace, or you can write them as part of an application that you are developing.

To create an OLAP DML program, take the following steps:

1.  Issue a DEFINE PROGRAM statement to define the program object. When the program that you are defining is used is a function, include the `datatype` or the `dimension` argument.
2.  Add contents to the program that specify the processing that you want performed as described in "Specifying Program Contents".
3.  Compile the program as described in "Compiling Programs".
4.  Test and debug the program as described in "Testing and Debugging Programs".
5.  Execute the program as described in "Executing Programs".

### 6.3 Specifying Program Contents

The content of a program consists of the following OLAP DML statements:

1.  A PROGRAM statement that indicates the beginning of the program contents. (Omit when coding the specification in an Edit window of the OLAP Worksheet.)

2.  (Optional) VARIABLE statements that define any local variables.

3.  (Optional) ARGUMENT statements that declare arguments. (See "Passing Arguments" for more information.)

4.  Additional OLAP DML statements that specify the processing you want performed. You can use almost any of the OLAP DML statements in a program. There are also some OLAP DML statements, such as flow-of-control statements, that are only used in programs.

    Use the following formatting guidelines as you add lines to your program:

    - Each line of code can have a maximum of 4,000 bytes.

    - To continue a single statement on the next line, place a hyphen (`-`) at the end of the line to be broken. The hyphen is called a continuation character.

    - You cannot use a continuation character in the middle of a text literal.

    - To write multiple statements on a single line, separate the statements with semicolon (`;`).

    - Enclose literal text in single quotation marks (`'`). To include a single quotation mark within literal text, precede it with a backslash (`\`). To specify escape sequences, see "[Escape Sequences](data-types-operators-and-expressions.md)".

    - Precede comments with double quotation marks (`"`). You can place a comment, preceded by double quotation marks, either at the beginning of a line or at the end of a line, after some statements.

5.  A final END statement that indicates the end of the contents of the program. (Omit when coding the specification in an Edit window of the OLAP Worksheet.)

#### 6.3.1 Creating User-Defined Functions

One type of program that is commonly written is a user-define function that you can use in OLAP DML statements in much the same way as you use an OLAP DML function. A user-defined function is simply an OLAP DML program that returns a value. For an example of a user-defined function, see [Example 9-44](olap-dml-commands-a-g.md).

When you create a user‐defined function, you use a DEFINE PROGRAM statement that includes the `datatype` and `dimension` arguments. Within the program, you include a RETURN statement that returns a value. The return expression in the program should match the data type that is specified in its definition. When the data type of the return value does not match the data type that is specified in its definition, then the value is converted to the data type in the definition.

User-defined functions can accept arguments. A user-defined function returns only a single value. However, when you supply an argument to a user‐defined function in a context that loops over a dimension (for example, in a REPORT statement), then the function returns results with the same dimensions as its argument.

You must declare the arguments using an ARGUMENT statement within the program, and you must specify the arguments in parentheses following the name of the program.

**See Also:**

"Passing Arguments" for more information about using arguments with programs.

#### 6.3.2 Passing Arguments

Use ARGUMENT statements to declare both simple and complex arguments (such as expressions). ARGUMENT statement also make it convenient to pass arguments from one program to another, or to create your own user‐defined functions because by using these statements you can declare an argument of any data type, dimension, or valueset. Any ARGUMENT statements must precede the first executable line in the program. When you run the program, these declared arguments are initialized with the values you provided as arguments to the program. The program can then use these arguments in the same way it would use local variables.

##### 6.3.2.1 Using Multiple Arguments

A program can declare as many arguments as needed. When the program is executed with arguments specified, the arguments are matched positionally with the declared arguments in the program. When you run the program, you must separate arguments with spaces rather than with commas or other punctuation. Punctuation is treated as part of the arguments. For an example of passing multiple arguments, see [Example 9-45](olap-dml-commands-a-g.md).

##### 6.3.2.2 Handling Arguments Without Converting Values to a Specific Data Type

Sometimes you want your OLAP DML program to be able to handle arguments without converting values to a specific data type. In this case, you can specify a data type of `WORKSHEET` in the ARGUMENT and VARIABLE statements that define the arguments and temporary variables for the program. You can use WKSDATA to determine the actual data type of the argument or variable.

##### 6.3.2.3 Passing Arguments as Text with Ampersand Substitution

It is very common to pass a simple text argument to a program. However, there are some situations in which you might want to write more general programs or pass a more complicated text argument, such as an argument that is all of the data in an analytic workspace object or the results of an expression. In these cases, you can pass the argument using a substitution expression. Passing an argument in this way is called ampersand substitution.

For the following types of arguments, you must always use an ampersand to make the appropriate substitution:

- Names of workspace objects, such as `units` or `product`

- Statement keywords, such as `COMMA` or `NOCOMMA` in the REPORT` `statement, or `A` or `D` in the SORT command

When you use ampersand substitution to pass the names rather than the values of workspace objects to a program, the program has access to the objects themselves. This feature is useful when the program must manipulate the objects in several operations.

**Note:**

You cannot compile and save any program line that contains an ampersand. Instead, the line is evaluated at run time, which can reduce the speed of your programs. Therefore, to maximize performance, avoid using ampersand substitution when another technique is available.

For an example of using ampersand substitution to pass multiple dimension values, see [Example 10-18](olap-dml-commands-h-z.md). For an example of using ampersand substitution to pass the text of an expression, see [Example 9-47](olap-dml-commands-a-g.md). For an example of using ampersand substitution to pass object names and keywords, see [Example 9-48](olap-dml-commands-a-g.md).

**See Also:**

"[Substitution Expressions](data-types-operators-and-expressions.md)" for more information about ampersand substitution.

#### 6.3.3 Program Flow-of-Control

Like most programming languages, the OLAP DML has several statements that you can use to determine the flow-of-control within a program. However, you must code explicit loops less frequently in an OLAP DML program because of the intrinsic looping nature of many OLAP DML statements.

The following table lists OLAP DML flow-of-control statements. The looping characteristic of OLAP DML statements is discussed in "[OLAP DML Statements Apply to All of the Values of a Data Object](olap-dml-basic-concepts.md)".

The OLAP DML contains the flow-of-control statements typically found in a programming language. The following table lists these statements:

Table 6-1 Statements For Determining Flow-of-Control

| Statement                                            | Description                                                                                                                                                                                                                                                                                                          |
|:-----------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [BREAK](olap-dml-commands-a-g.md)                    | Transfers program control from within a SWITCH, FOR, or WHILE statement to the statement immediately following the DOEND associated with SWITCH, FOR, or WHILE.                                                                                                                                                      |
| [CONTINUE](olap-dml-commands-a-g.md)                 | Transfers program control to the end of a FOR or WHILE loop (just before the DO/DOEND statement), allowing the loop to repeat. You can use CONTINUE only within programs and only with FOR or WHILE.                                                                                                                 |
| [DO ... DOEND](olap-dml-commands-a-g.md)             | Brackets a group of one or more statements. DO and DOEND are normally used to bracket a group of statements that are to be executed under a condition specified by an IF statement, a group of statements in a repeating loop introduced by FOR or WHILE, or the CASE labels for a SWITCH statement.                 |
| [FOR](olap-dml-commands-a-g.md)                      | Specifies one or more dimensions whose status controls the repetition of one or more statements.                                                                                                                                                                                                                     |
| [GOTO](olap-dml-commands-a-g.md)                     | Alters the sequence of statement execution within the program by indicating the next program statement to execute.                                                                                                                                                                                                   |
| [IF...THEN...ELSE command](olap-dml-commands-h-z.md) | Executes one or more statements in a program if a specified condition is met. Optionally, it also executes an alternative statement or group of statements when the condition is not met.                                                                                                                            |
| [OKFORLIMIT](olap-dml-options.md)                    | An option that determines whether you can limit the dimension you are looping over within an explicit FOR loop.                                                                                                                                                                                                      |
| [RETURN](olap-dml-commands-h-z.md)                   | Terminates execution of a program before its last line. You can optionally specify a value that the program returns.                                                                                                                                                                                                 |
| [SIGNAL](olap-dml-commands-h-z.md)                   | Produces an error message and halts normal execution of the program. When the program contains an active trap label, execution branches to the label. Without a trap label, execution of the program terminates and, if the program was called by another program, execution control returns to the calling program. |
| [SWITCH command](olap-dml-commands-h-z.md)           | Provides a multipath branch in a program. The specific path taken during program execution depends on the value of the control expression that is specified with SWITCH.                                                                                                                                             |
| [TEMPSTAT](olap-dml-commands-h-z.md)                 | Limits the dimension you are looping over, inside a FOR loop or inside a loop that is generated by a REPORT statement. Status is restored after the statement following TEMPSTAT. If a DO ... DOEND phrase follows TEMPSTAT, status is restored when the matched DOEND or a BREAK or GOTO statement is encountered.  |
| [TRAP](olap-dml-commands-h-z.md)                     | Causes program execution to branch to a label when an error occurs in a program or when the user interrupts the program. When execution branches to the trap label, that label is deactivated.                                                                                                                       |
| [WHILE](olap-dml-commands-h-z.md)                    | Repeatedly executes a statement while the value of a Boolean expression remains TRUE.                                                                                                                                                                                                                                |

#### 6.3.4 Preserving the Environment Settings

There are two types of environments:

- Session environment. The dimension status, option values, and output destination that are in effect before a program is run constitute the session environment.

- Program environment. The dimension status, option values, and output destination that you use in a program constitute the program environment.

##### 6.3.4.1 Changing the Program Environment

To perform a task within a program, you often must change the output destination or some dimension and option values. For example, you might run a monthly sales report that always shows the last six months of sales data. You might want to show the data without decimal places, include the text "No Sales" where the sales figure is zero, and send the report to a file. To set up this program environment, you can use the following statements in your program.

    LIMIT month TO LAST 6
    DECIMALS = 0
    ZSPELL = 'No Sales'
    OUTFILE monsales.txt

To avoid disrupting the session environment, the initialization section of a program should save the values of the dimensions and options that are set in the program. After the program executes, you can restore the saved environment, so that other programs do not need to be concerned about whether any values have been changed. In addition, when you have sent output to a file, then the exit sections should return the output destination to the default outfile.

##### 6.3.4.2 Ways to Save and Restore Environments

The following suggestions let you save the environment of a program or a session:

- When you want to save the current status or value of a dimension, a valueset, an option, or a single-cell variable that is changed in the current program, then use PUSHLEVEL and PUSH statements. You can restore the current status values using POPLEVEL and POP statements.

- When you want to save, access, or update the current status or value of a dimension, a valueset, an option, a single-cell variable, or a single-cell relation for use in the current session, then use a named context. Use the CONTEXT command to define the context.

Contexts are the most sophisticated way to save object values for use during a session. With contexts, you can access, update, and commit the saved object values. In contrast, PUSH and POP simply allow you to save and restore values. Typically, you use PUSH and POP statements within a program to make changes that apply only during the execution of the program.

##### 6.3.4.3 Saving the Status of a Dimension or the Value of an Option

A PUSH statement saves the current status of a dimension, the value of an option, or the value of a single-cell variable. For example, to save the current value of the `DECIMALS` option so you can set it to a different value for the duration of the program, use the following statement in the initialization section.

    PUSH DECIMALS

You do not need to know the original value of the option to save it or to restore it later. You can restore the saved value with a POP statement.

    POP DECIMALS

You must make sure a POP statement is executed when errors cause abnormal termination of the program and when the program ends normally. Therefore, place the POP statement in the normal and abnormal exit sections of the program.

##### 6.3.4.4 Saving Several Values at Once

You can save the status of one or more dimensions and the values of any number of options and variables in a single PUSH statement, and you can restore the values with a single POP statement, as shown in the following example.

    PUSH month DECIMALS ZSPELL
           ...
    POP month DECIMALS ZSPELL

##### 6.3.4.5 Using Level Markers

When you are saving the values of several dimensions and options, then PUSHLEVEL and POPLEVEL statements provide a convenient way to save and restore the session environment.

You first use a PUSHLEVEL statement to establish a level marker. Once the level marker is established, you use a PUSH statement to save the status of dimensions and the values of options or single-cell variables.

When you place multiple PUSH statements between the PUSHLEVEL and POPLEVEL statements, then all the objects that are specified in those PUSH statements are restored with a single POPLEVEL statement.

By using PUSHLEVEL and POPLEVEL, you save some typing as you write your program because you must only type the list of objects once. You also reduce the risk of omitting an object from the list or misspelling the name of an object.

For an example of creating level markers, see [Example 10-85](olap-dml-commands-h-z.md). [Example 10-86](olap-dml-commands-h-z.md) illustrates nesting PUSHLEVEL and POPLEVEL statements.

##### 6.3.4.6 Using CONTEXT to Save Several Values at Once

As an alternative to using PUSHLEVEL and POPLEVEL, you can use the CONTEXT command. After you create a context, you can save the current status of dimensions and the values of options, single-cell variables, valuesets, and single-cell relations in the context. You can then restore some or all of the object values from the context. The CONTEXT function returns information about objects in a context.

#### 6.3.5 Handling Errors

When an error occurs anywhere in a program, Oracle OLAP performs the following actions:

1.  Stores the name of the error in the ERRORNAME option, and the text of the error message in the ERRORTEXT option.

    **Note:**

    When the ERRNAMES option is set to the default value of `YES`, the ERRORTEXT option contains the name of the error (that is, the value of the ERRORNAME option) and the text of the error message.

2.  When ECHOPROMPT is `YES`, then Oracle OLAP echoes input lines, error messages, and output lines, to the current outfile. When you use the OUTFILE or DBGOUTFILE statement, you can capture the error messages in a file. See [Example 10-69](olap-dml-commands-h-z.md) for an example of directing output to a file.

3.  When error trapping is off, then the execution of the program is halted. When error trapping is on, then the error is trapped.

##### 6.3.5.1 Trapping an Error

To make sure the program works correctly, anticipate errors and set up a system for handling them. You can use a TRAP statement to turn on an error-trapping mechanism in a program. When error trapping is on and an error is signaled, then the execution of the program is not halted. Instead, error trapping does the following:

1.  Turns off the error‐trapping mechanism to prevent endless looping in case additional errors occur during the error-handling process

2.  Branches to the label that is specified in the `TRAP` statement

3.  Executes the statements following the label

##### 6.3.5.2 Passing an Error to a Calling Program

To pass an error to a calling program, you can use one of two methods. The method you use depends on when you want the error message to be produced. With the first method, Oracle OLAP produces the message immediately and then the error condition is passed through the chain of programs. With the second method, Oracle OLAP passes the error through the chain of programs first and then produces the message. See "Passing an Error: Method One" and "Passing an Error: Method Two" for details.

With both methods, the appropriate error handling happens in each program in the chain, and at some point Oracle OLAP sends an error message to the current outfile.

###### 6.3.5.2.1 Passing an Error: Method One

Using this method, Oracle OLAP produces the message immediately and then the error condition is passed through the chain of programs.

Use a TRAP statement with the (default) PRINT option. When an error occurs, Oracle OLAP produces an error message, and execution branches to the trap label. After the trap label, perform whatever cleanup you want, and then execute the following statement.

    SIGNAL PRGERR

Using this statement creates an error condition that is passed up to the program from which the current program was run. However, PRGERR does not produce an error message. PRGERR sets the ERRORNAME option to a blank value.

When the calling program contains a trap label, execution branches to the label. When each of the programs in a sequence of nested programs uses TRAP and SIGNAL in this way, you can pass the error condition up through the entire sequence of programs.

###### 6.3.5.2.2 Passing an Error: Method Two

Using this method, Oracle OLAP passes the error through the chain of programs first and then produces the message.

Use a TRAP statement with the NOPRINT option. When an error occurs, execution branches to the trap label, but the error message is suppressed. After the trap label, perform whatever cleanup you want, then execute the following statement.

    SIGNAL ERRORNAME ERRORTEXT

The options ERRORNAME and ERRORTEXT contain the name and message of the original error, so this SIGNAL statement reproduces the original error. The error is then passed up to the program from which the current program was run.

When the calling program also contains a trap label, execution branches to its label. When each of the programs in a sequence of nested programs uses `TRAP...NOPRINT` and `SIGNAL` `ERRORNAME` `ERRORTEXT` in this way, you can pass the error condition up through the entire sequence of programs. Oracle OLAP produces the error message at the end of the chain.

When you reach a level where you want to handle the error and continue the application, omit the SIGNAL statement. You can display your own message with a SHOW statement.

##### 6.3.5.3 Suppressing Error Messages

When you do not want to produce the error message that is normally provided for a given error, then you can use TRAP statement with a `NOPRINT` keyword.

    TRAP ON error NOPRINT

When you use the `NOPRINT` keyword with `TRAP`, control branches to the `error` label, and an error message is not issued when an error occurs. The statements following the `error` label are then executed.

When you suppress the error message, you might want to produce your own message in the abnormal exit section. A `SHOW` statement produces the text you specify but does not signal an error.

    TRAP ON error NOPRINT
            ...
    error:
            ...
    SHOW 'The report will not be produced.'

The program continues with the next statement after producing the message.

##### 6.3.5.4 Creating Your Own Error Messages

All errors that occur when a statement or statement sequence does not conform to its requirements are signaled automatically. In your program, you can establish additional requirements for your own application. When a requirement is not met, you can execute a `SIGNAL` statement to signal an error.

You can give the error any name. When a `SIGNAL` statement is executed, the error name you specify is stored in the `ERRORNAME` option, just as an OLAP DML error name is automatically stored. When you specify your own error message in a `SIGNAL` statement, then your message is produced just as an OLAP DML error message is produced. When you are using a `TRAP` statement to trap errors, a `SIGNAL` statement branches to the `TRAP` label after the error message is produced.

For an example of signaling an error, see [Example 10-123](olap-dml-commands-h-z.md).

When you want to produce a warning message without branching to an error label, then you can use a `SHOW` statement as illustrated in [Example 10-121](olap-dml-commands-h-z.md).

##### 6.3.5.5 Handling Errors in Nested Programs

When handling errors in nested programs, the error-handling section in each program should restore the environment. It can also handle any special error conditions that are particular to that program. For example, when your program signals its own error, then you can include statements that test for that error.

Any other errors that occur in a nested program should be passed up through the chain of programs and handled in each program. To pass errors through a chain of nested programs, you can use one of two methods, depending on when you want the error message to be produced:

- The error message is produced immediately, and the error condition is then passed through the chain of programs as illustrated in [Example 10-157](olap-dml-commands-h-z.md).

- The error is passed through the chain of programs first, and the error message is produced at the end of the chain as illustrated in[Example 10-158](olap-dml-commands-h-z.md).

A `SIGNAL` statement is used in both methods.

##### 6.3.5.6 Handling Errors While Saving the Session Environment

To correctly handle errors that might occur while you are saving the session environment, place your `PUSHLEVEL` statement before the `TRAP` statement and your `PUSH` statements after the `TRAP` statement.

    PUSHLEVEL 'firstlevel'
    TRAP ON error
    PUSH
     ...

In the abnormal exit section of your program, place the error label (followed by a colon) and the statements that restore the session environment and handle errors. The abnormal exit section might look like this.

    error:
    POPLEVEL 'firstlevel'
    OUTFILE EOF

These statements restore saved dimension status and option values and reroute output to the default outfile.

### 6.4 Compiling Programs

You can explicitly compile a program by using a `COMPILE` statement. If you do not explicitly compile a program, then it is compiled when you run the program for the first time.

When a program is compiled, it translates the program statements into efficient processed code that executes much more rapidly than the original text of the program. When errors are encountered in the program, then the compilation is not completed, and the program is considered to be uncompiled.

After you compile a program, the compiled code is used each time you run the program in the current session. When you update and commit your analytic workspace after compiling a program, the compiled code is saved in your analytic workspace and used to run the program in future sessions. Therefore, be sure to update and commit after compiling a program. Issuing an update and commit after program compilation is particularly critical when the program is part of an application that is run by many users. Unless the compiled version of the program is saved in the analytic workspace, the program is recompiled individually in each user session.

[Example 9-69](olap-dml-commands-a-g.md) illustrates using COMPILE to compile a program

#### 6.4.1 Finding Out If a Program Has Been Compiled

You can use the `ISCOMPILED` choice of the `OBJ` function to determine whether a specific program in your analytic workspace has been compiled since the last time it was modified. The function returns a Boolean value.

    SHOW OBJ(ISCOMPILED 'myprogram')

#### 6.4.2 Programming Methods That Prevent Compilation

Program lines that include ampersand substitution are not compiled. Any syntax errors are not caught until the program is run. A program whose other lines compiled correctly is considered to be a compiled program.

When your program defines an object and then uses the object in the program, the program cannot be compiled. `COMPILE` treats the reference to the object as a misspelling because the object does not yet exist in the analytic workspace.

### 6.5 Testing and Debugging Programs

Even when your program compiles cleanly, you must also test the program by running it. Running a program helps you detect errors in statements with ampersand substitution, errors in logic, and errors in any nested programs.

To test a program by running it, use a full set of test data that is typical of the data that the program processes. To confirm that you test all the features of the program, including error-handling mechanisms, run the program several times, using different data and responses. Use test data that:

- Falls within the expected range

- Falls outside the expected range

- Causes each section of a program to execute

#### 6.5.1 Generating Diagnostic Messages

Each time you run the program, confirm that the program executes its statements in the correct sequence and that the output is correct. As an aid in analyzing the execution of your program, you can include `SHOW` or TRACE statements in the program to produce diagnostic or status messages. Then delete the `these` statements after your tests are complete.

When you detect or suspect an error in your program or a nested program, you can track down the error by using the debugging techniques that are described in the rest of this section.

#### 6.5.2 Identifying Bad Lines of Code

When you set the BADLINE option to `YES`, additional information is produced, along with any error message when a bad line of code is encountered. When the error occurs, the error message, the name of the program, and the program line that triggered the error are sent to the current outfile. You can edit the specified program to correct the error and then run the original program. See [Example 5-4](olap-dml-options.md) for an example of using BADLINE.

#### 6.5.3 Sending Output to a Debugging File

When your program contains an error in logic, then the program might execute without producing an error message, but it executes the wrong set of statements or produces incorrect results. For example, suppose you write a Boolean expression incorrectly in an `IF` statement (for example, you use `NE` instead of `EQ`). The program executes the statements you specified, but it does so under the wrong conditions.

To find an error in program logic, you must often see the order in which the statements are being executed. One way you can do this is to create a debugging file and then examine the file to diagnose any problems in your programs by issuing the following DML statements:

1.  Create a debugging file, by issuing an DBGOUTFILE statement.

2.  Specify that you want each program line to be sent to the debugging file when a line executes by setting the PRGTRACE option to `YES`.

3.  (Optional) When you want the debugging file to interweave the program lines with both the program input and error messages, set the ECHOPROMPT option to `YES`.

**See Also:**

The following examples of using a debugging file:

- [Example 9-76](olap-dml-commands-a-g.md)

- [Example 9-77](olap-dml-commands-a-g.md)

### 6.6 Executing Programs

You can invoke a program that does not return a value by using a CALL statement. You enclose arguments in parentheses, and they are passed by value. For example, suppose you create a simple program named `addit` to add two `INTEGER` values. You can use a CALL statement in the main program of your application to invoke the program.

You can also invoke programs in much the same way as you issue OLAP DML statements. You invoke user-defined functions in the same way as you use built-in functions. You use the program name in an expression and enclose the program arguments, if any, in parentheses. For a program that does not return a value (a user-defined command), you use the program name as you would an OLAP DML command. When you invoke a user-defined program as a function, the program returns `NA`.

You can also create programs that execute automatically when Oracle OLAP:

- Executes an AW ATTACH. AW CREATE, AW DELETE, AW DETACH, DEFINE, MAINTAIN, PROPERTY, UPDATE, or SET statement as described in "Trigger Programs".

- Encounters an `NA` value as described in \$NATRIGGER.

### 6.7 Common Types of OLAP DML Programs

This section provides overview information about the following types of programs:

- Startup Programs

- Data Import and Export Programs

- Trigger Programs

- Aggregation, Allocation, and Modeling Programs

- Forecasting Programs

- Programs to Export and Import Workspace Objects

#### 6.7.1 Startup Programs

Startup programs are programs that you write and that Oracle OLAP checks for by name when an AW ATTACH statement executes. Startup programs do not exist within an analytic workspace unless you define and write them. In a startup program you can execute any OLAP DML statements, or run any of your own programs. For example, a startup program might set options to values appropriate to your application.

When you first attach an analytic workspace, Oracle OLAP looks for and executes the Oracle OLAP startup programs (if they exist) in the order indicated:

1.  Permission programs. The execution of a permission program is determined by the attachment mode specified in the AW ATTACH statement and whether or not a related permission program exists in the analytic workspace you are attaching. For more information, see "Permission Programs".

2.  OnAttach programs. The execution of an OnAttach program is determined by how you code the ONATTACH and NOONATTACH clauses of the AW ATTACH statement and whether or not a program named ONATTACH exists in the analytic workspace you are attaching. For more information, see "OnAttach Programs".

3.  Autogo programs. The execution of an Autogo program is determined by how you code the AUTOGO and NOAUTOGO clauses of the AW ATTACH statement and whether or not a program named AUTOGO exists in the analytic workspace you are attaching. For more information, see "Autogo Programs".

4.  Trigger program. The execution of a Trigger program is determined by whether or not a program named TRIGGER_AW exists in an already attached analytic workspace. When a TRIGGER_AW program exists in one attached analytic workspace, it is executed whenever you create, attach, detach, or delete any other analytic workspace. For more information, see "Trigger Programs" and TRIGGER_AW.

**Note:**

Within a session, when you:

- Reattach an attached workspace, Oracle OLAP does not look for and execute permission programs and OnAttach programs.

- Reattach a previously detached workspace, Oracle OLAP does not execute permission programs, OnAttach programs, or Autogo programs, unless you detached that workspace using an AW DETACH statement that included the NOCACHE keyword .

##### 6.7.1.1 Permission Programs

Permission programs are programs that you write that give permission to users to access workspace data. When a user first attaches an analytic workspace, Oracle OLAP checks to see if a permission program that is appropriate for the attachment mode exists.

**Note:**

When you reattach an attached workspace, Oracle OLAP does not look for and execute permission programs.

The permission program for each attachment mode must have a particular name as outlined in the following table:

Table 6-2 Names of Permission Programs for Different Attachment Modes

| Attachment Modes        | Name of Program |
|:------------------------|:----------------|
| Read-only               | PERMIT_READ     |
| Multiwriter, Read/write | PERMIT_WRITE    |

When an appropriate permission program exists, Oracle OLAP executes the program. When a user specifies a password when attaching the analytic workspace, then the password is passed as an argument to the permission program for processing.

**Note:**

A dimension surrogate has the access permissions of its dimension. Use a PERMIT on a dimension to grant or deny permission to access the values of a dimension surrogate for that dimension.

Permission programs allow you to control two levels of access to the analytic workspace in which they reside.

- Access at the analytic workspace level—Depending on the return value of the permission program, the user is or is not granted access to the entire analytic workspace. You can use the return value to indicate to Oracle OLAP whether or not the user has the right to attach the workspace.

- Access at the object level—Within a permission program for read-only or read/write attachment, you can specify PERMIT statements that grant or restrict access to individual workspace objects. PERMIT programs must be in the same workspace as the objects for which they issue PERMIT statements.

  **Note:**

  All of the objects referred to in a given permission program must exist in the same analytic workspace.

To create a permission program, define a user-defined function (as described in "Creating User-Defined Functions") with a recognized name, then define the contents for the program as described in "Specifying Program Contents".

##### 6.7.1.2 OnAttach Programs

An OnAttach program can have any name or it can explicitly be named `ONATTACH`.

**Note:**

When an analytic workspace is created as an OLAP cube using the OLAP API, the OLAP API may also create a program named `ONATTACH`. You cannot modify an `ONATTACH` program that is automatically created in this way. Additionally, overriding the execution of `ONATTACH` is not recommended.

Consequently, when this type of `ONATTACH` program exists in an analytic workspace, create a different type of startup program to specify behavior that you want performed when that analytic workspace is attached.

How you specify the execution of an OnAttach program varies depending on its name:

- When a program named `ONATTACH`. exists in an analytic workspace, each time you attach the workspace, that program executes automatically unless you include a NOOTTACH keyword in the AW ATTACH statement, or unless you include an ONATTACH clause that specifies a different program name.

- To execute an OnAttach program that is not named `ONATTACH`, specify the name of the program within the ONATTACH clause of [AW ATTACH](olap-dml-commands-a-g.md) statement.

**Note:**

When you reattach an attached cached workspace, Oracle OLAP does not look for and execute OnAttach programs. To force an analytic worksapce to be fully detached so that Oracle OLAP will look for and execute OnAttach programs when you retach the workspace, specify the NOCACHE keyword in the DETACH statement that detaches the analytic workspace.

##### 6.7.1.3 Autogo Programs

An Autogo program can have any name or it can explicitly be named `AUTOGO`.

How you specify the execution of an Autogo program varies depending on its name:

- When a program named AUTOGO exists in an analytic workspace, each time you attach the workspace, that program executes automatically unless you include a NOAUTOGO keyword in the AW ATTACH statement, or unless you include an AUTOGO clause that specifies a different program name.

- To execute an Autogo program that is not named `AUTOGO`, specify the name of the program within the AUTOGO clause of [AW ATTACH](olap-dml-commands-a-g.md) statement.

#### 6.7.2 Data Import and Export Programs

The OLAP DML provides support for importing data from relational tables, flat files, and spreadsheets into analytic workspace objects; and for exporting data from analytic workspace objects to relational tables, flat files, and spreadsheets.

##### 6.7.2.1 Importing Data to and Exporting Data from Relational Tables

You can embed SQL statements in OLAP DML programs using the OLAP DML SQL statement. Using the OLAP DML SQL statement you can import data from relational tables into analytic workspace objects and export data from analytic workspace objects to relational tables.

###### 6.7.2.1.1 Importing Data From Relational Tables to Workspace Objects

Using the OLAP DML SQL statement within an OLAP DML program you can copy relational data into analytic workspace objects using either an implicit cursor or an explicit cursor:

- To copy data from relational tables into analytic workspace objects using an implicit cursor, use the SQL SELECT statement. You can use this OLAP DML statement interactively in the OLAP Worksheet or within an OLAP DML program.

- To copy data from relational tables into analytic workspace objects using an explicit cursor, use the following statements in the order indicated. You can only use these statements within an OLAP DML program. You cannot use them interactively in the OLAP Worksheet.

  1.  SQL DECLARE CURSOR defines a SQL cursor by associating it with a SELECT statement or procedure.

  2.  SQL OPEN activates a SQL cursor.

  3.  SQL FETCH and SQL IMPORT retrieve and process data specified by a cursor.

  4.  SQL CLOSE closes a SQL cursor.

  5.  SQL CLEANUP cancels a SQL cursor declaration and frees the memory resources of an SQL cursor.

For examples of programs that copy table data into workspace objects, see [SQL FETCH](olap-dml-commands-h-z.md) and [SQL IMPORT](olap-dml-commands-h-z.md).

###### 6.7.2.1.2 Exporting Data from OLAP DML Objects to Relational Tables

Within a program, you can use an OLAP DML SQL statement with the INSERT keyword to copy data from analytic workspace objects into relational tables. Typically, you do this by issuing the following statements in your OLAP DML program:

1.  SQL PREPARE statements, to precompile the INSERT and UPDATE statements.

2.  SQL EXECUTE statements, to execute the statements that you precompiled in Step 1.

##### 6.7.2.2 Importing Data to and Exporting Data from Flat Files

Oracle OLAP provides several statements that you can use to read data from flat files or to write data to flat files. These statements are frequently used together in a special program.

##### 6.7.2.3 Importing Data to and Exporting Data from Spreadsheets

Within an OLAP DML program you can use an IMPORT statement to import data from a spreadsheet into analytic workspace objects. You can use an EXPORT statement to export data from analytic workspace objects into a spreadsheet.

#### 6.7.3 Trigger Programs

DEFINE, MAINTAIN, PROPERTY, SET (=) UPDATE, and AW commands are recognized by Oracle OLAP as events that can trigger the execution of OLAP DML programs.

- Programs triggered by DEFINE, MAINTAIN, PROPERTY, UPDATE, or SET commands, are called object trigger programs and are discussed in this section and in the topic for the [TRIGGER command](olap-dml-commands-h-z.md).

- A program named TRIGGER_AW that is defined within one analytic workspace and which is triggered when another analytic workspace is created, attached, detached or deleted. See the discussion of the "TRIGGER_AW" for more information.

Trigger programs are frequently written to maintain application-specific metadata. Trigger programs have certain characteristics depending on the statement that triggers them. Some trigger programs execute before the triggering statement executes; some after. Oracle OLAP passes arguments to programs triggered by some statements, but not others. Oracle OLAP does not change dimension status before most trigger programs execute, but does change dimension status before some MAINTAIN statements trigger program execution. In most cases, you can give a trigger program any name that you choose, but some events require a program with a specific name. "Characteristics of Object Trigger Programs" discusses these characteristics.

**See Also:**

The following statements:

- [TRIGGER function](olap-dml-functions-l-z.md), [DESCRIBE](olap-dml-commands-a-g.md) command, and [OBJ](olap-dml-functions-l-z.md) function that retrieve information about triggers.

- [USETRIGGERS](olap-dml-options.md) option that you can use to disable all triggers.

##### 6.7.3.1 Creating an Object Trigger Program

Once an object is defined in an analytic workspace, you can create a trigger program for that object by following the following procedure:

1.  Define the program as described in DEFINE PROGRAM.
2.  Determine what to name the program and whether the program can be a user-defined program. (See Table 6-3.) If the program can be a user-defined program, decide whether or not you want to define the trigger program as a user-defined function.
3.  Code the actual program as described in"Specifying Program Contents".
4.  Keep the following points in mind when coding trigger programs:
    - Use Table 6-3 to determine if Oracle OLAP passes values to the program. If it does, use an ARGUMENT statement to declare these arguments in your program and the VARIABLE statement to define program variables for the values. (See Table 6-4 for specific information about the arguments.)

    - A program that is triggered by an Assign event is executed each time Oracle OLAP assigns a value to the object for which the event was defined. Thus, a program triggered by an Assign event is often executed over and over again as the assignment statements loops through an object assigning values. You can use TRIGGERASSIGN to assign a value that is different from the value specified by the assignment statement that triggered the execution of the program.

    - In some cases, Oracle OLAP changes the status of the dimension being maintained when a Maintain event triggers the execution of a program. See Table 6-5 for details

    - Use the CALLTYPE function within a program to identify that the program was invoked as a trigger.
5.  When the trigger program is not a TRIGGER_AFTER_UPDATE, TRIGGER_BEFORE_UPDATE, or TRIGGER_DEFINE program, associate the program with the desired object and event using the TRIGGER command.
6.  There is no support for recursive triggers. You must set the USETRIGGERS option to `NO` before you issue the same DML statement within a trigger program that triggered the program itself. For example, assume that you have written a program named `TRIGGER_MAINTAIN_ADD` that is triggered by MAINTAIN ADD statements. Within the `TRIGGER_MAINTAIN_ADD` program, you must set the USETRIGGERS option to `NO` before you issue a MAINTAIN statement.

##### 6.7.3.2 Characteristics of Object Trigger Programs

Object trigger programs have certain characteristics depending on the statement that triggers them. Some trigger programs execute before the triggering statement executes; some after. Oracle OLAP passes arguments to programs triggered by some statements, but not others. Oracle OLAP does not change dimension status before most trigger programs execute, but does change dimension status before some MAINTAIN statements trigger program execution. In most cases, you can give a trigger program any name that you choose, but some events require a program with a specific name.

Table 6-3 lists the OLAP DML statements that trigger programs, the required name of the program (if any), whether or not Oracle OLAP uses values returned by the program, and whether or not Oracle OLAP passes arguments to the program.

Keep the following points in mind when designing trigger programs:

- Triggers that execute before the DML statement—For trigger programs that execute before the triggering OLAP DML statement executes, you can define the trigger program as a user-defined function that returns a `BOOLEAN` value. The value returned by the program determines if Oracle OLAP executes the statement that triggered the execution of the trigger program. When the program returns `FALSE`, Oracle OLAP does not execute the triggering statement; when it returns `TRUE` or `NA`, the triggering statement executes.

- Arguments passed to trigger programs—Oracle OLAP passes arguments to some trigger programs. These programs are identified in Table 6-3. Descriptions of these arguments are provided in Table 6-4. Use the ARGUMENT statement to declare these arguments in your program. Use VARIABLE to define program variables for the values. Use the WKSDATA function to retrieve the data type of an argument with a `WORKSHEET` data type.

- Assign trigger programs—Oracle OLAP executes a program triggered by an Assign event each time it assigns a value to the object for which the event was defined. Thus, a program triggered by an Assign event is often executed over and over again as the assignment statements loops through an object assigning values. With each execution, the value to be assigned is passed as argument1 to the Assign trigger program. (See Table 6-4 for more information and [Example 10-163](olap-dml-commands-h-z.md) for an example.) Within the Assign trigger program, you can use a TRIGGER ASSIGN statement to assign a different value than that specified by the assignment statement that triggered the execution of the Assign trigger program.

  You can only assign values to a formula when the formula has an Assign trigger defined for it. When you assign a value to a formula with an Assign event, Oracle OLAP executes the trigger program for the event for assigned value and passes the assigned value to the trigger program. The Assign trigger does `not `change the definition of the formula itself. See [Example 10-165](olap-dml-commands-h-z.md) for an example of an Assign trigger on a formula.

- Maintain trigger programs and dimension status —In some cases, Oracle OLAP changes the status of the dimension being maintained when a Maintain event triggers the execution of a program. See Table 6-5 for details.

- Maintain triggers and dimension surrogates—Maintain triggers for dimension surrogates are different than Maintain triggers for other objects. You can only successfully issue a MAINTAIN statement against a dimension surrogate, when the dimension surrogate has a Maintain trigger. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error. Also, for Maintain Add and Maintain Merge triggers, whether or not an argument is passed to the program depends on the object on which the trigger is defined:

  - For dimension surrogates with a Maintain trigger, Oracle OLAP executes the trigger program one time for each value added or merged and passes that value into the program.

  - For other objects with a Maintain trigger, Oracle OLAP executes the trigger program only once after the MAINTAIN statement executes and no values are passed into the program

Table 6-3 Object Trigger Program Characteristics

| Triggering Statement (event)   | Program Name          | Return Values | Passed Arguments |
|:-------------------------------|:----------------------|:--------------|:-----------------|
| = (assignment) statement (SET) | No required name      | No            | Yes              |
| DEFINE                         | TRIGGER_DEFINE        | No            | No               |
| MAINTAIN ADD                   | No required name      | No            | No               |
| MAINTAIN DELETE (not ALL)      | No required name      | Yes           | No               |
| MAINTAIN DELETE ALL            | No required name      | Yes           | No               |
| MAINTAIN MERGE                 | No required name      | No            | No               |
| MAINTAIN MOVE                  | No required name      | Yes           | Yes              |
| MAINTAIN RENAME                | No required name      | Yes           | Yes              |
| PROPERTY                       | No required name      | Yes           | Yes              |
| UPDATE (Update AW)             | TRIGGER_AFTER_UPDATE  | No            | No               |
| UPDATE (Update AW)             | TRIGGER_BEFORE_UPDATE | Yes           | No               |
| UPDATE (Update Multi)          | No required name      | No            | No               |

Table 6-4 Arguments Passed to Trigger Programs

| Event           | Argument1                                                                                                                                                                                                                                | Argument2                                                                                                                                                     |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Property        | When the PROPERTY statement is assigning a property to an object, the name of the property. When the PROPERTY statement is deleting one or more properties, `the literal DELETE`. (`TEXT` data type)                                     | When the value of argument1 is `DELETE`, the name of the property or the literal `ALL`. In all other cases, the name of the property. (`WORKSHEET` data type) |
| Assignment      | The value to assign. When you know the data type of the object to which the value is assigned, specify that data type for the argument. When you do not know the actual data type, specify `WORKSHEET` as the data type of the argument. | None. Oracle OLAP passes only one argument to the program.                                                                                                    |
| Maintain Add    |                                                                                                                                                                                                                                          | (Dimension surrogates only) The value added. (`WORKSHEET data type)`                                                                                          |
| Maintain Rename | The dimension value to rename. (`TEXT` data type)                                                                                                                                                                                        | The new name of the dimension member. (`WORKSHEET` data type)                                                                                                 |
| Maintain Merge  |                                                                                                                                                                                                                                          | (Dimension surrogates only) The value merged. (`WORKSHEET data type)`                                                                                         |
| Maintain Move   | The position of the dimension value to move. (`TEXT` data type)                                                                                                                                                                          | The literal `BEFORE` or `AFTER`. (`WORKSHEET` data type)                                                                                                      |

Table 6-5 How Programs Triggered by Maintain Events Effect Dimension Status

| Event Subevent      | Dimension Status Before Program Execution           |
|:--------------------|:----------------------------------------------------|
| Maintain Add        | Status set to dimension values just added.          |
| Maintain Delete     | Status set to dimension values about to be deleted. |
| Maintain Delete All | Current status is not changed.                      |
| Maintain Merge      | Status set to dimension values just merged.         |
| Maintain Move       | Status set to dimension values about to be moved.   |
| Maintain Rename     | Current status is not changed.                      |

#### 6.7.4 Aggregation, Allocation, and Modeling Programs

To aggregate, allocate, or model data using the OLAP DML, you first specify the calculation that you want performed by defining a calculation specification as outlined in "[Creating Calculation Objects](formulas-models-aggregations-and-allocations.md)". Later, to populate variables with aggregated, allocated or modeled values as a database maintenance procedure, write a program to execute the calculation object. For more information on the OLAP DML statements that you use in these programs, see "[Running a Model](formulas-models-aggregations-and-allocations.md)", "[Executing the Aggregation](formulas-models-aggregations-and-allocations.md)", and "[Allocating Data](formulas-models-aggregations-and-allocations.md)".

#### 6.7.5 Forecasting Programs

The OLAP DML has several related statements that allow you to forecast data using the Geneva Forecasting engine which is a statistical forecasting engine from Roadmap Technologies that is used extensively in demand planning applications.

To forecast using the Geneva Forecasting engine, take the following steps:

1.  Add the future time values to the time dimension.

2.  Create a variable to hold the results of the forecast.

3.  Write a forecasting program. Within the program, issue the following statements in the order indicated:

    1.  FCOPEN function -- Creates a forecasting context.

    2.  FCSET command -- Specifies the forecast characteristics.

    3.  FCEXEC command -- Executes a forecast and populates Oracle OLAP variables with forecasting data.

    4.  FCQUERY function -- Retrieves information about the characteristics of a forecast or a trial of a forecast.

    5.  FCCLOSE command -- Closes a forecasting context.

For examples of using these statements to forecast data see [Example 9-119](olap-dml-commands-a-g.md).

#### 6.7.6 Programs to Export and Import Workspace Objects

You can export an entire workspace, several workspace objects, a single workspace object, or a portion of an analytic workspace object to a specially formatted EIF file. Then you can import the information into a different workspace within the same schema or a different one.

One reason for exporting and importing is to move your data to a new location. Another purpose is to remove extra space from your analytic workspace after you have added and then deleted many objects or dimension values. To do this, issue an EXPORT statement to put all the data in an EIF file, create another workspace with a different name, and then use an IMPORT statement to import the EIF file into the new workspace. When you have imported into the same database, you can delete the old workspace and refer to the new one with the same workspace alias that you used for the original one.

The following statement copies all the data and definitions from the current analytic workspace to an EIF file called `reorg.eif` in a directory object called `mydir`.

    EXPORT ALL TO EIF FILE 'mydir/reorg.eif'

### 6.8 User-Written Programs Looked For by Oracle OLAP

Oracle OLAP looks for the Oracle OLAP programs with the following names and executes them as explained in the topic for each program.

- AUTOGO
- ONATTACH
- ONDETACH
- PERMIT_READ
- PERMIT_WRITE
- TRIGGER_AFTER_UPDATE
- TRIGGER_AW
- TRIGGER_BEFORE_UPDATE
- TRIGGER_DEFINE

#### 6.8.1 AUTOGO

An AUTOGO program is a program that you can create and that Oracle OLAP checks for by name when an [AW ATTACH](olap-dml-commands-a-g.md) command executes.

When you attach an analytic workspace that contains a program named AUTOGO, unless the AW ATTACH statement includes an NOAUTOGO clause or an AUTOGO clause that specifies a program with a different name, Oracle OLAP executes the ONATTACH program.

**Note:**

Oracle OLAP checks for this program and other programs when a user attaches an analytic workspace. See "Startup Programs" for more information.

##### Return Value

`BOOLEAN`

`TRUE` when Oracle OLAP has successfully set up and attached the analytic workspace; or `FALSE` when it has not or when the Autogo program has thrown an exception.

**Note:**

You are encouraged to use the normal return values rather than relying on exceptions to create a return value of `FALSE`.

##### Syntax

To define a program with the name `AUTOGO` use the syntax shown in [DEFINE PROGRAM](olap-dml-commands-a-g.md). Code the actual program as a user-defined function with the following argument.

AUTOGO (password)

##### Parameters

See [AW ATTACH](olap-dml-commands-a-g.md) for explanation of password.

##### Examples

For examples of how attachment programs behave, see [Example 9-50](olap-dml-commands-a-g.md).

#### 6.8.2 ONATTACH

An ONATTACH program is a program that you can create and that Oracle OLAP checks for by name when an [AW ATTACH](olap-dml-commands-a-g.md) command executes.

When you attach an analytic workspace that contains a program named ONATTACH, unless the AW ATTACH statement includes an NOONATTACH clause or an ONATTACH clause that specifies a program with a different name, Oracle OLAP executes the ONATTACH program.

Depending on the statements in the` onattach` program, the user is granted or denied access to specific objects or sets of object values. For multiwriter attachment, you can use [ACQUIRE](olap-dml-commands-a-g.md) commands to provide access to individual workspace objects. For read-only and read/write attachment, you can use [PERMIT](olap-dml-commands-h-z.md) commands that grant or restrict access to individual workspace objects. All of the objects referred to in a given `onattach` program must exist in the same analytic workspace.

**Note:**

Oracle OLAP checks for this program and other programs when a user attaches an analytic workspace. See "Startup Programs" for more information.

##### Return Value

`BOOLEAN`

`TRUE` when Oracle OLAP has successfully set up and attached the analytic workspace; or `FALSE` when it has not or when the `onattach` program has thrown an exception.

**Note:**

You are encouraged to use the normal return values rather than relying on exceptions to create a return value of `FALSE`.

##### Syntax

To define a program with the name `ONATTACH` use the syntax shown in [DEFINE PROGRAM](olap-dml-commands-a-g.md). Code the actual program as a user-defined function with the following argument.

ONATTACH ({READ\|WRITE\|EXCLUSIVE\|MULTI} password)

##### Parameters

See [AW ATTACH](olap-dml-commands-a-g.md) for explanations of the attachment modes (that is, READ, WRITE, EXCLUSIVE, and MULTI) and password.

##### Usage Notes

ONATTACH Programs Created by the OLAP API

When an analytic workspace is created as an OLAP cube using the OLAP API, the OLAP API may also create a program named ONATTACH. You can not modify an ONATTACH program that is automatically created in this way. Additionally, overriding the execution of this ONATTACH is not recommended.

Consequently, when this type of ONATTACH program exists in an analytic workspace, create a different type of startup program to specify behavior that you want performed when that analytic workspace is attached.

##### Examples

For examples of how attachment programs behave, see [Example 9-50](olap-dml-commands-a-g.md).

#### 6.8.3 ONDETACH

An ONDETACH program is a program that you can create and that Oracle OLAP checks for by name when an [AW DETACH](olap-dml-commands-a-g.md) command executes. Depending on the value returned by the program, Oracle OLAP executes the code within the program immediately after detaching the analytic workspace.

**Note:**

Oracle OLAP checks for other programs when a user attaches an analytic workspace. See "Startup Programs" for more information.

##### Return Value

`BOOLEAN`

`TRUE` when Oracle OLAP has successfully detached the analytic workspace; or `FALSE` when it has not or when the `detach` program has thrown an exception.

**Note:**

You are encouraged to use the normal return values rather than relying on exceptions to create a return value of `FALSE`.

##### Syntax

To define a program with the name `ONDETACH` use the syntax shown in [DEFINE PROGRAM](olap-dml-commands-a-g.md).

#### 6.8.4 PERMIT_READ

A PERMIT_READ program is a program that you can create and that Oracle OLAP checks for by name when an [AW ATTACH](olap-dml-commands-a-g.md) read-only command executes. Depending on the value returned by the program, Oracle OLAP executes the code within the program after attaching the analytic workspace. Depending on the statements in the `permit_read` program the user is granted or denied access to specific objects or sets of object values. Within `permit_read` program, you can specify [PERMIT](olap-dml-commands-h-z.md) commands that grant or restrict access to individual workspace objects. All of the objects referred to in a given `permit_read` must exist in the same analytic workspace.

**Note:**

Oracle OLAP checks for this program and other programs when a user attaches an analytic workspace. See "Startup Programs" for more information.

**See Also:**

[PERMITERROR](olap-dml-options.md) option, [PERMITREADERROR](olap-dml-options.md) option, and PERMIT_WRITE program

##### Return Value

`BOOLEAN`

`TRUE` when Oracle OLAP has successfully set up and attached the analytic workspace; or `FALSE` when it has not or when the `permit_read` program has thrown an exception

**Note:**

You are encouraged to use the normal return values rather than relying on exceptions to create a return value of `FALSE`.

##### Syntax

To define a program with the name `PERMIT_READ` use the syntax shown in [DEFINE PROGRAM](olap-dml-commands-a-g.md). Code the actual program as a user-defined function with the following argument.

PERMIT_READ (password)

##### Parameters

See [AW ATTACH](olap-dml-commands-a-g.md) for an explanation of password. When a user specifies a password when attaching the analytic workspace, then the password is passed as an argument to the program for processing.

##### Examples

To see the order in which permission programs are executed when an analytic workspace is attached, see [Example 9-50](olap-dml-commands-a-g.md).

#### 6.8.5 PERMIT_WRITE

A PERMIT_WRITE program is a program that you can create and that Oracle OLAP checks for by name when an [AW ATTACH](olap-dml-commands-a-g.md) read/write command executes. Depending on the value returned by the program, Oracle OLAP executes the code within the program after attaching the analytic workspace. Depending on the statements in the `permit_write` program, the user is granted or denied access to specific objects or sets of object values. Within `permit_write` program, you can specify [PERMIT](olap-dml-commands-h-z.md) commands that grant or restrict access to individual workspace object. All of the objects referred to in a given `permit_write` program must exist in the same analytic workspace.

**Note:**

Oracle OLAP checks for this program and other programs when a user attaches an analytic workspace. See "Startup Programs" for more information.

**See Also:**

[PERMITERROR](olap-dml-options.md) option, [PERMITREADERROR](olap-dml-options.md) option, and PERMIT_READ program

##### Return Value

`BOOLEAN`

`TRUE` when Oracle OLAP has successfully set up and attached the analytic workspace; or `FALSE` when it has not or when the `permit_write` program has thrown an exception

**Note:**

You are encouraged to use the normal return values rather than relying on exceptions to create a return value of `FALSE`.

##### Syntax

To define a program with the name `PERMIT_WRITE` use the syntax shown in [DEFINE PROGRAM](olap-dml-commands-a-g.md). Code the actual program as a user-defined function with the following argument.

PERMIT_WRITE (password)

##### Parameters

See [AW ATTACH](olap-dml-commands-a-g.md) for an explanation of password. When a user specifies a password when attaching the analytic workspace, then the password is passed as an argument to the program for processing.

##### Examples

To see the order in which permission programs are executed when an analytic workspace is attached, see [Example 9-50](olap-dml-commands-a-g.md).

#### 6.8.6 TRIGGER_AFTER_UPDATE

A TRIGGER_AFTER_UPDATE program is a program that you can create in an analytic workspace and that Oracle OLAP checks for by name when an [UPDATE](olap-dml-commands-h-z.md) command for that analytic workspace executes. When the program exists in the same analytic workspace that you are updating, Oracle OLAP executes the program after executing the UPDATE.

**Note:**

The [USETRIGGERS](olap-dml-options.md) option must be set to its default value of `TRUE` for a TRIGGER_AFTER_UPDATE program to execute

**Note:**

"Trigger Programs".

##### Syntax

To create a program with the name `TRIGGER_AFTER_UPDATE`, follow the guidelines presented in "Trigger Programs".

##### Examples

Example 6-1 TRIGGER_AFTER_UPDATE Program

Assume you have defined the following program in your analytic workspace.

    DEFINE TRIGGER_AFTER_UPDATE PROGRAM
    PROGRAM
    SHOW JOINCHARS ('calltype = ' CALLTYPE)
    SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
    SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
    END


When you issue an UPDATE statement the program executes and displays the following output.

    calltype = TRIGGER
    triggering event = AFTER_UPDATE
    triggering subevent = AW

#### 6.8.7 TRIGGER_AW

A TRIGGER_AW program is a program that you can create in one analytic workspace and that Oracle OLAP checks for by name when that analytic workspace is current and you create, attach, detach, or delete any other analytic workspace.

**Note:**

Oracle OLAP checks for this program and other programs when a user attaches an analytic workspace. See "Startup Programs" for more information.

**See Also:**

"Trigger Programs"

##### Return Value

None.

##### Syntax

To create a program with the name `TRIGGER_AW`, follow the guidelines presented in"How to Create a TRIGGER_AW Program".

##### Usage Notes

How to Create a TRIGGER_AW Program

You create a TRIGGER_AW program by following the following procedure:

1.  Define the program as described in DEFINE PROGRAM.

2.  Name the program TRIGGER_AW.

3.  Code the actual program as described in "Specifying Program Contents".

    **Note:**

    There is no support for recursive triggers. You must set the USETRIGGERS option to `NO` before you issue an AW statement within an TRIGGER_AW program

##### Examples

Example 6-2 A TRIGGER_AW Program

Assume that you have defined a program with the following definition in an analytic workspace named `my_aw`.

    DEFINE TRIGGER_AW PROGRAM
    PROGRAM
    SHOW CALLTYPE
    SHOW TRIGGER(EVENT)
    SHOW TRIGGER(SUBEVENT)
    SHOW TRIGGER(NAME)
    END

When attach the `my_aw` workspace, the specified values are displayed.

    AW ATTACH MY_AW

    TRIGGER
    AW
    ATTACH
    MY_AW

#### 6.8.8 TRIGGER_BEFORE_UPDATE

A TRIGGER_BEFORE_UPDATE program is a program that you can create and that Oracle OLAP checks for by name when an [UPDATE](olap-dml-commands-h-z.md) command executes. When the program exists in the same analytic workspace that you are updating, Oracle OLAP executes the program and then, depending on the value returned by the program (if any), either does nor does not update the workspace.

**Note:**

The [USETRIGGERS](olap-dml-options.md) option must be set to its default value of `TRUE` for a TRIGGER_BEFORE_UPDATE program to execute

**Note:**

"Trigger Programs"

##### Return Value

You can write the program as a function that returns a `BOOLEAN` value. In this case, when the program returns FALSE, Oracle OLAP does not execute the UPDATE statement that triggered the execution of the TRIGGER_BEFORE_UPDATE program; when the program returns `TRUE` or `NA`, the UPDATE statement executes.

##### Syntax

To create a program with the name `TRIGGER_UPDATE`, follow the guidelines presented in "Trigger Programs".

##### Examples

Example 6-3 TRIGGER_BEFORE_UPDATE Program

Assume that an analytic workspace named `myaw` has an TRIGGER_BEFORE_UPDATE program with the following definition.

    DEFINE TRIGGER_BEFORE_UPDATE PROGRAM BOOLEAN
    PROGRAM
    SHOW JOINCHARS ('calltype = ' CALLTYPE)
    SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
    SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
    RETURN TRUE
    END


Assume that you define a `TEXT` variable named `myvar` and, then, issue an UPDATE statement. The TRIGGER_BEFORE_UPDSATE program executes.

    calltype = TRIGGER
    triggering event = BEFORE_UPDATE
    triggering subevent = AW

Because the program returned TRUE, the definition for `myva`r exists after you detach and reattach the workspace.

    AW DETACH myaw
    AW ATTACH myaw
    DESCRIBE

    DEFINE TRIGGER_BEFORE_UPDATE PROGRAM BOOLEAN
    PROGRAM
    SHOW JOINCHARS ('calltype = ' CALLTYPE)
    SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
    SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
    RETURN TRUE
    END

    DEFINE MYVAR VARIABLE TEXT

However, if you modified the program so that it returned `FALSE`, then when you detach and reattach the workspace, not only would the `myva`r definition not in the workspace, the definition for the TRIGGER_BEFORE_UPDATE program would also not be in the workspace.

#### 6.8.9 TRIGGER_DEFINE

A TRIGGER_DEFINE program is a program that you create and that Oracle OLAP checks for by name when a [DEFINE](olap-dml-commands-a-g.md) command executes. When the program exists in the same analytic workspace in which you are defining a new object, Oracle OLAP executes the program.

**Note:**

The [USETRIGGERS](olap-dml-options.md) option must be set to its default value of `TRUE` for a TRIGGER_DEFINE program to execute

**Note:**

"Trigger Programs"

##### Syntax

To create a program with the name `TRIGGER_DEFINE`, follow the guidelines presented in "Trigger Programs".

##### Examples

Example 6-4 A TRIGGER_DEFINE Program

Assume that you have written a TRIGGER_DEFINE program with the following description in your analytic workspace.

    DEFINE TRIGGER_DEFINE PROGRAM
    PROGRAM
    SHOW JOINCHARS ('calltype = ' CALLTYPE)
    SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
    SHOW JOINCHARS ('fully qualified object name ='TRIGGER(NAME))
    SHOW JOINCHARS ('type of object = 'OBJ(TYPE TRIGGER(NAME))
    DESCRIBE &TRIGGER(NAME)
    END

Assume, as shown in the following statements, that you issue a DEFINE VARIABLE statement to define a variable named `myvar`. As shown by the output following the statement, Oracle OLAP defines the variable and executes the TRIGGER_DEFINE program.

    DEFINE myvar VARIABLE TEXT
    calltype = TRIGGER
    triggering event = DEFINE
    fully qualified object name =MYAW!MYVAR
    type of object = VARIABLE

    DEFINE MYVAR VARIABLE TEXT
