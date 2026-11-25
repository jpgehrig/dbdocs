This chapter contains the following:

- Intended Audience

- Documentation Accessibility

- Structure

- Related Documents

- Conventions

This manual is a comprehensive user's guide and reference to the Oracle Pro\*COBOL and Pro\*FORTRAN Precompilers. It shows you step-by-step how to develop applications that use the SQL to access and manipulate data. It explores underlying concepts to advanced programming techniques using clear examples.

### Intended Audience

Anyone developing new applications or converting existing applications to run in the Oracle database environment will benefit from reading this guide. Written especially for programmers, this comprehensive treatment of the Oracle Precompilers will also be of value to systems analysts, project managers, and others interested in embedded SQL applications.

To use this guide effectively, you need a working knowledge of the following subjects:

- Applications programming in a high-level language

- The SQL database language

- Oracle concepts and terminology

### Structure

This guide contains eleven chapters and five appendixes. Chapters 1 and 2 give you your bearings, then Chapters 3, 4, 5, and 6 lead you through the essentials of embedded SQL programming. After reading these chapters, you will be able to write and run useful embedded SQL applications. Chapters 7, 8, 9, 10, and 11 cover advanced topics. A brief summary of what you will find in each chapter and appendix follows.

This sample manual contains one part, two chapters, and one appendixes. (Insert this chapter, appendix, and parts as cross-references so that the links are apparent in HTML.)

####  [Getting Acquainted](getting-acquainted.md)

This chapter introduces you to the Oracle Precompilers. You look at their role in developing application programs that manipulate Oracle data and find out what they allow your applications to do.

####  [Learning the Basics](learning-basics.md)

This chapter explains how embedded SQL programs do their work. You examine the special environment in which they operate, the impact of this environment on the design of your applications, the key concepts of embedded SQL programming, and the steps you take in developing an application.

####  [Meeting Program Requirements](meeting-program-requirements.md)

This chapter shows you how to meet embedded SQL program requirements. You learn the embedded SQL commands that declare variables, declare communications areas, and connect to an Oracle database. You also learn about the Oracle datatypes, Globalization Support (Globalization Support), data conversion, and how to take advantage of datatype equivalencing. In addition, this chapter shows you how to embed Oracle Call Interface (OCI) calls in your program and how to develop X/Open applications.

#### [ Using Embedded SQL](using-embedded-SQL.md)

This chapter teaches you the essentials of embedded SQL programming. You learn how to use host variables, indicator variables, cursors, cursor variables, and the fundamental SQL commands that insert, update, select, and delete Oracle data.

####  [Using Embedded PL/SQL](using-embedded-PLSQL.md)

This chapter shows you how to improve performance by embedding PL/SQL transaction processing blocks in your program. You learn how to use PL/SQL with host variables, indicator variables, cursors, stored subprograms, host arrays, and dynamic SQL.

####  [Running the Oracle Precompilers](running-Oracle-precompilers.md)

This chapter details the requirements for running an Oracle Precompiler. You learn what happens during precompilation, how to issue the precompiler command, how to specify the many useful precompiler options, how to do conditional and separate precompilations, and how to embed OCI calls in your host program.

####  [Defining and Controlling Transactions](defining-controlling-transactions.md)

This chapter describes transaction processing. You learn the basic techniques that safeguard the consistency of your database.

####  [Error Handling and Diagnostics](error-handling-diagnostics.md)

This chapter provides an in-depth discussion of error reporting and recovery. You learn how to detect and handle errors using the status variable SQLSTATE, the SQLCA structure, and the WHENEVER statement. You also learn how to diagnose problems using the ORACA.

####  [Using Host Arrays](using-host-arrays.md)

This chapter looks at using arrays to improve program performance. You learn how to manipulate Oracle data using arrays, how to operate on all the elements of an array with a single SQL statement, and how to limit the number of array elements processed.

####  [Using Dynamic SQL](using-dynamic-SQL.md)

This chapter shows you how to take advantage of dynamic SQL. You are taught four methods--from simple to complex--for writing flexible programs that, among other things, let users build SQL statements interactively at run time.

####  [Writing User Exits](writing-user-exits.md)

This chapter focuses on writing user exits for your SQL\*Forms or Oracle Forms applications. First, you learn the commands that allow a Forms application to interface with user exits. Then, you learn how to write and link a Forms user exit.

####  [New Features](new-features.md)

This appendix highlights the improvements and new features introduced with Release 1.8 of the Oracle Precompilers.

####  [Oracle Reserved Words\_ Keywords\_ and Namespaces](Oracle-reserved-words-keywords-namespaces.md)

This appendix lists words that have a special meaning to Oracle and namespaces that are reserved for Oracle libraries.

####  [Performance Tuning](performance-tuning.md)

This appendix gives you some simple, easy-to-apply methods for improving the performance of your applications.

####  [Syntactic and Semantic Checking](syntactic-and-semantic-checking.md)

This appendix shows you how to use the SQLCHECK option to control the type and extent of syntactic and semantic checking done on embedded SQL statements and PL/SQL blocks.

####  [Embedded SQL Commands and Directives](embedded-SQL-commands-and-directives.md)

This appendix contains descriptions of precompiler directives, embedded SQL commands, and Oracle embedded SQL extensions. These commands are prefaced in your source code with the keywords, EXEC SQL.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information on Programmer's Guide to the Oracle Precompilers, refer to the Oracle Technology Network (OTN):

[`http://www.oracle.com/technology/documentation/index.html`](http://www.oracle.com/technology/documentation/index.html)

### Conventions

The following conventions are also used in this manual:

| Convention    | Meaning                                                                                                                                                |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| . . .         | Vertical ellipsis points in an example mean that information not directly related to the example has been omitted.                                     |
| . . .         | Horizontal ellipsis points in statements or commands mean that parts of the statement or command not directly related to the example have been omitted |
| boldface text | Boldface type in text indicates a term defined in the text, the glossary, or in both locations.                                                        |
| \< \>         | Angle brackets enclose user-supplied names.                                                                                                            |
| \[ \]         | Brackets enclose optional clauses from which you can choose one or none.                                                                               |
