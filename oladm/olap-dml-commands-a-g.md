This chapter contains the following topics:

- About OLAP DML Commands

- Commands: Alphabetical Listing

- Commands by Category

- One topic for each of the OLAP DML commands that begins with the letters A - G, beginning with ACQUIRE.

Reference topics for the remaining OLAP DML commands appear in alphabetical order in [OLAP DML Commands: H-Z](olap-dml-commands-h-z.md).

For other OLAP DML reference topics, see [OLAP DML Properties](olap-dml-properties.md), [OLAP DML Options](olap-dml-options.md), [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), and [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md).

### 9.1 About OLAP DML Commands

OLAP DML commands work in much the same way as commands in other programming languages—the one exception is the looping nature of OLAP DML commands as discussed in "[OLAP DML Statements Apply to All of the Values of a Data Object](olap-dml-basic-concepts.md)".

Many OLAP DML commands perform complex actions. Some of these commands are data definition commands like the AW command which you use to create an analytic workspace and the DEFINE command which you use to define objects within an analytic workspace. Other OLAP DML commands are data manipulation commands. For example, you can use the OLAP DML SQL command to embed SQL statements in an OLAP DML program to copy data from relational tables into analytic workspace data objects, or you can use the AGGREGATE command to calculate summary data. Additionally, the DEFINE, MAINTAIN, PROPERTY, SET (=) UPDATE, and AW commands are recognized by Oracle OLAP as events that can trigger the execution of OLAP DML programs. (See "[Trigger Programs](olap-dml-programs.md)" for more information.)

**Tip:**

Many OLAP DML statements can be coded as a 3-character abbreviation that consists of the first letter of the statement plus the next two consonants.

Additionally, you can augment the functionality of the OLAP DML by writing an OLAP DML program for use as a command.

### 9.2 Commands: Alphabetical Listing

#### A

- ACQUIRE
- ACROSS
- ADD_CUBE_MODEL
- ADD_DIMENSION_MEMBER
- ADD_MODEL_DIMENSION
- AGGMAP
- AGGMAP ADD or REMOVE model
- AGGMAP SET
- AGGREGATE command
- ALLCOMPILE
- ALLOCATE
- ALLOCMAP
- ALLSTAT
- ARGUMENT
- AW command
- AWDESCRIBE

#### B

- BLANK
- BREAK

#### C

- CALL
- CDA
- CHGDFN
- CLEAR
- COMMIT
- COMPILE
- CONSIDER
- CONTEXT command
- CONTINUE
- COPYDFN
- CREATE_LOGICAL_MODEL

#### D

- DATE_FORMAT
- DBGOUTFILE
- DEFINE
- DELETE
- DESCRIBE
- DO ... DOEND

#### E

- EDIT
- EQ
- EXPORT

#### F

- FCCLOSE
- FCEXEC
- FCSET
- FETCH
- FILECLOSE
- FILECOPY
- FILEDELETE
- FILEMOVE
- FILEPAGE
- FILEPUT
- FILEREAD
- FILESET
- FILEVIEW
- FOR
- FORECAST
- FORECAST.REPORT
- FULLDSC

#### G

- GOTO
- GROUPINGID command
- [HEADING](olap-dml-commands-h-z.md)

#### H

- [HIDE](olap-dml-commands-h-z.md)
- [HIERDEPTH](olap-dml-commands-h-z.md)
- [HIERHEIGHT command](olap-dml-commands-h-z.md)

#### I

- [IF...THEN...ELSE command](olap-dml-commands-h-z.md)

#### I

- [IMPORT](olap-dml-commands-h-z.md)
- [INFILE](olap-dml-commands-h-z.md)

#### L

- [LD](olap-dml-commands-h-z.md)
- [LIMIT command](olap-dml-commands-h-z.md)
- [LIMIT BASEDIMS](olap-dml-commands-h-z.md)
- [LISTBY](olap-dml-commands-h-z.md)
- [LISTFILES](olap-dml-commands-h-z.md)
- [LISTNAMES](olap-dml-commands-h-z.md)
- [LOAD](olap-dml-commands-h-z.md)
- [LOG command](olap-dml-commands-h-z.md)

#### M

- [MAINTAIN](olap-dml-commands-h-z.md)
- [MODEL](olap-dml-commands-h-z.md)
- [MODEL.COMPRPT](olap-dml-commands-h-z.md)
- [MODEL.DEPRT](olap-dml-commands-h-z.md)
- [MODEL.XEQRPT](olap-dml-commands-h-z.md)
- [MONITOR](olap-dml-commands-h-z.md)
- [MOVE](olap-dml-commands-h-z.md)

#### O

- [OUTFILE](olap-dml-commands-h-z.md)

#### P

- [PAGE](olap-dml-commands-h-z.md)
- [PARSE](olap-dml-commands-h-z.md)
- [PERMIT](olap-dml-commands-h-z.md)
- [PERMITRESET](olap-dml-commands-h-z.md)
- [POP](olap-dml-commands-h-z.md)
- [POPLEVEL](olap-dml-commands-h-z.md)
- [PROGRAM](olap-dml-commands-h-z.md)
- [PROPERTY](olap-dml-commands-h-z.md)
- [PUSH](olap-dml-commands-h-z.md)
- [PUSHLEVEL](olap-dml-commands-h-z.md)

#### R

- [RECAP](olap-dml-commands-h-z.md)
- [REDO](olap-dml-commands-h-z.md)
- [REEDIT](olap-dml-commands-h-z.md)
- [REGRESS](olap-dml-commands-h-z.md)
- [REGRESS.REPORT](olap-dml-commands-h-z.md)
- [RELATION command](olap-dml-commands-h-z.md)
- [RELEASE](olap-dml-commands-h-z.md)
- [REMOVE_CUBE_MODEL](olap-dml-commands-h-z.md)
- [REMOVE_DIMENSION_MEMBER](olap-dml-commands-h-z.md)
- [REMOVE_MODEL_DIMENSION](olap-dml-commands-h-z.md)
- [RENAME](olap-dml-commands-h-z.md)
- [REPORT](olap-dml-commands-h-z.md)
- [RESYNC](olap-dml-commands-h-z.md)
- [RETURN](olap-dml-commands-h-z.md)
- [REVERT](olap-dml-commands-h-z.md)
- [ROW command](olap-dml-commands-h-z.md)

#### S

- [SET](olap-dml-commands-h-z.md)
- [SET1](olap-dml-commands-h-z.md)
- [SET_INCLUDED_MODEL](olap-dml-commands-h-z.md)
- [SET_PROPERTY](olap-dml-commands-h-z.md)
- [SHOW](olap-dml-commands-h-z.md)
- [SIGNAL](olap-dml-commands-h-z.md)
- [SLEEP](olap-dml-commands-h-z.md)
- [SORT command](olap-dml-commands-h-z.md)
- [SQL](olap-dml-commands-h-z.md)
- [STATUS](olap-dml-commands-h-z.md)
- [STDHDR](olap-dml-commands-h-z.md)
- [SWITCH command](olap-dml-commands-h-z.md)

#### T

- [TEMPSTAT](olap-dml-commands-h-z.md)
- [TRACE](olap-dml-commands-h-z.md)
- [TRACKPRG](olap-dml-commands-h-z.md)
- [TRAP](olap-dml-commands-h-z.md)
- [TRIGGER command](olap-dml-commands-h-z.md)
- [TRIGGERASSIGN](olap-dml-commands-h-z.md)

#### U

- [UNHIDE](olap-dml-commands-h-z.md)
- [UPDATE](olap-dml-commands-h-z.md)
- [UPDATE_ATTRIBUTE_VALUE](olap-dml-commands-h-z.md)
- [UPDATE_DIMENSION_MEMBER](olap-dml-commands-h-z.md)

#### V

- [VARIABLE](olap-dml-commands-h-z.md)
- [VNF](olap-dml-commands-h-z.md)

#### W

- [WHILE](olap-dml-commands-h-z.md)

#### Z

- [ZEROTOTAL](olap-dml-commands-h-z.md)

### 9.3 Commands by Category

#### OLAP Cube and Cube Dimension Modification Commands

- ADD_CUBE_MODEL
- ADD_DIMENSION_MEMBER
- ADD_MODEL_DIMENSION
- CREATE_LOGICAL_MODEL
- [REMOVE_CUBE_MODEL](olap-dml-commands-h-z.md)
- [REMOVE_DIMENSION_MEMBER](olap-dml-commands-h-z.md)
- [REMOVE_MODEL_DIMENSION](olap-dml-commands-h-z.md)
- [SET_INCLUDED_MODEL](olap-dml-commands-h-z.md)
- [SET_PROPERTY](olap-dml-commands-h-z.md)
- [UPDATE_ATTRIBUTE_VALUE](olap-dml-commands-h-z.md)
- [UPDATE_DIMENSION_MEMBER](olap-dml-commands-h-z.md)
- See also [OBJORG](olap-dml-functions-l-z.md) function

#### Aggregation Commands

- AGGMAP
- AGGMAP ADD or REMOVE model
- AGGMAP SET
- AGGREGATE command
- DEFINE AGGMAP
- [HIERDEPTH](olap-dml-commands-h-z.md)
- [HIERHEIGHT command](olap-dml-commands-h-z.md)

#### Allocation Commands

- ALLOCATE
- ALLOCMAP
- DEFINE AGGMAP

#### Assigment Commands

- CLEAR
- [MAINTAIN](olap-dml-commands-h-z.md)
- [SET](olap-dml-commands-h-z.md)
- [SET1](olap-dml-commands-h-z.md)
- [TRIGGER command](olap-dml-commands-h-z.md)
- [TRIGGERASSIGN](olap-dml-commands-h-z.md)

#### Debugging Commands

- DBGOUTFILE
- [LOG command](olap-dml-commands-h-z.md)
- [MONITOR](olap-dml-commands-h-z.md)
- [SIGNAL](olap-dml-commands-h-z.md)
- [TRACKPRG](olap-dml-commands-h-z.md)
- [TRAP](olap-dml-commands-h-z.md)

#### Analytic Workspace Object Definition Commands

- CHGDFN
- CONSIDER
- COPYDFN
- DEFINE
- DELETE
- DESCRIBE
- FULLDSC
- GROUPINGID command
- [HIDE](olap-dml-commands-h-z.md)
- [HIERHEIGHT command](olap-dml-commands-h-z.md)
- [LD](olap-dml-commands-h-z.md)
- [LISTBY](olap-dml-commands-h-z.md)
- [LISTNAMES](olap-dml-commands-h-z.md)
- [LOAD](olap-dml-commands-h-z.md)
- [PROPERTY](olap-dml-commands-h-z.md)
- [RELATION command](olap-dml-commands-h-z.md)
- [RENAME](olap-dml-commands-h-z.md)
- [TRIGGER command](olap-dml-commands-h-z.md)
- [UNHIDE](olap-dml-commands-h-z.md)

#### Dimension Status Commands

- ACROSS
- ALLSTAT
- [LIMIT command](olap-dml-commands-h-z.md)
- [LIMIT BASEDIMS](olap-dml-commands-h-z.md)
- [STATUS](olap-dml-commands-h-z.md)
- [TEMPSTAT](olap-dml-commands-h-z.md)

#### Forecast and Regression Commands

- FCCLOSE
- FCEXEC
- FCSET
- FORECAST
- FORECAST.REPORT
- [REGRESS](olap-dml-commands-h-z.md)
- [REGRESS.REPORT](olap-dml-commands-h-z.md)

#### Date Formatting Commands

- DATE_FORMAT
- [VNF](olap-dml-commands-h-z.md)

#### Formula Commands

- DEFINE FORMULA
- EQ
- [TRACE](olap-dml-commands-h-z.md)

#### Analytic Workspace Management Commands

- AW command
- COMMIT
- EXPORT (EIF)
- [IMPORT (EIF)](olap-dml-commands-h-z.md)
- [PERMIT](olap-dml-commands-h-z.md)
- [PERMITRESET](olap-dml-commands-h-z.md)
- [RENAME](olap-dml-commands-h-z.md)
- [UPDATE](olap-dml-commands-h-z.md)

#### Analytic Workspace Multiwriter Management Commands

- ACQUIRE
- [RELEASE](olap-dml-commands-h-z.md)
- [RESYNC](olap-dml-commands-h-z.md)
- [REVERT](olap-dml-commands-h-z.md)

#### File Management Commands

- CDA
- FILECLOSE
- FILECOPY
- FILEDELETE
- FILEMOVE
- FILEPAGE
- FILEPUT
- FILEREAD
- FILESET
- FILEVIEW
- [IMPORT (text)](olap-dml-commands-h-z.md)
- [INFILE](olap-dml-commands-h-z.md)
- [LISTFILES](olap-dml-commands-h-z.md)
- [OUTFILE](olap-dml-commands-h-z.md)

#### Data Model Commands

- AGGMAP ADD or REMOVE model
- DEFINE MODEL
- [DIMENSION (in models)](olap-dml-commands-h-z.md)
- [INCLUDE](olap-dml-commands-h-z.md)
- [MODEL](olap-dml-commands-h-z.md)
- [MODEL.COMPRPT](olap-dml-commands-h-z.md)
- [MODEL.DEPRT](olap-dml-commands-h-z.md)
- [MODEL.XEQRPT](olap-dml-commands-h-z.md)
- [SET](olap-dml-commands-h-z.md)
- [TRACE](olap-dml-commands-h-z.md)

#### Programming Commands

- ALLCOMPILE
- ARGUMENT
- BREAK
- BREAK
- CALL
- CONTINUE
- CONTINUE
- DEFINE PROGRAM
- DO ... DOEND
- FOR
- GOTO
- [HIDE](olap-dml-commands-h-z.md)
- [IF...THEN...ELSE command](olap-dml-commands-h-z.md)
- [PARSE](olap-dml-commands-h-z.md)
- [PROGRAM](olap-dml-commands-h-z.md)
- [RETURN](olap-dml-commands-h-z.md)
- [SLEEP](olap-dml-commands-h-z.md)
- [SWITCH command](olap-dml-commands-h-z.md)
- [TRACE](olap-dml-commands-h-z.md)
- [TRIGGER command](olap-dml-commands-h-z.md)
- [TRIGGERASSIGN](olap-dml-commands-h-z.md)
- [UNHIDE](olap-dml-commands-h-z.md)
- [VARIABLE](olap-dml-commands-h-z.md)
- [WHILE](olap-dml-commands-h-z.md)

#### Reporting Commands

- BLANK
- [HEADING](olap-dml-commands-h-z.md)
- [PAGE](olap-dml-commands-h-z.md)
- [REPORT](olap-dml-commands-h-z.md)
- [ROW command](olap-dml-commands-h-z.md)
- [SHOW](olap-dml-commands-h-z.md)
- [STDHDR](olap-dml-commands-h-z.md)
- [ZEROTOTAL](olap-dml-commands-h-z.md)

#### Save and Restore Value Commands

- CONTEXT command
- [POP](olap-dml-commands-h-z.md)
- [POPLEVEL](olap-dml-commands-h-z.md)
- [PUSH](olap-dml-commands-h-z.md)
- [PUSHLEVEL](olap-dml-commands-h-z.md)

#### Sorting Commands

- [MOVE](olap-dml-commands-h-z.md)
- [SORT command](olap-dml-commands-h-z.md)

#### Spreadsheet Commands

- DEFINE WORKSHEET
- EXPORT (spreadsheet)
- [IMPORT (spreadsheet)](olap-dml-commands-h-z.md)

#### SQL Execution Commands

- FETCH
- [SQL](olap-dml-commands-h-z.md)

#### OLAP DML Statement Edit Commands

- EDIT
- [RECAP](olap-dml-commands-h-z.md)
- [REDO](olap-dml-commands-h-z.md)
- [REEDIT](olap-dml-commands-h-z.md)

### 9.4 ACQUIRE

When an analytic workspace is attached in multiwriter mode, the ACQUIRE command acquires and (optionally) resynchronizes the specified objects so that their changes can be updated and committed.

**See Also:**

"Managing Analytic Workspaces Attached in Multiwriter Mode"

#### Syntax

ACQUIRE {acquired_noresync_objects \| RESYNC \[CASCADE\] -     resync_objects \[WAIT\] } \[CONSISTENT WITH \[CASCADE\] consistency_objects \[WAIT\]\]

where `resync_objects` has the following syntax:

resynch_objname \[FOR DELETE \| \[WITH  \[CASCADE\]\|WITHOUT\] RELATIONS\]\] , ...

#### Parameters

acquired_noresync_objects
A list of one or more variables, relations, valuesets, dimension names, separated by commas, that you want to access in read/write mode without resynchronizing.

To specify individual partitions of a partitioned variable, use the following syntax.

     variable_name (PARTITION partition_name \[, PARTITION partition_name \]...)

Acquiring objects in this manner preserves all read-only changes made to the objects. You can update variables and dimensions acquired in this manner using an UPDATE statement.

partition_name
The name of the partition in which you want to acquire the objects.

RESYNC
Specifies acquisition in read/write mode of the latest generation of the specified objects with all private changes discarded.

CASCADE

resync_objname
The name of a variable, relations, valueset, or dimension name that you want to access in read/write mode and resynchronize.

To specify individual partitions of a partitioned variable, use the following syntax.

variable_name (PARTITION partition_name \[, PARTITION partition_name \]...)

WAIT
When you do not specify WAIT, the ACQUIRE statement fails when another user has acquired any of the objects in `resync_objects` in read/write mode. When you specify WAIT, Oracle OLAP waits until all objects in `resync_objects` it can be acquired in read/write mode or the wait times out.

CONSISTENT WITH
Specifies that additional objects are to be accessible in read-only mode.the behavior of the ACQUIRE statement when a specified object is already acquired by another user and resynchronizes the specified objects when the ACQUIRE statement succeeds.

consistency_objects \[WAIT\]
A list of one or more a list of one or more variables, relations, valuesets, or dimension names, separated by commas, that you want to acquire in read-only mode.

To specify individual partitions of a partitioned variable, use the following syntax.

variable_name (PARTITION partition_name \[, PARTITION partition_name \]...)

When you do not specify WAIT, the ACQUIRE statement fails when any of the objects in the `consistency_objects` are acquired in read/write mode by another user. When you specify the WAIT keyword, Oracle OLAP waits to execute the ACQUIRE statement until none of the objects in `consistency_objects` are acquired in read/write mode by another user or until the wait times out.

#### Usage Notes

Understanding Consistency

To some extent you can think of an ACQUIRE statement with a CONSISTENT WITH phrase as a combination of ACQUIRE and RELEASE statements.

    ACQUIRE [avar...] RESYNC [rvar ...] cvar ... [WAIT]
    RELEASE cvar ...

The difference is that an ACQUIRE CONSISTENT WITH statement succeeds even when the user does not have sufficient permissions to acquire `cvar` variables.

Failure and Error-Handling

All of the clauses in the ACQUIRE statement must succeed or the statement fails. Consequently, either all of the requested objects are acquired or none of them are acquired.

Only one user can acquire an object in read/write mode at a time. You can first acquire an object in read-only mode, and then, assuming another user has not also acquired it in read-only mode, you can acquire it in read/write mode without releasing it first. However, once another user has acquired an object in read-only mode, you cannot acquire the same object in read/write mode until the other user releases the object. When a specified object has been acquired by another user or when your read-only generation for a specified object is not the latest generation for the object, the ACQUIRE statement fails.

Also, it can take a long time for the ACQUIRE statement to complete when you specify WAIT for either the RESYNC or CONSISTENT phrase. During the wait, some variables in the acquisition lists may be released while others may have been acquired. It is even possible for a deadlock to occur which causes the ACQUIRE statement to fail with a timeout error.

To avoid problems caused by deadlock, be thoughtful about the order in which you code ACQUIRE and RELEASE statements and include appropriate error handling routines.

#### Examples

Example 9-1 Acquiring, Updating, and Releasing Objects

A classic use of multiwriter attachment mode is to allow two users to modify two different objects in the same analytic workspace. For example, assume that an analytic workspace has two variables: `actuals` and `budget`. Assume also that one user (user A) wants to modify `actuals`, while another user (user B) wants to modify `budget`. In this case, after attaching the analytic workspace in the multiwriter mode, each user acquires the desired variable, performs the desired modification, updates, commits the changes, and then, either detaches the workspace or releases the acquired variable.

User A executes the following statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE actuals
    ... make modifications
    UPDATE MULTI actuals
    COMMIT
    RELEASE actuals
    AW DETACH myworkspace

While, at the same time, User B executes the following statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE budget
    ... make modifications
    UPDATE MULTI budget
    COMMIT
    RELEASE budget
    AW DETACH myworkspace

Example 9-2 Acquiring and Resynchronizing Objects

Assume that two users (named B1 and B2) both have to make what-if changes to `budget` and possibly modify their parts of `budget` when they like the results of the what-if changes. Neither user knows if anyone else needs to access `budget` at the same time that they are or if they have to make any permanent changes to `budget`. Consequently, they do not want to block anyone while they are performing what-if changes.

In this case, both users perform their what-if computation after attaching the analytic workspace in the multiwriter mode but without acquiring `budget`. When they later decide to make their what-if changes permanent, they try to acquire budget in unresynchronized mode. When the acquire succeeds, they update `budget` and commit the changes. The following OLAP DML statements show this scenario.

    AW ATTACH myworkspace MULTI
    ...perform what-if computations
    ACQUIRE budget
    ...maybe make some additional final changes
    UPDATE MULTI budget
    COMMIT
    RELEASE budget
    AW DETACH myworkspace

However, when the first acquire does not succeed, however, the users try again to acquire `budget` in resynchronized mode (possibly requesting a wait). When the resynchronized acquisition succeeds, they re-create the changes (because some relevant numbers might have changed) and then proceed to update and commit their analytic workspace. The following OLAP DML statements show this scenario.

    AW ATTACH myworkspace MULTI
    ... perform what-if computations
    ACQUIRE budget
    ...maybe make some additional final changes
    UPDATE MULTI budget
    COMMIT
    RELEASE budget
    AW DETACH myworkspace
    AW ATTACH myworkspace MULTI
    ...perform what-if computations
    ACQUIRE budget --> failed
    ACQUIRE RESYNC budget WAIT
    ...determine that the changes are still needed
    ...make changes to make permanent
    UPDATE MULTI budget
    COMMIT
    RELEASE budget
    AW DETACH myworkspace

Example 9-3 Acquiring Objects While Keeping Consistency

Sometimes you must keep some objects consistent with each other, which requires special care in multiwriter mode.

Assume that two users (User B1 and User B2) both have to modify `budget`, that `budget` must be kept consistent with `investment`, and that another user (User I) needs to modify `investment`. In this scenario, even though none of the users needs to modify both `budget` and `investment`, they all must ensure that when they acquire either `budget` or `investment` that no one else has either budget or investment already acquired. To achieve this effect, each user must issue an ACQUIRE statement with the CONSISTENT WITH phrase as shown in the following example code. Note that all of the users must be aware that the objects listed in the CONSISTENT phrase may be resynchronized by the ACQUIRE statement, if needed.

For example, User B1 could issue the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ... perform what-if computations
    ACQUIRE budget CONSISTENT WITH investment
    ... maybe make some additional final changes
    UPDATE MULTI budget
    COMMIT
    RELEASE budget, investment
    AW DETACH myworkspace

User B2 could issue the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ... perform what-if computations
    ACQUIRE budget CONSISTENT WITH investment --> failed
    ACQUIRE RESYNC budget CONSISTENT WITH investment WAIT
    ... determine that the changes are still needed
    ... make changes to make permanent
    UPDATE MULTI budget
    COMMIT
    RELEASE budget, investment
    AW DETACH myworkspace

User I could issue the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE investment CONSISTENT WITH budget --> failed
    ACQUIRE RESYNC investment CONSISTENT WITH budget WAIT
    ... make changes to investment
    UPDATE MULTI investment
    COMMIT
    RELEASE budget, investment
    AW DETACH myworkspace

### 9.5 ACROSS

The ACROSS command specifies a text expression that contains one or more statements to be executed in a loop. ACROSS temporarily sets status to the values that are in current status for the specified dimensions. After the ACROSS statement executes, dimension status is restored to what it was before the loop, and execution of the program resumes with the next statement. The repetition of the statements in the DO clause statements is controlled by the status of the dimensions and composites specified in the ACROSS statement and by the results of the WHERE clause when included.E

#### Syntax

ACROSS dimension... DO dml-statements \[WHERE boolean-expression\]

#### Parameters

dimension
One or more dimensions or composites whose current status controls the repetition of one or more statements, which are contained in dml-statements. The statements are repeated for each combination of the values of the specified dimensions in the current status. When two or more dimensions are specified, the first one varies the slowest.

DO dml-statements
A multiline text expression that is one or more OLAP DML statements to be executed for each iteration of the loop. You can specify any OALAP DML statement except one that is typically used as part of a multiple-line construct in a program. For example, the IF...THEN...ELSE, WHILE, FOR, or SWITCH commands cannot be executed by an ACROSS statement.

WHERE boolean-expression
For each iteration of the loop, specifies that the command evaluate boolean-expression before executing dml-statements and, when the result of boolean-expression is either `NA` or `FALSE`, to not execute dml-statements for that iteration.

#### Usage Notes

Code May Change Between Compilation and Execution

Oracle OLAP does not generate the code for the loop body until an ACROSS statement or the program that contains it is executed. Waiting until execution to generate the code allows for the possibility that, because the statements are contained within a text expression, the contents of an ACROSS loop may change between compilation and execution.

#### Examples

Example 9-4 Using ACROSS to Repeat ROW Commands

In a report program, you want to show the unit sales of tents for each of three months. Use the following ACROSS statement to repeat ROW commands for each value of the `month` dimension.

    LIMIT product TO 'Tents'
    LIMIT month TO 'Jan95' to 'Mar95'
    ACROSS month DO 'ROW INDENT 5 month WIDTH 6 unit'

         Jan95     533363
         Feb95     572796
         Mar95     707198

### 9.6 ADD_CUBE_MODEL

Adds a MODEL (in an aggregation) statement for a specified model into the aggregation map of a cube dimension. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**Note:**

You cannot use this program to modify a cube dimension if a materialized view exists for that cube dimension or any cube in which it participates.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL ADD_CUBE_MODEL(logical_cube, logical_dim, model_name, is_static_model, \[position \])

#### Parameters

CALL
Because ADD_CUBE_MODEL is an OLAP DML program with arguments, you invoke it using the OLAP DML CALL statement.

logical_cube
A text expression that is the name of the cube as defined in the Oracle data dictionary.

**See Also:**

"Guidelines for Specifying Values for the Names of Logical OLAP Objects"

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

model_name
A text expression that is the name of the logical model that is associated with logical_dim.

is_static_model
A Boolean expression that specifies whether model_name is added before or after the RELATION (for aggregation) statements in the aggmap for logical_cube.

The default value is `TRUE` which means that the MODEL statement added before the RELATION statements (that is that model_name is a static model).

Specify `FALSE` if you want the MODEL statement added after the RELATION statements (that is, that model_name is a dynamic model).

position
An integer that specifies where in the list of either static or dynamic models, the new model is added. For example, if you specify a value of `0` (zero) for position and `FALSE` for is_static_model, then the model is added as the first dynamic model. The default value of position, is at the end of the list.

When you specify a negative value for position, then the model is added that many positions from the end of the list.

#### Examples

For an example of using ADD_CUBE_MODEL in conjunction with SET_INCLUDED_MODEL, see the example provided for [SET_INCLUDED_MODEL](olap-dml-commands-h-z.md).

### 9.7 ADD_DIMENSION_MEMBER

The ADD_DIMENSION_MEMBER program adds a member to an OLAP cube dimension. An OLAP cube dimension (sometimes also called an "OLAP logical dimension") is an OLAP dimension that is defined as a first-class data object in the Oracle data dictionary.

**Note:**

You cannot use this program to modify a cube dimension if a materialized view exists for that cube dimension or any cube in which it participates.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL ADD_DIMENSION_MEMBER(member_id, logical_dim, hier_list,  level_name,  -

     parent-member_id, \[ auto_compile, \[ merge \]\])

#### Parameters

CALL
Because ADD_DIMENSION_MEMBER is an OLAP DML program with arguments, you invoke it using the OLAP DML CALL statement.

member_id
A text expression that is the value of the member that you want to add to the cube dimension.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"Guidelines for Specifying Values for the Names of Logical OLAP Objects"

hier_list
A multi-line text expression consisting of the Oracle data dictionary names of all of the hierarchies that you want the dimension member added to. Specify one hierarchy name per line.

When you want the member to be added to all of the cube dimension hierarchies, specify `NA`.

level_name
For level hierarchies, a text value that specifies the hierarchy level at which the program will add the member to the cube dimension. For level hierarchies, the value you specify for level_name must be:

- Compatible with the value you specify for parent_member_id

- At the same hierarchy level as the existing cube dimension member because a cube dimension member cannot be in two different levels across hierarchies.

When the member participates in a value hierarchy (that is, when there are no levels), specify `NA`.

**See Also:**

"Invalid Level Names in Cube-Aware OLAP DML Statements"

parent_member_id
A text expression that specifies the value of the member which is the parent of the member that you want to add to the cube dimension. When you want to add the member as the top member of a hierarchy, specify `NA`.

auto_compile
A Boolean expression that specifies whether or not you want related analytic workspace objects (for example, he parent relation) to be updated immediately. The default value is `TRUE` in which case all of the changes to the analytic workspace that are needed to add the cube dimension member happen now. Specify FALSE only when, for performance reasons, you want to make a bulk set of changes before issuing a compile. In this case, you need to explicitly compile the cube dimension before the values of the analytic workspace objects take effect as described in "Explicitly Compiling a Cube Dimension".

**Note:**

Regardless of the value that you specify for this argument, the new member is always immediately added to the dimension -- even when an error is signaled during compilation.

merge
A Boolean expression that specifies whether or not the program updates the dimension member if it exists or creates it if it does not. The default value is `FALSE`.

#### Usage Notes

Explicitly Compiling a Cube Dimension

When you specify `FALSE` for auto_compile, you need to explicitly compile the cube dimension before the values of the analytic workspace objects take effect. You perform the compilation with a `DBMS_CUBE.BUILD` package call. You can make this call within Analytic Workspace Manager by issuing the following statement where cube_dimension_name is the fully-qualified name of the cube dimension as defined in the Oracle data dictionary.

    SQL PROCEDURE DBMS_CUBE.BUILD('cube_dimension_name USING (COMPILE)');

By default, issuing the above statement performs an UPDATE and COMMIT to the database. To prevent an UPDATE and COMMIT from occurring, add NO COMMIT to the statement as shown below.

    SQL PROCEDURE DBMS_CUBE.BUILD'NO COMMIT cube_dimension_name USING (COMPILE)');

Guidelines for Specifying Values for the Names of Logical OLAP Objects

In an OLAP DML statement the text expression that you specify for an OLAP logical object (that is, a first-class OLAP object that is defined in the Oracle data dictionary such as a cube or cube dimension) must resolve to a value with the following form where LOGICAL_OBJECT_NAME is the Oracle data dictionary name of the OLAP object:

\[SCHEMA_NAME.\] LOGICAL_OBJECT_NAME

For example, valid expressions for referencing the XADEMO cube dimension in the XADEMO schema include:

    'product'
    'xademo.product'
    'PRODUCT'
    'XADEMO.product'
    '\"XADEMO\".\"PRODUCT\"'

**Note:**

OLAP DML cube-aware programs interpret a text value that you specify for an OLAP logical object as upper case text unless you enclose the value in double quotes.

Transaction Scope of Cube-Aware OLAP DML Statements

Unless otherwise noted, the scope of a cube-aware OLAP DML statement, just like other OLAP DML statement, is a single session. To persist any changes, you must have attached the analytic workspace in Read/Write mode before you issue the statement and issue OLAP DML UPDATE and COMMIT statements after you execute the statement. If the analytic workspace is attached Read Only or if you do not issue UPDATE and COMMIT statements, then the changes exist only in the session while the analytic workspace is attached.

Invalid Level Names in Cube-Aware OLAP DML Statements

If you specify an invalid value for level_name or parent_member_id, a compile-time error is thrown. Also, an error will occur if you specify a hierarchy level for the member that is different from the level it participates in another hierarchy. In this case, a call error is thrown if auto_compile is `FALSE`.

#### Examples

Example 9-5 Adding Members to an OLAP Cube Dimension

This example adds members to an OLAP cube dimension named `my_time`.

1.  Execute the following PL/SQL statement to report on the values and hierarchy of the `my_time` cube dimension before any changes are made.

        select dim_key||'  '||level_name||'  '||parent
                 from my_time_lvl_hier_view
                 order by dim_key asc;

        DIM_KEY||''||LEVEL_NAME||''||PARENT
        -------------------------------------------------------------------------------
        L1_0  L1
        L1_1  L1
        L2_1  L2  L1_1
        L2_2  L2  L1_1
        L3_1  L3  L2_1
        L3_2  L3  L2_1
        L3_3  L3  L2_2
        L3_4  L3  L2_2
        L3_5  L3  L2_2

        9 rows selected.

2.  Execute the following PL/SQL statement to execute the user-written OLAP DML program named `ADD_LQ_2`.

        exec dbms_aw.execute('call my_util_aw!add_l1_2');

    The definition of the user-written OLAP DML program named `ADD_LQ_2` is shown below. Note that it calls the `ADD_DIMENSION_MEMBER` program provided with the OLAP DML to add new members to the `my_time` cube dimension.

        DEFINE ADD_L1_2 PROGRAM
        PROGRAM
          VARIABLE _aw_dim       text
          VARIABLE _aw_sales     text
          VARIABLE _members      text
          VARIABLE _member       text
          VARIABLE _i            integer

          _aw_dim = OBJORG(DIM 'my_time')
          _aw_sales = OBJORG(MEASURE 'my_cube' 'sales')

          " Adds L1_2, L2_3, L3_6  CALL ADD_DIMENSION_MEMBER('L1_2', 'my_time', NA, 'L1', NA, NO)
          CALL ADD_DIMENSION_MEMBER('L2_3', 'my_time', NA, 'L2', 'L1_2', NO)
          CALL ADD_DIMENSION_MEMBER('L3_6', 'my_time', NA, 'L3', 'L2_3', NO)

          " Set my_time attribute (to meaningless values) so dimension can compile
          LIMIT &_aw_dim TO 'L1_2', 'L2_3', 'L3_6'
          _members = VALUES(&_aw_dim)
          _i = 1
          WHILE _i LE NUMLINES(_members)
          DO
            _member = EXTLINES(_members, _i, 1)
            _i = _i + 1
            CALL UPDATE_ATTRIBUTE_VALUE(_member, 'my_time', 'start_date', -
                                        to_date('01/01/08', 'MM/DD/YY'), NO)
            CALL UPDATE_ATTRIBUTE_VALUE(_member, 'my_time', 'timespan', 1, NO)
          DOEND

          &_aw_sales(&_aw_dim 'L3_6') = 3

          UPDATE
          COMMIT
        END

3.  Issue the following PL/SQL statement to compile the `my_time` cube dimension.

         exec dbms_cube.build('MY_TIME USING (COMPILE)');

4.  Report the values and hierarchy of the `my_time` cube dimension after compilation

        select dim_key||'  '||level_name||'  '||parent
            from my_time_lvl_hier_view
            order by dim_key asc;

        DIM_KEY||''||LEVEL_NAME||''||PARENT
        -------------------------------------------------------------------------------
        L1_0  L1
        L1_1  L1
        L1_2  L1
        L2_1  L2  L1_1
        L2_2  L2  L1_1
        L2_3  L2  L1_2
        L3_1  L3  L2_1
        L3_2  L3  L2_1
        L3_3  L3  L2_2
        L3_4  L3  L2_2
        L3_5  L3  L2_2
        L3_6  L3  L2_3

        12 rows selected.

5.  Execute the following PL/SQL statement to solve `my_cube` with the new hierarchy.

        exec dbms_cube.build(script => 'MY_CUBE USING (SOLVE)', add_dimensions => false);

6.  Issue the following PL/SQL statement to report on the values of the `sales` and `moving_sales` measure in my-cube. Note that the new `my_time` cube dimension values are shown.

        select my_time||'  '||lpad(sales, 2)||'  '||lpad(moving_sales, 2)
        from my_cube_view
        order by my_time asc;

        MY_TIME||''||LPAD(SALES,2)||''||LPAD(MOVING_SALES,2)
        --------------------------------------------------------------------
        L1_0  24  27
        L1_1  14  38
        L1_2   3   3
        L2_1   2   5
        L2_2  12  14
        L2_3   3   3
        L3_1   1   4
        L3_2   1   2
        L3_3  10  11
        L3_4   1  11
        L3_5   1   2
        L3_6   3   3

        12 rows selected.

### 9.8 ADD_MODEL_DIMENSION

The ADD_MODEL_DIMENSION program adds a [DIMENSION (in models)](olap-dml-commands-h-z.md) statement to a cube dimension's model. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL ADD_MODEL_DIMENSION(logical_dim, model_name, explicit_dim)

#### Parameters

CALL
Because ADD_MODEL_DIMENSION is an OLAP DML program with arguments, you invoke it using the OLAP DML CALL statement.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"Guidelines for Specifying Values for the Names of Logical OLAP Objects"

model_name
A text expression that is the name of the logical model that is associated with logical_dim.

explicit_dim
A text expression that is the name of the dimension that you want to add to the cube dimension's model.

### 9.9 AGGMAP

The AGGMAP command identifies an aggmap object as a specification for aggregation and adds an aggregation specification to the definition of the current aggmap object. To use AGGMAP to assign an aggregation specification to n aggmap object, the definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

An alternative to the AGGMAP command is the EDIT AGGMAP statement, which is available only in OLAP Worksheet. The EDIT AGGMAP statement opens an Edit window in which you can add, delete, or change the aggregation specification for an aggmap object.

**See Also:**

"[OLAP DML Aggregation Objects](formulas-models-aggregations-and-allocations.md)"

(Note that there are two other OLAP DML statements that are also sometimes referred to as "AGGMAP statements": AGGMAP ADD or REMOVE model statement that you can use to add or remove a model from an aggmap object of type AGGMAP, and AGGMAP SET that you can use to specify the default aggmap for a variable.)

#### Syntax

AGGMAP\[specification\]

#### Parameters

specification
A multiline text expression that is the aggregation specification for the current aggmap object. Each statement is a line of the multiline text expression. When coding an AGGMAP command at the command line level, separate statements with newline delimiters (`\n`), or use JOINLINES.

An aggregation specification begins with AGGMAP and ends with an `END`. Between these statements, you code one or more the following statements depending on the calculation that you want to specify. Minimally, you must code one RELATION (for aggregation) statement.

- AGGINDEX
- BREAKOUT DIMENSION
- CACHE
- DIMENSION (for aggregation)
- DROP DIMENSION
- MEASUREDIM (for aggregation)
- MODEL (in an aggregation)
- PRECOMPUTE
- RELATION (for aggregation)

**Note:**

You cannot specify a conjoint dimension in the specification for the aggmap; use composites instead.

#### Usage Notes

Creating Temporary or Custom Aggregates

Most aggmap objects are defined to calculate variable values that are dimensioned by permanent dimension members (that is, dimension members that persist from one session to another). However, users might want to create their own aggregates at run time for forecasting or what-if analysis, or just because they want to view the data in an unforeseen way. Adding temporary members to dimensions and aggregating data for those members is sometimes called creating temporary or custom aggregates. For example, you can use a [MAINTAIN ADD SESSION](olap-dml-commands-h-z.md) statement like the one below to temporarily add a model to an aggmap object.

`MAINTAIN` `dimension` `ADD SESSION` `member` `=` `model` `APPLY TO AGGMAP` `aggmap`

Aggregating Variables Dimensioned by Compressed Composites

Keep the following points in mind when designing an aggregation specification for a variable dimensioned by a compressed composite:

- RELATION statements in the aggregation specification must be coded following the guidelines given in "RELATION Statements for Compressed Composites".

- There is no support for parallel aggregation. Instead, use multiple sessions to compute variables or partitions that have their own compressed composites.

- If possible, Oracle OLAP automatically performs incremental aggregation when you reaggregate a variable dimensioned by the compressed composite. In other words, Oracle OLAP determines what changes have occurred since the last aggregation, determines the smallest region of the variable that needs to be recomputed, and recomputes only that region.

  Consequently, there is no support for explicit incremental aggregation. You cannot aggregate a variable dimensioned by a compressed composite if the dimension status of the variable is limited. The status of the variable's dimensions must be ALLSTAT for the aggregation to succeed. You can, however, partition using a dense dimension with local compressed composites. In this way you can aggregate only those partitions that contain new data.

Aggregation Options and System Properties

Several options can impact aggregation as outlined in "[Aggregation Options](olap-dml-options.md)".

See "[System Properties by Category](olap-dml-properties.md)" for a list of system properties that relate to aggregation or allocation.

Checking for Circularity

AGGREGATE automatically checks relations for circularity in and among multiple hierarchies. When you first define hierarchies, check for circularity by setting PRECOMPUTE statements to `NA` and AGGINDEX to `NO`. A XSHIERCK01 error during aggregation indicates that a circular hierarchy may have been detected. However, when the message includes a reference to UNDIRECTED, then multiple paths to an ancestor from a detail data cell have been detected. Some calculations require that a detail data cell use multiple paths to the same ancestor cell. When this is the case, then you must set the MULTIPATHHIER option to `YES` before you execute the AGGREGATE command. Otherwise, you must correct the error in the hierarchy structure. For more details about this error message and how to interpret it, see the [MULTIPATHHIER](olap-dml-options.md) option.

#### Examples

Example 9-6 Combining Pre-calculation and Calculation on the Fly

This example describes the steps you can take to pre-calculate some data in your analytic workspace and specify that the rest should be calculated when users request it.

Suppose you define an analytic workspace named `mydtb` that has a `units` variable with the following definition.

    DEFINE units INTEGER <time, SPARSE <product, geography>>

You now must create and add a specification to the aggmap, which specifies the data that should be aggregated. This example shows you how to use an input file, which contains OLAP DML statements that define the aggmap and add a specification to it:

1.  Identify the name of each dimension's hierarchy. When you have defined the hierarchies as self-relations, you use the names of the self-relations.

2.  Decide which data to aggregate.

    Suppose you want to calculate data for all levels of the `time` and `product` dimensions, but not for `geography`. The `geography` dimension's lowest level of data is at the city level. The second level of the hierarchy has three dimension values that represent regions: `East`, `Central`, and `West`. The third level of the hierarchy has one dimension value: `Total`.

    Suppose that you want to pre-calculate the data for `East` and store it in the analytic workspace. You want the data for `Central`, `West`, and `Total` to be calculated only when users request that data — that data is not stored in the analytic workspace. Therefore, you must specify this information in the specification that you add to your aggmap object.

3.  Create an ASCII text file named `units.txt`. Add the following OLAP DML statements to your text file.

        DEFINE units.agg AGGMAP <time, SPARSE <product, geography>>
        AGGMAP
        RELATION myti.parent
        RELATION mypr.parent
        RELATION myge.parent PRECOMPUTE ('East')
        END

    The preceding statements define an aggmap named `units.agg`, then add the three RELATION statements to the aggregation specification when you read the units.txt file into your analytic workspace.

4.  To read the `units.txt` file into your analytic workspace, execute the following statement.

        INFILE 'inf/units.txt'

5.  The `units.agg` aggmap should now exist in your analytic workspace. You can aggregate the `units` variable with the following statement.

        AGGREGATE units USING units.agg

    Now the data for `East` for all times and products has been calculated and stored in the analytic workspace.

6.  Set up the analytic workspace so that when a user requests data for `Central`, `West`, or `Total`, that data is calculated and displayed. It is generally a good idea to compile the aggmap object before using it with the AGGREGATE function, as shown by the following statement.

        COMPILE units.agg

    This is not an issue when you are just using the AGGREGATE command, because this statement compiles the aggmap object before it uses it. However, when you do not use the FUNCDATA keyword with the AGGREGATE command, the metadata that is needed to perform calculation on the fly has not been compiled yet. If you have performed all other necessary calculations (such as calculating models), then it is a good practice to compile the aggmap when you load data. When you fail to do so, that means that every time a user opens the analytic workspace, that user has to wait for the aggregation to be compiled automatically. In other words, when any data is calculated on the fly, you can improve query performance for all of your users by compiling the aggmap before making the analytic workspace available to your users.

7.  Add a property to the `units` variable.

        CONSIDER units
        PROPERTY '$NATRIGGER' 'AGGREGATE(units USING units.agg)'

    This property indicates that when a data cell contains an `NA` value, Oracle OLAP calls the AGGREGATE function to aggregate the data for that cell. Therefore, any `units` data that is requested by a user displayed. However, only the data for the `East` dimension value of the `geography` dimension has actually been aggregated and stored in the analytic workspace. All other data (for `Central`, `West`, and `Total`) is calculated only when users request it.

Example 9-7 Performing Non-additive Aggregation

This example shows how to use operators and arguments to combine additive and non-additive aggregation.

Suppose that you have defined four variables: `sales`, `debt`, `interest_rate`, and `inventory`. The variables have been defined with the same dimensionality where `cp` is a composite that has been defined with the `product` and `geography` dimensions.

    <time cp<product geography>>

Suppose you want to use one AGGREGATE command to aggregate all four variables. The `debt` variable requires additive aggregation. The `sales` variable requires a weighted sum aggregation, and `interest_rate` requires a hierarchical weighted average. Therefore, both `sales` and `interest_rate` require a weight object, which you must define and populate with weight values. `inventory` requires a result that represents the total inventory, which is the last value in the hierarchy.

You specify the aggregation operation for `debt` and `inventory` with the OPERATOR keyword. However, because `sales` and `interest_rate` have aggregation operations that require weight objects, you must use the ARGS keyword to specify their operations. You define an operator variable to use the OPERATOR keyword. Typically, the operator variable is dimensioned by a measure dimension or a line item dimension.

Here are the steps to define the aggregation you want to occur:

1.  Because you are also using a measure dimension to define an argument variable to use with the ARGS keyword, define that `measure` dimension, as illustrated by the following statements.

        DEFINE measure DIMENSION TEXT
        MAINTAIN measure 'sales', 'debt', 'interest_rate', 'inventory'

    **Note:**

    Whenever you use a `measure` dimension in a RELATION statement, you must include a MEASUREDIM statement in the same aggregation specification

2.  Define an operator variable named `opvar` and populate it.The statements specify that the aggregation for `debt` should use the `SUM` operator, and the aggregation for `inventory` should use the `HLAST` operator.

        DEFINE opvar TEXT <measure>
        opvar (measure 'sales') = 'WSUM'
        opvar (measure 'debt') = 'SUM'
        opvar (measure 'interest_rate') = 'HWAVERAGE'
        opvar (measure 'inventory') = 'HLAST'

3.  Because `sales` and `interest_rate` require weight objects, define and populate those weight objects. The following statement defines a weight object named `currency` (to be used by `sales`).

        DEFINE currency DECIMAL <time geography>

    Notice that the `currency` variable is dimensioned only by `time` and `geography`. The purpose of this variable is to provide weights that act as currency conversion information for foreign countries; therefore, it is unnecessary to include the `product` dimension.

4.  Populate `currency` with the weight values that you want to use.

5.  The `interest_rate` variable's nonaddictive aggregation (hierarchical weighted average) requires the sum of the variable `debt`. In other words, `interest_rate` cannot be aggregated without the results of the aggregation of `debt`.

    You can now define an argument variable, which you must specify the aggregation results of `debt` as a weight object for `interest_rate`. You use the same argument variable to specify `currency` as the weight object for the `sales` variable. The following statement defines an argument variable named `argvar`.

        DEFINE argvar TEXT <measure>

6.  The next few statements populate the argument variable.

        argvar (measure 'sales') = 'weightby currency'
        argvar (measure 'debt') = NA
        argvar (measure 'interest_rate') = 'weightby debt'
        argvar (measure 'inventory') = NA

7.  For the aggregation of `product` and `geography`, the data for the `sales`, `debt`, and `interest_rate` variables can simply be added. But the `inventory` variable requires a hierarchical weighted average. Consequently, it is necessary to define a second operator variable and a second argument variable, both of which are used in the RELATION statement for `product` and `geography`.

    The following statements define the second operator variable and populate it.

        DEFINE opvar2 TEXT <measure>
        opvar (measure 'sales') = 'Sum'
        opvar (measure 'debt') = 'Sum'
        opvar (measure 'interest_rate') = 'Sum'
        opvar (measure 'inventory') = 'HWAverage'

    The following statements define the second argument variable and populate it.

        DEFINE argvar2 TEXT <measure>
        argvar (measure 'sales') = NA
        argvar (measure 'debt') = NA
        argvar (measure 'interest_rate') = NA
        argvar (measure 'inventory') = 'weightby debt'

8.  Now create the aggmap, by issuing the following statements.

        DEFINE sales.agg AGGMAP <time, CP<product geography>>
        AGGMAP
        RELATION time.r OPERATOR opvar ARGS argvar
        RELATION product.r OPERATOR opvar2 ARGS argvar2
        RELATION geography.r OPERATOR opvar2 ARGS argvar2
        MEASUREDIM measure
        END

9.  Finally, use the following statement to aggregate all four variables.

        AGGREGATE sales debt interest_rate inventory USING sales.agg

Example 9-8 Programmatically Defining an Aggmap

The following program uses the EXISTS function to test whether an AGGMAP exists, and defines the AGGMAP when it does not. It then uses an AGGMAP statement to define the specification for the aggmap.

    DEFINE MAKEAGGMAP PROGRAM
    LD Create dynamic aggmap
    PROGRAM
    IF NOT EXISTS ('test.agg')
       THEN DEFINE test.agg AGGMAP <geography product channel time>
       ELSE CONSIDER test.agg
    AGGMAP JOINLINES(-
       'RELATION geography.parentrel PRECOMPUTE (geography.lvldim 2 4)' -
       'RELATION product.parentrel' -
       'RELATION channel.parentrel' -
       'RELATION time.parentrel' -
       'END')
    END

Example 9-9 Creating an Aggmap Using an Input File

Suppose that you have created a disk file called `salesagg.txt`, which contains the following aggmap definition and specification.

    DEFINE sales.agg AGGMAP <time, product, geography>
    AGGMAP
    RELATION time.r PRECOMPUTE (time NE 'Year99')
    RELATION product.r PRECOMPUTE (product NE 'ALL')
    RELATION geography.r
    CACHE STORE
    END

To include the `sales.agg` aggmap in your analytic workspace, execute the following statement, where `inf` is the alias for the directory where the file is stored.

    INFILE 'inf/salesagg.txt'

The `sales.agg` aggmap has now been defined and contains the three RELATION statements and the CACHE statement. In this example, you are specifying that all of the data for the hierarchy for the `time` dimension, `time.r`, should be aggregated, except for any data that has a `time` dimension value of `Year99`. All of the data for the hierarchy for the `product` dimension, `product.r`, should be aggregated, except for any data that has a `product` dimension value of `All`. All `geography` dimension values are aggregated. The CACHE STORE statement specifies that any data that are rolled up on the fly should be calculated just once and stored in the cache for other access requests during the same session.

You can now use the `sales.agg` aggmap with an AGGREGATE command, such as.

    AGGREGATE sales USING sales.agg

In this example, any data value that dimensioned by a `Year99` value of the `time` dimension or an `All` value of the `product` dimension is calculated on the fly. All other data is aggregated and stored in the analytic workspace.

Example 9-10 Using Multiple Aggmaps

When you use a forecast, you must ensure that all of the input data that is required by that forecast has been pre-calculated. Otherwise, the forecast uses incorrect or nonexistent data. For example, suppose your forecast requires that all line items are aggregated. Using a `budget` variable that is dimensioned by `time`, `line`, and `division`, one approach would be to perform a complete aggregation of the `line` dimension, forecast the `dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR`, and then aggregate the remaining dimension, `division`.

You can support this processing by defining three aggmap objects:

1.  Define the first aggmap, named `forecast.agg1`, which aggregates the data needed by the forecast. It contains the following statement.

        RELATION line.parentrel

2.  Define the second aggmap, named `forecast.agg2`, which aggregates the data generated using the first aggmap and the forecast. It contains the following statement.

        RELATION division.parentrel PRECOMPUTE ('L3')

3.  Define the third aggmap, named `forecast.agg3`, which contains the RELATION statements in the specifications of the first two aggmaps.

        RELATION line.parentrel
        RELATION division.parentrel PRECOMPUTE ('L3')

When your forecast is in a program named `fore.prg`, then you would use the following statements to aggregate the data.

    AGGREGATE budget USING forecast.agg1   "Aggregate over LINE
    CALL fore.prg                          "Forecast over TIME
    AGGREGATE budget USING forecast.agg2   "Aggregate over DIVISION
    "Compile the limit map for LINE and DIVISION
    COMPILE forecast.agg3
    "Use the combined aggmap for the AGGREGATE function
    CONSIDER budget
    PROPERTY 'NATRIGGER' 'AGGREGATE(budget USING forecast.agg3)'

Example 9-11 Using an AGGINDEX Statement in an Aggregation Specification

Suppose you have two variables, `sales1` and `sales2`, with the following definitions.

    DEFINE sales1 DECIMAL <time, SPARSE<product, channel, customer>>
    DEFINE sales2 DECIMAL <time, SPARSE<product, channel, customer>>

You do not want to precompute and commit all of the `sales` data to the database, because disk space is limited and you must improve performance. Therefore, you must create an aggmap, in which you specify which data should be pre-computed and which data should be calculated on the fly.

You define the aggmap, named `sales.agg`, with the following statement.

    DEFINE sales.agg AGGMAP <time, SPARSE<product, channel, customer>>

Next, you use an AGGMAP statement to enter the following specification for `sales.agg`.

    RELATION time.r PRECOMPUTE (time NE 'Year99')
    RELATION product.r PRECOMPUTE (product NE 'All')
    RELATION channel.r
    RELATION customer.r
    AGGINDEX NO

This aggregation specification tells Oracle OLAP that all `sales` data should be rolled up and committed to the database except for any data that has a `time` dimension value of `Year99` or a `product` dimension value of `All`—the data for those cells is calculated the first time a user accesses them. The AGGINDEX value of `NO` tells Oracle OLAP not to create the indexes for data that should be calculated on the fly.

Now you execute the following statement.

    sales2 = AGGREGATE(sales1 USING sales.agg) ACROSS SPARSE -
       <product, channel, customer>

`sales2` now contains all of the data in `sales1`, plus any data that is aggregated for `Year99`—this is because `time` is not included in a composite.

On the other hand, the data that is aggregated for the `product` value of` All` is not computed and stored in `sales2`. This data is not computed or stored because the `product` dimension is included in a composite—the indexes that are required for dimensions that are included in composites were not created because the aggregation specification contains an `AGGINDEX` `NO` statement. Because the indexes did not exist, Oracle OLAP never called the AGGREGATE function to compute the data to be calculated on the fly.

Example 9-12 Aggregating By Dimension Attributes

Assume that when your business makes a sales it keeps records of the customer's name, sex, age, and the amount of the sale. To hold this data, your analytic workspace contains a dimension named `customer` and three variables (named `customer_sex`, `customer_age`, and `sales`) that are dimensioned by `customer`.

     REPORT W 14 <customer_sex customer_age sales>

    CUSTOMER        CUSTOMER_SEX   CUSTOMER_AGE      SALES
    -------------- -------------- -------------- --------------
    Clarke         M                          26      26,000.00
    Smith          M                          47      15,000.00
    Ilsa           F                          24      33,000.00
    Rick           M                          33      22,000.00

You want to aggregate the detail sales data over sex and age to calculate the amount of sales you have made to males and females, and the amount of sales for different age ranges. To hold this data you need an `INTEGER` variable that is dimensioned by hierarchical dimensions for sex and age. You also need an aggmap object that specifies the calculations that Oracle OLAP performs to populate this variable from the data in the `sales` variable.

To create and populate the necessary objects, you take the following steps:

1.  Create and populate dimensions and self-relations for hierarchical dimensions named `sex` and `age`.

        DEFINE sex DIMENSION TEXT
        DEFINE sex.parentrel RELATION sex <sex>
        DEFINE age DIMENSION TEXT
        DEFINE age.parentrel RELATION age <age>

        AGE               AGE.PARENTREL
        -------------- --------------------
        0-20           All
        21-30          All
        31-50          All
        51-100         All
        No Response    All
        All            NA

        SEX               SEX.PARENTREL
        -------------- --------------------
        M              All
        F              All
        No Reponse     All
        All            NA

2.  Create and populate relations that map the `age` and `sex` dimensions to the `customer` dimension.

        DEFINE customer.age.rel RELATION age <customer>
        DEFINE customer.sex.rel RELATION sex <customer>

        CUSTOMER         CUSTOMER.AGE.REL     CUSTOMER.SEX.REL
        -------------- -------------------- --------------------
        Clarke         21-30                M
        Smith          31-50                M
        Ilsa           21-30                F
        Rick           31-50                M

3.  Create a variable named `sales_by_sex_age` to hold the aggregated data. Like the `sales` variable this variable is of type DECIMAL, but it is dimensioned by `sex` and `age` rather than by `customer`.

        DEFINE sales_by_sex_age VARIABLE DECIMAL <sex age>

4.  Define an AGGMAP type aggmap object named `ssa_aggmap` to calculate the values of the `sales_by_sex_age` variable.

        DEFINE SSA_AGGMAP AGGMAP
        AGGMAP
        RELATION sex.parentrel OPERATOR SUM
        RELATION age.parentrel OPERATOR SUM
        BREAKOUT DIMENSION customer -
        BY customer.sex.rel, customer.age.rel OPERATOR SUM
        END

    Notice that the specification for the `ssa_aggmap` includes the following statements:

    - A BREAKOUT DIMENSION statement that specifies how to map the `customer` dimension of the `sales` variable to the lowest-level values of the `sales_by_sex_age` variable. This statement specifies the name of the dimension of the variable that contains the detail values (that is, `customer`) and the names of the relations (`customer.sex.rel` and `customer.age.rel`) that define the relations between `customer` dimension and the `sex `and `age` dimensions.

    - Two RELATION statements that specify how to aggregate up the `sex` and `age` dimensions of the `sales_by_sex_age` variable. Each of these statements includes the name of the child-parent relation (`sex.parentrel` or `age.parentrel`) that define the self-relation for the hierarchal dimension (`sex` or `age`).

5.  Populate the `sales_by_sex_age` variable by issuing an AGGREGATE command that specifies that the detail data for the aggregation comes from the `sales` variable.

        AGGREGATE sales_by_sex_age USING ssa_aggmap FROM sales

    After performing the aggregation, a report of `sales_by_sex_age` shows the calculated values.

                       ---------------------SALES_BY_SEX_AGE----------------------
                       ----------------------------SEX----------------------------
        AGE                  M              F          No Reponse        All
        -------------- -------------- -------------- -------------- --------------
        0-20                       NA             NA             NA             NA
        21-30               26,000.00      33,000.00             NA      59,000.00
        31-50               37,000.00             NA             NA      37,000.00
        51-100                     NA             NA             NA             NA
        No Response                NA             NA             NA             NA
        All                 63,000.00      33,000.00             NA      96,000.00

Example 9-13 Using a CACHE Statement in an Aggregation Specification

Suppose you have a `sales` variable with the following definition.

    DEFINE sales DECIMAL <time, SPARSE<product, channel, customer>>

You do not want to pre-compute and commit all of the `sales` data, because space is limited and you must improve performance. Therefore, you must create an aggmap, in which you specify which data should be pre-computed and which data should be calculated on the fly.

You define the aggmap, named `sales.agg`, with the following statement.

    DEFINE sales.agg AGGMAP <time, SPARSE<product, channel, - customer>>

Next, you use the AGGMAP statement to enter the following aggregation specification for`sales.agg`.

    AGGMAP
    RELATION time.r PRECOMPUTE (time NE 'YEAR99')
    RELATION product.r PRECOMPUTE (product NE 'ALL')
    RELATION channel.r
    RELATION customer.r
    CACHE SESSION
    END

This aggregation specification tells Oracle OLAP that all `sales` data should be rolled up and committed, except for any cells that have a time dimension value of `Year99` or a product dimension value of `ALL`; the data for those cells is calculated the first time a user accesses them. Because the CACHE statement uses the SESSION keyword, that means that when those cells are calculated on the fly, the data is stored in the cache for the remainder of the Oracle OLAP session. That way, the next time a user accesses the same cell, the data does not have to be calculated again. Instead, the data is retrieved from the session cache.

Example 9-14 Populating All Levels of a Hierarchy Except the Detail Level

Assume that your analytic workspace contains the relations and dimensions with the following definitions.

    DEFINE geog.d TEXT DIMENSION
    DEFINE geog.r RELATION geog.d <geog.d>
    DEFINE sales_by_units   INTEGER VARIABLE <geog.d>
    DEFINE sales_by_revenue DECIMAL VARIABLE <geog.d>
    DEFINE price_per_unit   DECIMAL VARIABLE <geog.d>

Assume that you create two aggmap objects. One aggmap object, named `units_aggmap`, is the specification to aggregate data in the `sales_by_units` variable. The other aggmap object, `revenue_aggmap`, is the specification to calculate all of the data except the detail data in the `sales_by_revenue` variable.

    DEFINE units_aggmap AGGMAP
    AGGMAP
      RELATION geog.r OPERATOR SUM
    END

    DEFINE revenue_aggmap AGGMAP
    AGGMAP
      RELATION geog.r OPERATOR WSUM ARGS WEIGHTBY price_per_unit
      CACHE NOLEAF
    END

The following steps outline the aggregation process:

1.  Before either the `sales_by_unit` or `sales_by_revenue` variables are aggregated, they have the following values.

        GEOG.D    SALES_BY_UNIT SALES_BY_REVENUE
        --------- ------------- ----------------
        Boston                1               NA
        Medford               2               NA
        San Diego             3               NA
        Sunnydale             4               NA
        MA                    NA              NA
        CA                    NA              NA
        USA                   NA              NA

2.  After the data for the `sales_by_unit` variable is aggregated, the `sales_by_unit` and `sales_by_revenue` variables have the following values.

        AGGREGATE sales_by_unit    USING units_aggmap

        GEOG.D    SALES_BY_UNIT SALES_BY_REVENUE
        --------- ------------- ----------------
        Boston                1               NA
        Medford               2               NA
        San Diego             3               NA
        Sunnydale             4               NA
        MA                    3               NA
        CA                    7               NA
        USA                  10               NA

3.  After the data for the `sales_by_revue` variable is aggregated, the `sales_by_unit` and `sales_by_revenue` variables have the following values.

        AGGREGATE sales_by_revenue USING revenue_aggmap FROM units_aggmap

        GEOG.D    SALES_BY_UNIT SALES_BY_REVENUE
        --------- ------------- ----------------
        Boston                1               NA
        Medford               2               NA
        San Diego             3               NA
        Sunnydale             4               NA
        MA                    3             13.5
        CA                    7             31.5
        USA                  10             45.0

Example 9-15 Aggregating into a Different Variable

Assume that there is a variable named `sales` that is dimensioned by `time`, a hierarchical dimension, and `district`, a non-hierarchical dimension.

    DEFINE time DIMENSION TEXT
    DEFINE time.parentrel RELATION time <time>
    DEFINE district DIMENSION TEXT
    DEFINE sales VARIABLE DECIMAL <time district>

                 -----------------------SALES-----------------------
                 ---------------------DISTRICT----------------------
    TIME            North        South         West         East
    ------------ ------------ ------------ ------------ ------------
    1976Q1         168,776.81   362,367.87   219,667.47   149,815.65
    1976Q2         330,062.49   293,392.29   237,128.26   167,808.03
    1976Q3         304,953.04   354,240.51   170,892.80   298,737.70
    1976Q4         252,757.33   206,189.01   139,954.56   175,063.51
    1976                   NA           NA           NA           NA

Assume also that you want to calculate the total sales for each quarter and year for all districts except the `North` district. To perform this calculation using an aggmap object, you take the following steps:

1.  Create a valueset named `not_north` that represents the values of `district` for which you want to aggregate data.

        DEFINE not_north VALUESET district
        LIMIT not_north TO ALL
        LIMIT not_north REMOVE 'North'

2.  Define a variable named `total_sales_exclud_north` to hold the results of the calculation.

        DEFINE total_sales_exclud_north VARIABLE DECIMAL <time>

    Notice that, like `sales`, the `total_sales_exclud_north` variable is dimensioned by time. However, unlike `sales`, the `total_sales_exclud_north` variable is not dimensioned by `district` because it holds detail data for each district, but only the total (aggregated) values for the `South`, `West`, and `East` districts (that is, all districts except `North`).

3.  Define an aggmap object that specifies the calculation that you want performed.

        DEFINE agg_sales_exclud_north AGGMAP
        AGGMAP
        RELATION time.parentrel OPERATOR SUM
        DROP DIMENSION district OPERATOR SUM VALUES not_north
        END

    Notice that the aggregation specification consists of two statements that specify how to perform the aggregation:

    - A RELATION statement that specifies how to aggregate up the hierarchical `time` dimension

    - A DROP DIMENSION statement that specifies how to aggregate across the non-hierarchical `district` dimension. In this case, the DROP DIMENSION also uses the `not_north` valueset to specify that values for the `North` district are excluded when performing the aggregation

4.  Aggregate the data.

        AGGREGATE total_sales_exclud_north USING agg_sales_exclud_north FROM sales

    The report of the `total_sales_exclud_north` variable shows the aggregated values.

        TIME             ALL_SALES_EXCEPT_NORTH
        ------------ ------------------------------
        1976Q1                           731,850.99
        1976Q2                           698,328.58
        1976Q3                           823,871.02
        1976Q4                           521,207.09
        1976                           2,775,257.69

Example 9-16 Using a MEASUREDIM Statement in an Aggregation Specification

Suppose you have defined a measure dimension named `measure`. You then define an operation variable named `myopvar`, which is dimensioned by `measure`. When you use `myopvar` in an aggregation specification, you must also include a MEASUREDIM statement that identifies `measure` as the dimension is included in the definition of `myopvar`.

The MEASUREDIM statement should follow the last RELATION statement in the aggregation specification, as shown in the following example.

    DEFINE sales.agg AGGMAP <time, product, geography>
    AGGMAP
    RELATION time.r OPERATOR myopvar
    RELATION product.r
    RELATION geography.r
    MEASUREDIM measure
    END

Example 9-17 Solving a Model in an Aggregation

This example uses the `budget` variable.

    DEFINE budget VARIABLE DECIMAL <line time>
    LD Budgeted $ Financial

The `time` dimension has two hierarchies (`Standard` and `YTD`) and a parent relation named `time.parentrel` as follows.

                   -----TIME.PARENTREL------
                   ----TIME.HIERARCHIES-----
    TIME             Standard       YTD
    -------------- ------------ ------------
    Last.YTD       NA           NA
    Current.YTD    NA           NA
    Jan01          Q1.01        Last.YTD
    ...
    Dec01          Q4.01        Last.YTD
    Jan02          Q1.02        Current.YTD
    Feb02          Q1.02        Current.YTD
    Mar02          Q1.02        Current.YTD
    Apr02          Q2.02        Current.YTD
    May02          Q2.02        Current.YTD
    Q1.01          2001         NA
    ...
    Q4.01          2001         NA
    Q1.02          2002         NA
    Q2.02          2002         NA
    2001           NA           NA
    2002           NA           NA

The relationships among line items are defined in the following model.

    DEFINE income.budget MODEL
    MODEL
    DIMENSION line time
    opr.income = gross.margin - marketing
    gross.margin = revenue - cogs
    revenue = LAG(revenue, 12, time) * 1.02
    cogs = LAG(cogs, 1, time) * 1.01
    marketing = LAG(opr.income, 1, time) * 0.20
    END

The following aggregation specification pre-aggregates all of the data. Notice that all of the data must be pre-aggregated because the model includes both LAG functions and a simultaneous equation.

    DEFINE budget.aggmap1 AGGMAP
    AGGMAP
    MODEL income.budget
    RELATION time.parentrel
    END

Example 9-18 Aggregating Up a Hierarchy

Suppose you define a `sales` variable with the following statement.

    DEFINE sales VARIABLE <time, SPARSE <product, geography>>

The aggregation specification for `sales` might include RELATION statements like the following.

    AGGMAP
    RELATION time.r PRECOMPUTE ('Yr98', 'Yr99')
    RELATION product.r
    RELATION geography.r PRECOMPUTE (geography NE 'Atlanta')
    END

The AGGREGATE command aggregates values for `Yr98` and `Yr99`, over all of products, and over all geographic areas except for `Atlanta`. All other aggregates are calculated on the fly.

Example 9-19 Using Valuesets

Suppose you have a hierarchy dimension named time.type, whose dimension values are `Fiscal` and `Calendar`, in that order. These hierarchies are in conflict, and you want to precompute some `time` data but calculate the rest on the fly. Because the `Calendar` hierarchy is the last dimension value in the hierarchy dimension, consequently, you must define a valueset to get the correct results for the `Fiscal` hierarchy.

First, use the following statements to define and populate a valueset.

    DEFINE time.vs VALUESET time
    LIMIT time.vs TO 'Calendar' 'Fiscal'

You can then use the valueset in the following RELATION statement. Because the Fiscal hierarchy is the last hierarchy in the valueset, the data that is aggregated is accurate for the Fiscal hierarchy.

    RELATION time.r(time.vs) PRECOMPUTE ('Yr99', 'Yr00')

Example 9-20 Aggregating with a RELATION Statement That Uses an ARGS Keyword

You can list the arguments in a RELATION statement directly in the statement or as the value of a text variable. For example, the following statement specifies `WEIGHTBY wobj` as an argument.

    RELATION time.r OPERATOR wsum ARGS WEIGHTBY wobj

Alternatively, you can define an variable for the argument whose value is the text of the WEIGHTBY clause.

    DEFINE argvar TEXT
    argvar = 'WEIGHTBY wobj'

Then the RELATION statement can specify the text variable that contains the WEIGHTBY clause.

    RELATION time.r OPERATOR WSUM ARGS argvar

Example 9-21 Aggregating Using a Measure Dimension

Suppose you want to use a single AGGREGATE command to aggregate the `sales`, `units`, `price`, and `inventory` variables. When you want to use the same operator for each variable, then you do not have to use a measure dimension. However, when you want to specify different aggregation operations, then you must use a measure dimension.

The following statement defines a dimension named `measure`.

    DEFINE measure DIMENSION TEXT

You can then use a MAINTAIN statement to add dimension values to the `measure` dimension.

    MAINTAIN measure ADD 'sales', 'units', 'quota', 'inventory'

Use the `measure` dimension to dimension a text variable named `meas.opvar` that you use as the operator variable.

    DEFINE meas.opvar TEXT WIDTH 2 <measure>

The following statements add values to OPVAR

    meas.opvar (measure 'sales') = 'SU'
    meas.opvar (measure 'units') = 'SU'
    meas.opvar (measure 'price') = 'HA'
    meas.opvar (measure 'inventory') = 'HL'

The aggregation specification might look like the following. Note that when you specify an operator variable in a RELATION statement, you must include a MEASUREDIM statement that specifies the name of the measure dimension (`measure` in the following example) in the aggregation specification.

    DEFINE opvar.aggmap AGGMAP
    AGGMAP
    RELATION geography.parentrel PRECOMPUTE (geography.lvldim 2 4)
    RELATION product.parentrel OPERATOR opvar
    RELATION channel.parentrel OPERATOR opvar
    RELATION time.parentrel OPERATOR opvar
    MEASUREDIM measure
    END

Example 9-22 Aggregating Using a Line Item Dimension

Suppose you have two variables, `actual` and `budget`, that have these dimensions.

    <time line division>

You want to use different methods to calculate different line items. You create a text variable that you use as the operator variable.

    DEFINE line.opvar TEXT WIDTH 2 <line>

You then populate `line.opvar` with the appropriate operator for each line item, for example.

    line.opvar (line 'Net.Income') = 'SU'
    line.opvar (line 'Tax.Rate') = 'AV'

 The aggregation specification might look like this.

    DEFINE LINE.AGGMAP AGGMAP
    AGGMAP
    RELATION time.parentrel OPERATOR line.opvar
    RELATION division.parentrel
    END

Example 9-23 Skip-Level Aggregation

Suppose you want to aggregate `sales` data. The `sales` variable is dimensioned by `geography`, `product`, `channel`, and `time`.

First, consider the hierarchy for each dimension. How many levels does each hierarchy have? What levels of data do users typically query? When you are designing a new workspace, what levels of data do your users plan to query?

Suppose you learn the information described in the following table about how users tend to query `sales` data for the `time` hierarchy.

| Time Level Names | Descriptive Level Name | Examples of Dimension Values | Do users query this level often? |
|:-----------------|:-----------------------|:-----------------------------|:---------------------------------|
| L1               | Year                   | `Year99`, `Year00`           | yes                              |
| L2               | Quarter                | `Q3.99`, `Q3.99`, `Q1.00`    | yes                              |
| L3               | Month                  | `Jan99`, `Dec00`             | yes                              |

While the next table shows how your users tend to query `sales` data for the `geography` hierarchy.

| Geography Level Names | Descriptive Level Name | Examples of Dimension Values | Do users query this level often? |
|:----------------------|:-----------------------|:-----------------------------|:---------------------------------|
| L1                    | World                  | `World`                      | yes                              |
| L2                    | Continent              | `Europe, Americas`           | no                               |
| L3                    | Country                | `Hungary, Spain`             | yes                              |
| L4                    | City                   | `Budapest, Madrid`           | yes                              |

Finally, the next table shows how your users tend to query `sales` data for the `product` dimension hierarchy.

| Product Level Names | Descriptive Level Name | Examples of Dimension Values | Do users query this level often? |
|:--------------------|:-----------------------|:-----------------------------|:---------------------------------|
| L1                  | All Products           | `Totalprod`                  | yes                              |
| L2                  | Division               | `Audiodiv, Videodiv`         | yes                              |
| L3                  | Category               | `TV, VCR`                    | yes                              |
| L4                  | Product                | `Tuner, CDplayer`            | yes                              |

Using this information about how users query data, use the following strategy for aggregation:

- Fully aggregate `time` and `product` because all levels are queried frequently.

- For the `geography` dimension, aggregate data for `L1` (`World`) and `L3` (`Country`) because they are queried frequently. However, `L2` is queried less often and so can be calculated on the fly.

The lowest level of data was loaded into the analytic workspace. The aggregate data is calculated from this source data.

Therefore, the aggregation specification might look like the following.

    RELATION time.parentrel
    RELATION geography.parentrel PRECOMPUTE (geog.leveldim 'L3' 'L1')
    RELATION product.parentrel

Example 9-24 Aggregation Specification with RELATION Statements That Include PRECOMPUTE Clauses

This aggregation specification uses PRECOMPUTE clauses in the RELATION statements to limit the data that is aggregated by the AGGREGATE command.

    DEFINE gpct.aggmap AGGMAP
    LD Aggmap for sales, units, quota, costs
    AGGMAP
    RELATION geography.parentrel PRECOMPUTE (geography.levelrel 'L3')
    RELATION product.parentrel PRECOMPUTE (LIMIT(product complement 'TotalProd'))
    RELATION channel.parentrel
    RELATION time.parentrel PRECOMPUTE (time NE '2001')
    END

#### 9.9.1 AGGINDEX

Within an aggregation specification used with a non-compressed cube, an AGGINDEX statement tells Oracle OLAP whether the AGGREGATE command should create indexes (meaning, composite tuples) for data cells that it calculates on the fly. The AGGINDEX statement signals the AGGREGATE command to create composite tuples for any dimension that is included in a composite.

These indexes are used by the MODEL statement in an AGGMAP and by statements that use the ACROSS phrase to help Oracle OLAP loop over variables that are dimensioned by composites. These statements expect all data to be calculated. When you specify calculating some data on the fly, that data appears to be missing. When you set AGGINDEX to `YES`, then the statements try to access the missing data whether or not you are using the AGGREGATE function to perform calculation on the fly (meaning, you have added to the variable whose data is being aggregated an `NA` trigger property that calls the AGGREGATE function).

When the indexes have been created and you use the AGGREGATE function, then when MODEL (or a statement that uses the ACROSS phrase) requests the missing data, that data is calculated on the fly. That means that the results of the MODEL (or other statement) are correct, because the statement has all of the data that it needs.

When these indexes have not been created, the missing data cannot be calculated. Consequently, the statements that need the indexes interpret the missing data as `NA` data, even when you use the AGGREGATE function.

##### Syntax

AGGINDEX {YES\|NO}

##### Parameters

YES
(Default) Ensures that all possible indexes are created whenever the AGGREGATE command is used with an aggmap. Indexes are created both for the data that is being pre-calculated and the data that is calculated on the fly. The creation of all possible indexes results in the AGGREGATE command taking longer to execute. For a discussion of when AGGINDEX should be set to YES, see "When To Use an AGGINDEX Value of YES " in the Usage Notes..

NO
Does not create the indexes for data that is calculated on the fly. Omitting the creation of these index values accelerates execution of the AGGREGATE command, but causes Oracle OLAP to treat the uncomputed data as `NA` data whenever the MODEL statement in an AGGMAP or an ACROSS phrase is executed. For a discussion of when AGGINDEX should be set to NO, see "When To Use an AGGINDEX Value of NO " in the Usage Notes.

##### Usage Notes

When To Use an AGGINDEX Value of YES

The primary advantage to using an AGGINDEX value of YES is that then Oracle OLAP always tries to access data that you have specified to be calculated on the fly. When you have created an \$NATRIGGER property for a variable that calls the AGGREGATE function, the variable appears to have been fully precomputed. That means that when any NA value is encountered, the NA trigger is called during the execution of an ACROSS phrase or the MODEL statement in an AGGMAP. When the NA trigger is called, the AGGREGATE function is executed, and the data is calculated on the fly.

The primary advantage to using an AGGINDEX value of `YES` is that then Oracle OLAP always try to access data that you have specified to be calculated on the fly. When you have created an \$NATRIGGER property for a variable that calls the AGGREGATE function, the variable appears to have been fully precomputed. That means that when any `NA` value is encountered, the `NA` trigger is called during the execution of an ACROSS phrase or the MODEL statement in an AGGMAP. When the `NA` trigger is called, the AGGREGATE function is executed, and the data is calculated on the fly.

When AGGINDEX has a value of `NO`, then the `NA` trigger is called only to aggregate data for composite tuples that have been materialized and for all of the values of dimensions not included in the composite. Data for composite dimensions that is not PRECOMPUTED is interpreted as `NA` values.

For example, suppose you have two variables called `sales1` and `sales2`, which are defined with the following definitions.

    DEFINE sales1 DECIMAL <time, SPARSE <product, geography>>
    DEFINE sales2 DECIMAL <time, SPARSE <product, geography>>

Now suppose you have an aggmap object named `sales.agg`, which has the following definition.

    DEFINE sales.agg AGGMAP

When you add a specification to the `sales.agg` aggmap, you enter RELATION statements for `time`, `product` and `geography` with `PRECOMPUTE` clauses that specify `NA` which specifies that no data is aggregated—instead, all of the data for any variable that uses this aggmap is calculated on the fly.

    RELATION time.r PRECOMPUTE (NA)
    RELATION product.r PRECOMPUTE (NA)
    RELATION geography.r PRECOMPUTE (NA)
    AGGINDEX YES

Now attach the following \$NATRIGGER property to the `sales1` variable.

    CONSIDER sales1
    PROPERTY '$NATRIGGER' 'AGGREGATE(sales1 USING sales.agg)'

Now call the AGGREGATE command on sales1 to instantiate the index values.

    AGGREGATE sales1 using sales.agg

Consider the effect of AGGINDEX in the following statement, when the aggmap specifies AGGINDEX `YES`.

    sales2 = sales1 ACROSS SPARSE <product, geography>

This statement loops over the data in `sales1` and copies the values into `sales2`. This statement causes the `NA` trigger to call the AGGREGATE function for all of the data that you have specified to be calculated on the fly in `sales1`. Consequently, after the aggregation that `sales2` contains a copy of `sales1` plus all the aggregate data cells (the cells that would have been calculated if the `sales1` data had been completely precomputed, meaning, fully rolled up).

However, when you put an AGGINDEX `NO` statement in the `sales.agg` aggregation specification, then `sales2` contains a copy of the data in `sales1` and the aggregate data cells for the leaf values of the composite dimensions.

Note that in both cases, \$NATRIGGER is called to aggregate `time` data, because the `time` dimension is not included in the composite, so the value of AGGINDEX has no effect on it.

When To Use an AGGINDEX Value of NO

You can use an AGGINDEX value of `NO` when you know that either of the following is true:

- Your application does not contain an ACROSS phrase or a MODEL statement in an AGGMAP command.

- The MODEL statement in the aggmap appears before the RELATION statements. The results of your MODEL statements or ACROSS phrases are additive, and data that needs to be aggregated can be calculated safely on the fly.

Each of the preceding cases ensures that the data that you have specified to be calculated on the fly is available at the appropriate time.

By setting AGGINDEX to `NO`, the size of the indexes is reduced, and overall application performance improves.

When Using an AGGINDEX Value Of NO Causes Problems

When you run a MODEL that assumes all data that should be aggregated has been aggregated, then you may get `NA` data where real data should occur. For instance, suppose you have a variable that has a composite that includes the `time` dimension. You perform a calculation that subtracts the fourth quarter from the total for the year. When the value of `Year` is to be calculated dynamically, and the AGGINDEX statement is set to `NO`, then the result of the calculation is `NA`. When the value of `Year` was precomputed or when AGGINDEX is set to `YES`, then the MODEL correctly calculates a result equal to the sum of the first three quarters.

Index Creation Is Based on Existing Data

Only the indexes that are needed to aggregate existing data are created when AGGINDEX has a value of `YES`. For example, suppose one dimension in your composite is a dimension named `time`. The lowest-level data for the `time` dimension is at the monthly level. Therefore, the dimension values that are associated with the lowest-level data are `Jan99`, `Feb99`, and so on. The monthly data aggregates to quarters and to years. Suppose you have data for the first six months of the year. When AGGINDEX has a value of `YES`, indexes are created for the `Q1`, `Q2`, and `Yr99` dimension values, but not for `Q3` and `Q4`.

##### Examples

For an example of using an AGGINDEX statement, see Example 9-11.

#### 9.9.2 BREAKOUT DIMENSION

Within an aggregation specification, a BREAKOUT DIMENSION statement specifies how a dimension of the target variable maps to one or more dimensions of the source variable. You use this statement in an aggregation specification when you are aggregating the detail data from one variable (the source variable) into another variable (the target variable) that has a different dimension (that is, a "breakout" dimension) than the variable that contains the detail data.

##### Syntax

BREAKOUT DIMENSION dimname BY relation \[, relation...\] -      OPERATOR operation \[ARGS argument\]

where:

`relation` has the following syntax:

    relationname \[IGNORE ignore_dim_value \[DEFAULT default_dim_value\]\]

`argument` specifies the settings of various options and is one or more of the following phrases:

-      `DIVIDEBYZERO {YES|NO}`
-      `DECIMALOVERFLOW {YES|NO}`
-      `NASKIP {YES|NO}`
-      `WEIGHTBY [WNAFILL {``number ``| NA}] ``wobj`

##### Parameters

dimname
The name of a dimension in the variable that contains the detail data (that is, the source variable).

relationname
The name of a relation whose values relate a dimension of the target variable to dimname.

IGNORE ignore_dim_value
Specifies that if the target dimension is QDRd to the value specified by ignore_dim-value then AGGREGATE does not use the relation specified by relationname to limit the source dimension.

DEFAULT default_dim_value
Specifies that if all relations have an IGNORE phrase, then AGGREGATE uses the value specified by default_dim-value value to create a QDR rather than using a relation. If all relations have an IGNORE phrase and you do not include a DEFAULT phrase, the AGGREGATE arbitrarily chooses a relationship to limit by.

when dimname is QDRd to the dimension value specified by ignore_dim-value then AGGREGATE does not use the relation specified by relationname to limit the source dimension

OPERATOR
Identifies the calculation method used to aggregate the data.

operation
A keyword that describes the type of aggregation to perform. The keywords are listed in the description of the operation parameter in the RELATION (for aggregation) statement of the AGGMAP command.

ARGS
Indicates optional handling of the aggregation.

DIVIDEBYZERO
Specifies whether to allow division by zero.

`YES` allows division by zero; a statement involving division by zero executes without error but produces `NA` results.

`NO` disallows division by zero; a statement involving division by zero stops executing and produces an error message.

The default value is the current value of the DIVIDEBYZERO option.

DECIMALOVERFLOW
Specifies whether to allow decimal overflow, which occurs when the result of a calculation is very large and can no longer be represented by the exponent portion of the numeric representation. Specify `YES` to allow overflow, which means that a calculation that generates overflow executes without error and produces `NA` results. Specify `NO` to disallow overflow, which means that; a calculation involving overflow stops executing and generates an error message. The default value is the current value of the DECIMALOVERFLOW option.

NASKIP
Specifies whether `NA` values are input. Specify `YES` when you want Oracle OLAP to ignore `NA` values when aggregating which means that only actual values are used in calculations. Specify `NO` when you want Oracle OLAP to consider `NA` values are considered which means that when any of the values being considered are `NA`, the calculation returns `NA`.The default value is the current value of the NASKIP option.

The value that you specify for the NASKIP phrase does not effect calculation performed when you specify HAVERAGE, HFIRST, HLAST, HWAVERAGE, HWFIRST, HWLAST for operation.

WEIGHTBY
Indicates that weighted aggregation is to be performed. You must include a WEIGHTBY clause when you specify HWAVERAGE, HWFIRST, HWLAST, SSUM, WAVERAGE, WFIRST, WLAST, or WSUM for operation. The WEIGHTBY phrase always includes a wobj argument and can optionally include the WNAFILL keyword. For more information about the use of the WEIGHTBY phrase, see RELATION (for aggregation) statement of the AGGMAP command.

WNAFILL
Indicates handling for `NA` values. The default values for WNAFILL vary depending on the value of operation.

`number`
Substitutes a number for every `NA` value. That number replaces every `NA` value in the weight object, weight formula, or weight relation. The default for HWAVERAGE and SSUM is The default for HWFIRST, HWLAST, WAVERAGE, WFIRST, WLAST, and WSUM is `1.0` .

`NA`
Specifies that `NA` values are to be specified as `NA`. `NA` is the default for OR.

For more information about using the WNAFILL phrase, see RELATION (for aggregation) statement of the AGGMAP command.

wobj
A variable, formula, or relation that provides the weighted values. It can be numeric or BOOLEAN. When wobj is BOOLEAN, then `TRUE` has a weight of `1.0` and `FALSE` has a weight of `0.0`. A formula is queried only when needed, depending on the dimensionality of the formula and the variable being aggregated. When wobj is a relation, it should be a one-dimensional self-relation. For more information about specifying values for wobj, see RELATION (for aggregation) statement of the AGGMAP command.

##### Examples

For an example of using the BREAKOUT DIMENSION statement, see Example 9-12.

#### 9.9.3 CACHE

Within an aggregation specification, a CACHE statement tells Oracle OLAP whether to cache or store the calculated data, whether to populate leaf or detail data when the variable data is aggregated using detail data from another variable, and whether to cache `NA` values when a summary values calculates to `NA`.

**Note:**

The CACHE statement is only one factor that determines whether variable data that has been aggregated on-the-fly using the AGGREGATE function is stored or cached. See "[How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER](olap-dml-properties.md)".

##### Syntax

CACHE {NOSTORE\|NONE\|STORE\|SESSION\|DEFAULT} \[LEAF\|NOLEAF\] \[NA\|NONA\]

##### Parameters

NONE
NOSTORE
For data that is calculated using the AGGREGATE function, specifies that Oracle OLAP calculates the data each time the AGGREGATE function executes. When you specify either of these keywords, Oracle OLAP does not store or cache the data calculated by the AGGREGATE function.

STORE
For data that is calculated using the AGGREGATE function, specifies that Oracle OLAP stores data calculated by the AGGREGATE function in the variable in the database. When you specify this option, the results of the aggregation are permanently stored in the variable when the analytic workspace is updated and committed.

SESSION
For data that is calculated using the AGGREGATE function, specifies that Oracle OLAP caches data calculated by the AGGREGATE function in the session cache (see "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)"). When you specify this option, the results of the aggregation are ignored during updates and commits and are discarded after the session.

**Note:**

When SESSCACHE is set to `NO`, Oracle OLAP does not cache the data even when you specify `SESSION`. In this case, specifying `SESSION` is the same as specifying `NONE`.

DEFAULT
(Default) For data that is calculated using the AGGREGATE function, specifies that Oracle OLAP uses the value of the VARCACHE option to determine what to do with data that is calculated by the AGGREGATE function. See "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)".

LEAF
When the variable data is aggregated using detail data from another variable, specifies that Oracle OLAP calculates the leaf data for the variable.

NOLEAF
(Default) When the variable data is aggregated using detail data from another variable, specifies that Oracle OLAP does not calculate the leaf data for the variable.

NA
For data that is calculated using the AGGREGATE function, specifies that Oracle OLAP places any `NA` values that are the results of the execution of the AGGREGATE function in the Oracle OLAP session cache. In this case, when there is a variable has an \$NATRIGGER property with an AGGREGATE function as its expression, Oracle OLAP does not recalculate the values for the variable. (For more information on the caching `NA` values, see "[How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER](olap-dml-properties.md)".)

NONA
For data that is calculated using the AGGREGATE function, specifies that Oracle OLAP does not cache any `NA` values that are the results of the execution of the AGGREGATE function. In this case, when a variable has an \$NATRIGGER property with an AGGREGATE function as its expression, Oracle OLAP recalculates the values for the variable.

##### Usage Notes

When to Use NOSTORE

Use NOSTORE when you know that your users are likely to modify pre-computed data, and you want any data that calculated by the AGGREGATE function to consistent with any of those users' changes.

In other words, suppose a user makes a change to detail-level data, such as `sales` figures for three stores, which are in a `geography` dimension. The `geography` dimension rolls up data from stores to cities to states to regions to countries. In other words, there are five levels in the `geography` dimension's hierarchy. Now suppose that users tend to access data only at the store level (your detail data), the regions level, and the countries level. Those are the levels for which you roll up sales data and commit it to the database. Because users do not access data at the city and state level, you specify that the data cells in those two levels are calculated on the fly. When users modify the store-level data and then access city data, the city data are calculated every time that a user requests it. Therefore, any changes that a user makes to the store-level details accurately rollup to the city and state level every time that user accesses a data cell in the city or state level. (However, this is not true of the data in the region and country levels, because those cells store pre-computed data.)

When to Use STORE or SESSION

The advantage to using STORE or SESSION is that it improves query performance. For example, suppose your users use a Table tool to look at a variable's data and an individual user requests the same data cells several times in the same session. When you use the default of NOSTORE, then any data that is not aggregated using the AGGREGATE command has to be calculated every time the user requests that data even if you do not use the FORECALC keyword in the AGGREGATE function. On the other hand, when you use STORE or SESSION, then any given cell of data is calculated only once because it is available in either the variable or the cache for the entire session. Therefore, the next time a user requests that data cell, the data is returned from the variable or the cache instead of being calculated on the fly, which results in faster query time for the user.

Frequently you do not want the data that is calculated using the AGGREGATE function to be stored permanently in the database because that would defeat the purpose of calculating data on the fly.

- To ensure that the aggregated values cannot be permanently committed to the database, use SESSION.

- Use STORE when you know either of the following is true which also ensures that the data that is calculated on the fly using the AGGREGATE function is not committed to the database:

  - The users of the analytic workspace can only open it as read-only

  - You know that the users of the analytic workspace will not or cannot issue UPDATE and COMMIT statements.

    **Note:**

    Use STORE with caution when it is likely that your users modify pre-computed data, and they access data that you have specified to be calculated on the fly using the AGGREGATE function. The problem is that any data that is calculated using the AGGREGATE function before the user's modification does not reflect the user's change unless the user made the change using an AGGREGATE function with the FORCECALC keyword or unless there is an \$AGGREGATE_FORCECALC property on the variable being aggregated

##### Examples

For examples of using a CACHE statement in an aggregation specification, see Example 9-13 and Example 9-14.

#### 9.9.4 DIMENSION (for aggregation)

Within an aggregation specification, a DIMENSION statement sets the status to a single value of a dimension. When an aggregation specification does not specify such single values with DIMENSION statements, Oracle OLAP uses the current status values of the dimensions when performing the aggregation.

You use a DIMENSION statement to ensure that the status of a dimension is set to the value that you want it to have for the aggregation. You must use a separate DIMENSION statement for each dimension that is not shared by the source, basis, and target objects.

##### Syntax

DIMENSION dimension 'dimval '

##### Parameters

dimension
the name of the dimension to limit.

dimval
A `TEXT` expression that is the single value of the dimension to which you want the status of the dimension set for the duration of an aggregation.

#### 9.9.5 DROP DIMENSION

Within an aggregation specification, a DROP DIMENSION statement specifies how non-hierarchical aggregation across variables is performed. You use this statement in aggregation specification when you are aggregating the detail data from one variable (the source variable) into another variable (the target variable) and you want to aggregate across a non-hierarchical dimension of the source variable. In this case, the target variable has one less dimension (the "dropped" dimension) than the source variable because the values of the source variable associated with this dimension are aggregated to populate the target variable.

##### Syntax

DROP DIMENSION dimname \[VALUES {valsetname\|ALL}  OPERATOR operation \[ARGS argument\]

where `argument` is one or more of the following phrases:

     DIVIDEBYZERO {YES\|NO}      DECIMALOVERFLOW {YES\|NO}      NASKIP {YES\|NO}      WEIGHTBY \[WNAFILL {number\|NA}\] wobj

##### Parameters

dimname
The name of a dimension in the source variable that contains the detail data.

VALUES
Sets the status of dimname during the aggregation.

valueset
The name of a valueset object that determines the status of the dimension specified by dimname.

ALL
Specifies that all of the values of dimname are in status.

OPERATOR
Identifies the calculation method used to aggregate the data.

operation
A keyword that describes the type of aggregation to perform. The keywords are listed in the description of the operation parameter in the RELATION (for aggregation) statement of the AGGMAP command.

ARGS
Indicates optional handling of the aggregation.

DIVIDEBYZERO
Specifies whether to allow division by zero. Specify `YES` to allow division by zero which means that a statement involving division by zero executes without error but produces `NA` results. Specify `NO` to disallow division by zero which means that a statement involving division by zero stops executing and produces an error message. The default value is the current value of the DIVIDEBYZERO option.

DECIMALOVERFLOW
Specifies whether to allow decimal overflow, which occurs when the result of a calculation is very large and can no longer be represented by the exponent portion of the numeric representation. Specify `YES` to allow overflow, which means that a calculation that generates overflow executes without error and produces `NA` results. Specify `NO` to disallow overflow which means that a calculation involving overflow stops executing and generates an error message. The default value is the current value of the DECIMALOVERFLOW option.

NASKIP
Specifies whether `NA` values are input. Specify `YES` when you want Oracle OLAP to ignore `NA` values when aggregating which means that only actual values are used in calculations. Specify `NO` when you want Oracle OLAP to consider `NA` values when aggregating which means that when any of the values being considered are `NA`, the calculation returns `NA`. The default value is the current value of the NASKIP option.

The value that you specify for the NASKIP phrase does not effect calculation performed when you specify HAVERAGE, HFIRST, HLAST, HWAVERAGE, HWFIRST, HWLAST for operation.

WEIGHTBY
Indicates that weighted aggregation is to be performed. You must include a WEIGHTBY clause when you specify HWAVERAGE, HWFIRST, HWLAST, SSUM, WAVERAGE, WFIRST, WLAST, or WSUM for operation. The WEIGHTBY phrase always includes a wobj argument and can optionally include the WNAFILL keyword. For more information about the use of the WEIGHTBY phrase, see the RELATION (for aggregation) statement of the AGGMAP command.

WNAFILL
Indicates handling for `NA` values. The default values for WNAFILL vary depending on the value of operation. For more information about using the WNAFILL phrase, see the RELATION (for aggregation) statement of the AGGMAP command.

number
Substitutes a number for every `NA` value. That number replaces every `NA` value in the weight object, weight formula, or weight relation.

- `0.0` is the default for HWAVERAGE and SSUM.

- `1.0` is the default for HWFIRST, HWLAST, WAVERAGE, WFIRST, WLAST, and WSUM.

`NA`
Specifies that `NA` values are to be specified as `NA`. `NA` is the default for OR.

wobj
A variable, formula, or relation that provides the weighted values. It can be numeric or BOOLEAN. When wobj is BOOLEAN, then `TRUE` has a weight of `1.0` and `FALSE` has a weight of `0.0`. A formula is queried only when needed, depending on the dimensionality of the formula and the variable being aggregated. When wobj is a relation, it should be a one-dimensional self-relation. For more information about specifying values for wobj, see the RELATION (for aggregation) statement of the AGGMAP command.

##### Examples

For an example of using a DROP DIMENSION statement in an aggregation specification, see Example 9-15.

#### 9.9.6 MEASUREDIM (for aggregation)

Within an aggregation specification, a MEASUREDIM statement identifies the name of a measure dimension that is specified in the definition of an operator variable or an argument variable.

##### Syntax

MEASUREDIM name

##### Parameters

name
The name of the measure dimension. A measure dimension is a dimension that you define. The dimension values are names of existing variables.

**Note:**

You cannot specify a measure dimension when it is included in the definition of the aggmap object.

##### Usage Notes

Defining a Measure Dimension

The following statement defines a dimension named MEASURE.

    DEFINE measure DIMENSION TEXT

Populating a Measure Dimension

Once you have defined a measure dimension, you can then use a MAINTAIN statement to add dimension values to the MEASURE dimension.

The following statement adds the names of the `sales`, `units`, `price`, and `inventory` variables to `measure` as its dimension values.

    MAINTAIN measure ADD 'sales', 'units', 'price', 'inventory'

Using a Measure Dimension with an Operator Variable

The purpose of using measure dimensions is to take advantage of the flexibility of using non-additive aggregation operators. You can use measure dimensions in the definition of operation variables or argument variables.

The following statements show how to define an operator variable named `opvar` and populate it.

    DEFINE opvar TEXT <measure>
    opvar (measure 'sales') = 'SUM'
    opvar (measure 'inventory') = 'HLAST'

##### Examples

For an example of an aggregation specification that includes a MEASUREDIM statement, see Example 9-16.

#### 9.9.7 MODEL (in an aggregation)

Within an aggregation specification, a MODEL statement executes a predefined model.

##### Syntax

MODEL modelname \[PRECOMPUTE ALL \|  PRECOMPUTE NA\]

##### Parameters

modelname
A text expression that contains the name of a predefined MODEL object.

PRECOMPUTE ALL
PRECOMPUTE NA
 Specifies whether the model is a static (precomputed) model or a dynamic model.

- ` PRECOMPUTE ALL` is the default and specifies a static model. The following conditions must be met:

  - Any RELATION or MODEL statements that precede it in the aggregation specification must also be specified as PRECOMPUTE ALL.

  - Any RELATION or MODEL statements that follow it in the aggregation specification can either be specified as PRECOMPUTE ALL or PRECOMPUTE NA.

- `PRECOMPUTE NA` specifies a dynamic model. The following conditions must be met for run-time execution of the model:

  - All RELATION statements in the aggregation specification must appear before the MODEL statements specified as PRECOMPUTE NA.

  - Any additional MODEL statements that follow it in the aggregation specification must also be specified as PRECOMPUTE NA.

##### Usage Notes

Dynamic Models and Non-Additive Operators

Model statements are executed in the order that they are coded within the aggregation specification. Typically, when the order of execution matters to the result, MODEL statements follow the corresponding RELATION statement.

Because the order of RELATION statements that use non-additive operators (for example, MAX) effects the result of the calculation and because dynamic models (that is, MODEL statements that include a PRECOMPUTE NA phrase) must follow all RELATION statements, the use of dynamic models with non-additive operators is somewhat constrained.

##### Examples

For an example of using a model in an aggregation specification, see Example 9-17.

#### 9.9.8 PRECOMPUTE

Within an aggregation specification, a PRECOMPUTE statement specifies which of the variable's aggregate values are calculated only with the AGGREGATE command.

**Note:**

An aggregation specification that has a PRECOMPUTE statement cannot have any PRECOMPUTE clauses in its RELATION statements.

##### Syntax

PRECOMPUTE precompute-phrase

where `precompute-phrase` is one of the following:

- `n``% | AUTO`
- `ALL`
- `NA | NONE`

##### Parameters

n%
Specifies an explicit percentage of the aggregate variable values that are aggregated as a database maintenance procedure using an AGGREGATE command. Oracle OLAP uses special functionality called the Aggregate Advisor to determine exactly which values are in the percentage.

AUTO
Specifies that Oracle OLAP uses the Aggregate Advisor to determine how many and which aggregate variable values to aggregate as a database maintenance procedure using an AGGREGATE command.

ALL
Specifies that all aggregated data is precomputed using an AGGREGATE command.

NA
NONE
Specifies that all values should be calculated on the fly using the AGGREGATE function (that is, that no data should be precalculated with the AGGREGATE command).

#### 9.9.9 RELATION (for aggregation)

Within an aggregation specification, a RELATION statement specifies how data is aggregated across a hierarchical dimension. Frequently, an aggregation specification contains one RELATION statement for each of the hierarchical dimensions of a variable.

**Note:**

Do not confuse this RELATION statement which can only be used as part of an AGGMAP command with either the RELATION command that defines a default relation for a dimension or the RELATION statement that is used as part of an ALLOCMAP command.

##### Syntax

RELATION rel-name \[(valueset...)\] -

     \[PRECOMPUTE (precompute-phrase)\] -      \[OPERATOR {operation\|opvar}\] -      \[PARENTALIAS dimension-alias-name\] -      \[ARGS {argument\|argsvar}\] -      \[LOAD_STATUS(status-valueset-name)\]

where:

- `precompute-phrase` is one or more of the following:

  - `n``% | AUTO`
  - `dimension-values`
  - `positions-of-dim-values`
  - `level-relation-name` `level-name``... `
  - `valueset2`
  - `ALL`
  - `NA | NONE`
  -

- `argument` is one or more of the following:

  - `DIVIDEBYZERO {YES|NO}`
  - `DECIMALOVERFLOW {YES|NO}`
  - `NASKIP {YES|NO}`
  - `WEIGHTBY [WNAFILL {``number ``| NA}]` `wobj`
  - `COUNT {YES|NO}`
  -

- `argsvar` is a text variable that contains `argument` phrases for some or all dimension values.

##### Parameters

rel-name
A relation that defines a hierarchy by identifying the parent of every dimension value in a hierarchy.

valueset
Sets the status of one or more dimensions for the duration of the aggregation. It overrides the current status.

PRECOMPUTE
Indicates that some dimension values are populated only with the AGGREGATE command. The PRECOMPUTE clause of the RELATION statement limits the data that is aggregated by the AGGREGATE command. In its simplest form, you can think of the PRECOMPUTE clause as working like a LIMIT dimension TO statement. Notice that the default limit is on the dimension, which is not explicitly named in the RELATION statement.

**Note:**

An aggregation specification has PRECOMPUTE clauses in any of its RELATION statements cannot also have a PRECOMPUTE statement. Additionally, you cannot specify a PRECOMPUTE phrase for a RELATION statement for a compressed composite.

n%
Specifies an explicit percentage of the aggregate variable values that are aggregated as a database maintenance procedure using an AGGREGATE command. Oracle OLAP uses special functionality called the Aggregate Advisor to determine exactly which values are in the percentage.

AUTO
Specifies that Oracle OLAP uses the Aggregate Advisor to determine how many and which aggregate variable values to aggregate as a database maintenance procedure using an AGGREGATE command.

dimension-values
A list of one or more values of dimension.

positions-of-dim-values
For all dimensions except those with `INTEGER` or `NUMBER` values, the positions of the dimension values that you want precomputed. Specify the positions using `INTEGER` values, separated by commas.

valueset2
The name of a valueset. When you include this argument, only data that is dimensioned by the dimension values in the valueset should be precalculated with the AGGREGATE command. The rest of the values can be calculated on the fly.

Note that the current status of a dimension can also limit the data that is precalculated. See the AGGREGATE command for details.

ALL
Specifies that data should be precalculated for all dimension values.

NA
NONE
Specifies that all values should be calculated on the fly using the AGGREGATE function (that is, that no data should be precalculated with the AGGREGATE command).

level-relation-name level-name ...
Specifies the levels of the dimension to be precomputed. For level-relation-name, specify, as a `TEXT` value, the name of the relation object that relates the values of the dimension to the names of the levels of the dimension. For level-name, specify, as `TEXT` values, the name of one or more levels using the same level names used in level-relation-name.

OPERATOR
Identifies the calculation method used to aggregate the data.

operation  
A keyword that describes the type of calculation to perform. The keywords are listed in the following table and can be retrieved by issuing an AGGROPS statement. You can specify a fixed-length three-character abbreviation for the keywords by specifying only the first three characters.

Table 9-1 Aggregation Methods

| Keyword   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AND       | When any child data value is `FALSE`, then the data value of its parent is `FALSE`. A parent is `TRUE` only when all of its children are `TRUE`. (BOOLEAN variables only)                                                                                                                                                                                                                                                                                                                                                  |
| AVERAGE   | Adds data values, then divides the sum by the number of data values that were added. When you use AVERAGE, there are special considerations described in "Average Operators".                                                                                                                                                                                                                                                                                                                                              |
| FIRST     | The first non-`NA` data value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| HAVERAGE  | (Hierarchical Average) Adds data values, then divides the sum by the number of the children in the dimension hierarchy. Unlike AVERAGE, which counts only non-`NA` children, HAVERAGE counts all of the logical children of a parent, regardless of whether each child does or does not have a value.<br>This keyword is not affected by the setting of the NASKIP option for argument.                                                                                                                                    |
| HFIRST    | (Hierarchical First) The first data value that is specified by the hierarchy, even when that value is `NA`.<br>This keyword is not affected by the setting of the NASKIP option for argument.                                                                                                                                                                                                                                                                                                                              |
| HLAST     | (Hierarchical Last) The last data value that is specified by the hierarchy, even when that value is `NA`.<br>This keyword is not affected by the setting of the NASKIP option for argument.                                                                                                                                                                                                                                                                                                                                |
| HWAVERAGE | (Hierarchical Weighted Average) Multiplies non-`NA` child data values by their corresponding weight values then divides the result by the sum of the weight values. Unlike WAVERAGE, HWAVERAGE includes weight values in the denominator sum even when the corresponding child values are `NA`.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.<br>This keyword is not affected by the setting of the NASKIP option for argument. |
| HWFIRST   | (Hierarchical Weighted First) The first data value that is specified by the hierarchy multiplied by its corresponding weight value, even when that value is `NA`.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.<br>This keyword is not affected by the setting of the NASKIP option for argument.                                                                                                                               |
| HWLAST    | (Hierarchical Weighted Last) The last data value that is specified by the hierarchy multiplied by its corresponding weight value, even when that value is `NA`.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.<br>This keyword is not affected by the setting of the NASKIP option for argument.                                                                                                                                 |
| LAST      | The last non-`NA` data value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| MAX       | The largest data value among the children of any parent data value.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| MIN       | The smallest data value among the children of any parent data value.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| NOAGG     | Do not aggregate any data for this dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| OR        | When any child data value is `TRUE`, then the data value of its parent is `TRUE`. A parent is `FALSE` only when all of its children are `FALSE`. (BOOLEAN variables only)                                                                                                                                                                                                                                                                                                                                                  |
| SSUM      | (Scaled Sum) Adds the value of a weight object to each data value, then adds the data values.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                                                                                     |
| SUM       | (Default) Adds data values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| WAVERAGE  | (Weighted Average) Multiplies each data value by a weight factor, adds the data values, and then divides that result by the sum of the weight factors.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                            |
| WFIRST    | (Weighted First) The first non-`NA` data value multiplied by its corresponding weight value.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                                                                                      |
| WLAST     | (Weighted Last) The last non-`NA` data value multiplied by its corresponding weight value.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                                                                                        |
| WMAX      | (Weighted Maximum) The largest data value among the children of any parent data value multiplied by its corresponding weight value.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                                               |
| WMIN      | (Weighted Minimum) The smallest data value among the children of any parent data value multiplied by its corresponding weight value.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                                              |
| WSUM      | (Weighted Sum) Multiplies each data value by a weight factor, then adds the data values.<br>When you use this keyword, you must include the WEIGHTBY argument keyword with a variable, formula, or relation as the weight object.                                                                                                                                                                                                                                                                                          |

opvar
A `TEXT` variable that you define that specifies a different the operation for each of its dimension values.

**Note:**

Not valid for variables dimensioned by compressed composites.

The opvar argument is used in two ways:

- Measure dimension -- Changes the aggregation method depending upon the variable being aggregated. Changing the aggregation method based on the variable being aggregated is useful when a single aggmap is used to aggregate several variables that must be aggregated with different methods. Whether you pre-aggregate all of the measures in a single AGGREGATE command or in separate statements, AGGREGATE uses the operation variable to identify the calculation method. The values of the measure dimension are the names of the variables to be aggregated. It dimensions a text variable whose values identify the operation to be used to aggregate each measure. The aggregation specification must include a MEASUREDIM statement that identifies the measure dimension. See Example 9-21.

- Line item dimension -- Changes the aggregation method depending upon the line item being aggregated. The line item dimension is typically non-hierarchical and identifies financial allocations. The line item dimension is used both to dimension the data variable and to dimension a text variable that identifies the operation to be used to aggregate each item. The operation variable is typically used to aggregate line items over time. You do not use the MEASUREDIM statement in the aggmap. See Example 9-22.

The opvar argument cannot be dimensioned by the dimension it is used to aggregate. For example, when you want to specify different operations for the `geography` dimension, then opvar cannot be dimensioned by `geography`.

To minimize the amount of paging for the operator variable, define the operation variable as type of `TEXT` with a fixed width of `8`.

PARENTALIAS
Specifies that an alias dimension for the dimension being aggregated is QDRd to the parent value currently being aggregated.

dimension-alias-name
The name of the alias dimension for the dimension of rel-name.

ARGS
Indicates optional handling of the aggregation.

DIVIDEBYZERO
Specifies whether to allow division by zero.

- `YES` allows division by zero; a statement involving division by zero executes without error but produces `NA` results.

- `NO` disallows division by zero; a statement involving division by zero stops executing and produces an error message.

The default value is the current value of the DIVIDEBYZERO option.

DECIMALOVERFLOW
Specifies whether to allow decimal overflow, which occurs when the result of a calculation is very large and can no longer be represented by the exponent portion of the numeric representation.

- `YES` allows overflow; a calculation that generates overflow executes without error and produces `NA` results.

- `NO` disallows overflow; a calculation involving overflow stops executing and generates an error message.

The default value is the current value of the DECIMALOVERFLOW option.

NASKIP
Specifies whether `NA` values are input.

- `YES` specifies that `NA` values are ignored when aggregating. Only actual values are used in calculations.

- `NO` specifies that `NA` values are considered when aggregating. When any of the values being considered are `NA`, the calculation returns `NA`.

The default value is the current value of the NASKIP option.

The value that you specify for the NASKIP phrase does not effect calculation performed when you specify HAVERAGE, HFIRST, HLAST, HWAVERAGE, HWFIRST, HWLAST for operation.

WEIGHTBY
Indicates that weighted aggregation is to be performed. You must include a WEIGHTBY clause when you specify HWAVERAGE, HWFIRST, HWLAST, SSUM, WAVERAGE, WFIRST, WLAST, or WSUM for operation. The WEIGHTBY phrase always includes a wobj argument and, optionally, can include the WNAFILL keyword.

WNAFILL {number \| NA}
Indicates handling for `NA` values. The default values for WNAFILL vary depending on the value of operation. The default value for HWAVERAGE and SSUM is `0.0`. The default value for OR is `NA`. The default value for the other operators is `1.0`. WNAFILL defaults for each operator in an aggregation specification. In other words, when one RELATION statement includes a WSUM OPERATOR, then WNAFILL defaults to `1.0`. When the next RELATION statement includes an SSUM OPERATOR, then WNAFILL defaults to `0.0`, and so on. See "Using WNAFILL".

wobj
A variable, formula, or relation that provides the weighted values. It can be numeric or BOOLEAN. When wobj is BOOLEAN, then `TRUE` has a weight of `1.0` and `FALSE` has a weight of `0.0`. A formula is queried only when needed, depending on the dimensionality of the formula and the variable being aggregated. When wobj is a relation, it should be a one-dimensional self-relation. See Using Weighted Aggregation Methods for more information about specifying values for wobj.

COUNT {YES\|NO}
YES specifies that when Oracle OLAP aggregates a variable using this relation that it also populates the Aggcount variable associated with that variable. For more information on Aggcount variables, see "Aggcount Variables".

NO specifies that when Oracle OLAP aggregates a variable using this relation that it does not populate the Aggcount variable associated with that variable. For more information on Aggcount variables, see "Aggcount Variables".

argsvar
A `TEXT` variable that contains the argument options for some or all dimension values.

LOAD_STATUS
Specifies that, for the aggregation, Oracle OLAP consider the values specified by status-valueset-name as the detail or lowest level of the hierarchy.

status-valueset-name
A previously-defined valueset that specifies the lowest-level values to have in status when performing the aggregation. When performing any aggregation using an aggmap with a RELATION statement with this clause, Oracle OLAP temporarily sets the status of the dimension to the values specified by status-valueset-name and their ancestors. The valueset specified by status-valueset-name must be a single dimensional valueset for the relation dimension (not the hierarchy dimension). Additionally, the valueset specified by status-valueset-name cannot contain both a value and an ancestor of that value.

##### Usage Notes

Ordering RELATION Statements with Non-Additive Operators

The order of RELATION statements that use non-additive operators effects the result of the calculation. For example the max of sum is not generally equal to the sum of max. Consequently, the order of RELATION statements within an aggregation specification must follow the logical requirements of the calculation. This logical necessity limits the use of dynamic models within an aggregation as discussed in "Dynamic Models and Non-Additive Operators".

RELATION Statements for Compressed Composites

When designing the aggregation specification, follow these guidelines when coding RELATION statements for compressed composites:

- The HAVERAGE, HWAVERAGE, HWFIRST, HWLAST, SSUM, WAVERAGE, WFIRST, WLAST, WMAX, WMIN, and WSUM operators cause data values to change with each level of aggregation, regardless of sparsity. When possible, to insure the largest amount of overall compression, place RELATION statements with these operators at the beginning of your aggregation specification before RELATION statements that use an AND, AVERAGE, FIRST, HFIRST, HLAST, LAST, MAX, MIN, NOAGG, OR, or SUM operator.

- To optimize the compression of a compressed composite, list similar operators contiguously if the calculation logic allows. For example, specifying MAX for the first dimension and then SUM for all the other dimensions results in better compression, and thus provides better calculation performance, than specifying SUM, MAX, and then SUM over the remaining dimensions.

- SUM is the fastest and most compressible operator. Changing the aggregation operator for one or more dimensions from SUM to some other operator results in less compression, and therefore a larger variable, and the AGGREGATE command for that variable takes longer to complete.

- When an AGGMAP contains a RELATION statement that specifies the AVERAGE operator, any variable using that aggregation specification must be defined using a DEFINE VARIABLE statement with a WITH AGGCOUNT phrase.

- You can only specify a single aggregation operation. You cannot specify aggregation operations using an opvar variable.

Two Ways to use Valuesets

You can use valuesets to:

- Limit hierarchy dimensions. You can limit which hierarchies are used by the AGGREGATE command and AGGREGATE function and the order in which these hierarchies should be used. The valueset that you use specifies the names of a dimension's hierarchies. To use a valueset in this way, use the following syntax.

      RELATION rel-name (valueset)

  In this case, using valuesets provides a way to manage hierarchies that are in conflict with each other, meaning, when the same dimension value stores data for different children in different hierarchies (such as, `Q1` stores data for `Jan`, `Feb`, and `Mar` in the `Calendar` hierarchy, but `Q1` stores data for `May`, `Jun`, and `Jul` in the `Fiscal` hierarchy).

- Specify which values should be calculated on the fly by the AGGREGATE function and which values should be pre-calculated by the AGGREGATE command. The valueset that you use specifies the names of dimension values. To use a valueset in this way, use the following syntax.

      RELATION rel-name PRECOMPUTE (valueset)

  In this case, you use the valueset that follows the PRECOMPUTE keyword.

  When you use valuesets to limit hierarchy dimensions and when using multiple aggmaps and the hierarchies are inconsistent, you must also use the FORCECALC keyword in the AGGREGATE function or have set an \$AGGREGATE_FORCECALC property on the variable to be aggregated.

When You Change a PRECOMPUTE or an OPERATOR Clause

Any time you make changes to a PRECOMPUTE or an OPERATOR clause, aggregate the variable data again and recompile the aggmap to produce accurate data.

Aggregating Data Loaded into Different Hierarchy Levels

When data is loaded into dimension values that are at different levels of a hierarchy, then you must be careful in how you set status in the PRECOMPUTE clause in a RELATION statement in your aggregation specification.

Suppose that a `time` dimension has a hierarchy with three levels: months aggregate into quarters, and quarters aggregate into years. Some data is loaded into month dimension values, while other data is loaded into quarter dimension values. For example, `Q1` is the parent of` January`, `February`, and `March`. Data for `March` is loaded into the `March` dimension value. But the sum of data for `January` and `February` is loaded directly into the` Q1` dimension value. In fact, the `January` and `February` dimension values contain `NA` values instead of data. Your goal is to add the data in `March` to the data in `Q1`.

When you attempt to aggregate` January`, `February`, and `March` into `Q1`, the data in `March` simply replaces the data in `Q1`. When this happens, `Q1` contains only the `March` data instead of the sum of `January`, `February`, and `March`.

To aggregate data that is loaded into different levels of a hierarchy, create a valueset for only those dimension values that contain data.

    DEFINE all_but_q4 VALUESET time
    LIMIT all_but_q4 TO ALL
    LIMIT all_but_q4 REMOVE 'Q4'

Within the aggregation specification, use that valueset to specify that the detail-level data should be added to the data that exists in its parent, `Q1`, as shown in the following statement.

    RELATION time.r PRECOMPUTE (all_but_q4)

Average Operators

There are several issues involved in using the AVERAGE, HAVERAGE, WAVERAGE, and HWAVERAGE operators:

- Oracle OLAP needs a separate `INTEGER` variable in which it stores the non-`NA` counts of the number of leaf nodes that contributed to aggregate values to calculate average values. When you want to aggregate a variable using one the average operators, include the WITH AGGCOUNT phrase in the DEFINE VARIABLE statement for the variable.

- Accuracy when averaging—All decimal data is converted to floating point format, both for storing and for calculations, consequently, in some cases, an average aggregation computed on a `DECIMAL` or `SHORTDECIMAL` variable can differ in the least significant digits from a result you compute by hand. For this reason, you might want to use the `NUMBER` data type when accuracy is more important than computational speed, such as variables that contain currency amounts. See "[Numeric Expressions](data-types-operators-and-expressions.md)" for more information.

- Using Average operators when aggregating using an AGGREGATE command—When you use an average operator with the PRECOMPUTE keyword, the best practice is to use variables that have a decimal or `NUMBER` data type to ensure the accuracy of the results.

- Using Average operators for partial aggregations—When you use an average operator in a partial aggregation, then you must always aggregate using the same `INTEGER` variable (that is, Aggcount or Countvar variable). Do not change the values that are stored in this `INTEGER` variable between aggregations. Finally, the number of `INTEGER` variables must match the number of variables that are being aggregated.

HAVERAGE, HFIRST, HLAST, AND HWAVERAGE Operators

The "hierarchical" operators (HAVERAGE, HFIRST, HLAST, AND HWAVERAGE) are intended to provide an alternative form of `NA` handling.

FIRST, HFIRST, LAST, AND HLAST Operators

These operators rely on the existing order of the dimension values, which are assumed to be the default logical order of that dimension. For example, in a month dimension, it is assumed that February follows January, March follows February, and so on.

When you must change the default order, use the MAINTAIN statement to do so. For example, suppose `Q1` includes `January`, `February`, and `March`, but you must make `Februar`y the last month in the `Q1` instead of `March`. Use the following statement to do so.

    MAINTAIN time MOVE 'Feb01' AFTER 'Mar01'

Now, the LAST operator assumes that `FEB01` is the last month in `Q1`.

Read Permissions and Aggmaps

When you change the read permission to rel-name in a RELATION statement, then you must recompile the aggmap before using it with the AGGREGATE function. Compilation is not an issue when you use the AGGREGATE command, because the aggmap is recompiled automatically. However, when you do not have read access to every rel-name in the aggmap, then attempting to use that aggmap results in an error message.

Using Weighted Aggregation Methods

When you use a weighted method of aggregation, you must define and populate an object that contains the weights. You identify the aggregation method in the OPERATOR clause and the weight object in the ARGS clause.

The weight object can be a variable, a formula, or a relation. Special considerations apply depending on the type of object. the data type of the weight object, and whether or not you are performing a partial aggregation.

Weight Object Considerations Based on Type of Object

The following considerations apply depending on the type of object that you use for the weight object:

- When the weight object is a variable, you can define it with a numeric or BOOLEAN data type. Use a variable as your weight object when you want to pre-calculate weight values and commit them to the database. You can use a variable weight object with any weight option.

- When the weight object is a relation, define it as a one-dimensional self-relation. You can use the weight object to specify that the weight for a specific cell is contained in the current variable at a different location. Use a relation as your weight object when you use a line item or a measure dimension. In this case, one line item is used as the weight to calculate the aggregate value of another line item. Using a relation enables you to specify another set of cells in the variable being aggregated as the weight values for a weighted operation.

- When the weight object is a formula, that formula is queried only as often as needed, depending on the dimensionality of the formula and the dimensionality of the variable whose data is being aggregated. You can define the formula with a numeric or BOOLEAN data type. Use a formula as your weight objectwhen you want to calculate weight values on the fly. A formula weight object is similar to a variable weight object, except that it cannot be aggregated. The value of a formula weight object is executed dynamically. Therefore, you cannot use a formula weight object with many of the weight options.

Considerations Based on Data Type of the Weight Object

The following considerations apply when the weight object is numeric or `BOOLEAN`:

- When the weight object has a numeric data type, It is good practice for the weight object variable to have the same dimensionality (or a subset thereof) as the variable to which it corresponds, but it is not required. When you use Oracle numbers or decimals to define your data variable, then always use the same data type to define the corresponding weight object. Otherwise, use the same data type for the weight object and the data variable unless you use WAVERAGE or HWAVERAGE; in this case, use a decimal or `NUMBER` data type to define the weight object.

- When the weight object variable, formula, or relation that you define has a `BOOLEAN` data type, then `TRUE` represents a weight of `1.0` and `FALSE` represents a weight of `0.0`. Furthermore, when an `NA` value is multiplied by any value, the result is `NA`.

Weight Object Considerations When Performing Partial Aggregations

When you use any operators that require the WEIGHTBY phrase, and you are performing a partial aggregation, then do not change the values that are stored in the weight object between AGGREGATE commands.

Using WNAFILL

For example, suppose you use the WSUM operator to perform currency conversion. The currency conversation rates are applied at the detail data level. Only the detail data needs to be converted, because the variable data is aggregated after the conversion. To get the correct results, all of the non-detail level weight values in the weight object would have to be `1`. Although this strategy produces correct results, it is inefficient. The best practice is to use the default WNAFILL value of `1` which specifies that all `NA` values in the weight object should be treated as if they have a weight of `1`. In this case, because the operator is WSUM, you do not have to include WNAFILL in the AGGREGATE command, because the default values are correct.

For example, the following statement causes the value `0.7` to be substituted for every `NA` value in the `salesw` weight object.

    AGGREGATE sales USING sales.agg WEIGHTBY WNAFILL 0.7 salesw

When you do not want to specify a number to replace `NA` values, then you can use `NA` instead of a number, as shown in the following statement.

    AGGREGATE sales USING sales.agg WEIGHTBY WNAFILL NA salesw

Specifying `NA` after WNAFILL has the following effect:

- When the aggregation specification contains a WAVERAGE or a WSUM OPERATOR, then any child cell in the weight object that has an `NA` value is treated as an `NA` cell.

- When the aggregation specification contains an SSUM OPERATOR, then the results depend on how the Oracle OLAP option NASKIP is set. When NASKIP is set to `YES`, then any `NA` value is treated as 0.0. However, when NASKIP is set to `NO`, then any `NA` value is treated as an `NA` cell.

Effects of Dimension Status on Aggregation

A RELATION statement only aggregates those source data values that are in status—whether you set the status using LIMI T statements or a LOAD STATUS clause on the RELATION statement. The parent values are calculated regardless of whether they are in status or not. For example, when only `Jan01`, `Feb01`, and `Mar01` are in status for the `time` dimension, then `Q1.01` is calculated (but no other quarters), and `2001` is calculated (but no other years) using only `Q1.01` as input because the other quarters are NA. This functionality is useful when you want to aggregate just the new data in your analytic workspace.

Assume that there is a variable named `sales` that is dimensioned by `time`, a hierarchical dimension, and `district`, a non-hierarchical dimension.

    DEFINE time DIMENSION TEXT
    DEFINE time.parentrel RELATION time <time>
    DEFINE district DIMENSION TEXT
    DEFINE sales VARIABLE DECIMAL <time district>

    REPORT DOWN time sales

                 -----------------------SALES-----------------------
                 ---------------------DISTRICT----------------------
    TIME            North        South         West         East
    ------------ ------------ ------------ ------------ ------------
    1976Q1         168,776.81   362,367.87   219,667.47   149,815.65
    1976Q2         330,062.49   293,392.29   237,128.26   167,808.03
    1976Q3         304,953.04   354,240.51   170,892.80   298,737.70
    1976Q4         252,757.33   206,189.01   139,954.56   175,063.51
    1976                   NA           NA           NA           NA

##### Examples

For examples of aggregation specifications that include RELATION statements, see the examples in the AGGMAP command.

### 9.10 AGGMAP ADD or REMOVE model

The AGGMAP ADD or REMOVE model command adds or removes a previously-defined model from a previously-defined aggregation specification (that is, aggmap object of type AGGMAP). Models are used in aggregation specifications to aggregate data over a non-hierarchical dimension (such as line items), which has no parent relation and therefore cannot be aggregated by a RELATION statement. See MODEL (in an aggregation) for details.

**Note:**

Although you can use the AGGMAP ADD MODEL and AGGMAP REMOVE MODEL statements to temporarily add a model to an aggmap object, typically you use a [MAINTAIN ADD SESSION](olap-dml-commands-h-z.md) statement like the one below to perform this action.

`MAINTAIN` `dimension` `ADD SESSION` `member` `=` `model` `APPLY TO AGGMAP` `aggmap`

When you use a MAINTAIN ADD SESSION statement neither the calculated member or its definition persists from session to session; both are deleted after the session in which they are created

#### Syntax

AGGMAP {ADD model TO aggmap\|REMOVE model FROM aggmap}

#### Parameters

ADD
Temporarily adds a model to an aggmap object. The model is attached to the aggmap only for the duration of the session. Even when the analytic workspace has been updated and committed, the model is discarded from the aggmap when the session is closed.

REMOVE
Removes a model from an aggmap.

model
The name of the model object that you want to add to the specified aggmap.

aggmap
The name of a previously defined aggmap object of type AGGMAP.

#### Examples

Example 9-25 Temporarily Adding a Model to an Aggmap

Assume for example, that you have an aggmap object named `letter.aggmap` with the following definition.

    DEFINE LETTER.AGGMAP AGGMAP
    AGGMAP
    RELATION letter.letter PRECOMPUTE ('AA')
    END

Assume also that you want to create summarized variable data for the cells that are dimensioned by the dimension values `AAB` and `ABA`. However, you do not want this data to be permanently stored in the analytic workspace. You just want to see the data during your session.

To perform this type of aggregation, you can take the following steps:

1.  Create a dimension value for the custom aggregate. This dimension value is the parent of the dimension values `AAB` and `ABA`. The following statement adds '`BB`' to the `letter `dimension.

        MAINTAIN letter ADD 'BB'

2.  Create a `MODEL` object that contains an `AGGREGATION` function, which associates child dimension values with the new dimension value. The following model identifies `BB` as the parent of `AAB` and `ABA`. Note that the parent dimension value (in this case, BB) cannot already be defined as a parent in the parent relation (`letter.letter`).

        DEFINE LETTER.MODEL MODEL
        MODEL
        DIMENSION letter
        BB=AGGREGATION('AAB' 'ABA')

3.  Execute an `AGGMAP ADD` statement to append the model to the existing `AGGMAP` object.

        AGGMAP ADD letter.model TO letter.aggmap

    The aggmap now looks like this.

        DEFINE LETTER.AGGMAP AGGMAP
        AGGMAP
        RELATION letter.letter PRECOMPUTE ('AA')
        END
        AGGMAP ADD letter.model

4.  The model is executed only by the `AGGREGATE` function like the one shown here; the `AGGREGATE` command ignores it.

        REPORT AGGREGATE(units USING letter.aggmap)

5.  When you want to remove the model from the aggmap during a session, use the `AGGMAP REMOVE` statement.

6.  To ensure that your aggmap does not become a permanent object in the analytic workspace, before you close your session issue the following statement to delete the dimension values that you added in Step 1.

        MAINTAIN letter DELETE 'BB'

    When your session ends, Oracle OLAP automatically removes the model added using the AGGMAP ADD statement. You do not have to issue an explicit AGGMAP REMOVE statement.

### 9.11 AGGMAP SET

Specifies the default aggmap for a variable.

**Note:**

You can also use an \$AGGMAP property to specify the default aggregation specification for a variable or the \$ALLOCMAP property to specify the default allocation specification for a variable.

#### Syntax

AGGMAP SET aggmap AS DEFAULT FOR variables

#### Parameters

aggmap
The name of a previously defined aggmap object.

variables
A text expression that is the name of one or more variables for which the specified aggmap is the default aggmap. When you specify a literal value, separate the names of the variables with commas.

#### Examples

Example 9-26 Using AGGMAP SET to Specify a Default Aggmap

[\$AGGREGATE_FROM](olap-dml-properties.md) illustrates how the AGGREGATE command shown in Example 9-13 can be simplified to the following statement.

    AGGREGATE sales_by_revenue USING revenue_aggmap

You can further simplify the AGGREGATE command if you make `revenue_aggmap` the default aggmap for the `sales_by_revenue` variable. You can do this either by defining an \$AGGMAP property on the `sales_by_revenue` variable or by issuing the following statement.

    AGGMAP SET revuienue_aggmap AS DEFAULT FOR sales_by_revenue

Now you can aggregate the data by issuing the following AGGREGATE command that does not include a USING clause.

    AGGREGATE sales_by_revenue

### 9.12 AGGREGATE command

The AGGREGATE command calculates summary data in the variable that is specified as PRECOMPUTE in the specified aggmap. (For information about specifying precompute data, see the PRECOMPUTE and RELATION (for aggregation) statements of the AGGMAP command.) The aggregation is limited to those values that are currently in status.

Use the \$AGGMAP property or the AGGREGATE function to calculate data that is not specified as precomputed data.

**See Also:**

[AGGREGATE function](olap-dml-functions-a-k.md)

#### Syntax

AGGREGATE\|AGGR { var  \[(PARTITION partition-name)\]}... \[USING aggmap\] -      \[FROM fromspec\|FROMVAR textvar\] \[FORCEORDER\] \[FUNCDATA\] \[COUNTVAR countvar...\]

#### Parameters

var
A variable whose data values are to be calculated. Every variable in a single AGGREGATE command must have the same dimensions in the same order.

PARTITION
Specifies that you want AGGREGATE to recalculate only the values in the specified partition of the specified variable. Frequently, the reason for aggregating only a single partition is to parallelize a build using multiwriter.

**Note:**

Because the AGGREGATE command does not consider partition dependencies when aggregating individual partitions, aggregate only a set of non-dependent partitions within a single AGGREGATE command.

partition-name
The name of a previously-defined partition. See DEFINE PARTITION TEMPLATE

USING
This keyword indicates that the aggregation is performed using the specified aggmap. When you do not include this phrase, the command uses the default aggmap for the variable as previously specified using an AGGMAP statement or the \$AGGMAP property.

aggmap
The name of a previously-defined aggmap that specifies how the data is aggregated. For information about aggmaps, see the DEFINE AGGMAP command.

FROM
This keyword indicates that the detail data is obtained from a different object.

A FROM clause is only one way in which you can specify the variable from which detail data should be obtained when performing aggregation. See "Ways of Specifying Where to Obtain Detail Data for Aggregation".

fromspec
An arbitrarily dimensioned variable, formula, or relation from which the detail data for the aggregation is obtained.

FROMVAR
This keyword indicates that the detail data is obtained from different objects to perform a capstone aggregation. (For an example of using the FROMVAR clause, see Example 9-32.)

A FROMVAR clause is only one way in which you can specify the variable from which detail data should be obtained when performing aggregation. See "Ways of Specifying Where to Obtain Detail Data for Aggregation".

textvar
An arbitrarily dimensioned variable used to resolve any leaf nodes. Specify `NA` to indicate that a node does not need detail data to calculate the value.

FORCEORDER
Specifies that the calculation must be performed in the order in which the RELATION statements are listed in the aggmap. Use this option when you have changed some values calculated by the AGGREGATE command. Otherwise, the optimization methods used by the AGGREGATE command may cause the modified values to be ignored.

**Note:**

You can also set an \$AGGREGATE_FORCEORDER property on a variable to specify this behavior as the default aggregation behavior. In this case, you do not have to include the FORCEORDER keyword with the AGGREGATE command.

FUNCDATA
Compiles the aggregation specification for future use by the AGGREGATE function. When you use FUNCDATA, you do not have to recompile the aggmap before using the AGGREGATE function, unless afterward you make changes to the aggmap, the relation hierarchies, or a composite.

When the variables have composite dimensions, the indexes (composite tuples) are created and saved for use by the AGGREGATE function. Otherwise, the indexes are re-created each time the AGGREGATE function is called. Refer to AGGINDEX for more information about composite indexes.

COUNTVAR countvar
Indicates that Oracle OLAP should use the user-defined variable specified by countvar to store the non-`NA` counts of the number of leaf nodes that contributed to aggregate values calculated for RELATION statements that have an AVERAGE, HAVERAGE, HWAVERAGE, or WAVERAGE operator.

**Note:**

Typically, you do not use a user-defined Countvar variable to store the counts for average aggregations. Instead, you use an Oracle OLAP-created Aggcount variable. You must use an Aggcount variable when the aggregation specification includes a RELATION statement with an average operator is for a compressed composite.

For more information on Aggcount variables, see "Aggcount Variables".

The countvar variable must be an `INTEGER` variable with the same dimensions in the same order as the dimensions of the variable specified by var. When you aggregate several variables together, you must define an `INTEGER` variable for each one to record the results.

#### Usage Notes

Effect of Status on AGGREGATE

The current status only affects dimension values at the lowest level of the hierarchy, that is, the leaf nodes. Only leaf-node dimension values that are currently in status are aggregated. The parent values of leaf nodes in status are calculated, whether the parent values are in status or not (unless you exclude the dimension values in those levels with a PRECOMPUTE clause in the AGGMAP command). Thus, when you want to aggregate all of the data specified in the aggmap, then be sure to set the status of the dimensions to ALL before performing the aggregation.

AGGREGATE uses the parent relation to distinguish among dimension values at different levels of the hierarchy. Alternatively, you can perform a partial aggregation of the data by limiting status. However, this must be done carefully when some data is aggregated at run time by the AGGREGATE function. See the notes in the [AGGREGATE function](olap-dml-functions-a-k.md) topic for more information.

For example, suppose you use the `area` dimension and the `area.area` child-parent relation that supports one hierarchy for a geography dimension as illustrated in the following table:

Table 9-2 Geography Hierarchy

| Level | area Dimension | area.area Parent Relation |
|:------|:---------------|:--------------------------|
| 1     | `TotalUS`      | `NA`                      |
| 2     | `East`         | `TotalUS`                 |
| 2     | `South`        | `TotalUS`                 |
| 3     | `Boston`       | `East`                    |
| 3     | `New York`     | `East`                    |
| 3     | `Atlanta`      | `South`                   |

Now suppose you change the data value for `New` `York`. When you then use AGGREGATE with only `New` `York`, the calculation occurs without including the child value for `South` (`Atlanta`), but still includes level `2` as it goes from level `3` to level `1` (`TotalUS`). When you want all the child values included in rolling up to `TotalUS`, use `a LIMIT TO ALL` statement before you execute the AGGREGATE command.

When the data has changed for some, but not all, of the child values in a hierarchy, you can set the status to calculate just the values that have changed. For example, when your embedded-total dimension is called `d2`, and its parent relation is called `reld2`, first limit `d2` to the values that have changed.

To calculate the data for every hierarchy in a dimension, limit the dimension's hierarchy dimension to `ALL` before you execute the AGGREGATE command.

Controlling the Amount of Data That Is Calculated

You can control how much of the variable data is calculated by using the PRECOMPUTE keyword with the RELATION statement in the aggmap. Use the limit clause (after the PRECOMPUTE keyword) to set the status of the dimension.

When Users Modify Data

When users are able to change the data in a variable, then calculate aggregates on the fly using the AGGREGATE function, so that their changes are reflected in the aggregate data. See the [AGGREGATE function](olap-dml-functions-a-k.md) for more information about run-time changes to the data.

Generation-Skipping Hierarchies

AGGREGATE automatically distinguishes between generations in the parent relation, even to the extent of allowing generation-skipping hierarchies. For example, you can have a four-level hierarchy (for example, `neighborhoods`, `cities`, `states`, and `totalUS`) that has a three-level branch (for example, `Boston`, `Massachusetts`, and `totalUS`).

Restrictions on Permissions

AGGREGATE does not work on variables that have cell-by-cell permissions; it immediately return an error. It also ignores the PERMITERROR option. However, AGGREGATE operates on variables with object level or dimension level permission. See the [PERMIT](olap-dml-commands-h-z.md) command and [PERMITERROR](olap-dml-options.md) option.

Ways of Specifying Where to Obtain Detail Data for Aggregation

You can specify where to obtain detail data when aggregating data in the following ways:

- Assign either an \$AGGREGATE_FROM property or an \$AGGREGATE_FROMVAR property to a variable.

  **Note:**

  You can only assign one of these properties to a variable. A variable cannot have both the \$AGGREGATE_FROM and \$AGGREGATE_FROMVAR properties assigned to it.

- Include either a FROM or FROMVAR clause in the AGGREGATE command or AGGREGATE function that aggregates the data.

When performing an aggregation, Oracle OLAP determines where to obtain the detail data as follows:

1.  When a location has been specified using a FROM or FROMVAR clause, Oracle OLAP uses the detail data at that location.

2.  When a location has not been specified using a FROM or FROMVAR clause, Oracle OLAP checks to see if a location has been specified using an \$AGGREGATE_FROM property or an \$AGGREGATE_FROMVAR property. When a location has been specified using one of these properties, Oracle OLAP uses the detail data at that location.

3.  When a location has not been specified using either FROM or FROMVAR clause or an \$AGGREGATE_FROM property or an \$AGGREGATE_FROMVAR property, Oracle OLAP performs the aggregation using the detail data in the variable itself.

#### Examples

This section contains several examples of using the AGGREGATE command. For additional aggregation examples, see the examples in the AGGMAP command.

Example 9-27 Precalculating Data in a Batch Job

Frequently, you generate precalculated aggregates in a batch window as part of maintaining the data in your database. For example, you can use Job Manager to schedule batch jobs in Oracle Enterprise Manager

To generate precalculated aggregates, you use the AGGREGATE command. The AGGREGATE command aggregates the data for one or more variables according to the specifications provided in the aggmap.

Your batch job should include statements like the following.

    AGGREGATE sales units USING gpct.aggmap
    UPDATE
    COMMIT

Example 9-28 Aggregating One Variable

Suppose your analytic workspace contains a variable named `actuals`, which has the following definition.

    DEFINE actuals DECIMAL <time, SPARSE <product, customer, channel>>

The next step is to define an aggmap object, whose definition has the same dimensions in the same dimension order. Suppose you define an aggmap object named `act.agg` using DEFINE AGGMAP.

    DEFINE act.agg AGGMAP <time, SPARSE <product, customer, channel>>

Suppose that the name of the hierarchy for the `time` dimension is `time.r`, the name of the `product` dimension is `product.r`, and so on Next, you use an AGGMAP statement to add the following text in the `act.agg` aggmap.

    AGGMAP
    RELATION time.r
    RELATION product.r
    RELATION customer.r
    RELATION channel.r
    END

The preceding text specifies the name of each dimension's hierarchy for which data should be rolled up. Assuming that the current status of every dimension is `ALL`, data is calculated for every dimension value of every dimension in the definition of `actuals`. No data is calculated on the fly.

Use the following statements to calculate the `actuals` variable. (It is not necessary to compile the aggmap, because the compilation is included as part of the AGGREGATE command.)

    AGGREGATE actuals USING act.agg

Example 9-29 Aggregating Multiple Variables

Suppose your analytic workspace contains a variable named `actuals` and a variable named `forecast`. As shown in the following variable definitions, these variables have the same dimensions in the same dimension order.

    DEFINE actuals DECIMAL <time, SPARSE <product, customer, channel>>
    DEFINE forecast DECIMAL <time, SPARSE <product, customer, channel>>

The next step is to define an aggmap object, whose definition has the same dimensions in the same dimension order. Suppose you define the same aggmap object named `act.agg`, as described in "Example 9-28". When you want the data for each variable to be rolled up in the same way, you can use the same aggmap to calculate both variables in a single statement.

Use the following statements to calculate the `actuals` and the `forecast` variables.

    AGGREGATE actuals forecast USING act.agg

Because the aggmap specifies that all data for every dimension value in each dimension should be rolled up, this statement rolls up all of the data in `actuals` and all of the data in `forecast`.

Example 9-30 Using COUNTVAR with Multiple Variables

Suppose you plan to use one AGGREGATE command to aggregate the data for three variables: `sales`, `units`, and `projected_sales`. Each variable has the following dimensionality.

    <month product geography>

To tally the results with COUNTVAR, you must define three `INTEGER` variables that have the same dimensionality as `sales`, `units`, and `projected_sales`.

    DEFINE intsales INTEGER <month product geography>
    DEFINE intunits INTEGER <month product geography>
    DEFINE intprojsales INTEGER <month product geography>

You can then specify the `INTEGER` variables in the following statement.

    AGGREGATE sales units projected_sales USING sales.agg -
      COUNTVAR intsales intunits inprojsales

Example 9-31 Performing a Partial Aggregation

This example limits the `time` dimension to the last two time periods, so that only newly loaded data is aggregated.

The `tp2.agg` aggmap specifies preaggregation for all detail data currently in status.

    DEFINE TP2.AGG AGGMAP
    LD Full preaggregation
    AGGMAP
    RELATION time.parentrel PRECOMPUTE (ALL)
    RELATION product.parentrel PRECOMPUTE (ALL)
    END

For the aggregation, `time` is limited to the last two time periods and all `product` values are in status.

    LIMIT time TO LAST 2
    STATUS time product
    The current status of TIME is:
    Apr02, May02
    LIMIT product TO ALL

The following AGGREGATE statement calculates `units` using the `tp2.agg` aggmap.

    AGGREGATE units USING tp2.agg

The results of this aggregation show that parent values are calculated, regardless of their own status, when their children are in status.

    LIMIT time TO '2002' 'Q1.02' 'Q2.02' 'Jan02' to 'May02'
    REPORT DOWN time units

     -----------------------------------------UNITS-----------------------------------------
     ----------------------------------------PRODUCT----------------------------------------
    TIME     FOOD      SNACKS    DRINKS   POPCORN   COOKIES   CAKES     SODA      JUICE
    -------  --------  --------  -------- --------  --------  --------  --------  --------
    2002     38        24        14       6         9         9         9         5
    Q1.02    NA        NA        NA       NA        NA        NA        NA        NA
    Q2.02    38        24        14       6         9         9         9         5
    Jan02    NA        NA        NA       8         2         4         5         8
    Feb02    NA        NA        NA       5         3         2         2         5
    Mar02    NA        NA        NA       3         4         4         2         4
    Apr02    21        13        8        2         7         4         6         2
    May02    17        11        6        4         2         5         3         3

Example 9-32 Capstone Aggregation

Assume that your analytic workspace has the two hierarchical `TEXT` dimensions named `geog.d` and `time.d` with the following values.

    GEOG.D
    --------------
    Boston
    Medford
    San Diego
    Sunnydale
    Massachusetts
    California
    United States

    TIME.D
    --------------
    Jan76
    Feb76
    Mar76
    76Q1

Assume, also, that there are four variables with the following definitions

    DEFINE sales_jan76 VARIABLE INTEGER <geog.d>
    DEFINE sales_feb76 VARIABLE INTEGER <geog.d>
    DEFINE sales_mar76 VARIABLE INTEGER <geog.d>
    DEFINE sales_capstone76 VARIABLE INTEGER <geog.d time.d>

Assume that you issue the following REPORT statements for the variables. The output of the reports show the detail data in the variables.

    REPORT sales_jan76  sales_feb76 sales_mar76
    REPORT DOWN geog.d sales_capstone76

    GEOG.D         SALES_JAN76  SALES_FEB76  SALES_MAR76
    -------------- ------------ ------------ ------------
    Boston                1,000        2,000        3,000
    Medford               2,000        4,000        6,000
    San Diego             3,000        6,000        9,000
    Sunnydale             4,000        8,000       12,000
    Massachusetts            NA           NA           NA
    California               NA           NA           NA
    United States            NA           NA           NA

                   -----------------SALES_CAPSTONE76------------------
                   ----------------------TIME.D-----------------------
    GEOG.D            Jan76        Feb76        Mar76         76Q1
    -------------- ------------ ------------ ------------ ------------
    Boston                   NA           NA           NA           NA
    Medford                  NA           NA           NA           NA
    San Diego                NA           NA           NA           NA
    Sunnydale                NA           NA           NA           NA
    Massachusetts            NA           NA           NA           NA
    California               NA           NA           NA           NA
    United States            NA           NA           NA           NA

1.  Define two aggmap objects with the following definitions.

        DEFINE leaf_aggmap AGGMAP
        AGGMAP
        RELATION geog.parentrel OPERATOR SUM
        END

        DEFINE capstone_aggmap AGGMAP
        AGGMAP
        RELATION time.parentrel OPERATOR SUM
        END

2.  Define a variable named `capstone_source` with the following definition to use to aggregate the data.

        DEFINE capstone_source VARIABLE TEXT <time.d>

    As the following output of a REPORT statement illustrates, for each value of `time.d`, you populate `capstone_source` with the name of the variable that contains the corresponding sales data.

        TIME.D            CAPSTONE_SOURCE
        -------------- ----------------------
        Jan76          sales_jan76
        Feb76          sales_feb76
        Mar76          sales_mar76
        76Q1           NA

3.  Issue the following statements to aggregate the variables.

        AGGREGATE sales_jan76 sales_feb76 sales_mar76 USING leaf_aggmap
        AGGREGATE sales_capstone76 USING capstone_aggmap FROMVAR capstone_source

    After aggregating the variables, when you issue the REPORT statements, the variables are populated with the calculated data.

        REPORT sales_jan76  sales_feb76 sales_mar76
        REPORT DOWN geog.d sales_capstone76

        GEOG.D         SALES_JAN76  SALES_FEB76  SALES_MAR76
        -------------- ------------ ------------ ------------
        Boston                1,000        2,000        3,000
        Medford               2,000        4,000        6,000
        San Diego             3,000        6,000        9,000
        Sunnydale             4,000        8,000       12,000
        Massachusetts         3,000        6,000        9,000
        California            7,000       14,000       21,000
        United States        10,000       20,000       30,000

                       -----------------SALES_CAPSTONE76------------------
                       ----------------------TIME.D-----------------------
        GEOG.D            Jan76        Feb76        Mar76         76Q1
        -------------- ------------ ------------ ------------ ------------
        Boston                1,000        2,000        3,000        6,000
        Medford               2,000        4,000        6,000       12,000
        San Diego             3,000        6,000        9,000       18,000
        Sunnydale             4,000        8,000       12,000       24,000
        Massachusetts         3,000        6,000        9,000       18,000
        California            7,000       14,000       21,000       42,000
        United States        10,000       20,000       30,000       60,000

### 9.13 ALLCOMPILE

The ALLCOMPILE program compiles every compilable object in your current analytic workspace, one at a time. As it works, ALLCOMPILE sends to the current outfile messages that show the name of the object being compiled.

ALLCOMPILE uses the COMPILE command. Consequently, it checks for syntax errors as it compiles an object, and it records error messages in the current outfile as appropriate.

#### Syntax

ALLCOMPILE \[n\]

#### Parameters

n
An `INTEGER` expression with a value of zero or higher. The expression specifies the number of objects to be compiled before an UPDATE statement is executed. For example, when you specify `1`, an UPDATE statement is executed after each object is compiled. When you specify `0` (zero), all the objects are compiled and an UPDATE statement is executed only at the end. When you omit the argument, no UPDATE statement is executed by ALLCOMPILE. Frequent updates during an ALLCOMPILE help ensure the most efficient use of space in the analytic workspace.

#### Examples

Example 9-33 ALLCOMPILE Output

The following example shows the output of ALLCOMPILE when it is run on an analytic workspace that contains four programs.

    Compiling AUTOGO
    Compiling READIT
    Compiling REGION.REPORT
    Compiling SALES.REPORT

### 9.14 ALLOCATE

The ALLOCATE command calculates lower-level data from upper-level data by allocating variable data down a hierarchical dimension.

Frequently you allocate data for budgeting, forecasting, and profitability analysis.

#### Syntax

ALLOCATE source \[SOURCE conjoint\] \[BASIS basisname \[ACROSS dimname\]\] -     \[TARGET targetname \[TARGETLOG targetlogname\]\] -     \[USING aggmap\] \[ERRORLOG errorlogfileunit\]

#### Parameters

source
A variable or formula that provides the values to allocate. When the source object is a formula, you must also specify a variable with the TARGET keyword. When you specify a variable as source and you do not specify a target variable or a basisname variable, then ALLOCATE uses source as the basis and the target.

SOURCE conjoint
Specifies a conjoint dimension that contains a list of cells the user has changed. The ALLOCATE command uses this list to produce the smallest target status needed to allocate all of the changed source cells.

BASIS basisname
Specifies a variable, relation, or formula that provides the data on which the allocation is based. That data determines which cells of the target receive allocated values and, in an even or proportional operation, the amount of the source allocated to a target cell.

When the OPERATOR specified by a RELATION (for allocation) statement in aggmap is a COPY operator (COPY, MIN, MAX, FIRST, LAST), the basis tells the ALLOCATE command which target cells to update. When the OPERATOR specified is EVEN, then ALLOCATE derives the counts that it uses for allocation from the basis. When the OPERATOR specified is the PROPORTIONAL, then ALLOCATE uses the basis data to determine the amount to allocate to each target cell. When the OPERATOR is HCOPY, HFIRST, HLAST, or HEVEN, then ALLOCATE does not use a BASIS object. Instead, it allocates the source data to all of the target cells in the dimension hierarchy that is specified by the relation named in the RELATION statement.

When you specify the same variable as both the basis and the target, the current values of the target cells determine the allocation. When you do not specify a basis, then the ALLOCATE command uses the source as the basis.

ACROSS dimname
Specifies a dimension, which can be a named composite, that the ALLOCATE command loops over to discover the cells in a basis. Because a basis can be a formula, you can realize a significant performance advantage by supplying a looping dimension that eliminates the sparsity from the basis loop.

TARGET targetname
Specifies a variable to hold the allocated values. When the source object is a formula, then you must specify a target. When the source object is a variable and you do not specify a target, then ALLOCATE uses the source variable as the target.

TARGETLOG targetlogname
Specifies a variable (identically dimensioned to the targetname variable), or a relation that specifies such a variable, to which ALLOCATE assigns a copy of the allocation. For instance, when ALLOCATE assigns the value of `100` to the cell of the `costs` variable that is specified by the `time` and `product` dimension values `Jan01` and `TV`, and the `targetlog` relation specifies the cell of the `costacct` variable that is specified by the same dimension values, then ALLOCATE assigns the value of `100` to the specified `costacct` cell, also.

USING aggmap
Specifies the name of a previously-defined aggmap to use for the allocation. When you do not include this phrase, the command uses the default allocation specification for the variable as previously specified using the \$ALLOCMAP property.

ERRORLOG errorlogfileunit
Specifies a file unit that ALLOCATE uses for logging allocation deadlocks, errors, or other information. When the allocation does not generate any deadlocks or errors, ALLOCATE sets errorlogname to `NA`. When the allocation produces one or more deadlocks or errors, the events are sent to the specified file. ALLOCATE writes one line in the file for each allocation source that remains unallocated.

When you do not specify a file unit with ERRORLOG, ALLOCATE sends the information to the standard output device.

#### Usage Notes

Preserving Original Basis Values

Often the source, basis, and target objects are the same variable and therefore the original values in the cells of the target variable determine the proportions of the allocation. The allocation overwrites those original values in the target cells with the allocated values. To preserve original values in a variable, specify the original variable as the basis object and save the allocated values to a new variable as the target object. Using different basis and target objects makes it possible for you to preview the allocated data. When you then want to store the allocated values in the same variable as the basis, you can perform the allocation again with the same object as the basis and the target. Another example of using different basis and target objects is using an `actuals` variable as the basis of the allocation and a budget variable as the target.

Using a Formula as a Source or Basis

Source and basis objects can be formulas, which makes it possible for you to make complex computations and have the results be the source or basis object. For example, when you want to see the sales of individual products that would be necessary to produce a thirty percent increase in sales for the next year, you could express the increase in the following formula.

    DEFINE actualsWanted DECIMAL FORMULA <time, product>
    EQ LAG(actuals, 1, time) * 1.3

You would then use ACTUALSWANTED as the source object with the ALLOCATE command. In this example, you would use the ACTUALS variable as the basis.

Tracking Multiple Allocations

When you specify a variable with the TARGETLOG argument, you can store an allocated value in that variable and in the `target` variable. This double entry allocation makes it possible for you to track multiple allocations to the same target cell. For example, when you allocate a series of different costs to the same costs centers, then each allocation increases the values in the target cells. You can keep track of the individual allocations by specifying a different targetlogname variable for each allocation.

Logging Allocation Errors

When you specify a file with the ERRORLOG argument, you can record errors that result from locks and `NA` basis values. The log can provide feedback to an application about which source values remain unallocated. You can use the information to modify the allocation, for example by using a hierarchical operator such as HEVEN in a RELATION statement in the aggmap. You can use the ALLOCERRLOGHEADER and ALLOCERRLOGFORMAT options to format the error log. Within an allocation specification, you can specify other aspects of the error log using the ERRORLOG and ERRORMASK statements.

Logging the Progress of an Allocation

With the cube operations log, you can record and monitor the progress of an allocation. You can use the file to get feedback during a lengthy allocation and to gain information that might be useful for optimizing the allocation in the future.

**See Also:**

Oracle Database PL/SQL Packages and Types Reference for information about the cube operations log and the DBMS_CUBE_LOG package

#### Examples

Example 9-34 Direct Even Allocation

This example allocates a value specified at one level of the `time` dimension hierarchy directly to the variable target cells that are specified by lower level values in the hierarchy without allocating values to an intermediate level. The `timemonthyear` relation specifies the hierarchical relationship of the `time` values. The source, basis, and target of the allocation are all the same variable, PROJBUDGET, which is dimensioned by `division`, `time`, and `line`. The `time` dimension is a nonunique concat dimension that has as its base dimensions `year`, `quarter`, and `month`. The `time` dimension is limited to` <year: Yr02>`, `<quarter: Q1.02>`, `<quarter: q1.02>`, and `<month: Jan02>` to `<month: Jun02>`. The following statements define the `projbudget` variable, set the value of a cell in to `6000` and then report the variable.

    DEFINE projbudget VARIABLE DECIMAL <division time line>
    projbudget(division 'CAMPING' time '<YEAR: YR02>' line  'MARKETING') = 6000
    REPORT projbudget

The preceding statement produces the following results.

    LINE: MARKETING
                     -PROJBUDGET--
                     --DIVISION---
    TIME                CAMPING
    ---------------- -------------
    <year: Yr02>          6,000.00
    <quarter: Q1.02>            NA
    <quarter: Q2.02>            NA
    <month: Jan02>              NA
    <month: Feb02>              NA
    <month: Mar02>              NA
    <month: Apr02>              NA
    <month: May02>              NA
    <month: Jun02>              NA

The following statements define a self-relation on the `time` dimension, relate the `month` values directly to the `year` values, and report the values of the relation.

    DEFINE timemonthyear RELATION time <time>
    LIMIT month TO 'JAN02' TO 'JUN02'
    timemonthyear(time month) = '<YEAR: YR02>'
    REPORT timemonthyear

The preceding statement produces the following results.

    TIME             TIMEMONTHYEAR
    ---------------- -------------
    <year: Yr02>     NA
    <quarter: Q1.02> NA
    <quarter: Q2.02> NA
    <month: Jan02>   <year: Yr02>
    <month: Feb02>   <year: Yr02>
    <month: Mar02>   <year: Yr02>
    <month: Apr02>   <year: Yr02>
    <month: May02>   <year: Yr02>
    <month: Jun02>   <year: Yr02>

The following statements define an aggmap and enter statements into the allocation specification. They allocate the value that is specified by `<year: Yr02>` from `projbudget` to the cells of the same variable that are specified by the `month` dimension values, and then report `projbudget`. The target cells of the variable have `NA` values so the RELATION statement in the allocation specification specifies the HEVEN operator. The ALLOCATE command specifies only one variable, `projbudget`, so that variable is the source and target of the allocation. No basis object is required because the allocation is an HEVEN operation. The allocation is directly from the `year` source value to the `month` target values because that is the hierarchy specified by the relation in the allocation specification.

    DEFINE projbudgmap AGGMAP
    ALLOCMAP 
    RELATION timemonthyear OPERATOR HEVEN
    END
    ALLOCATE projbudget USING projbudgmap
    REPORT projbudget

The preceding statement produces the following results.

    LINE: MARKETING
                     -PROJBUDGET--
                     --DIVISION---
    TIME                CAMPING
    ---------------- -------------
    <YEAR: YR02>          6,000.00
    <QUARTER: Q1.02>            NA
    <QUARTER: Q2.02>            NA
    <MONTH: JAN02>        1,000.00
    ...
    <MONTH: JUN02>        1,000.00

Example 9-35 Recursive Even Allocation with a Lock

This example allocates a value specified at one level of the `time` dimension hierarchy first to the target cells at an intermediate level in a variable and then to the cells that are specified by the lowest level values in the hierarchy. The `timeparent` relation specifies the hierarchical relationship of the `time` values. The source, basis, and target of the allocation are `projbudget`. The status of the `division`, `time`, and `line` dimensions are the same as the direct allocation example. At the beginning of this example, the `projbudget` variable again has just the single value, `6000`, in the cell specified by `<year: Yr02>`.

    DEFINE timeparent RELATION time <time>
    LIMIT quarter TO 'Q1.02' 'Q2.02'
    timeparent(time quarter) = '<YEAR: YR02>'
    LIMIT month TO 'JAN02' TO 'MAR02'
    timeparent(time month) = '<QUARTER: Q1.02>'
    LIMIT month TO 'APR02' TO 'JUN02'
    timeparent(time month) = '<QUARTER: Q1.02>'
    REPORT timeparent

The preceding statement produces the following results.

    TIME             TIMEPARENT
    ---------------- -------------
    <year: Yr02>     NA
    <quarter: Q1.02> <year: Yr02>
    <quarter: Q2.02> <year: Yr02>
    <month: Jan02>   <quarter: Q1.02>
    <month: Feb02>   <quarter: Q1.02>
    <month: Mar02>   <quarter: Q1.02>
    <month: Apr02>   <quarter: Q2.02>
    <month: May02>   <quarter: Q2.02>
    <month: Jun02>   <quarter: Q2.02>

This example demonstrates locking a cell so that it does not participate in the allocation. Locking a cell requires a valueset, so the following statements define one, limit the `time` dimension to the desired value, assign a value to the valueset, and then reset the status of the `time` dimension.

    DEFINE timeval TO '<QUARTER: Q2.02>'
    LIMIT time TO '<Year: YR02>' '<Quarter: Q1.02>'  '<Quarter: Q2.02>' -
       '<month: Jan02>' '<month: Feb02>' '<month: Mar02>' -
       '<month: Apr02>' '<month: May02>' '<month: Jun02>

The following statements revise the specification of the aggmap named `projbudgmap`. This time the RELATION statement in the allocation specification specifies the `timeparent` relation, the HEVEN operator, and the PROTECT argument. The READWRITE keyword specifies that the children of the locked cell also do not participate in the allocation. The NONORMALIZE keyword specifies that the value of the locked cell is not subtracted from the source value before it is allocated to the target cells. The statements then allocate the source value and report the results.

    CONSIDER projbudgmap
    ALLOCMAP 
    RELATION timeparent OPERATOR HEVEN ARGS PROTECT NONORMALIZE READWRITE timeval
    END

    ALLOCATE projbudget USING projbudgmap
    REPORT projbudget

The preceding statement produces the following results.

    LINE: MARKETING
                     -PROJBUDGET--
                     --DIVISION---
    TIME                CAMPING
    ---------------- -------------
    <year: Yr02>          6,000.00
    <quarter: Q1.02>      6,000.00
    <quarter: Q2.02>            NA
    <month: Jan02>        2,000.00
    <month: Feb02>        2,000.00
    <month: Mar02>        2,000.00
    <month: Apr02>              NA
    <month: May02>              NA
    <month: Jun02>              NA

Example 9-36 Recursive Proportional Allocation

This example uses the same relation as the recursive even allocation but it uses the PROPORTIONAL operator and it does not lock any cells. Because a proportional allocation uses the values of the basis object to calculate the values to assign to the target cells, the `projbudget` variable has values assigned to each of its cells. The value of the `<year: Yr02>` cell is `6000`., which was assigned to that cell. It is not the value an aggregation of the lower levels. A report of `projbudget` before the allocation produces the following results.

    LINE: MARKETING
                     -PROJBUDGET--
                     --DIVISION---
    TIME                CAMPING
    ---------------- -------------
    <year: Yr02>          6,000.00
    <quarter: Q1.02>      1,000.00
    <quarter: Q2.02>      2,000.00
    <month: Jan02>          300.00
    <month: Feb02>          100.00
    <month: Mar02>          600.00
    <month: Apr02>          400.00
    <month: May02>          800.00
    <month: Jun02>          800.00

The following statements replace the previous specification of the aggmap with the new RELATION statement, which specifies the PROPORTIONAL operator. The allocation specification includes a `SOURCEVAL` `ZERO` statement, which specifies that the source value is replace with a zero value after the allocation (see the SOURCEVAL statement of the ALLOCMAP command for more information). The statements then allocate the source value and report the result.

    CONSIDER projbudgmap
    ALLOCMAP JOINLINES('RELATION timeparent OPERATOR PROPORTIONAL timeval' -
      'SOURCEVAL ZERO' -
      'END')
    ALLOCATE projbudget USING projbudgmap
    REPORT projbudget

The preceding statement produces the following results.

    TIME             TIMEPARENT
    LINE: MARKETING
                     -PROJBUDGET--
                     --DIVISION---
    TIME                CAMPING
    ---------------- -------------
    <year: Yr02>                 0
    <quarter: Q1.02>      2,000.00
    <quarter: Q2.02>      4,000.00
    <month: Jan02>          600.00
    <month: Feb02>          200.00
    <month: Mar02>        1,200.00
    <month: Apr02>          800.00
    <month: May02>        1,600.00
    <month: Jun02>        1,600.00

### 9.15 ALLOCMAP

The ALLOCMAP command identifies an aggmap object as an allocation specification and enters the contents of the specification. To use AGGMAP to assign an allocation specification to n aggmap object, the definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

An alternative to the AGGMAP command is the EDIT AGGMAP command, which is available only in OLAP Worksheet. The EDIT AGGMAP command opens an Edit window in which you can delete or change an allocation specification for an aggmap object. To use the OLAP Worksheet, to code an allocation specification follow the instructions given in "Editing a Newly Defined Aggmap to Code an Allocation Specification".

**See Also:**

"[OLAP DML Allocation Objects](formulas-models-aggregations-and-allocations.md)" and "[Allocation Options](olap-dml-options.md)".

#### Syntax

ALLOCMAP \[specification\]

#### Parameters

specification
A multiline text expression that is the allocation specification for the current aggmap object. An allocation specification begins with an ALLOCMAP statement and ends with an `END` statement. Between these statements, you code one or more of the following statements depending on the calculation that you want to specify:

- CHILDLOCK
- DEADLOCK
- DIMENSION (for allocation)
- ERRORLOG
- ERRORMASK
- MEASUREDIM (for allocation)
- RELATION (for allocation)
- SOURCEVAL
- VALUESET

Each statement is a line of the multiline text expression. When coding an ALLOCMAP statement at the command line level, separate statements with newline delimiters (`\n`), or use JOINLINES.

For a discussion of how to determine which statements to include, see "Designing an Allocation Specification".

#### Usage Notes

Designing an Allocation Specification

Minimally, an allocation specification consists of a RELATION statement or a VALUESET statement However, you can create more complex allocation specifications and change the default settings for error handling by including additional OLAP DML statements in the specification, as follows:

1.  For hierarchical allocations, a RELATION statement that specifies a self-relation that identifies the child-parent relationships of the hierarchy. List the statements in the order in which you want to perform the various operations; or if this is not important, list the RELATION statements in the same order as the dimensions appear in the variable definition.

2.  For non-hierarchical allocations, a VALUESET statement that specifies the values to be used when allocating.

3.  A CHILDLOCK statement that tells the ALLOCATE command whether to determine if RELATION statements in the aggmap specify lock on both a parent and a child element of a dimension hierarchy.

4.  A DEADLOCK statement that tells the ALLOCATE command whether to continue an allocation when it encounters a deadlock, which occurs when the allocation cannot distribute a value because the targeted cell is locked or, for some operations, has a basis value of `NA.`

5.  When a dimension is not shared by the target variable and the source or the basis objects, a DIMENSION (for allocation) statement that specifies a single value to set as the status of that dimension.

6.  An ERRORLOG statement that specifies how many errors to allow in the error log specified by the ALLOCATE command and whether to continue the allocation when the maximum number of errors has occurred.

7.  An ERRORMASK statement that specifies which error conditions to exclude from the error log.

8.  When the source data comes from a variable, a SOURCEVAL statement that specifies whether ALLOCATE changes the source data value after the allocation.

Aggmap Type

You can use the AGGMAPINFO function to learn the type of an aggmap. An aggmap into which you have entered an allocation specification using the ALLOCMAP has the type ALLOCMAP and an aggmap into which you have entered an aggregation specification using an AGGMAP statement has the type AGGMAP. When you have defined an aggmap but have not yet entered a specification in it, its type is `NA`.

One RELATION for Each Dimension

An aggmap can have only one RELATION statement for any given dimension.

One Hierarchy For Each Dimension

An allocation operation proceeds down only one hierarchy in a dimension. When a dimension has multiple hierarchies, then you must limit the dimension to a hierarchy with a qualified data reference after the rel-name argument.

#### Examples

Example 9-37 Allocation Specification from an Input File

In this example an aggmap and its specification are defined in an ASCII disk file called `salesalloc.txt`. The statements in the file are then executed in the analytic workspace through the use of the INFILE statement. The statements in `salesalloc.txt` are the following.

    IF NOT EXISTS ('salesalloc')
      THEN DEFINE salesalloc AGGMAP
      ELSE CONSIDER salesalloc
    ALLOCMAP
      RELATION time.parent OPERATOR EVEN
      RELATION product.parent OPERATOR EVEN
      RELATION geography.parent OPERATOR EVEN
      SOURCEVAL ZERO
      DEADLOCK SKIP
    END

To include the `salesalloc` aggmap in your analytic workspace, execute the following statement.

    INFILE 'salesalloc.txt'

The `sales.agg` aggmap has now been defined and contains three RELATION statements and the SOURCEVAL and DEADLOCK statements. In this example, the ALLOCATE statement allocates its source value evenly to all of the aggregate level cells and the detail level cells of the target variable because the relations `time.parent`, `product.parent`, and `geography.parent` relate each child dimension value to its parent in the dimension hierarchy. The DEADLOCK statement tells the ALLOCATE statement to log an error and continue the allocation when a branch of a target hierarchy is locked or has a value of `NA`. The SOURCEVAL statement tells ALLOCATE to assign a zero value to the source cells after allocating the source data.

You can now use the `salesalloc` aggmap with an ALLOCATE statement, such as.

    ALLOCATE sales USING salesalloc

Example 9-38 Allocation Specification from a Text Expression

In this example the `salesalloc` aggmap has already been defined. The specification is added to the aggmap as a text expression argument to the ALLOCMAP statement.

    CONSIDER salesalloc
    ALLOCMAP
    RELATION time.parent OPERATOR EVEN
    RELATION product.parent OPERATOR EVEN
    RELATION geography.parent OPERATOR EVEN
    SOURCEVAL ZERO
    DEADLOCK SKIP

Example 9-39 Specifying a Single Dimension Value in an Allocation Specification

This example proportionally allocates a value it calculates from the `sales` variable to cells in a `projectedsales` variable. The `sales` variable is dimensioned by the `time`, `product`, `customer`, and `channel` dimensions.

The example defines the `projectedsales` variable to use as the target of the allocation and the `increasefactor` formula to use as the source. The formula multiplies values from `sales` by ten percent. The example limits the `time` dimension and creates the `ytoq.rel` relation, which relates the year 2001 to the quarters of 2002. The next LIMIT commands limit the dimensions shared by `sales` and `projectedsales`.

The example creates an aggmap and uses the ALLOCMAP statement to enter a RELATION and a DIMENSION statement into the map. The RELATION statement specifies the `ytoq.rel` relation as the dimension hierarchy to use for the allocation and specifies that the allocation is proportional. The DIMENSION statement tells ALLOCATE to set the status of the `channel` dimension to `totalchannel` for the duration of the allocation.

    DEFINE projectedSales DECIMAL VARIABLE <time, SPARSE <product, customer>>
    DEFINE increaseFactor DECIMAL FORMULA <product>
    EQ sales * 1.1
    LIMIT time TO '2001' 'Q1.02' TO 'Q4.02'
    DEFINE YtoQ.rel RELATION time <time>
    LIMIT time TO 'Q1.02' to 'Q4.02'
    YtoQ.rel = '2001'
    LIMIT time TO '2001' 'Q1.02' to 'Q4.02'
    LIMIT product TO 'TotalProduct' 'Videodiv' 'Audiodiv' 'Accdiv'
    LIMIT customers TO 'TotalCustomer'
    DEFINE time.alloc AGGMAP
    ALLOCMAP
    RELATION YtoQ.rel OPERATOR PROPORTIONAL
    DIMENSION channel 'TotalChannel'
    END
    ALLOCATE increaseFactor BASIS sales TARGET projectedSales USING time.alloc

The `sales` values that are the basis of the allocation are the following.

    CHANNEL: TOTALCHANNEL
    CUSTOMERS: TOTALCUSTOMER
                     ---------------PROJECTEDSALES---------------
                     --------------------TIME--------------------
    PRODUCT           2001      Q1.02      Q2.02      Q3.02      Q4.02
    ------------     ------     ------     ------     ------     ------
    TotalProduct      7000       1000       2000       3000       1000
    Videodiv          4100        600       1100       1900        500
    Audiodiv          1700        200        600        600        300
    Accdiv            1200        200        300        500        200

The following shows a report of `projectedsales` for `totalchannel` after the allocation.

    CHANNEL: TOTALCHANNEL
    CUSTOMERS: TOTALCUSTOMER
                     ---------------PROJECTEDSALES---------------
                     --------------------TIME--------------------
    PRODUCT           2001      Q1.02      Q2.02      Q3.02      Q4.02
    ------------     ------     ------     ------     ------     ------
    TotalProduct       NA         NA         NA         NA         NA
    Videodiv           NA        660       1210       2090        550
    Audiodiv           NA        220        660        660        330
    Accdiv             NA        220        330        550        220

Example 9-40 Entering RELATION Statements in an Allocation Specification

This example defines a `time.type` dimension and adds to it the two hierarchies of the `time` dimension. It defines the `time.time` relation that relates the hierarchy types (that is, `time.type`) to the `time` dimension. The example defines the `time.alloc` aggmap. With the ALLOCMAP command, it enters a RELATION statement in the aggmap. The RELATION statement specifies the values of the `time` dimension hierarchy to use in the allocation, limits the `time` dimension to one hierarchy with the QDR, and the specifies the EVEN operation for the allocation. The ALLOCATE command then allocates data from the source object to the target variable using the `time.alloc` aggmap. In the ALLOCATE command the source, basis, and target objects are the same `sales` variable.

     
    DEFINE time.type TEXT DIMENSION
    MAINTAIN time.type add 'Fiscal'
    MAINTAIN time.type add 'Calendar'
    DEFINE time.time RELATION time <time, time.type>
    DEFINE time.alloc AGGMAP
     
    ALLOCMAP
    RELATION time.time (time.type 'Fiscal') OPERATOR EVEN 
    END
     
    ALLOCATE sales USING time.alloc

#### 9.15.1 CHILDLOCK

Within an allocation specification, a CHILDLOCK statement tells the ALLOCATE statement to determine if RELATION statements in the allocation specification have specified locks on both a parent and on a child of the parent in a dimension hierarchy. Locking both a parent and one of its children can cause incorrect allocation results.

##### Syntax

CHILDLOCK \[DETECT\|NODETECT\]

##### Parameters

DETECT
Tells the ALLOCATE statement to detect that an allocation lock exists on a parent and also on one of its children in a dimension hierarchy. When it detects a locked parent and child, the ALLOCATE statement creates an entry in the error log for the allocation.

NODETECT
(Default) Tells the ALLOCATE statement to continue an allocation even when a lock exists on a parent and also on one of its children in a hierarchy.

##### Examples

For an example of using a CHILDLOCK statement in an allocation specification, see Example 9-79.

#### 9.15.2 DEADLOCK

Within an allocation specification, a DEADLOCK statement tells the ALLOCATE statement what to do when it cannot distribute a source value to a target cell specified by a value in a dimension hierarchy because the target cell is either locked by a RELATION statement in the allocation specification or the cell has a basis value of `NA`.

##### Syntax

DEADLOCK \[SKIP\|NOSKIP\]

##### Parameters

SKIP
Tells the ALLOCATE statement to log the error and continue with the allocation even though it cannot distribute source values to cells specified by a branch of a dimension hierarchy because a target cell is locked or the basis value of the cell is `NA`.

NOSKIP
Tells the ALLOCATE statement to stop the allocation and to return an error when it cannot distribute source values to cells in a branch of a dimension hierarchy because a target cell is locked or the basis value is `NA`. NOSKIP is the default action when you do not include a DEADLOCK statement in the aggmap used by the ALLOCATE command.

##### Examples

For examples of using a DEADLOCK statement in an allocation specification, see Example 9-37 and Example 9-38.

#### 9.15.3 DIMENSION (for allocation)

Within an allocation specification, a DIMENSION statement sets the status to a single value of a dimension. Within an allocation specification this dimension is a dimension that the source, basis, and target objects do not have in common. When an allocation specification does not specify such single values with DIMENSION statements, Oracle OLAP uses the current status values of the dimensions when performing the allocation.

You use a DIMENSION statement to ensure that the status of a dimension is set to the value that you want it to have for the allocation. You must use a separate DIMENSION statement for each dimension that is not shared by the source, basis, and target objects.

##### Syntax

DIMENSION dimension 'dimval'

##### Parameters

dimension
the name of the dimension to limit.

dimval
The single value of the dimension to which you want the status of the dimension set for the duration of an allocation.

##### Examples

For an example of using a DIMENSION statement in an allocation specification, see Example 9-39.

#### 9.15.4 ERRORLOG

Within an allocation specification, an ERRORLOG statement specifies how many allocation error conditions to log and whether to continue or to stop the allocation when the specified maximum number of errors have been logged. You specify the error log with the ERRORLOG keyword to the ALLOCATE command.

##### Syntax

ERRORLOG \[UNLIMITED\|MAX \<num\>\] \[STOP\|NOSTOP\]

##### Parameters

UNLIMITED
Tells the ALLOCATE command to write an unlimited number of errors to the error log. (Default.)

MAX num
Specifies a maximum number of errors that ALLOCATE can write to the error log.

STOP
NOSTOP
Specifies whether to stop the allocation when ALLOCATE has written the maximum number of errors to the error log. When you specify STOP, the allocation stops. When you specify NOSTOP, the allocation continues but ALLOCATE does not write any more errors to the error log. When you have specified UNLIMITED, then the STOP and NOSTOP arguments have no effect and the allocation continues no matter how many errors occur.

##### Usage Notes

Formatting the Error Log

The ALLOCERRLOGFORMAT option determines the contents and the formatting of the error log that you specify with the ERRORLOG argument to the ALLOCATE command. You can specify a header for the error log with the ALLOCERRLOGHEADER option.

#### 9.15.5 ERRORMASK

Within an allocation specification, an ERRORMASK statement specifies the error conditions that you do not want to appear in the allocation error log. You specify the error log with the ERRORLOG keyword to the ALLOCATE command.

##### Syntax

ERRORMASK \<num...\>

##### Parameters

num...
The number of the error that you do not want to appear in the error log.

##### Examples

Example 9-41 Excluding CHILDLOCK Errors

To exclude a CHILDLOCK error, you would enter the following statement in the allocation specification.

    ERRORMASK 10

Example 9-42 Excluding All Allocation Errors

To exclude all errors, you would enter the following statement in the allocation specification.

    ERRORMASK 1 2 3 4 5 6 7 8 9 10

#### 9.15.6 MEASUREDIM (for allocation)

Within an allocation specification, a MEASUREDIM statement identifies the name of a measure dimension that is specified in the definition of an operator variable or an argument variable. However, you cannot specify a measure dimension when it is included in the definition of the aggmap object.

##### Syntax

MEASUREDIM name

##### Parameters

name
The name of the measure dimension. A measure dimension is a dimension that you define. The dimension values are names of existing variables.

**See Also:**

MEASUREDIM (for aggregation) statement for the AGGMAP command

#### 9.15.7 RELATION (for allocation)

Within an allocation specification, a RELATION statement identifies a relation that specifies the path through a dimension hierarchy and the method of the allocation. To allocate a source data down a hierarchy of a dimension, you must specify with a RELATION statement the values of the hierarchy that identify the cells of the variable that are the targets of the allocation. When the target of the allocation is a multidimensional variable, then you must include a separate RELATION statement for each dimension down which you want to allocate the source data. The order of the RELATION statements in an aggmap determines the order of the allocation. The allocation proceeds down the dimension hierarchy in the first RELATION statement, then down the second, and so on.

**Note:**

Do not confuse this RELATION statement which can only be used as part of an AGGMAP command with either the RELATION command that defines a default relation for a dimension or the RELATION statement that is used as part of an AGGMAP command.

##### Syntax

RELATION rel-name \[(qdr. . .)\] OPERATOR {operator\|} -

     \[NAOPERATOR operator\] \[REMOPERATOR operator\] -      \[PARENTALIAS dimension-alias-name\] -      \[ARGS {\[FLOOR floorval\] \[CEILING ceilval\] \[MIN minval\] \[MAX maxval\] -      \[NAHANDLE {IGNORE\|CONSIDER\|PREFER}\] -      \[ADD\|ASSIGN\] \[PROTECT \[NONORMALIZE\] \[READWRITE\|WRITE\] lockvalueset\] -      \[WEIGHTBY \[ADD\|MULTIPLY\] \[WNAFILL nafillval\] weightobj\]}\]

##### Parameters

rel-name
An Oracle OLAP self-relation that specifies the values of a dimension hierarchy that identify the path of allocation. The cells in the target variable identified by the values in rel-name receive the allocated data.

qdr. . .
One or more qualified data references that specify a single dimension value for each dimension of the relation that is not part of the self-relation. When the self-relation has multiple hierarchies, you must provide a qdr for the hierarchy dimension of the self-relation dimension that limits to single values any hierarchies not involved in the allocation.

OPERATOR operator
Specifies an allocation method described in the following table or returned by ALLOCOPS. The method determines the cells of the target variable for the rel-name relation to which ALLOCATE assigns a value. For the FIRST, LAST, HFIRST, and HLAST operators, ALLOCATE uses the order of the value in the dimension to determine the cell. The dimension order is the default logical order of the allocation dimension. There is no default operator for allocation.

Table 9-3 Allocation Operators

| Operator     | Description                                                                                                                                                                                                                                      |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COPY         | Copies the allocation source to all of the target cells that have a basis data value that is not `NA`.                                                                                                                                           |
| HCOPY        | Copies the allocation source to all of the target cells specified by the hierarchy even when the data in any of those cells is `NA`. When the source data is `NA`, then that `NA` value is not allocated to the target cells of that allocation. |
| MIN          | Copies the allocation source to the target that has the smallest basis data value.                                                                                                                                                               |
| MAX          | Copies the allocation source to the target that has the largest basis data value.                                                                                                                                                                |
| FIRST        | Copies the allocation source to the first target cell that has a non-`NA` basis data value.                                                                                                                                                      |
| HFIRST       | Copies the allocation source to the first target cell specified by the hierarchy even when the current data value of that cell is `NA`                                                                                                           |
| LAST         | Copies the allocation source to the last target cell that has a non-`NA` basis data value.                                                                                                                                                       |
| HLAST        | Copies the allocation source to the last target cell specified by the hierarchy even when the current data value of that cell is `NA`                                                                                                            |
| EVEN         | Divides the allocation source by the number of target cells that have non-`NA` basis data values and applies the quotient to each target cell.                                                                                                   |
| HEVEN        | Divides the allocation source by the number of target cells, including the ones that have `NA` values, and applies the quotient to each target cell.                                                                                             |
| PROPORTIONAL | Divides the allocation source by the sum of the data values of the target cells that have non-`NA` basis data values, multiplies the basis data value of each target cell by the quotient, and applies the resulting data to the target cell.    |

NAOPERATOR operator
The operator after the NAOPERATOR keyword specifies the operator that the ALLOCATE operation uses when it encounters an `NA` or lock-based deadlock. Valid operators are HFIRST, HLAST, and HEVEN.

REMOPERATOR operator
The operator after the REMOPERATOR keyword specifies the operator that the ALLOCATE operation uses when storing a remainder produced by an allocation. For example, assume you allocate the `INTEGER` 10 to three cells at the same level in a hierarchy, there is a remainder of 1. The REMOPERATOR specifies where you want the allocation operation to store this remainder. Valid operators for REMOPERATOR are MIN, MAX, FIRST, HFIRST, LAST, and HLAST.

ARGS
Indicates additional arguments specify additional parameters for the allocation operation. All of these arguments apply uniformly to the dimension hierarchy specified by rel-name.

PARENTALIAS dimension-alias-name
Specifies specialized allocation depending on the parent (for example, weighting by parent or child). For dimension-alias-name, specify the name of the alias for the dimension of rel-name.

ARGS argument...
One or more arguments after the ARGS keyword that specify additional parameters for the allocation operation. All of these arguments apply uniformly to the dimension hierarchy specified by rel-name.

FLOOR floorval
Specifies that when an allocated target data value is less than floorval, the data allocated to the target cell is `NA`. This argument applies to the relation only when the PROPORTIONAL operator is specified.

CEILING ceilval
Specifies that when an allocated target data value is greater than ceilval, the data allocated to the target cell is `NA`. This argument applies to the relation only when the PROPORTIONAL operator is specified.

MIN minval
Specifies that when an allocated target data value is less than minval, the data allocated to the target cell is minval.

MAX maxval
Specifies that when an allocated target data value is greater than maxval, the value allocated to the target cell is maxval.

NAHANDLE
Specifies how ALLOCATE treats `NA` values. Valid only when the OPERATOR is MIN or MAX.

- `IGNORE` specifies that ALLOCATE does not consider `NA` values in a MIN or MAX operation. (Default)

- `CONSIDER` specifies that ALLOCATE treats an `NA` value as a zero; however, when the data value of a target cell is actually zero, the zero cell receives the allocated data value and not the `NA` cell.

- `PREFER` specifies that ALLOCATE treats an `NA` value as a zero and the `NA` has priority over a zero value, so the `NA` cell receives the allocated data value and not the cell with the actual zero value.

ADD
Specifies that ALLOCATE adds the allocated data to the current data in the target cell.

ASSIGN
Specifies that ALLOCATE replaces the data in the target cell with the allocated data, which is the default behavior.

PROTECT lockvalueset
Specifies a set of dimension values to lock so that they cannot be targets of the allocation. Before allocating the source data, the allocation operation normalizes the sources by subtracting the data values of the specified locked cells from the source data.

NONORMALIZE
Specifies that the allocation operation does not normalize the source data. Using NONORMALIZE effectively removes from the allocation the values of the hierarchy at and below the dimension values specified by lockvalueset.

READWRITE
Specifies that the locked data values cannot be used as source data in a subsequent allocation, thereby locking the data of the hierarchy below the lockvalueset values.

WRITE
Specifies that the allocation cannot store data values in the cells identified by the lockvalueset dimension values but the allocation can use the data in those cells as source data in its subsequent steps. However, when in the aggmap you include a SOURCEVAL statement that specifies `NA` or `ZERO` and the locked cell is the source of an allocation, then ALLOCATE sets the value of the locked cell to `NA` or zero after the allocation.

WEIGHTBY
Specifies that the allocation uses a the value specified by weightobj. Using this clause allows for processes such as unit or currency conversion.

ADD
Specifies that ALLOCATE adds the value specified by weightobj to the existing data value of the target and assigns the sum to the target cell.

MULTIPLY
(Default) Specifies that ALLOCATE multiplies the value specified by weightobj by the data value of the target and assigning the product.

WNAFILL
Specifies that ALLOCATE replaces `NA` values in a cell before applying the value specified by weightobj to the nafillval value.

nafillval
The value that the ALLOCATE replaces `NA` values with. When you specify the ADD option to the WEIGHTBY clause, the default `NA` fill value is `0`; in all other cases, the default `NA` fill value is `1`.

weightobj
The name of an variable, formula, or relation whose value or values are the weights that Oracle OLAP applies to the allocated data just before it is stored in the target cell. When a relation is used, the target variable is referenced based on the weight relation and the cell is applied to the allocation target cell.

##### Usage Notes

Specifying the Path of the Allocation

The path of the allocation is the route the allocation system takes to go from the source data to the target data. Very different results derive from different allocation paths. You specify the path with the RELATION statements that you enter in the aggmap. The relation objects in the RELATION statements and the order of those statements specify the path and the method of allocation.

The allocation path goes from any level in the hierarchy of a dimension to any lower level of the hierarchy. You use a relation object that relates the members of the hierarchy to each other (a self-relation) to identify the elements of the hierarchy that you want to participate in the allocation. The allocation proceeds down the hierarchy of the dimension in the first RELATION statement in the aggmap, then down the hierarchy of the second RELATION statement, and so on.

When the dimension has multiple hierarchies, you must use the qdr argument in the RELATION statement to specify which hierarchy to use for the allocation. The hierarchy that you specify with a relation must not contain a circular relation (for example, one in which dimension value `A` relates to dimension value `B` which relates to dimension value `C` which relates to dimension value `A`).

Types of Allocation Paths

You can allocate values from a source to a target with any one of the following types of paths:

- Direct allocation path ­— You can allocate values directly from a source to the final target cells with no allocations to intermediate nodes of the hierarchy. For example, you can allocate source data values specified by dimension values at the `Quarter` level of a hierarchical `time` dimension to those at the `Month` level or those specified by dimension values at the `Year `level to those at the `Month` level.

- Recursive descent hierarchy path ­— You can allocate values to intermediate nodes of the hierarchy and then to final target cells. For example, you can allocate source data values specified by dimension values at the `Category` level of a `product` dimension to those at the `Subcategory` level and then to those at the `ProductID` level.

- Multidimensional allocation path ­— You can allocate values first down one dimension and then down another dimension. The allocations can be direct or recursive or a combination of both. The results might vary depending on the order of the allocation.

- Simultaneous multidimensional allocation path ­— You can do a direct allocation of values simultaneously to variable cells specified by multiple dimensions by creating a composite dimension that specifies the non-`NA` cells of the variable to which you want to allocate values. You then use that composite as the basis of the allocation.

Restrictions When Designing a RELATION Statement for Allocation

Keep the following restrictions in mind when designing a RELATION statement:

- Oracle OLAP can perform allocations on only one hierarchy in a dimension in one execution of the ALLOCATE command. When a dimension has multiple hierarchies, then you must supply a qdr argument to limit the relation to only one hierarchy.

- An allocation specification must include either a RELATION statement or a VALUESET statement.

- Only one RELATION statement or VALUESET statement may be used for each dimension in the allocation specification.

Locking Cells in the Allocation Path

Sometimes you want a cell to retain its existing value and to not be affected by an allocation. You can lock a value of the hierarchy of the dimension and thereby remove that value from the allocation path.When you lock a value above the detail level in a hierarchy, then you remove the branch of the hierarchy below that value from the allocation. To lock a value, use the PROTECT argument to the RELATION statement.

For example, when you want to allocate a yearly budget that you revise monthly, then you would set the value of the `budget` at the `Year` level of the `time` dimension hierarchy. You would allocate data to the elements that are at the `Month` level. As the year progresses, you would enter the actual data for a month and then lock that element and reallocate the remaining yearly budget value to see the new monthly targets that are required to meet the annual goal.

When you lock an element, you can specify whether the source value is renormalized. By default, when you lock an element of the hierarchy, the value of the cell of the target variable specified by that element is subtracted from the source value and the remainder is allocated to the target cells. When you do not want the source renormalized during the allocation, specify NONORMALIZE after the PROTECT argument.

##### Examples

For an example of using RELATION statements in an allocation statement, see the examples in the ALLOCMAP command, especially Example 9-40.

#### 9.15.8 SOURCEVAL

Within an allocation specification, a SOURCE VAL statement specifies the value that the ALLOCATE command assigns to a source cell in an allocation operation after it successfully allocates the value that the cell contained before the allocation.

The default value of SOURCEVAL is `NA`, which means that ALLOCATE sets the value of each of the allocated source cells to `NA` following the allocation. When you specify CURRENT as the SOURCEVAL, then the allocated source cells retain the values that they had before the allocation. When you specify `ZERO` as the SOURCEVAL, then ALLOCATE assigns a zero value to each source cell that is allocated.

##### Syntax

SOURCEVAL \[CURRENT\|ZERO\|NA\]

##### Parameters

CURRENT
Specifies that the value of a source cell after the allocation equals its value before the allocation.

ZERO
Specifies that the value of a source cell after the allocation is zero.

NA
Specifies that the value of a source cell after the allocation is `NA`. (Default value.)

#### 9.15.9 VALUESET

Within an allocation specification, a VALUESET statement specifies the target dimension values of an allocation. A dimensioned valueset can be used to specify the allocation targets for an entire non-hierarchical dimension such as a measure or line dimension.

**Note:**

Keep the following restrictions in mind:

- An allocation specification must include at least one RELATION statement or a VALUESET statement.

- You can only specify one RELATION statement or VALUESET statement for each dimension specified in the allocation specification.

##### Syntax

VALUSET vs-name\[(nondimvalueset)\| qdr... \] OPERATOR operator \| opvar –       \[NAOPERATOR text -exp\] \[REMOPERATOR text -exp\] -       \[ARGS \[FLOOR floorval\] \[CEILING ceilval\] –       \[MIN minval\] \[MAX maxval\] –       \[ADDT \[ {TRUE\|FALSE} \| ASSIGN\] –       \[{PROTECTRW\| PROTECTW}  \[NONORMALIZE\] lockvalueset\] –       \[WEIGHTBY \[ADD\] weightobj \[WNAFILL nafillval\]\] \| -       \[WEIGHTBY WEIGHTVAR wobjr\]\]

##### Parameters

vs-name
Specifies the name of a valueset object that specifies the values of a dimension which are the path of allocation. The cells in the target variable identified by the values in vs-name receive the allocated data.

nondimvalueset
When vs-name is a dimensioned valueset, specifies a nondimensioned valueset that is the status used to loop the valueset dimension. When you do not include nondimvalueset or qdr, Oracle OLAP uses the default logical order of the dimensions, not its current status.

qdr
When vs-name is a non-dimensioned valueset, one or more qualified data references that specify the dimension values to use when allocating data.

OPERATOR operator
The operator argument after the OPERATOR keyword is a text expression that is an operator type described in RELATION (for allocation). The operator type specifies the method of the allocation. The method determines the cells of the target variable for the vs-name relation to which ALLOCATE assigns a value. Unless you have specified a different status using dimorder valueset, for the FIRST, LAST, HFIRST, and HLAST operators, ALLOCATE uses the default logical order of the allocation dimension to determine the cell. There is no default operator for allocation.

OPERATOR opvar
The opvar argument after OPERATOR keyword specifies a `TEXT` variable that specifies different the operation for each of the values of a dimension. The values of the variable are the allocation operators described in RELATION (for allocation). An operator variable is used to change the allocation operator with the values of one dimension. The opvar argument is used with the following types of dimensions:

- Measure dimension -- Changes the allocation method depending upon the variable being allocated. The values of the measure dimension are the names of the variables to be allocated. It dimensions a text variable whose values identify the operation to be used to allocate each measure. The allocation specification must include a MEASUREDIM (for allocation) statement that identifies the measure dimension.

- Line item dimension -- Changes the allocation method depending upon the line item being allocated. The line item dimension is typically non-hierarchical and identifies financial allocations. The line item dimension is used both to dimension the data variable and to dimension a text variable that identifies the operation to be used to allocate each item. The operation variable is typically used to allocate line items over time.

The opvar argument cannot be dimensioned by the dimension it is used to allocate. For example, when you want to specify different operations for the `geography` dimension, then opvar cannot be dimensioned by `geography`.

**Tip:**

To minimize the amount of paging for the operator variable, define the opvar variable as type of `TEXT` with a fixed width of `8`.

NAOPERATOR text-exp
The operator after the NAOPERATOR keyword specifies the operator that the ALLOCATE operation uses when it encounters an `NA` or lock-based deadlock. Valid operators are HFIRST, HLAST, and HEVEN which are described in RELATION (for allocation).

REMOPERATOR text-exp
The operator after the REMOPERATOR keyword specifies the operator that the ALLOCATE operation uses when storing a remainder produced by an allocation. For example, assume you allocate the `INTEGER` 10 to three cells at the same level in a hierarchy, there is a remainder of 1. The REMOPERATOR specifies where you want the allocation operation to store this remainder. Valid operators for REMOPERATOR are MIN, MAX, FIRST, HFIRST, LAST, and HLAST which are described in RELATION (for allocation).

ARGS
Indicates that additional arguments specify additional parameters for the allocation operation. All of these arguments apply uniformly to the valueset.

FLOOR floorval
Specifies that when an allocated target value falls below the value specified in floorval, Oracle OLAP stores the value as NA.

CEILING ceilval
Specifies that when an allocated target value exceeds the value specified in ceilval, then Oracle OLAP stores the value as NA.

MIN minval
Specifies that when an allocated target value falls below the value specified minval, then Oracle OLAP stores the value of minval in the target.

MAX maxval
Specifies that when an allocated target value exceeds the value specified maxval, then Oracle OLAP stores the value of maxval in the target

ADDT {TRUE\|FALSE}
The ADDT phrase specifies the sign of the addition when Oracle OLAP adds target cells to the existing contents of the target cell:

- `TRUE` specifies that the results of the allocation are added to the target. (Default)

- `FALSE` specifies that the results of the allocation are subtracted from the target cell.

PROTECTRW lockvalueset
Specifies that the dimension members specified by lockvalueset cannot be the targets or source values of allocation. Using this phrase allows users to specify an allocation "lock" on a hierarchical subtree. The current contents of the target cell are subtracted from the source and the source and basis is renormalized.

PROTECTW lockvalueset
Specifies that the dimension members specified by lockvalueset cannot be the targets of an allocation. However, these target cells are used as the source values for subsequent steps in the allocation process. When the SOURCEVAL statement is set to `0` (zero) or `NA` and these values are reallocated, they are set appropriately.

NONORMALIZE
Specifies that Oracle OLAP should not renormalize the source and basis based on the protected cells. Specifying this keyword has an effect similar to removing a sub-branch from a hierarchy. Frequently, when you use this keyword, if, after allocation, data is aggregated from the allocation level, the source cell probably does not contain the original allocated amount

WEIGHTBY weightobj
Specifies a weight that should be applied to the target cell just before it is stored. Using this phrase allows for processes such and unit or currency conversion. Value weight objects are variables, formulas and relations. When a relation is used, the target variable is referenced based on the weight relation, and the cell is applied the allocation target cell.

ADD
Specifies that Oracle OLAP adds the value of the weight to the allocation target rather than using multiplication.

WNAFILL nafillval
Specifies the default value of the weight variable that should be used. When you do not include an `ADD` clause, the default value of `nafillval` is `1`. When you include the `ADD` clause, the default value of `nafillval` is `0` (zero).

WEIGHTBY WEIGHTVAR wobj
Specifies that the allocated data should be weighted. The wobj argument is the name of a variable, relation, or formula whose values are the weights that Oracle OLAP applies to the allocated data just before it is stored in the target cell. Using this clause allows for processes such as unit or currency conversion and enables you to use different weight objects with the different operators specified in the operator variable you created for the OPERATOR opvar clause.

### 9.16 ALLSTAT

The ALLSTAT program sets the status of all dimensions in the current analytic workspace to all their values. ALLSTAT does not, however, set the status of the NAME dimension.

#### Syntax

ALLSTAT

#### Usage Notes

Limiting One Dimension

You can set the status of a single dimension to all its values with the LIMIT command.

ALLSTAT and the LOCK_LANGUAGE_DIMS Option

When LOCK_LANGUAGE_DIMS is `TRUE`, ALLSTAT ignores language dimensions. When LOCK_LANGUAGE_DIMS is `FALSE`, ALLSTAT treats language dimensions the same way it treats other dimensions.

**See Also:**

[\$DEFAULT_LANGUAGE](olap-dml-properties.md) property and [LOCK_LANGUAGE_DIMS](olap-dml-options.md) option

#### Examples

Example 9-43 Limiting to All Values

The following STATUS statement produces the current status of the dimensions of the variable UNITS.

    status units

    The current status of MONTH is:
    Jul96 TO Dec96
    The current status of PRODUCT is:
    Tents TO Racquets
    The current status of DISTRICT is:
    DALLAS

After you execute an ALLSTAT statement the same STATUS statement produces this output.

    The current status of MONTH is:
    ALL
    The current status of PRODUCT is:
    ALL
    The current status of DISTRICT is:
    ALL

### 9.17 ARGUMENT

Within an OLAP DML program, the ARGUMENT statement declares an argument that is expected by the program. Within the program, the argument is stored in a structure similar to a variable or valueset. The argument is initialized with the value that was passed when the program was invoked. An argument exists only while the program is running.

The ARGUMENT statement is used only in programs, and it must precede the first executable line in the program. Be careful to distinguish the ARG abbreviation of the ARGUMENT statement from the ARG function.

#### Syntax

ARGUMENT name {datatype\|dimension\|VALUESET dim}

#### Parameters

name
The name by which the argument is referenced in the program. An argument cannot have the same name as a local variable or valueset. You name an argument according to the rules for naming analytic workspace objects (see the DEFINE command).

datatype
The data type of the argument, which indicates the kind of data to be stored. You can specify any of the data types that are listed and described in the DEFINE VARIABLE entry. Also, when you want to the program to be able to receive an argument without converting it to a specific data type, you can also specify `WORKSHEET` for the data type.

**Note:**

When you declare an argument to be of type NTEXT, and a TEXT value is passed into the program, Oracle OLAP converts the TEXT value to NTEXT. Similarly, when you declare an argument to be of type TEXT, and an NTEXT value is passed into the program, Oracle OLAP converts the NTEXT value to TEXT. Data can be lost when NTEXT is converted to TEXT.

dimension
The name of a dimension, whose value is contained in the argument. The argument holds a single value of the dimension. Assigning a value that does not currently exist in the dimension causes an error.

VALUESET dim
Indicates that name is a valueset. The keyword dim specifies the dimension for which the valueset holds values. Argument valuesets can be used within the program in the same way you would use a valueset in the analytic workspace.

#### Usage Notes

The Life Span of an Argument

An argument exists only while the program in which it is declared is running. When the program terminates, the argument ceases to exist and its value is lost. Therefore, an argument is not an analytic workspace object.

A program can terminate when a RETURN or SIGNAL statement, or at the last line of the program executes. When the program calls a subprogram, the original program is temporarily suspended and the argument still exists when the subprogram ends and control returns to the original program. A program that calls itself recursively has separate arguments for each running copy of the program.

Declaring Arguments that Are Passed Into a Program

When declaring arguments that are passed into a program special considerations apply.

Arguments Passed by Value

Arguments are passed into a program by value. Consequently, the called program is given only the value of an argument, without access to any analytic workspace object to which it might be related. Therefore, you can change an argument value within the called program without affecting any value outside the program. You can think of an argument variable or valueset as a conveniently initialized local variable or local valueset.

Argument Processing for a Function

When a program is invoked either with a CALL statement or as a function, the following two-step process occurs:

1.  The specified data types are established. Argument expressions specified by the calling program are evaluated left to right, and their data types are identified. An expression representing a dimension value can be a text (`TEXT` or `ID`), numeric (`INTEGER`, `DECIMAL`, and so on), or RELATION value. An error in one argument expression stops the process.

2.  Each specified data type is matched with the declared data type. Argument expressions are matched positionally with the declared arguments. The first argument expression is matched with the first declared argument, the second argument expression with the second argument, and so on. Each expression is converted in turn to the declared data type of the declared argument.

When an argument is declared as a dimension value, the matching value passed from the calling program can be `TEXT` or `ID` (representing a value of the specified dimension), numeric (representing a logical dimension position), or RELATION (representing a physical dimension position). The RELATION method is the way Oracle OLAP passes along dimension values that are the result of evaluating a dimension name or relation name used as the matching value. When the matching value is a noninteger numeric value (for example, `DECIMAL`), it is rounded to the nearest `INTEGER` value to represent a logical dimension position.

When an argument is declared as something other than a dimension value, and the matching value from the calling program is a RELATION value, an error occurs. When you want to pass a RELATION value and receive it as a `TEXT` argument, use CONVERT to convert the value in the program's argument list.

When an argument is declared as a valueset of a dimension, only the name of a valueset of that dimension is accepted as an argument.

When an error occurs in either the first or second step, the program is not executed.

Argument Processing for a Command

When a program is invoked as a standalone command with its arguments not enclosed by parentheses, the arguments are matched positionally with the declared arguments. The called program can reference the specified arguments either as declared arguments or through the ARG (n), ARGS, and ARGFR (n) functions. In this situation, the arguments are passed as text strings, not by value.

Extra Arguments

When the calling program specifies more arguments than there are declarations in the called program, the extra arguments are ignored. When the calling program specifies fewer arguments than there are declarations in the called program, the extra arguments are given `NA` values.

Argument Name that Duplicate the Names of Analytic Workspace Objects

Ordinarily, when you give an argument the same name as an analytic workspace object, the argument (not the analytic workspace object) is referenced within the program. Exceptions to this rule occur only when the statement in which the reference is made requires an analytic workspace object as an argument.

#### Examples

In the `custom.rpt` program, you could use the following statements to produce a report of this expression.

    ARGUMENT rptexp TEXT
    REPORT &rptexp

For an example of using ampersand substitution to pass multiple dimension values, see [Example 10-18](olap-dml-commands-h-z.md).

Example 9-44 Passing an Argument to a User-Defined Function

Sometimes verifying user input to the GET function can become complicated. The usual method involves a line of code such as the following one.

    SHOW GET(INT VERIFY VALUE GT 0 AND VALUE LT 100 -
       IFNOT 'The value must be between 1 and 100')

You can create a user-defined function to make the GET expression simpler. For example, the following program can be used as a function to check for values between `0` and `100`.

    DEFINE verit PROGRAM BOOLEAN
    PROGRAM
      ARGUMENT uservalue INT
      TRAP ON haderror NOPRINT
      IF uservalue GT 100
         THEN SIGNAL toobig 'The value must be 100 or smaller.'
      ELSE IF uservalue LT 0
         THEN SIGNAL toosmall 'The value must be 0 or greater.'
      RETURN TRUE
    haderror:
      RETURN FALSE
    END

The following GET expression uses the `verit` function.

    SHOW GET(INT VERIFY VERIT(VALUE) IFNOT ERRORTEXT)

Example 9-45 Passing Multiple Arguments

Suppose, in the `product.rpt` program, that you want to supply a second argument that specifies the column width for the data columns in the report. In the `product.rpt` program, you would add a second ARGUMENT statement to declare the `INTEGER` argument to be used in setting the value of the COLWIDTH option.

    ARGUMENT natext TEXT
    ARGUMENT widthamt INTEGER
    NASPELL = natext
    COLWIDTH = widthamt

To specify eight‐character columns, you could run the `product.rpt` program with the following statement.

    CALL product.rpt ('Missing' 8)

When the `product.rpt` program also requires the name of a product as a third argument, then in the `product.rpt` program you would add a third ARGUMENT statement to handle the product argument, and you would set the status of the `product` dimension using this argument.

    ARGUMENT natext TEXT
    ARGUMENT widthamt INTEGER
    ARGUMENT rptprod PRODUCT
    NASPELL = natext
    COLWIDTH = widthamt
    LIMIT product TO rptprod

You can run the `product.rpt` program with the following statement.

    CALL product.rpt ('Missing' 8 'TENTS')

In this example, the third argument is specified in uppercase letters with the assumption that all the dimension values in the analytic workspace are in uppercase letters.

Example 9-46 Using the ARGUMENT Statement

Suppose you are writing a program, called `product.rpt`. The `product.rpt` program produces a report, and you want to supply an argument to the report program that specifies the text that should appear for an NA value in the report. In the `product.rpt` program, you can use the declared argument `natext` in an ARGUMENT statement to set the NASPELL option to the value provided as an argument.

    ARGUMENT natext TEXT
    NASPELL = natext

To specify `Missing` as the text for NA values, you can execute the following statement.

    CALL product.rpt ('Missing')

In this example, literal text enclosed in single quotes provides the value of the text argument. However, any other type of text expression works equally well, as shown in the next example.

    DEFINE natemp VARIABLE TEXT TEMP
    natemp = 'Missing'
    CALL product.rpt (natemp)

Example 9-47 Passing the Text of an Expression

Suppose you have a program named `custom.rpt` that includes a REPORT statement, but you want to be able to use the program to present the values of an expression, such as `sales ‐ expense`, and individual variables.

    custom.rpt 'sales ‐ expense'

Note that you must enclose the expression in single quotation marks. Because the expression contains punctuation (the minus sign), the quotation marks are necessary to indicate that the entire expression is a single argument.

Example 9-48 Passing Workspace Object Names and Keywords

Suppose you design a program called `sales.rpt` that produces a report on a variable that is specified as an argument and sorts the `product` dimension in the order that is specified in another argument. You would run the `sales.rpt` program by executing a statement like the following one.

    sales.rpt units d

In the `sales.rpt` program, you can use the following statements.

    ARGUMENT varname TEXT
    ARGUMENT sortkey TEXT
    SORT product &sortkey &varname
    REPORT &varname

After substituting the arguments, these statements are executed in the `sales.rpt` program.

    SORT product D units
    REPORT units

### 9.18 AW command

The syntax of the AW command varies depending on the task that you want to perform.

- AW ALIASLIST
- AW ATTACH
- AW CREATE
- AW DELETE
- AW DETACH
- AW FREEZE
- AW LIST
- AW PURGE CACHE
- AW ROLLBACK TO FREEZE
- AW SEGMENTSIZE
- AW THAW
- AW TRUNCATE

#### Usage Notes

Triggering Program Execution When an AW Statement Executes

When a program named TRIGGER_AW exists in an analytic workspace, the execution of an AW statement for that workspace automatically executes that program. See "[Trigger Programs](olap-dml-programs.md)" and the "[TRIGGER_AW](olap-dml-programs.md)" program for more information.

When an AW ATTACH statement executes Oracle OLAP checks for other programs as well. See "[Startup Programs](olap-dml-programs.md)" for more information.

Options Related to the AW Statement

"[Analytic Workspace Options](olap-dml-options.md)" lists the options that you might want to reset before you either create or attach an analytic workspace.

EXPRESS Workspace

When your database is installed with the OLAP option, the `EXPRESS` workspace is always attached in read-only mode in your session. It never automatically becomes the current workspace, even when it is the first or only workspace in your workspace list, because it is for internal use by Oracle OLAP. You can make the `EXPRESS` workspace the current workspace by explicitly attaching it, but this is not recommended. You cannot detach the `EXPRESS` workspace.

#### 9.18.1 AW ALIASLIST

The AW ALIASLIST command assigns or deletes one or more workspace alias for the specified attached workspace or, when no workspace is specified, for the current workspace. ALIAS indicates that the alias or aliases should be assigned, and UNALIAS indicates that the alias or aliases should be deleted. All aliases for a given workspace are automatically deleted when you detach an analytic workspace.

##### Syntax

AW ALIASLIST \[workspace\] {ALIAS\|UNALIAS} alias1, alias2, ...

##### Parameters

workspace
The name of the analytic workspace. You can specify either an analytic workspace name or an analytic workspace alias, depending on the keywords you are using.

ALIAS
Assigns one or more workspace alias for the specified attached workspace or, when no workspace is specified, for the current workspace. ALIAS indicates that the alias or aliases should be assigned, and UNALIAS indicates that the alias or aliases should be deleted.

All aliases for a given workspace are automatically deleted when you detach an analytic workspace. Therefore, each time you attach an unattached workspace, you must reassign its aliases.

UNALIAS
Deletes one or more workspace alias for the specified attached workspace or, when no workspace is specified, for the current workspace.

alias1
alias2
The alias name for the analytic workspace. Alias names:

- Can be from 1 - 26 characters in length. All characters must come from the database character set and must be letters, numerals, or underscores.

- Cannot begin with a numeral and cannot be reserved words in the DML. (Use RESERVED to identify reserved words.)

##### Examples

Example 9-49 Assigning an Alias

The following statement assigns `sdemo` as an alias for the `demo` workspace, which was created by a user named `scott`. The full name of the workspace is specified because the current user is not `scott`.

    AW ALIASLIST scott.demo ALIAS sdemo

In the following statement, the user named `scott` assigns `mydemo` as an alias for the same workspace.

    AW ALIASLIST demo ALIAS mydemo

#### 9.18.2 AW ATTACH

The AW ATTACH command attaches an analytic workspace to your session. Oracle OLAP makes the specified workspace the current one. Previously attached workspaces move down in the list of attached workspaces to make room for the new current one at the top of the list. When there is a cached version of the requested analytic workspace then the cached version is moved back to the list of attached workspaces unless, of course, the current version of the analytic workspace is more recent than the cached version.

When you attach multiple workspaces, the code and data in all the attached workspaces are available during your session. The current workspace is first on the workspace list, which Oracle OLAP keeps for your session.

**Note:**

When an AW ATTACH statement executes, it can trigger the execution of several programs. See "[Startup Programs](olap-dml-programs.md)" for more information.

##### Syntax

AW ATTACH workspace  -      \[ONATTACH \[progname\]\|NOONATTACH\] -      \[RO \[THAW\] \] \| RW \| RWX \| MULTI \[THAW\]\] \[WAIT \| NOWAIT\] \] -      \[AUTOGO \[progname\]\|NOAUTOGO\] -      \[AFTER workspace\|BEFORE workspace\|LAST\|FIRST\] -      \[PASSWORD password\]

##### Parameters

workspace
The name of the analytic workspace. When you use the ATTACH keyword to attach an analytic workspace that is not already attached, you must specify the workspace name. Again this is because no alias has been assigned using AW ALIAS LIST. However, when you use the ATTACH keyword on an already attached workspace (for example, to change its position in the workspace list), you can assign an alias using AW ALIAS LIST and then use that assigned alias.

ONATTACH \[progname\]
(Default) When you do not specify progname, the ONATTACH clause automatically runs a program named ONATTACH if one exists in the attached workspace. You can get the same results by not specifying NOONATTACH.

NOONATTACH
Specifying NOONATTACH indicates that when a program named `ONATTACH` exists in the workspace, Oracle OLAP should not execute that program.

AUTOGO \[progname\]
(Default) When you do not specify progname, the AUTOGO clause automatically runs a program named AUTOGO if one exists in the attached workspace. You can get the same results by not specifying NOAUTOGO.

When you do specify progname, the AUTOGO clause automatically runs the specified program in the attached program.

NOAUTOGO
Specifying NOAUTOGO indicates that when a program named `AUTOGO` exists in the workspace, Oracle OLAP should not execute that program.

RO
(Default) Specifies that the workspace is attached in read-only access mode. Users can make private changes to the data in the workspace to perform what-if analysis but cannot commit any of these changes.

An analytic workspace that is attached read-only can be accessed simultaneously by several sessions. The read-only attach mode is compatible with the read/write and multiwriter access mode. A user can attach an analytic workspace in read-only mode when other users have the workspace attached in either read/write and multiwriter access mode. Likewise, a user cannot attach an analytic workspace in read/write exclusive mode when another user has it attached in read-only mode. When you attach an analytic workspace with read-only access, Oracle OLAP executes a program called [PERMIT_READ](olap-dml-programs.md), when it finds one in the workspace.

THAW
Specifies that Oracle OLAP attach the current view of an analytic workspace that was frozen using an AW FREEZE command without the NOTHAW keyword.

RW
Specifies that the workspace is attached in read/write access mode. Only one user can have an analytic workspace open in read/write at a time. The user has to commit either all or none of the changes made to the workspace.

An analytic workspace that is attached read/write non-exclusive can be accessed simultaneously by several sessions. The read/write non-exclusive attach mode is only compatible with the read-only access mode. A user can attach an analytic workspace in read/write mode when other users have the workspace attached in read-only mode; however, a user cannot attach an analytic workspace in read/write mode when another user has it attached in any other mode. Likewise, a user cannot attach an analytic workspace in any mode other than read-only when another user has it attached in read/write non-exclusive mode. When you attach an analytic workspace with read/write access, Oracle OLAP executes a program called [PERMIT_WRITE](olap-dml-programs.md), when it finds one in the workspace.

RWX
Specifies that the workspace is attached in read/write exclusive access mode. Only one user can have an analytic workspace open in read/write exclusive at a time. The user has to commit either all or none of the changes made to the workspace.

An analytic workspace that is attached read/write exclusive cannot be accessed by any other sessions.  The read/write exclusive attach mode is not compatible with any other access modes. A user cannot attach an analytic workspace in read/write exclusive mode when another user has it attached in any mode. Likewise, a user cannot attach an analytic workspace in any other mode when another user has it attached in read/write exclusive mode. When you attach an analytic workspace with read/write access, Oracle OLAP executes a program called [PERMIT_WRITE](olap-dml-programs.md), when it finds one in the workspace.

MULTI
Specifies that the workspace is attached in multiwriter access mode. An analytic workspace that is attached in multiwriter mode can be accessed simultaneously by several sessions. In multiwriter mode, users can simultaneously modify the same analytic workspace in a controlled manner by specifying the attachment mode (read-only or read/write) for individual variables, relations, valuesets, and dimensions.

**See Also:**

"Managing Analytic Workspaces Attached in Multiwriter Mode" 

The multiwriter attach mode is only compatible with read-only and multiwriter modes. A user cannot attach an analytic workspace in multiwriter mode when another user has it attached in read/write or exclusive modes. Likewise, a user cannot attach an analytic workspace in read/write or exclusive mode when another user has it attached in multiwriter mode.

WAIT
NOWAIT
Specifies whether Oracle OLAP waits for an analytic workspace to become available for access when you request access to an analytic workspace that is being used with read/write exclusive access or when you request read/write access to an analytic workspace that is being used with read/write non-exclusive access. NOWAIT (the default) causes Oracle OLAP to produce an error message indicating that the workspace is unavailable. When you specify WAIT, Oracle OLAP waits for the workspace to become available for access. The number of seconds that Oracle OLAP waits for access depends on the value of the Oracle OLAP AWWAITTIME option.

FIRST
(Default) Makes the workspace you are attaching the current workspace in the workspace list.

LAST
Puts the workspace after the current workspace in the workspace list and before the `EXPRESS` workspace. When there are other workspaces attached before the `EXPRESS` workspace, the specified workspace is attached after them. When there are no workspaces before the `EXPRESS` workspace, LAST makes the specified workspace the current one. LAST ignores any workspaces after the `EXPRESS` workspace.

AFTER workspace
BEFORE workspace
Let you specify the position in the workspace list of the newly attached workspace relative to an analytic workspace that is attached. Use AFTER, rather than LAST, to attach an analytic workspace after the `EXPRESS` workspace. When specifying BEFORE puts the workspace first, the workspace becomes the current one.

The order of the workspace list determines the order in which workspaces are searched when Oracle OLAP looks for programs or objects named in programs.

PASSWORD password
Specifies a password to be checked in a startup program to give or deny access to the workspace being attached. See "[Startup Programs](olap-dml-programs.md)".

##### Usage Notes

Using ATTACH on an Already-Attached Workspace

Reattaching an attached workspace with an AW ATTACH workspace statement does not cause Oracle OLAP to bring a new copy of the workspace into working memory. Instead, Oracle OLAP takes the following actions:

1.  Makes the workspace the current workspace.

2.  Runs an Autogo program, when you specify the AUTOGO keyword

However, when you have made any changes to data during the session, they are not discarded when you reattach an active workspace. Furthermore, current aliases for the workspace are not changed.

Managing Analytic Workspaces Attached in Multiwriter Mode

You use the following commands to manage objects in multiwriter mode:

- ACQUIRE -- Acquires and (optionally) resynchronizes the specified objects so that their changes can be updated and committed.

- [RELEASE](olap-dml-commands-h-z.md) -- Changes the access mode of the specified variables, relations, valuesets, or dimensions from read/write (acquired) access to read-only access.

- [RESYNC](olap-dml-commands-h-z.md) -- Drops private changes for the specified read-only objects and retrieves the data from the latest visible generations.

- [REVERT](olap-dml-commands-h-z.md)-- Drops all changes made to the specified objects since they were last updated, resynchronized (using a RESYNC statement), or acquired using ACQUIRE with the RESYNC phrase, or since the analytic workspace was attached.

The following considerations apply:

- Only one user can acquire an object in read/write mode at a time. You can first acquire an object in read-only mode, and then, assuming another user has not also acquired it in read-only mode, you can acquire it in read/write mode without releasing it first. However, once another user has acquired an object in read-only mode, you cannot acquire the same object in read/write mode until the other user releases the object. When a specified object has been acquired by another user or when your read-only generation for a specified object is not the latest generation for the object, an acquire fails.

- You must resynchronize all variables, valuesets, and relations that share a composite dimension at the same time.

- When resynchronizing objects, keep in mind the logical relationship of different objects to avoid losing the logical consistency of the data by promoting some objects, but not others to a new generation.

- Objects that share a composite dimension can be resynchronized separately when all such objects that are not being resynchronized are either unchanged or acquired.

- You cannot update a variable if any of its dimensions have been acquired and modified.

- You must acquire a dimension before you maintain it.

- If you release a dimension, then an automatic revert occurs.

- Releasing objects that have been updated does not allow others to acquire the object until you commit or roll back the transaction. It may still be useful to release an object that has been updated before a commit when one wants to make further what-if changes and later update all acquired variables

- Reverting a dimension after adding dimension values is not recommended because it can result in suboptimal space allocation for variables dimensioned by that dimension

- If an acquired variable is dimension by an acquired dimension that has been maintained then you cannot update that variable until after you update or release the dimension.

- You cannot delete dimension values.

Attaching a Frozen Analytic Workspace

Once an analytic workspace is frozen, attaching an analytic workspace in RO and MULTI attaches the frozen view of the workspace unless you specify the THAW keyword to request that the current view be attached. (When you attach in RW or RW, you always get the latest generation.)

When you attach the current view, the state of the analytic workspace may not necessarily be consistent if there is a multi-step build with intermediate commits. For example, assume that there is an analytic workspace that has two variables: actual and `budget`. Assume also that you have populated `actual` and then issued UPDATE and COMMIT commands. At this point in time, there is data only in actual.

When you are attaching a frozen analytic workspace in read multi mode, you can use the multi-writer commands ([RESYNC](olap-dml-commands-h-z.md) and ACQUIRE) to retrieve up-to-date versions of the data whether or not you have specified AW FREEZE with the NOTHAW keyword.

Conflicts between Workspace Names and Aliases

You cannot attach an analytic workspace that is in your schema and whose name is the same as an assigned alias. Similarly, you cannot assign an alias that duplicates the name of an attached workspace that is in your schema. Furthermore, you cannot assign the same alias to two attached workspaces.

In an AW DELETE statement, when you specify an analytic workspace name (for an analytic workspace that is not attached) and the name is the same as an assigned alias, Oracle OLAP interprets the name as an alias and reports an error.

##### Examples

Example 9-50 Startup Programs

Assume that you have created an analytic workspace named `awtest` that contains five programs named `PERMIT_READ,` `PERMIT_WRITE`, `ONATTACH`, `MYATTACH`, and `AUTOGO` that have the following definitions.

    DEFINE PERMIT_READ PROGRAM BOOLEAN
    PROGRAM
    SHOW 'permit_read program executing'
    AW LIST
    RETURN YES
    END

    DEFINE PERMIT_WRITE PROGRAM BOOLEAN
    PROGRAM
    SHOW 'permit_write program executing'
    AW LIST
    RETURN YES
    END

    DEFINE ONATTACH PROGRAM BOOLEAN
    PROGRAM
    SHOW 'onattach program executing'
    AW LIST
    RETURN YES
    END

    DEFINE MYATTACH PROGRAM BOOLEAN
    PROGRAM
    SHOW 'myattach program executing'
    AW LIST
    RETURN YES
    END

    DEFINE AUTOGO PROGRAM
    PROGRAM
    SHOW 'autogo program executing'
    AW LIST
    END



The programs that execute when you attach `awtest` vary depending on the attachment mode and keywords in the AW ATTACH statement:

- When you attach `awtest` in read/write mode using the following statements.

      AW DETACH awtest
      AW ATTACH awtest RW

  First the `PERMIT_WRITE` program executes, and then the `ONATTACH` program executes.

- When you attach `awtest` in read-only mode using the following statements.

      AW DETACH axuserwtest
      AW ATTACH awtest NOONATTACH RO

  Only the `PERMIT_READ` program executes.

- When you attach `awtest` in read-only mode using the following statements.

      AW DETACH awtest
      AW ATTACH awtest RO

  First the `PERMIT_READ` program executes, and then the `ONATTACH` program executes.

- When you attach `awtest` in read-only mode using the following statements.

      AW DETACH awtest
      AW ATTACH awtest ONATTACH myattach RO

  First the `PERMIT_READ` program executes, and then the `MYATTACH` program executes.

- When you attach `awtest` in multi mode using the following statements.

      AW DETACH awtest
      AW ATTACH awtest MULTI

  First the `PERMIT_WRITE` program executes, and then the `ONATTACH` program executes.

- When you attach `awtest` in read-only mode using the following statements.

      AW DETACH awtest
      AW ATTACH awtest AUTOGO

  First the `PERMIT_WRITE` program executes. Secondly, the `ONATTACH` program executes. Finally, the `AUTOGO` program executes.

Example 9-51 Attaching an Analytic Workspace Using an ONATTACH Program

Suppose you have two workspaces of sales data, one for `expenses` and one for `revenue`. You have a third workspace called `analysis` contains programs to analyze the data. Your `analysis` workspace has the following `ONATTACH` program to attach the other two.

    DEFINE onattach PROGRAM
    PROGRAM
    AW ATTACH expenses RW AFTER analysis 
    AW ATTACH revenues RW AFTER analysis 
    END

To run the `ONATTACH` program, attach the `analysis` workspace with the following statement.

    AW ATTACH analysis 

When you issue an AW LIST statement, you can see from the following output, that all three of your analytic workspaces are attached.

    ANALYSIS  R/W CHANGED   XUSER.ANALYSIS
    REVENUE   R/W UNCHANGED XUSER.REVENUES
    EXPENSES  R/W UNCHANGED XUSER.EXPENSES
    EXPRESS   R/O UNCHANGED SYS.EXPRESS

#### 9.18.3 AW CREATE

The AW CREATE command creates a new workspace and make it the current workspace in your session.

Oracle OLAP automatically executes a COMMIT as part of its procedure for creating an analytic workspace. Previously attached workspaces move down in the list of attached workspaces to make room for the new one at the top of the list.

Also, if the current analytic workspace is creating a different analytic workspace and the current workspace contains a program named TRIGGER_AW, then the TRIGGER_AW program executes.

**Note:**

Before you can create an analytic workspace you need the appropriate SQL GRANT privileges as outlined in "[Privileges Needed to Create and Delete Analytic Workspaces](olap-dml-basic-concepts.md)".

##### Syntax

AW CREATE workspace \[position\] \[UNPARTITIONED\|PARTITIONS n\] -      \[TABLESPACE tblspname \[SEGMENTSIZE n \[K, M, or G\]\]\]

where `position` specifies the workspace's position in the workspace list and is one of the following values. (`FIRST` is the default.)

- `AFTER` `workspace`
- `BEFORE` `workspace`
- `LAST`
- `FIRST`

##### Parameters

workspace
The name of the analytic workspace. Workspace names:

- Can be from 1 - 26 characters in length. All characters must come from the database character set and must be letters, numerals, or underscores.

- Cannot begin with a numeral and cannot be reserved words in the DML. (Use RESERVED to identify reserved words.)

FIRST
(Default) Makes the workspace you are attaching the current workspace.

LAST
Puts the workspace after the current workspace and before the `EXPRESS` workspace. When there are other workspaces attached before the `EXPRESS` workspace, the specified workspace is attached after them. When there are no workspaces before the `EXPRESS` workspace, LAST makes the specified workspace the current one. LAST ignores any workspaces after the `EXPRESS` workspace.

AFTER
BEFORE
Specify the position of the newly attached workspace relative to an analytic workspace that is already attached. Use AFTER, rather than LAST, to attach an analytic workspace after the `EXPRESS` workspace. When specifying BEFORE puts the workspace first, the workspace becomes the current one.

The order of the workspace list determines the order in which workspaces are searched when Oracle OLAP looks for programs or objects named in programs.

UNPARTITIONED
Specifies that the relational table that is the analytic workspace is not a partitioned table.

PARTITIONS n
Specifies that the relational table that is the analytic workspace is a hash partitioned table with n partitions. Specifying a value of 0 (zero) for n is the same as specifying UNPARTITIONED. The default value of n is 8.

TABLESPACE  tblspname
Specifies the name of an Oracle Database tablespace in which the analytic workspace is created.

**Tip:**

Oracle suggests that you use the TABLESPACE argument to create your workspace in a tablespace that has been prepared for this purpose. Ask your DBA which tablespace use.

SEGMENTSIZE n \[K, M, or G\]
With the CREATE keyword, this argument sets the maximum size of each segment for the workspace being created. When you do not specify `K`, `M`, or `G`, the value you specify for n is interpreted as bytes. When you specify `K`, `M`, or `G` after the value n, the value is interpreted as kilobytes, megabytes, or gigabytes, respectively.

##### Usage Notes

Analytic Workspace Permissions

You can add security to analytic workspaces at several levels:

- At the relational table level using SQL `GRANT` statements

- At the analytic workspace level and workspace object level using different attachment modes and startup programs. See the AW ATTACH command and "[Startup Programs](olap-dml-programs.md)".

##### Examples

Example 9-52 Creating and Starting an analytic workspace

You can use the AW command with the CREATE keyword to create and start a new workspace.

    AW CREATE mywork

#### 9.18.4 AW DELETE

The AW DELETE command deletes a detached analytic workspace from the database. It is important to note that Oracle OLAP automatically executes a COMMIT as part of its procedure for deleting an analytic workspace. The DELETE keyword executes successfully only when no user has the workspace attached.

**Note:**

If the current analytic workspace is deleting a different analytic workspace and the current workspace contains a program named TRIGGER_AW, then the TRIGGER_AW program executes.

**See Also:**

AW DETACH, AW TRUNCATE

##### Syntax

AW DELETE workspace

##### Parameters

workspace
The name of the analytic workspace. You must specify the name; you cannot specify an alias.

##### Usage Notes

Deleting an Unattached Workspace

When you attempt to delete an unattached workspace and the name is the same as an assigned alias, Oracle OLAP interprets the name as an alias and reports an error.

##### Examples

Example 9-53 Deleting an analytic workspace

You can use the AW command with the DELETE keyword to delete an analytic workspace.

    AW DELETE mywork

#### 9.18.5 AW DETACH

The AW DETACH command removes an analytic workspace from the workspace list. When you remove the first workspace, the second workspace becomes the current workspace (unless it is the `EXPRESS` workspace). When you detach an analytic workspace, changes that were made before an UPDATE was issued remain in the database and become permanent with the next COMMIT. When changes were made after the UPDATE was issued, they are discarded.

**Note:**

When a program named TRIGGER_AW exists in the analytic workspace, the execution of an AW DETACH statement automatically executes that program.

##### Syntax

AW DETACH \[CACHE\|NOCACHE\] workspace

##### Parameters

CACHE
Specifies that the analytic workspace is cached if there have been no changes to it since it was attached. (Default)

NOCACHE
Specifies that the analytic workspace is not cached even if there have been no changes to it since it was attached.

**Note:**

You must specify NOCACHE when you detach an analytic workspace if you want Oracle OLAP to execute any Permission, OnAttach, or Autogo programs the next time you attach the workspace in the same session.

workspace
The name of the analytic workspace. You can specify either an analytic workspace name or an analytic workspace alias, depending on the keywords you are using.

##### Usage Notes

Determining if an Analytic Workspace Has Changed

The following statements indicate if an analytic workspace has been changed while it was attached:

- [AW function](olap-dml-functions-a-k.md) with the CHANGED keyword

- AW LIST shows the analytic workspace as unattached.

Cache Size

By default the list of cached analytic workspaces is two. In other words, by default only two analytic workspaces can be on the cached at one time and as new workspaces are added to the cache list, earlier workspaces are removed. For example, assume that you have detached two analytic workspaces in the following order: 1) `mywk1`, 2) `mywk2`. Now you issue an AW DETACH CACHE command for `mywk3`. Oracle OLAP removes `mywk1` from the cache and the cache list and caches `mywk3` adding it to the cache list after `mywk2`.

**Note:**

Under severe memory contention, Oracle OLAP may release memory by emptying the cache.

You can change the size of the cache by using the event number 37372 where level is the number of analytic workspaces to retain. Specify a level of 1024 to disable the cache entirely. Not determined for beta: Is this information valid to regular developers?

Programs Executed When an Analytic Workspace is Detached

When an analytic workspace is detached, the following programs may execute:

- If that analytic workspace being detached contains a program named ONDETACH, the ONDETACH program executes.

- If the current analytic workspace is detaching a different analytic workspace and the current workspace contains a program named TRIGGER_AW, then the TRIGGER_AW program executes.

##### Examples

Example 9-54 Detaching an analytic workspace

You can use the AW command with the DETACH keyword to detach an analytic workspace.

    AW DETACH expense 

#### 9.18.6 AW FREEZE

The AW FREEZE command commits the current transaction (if any) and sets a flag that specifies that the analytic workspace is the default attach version of the workspace. Later, when a request is made to attach the workspace in read only or read multi mode, Oracle OLAP attaches this flagged generation of the analytic workspace.

**Note:**

You must be attached to the analytic workspace in a write mode to execute this command.

##### Syntax

AW FREEZE \[NOTHAW\]

##### Parameters

NOTHAW
Specifies that you cannot specify the THAW keyword with AW ATTACH when you attach the workspace at a later time.

**Note:**

Once an analytic workspace is frozen, attaching an analytic workspace in read only or read multi mode attaches the analytic workspace as of the frozen view unless you specify the THAW keyword with the AW ATTACH command.

##### Usage Notes

Freezing an Analytic Workspace

Keep the following points in mind when freezing an analytic workspace:

- Only one generation of an analytic workspace can be frozen at a time

- You cannot refreeze a currently frozen analytic workspace without first thawing it using the AW THAW command.

#### 9.18.7 AW LIST

The AW LIST command sends to the current outfile a list of the active workspaces, along with their update status.

##### Syntax

AW LIST

##### Usage Notes

Output Produced by AW LIST

The first workspace in the list is the current workspace, unless you do not have a current workspace. The meaning of the update status, CHANGED or UNCHANGED, depends on whether the workspace is attached with read/write or read-only access and whether or not the workspace is being shared with other users. The update status displayed by AW LIST is as follows:

- An unshared workspace in read/write mode -- The update status is CHANGED when you have made changes since attaching the workspace or since your last update.

- An unshared workspace in read-only mode -- The status is always UNCHANGED because you cannot update it.

- A shared or unshared workspace in read/write mode -- The status is CHANGED when you have made changes since attaching the workspace or since your last update.

- A shared workspace in read-only mode -- The status is CHANGED when another user has updated it since you accessed it. To access the new objects or data, you must detach and reattach the workspace after the other user commits his or her changes. If you keep the workspace attached, then your view of the workspace remains unchanged.

Current Workspace

The name of the current workspace is first on the workspace list and is the name returned by the AW(NAME) function. (See the [AW function](olap-dml-functions-a-k.md) for details.) The NAME dimension includes only the objects in the current workspace. Programs such as AWDESCRIBE and LISTBY list only objects in the current workspace. When an analytic workspace is active but not current, you can change and update its data, edit and run its programs, and modify its objects.

##### Examples

Assume that you have just connected to Oracle OLAP using the OLAP Worksheet. You issue an `AW LIST` statement that returns a value showing that the only attached analytic workspace is `EXPRESS`.

    AW LIST
    EXPRESS   R/O UNCHANGED SYS.EXPRESS


Now you create an analytic workspace and issue another `AW LIST` statement. You can see that both the `EXPRESS` analytic workspace and the newly created analytic workspace are attached.

    AW CREATE myaw
    AW LIST
    MYAW      R/W UNCHANGED MYNAME.MYAW
    EXPRESS   R/O UNCHANGED SYS.EXPRESS


#### 9.18.8 AW PURGE CACHE

The AW PURGE CACHE command detaches any analytic workspaces that are currently in the cache.

##### Syntax

AW PURGE CACHE

#### 9.18.9 AW ROLLBACK TO FREEZE

The AW ROLLBACK TO FREEZE makes current the version of the analytic workspace that was created by the last AW FREEZE command.

##### Syntax

AW ROLLBACK TO FREEZE

#### 9.18.10 AW SEGMENTSIZE

The AW SEGMENTSIZE command sets up an analytic workspace for multiple segments.

##### Syntax

AW SEGMENTSIZE n \[K, M, or G\] \[workspace\]

##### Parameters

workspace
The name of the analytic workspace. You can specify either an analytic workspace name or an analytic workspace alias, depending on the keywords you are using.

SEGMENTSIZE n \[K, M, or G\] \[workspace\]
Sets the maximum size of each segment for a specified workspace or, when no workspace is specified, for the current workspace.

When the current workspace already has several segments, setting SEGMENTSIZE affects only the most recent one and has no effect on previous ones. Previous segments may have various sizes, determined by the SEGMENTSIZE setting at the time each one was created. When you do not specify `K`, `M`, or `G`, the value you specify for n is interpreted as bytes. When you specify `K`, `M`, or `G` after the value n, the value is interpreted as kilobytes, megabytes, or gigabytes, respectively.

#### 9.18.11 AW THAW

The AW THAW command commits the current transaction (if any) and undoes a previous AW FREEZE command.

##### Syntax

AW THAW

#### 9.18.12 AW TRUNCATE

Deletes all of the objects and data from an existing analytic workspace. Oracle also deallocates all of the table space used by the analytic workspace.Removing data using AW TRUNCATE can be more efficient and less "destructive" than deleting an analytic workspace using AW DELETE. For example, when you remove data using AW TRUNCATE, all of the object privileges that were previously granted remain.

For more information on truncating a table, see [TRUNCATE TABLE](../sqlrf/TRUNCATE-TABLE.md) in Oracle Database SQL Language Reference.

**Note:**

Before you can truncate an analytic workspace in a schema that you do not own, you need the appropriate SQL GRANT privilege as outlined in "[Privileges Needed to Create and Delete Analytic Workspaces](olap-dml-basic-concepts.md)".

##### Syntax

AW TRUNCATE workspace

##### Parameters

workspace
The name of the analytic workspace. You must specify the name; you cannot specify an alias.

##### Examples

Example 9-55 Removing all Data from an analytic workspace

You can use the AW command with the TRUNCATE keyword to delete all of the objects and data in an analytic workspace.

    AW TRUNCATE mywork

### 9.19 AWDESCRIBE

The AWDESCRIBE program sends information about the current analytic workspace to the current outfile. After a summary page, it provides a report in two parts:

- An alphabetic list of analytic workspace objects showing name, type, and description.

- A list of object definitions by object type. Each definition includes the information you would see when you used the DESCRIBE statement. It also includes a "Referenced By" list, which indicates any programs or other compilable objects that call or access the object. In addition, compilable objects have a "References To" list, indicating the analytic workspace objects that they call or access.

#### Syntax

AWDESCRIBE

#### Usage Notes

Information in Referenced By List

The AWDESCRIBE command does not provide information in the "Referenced By" and "References To" list for implicit references. For example: When a program contains a LIMIT command to limit a dimension by a related dimension, AWDESCRIBE does not list the relation for those dimensions in the "References To" list for that program.

#### Examples

Example 9-56 Describing an analytic workspace

The following example shows a portion of the output of AWDESCRIBE for an analytic workspace named `demo`.

                                 DEMO Workspace Listing
                                 =====================
     
    Last updated:  25Jun96     Time: 09:46:50
    Print date:    27Aug96     Time: 10:30:11
    DEMO contains:
       11 DIMENSIONS
       19 VARIABLES
        1 PROGRAM
        4 RELATIONS
        2 VALUESETS
     
    This report is in two parts: 
        - Object Listing: An alphabetic list of workspace objects,
          beginning on the next page. 
        - Object Descriptions: Detailed descriptions of all workspace
          objects, sorted by object type and alphabetically by name.
     
    Object List                                                      Page 2
    Workspace: DEMO         Updated: 25Jun96   At: 09:46:50           ACTUAL
     
    NAME              TYPE       DESCRIPTION
    ____              ____       ___________
    ACTUAL            VARIABLE   Actual $ Financials
    ADVERTISING       VARIABLE   Total Advertising Dollars
    BUDGET            VARIABLE   Budgeted $ Financials
    CHOICE            DIMENSION  List of choices
    CHOICEDESC        VARIABLE   Description line for the choices
    DEMOVER           VARIABLE   DEMO Workspace Version
    DISTRICT          DIMENSION
    DIVISION          DIMENSION  Division
    DIVISION.PRODUCT  RELATION   DIVISION for each PRODUCT
    EXPENSE           VARIABLE   Total Production & Distribution Cost
    FCST              VARIABLE   Forecasted $ Financials
    INDUSTRY.SALES    VARIABLE   Total Industry Sales Revenue
    LINE              DIMENSION  Lineitem
    MARKET            DIMENSION  Geography Dim with Embedded Totals
    MARKET.MARKET     RELATION   Self-relation for the Market Dim
    MARKETLEVEL       DIMENSION  Geography Level
    MLV.MARKET        RELATION
    MONTH             DIMENSION
    NAME.LINE         VARIABLE   Lineitem Names for Reporting
    NAME.PRODUCT      VARIABLE   Product Names for Reporting Purposes
    NATIONAL.SALES    VARIABLE   Projected Total U.S. Dollar Sales
    NOT.IMPLEMENTED   PROGRAM
    PRICE             VARIABLE   Wholesale Unit Selling Price
    PRODUCT           DIMENSION  Sporting Goods Products
    PRODUCT.MEMO      VARIABLE   Product Analysis Memo
    PRODUCTSET        VALUESET   Valueset for Sporting Goods Products
    QUARTER           DIMENSION
    QUARTERSET        VALUESET
    REGION            DIMENSION  Sales Region
    REGION.DISTRICT   RELATION   REGION for each DISTRICT
    SALES             VARIABLE   Sales Revenue
    SALES.FORECAST    VARIABLE   Forecasted Unit Sales
    SALES.PLAN        VARIABLE   Budgeted Sales Revenue
    SHARE             VARIABLE   Market Share (Based on Dollar Sales)
    UNITS             VARIABLE   Actual Unit Shipments
    UNITS.M           VARIABLE
    YEAR              DIMENSION
     
    Description of DIMENSIONS                                        Page 3
    Workspace: DEMO         Updated: 25Jun96   At: 09:46:50           CHOICE
     
    DEFINE CHOICE DIMENSION TEXT
    LD List of choices
         Referenced By:
             NONE
     
    DEFINE DISTRICT DIMENSION TEXT
         Referenced By:
             NONE
     
    DEFINE DIVISION DIMENSION TEXT
    LD Division 
         Referenced By:
             NONE
    ...

### 9.20 BLANK

The BLANK command sends one or more blank lines to the current outfile. BLANK is typically used only in OLAP DML programs. For example, in a report program, BLANK is commonly used to insert blank lines that separate headings from data or that separate groups of data from one another.

#### Syntax

BLANK \[n\]

#### Parameters

n
An `INTEGER` expression with a value of `0` (zero) or higher, that specifies how many blank lines should be inserted. When you omit n, Oracle OLAP inserts one blank line. `NA` produces an error.

#### Examples

Example 9-57 Inserting Blank Lines

This example inserts two blank lines between the title of a report and the column headings. The following lines are from a report program.

    LSIZE = 50
    HEADING WIDTH LSIZE CENTER 'Quarterly Sales Report'
    BLANK 2
    ROW WIDTH 20 'Unit Sales' ACROSS month -
       'Jan96' TO 'Mar96': month

The program produces the following output.

                  Quarterly Sales Report
     
    Unit Sales           Jan96    Feb96    Mar96

### 9.21 BREAK

Within SWITCH command, FOR, or WHILE statements in an OLAP DML program, the BREAK command transfers program control from within a SWITCH, FOR, or WHILE statement to the statement immediately following the DOEND associated with SWITCH, FOR, or WHILE.

#### Syntax

BREAK

#### Usage Notes

TEMPSTAT Statement and BREAK Statement

Within a FOR loop of a program, when a DO ... DOEND phrase follows TEMPSTAT, status is restored when the DOEND, BREAK, or GOTO is encountered.

#### Examples

Example 9-58 Using BREAK with SWITCH

The following lines from a program include a SWITCH command with two case labels. The last statement under each case label is BREAK, which ensures that execution does not continue from one set of case statements to the next. Each BREAK statement transfers control to the statement that follows DOEND.

    SWITCH userchoice
        DESCRIPTION 'MARKET REPORT\NFINANCE REPORT\NNO REPORT')
        DO
             CASE 'market':
                ...            
                BREAK
             CASE 'finance':
                ...  
                BREAK
             DEFAULT:
                ...
                BREAK
        DOEND
    cleanup:
          ...

### 9.22 CALL

The CALL command invokes a program. When the program has arguments, which are always enclosed in parentheses, it passes these arguments to the called program.

#### Syntax

CALL program-name \[(arg ...)\]

#### Parameters

program-name
The name of the program to be called.

arg
One or more optional arguments expected by the called program. These arguments can be declared in the called program with ARGUMENT, or they can be referenced in the program with ARG. If the program uses the ARGUMENT statement, when you use CALL to invoke the program, specify the arguments so that they match the positions of the arguments declared in the called program.

#### Usage Notes

Dimension Arguments

When you pass a dimension value or dimension name as an argument, you must enclose the exact text value in single quotes, for example, `'Jan96'`. When the program arguments are declared with the ARGUMENT statement, you can pass a text expression that evaluates to a text value.

Program Return Values

When you use CALL to invoke a program that returns a value, the return value is discarded. A program can use the CALLTYPE function to determine whether it was invoked as a function, as a command, or by using CALL.

ARGUMENT Command or ARG Function

The called program can process arguments using either the ARGUMENT statement or the ARG function. In a program that has been invoked with CALL or as a function, the ARGS and ARGFR functions always return `NA`.

When CALL invokes a program whose arguments are not declared with the ARGUMENT statement, the arguments passed can be referenced with the ARG function. However, the ARG function is a text function and, consequently, interprets all arguments passed as text values. When you want to pass NTEXT arguments, be sure to declare them using ARGUMENT instead of using ARG. With ARG, NTEXT arguments are converted to TEXT, and this can result in data loss when the NTEXT values cannot be represented in the database character set.

ARGUMENT Statement Processing

When a program is invoked with CALL or as a function, the following two-step process occurs. When an error occurs in either step, the program is not executed.

1.  The specified data types are established. Argument expressions specified by the calling program are evaluated left to right, and their data types are identified. Any expression representing a dimension value can be a text (`TEXT` or `ID`), numeric (`INTEGER`, `DECIMAL`, and so on), or RELATION value. An error in one argument expression stops the process.

2.  Each specified data type is matched with the declared data type. Argument expressions are matched by position with the declared arguments in the called program. The first argument expression is matched with the first declared argument variable, the second argument expression is matched with the second declared argument variable, and so on. Each expression is converted in turn to the declared data type of the argument variable.

When an argument variable is declared as a dimension value, the matching value passed from the calling program can be `TEXT` or `ID` (representing a value of the specified dimension), numeric (representing a logical dimension position), or RELATION (representing a physical dimension position).When the matching value is a non-integer numeric value (for example, `DECIMAL`), it is rounded to the nearest `INTEGER` to represent a logical dimension position.

When an argument variable is declared as something other than a dimension value, and the matching value from the calling program is a RELATION value, an error occurs. When you want to pass a RELATION value that is received as a `TEXT` argument, use the CONVERT function to convert the value in the program's argument list.

ARGUMENT Statement with Extra Arguments

When the calling program specifies more arguments than are declared in the called program, the extra arguments are ignored. When the calling program specifies fewer arguments than are declared in the called program, the extra argument variables are given `NA` values.

ARGUMENT Statement Passing by Value

When arguments are declared with the ARGUMENT statement, they are passed by value to a program. Consequently, the called program is given only the value of an argument, without access to any analytic workspace object to which it might be related. However, when the name of an analytic workspace object is specified as an argument enclosed in single quotes, the value of the analytic workspace object is not passed. Instead, the name of the object is passed as a text string. See Example 9-59.

#### Examples

(Compare the `roundup.f` program with the `roundup.p` program. `roundup.f` returns a value; it does not produce a report.)

Example 9-59 Calling a Program or Function

This example illustrates how two programs, `roundup.p` and `roundup.f`, are used in different ways to evaluate data and produce output.

The `roundup.p` program accepts the name of a decimal variable as a text string and produces a report of that variable's values rounded to the nearest `INTEGER`. The `roundup.f` program also accepts the name of a decimal variable. However, instead of passing the name of the variable as a text string, the variable's value is passed as an argument. `roundup.f` does not produce a report. Instead, it returns each of the values of the decimal variable, rounded to the nearest `INTEGER`.

The `roundup.p` program is invoked using CALL and includes a REPORT statement. In contrast, `roundup.f` is invoked as a user-defined function whose return value is then used as an argument to a REPORT statement.

The `roundup.p` program uses ARGUMENT to declare a text argument. When invoked, `roundup.p` uses the argument as the name of a decimal variable. The calling program passes the name of the variable to give the called program access to all the values of the dimensioned variable. When the calling program passed the variable itself, instead of its name, only a single value would have been accessible to the called program. This program does not return a value; it produces a report.

    DEFINE roundup.p PROGRAM INTEGER
    PROGRAM
    ARGUMENT varname TEXT
    Report Down Line Across Month: Heading 'VARNAME' -
       IF INTPART(&varname) EQ &varname -
       THEN &varname ELSE INTPART(&varname) + 1 
    END

The following statements

    LIMIT division TO 1
    LIMIT month TO 1 TO 4
    DECIMALS = 0
    CALL roundup.p('actual')

produce the following report.

    DIVISION: CAMPING
                   ----------------- Varname------------------
                   -------------------MONTH-------------------
    LINE             Jan95      Feb95      Mar95      Apr95
    -------------- ---------- ---------- ---------- ----------
    revenue           533,363    572,797    707,198    968,858
    cogs              360,811    400,902    478,982    641,716
    gross.margin      172,553    171,895    228,217    327,143
    marketing          37,370     38,867     51,224     69,439
    selling            89,008     86,458    102,233    139,567
    r.d                24,308     23,400     39,943     57,186
    opr.income         21,868     23,171     34,819     60,952
    taxes              15,971     16,320     23,030     27,584
    net.income          5,898      6,851     11,789     33,368

Another way to produce the same report is to write a user-defined function that can be used as an argument to the REPORT statement as illustrated in the following program named `roundup.f`.

    DEFINE roundup.f PROGRAM INTEGER
    PROGRAM
    ARGUMENT realval DECIMAL
    IF realval EQ INTPART(realval)
    THEN RETURN INTPART(realval)
    ELSE RETURN INTPART(realval) + 1
    END

The following statements

    LIMIT division TO 1
    LIMIT month TO 1 TO 4
    DECIMALS = 0
    REPORT DOWN line ACROSS month: roundup.f(actual)

produce the following report.

    DIVISION: CAMPING
                   ------------ ROUNDUP.F(ACTUAL)-------------
                   -------------------MONTH-------------------
    LINE             Jan95      Feb95      Mar95      Apr95
    -------------- ---------- ---------- ---------- ----------
    revenue           533,363    572,797    707,198    968,858
    cogs              360,811    400,902    478,982    641,716
    gross.margin      172,553    171,895    228,217    327,143
    marketing          37,370     38,867     51,224     69,439
    selling            89,008     86,458    102,233    139,567
    r.d                24,308     23,400     39,943     57,186
    opr.income         21,868     23,171     34,819     60,952
    taxes              15,971     16,320     23,030     27,584
    net.income          5,898      6,851     11,789     33,368

### 9.23 CDA

With the CDA command, you can identify or change the current directory object for your session.

With an established current directory object, you can specify a file identifier in a DML file access statement without including the name of the directory object. Some examples of file access statements are FILECOPY, FILEMOVE, FILEDELETE, EXPORT, and IMPORT.

#### Syntax

CDA \[directory-alias\]

#### Parameters

directory-alias
A text expression that specifies the directory object that you want to be the current one for your session.

When you do not specify this argument, CDA sends the name of the current directory object to the current outfile. When there is no current directory object, the statement reports that fact.

#### Usage Notes

Specifying a File Identifier with an Established Current Directory Object

The following statement moves the file `log.txt` from your session's current directory object to file `oldlog.txt` in a directory object called `backup`.

    FILECOPY 'log.txt' 'backup/oldlog.txt'

Setting Up a Directory Object

A database administrator must set up a directory object and give you access to it.

#### Examples

Example 9-60 Specifying the Current Directory Object

The following statement identifies `mydir` as the current directory object.

    CDA 'mydir'

Example 9-61 Obtaining the Current Directory Object

The following statement causes the current directory object to be sent to the current outfile.

    CDA

This statement produces the following output.

    The current directory is MYDIR.

### 9.24 CHGDFN

The CHGDFN command enables you to change certain aspects of the definitions of analytic workspace objects.

Before you can use CHGDFN to change the definition of an object, use CONSIDER to make that object definition the current definition.

**Note:**

You cannot use CHGDFN to change definitions of objects that are in an analytic workspace that is attached in multiwriter mode.

#### Syntax

CHGDFN desired-change

where `desired-change `is one of the following:

     varname SEGWIDTH length dim...      partitioned-varname {DROP \| ADD } (partition-instance...)      partition-template {DEFINE \| DELETE \[CLEAR\] } (partition-instance...)      partition-template RENAME PARTITION old-name new-name      {conjoint \| composite}  {HASH \| BTREE \| NOHASH}        concat BASE ADD dimensionlist      conjoint COMPOSITE      composite DIMENSION      dimension NTEXT \| TEXT \| NUMBER \[p, s\]      dwmqy-dimname { {BEGINNING \| ENDING} phase \| {EARLIER \| LATER} n}      concat \[NOT\] UNIQUE      varname {ADD \|DROP} AGGCOUNT      varname \[DROP\] NULLTRACKING

#### Parameters

varname
The name of the variable whose segment size you want to set.

SEGWIDTH
Indicates explicit sizing of a variable's segments. See "Understanding Variable Segments" for more information.

partitioned-varname
Specifies the name of a partitioned variable whose partitions you want to modify.

DROP partition-instance
ADD partition-instance
Removes or adds the specified partitions from the partitioned variable. See the DEFINE VARIABLE command for a complete description of the `partition-instance` argument.

DEFINE partition
DELETE \[CLEAR\] partition-instance
Removes or adds the specified partitions from the partition template object. See the DEFINE PARTITION TEMPLATE command for a complete description of the `partition-instance` argument.

When you include the optional CLEAR keyword, Oracle OLAP also drops any corresponding partitions in the variables that are partitioned using the partition template object. In other words, including CLEAR is the same as issuing an additional CHGDFN statements to DROP the partition from the variables partitioned by it.

RENAME PARTITION old-name new-name
Renames the specified partitions in the partition template object.

BASE ADD dimensionlist
Adds the dimension or dimensions specified by dimensionlist to the base dimensions of the concat dimension.When you add one or more dimensions as base dimensions of a concat, then Oracle OLAP appends the dimensions to the existing list of base dimensions of the concat. Objects that are dimensioned by the concat, or objects that are dimensioned by a concat that has the altered concat as a base dimension, gain additional `NA` values. You cannot add as a base dimension a dimension that is already a component of the concat dimension.

length-dim...
Segment width is specified as the maximum number of values in each segment for each dimension or composite in the variable's dimension list. The first length-dim is the number of values for the dimension or composite in the first position of the dimension list in the variable's definition (that is, the fastest-varying dimension or composite), the second length-dim is the number of values for the dimension or composite in the second position in the dimension list, and so on.

conjoint
composite
For the index syntax, the name of the conjoint dimension or composite whose index algorithm you want to change. For the conjoint-to-composite syntax, the name of the conjoint dimension you want to change to a composite. For the composite-to-dim syntax, the name of the composite you want to change to a conjoint dimension. You cannot change a conjoint dimension to a composite when the conjoint is a dimension of a formula.

BTREE
BTREE64
HASH
NOHASH
Indicates the index algorithm used to load and access values of your conjoint dimension or composite without losing data in objects defined with the conjoint or composite. A composite cannot be changed to NOHASH. A conjoint can be changed to NOHASH only when it was originally defined as HASH. See "Changing the Index Algorithm of a Conjoint from BTREE to NOHASH".

HASH, NOHASH, and BTREE are different index algorithms used to load and access the values of a conjoint dimension or composite. (BTREE64 can only be used with composites.) HASH is the default for conjoints. The default for composites is determined by the SPARSEINDEX option, which has a default value of BTREE. The index algorithm affects the performance of loading and accessing large conjoints or composites. Performance varies depending on your system configuration, the organization of your data, and the design of your application.

- BTREE is a standard indexing method that is recommended for composites and conjoint dimensions. Use BTREE as the default unless you are an advanced user and have a special need that requires HASH or NOHASH. BTREE tends to group similar values, which results in better locality of access.

- BTREE 64 can only be used with composites. It specifies the creation of a highly-scalable b-tree index to relate composite values to base dimension values. For a variable that is dimensioned by a BTREE64 composite, like a BTREE composite, Oracle OLAP creates array elements (that is, variable cells) only for those dimension values that are stored in the tuples of the composite; it does not create a cell for every value in the base dimensions. However, unlike a BTREE composite, a BTREE64 composite supports b-trees greater than 2 gigabytes

- HASH is a standard indexing method that can be used for composites or conjoint dimensions that have only 2 or 3 base dimensions. One advantage to using HASH is that it results in a small amount of code. However, HASH is generally not recommended. Using HASH results in a very large index table, which can be too large to fit into memory.

- NOHASH can only be used with conjoint dimensions. It can be advantageous to use NOHASH when there is little memory available and the conjoint dimension has only 2 or 3 base dimensions.Also, you can use NOHASH when you load a very large initial amount of data. When you use NOHASH, the data is loaded in a way that makes it easy to access that data after it has been loaded. Once the data is loaded, change the definition of the conjoint dimension back to BTREE to ensure good performance. Otherwise, performance is likely to suffer, especially when the conjoint dimension has 4 or more base dimensions. See "Changing the Index Algorithm of a Conjoint from BTREE to NOHASH".

**Tip:**

You can do performance testing to determine which algorithm provides the best performance for your situation. For example, suppose a data load executes well at first, then slows down drastically. Use CHGDFN to change the index algorithm from BTREE to NOHASH. Try the data load again to determine whether or not using NOHASH improves performance. You can then use CHGDFN to change the index algorithm back to BTREE. Note, however, that changing the index algorithm of a large conjoint dimension or composite from one algorithm type to another may take a considerable amount of time and that the CHGDFN command cannot be interrupted.

COMPOSITE
Indicates changing a conjoint dimension into a named composite. There are some restrictions on changing conjoint dimensions to composites; when a conjoint has the NOHASH index algorithm or when it has permissions, you cannot change it to a composite.

DIMENSION
Indicates changing a named composite into a conjoint dimension.

composite_dimension
The name of a composite that has a composite as a base dimension.

**Note:**

In Oracle Database 11g, you cannot define a nested composite. Consequently, you only use the UNNEST keyword with nested composites that were defined in an earlier release and then imported into Oracle Database 11g.

dimension
The name of a TEXT, NTEXT or NUMBER dimension

NTEXT
Specifies that the statement changes the data type of a TEXT dimension to NTEXT

TEXT
Specifies that the statement changes the data type of a NTEXT dimension to TEXT

NUMBER \[p, s\]
Specifies that the statement changes the data type of a TEXT, NTEXT, or NUMBER dimension to NUMBER with the precision specified by p and the scale specified by s.

dwmqy-dimname
Specifies or changes the phase of a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR.

BEGINNING phase
ENDING phase
Specifies the beginning phase or ending phase of a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. You must specify the phase as a date, giving the month, day, and year, enclosed in single quotes, using any of the input styles that are valid for variable values with a data type of DATE. When you specify a date with an ambiguous meaning (such as `'03 05 97'`), the date is interpreted according to the current setting of the DATEORDER option. For more information about specifying dates, see the [DATEORDER](olap-dml-options.md) option.

EARLIER n
LATER n
n is an `INTEGER` expression that increments or decrements the period on which the DAY, WEEK, MONTH, QUARTER, or YEAR dimension's phase begins or ends. For example, for a WEEK dimension whose current begin phase is Monday, specify `LATER 2` to change the phase to Wednesday.

\[NOT\] UNIQUE
When you include `NOT`, changes a unique concat dimension to a nonunique concat. When you do not include `NOT`, changes a nonunique concat dimension to a unique concat dimension. See the DEFINE DIMENSION CONCAT command for more information on concat dimensions.

ADD AGGOUNT
Adds an Aggcount variable to the specified variable. See the WITH AGGCOUNT phrase of the DEFINE VARIABLE command for more information about Aggcount variables.

DROP AGGOUNT
Removes an Aggcount variable from the specified variable. See the WITH AGGCOUNT phrase of the DEFINE VARIABLE command for more information about Aggcount variables.

NULLTRACKING
Adds NA2 bits to the specified variable if the variable does not have NA2 bits. For more information on NA2 bits and null tracking, see "NA2 Bits and Null Tracking" .

DROP NULLTRACKING
Removes NA2 bits to the specified variable if the variable has NA2 bits.

#### Usage Notes

Understanding Variable Segments

A segment is contiguous disk space reserved for a portion of the total number of values a variable holds. For example, for a variable dimensioned by `month` with a SEGWIDTH of `150` and `product` with a SEGWIDTH of `90,000`, each segment holds up to 150 x 90,000 values of the variable. The number of segments in a variable affects the performance of data loading and data accessing.

When you do not specify `CHGDFN` `SEGWIDTH`, the default behavior is to assign a segwidth of `0` (zero) on non-composite dimensions and a large value for composites that are not the slowest-varying in the dimension set. This behavior allows new dimension and composite values to be added in most situations without greatly increasing the number of segments and degrading performance.

When you specify SEGWIDTH, you must specify a number, `0` (zero), or nonzero, for every dimension and composite of the variable.

When you set the value of SEGWIDTH for a dimension to 0, Oracle OLAP grows segments in that dimension as needed, minimizing the number of segments but not changing any existing segments. You can always specify `0` (zero for the slowest-varying dimension, because the data for any values that are later added to that dimension is appended to the existing data in the variable's last segment.

The segment size that you specify is used not only for the variable you designate as varname, but also for all other variables and relations that are defined with the same combination of dimensions and composites in the same order. The DEFINE command sets the SEGWIDTH at the time it creates a variable or relation. Changing the SEGWIDTH affects any new variable or relation that you subsequently create. The changed SEGWIDTH setting does not apply to previously existing variables or relations.

The time it takes to do data loads on a variable depends on how many pages are brought into memory and then written back out. This number can be affected by how a variable is divided into segments. Too many segments (thousands to millions) can degrade performance. See "Reducing the Number of Segments".

The number of segments also affects data access. The time it takes to report a variable depends on how many values are brought into memory. You decide how many segments your variable should have based on your data loading and data accessing patterns.

DEFINE provides default segments. In most cases, you can use the default segments so that you do not have to use `CHGDFN SEGWIDTH` to manually control the size of segments. However, you may be able to improve performance by specifying the segment size instead of using the defaults.When you are not sure what your segment size should be, use the maximum anticipated number of values for each dimension or composite as the length arguments to SEGWIDTH. Then only one segment is created for the variable.

Reducing the Number of Segments

You can use OBJ (NUMSEGS) to find out if you have too many segments for objects that have a particular dimension set. When you find that you do, you can reduce the number of segments by following these steps:

1.  Export the variables and relations that use this dimension set to an EIF file.

2.  Execute a MAINTAIN DELETE ALL statement for a dimension in the dimension set.

3.  Optimally, execute a CHGDFN statement for a variable or relation with this dimension set, and increase the value of the length arguments to the SEGWIDTH keyword.

4.  From the EIF file, import all the values you exported in Step 1.

Changing the Index Algorithm of a Conjoint from BTREE to NOHASH

When you must change a conjoint dimension that was originally defined with the BTREE algorithm to a NOHASH conjoint, you can use the following method:

1.  Export the conjoint dimension and all the objects dimensioned by it to an EIF file.

2.  Delete all the objects dimensioned by the conjoint dimension, and then delete the conjoint itself.

3.  Redefine the conjoint as a NOHASH conjoint.

4.  Import the conjoint dimension and the objects dimensioned by it from the EIF file. The NOHASH attribute on the definition at the time of the import causes the conjoint dimension to be read in as a NOHASH conjoint.

Changing an Unnamed Composite to a Named Conjoint Dimension

When you want to change an unnamed composite into a conjoint dimension, you can use a RENAME statement to change the unnamed composite into a named composite, and then use CHGDFN to change the named composite into a conjoint dimension.

#### Examples

For an example of removing null tracking from a variable, see Example 9-104.

Example 9-62 Using CHGDFN SEGWIDTH

Suppose you have a variable called `d.sales` that is dimensioned by `month` and by a composite with the base dimensions `market` and `product`. The definition of `d.sales` looks like the following.

    DEFINE d.sales VARIABLE DECIMAL <month SPARSE<market product>>

Suppose you want to have only one segment in the `d.sales` variable. You estimate that the `month` dimension eventually has 150 values and the composite has 100,000. The following statement creates one segment for the `d.sales` variable.

    CHGDFN d.sales SEGWIDTH 150 100000

However, a better way to specify segment size for `d.sales` is to specify 0 for the slowest-varying dimension.

    CHGDFN d.sales SEGWIDTH 150 0

Suppose you want one segment for a variable defined with a composite and two dimensions. For example, suppose you have a variable called `f.costs` with the following definition.

    DEFINE f.costs VARIABLE DECIMAL <geog SPARSE<product channel> time>

You estimate the `geog` dimension has 100 values and the composite has 300,000. You do not have to estimate the number of values for the `time` dimension, because it is the slowest-varying dimension. The following statement creates one segment for the `f.costs` variable.

    CHGDFN f.costs SEGWIDTH 100 300000 0

Example 9-63 Changing the Phase of a YEAR Dimension

The following statements first create a dimension of type YEAR for a fiscal year, then use CHGDFN to switch to a new time phase for the fiscal year.

    DEFINE fiscal DIMENSION year BEGINNING '06 01 96'
    CHGDFN fiscal BEGINNING '01 01 97'

Example 9-64 Adding a Base Dimension to a Concat Dimension

The following statements create a nonunique concat dimension named `reg.dist.ccdim` that has the `region` and `district` dimensions as its base dimensions and report the values of the concat.

    DEFINE reg.dist.ccdim DIMENSION CONCAT(region district)
    REPORT W 22 reg.dist.ccdim

The preceding statement produces the following output.

    REG.DIST.CCDIM
    --------------------
    <region: East>
    <region: Central>
    <region: West>
    <district: Boston>
    <district: Atlanta>
    <district: Chicago>
    <district: Dallas>
    <district: Denver>
    <district: Seattle>

The following statements add the `store_id` dimension as a base to the concat dimension and then report the values of the concat again.

    CHGDFN reg.dist.ccd BASE ADD store_id
    REPORT W 22 reg.dist.ccd

The preceding statement produces the following output.

    REG.DIST.CCD
    ----------------------
    <region: East>
    <region: Central>
    <region: West>
    <district: Boston>
    ...
    <district: Seattle>
    <store_id: 10>
    <store_id: 20>
    <store_id: 30>
    <store_id: 100>
    ...
    <store_id: 500>
    <store_id: 510>

### 9.25 CLEAR

The CLEAR command deletes the data that you specify for one or more variables.

#### Syntax

CLEAR \[STATUS \| {ALL \[CACHE\]}\] \[VALUES \| {aggdata \[USING aggmapname\]}\] -        FROM {varname \[ ( PARTITION partition-name ) \] } \[, ... \]

where `aggdata` is one or more of the following keywords that identifies the type of aggregated data that you want deleted from the variable.

- `AGGREGATES`
- `LEAVES `
- `PRECOMPUTES `
- `NONPRECOMPUTES`

#### Parameters

STATUS
Specifies that only the data that is currently in status is taken into consideration. (Default)

**Tip:**

When clearing a compressed composite, do not execute a CLEAR when only some values are in status.

ALL
Specifies that the command consider all of a variable's data regardless of the current status. Required when you specify either the CACHE or AGGREGATES keywords.

CACHE
Empties the session cache. When you specify this keyword, you must also specify the ALL keyword.

VALUES
(Default) Deletes all of a variable's stored data and replaces each deleted data value with an `NA` value.

AGGREGATES
Deletes the data in all cells populated by the execution of an AGGREGATE command or an AGGREGATE function. When you specify this keyword, you must also specify the ALL keyword.

PRECOMPUTES
For all variables except those dimensioned by a compressed composite, deletes any data that was calculated when an AGGREGATE command executed and replaces that data with `NA` values.

NONPRECOMPUTES
Deletes any data that was calculated on the fly when an AGGREGATE function executed and replaces that data with `NA` values.

LEAVES
Deletes the detail-level data, meaning, the "leaf" data.

**Note:**

You cannot specify this keyword for a variable dimension by a compressed composite.

varname
The name of a variable from which data is deleted.

aggmapname
The name of the aggmap that should be used.

You must include this phrase to clear a variable that is not a compressed composite or that does not have an \$AGGMAP property. You do not have to specify this phrase to clear:

- A variable that is dimensioned by a compressed composite. By default, CLEAR uses the structure of the compressed composite to clear the variable.

- A variable that has an \$AGGMAP property when you want CLEAR to use the aggmap specified by that property. If you do not specify a USING phrase for a variable that has an \$AGGMAP property, then CLEAR uses the aggmap specified by that property.

When you include this phrase for a dimensioned aggmap, the dimensionality of every variable included in the CLEAR command must be identical to the dimensionality of the aggmap. In other words, every variable definition must have the same dimensions in the same order as those in the definition of the aggmap.

PARTITION partition_name
For a partitioned variable, specifies the name of a partition from which you want to clear data.

**Note:**

Clearing only a single partition of a compressed composite is resource intensive and time consuming as the variable is decompressed during the process.

#### Examples

Example 9-65 Clearing a Variable's Data

The CLEAR command gives you an easy way to delete all of a variable's stored data. Suppose you have defined a `sales` variable and loaded data into it. You then find out that much of this data has changed. It is more efficient to clear the `sales` variable and reload all of the data than it would be to change the existing data. You can do so with the following statement.

    CLEAR ALL FROM sales

In this example, the VALUES keyword is assumed by default. Therefore, all of the `sales` data is deleted and replaced with `NA` values.

Example 9-66 Clearing Aggregated Data

Suppose you have aggregated data for your `sales` and `units` variable, and you have specified that all other data should be calculated on the fly.

The `sales` and `units` variables are defined with the same dimensions in the same order: `time`, `product`, and `geography`. Therefore, they have been aggregated with the `sales.agg` aggmap, which has the following definition.

    DEFINE sales.agg AGGMAP <time, product, geography>

The `sales.agg` aggmap has the following contents.

    RELATION time.r PRECOMPUTES (time ne 'YEAR99')
    RELATION product.r PRECOMPUTES (product ne 'ALL')
    RELATION geography.r

After aggregating both `sales` and `units`, you learn that there are certain geographic regions that none of your users access. Because `geography` is the slowest-varying dimension, you can probably reduce the number of pages needed to store data by deleting data for the geographic regions that no one needs which can reduce the size of your analytic workspace and possibly improve performance.

1.  Set the status for each dimension. The only geographic regions that users need are New England, Europe, and Australasia. The following statements put all time periods and all products for every geographic region in the current status, except for the geographic regions that users need. In other words, the following statements put all of the data that users do not have to access in status.

        LIMIT time TO ALL
        LIMIT product TO ALL
        LIMIT geography COMPLEMENT 'NewEngland' 'Europe' 'Australasia'

2.  Use the following statement to delete the unneeded data.

        CLEAR STATUS PRECOMPUTES FROM sales units USING sales.agg

Example 9-67 Clearing Cached Data

Data is cached when an aggmap specifies calculation on the fly and contains a CACHE SESSION statement.

For example, suppose the `sales.agg` aggmap has the following contents.

    RELATION time.r PRECOMPUTES (time ne 'YEAR99')
    RELATION product.r PRECOMPUTES (product ne 'ALL')
    RELATION geography.r
    CACHE SESSION

Note that the `sales.agg` contains a CACHE SESSION command. Consequently, Oracle OLAP calculates some data at the time a user requests it, and then stores it in the session cache. To clear this data from the `sales` variable, use the following statement.

    CLEAR ALL CACHE FROM sales

### 9.26 COMMIT

The COMMIT command executes a SQL `COMMIT` statement. When you want changes that you have made in an analytic workspace to be committed when you execute the COMMIT command, then you must first update the workspace using an UPDATE statement. UPDATE moves changes from a temporary work area to the database table in which the workspace is stored. Changes that have not been moved to the table are not committed. When you do not use UPDATE and COMMIT statements, changes made to an analytic workspace during your session are discarded when you end your Oracle session.

When you execute a SQL `COMMIT` statement in your database session, all changes made in your session (including all updated changes in workspaces that you have attached with read/write access) are committed. All committed changes are visible to other users who subsequently attach the workspace. However, another user's UPDATE and COMMIT statements do not affect your view of an already attached workspace.

**Note:**

Many users execute DML statements using SQL\*Plus® or OLAP Worksheet. Both of these tools automatically execute a COMMIT statement when you end your session

#### Syntax

COMMIT

#### Examples

Example 9-68 Saving All Changes to an Analytic Workspace

The following statements permanently save all analytic workspace changes made so far in your session. The COMMIT command also saves database changes made in your session outside Oracle OLAP.

    UPDATE
    COMMIT

### 9.27 COMPILE

The COMPILE command generates compiled code for a compilable object, such as a program, formula, model, or aggmap without running it and saves the compiled code in the analytic workspace. During compilation, COMPILE checks for format errors, so you can use COMPILE to help debug your code before running it. COMPILE records the errors in the current outfile.

However, you are not required to use the COMPILE command before running a compilable object. When you do not use COMPILE, Oracle OLAP automatically compiles a compilable object the first time you run it after entering or changing its contents. This automatic compilation is unnoticeable except for a slight delay while it is happening. Use the OBJ function with the ISCOMPILED keyword to obtain information about the compilation status of a compilable object.

Whether you compile an object explicitly with COMPILE or automatically through running it, the code executes faster whenever you subsequently run the object during the same session, because the code is already compiled. When you update and commit your analytic workspace, the compiled code is saved as part of your analytic workspace and can be used in later sessions. The code thus executes faster the first time it is run in each later session.

Using COMPILE to compile code without running a compilable object is especially useful when you are writing code that is part of a read-only analytic workspace (that is, an analytic workspace that people can use but not update).

**Note:**

"[Compiling Programs](olap-dml-programs.md)", "[Compiling Models](formulas-models-aggregations-and-allocations.md)", and "[Compiling Aggregation Specifications](formulas-models-aggregations-and-allocations.md)"

#### Syntax

COMPILE object-name

#### Parameters

object-name
The name of a compilable object that you want to compile.

#### Usage Notes

Compilation Options

Several options effect compilation. These options are listed in "[Compilation Options](olap-dml-options.md)". By setting one or more of these options you can suppress error messages that appear at compilation time or replace occurrences of `THIS_AW` with a specified value.

Deleted Objects

When you delete or rename an object in your analytic workspace, Oracle OLAP automatically invalidates the compiled code for every statement in a program and every formula and model that depends on that object. When you try to execute code that refers to the deleted or renamed object, Oracle OLAP tries to compile the code again. Unless you have defined a new object with the same name, you receive an error message now.

When you run a program that contains invalidated code, it is compiled and executed one statement at a time. To save compiled code for the entire program, use the COMPILE command to explicitly compile it.

Multiple Errors in a Line

When a single statement has multiple errors, COMPILE finds only the first error. However, COMPILE continues checking for format errors in subsequent statements.

Declarative Errors

COMPILE handles declarative errors differently in programs and models:

- When a program has a declarative error (for example, when a VARIABLE or ARG statement follows executable code), COMPILE signals a trappable error

- When a model has a declarative model (for example, when a model statement has a DIMENSION statement following an assignment statement) COMPILE does not signal a trappable error. Instead, the model is not executable.

See the [TRAP](olap-dml-commands-h-z.md) command for more information on trapping error.s

Advantages of Compiling

Explicit compilation using the COMPILE command offers several advantages over automatic compilation:

- For any compilable object, COMPILE generates compiled code without executing the code in the object.

- In a program or model, automatic compilation diagnoses an error only in the first statement that contains an error. It then displays the error message and halts the execution of a program or the analysis of a model. So each time a program or model is automatically compiled, only a single error message is displayed. In contrast, COMPILE checks every statement in a program or model for correct format, and generates multiple error messages, one for each statement that contains an error. (In programs, some types of statements cannot be compiled, so they are exceptions. See "Errors COMPILE Does Not Catch".) Because COMPILE shows you every statement that contains at least one error, this minimizes the number of times you must edit the code to correct all errors.

- For a model, you may want to examine the results of the compilation or set options for handling simultaneous equations before you run the model.

Errors COMPILE Does Not Catch

Because the COMPILE command does not actually execute code, it can compile code that, for reasons unrelated to format errors, might not be successfully executed when the object were actually run. In a program, for example, you can compile the following statement, even though 'joplin' is not a district.

    LIMIT district TO 'joplin'

Although the statement compiles successfully, you get an error message at run time.

Statements Not Compiled

In programs, certain statements cannot be compiled at all, and are therefore interpreted each time they are executed. These include statements that contain ampersand substitution, statements involving analytic workspace operations, and any statement that calls a program as a command. (Statements that call a program as a function or with the CALL command are compiled.)

PRGTRACE Option

You can use the PRGTRACE option to check which statements in a program have been compiled. When you set PRGTRACE to `YES` and run a program, each statement is recorded in the current outfile before it is executed. A compiled statement is identified with an equal sign.

    (PRG= program-name) statement

An uncompiled statement is identified with a colon.

    (PRG: program-name) statement

Multiple Analytic Workspaces

When you compile a compilable object that uses objects in another analytic workspace, the second analytic workspace must be attached to your current Oracle OLAP session. You can then run the compilable object with that analytic workspace or another analytic workspace with objects of the same name and type attached. Oracle OLAP checks that the objects have the same name, type (variable, dimension, and so on), data type (`INTEGER`, `TEXT`, and so on), and dimensions as the objects used to compile the compilable object.

When you have multiple active analytic workspaces, do not have objects of the same name in both analytic workspaces. For example, when you have an analytic workspace of programs and two analytic workspaces with data about the products Tea and Coffee, both product analytic workspaces can have a MONTH dimension and the programs can refer to MONTH. However, during your session, attach only one product analytic workspace at a time so that there is only one MONTH dimension.

Memory Use

In order for code to compile, all variables referenced in a program (except for variables in lines containing ampersand substitution) must be loaded into memory. Consequently, Oracle OLAP reads the definition of every variable you use and stores it in a portion of available memory that is dedicated for storing object definitions. When the compilation tries to bind a large variable, this may use a large amount of memory and create a large `EXPTEMP` file. When the compilation tries to bind a large number of large variables, it may fail and Oracle OLAP records an error message such as 'Insufficient Main Memory'. See the [LOAD](olap-dml-commands-h-z.md) command for more information about loading an object's definition into memory.

#### Examples

Example 9-69 Compiling a Program

The following is an example of a `COMPILE` command that compiles the `myprog` program.

    COMPILE myprog

Suppose you misspell the dimension `month` in a LIMIT command in the `myprog` program.

    LIMIT motnh TO LAST 6

When the `COMPILE` command encounters this statement, it produces the following message.

    ERROR: (MXMSERR00) Analytic workspace object MOTNH does not exist.
    In DEMO!MYPROG PROGRAM:
    limit month to last 6

You can edit the program to correct the error and then try to compile it again.

Example 9-70 Finding Program Errors

This example shows a program called `salesrpt` that contains two errors.

    DEFINE salesrpt PROGRAM
    PROGRAM
    ROW WIDTH 80 CENTER Monthly Report
    BLANK 2
    ROWW 'Total Sales' TOTAL(sales)
    END

You can compile the program with the following statement.

    COMPILE salesrpt

Oracle OLAP identifies both errors and records the following messages.

    ERROR: You provided extra input starting at 'REPORT'.
    In SALESRPT PROGRAM:
    ROW WIDTH 80 CENTER Monthly Report
    ERROR: ROWW is not a command.
    In SALESRPT PROGRAM:
    roww 'Total Sales' TOTAL(sales)

You can now edit the program to correct these errors, enclosing `'Monthly Report`' in single quotes and correcting the spelling of `ROWW`. Then you can compile the program again, and save the compiled code as part of your analytic workspace.

### 9.28 CONSIDER

The CONSIDER command identifies a definition as the current definition which enables you to add a description, value name format, formula, program, model, permission, or property to the definition with an LD, VNF, EQ, PROGRAM, MODEL, PERMIT, or PROPERTY statement.

#### Syntax

CONSIDER name

#### Parameters

name
The name of a definition in the current workspace or in an attached workspace.

#### Usage Notes

Replacing a Definition Component

When you use an LD, VNF, EQ, PROGRAM, MODEL, or PERMIT statement to add a component to the current definition, any existing value for that component is discarded and replaced by the new value you specify. For the PROPERTY statement, the value is replaced only when you specify a new value for an existing property name. Definitions can have multiple properties.

Unsuccessful CONSIDER Statements

When the CONSIDER command you issue is unsuccessful, subsequent LD, VNF, EQ, PROGRAM, MODEL, PERMIT, or PROPERTY statements produce an error.

Implicit CONSIDER Statements

The DEFINE, COPYDFN, and RENAME commands automatically issue an implicit CONSIDER command.

#### Examples

Example 9-71 Adding a Description to an Analytic Workspace Object

This example adds a description (LD) to the definition for `district`. To add the LD, you must first use CONSIDER to make `district` the current definition. The statements

    CONSIDER district
    LD Sales Districts
    DESCRIBE district

produce the following definition.

    DEFINE district DIMENSION TEXT
    LD Sales Districts

### 9.29 CONTEXT command

The CONTEXT command lets you create and use a context during your Oracle OLAP session. A context is a means of preserving object values. After you create a context, you can save the current status of dimensions and the values of options, single-cell variables, valuesets, and single-cell relations in the context. You can then restore some or all of the object values from the context. A context exists only for the duration of an Oracle OLAP session. It is not an analytic workspace object and therefore cannot be saved as part of any analytic workspace. When a context contains saved values for objects in a particular analytic workspace, and you detach that analytic workspace, Oracle OLAP removes those objects from the context. That context retains any saved values for Oracle OLAP options and objects from other analytic workspaces that are still attached.

You can use the CONTEXT function to obtain information about a context.

The CONTEXT command and function provide an alternative to the PUSH and POP statements. With contexts, you can access and update the saved object values, whereas PUSH and POP simply allow you to save and restore values.

#### Syntax

CONTEXT context-name \[ CREATE \|  APPLY \| DISCARD \| {SAVE \|DROP\|RESTORE} objects\]

#### Parameters

context-name
A text expression that contains the name of the context.

CREATE
Creates a context with the name specified by context-name, which must be unique.

SAVE
Stores the values of the objects specified in objects in the context. You may save the values of single-cell variables and relations in a context. You cannot use the CONTEXT command to save the values of dimensioned variables, dimensioned relations, or the NAME dimension. If you try to save values from these objects, Oracle OLAP produces an error message.

APPLY
Sets the appropriate objects to the values of all corresponding objects saved in the context.

DISCARD
Deletes the context.

SAVE
Stores the values of the objects specified in objects in the context.

DROP
Drops the values of the objects specified in objects from the context.

**Note:**

When you delete an Oracle OLAP object during the session, it is also removed from the context.

RESTORE
Sets whatever objects you specify in objects to the values of the corresponding objects saved in the context.

objects
One or more object names. Each object name must be separated by a space. When you are listing several name(s) that do not fit on a single line, you may use the continuation character to continue the CONTEXT command on additional lines.

#### Usage Notes

Naming Convention

A suggested programming practice is to name the context after the analytic workspace with which it is associated.

#### Examples

Example 9-72 Saving Dimension Status

This example shows how you can use the CONTEXT command to save and restore the status of a dimension. The following statements create a context that includes a subset of the values in the `product` dimension.

    LIMIT product TO 'Tents' 'Canoes'
    CONTEXT 'democontext1' CREATE
    CONTEXT 'democontext1' SAVE product

The following statements limit `product` to all its values and produce a report that lists them all.

    LIMIT product TO ALL
    REPORT product

This is the report.

    PRODUCT
    -----------
    Tents
    Canoes
    Racquets
    Sportswear
    Footwear

The following statements apply the saved context and produce a report that lists only the values included in the context.

    CONTEXT 'democontext1' APPLY
    REPORT product

This is the new report.

    PRODUCT
    -----------
    Tents
    Canoes

### 9.30 CONTINUE

The CONTINUE command transfers program control to the end of a FOR or WHILE loop (just before the DO/DOEND statement), allowing the loop to repeat. You can use CONTINUE only within programs and only with FOR or WHILE.

For more information on controlling program execution, see also "[Program Flow-of-Control](olap-dml-programs.md)".

#### Syntax

CONTINUE

#### Examples

Example 9-73 Skipping Over Code in a FOR Loop

In the following lines from a program, an IF statement is used to test whether total sales for a district exceed 5,000,000. When sales are more this amount, the program goes on to produce a report for that district. However, when a district's sales are less than the amount, the CONTINUE statement is used to transfer control to the end of the FOR loop (just before the DOEND statement). No lines are produced for that district, and the program goes on to test the next district in the status list.

     ...
    FOR district
        DO          
        IF TOTAL(sales, district) LT 5000000
          THEN CONTINUE
         ... "(report statements for districts with total sales above 5,000,000)
        DOEND
     ...

### 9.31 COPYDFN

The COPYDFN program defines a new object in the analytical workspace and uses the same definition as a specified object in the current workspace or in an attached workspace.

COPYDFN copies the DEFINE, LD, and PROPERTY lines for any type of object, and it copies the formula (EQ) of a formula object, and the value name format (VNF) of a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. COPYDFN also copies the text of a program or model. COPYDFN does not copy the PERMIT lines for any object, and it does not copy the compiled code of a formula, program, or model.

#### Syntax

COPYDFN newobject oldobject

#### Parameters

newobject
The name of the new object to define.

oldobject
The name of the object whose definition you want to copy.

#### Examples

Example 9-74 Copying Programs

The following statements use COPYDFN to create a program, called `newprog`, which is a copy of an existing one called `oldprog`. You could then edit `newprog` to create a slightly different program. The `oldprog` program has the following definition.

    DEFINE oldprog PROGRAM
    LD Shows total sales for the top five months from high to low
    PROGRAM
    LIMIT district TO 'BOSTON'
    LIMIT month TO TOP 5 BASEDON TOTAL(sales, month)
    REPORT TOTAL(sales, month)
    END

The statements

    COPYDFN newprog oldprog
    DESCRIBE newprog

produce the following definition for `newprog`.

    DEFINE newprog PROGRAM
    LD Shows total sales for the top five months from high to low
    PROGRAM
    LIMIT district TO 'BOSTON'
    LIMIT month TO TOP 5 BASEDON TOTAL(sales, month)
    REPORT TOTAL(sales, month)
    END

### 9.32 CREATE_LOGICAL_MODEL

The CREATE_LOGICAL_MODEL program creates a new model for an OLAP cube dimension, and adds that definition to the Oracle data dictionary. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL CREATE_LOGICAL_MODEL ( logical_dim, model_name)

#### Parameters

CALL
Because CREATE_LOGICAL_MODEL is an OLAP DML program with arguments, you invoke it using the OLAP DML CALL statement.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"Guidelines for Specifying Values for the Names of Logical OLAP Objects"

model_name
A text expression that is the name that the model will have in the Oracle data dictionary.

### 9.33 DATE_FORMAT

The DATE_FORMAT command assigns a format template to the definition of an object that has a `DATETIME`, `TIMESTAMP`, `TIMESTAMP_TZ`, `TIMESTAMP_LTZ`, `DSINTERVAL`, or `YMINTERVAL` data type.

The datetime format template is a template that describes the format of datetime data stored in a character string. The template does not change the internal representation of the value in the database. When you convert a character string into a date, the template determines how Oracle OLAP interprets the string.

**Note:**

You can only use this statement with objects that have a datetime data type that corresponds to a SQL datetime data type. You cannot use this statement for time dimensions that have a DATE-only data type that is unique to the OLAP DML.

To assign a datetime format template to a definition, the definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

#### Syntax

DATE_FORMAT \[datetime_format_template\]

#### Parameters

datetime_format_template
An expression composed of one or more datetime format elements that specifies the format for entering and displaying the values of the current object. See Table 9-4 for the elements that you can specify in the template. Keep the following points in mind when creating a template:

- The total length of a datetime format template cannot exceed 22 characters

- For input format models, format items cannot appear twice, and format items that represent similar information cannot be combined. For example, you cannot use 'SYYYY' and 'BC' in the same format string.

- Some datetime format elements cannot be used in the `TO_*` datetime functions, as noted in [Table 2-7](data-types-operators-and-expressions.md).

- The following datetime format elements can be used in timestamp and interval format models, but not in the original `DATETIME` format model: `FF`, `TZD`, `TZH,` `TZM`, and `TZR`.

- Many datetime format elements are blank padded to a specific length.

When template is omitted, any existing date format template for the current definition is deleted and the default datetime format template is used. For a discussion of the datetime format template, see "Default Datetime Format Template".

The following table describes the datetime format elements.

Table 9-4 Datetime Format Elements

| Element                                            | Specify in TO\_\* datetime functions? | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:---------------------------------------------------|:--------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-`<br>`/`<br>`,`<br>`.`<br>`;`<br>`:`<br>`"text"` | Yes                                   | Punctuation and quoted text is reproduced in the result.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `AD`<br>`A.D.`                                     | Yes                                   | AD indicator with or without periods.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `AM`<br>`A.M.`                                     | Yes                                   | Meridian indicator with or without periods.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `BC`<br>`B.C.`                                     | Yes                                   | BC indicator with or without periods.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `CC`<br>`SCC`                                      | No                                    | Century.<br>• If the last 2 digits of a 4-digit year are between 01 and 99 (inclusive), then the century is one greater than the first 2 digits of that year.<br>• If the last 2 digits of a 4-digit year are 00, then the century is the same as the first 2 digits of that year.<br>For example, 2002 returns 21; 2000 returns 20.                                                                                                                                                                                                                                                                                                                |
| `D`                                                | Yes                                   | Day of week (1-7).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `DAY`                                              | Yes                                   | Name of day, padded with blanks to display width of the widest name of day in the date language used for this element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `DD`                                               | Yes                                   | Day of month (1-31).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `DDD`                                              | Yes                                   | Day of year (1-366).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `DL`                                               | Yes                                   | Returns a value in the long date format, which is an extension of the Oracle Database `DATETIME` format (the current value of the `NLS_DATE_FORMAT` parameter). Makes the appearance of the date components (day name, month number, and so forth) depend on the `NLS_TERRITORY` and `NLS_LANGUAGE` parameters. For example, in the `AMERICAN_AMERICA` locale, this is equivalent to specifying the format `'fmDay,` `Month` `dd,` `yyyy'`. In the `GERMAN_GERMANY` locale, it is equivalent to specifying the format'`fmDay, dd.` `Month yyyy`'.<br>Restriction: You can specify this format only with the `TS` element, separated by white space. |
| `DS`                                               | Yes                                   | Returns a value in the short date format. Makes the appearance of the date components (day name, month number, and so forth) depend on the `NLS_TERRITORY` and `NLS_LANGUAGE` parameters. For example, in the `AMERICAN_AMERICA` locale, this is equivalent to specifying the format '`MM/DD/RRRR`'. In the `ENGLISH_UNITED_KINGDOM` locale, it is equivalent to specifying the format '`DD/MM/RRRR`'.<br>Restriction: You can specify this format only with the `TS` element, separated by white space.                                                                                                                                            |
| `DY`                                               | Yes                                   | Abbreviated name of day.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `E`                                                | No                                    | Abbreviated era name (Japanese Imperial, ROC Official, and Thai Buddha calendars).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `EE`                                               | No                                    | Full era name (Japanese Imperial, ROC Official, and Thai Buddha calendars).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `FF [1..9]`                                        | Yes                                   | Fractional seconds; no radix character is printed (use the `X` format element to add the radix character). Use the numbers 1 to 9 after `FF` to specify the number of digits in the fractional second portion of the datetime value returned. If you do not specify a digit, then Oracle Database uses the precision specified for the datetime data type or the data type's default precision.<br>Examples: `'HH:MI:SS.FF'`<br>`SELECT TO_CHAR(SYSTIMESTAMP, 'SS.FF3') from dual;`                                                                                                                                                                 |
| `FM`                                               | Yes                                   | Returns a value with no leading or trailing blanks.<br>See Also: ["Format Model Modifiers"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `FX`                                               | Yes                                   | Requires exact matching between the character data and the format model.<br>See Also: ["Format Model Modifiers"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `HH`                                               | Yes                                   | Hour of day (1-12).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `HH12`                                             | No                                    | Hour of day (1-12).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `HH24`                                             | Yes                                   | Hour of day (0-23).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `IW`                                               | No                                    | Week of year (1-52 or 1-53) based on the ISO standard.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `IYY`<br>`IY`<br>`I`                               | No                                    | Last 3, 2, or 1 digit(s) of ISO year.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `IYYY`                                             | No                                    | 4-digit year based on the ISO standard.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `J`                                                | Yes                                   | Julian day; the number of days since January 1, 4712 BC. Number specified with J must be integers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `MI`                                               | Yes                                   | Minute (0-59).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `MM`                                               | Yes                                   | Month (01-12; January = 01).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `MON`                                              | Yes                                   | Abbreviated name of month.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `MONTH`                                            | Yes                                   | Name of month, padded with blanks to display width of the widest name of month in the date language used for this element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `PM`<br>`P.M.`                                     | No                                    | Meridian indicator with or without periods.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `Q`                                                | No                                    | Quarter of year (1, 2, 3, 4; January - March = 1).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `RM`                                               | Yes                                   | Roman numeral month (I-XII; January = I).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `RR`                                               | Yes                                   | Lets you store 20th century dates in the 21st century using only two digits.<br>See Also: ["The RR Datetime Format Element"](../sqlrf/Format-Models.md) in Oracle Database SQL Language Reference                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `RRRR`                                             | Yes                                   | Round year. Accepts either 4-digit or 2-digit input. If 2-digit, provides the same return as `RR`. If you do not want this functionality, then enter the 4-digit year.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `SS`                                               | Yes                                   | Second (0-59).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `SSSSS`                                            | Yes                                   | Seconds past midnight (0-86399).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `TS`                                               | `Yes`                                 | Returns a value in the short time format. Makes the appearance of the time components (hour, minutes, and so forth) depend on the `NLS_TERRITORY` and `NLS_LANGUAGE` initialization parameters.<br>Restriction: You can specify this format only with the `DL` or `DS` element, separated by white space.                                                                                                                                                                                                                                                                                                                                           |
| `TZD `                                             | Yes                                   | Daylight savings information. The `TZD` value is an abbreviated time zone string with daylight savings information. It must correspond with the region specified in `TZR`.<br>Example: `PST` (for US/Pacific standard time); `PDT` (for US/Pacific daylight time).                                                                                                                                                                                                                                                                                                                                                                                  |
| `TZH`                                              | Yes                                   | Time zone hour. (See `TZM` format element.)<br>Example: `'HH:MI:SS.FFTZH:TZM'`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `TZM`                                              | Yes                                   | Time zone minute. (See `TZH` format element.)<br>Example: `'HH:MI:SS.FFTZH:TZM'`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `TZR`                                              | Yes                                   | Time zone region information. The value must be a time zone region supported in the database.<br>Example: US/Pacific                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `WW`                                               | No                                    | Week of year (1-53) where week 1 starts on the first day of the year and continues to the seventh day of the year.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `W`                                                | No                                    | Week of month (1-5) where week 1 starts on the first day of the month and ends on the seventh.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `X`                                                | Yes                                   | Local radix character.<br>Example: `'HH:MI:SSXFF'`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `Y,YYY`                                            | Yes                                   | Year with comma in this position.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `YEAR`<br>`SYEAR`                                  | No                                    | Year, spelled out; `S` prefixes BC dates with a minus sign (-).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `YYYY`<br>`SYYYY`                                  | Yes                                   | 4-digit year; `S` prefixes BC dates with a minus sign.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `YYY`<br>`YY`<br>`Y`                               | Yes                                   | Last 3, 2, or 1 digit(s) of year.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

#### Usage Notes

Default Datetime Format Template

The default datetime format template is specified either explicitly with the initialization parameter `NLS_DATE_FORMAT` or implicitly with the initialization parameter `NLS_TERRITORY`. You can change the default datetime formats for your session with the `ALTER` `SESSION` statement.

ISO Standard Date Format Elements

Oracle calculates the values returned by the datetime format elements IYYY, IYY, IY, I, and IW according to the ISO standard.

For information on the differences between these values and those returned by the datetime format elements YYYY, YYY, YY, Y, and WW, see [Date and Time Formats](../nlspg/overview-of-globalization-support.md) in Oracle Database Globalization Support Guide.

The RR Datetime Format Element

The `RR` datetime format element is similar to the `YY` datetime format element, but it provides additional flexibility for storing date values in other centuries. The `RR` datetime format element lets you store 20th century dates in the 21st century by specifying only the last two digits of the year.

If you use the `TO_DATE` function with the `YY` datetime format element, then the year returned always has the same first 2 digits as the current year. If you use the `RR` datetime format element instead, then the century of the return value varies according to the specified two-digit year and the last two digits of the current year.

That is:

- If the specified two-digit year is 00 to 49, then

  - If the last two digits of the current year are 00 to 49, then the returned year has the same first two digits as the current year.

  - If the last two digits of the current year are 50 to 99, then the first 2 digits of the returned year are 1 greater than the first 2 digits of the current year.

- If the specified two-digit year is 50 to 99, then

  - If the last two digits of the current year are 00 to 49, then the first 2 digits of the returned year are 1 less than the first 2 digits of the current year.

  - If the last two digits of the current year are 50 to 99, then the returned year has the same first two digits as the current year.

Datetime Format Element Suffixes

The following table lists suffixes that can be added to datetime format elements:

Table 9-5 Date Format Element Suffixes

| Suffix       | Meaning                 | Example Element | Example Value |
|:-------------|:------------------------|:----------------|:--------------|
| TH           | Ordinal Number          | `DDTH`          | `4TH`         |
| SP           | Spelled Number          | `DDSP`          | `FOUR`        |
| SPTH or THSP | Spelled, ordinal number | `DDSPTH`        | `FOURTH`      |

Keep the following in mind when using date format element suffixes:

- When you add one of these suffixes to a datetime format element, the return value is always in English.

- Datetime suffixes are valid only to format output. You cannot use them to insert a date into the database.

Datetime Format Elements and Globalization Support

The functionality of some datetime format elements depends on the country and language in which you are using Oracle Database. For example, these datetime format elements return spelled values:

- MONTH

- MON

- DAY

- DY

- BC or AD or B.C. or A.D.

- AM or PM or A.M or P.M.

The language in which these values are returned is specified either explicitly with the initialization parameter `NLS_DATE_LANGUAGE` or implicitly with the initialization parameter `NLS_LANGUAGE`. The values returned by the `YEAR` and `SYEAR` datetime format elements are always in English.

The datetime format element `D` returns the number of the day of the week (1-7). The day of the week that is numbered 1 is specified implicitly by the initialization parameter `NLS_TERRITORY`.

**See Also:**

[Datetime Format Parameters](../nlspg/datetime-data-types-and-time-zone-support.md) for information on globalization support initialization parameters.

Uppercase Letters in Date Format Elements

Capitalization in a spelled-out word, abbreviation, or Roman numeral follows capitalization in the corresponding format element. For example, the datetime format template 'DAY' produces capitalized words like 'MONDAY'; 'Day' produces 'Monday'; and 'day' produces 'monday'.

Punctuation and Character Literals in Datetime Format Templates

You can include these characters in a datetime format template:

- Punctuation such as hyphens, slashes, commas, periods, and colons

- Character literals, enclosed in double quotation marks

These characters appear in the return value in the same location as they appear in the format model.

Oracle returns an error if an alphanumeric character is found in the date string where a punctuation character is found in the format string. For example, the following format string returns an error:

    TO_CHAR (TO_DATE('0297','MM/YY'), 'MM/YY')

#### Examples

Example 9-75 Changing the Datetime Format Template for an Object

Assume that the default datetime format template is `DD_MON_RR` as shown in the following statement.

    SHOW NLS_DATE_FORMAT
    DD-MON-RR

Assume also that you define a variable named `mydatetime` and assign it the value of CURRENT_TIMESTAMP.

    DEFINE mydatetime VARIABLE DATETIME
    mydatetime = CURRENT_TIMESTAMP


When you report on value of `mydatetime`, the following value is displayed. This value has the format determined by the setting NLS_DATETIME FORMAT. It shows only day, month, and year values in the order specified by

    REPORT mydatetime

    MYDATETIME
    -----------
    02-FEB-07


Now you change the date format map for `mydatetime` by issuing the following statements.

    CONSIDER mydatetime
    DATE_FORMAT MON-RRRR-DD-HH24


A display of the value of `mydatetime`, now includes hour as a 24-hour value.

    REPORT mydatetime

    MYDATETIME
    --------------
    FEB-2007-02-10

### 9.34 DBGOUTFILE

The DBGOUTFILE command (abbreviated DOTF) sends debugging information to a file. When you set PRGTRACE and MODTRACE to `YES`, the file produced by DBGOUTFILE interweaves each line of your program, model, or infile with its corresponding output. When you set ECHOPROMPT to `YES`, the debugging file also includes error messages.

#### Syntax

DBGOUTFILE {EOF \| TRACEFILE \| \[APPEND\] file-name \[NOCACHE\]}

#### Parameters

EOF
Closes the current debugging file, and debugging output is no longer sent to a file.

TRACEFILE
Specifies that the debugging output should be directed to the Oracle trace file, which is identified by the TRACEFILEUNIT option.

APPEND
Specifies that the output should be added to the end of an existing file. When you omit this argument and a file exists with the specified name, the new output replaces the current contents of the file.

file-name
A text expression that is the name of the file to which debugging output should be written. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use a CDA statement to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

NOCACHE
Specifies that Oracle OLAP should write to the debugging file each time a line is executed. Without this keyword, Oracle OLAP reduces file I/O activity by saving text and writing it periodically to the file.

The NOCACHE keyword slows performance significantly, but it ensures that the debugging file records every line as soon as it is executed. When you are debugging a program that aborts after a certain line, NOCACHE ensures that you see every line that was executed.

#### Examples

Example 9-76 Debugging with a Debugging File

The following statements create a useful debugging file called `debug.txt` in the current directory object.

    PRGTRACE = yes
    ECHOPROMPT = yes
    DBGOUTFILE 'debug.txt'

After executing these statements, you can run your program as usual. To close the debugging file, execute this statement.

    DBGOUTFILE EOF

In the following sample program, the first LIMIT command has a syntax error.

    DEFINE ERROR_TRAP PROGRAM
    PROGRAM
    TRAP ON traplabel
    LIMIT month TO FIRST badarg
    LIMIT product TO FIRST 3
    LIMIT district TO FIRST 3
    REPORT sales
    traplabel:
    SIGNAL ERRORNAME ERRORTEXT
    END

With `PRGTRACE` and `ECHOPROMPT` both set to `YES` and with `DBGOUTFILE` set to send debugging output to a file called `debug.txt`, the following text is sent to the `debug.txt` file when you execute the `error_trap` program.

    (PRG= ERROR_TRAP)
    (PRG= ERROR_TRAP) TRAP ON traplabel
    (PRG= ERROR_TRAP)
    (PRG: ERROR_TRAP) LIMIT month TO FIRST badarg
    ERROR: BADARG does not exist in any attached database.
    (PRG= ERROR_TRAP) traplabel:
    (PRG= ERROR_TRAP) SIGNAL ERRORNAME ERRORTEXT
    ERROR: BADARG does not exist in any attached database.

Example 9-77 Sending Debugging Information to a File

The following is the text of a program whose first LIMIT command has a syntax error.

    DEFINE error_trap PROGRAM
    PROGRAM
    TRAP ON traplabel
    LIMIT month TO FIRST BADARG
    LIMIT product TO FIRST 3
    LIMIT district TO FIRST 3
    REPORT sales
    traplabel:
    SIGNAL ERRORNAME ERRORTEXT
    END

The following statement sends debugging information to a file named `debug.txt`.

    DBGOUTFILE 'debug.txt'

With PRGTRACE and ECHOPROMPT both set to `YES`, Oracle OLAP sends the following text to the `debug.txt` file when you execute the ERROR_TRAP program. The last line in the file is the command to stop recording the debugging information.

    error_trap
    (PRG= ERROR_TRAP) 
    (PRG= ERROR_TRAP) trap on traplabel
    (PRG= ERROR_TRAP) 
    (PRG: ERROR_TRAP) limit month to first badarg
    ERROR: BADARG does not exist in any attached workspace.
    (PRG= ERROR_TRAP) traplabel:
    (PRG= ERROR_TRAP) signal errorname errortext
    ERROR: BADARG does not exist in any attached workspace.
    dbgoutfile eof

### 9.35 DEFINE

The DEFINE command adds a new object to the analytic workspace. This entry describes the DEFINE command in general. The following entries discuss the use of the DEFINE command for creating specific types of object:

- DEFINE AGGMAP

- DEFINE COMPOSITE

- DEFINE DIMENSION

  - DEFINE DIMENSION (simple)

  - DEFINE DIMENSION (conjoint)

  - DEFINE DIMENSION CONCAT

  - DEFINE DIMENSION ALIASOF

- DEFINE FORMULA

- DEFINE MODEL

- DEFINE PARTITION TEMPLATE

- DEFINE PROGRAM

- DEFINE RELATION

- DEFINE SURROGATE

- DEFINE VALUESET

- DEFINE VARIABLE

- DEFINE WORKSHEET

**See Also:**

[Formulas, Models, Aggregations, and Allocations](formulas-models-aggregations-and-allocations.md)

#### Syntax

DEFINE name object-type attributes \[AW workspace\] \[SESSION\]

#### Parameters

name
A `TEXT` expression that is the name for the new object. Follow these guidelines when specifying a value for name:

- The name must consist of 1 to 64 characters. When you are using a multibyte character set, you can still specify 64 characters even when this requires more than 64 bytes. Each character may be a letter (`A`-`Z`), a number (`0`-`9`), an underline (`_`), or a dot (`.`). However, the following restrictions apply to the use of these characters:

  - The name cannot consist of a single dot (`.`) character or a single underscore (`_`) character.

  - The name cannot duplicate a reserved word. For more information on identifying reserved words, see the [RESERVED](olap-dml-functions-l-z.md) function.

  - The first character in the name cannot be a number.

  - The first character cannot be a dot (`.`) when the second character is a number.

- By default Oracle OLAP creates the definition in the current workspace. To create the definition in a different attached workspace, you can specify a qualified object name for name or you can use the AW argument to specify the workspace. Do not use both.

**Note:**

Oracle OLAP does not warn you when you create an object that has the same name as an existing object in another attached workspace.

object-type
The type of object being defined. The default is VARIABLE. The object types are discussed in the subsections for the DEFINE command.

attributes
Attributes are different for each type of object. The attributes are listed in the entry for each object type.

AW workspace
The name of an attached workspace in which you want to define the object. You can also specify a noncurrent attached workspace using a qualified object name for name. Do not use this phrase when qualified object name for name.

SESSION
Specifies that the object exists only in the current session. The object is created in the EXPRESS analytic workspace to which you have read-only access. When you close the current session, the object no longer exists.

#### Usage Notes

Triggering Program Execution When DEFINE Executes

Using a TRIGGER_DEFINE program, you can make the DEFINE command an event that automatically executes an OLAP DML program. See "[Trigger Programs](olap-dml-programs.md)" for more information.

Effect of DEFINE on the Status of the NAME Dimension

When you execute a DEFINE command with the NAME dimension limited to less than all its values, the status of NAME is automatically limited to `ALL`.

Viewing Session Objects

Objects created with the SESSION keyword are stored in the analytic workspace named `EXPRESS` instead of the current analytic workspace. Therefore, statements that operate against the current analytic workspace (such as LISTNAMES) do not list session objects unless you do one of the following:

- Specify the `EXPRESS` analytic workspace in the statement (such as `LISTNAMES AW EXPRESS`)

- Make the `EXPRESS` analytic workspace the current analytic workspace by issuing an `AW ATTACH EXPRESS` statement.

#### 9.35.1 DEFINE AGGMAP

The DEFINE command with the AGGMAP keyword adds a new aggmap object to an analytic workspace. An aggmap object is a specification for how Oracle OLAP allocates or aggregates variable data.

Defining an aggmap merely creates an aggmap object in the analytic workspace; it does not define the calculation specification. The aggmap specification can either specify how to aggregate or how to allocate data:

- For information on coding an aggregation specification, see the AGGMAP command.

- For information on coding an allocation specification, see the ALLOCMAP command.

##### Syntax

DEFINE aggname AGGMAP \[\<dims...\>\]\[AW workspace\]\[SESSION\]

##### Parameters

aggname
The name of the object that you are defining. For general information about this argument, see the main entry for the DEFINE command.

AGGMAP
The object type when you are defining an aggmap.

dims
(Optional; retained for compatibility with earlier software versions.) When defining an aggmap object for aggregation (that is, an AGGMAP-type aggmap), the names of the dimensions. You cannot specify a conjoint dimension as a base dimension in the definition or specification for the aggmap.

AW workspace
The name of an attached workspace in which you want to define the object. For more about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. For more information about this argument, see the main entry for the DEFINE command.

##### Examples

Example 9-78 Creating an Aggmap for Aggregation

Suppose you define a `sales` variable with the following statement.

    DEFINE sales VARIABLE <time, product, geography>

Assume also that you have defined an aggmap named `sales.agg` with the following definition and specification.

    DEFINE sales.agg AGGMAP <time, product, geography>
    AGGMAP
    RELATION time.r PRECOMPUTE (time NE 'Year99')
    RELATION product.r PRECOMPUTE (product NE 'All')
    RELATION geography.r
    CACHE STORE
    END

The `sales.agg` aggregation specification contains the preceding three RELATION statements and a CACHE statements. In this example, you are specifying that all of the data for the `time.r` hierarchy of the `time` dimension should be aggregated, except for any data that has a `time` dimension value of `Year9`9. All of the data for the `product.r` hierarchy of the `product` dimension should be aggregated, except for any data that has the `product` dimension value of `ALL`. (In this example, the `product` dimension has a dimension value named `ALL` that represents all products in the hierarchy.) All `geography` dimension values are aggregated. The CACHE STORE statement specifies that any data that is rolled up on the fly should be calculated just once and stored in the cache for other access requests during t he same session.

Note that users should not have write access to the analytic workspace when CACHE STORE is set, because the data calculated during the session may be saved inadvertently.

In this example, any data value that dimensioned by a `Year99` `time` value or an `ALL` `product` dimension value is calculated on the fly.

You can now use the `sales.agg` aggmap with an AGGREGATE command, such as the following.

    AGGREGATE sales USING sales.agg

Example 9-79 Creating an Aggmap for Allocation

Suppose you have a `sales` variable that you defined with the following statement.

    DEFINE sales VARIABLE <time, product, geography>

To allocate data from a source to cells in the `sales` variable that are specified by the `time` and `product` dimension hierarchies, you have created an ASCII disk file called `salesalloc.txt`, which contains the following aggmap definition and specification.

    DEFINE sales.alloc AGGMAP
    ALLOCMAP
    RELATION time.r OPERATOR EVEN
    RELATION product.r operator EVEN NAOPERATOR HEVEN
    SOURCEVAL ZERO
    CHILDLOCK DETECT
    END

To include the `sales.alloc` aggmap in your workspace, execute the following statement.

    INFILE 'salesalloc.txt'

The `sales.alloc` aggmap is now defined, and it contains the preceding two RELATION statements, the SOURCEVAL statement and the CHILDLOCK statement. You end the entry of statements into the aggmap with the END statement. In this example, you are specifying that the first allocation of source values occurs down the `time` dimension hierarchy and that the source value is divided evenly between the target cells at each level of the allocation. The second allocation occurs down the `product` dimension hierarchy, with the source value again divided evenly between the target cells at each level of the allocation, and when the allocation encounters a deadlock, the source values is divided evenly between the target cells of the hierarchy including cells that have a basis value of `NA`. With the SOURCEVAL statement you specify that after the allocation, ALLOCATE sets the value of each source cell to zero. With the CHILDLOCK statement you specify that ALLOCATE detects the existence of locks on both a parent and a child element of a dimension hierarchy.

You can now use the `sales.alloc` aggmap with an ALLOCATE command, such as the following.

    ALLOCATE sales USING sales.alloc

The preceding statement does not specify a basis or a target object so ALLOCATE uses the `sales` variable as the source, the basis, and the target of the allocation.

#### 9.35.2 DEFINE COMPOSITE

The DEFINE command with the COMPOSITE keyword adds a new named composite to an analytic workspace. Conceptually, you can think of a composite consisting of two structures:

- The composite object itself. The composite contains the dimension-value combinations (that is, a composite tuples) that Oracle OLAP uses to determine the structure of any variables dimensioned by the composite.

- An index between the composite values and its base dimension values.

For a variable that is dimensioned by composite, Oracle OLAP creates array elements (that is, variable cells) only for those dimension values that are stored in the tuples of the composite; it does not create a cell for every value in the base dimensions. Data for the variable is stored in order, cell by cell, for each tuple in the composite. From the perspective of data storage, each combination of base dimension values in a composite is treated like the value of a regular dimension. Consequently, when you define a variable with one regular dimension and one composite, the data for the variable is stored as though it was a two-dimensional variable. Using composites to reduce the number of elements created for a variable results in more efficient data storage.

**Note:**

Oracle OLAP also supports the use of unnamed composites as described in "Unnamed Composites".

##### Syntax

DEFINE name COMPOSITE \<dims...\> \[AW workspace\] \[index-algorithm\] \[SESSION\]

where `index-algorithm` specifies the algorithm that Oracle OLAP uses to create an index that relates the composite values to its base dimension values. When you omit this optional argument, Oracle OLAP uses the value specified by the SPARSEINDEX option. Valid values for `index-algorithm` are:

- `BTREE`
- `BTREE64`
- `COMPRESSED`
- `HASH`

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

COMPOSITE
The object type when you are defining a named composite.

dims
The names of two or more dimensions that you want to be the base dimensions of the composite. When you specify COMPRESSED as the value of index-algorithm, at least one dimension must be a hierarchal dimension.

The order of the dimensions in dims varies by the value you specify for index-algorithm:

- For b-tree or hash composites, specify the dimensions in fastest to slowest-varying order as discussed in "Effect of Dimension Order on Variable Storage and Statement Looping".

- For compressed composites, it does not matter in which order you specify the dimensions. Oracle OLAP selects the order in which to store the values unless you override this optimization by specifying FORCEORDER in an AGGREGATE command or AGGREGATE function. To see the optimized order chosen by Oracle OLAP, view the cube operations log.

  **See Also:**

  Oracle Database PL/SQL Packages and Types Reference for information about the cube operations log and the DBMS_CUBE_LOG package

You must define all the dimensions and named composites used in the list before defining the composite. DEFINE automatically creates any unnamed composites in the list for you.

AW workspace
The name of an attached workspace in which you want to define the object. For more information about this argument, see the main entry for the DEFINE command.

BTREE
Specifies the creation of a b-tree index to relate composite values to base dimension values. BTREE is the standard indexing method for composites. For a variable that is dimensioned by a BTREE composite, Oracle OLAP creates array elements (that is, variable cells) only for those dimension values that are stored in the tuples of the composite; it does not create a cell for every value in the base dimensions.

BTREE64
Specifies the creation of a highly-scalable b-tree index to relate composite values to base dimension values. For a variable that is dimensioned by a BTREE64 composite, like a BTREE composite, Oracle OLAP creates array elements (that is, variable cells) only for those dimension values that are stored in the tuples of the composite; it does not create a cell for every value in the base dimensions. However, unlike a BTREE composite, a BTREE64 composite supports b-trees greater than 2 gigabytes.

**Note:**

Typically, you define a BTREE64 composite when you want to use it to dimension a variable which you populate from a relational table that is larger than 2 gigabytes.

COMPRESSED
Specifies the creation of a compressed index to relate composite values to base dimension values. You specify COMPRESSED only when you want to create a composite for a variable that has at least one hierarchical dimension that is specified in dims and that is aggregated.

A compressed composite contains one composite tuple for each set of base dimension values that identifies non-NA detail data in the variables that use it. Additionally, for variables dimensioned by compressed composite Oracle OLAP reduces redundancy in the variable, composite, and composite index by creating a physical position in the composite only for those tuples that represent a parent with multiple descendants. Oracle OLAP then creates an index between this composite structure and the base dimensions and uses this composite structure as the dimension of the variable. Because the actual structure of a compressed composite is smaller than that of a b-tree or hash composite, a variable dimensioned by a compressed composite is also smaller than a variable dimensioned by a b-tree or hash composite. Also, because the index for a compressed composite only has nodes for parents with multiple descendants, the index of a compressed composite has fewer levels and is smaller than the index of a b-tree composite. Although performance varies depending on the depth of the hierarchies and the order of the dimensions in the composite, aggregating variables defined with compressed composites is typically much faster than aggregating variables defined with b-tree or hash composites.

**Note:**

Oracle OLAP compresses the data in variables dimensioned by compressed composites using the "intelligence" of the AGGREGATE command or AGGREGATE function. Consequently, there are special considerations that apply when aggregating a variable dimensioned by one or more compressed composites. See "Aggregating Variables Dimensioned by Compressed Composites" for more information.

HASH
Specifies the creation of a hash index to relate composite values to base dimension values. HASH is rarely used and, then, typically, only when the composite has two or three dimensions. For a variable that is dimensioned by a b-tree or hash composite, Oracle OLAP creates array elements (that is, variable cells) only for those dimension values that are stored in the tuples of the composite; it does not create a cell for every value in the base dimensions.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Usage Notes

Shared Composites

You can use the same b-tree or hash composite to dimension several variables. (Compressed composites cannot be shared in this manner.) The actual sparsity of a variable dimensioned by a b-tree or hash composite varies depending on whether or not the composite is an unshared composite or a shared composite:

- An unshared composite is a composite that is used to dimension only one variable. All types of composites (that is, b-tree, hash, and compressed composites) can be unshared composites. An unshared composite is populated only when the variable that uses it is populated. Consequently, an unshared composite perfectly reflects the sparsity of the variable that it is used to dimension. It only has the dimension value combinations for each non-`NA` value in that variable.

- A shared composite is a composite that is used to dimension multiple variables. A shared composite can be either a b-tree or hash composite; it cannot be a compressed composite. A shared composite is populated when any of the variables that use it are populated. A shared composite has all of the dimension value combinations for non-`NA` values for all of the variables that it dimensions. A shared composite reflects the sparsity of all of the variable that it is used to dimension. Typically, therefore, variables dimensioned by shared composites are not perfectly sparse variables.

When the size of variables is important, or when you have variables that are sparse along the same dimensions but with significantly different patterns of sparsity, define different composites for the different variables.

##### Examples

This section contains a simple example of creating a named b-tree composite. For examples of using composites to dimension variables, see Example 9-99 and Example 9-100.

Example 9-80 Creating a Named b-Tree Composite

Assume that the value of SPARSEINDEX is `BTREE`. The following statements define two objects: a named composite that has a b-tree index and base dimensions of `market` and a variable called `expenses` that is dimensioned by the `month` dimension and the `market.product` composite.

    DEFINE market.product COMPOSITE <market product>
    DEFINE expenses DECIMAL <month market.product <market product>>

#### 9.35.3 DEFINE DIMENSION

The DEFINE command with the DIMENSION keyword adds a new dimension object to an analytic workspace. A dimension is a list of values that provides an index to the data.

Because the syntax of the DEFINE DIMENSION command is different depending on the type of the dimension that you are defining, four separate entries are provided:

- DEFINE DIMENSION (simple) for defining a dimension with unique values of the same data type.

- DEFINE DIMENSION (DWMQY) for defining a non-hierarchical dimension whose values represent a time period (day, week, month, quarter, or year).

- DEFINE DIMENSION (conjoint) for defining a dimension over two or more other base dimensions when the base dimensions do not contain duplicate values or have different data types and when you want to explicitly specify the dimension value combinations.

- DEFINE DIMENSION CONCAT for defining a dimension over two or more other base dimension when the base dimensions contain duplicate values or different data types or when you want Oracle OLAP to automatically populate the dimension value combinations.

- DEFINE DIMENSION ALIASOF for defining an alias for a simple dimension.

**Note:**

Defining a dimension in the analytic workspace merely adds the definition of the dimension to the analytic workspace; it does not populate the dimension. To populate dimensions using the OLAP DML, you can issue OLAP DML SQL, FILEREAD, or MAINTAIN statements.

##### 9.35.3.1 DEFINE DIMENSION (simple)

The DEFINE DIMENSION (simple) command defines a simple dimension. When a variable is dimensioned by regular dimensions, Oracle OLAP creates an array element for each set of its dimension values. The values of a simple dimension must be unique data values with the same data type. A simple dimension can be a flat dimension or a hierarchical dimension that contains values from different levels of a hierarchy.

**Note:**

To create a hierarchical dimension using duplicate values or values of different data types, use a concat dimension as described in DEFINE DIMENSION CONCAT.

##### Syntax

DEFINE name DIMENSION type \[TEMP\] \[AW workspace\] \[SESSION\]

where `type` is the data type of the dimension. The syntax of `type` varies depending on the data type:

- `TEXT  [WIDTH` `n``]`
- `NTEXT  [WIDTH ``n``]`
- `ID`
- `INTEGER`
- `NUMBER [(``precision`` ,`` scale``)`\]
- `DATETIME` `[(`` truncation-code` `)]`
- `TIMESTAMP` `[(`` truncation-code` `)]`
- `TIMESTAMP_TZ` `[(`` truncation-code` `)]`
- `TIMESTAMP_LTZ` `[(`` truncation-code` `)]`

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

DIMENSION
The object type when you are defining a dimension.

TEXT
Specifies that the values of the dimension have the TEXT data type which is equivalent to the CHAR and VARCHAR2 data types in Oracle Database. This data type stores up to 4,000 bytes for each line in the database character set.

NTEXT
Specifies that the values of the dimension have the NTEXT data type which is equivalent to the NCHAR and NVARCHAR2 data types in Oracle Database. This data type stores up to 4,000 bytes for each line in UTF-8 character encoding.

ID
Specifies a special text data type that stores up to 8 single-byte characters for each line in the database character set.

WIDTH n
For TEXT or NTEXT dimensions, the width, in bytes, of the storage area of each value of an object. Valid width values are `1` through `4000`. Specify a fixed width only when you are certain that the values of a particular dimension are of similar size. When a value exceeds the specified width, it is truncated.

INTEGER
Specifies that the values of the dimension have the `INTEGER` data type. The data type for a dimension with values that are identified by their numeric position (1, 2, and so on). A data type of `INTEGER` means that the dimension has no character values. For ease of use, use a text or time period data type, when possible.

NUMBER
Specifies that the values of the dimension have the `NUMBER` data type. A `NUMBER` dimension differs from other dimensions in that its values cannot be specified by position, only by value. To specify the values of a `NUMBER` dimension by position, you can define an `INTEGER` type dimension surrogate for the `NUMBER` dimension.

precision
The total number of digits a value of type `NUMBER` can have.

scale
The number of digits a value of type `NUMBER` can have to the right of a decimal point. For example, when you specify a precision of 7 and a scale of 2, then the highest value that the dimension can have is 99999.99. When you specify a precision value, but do not specify a scale value, then the scale is 0.

DATETIME
Specifies that the values of the dimension have the `DATETIME` data type.

TIMESTAMP
Specifies that the values of the dimension have the `TIMESTAMP` data type.

TIMESTAMP_TZ
Specifies that the values of the dimension have the `TIMESTAMP_TZ` data type.

TIMESTAMP_LTZ
Specifies that the values of the dimension have the `TIMESTAMP_LTZ` data type.

truncation_code
A text expression that specifies a format model shown in [Table 8-13](olap-dml-functions-l-z.md). A format model indicates how the date and time number should be truncated.

TEMP
Indicates that the dimension's values are only temporary and only for the current session. The dimension has a definition in the current workspace and can contain values during the current session. However, when you update and commit, only the definition of the dimension is saved. When you leave end your session or switch to another workspace, the data values are discarded. Each time you start the workspace, the values of a temporary dimension are `NA`.

AW workspace
The name of an attached analytic workspace in which you want to define the dimension. Any objects dimensioned by the dimension must be defined in the same workspace. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Usage Notes

NA Values in Variables Dimensioned by Simple Dimensions

When a variable is dimensioned by regular dimensions, Oracle OLAP creates an array element for each set of its dimension values. When an array element is empty, then the element is said to contain an `NA` value. In some cases, this can result in a sparse variable—that is, a variable in which a relatively high percentage of array elements that are empty. There are two types of sparsity:

- Controlled sparsity occurs when a range of one or more dimensions has no data; for example, a new variable dimensioned by `month` for which you do not have data for past months.

- Random sparsity occurs when some combinations of dimension values never have any data. For example, a district might only sell certain products and never have data for other products. Other districts might sell some of those products and other ones, too.

When a sequence of array elements contain enough `NA` values to fill up an analytic workspace page, Oracle OLAP does not actually store any of the `NA` values and, instead, keeps tracks of the values internally. However, when an analytic workspace page contains both regular values and `NA` values, then Oracle OLAP stores all of the values. You can reduce the number of array elements with `NA` values by dimensioning a variable with one or more composites or conjoint dimensions. See the DEFINE COMPOSITE and DEFINE DIMENSION (conjoint) commands.

##### Examples

Example 9-81 Defining a Simple Dimension

This example adds the dimension `city` to an analytic workspace. You can attach a description to the object immediately after defining it. (You can also add the description later when you use CONSIDER and LD statements.) After defining the dimension `city`, you can give it values with a MAINTAIN statement.

The statements

    DEFINE city DIMENSION ID
    LD List of cities
    MAINTAIN city ADD 'Boston' 'Chicago' 'Dallas' 'Seattle'
    DESCRIBE city

produce the following definition.

    DEFINE city DIMENSION ID
    LD List of cities

##### 9.35.3.2 DEFINE DIMENSION (DWMQY)

The DEFINE DIMENSION (DWMQY) command defines a DWMQY dimension (that is a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR) whose values represent time periods. After defining a DWMQY dimension, you can use a [VNF](olap-dml-commands-h-z.md) statement to add a value name format to the dimension's definition. The VNF command controls the format for entering dimension values and the format for showing them in output.

**Note:**

When you want to aggregate over time do not define the time dimension as a DWMQY dimension because you cannot aggregate over dimensions of this type. Instead, define the time dimension as a hierarchical dimension of type `TEXT` or `NTEXT`.

##### Syntax

DEFINE name DIMENSION dwmqy \[TEMP\] \[AW workspace\] \[SESSION\]

where `dwmqy` is the time period of the dimension. The valid types for dwmqy are DAY, WEEK, MONTH, QUARTER, and YEAR. Each type indicates the span of the time period represented by the individual dimension values of the dimension. The syntax of `dwmqy` varies depending on the type:

-     ` DAY` 
-     ` [``multiple``] WEEK [BEGINNING phase`` ] [ ENDING phase ``]` 
-     ` [``multiple``] MONTH [BEGINNING phase`` ] [ ENDING phase ``]` 
-     ` QUARTER [BEGINNING phase`` ] [ ENDING phase ``]` 
-     ` YEAR [BEGINNING phase`` ] [ ENDING phase ``]` 

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

DIMENSION
The object type when you are defining a dimension.

multiple
For the WEEK and MONTH types, specifies time periods that span a multiple number of weeks or months. With the WEEK keyword, multiple can be an `INTEGER` from 2 to 52. With the MONTH keyword, multiple can be 2, 3, 4, or 6.

BEGINNING phase
ENDING phase
Specifies the beginning or ending phase of a WEEK, MONTH, QUARTER, or YEAR dimension:

- For single weeks, phase can be a day of the week (corresponding to a name in the DAYNAMES option) or a date.

- For multiple weeks, phase must be a date.

- For months, quarters, or years, phase must be a month, expressed as a month name (corresponding to a name in the MONTHNAMES option) or as a date.

When you specify phase as a date, you give the month, day, and year, enclosed in single quotes, using any of the input styles that are valid for variable values with a data type of DATE. When you specify a date with an ambiguous meaning (such as `'03 05 97'`), the date is interpreted according to the current setting of the DATEORDER option.

**Note:**

When you define a multiple-period dimension of type WEEK but you do not specify a BEGINNING or an ENDING argument, DEFINE automatically supplies a phase that begins with the date `'31DEC1899'`.

TEMP
Indicates that the dimension's values are only temporary and only for the current session. The dimension has a definition in the current workspace and can contain values during the current session. However, when you update and commit, only the definition of the dimension is saved. When you leave end your session or switch to another workspace, the data values are discarded. Each time you start the workspace, the values of a temporary dimension are `NA`.

AW workspace
The name of an attached analytic workspace in which you want to define the dimension. Any objects dimensioned by the dimension must be defined in the same workspace. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Usage Notes

Implicit Relations Between DWMQY Dimensions

When you define two or more dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR, Oracle OLAP automatically defines implicit relations between the values of the dimensions. For example, when you define a dimension of type MONTH and a dimension of type YEAR, Oracle OLAP automatically defines a relation that associates all the MONTH values that fall within a particular year with the corresponding value of the YEAR dimension.

Using BEGINNING or ENDING Phase to Organize Data by Fiscal Calendar

For dimensions of type MONTH, QUARTER, and YEAR, the BEGINNING phase or ENDING phase argument is especially useful for data organized on a fiscal-year calendar.

By specifying a phase for a dimension of type MONTH or QUARTER, you identify the time period that is the first or last period within a year. For example, when you define a dimension of type MONTH with an ending phase of June, then June is identified as the twelfth month of the year. When a dimension of type QUARTER has an ending phase of June, the quarter ending in June is identified as the fourth quarter of the year. When you give a dimension a VNF that includes a period code, you can enter or report dimension values according to their period within the year.

By default, the single or multiple weeks in a dimension of type WEEK end on Saturday. The BEGINNING phase or ENDING phase argument lets you specify the day of the week on which each period begins or ends. For multiple-week periods, the phase argument also controls the starting or ending date for grouping the weeks into periods. By default, the starting point for grouping multiple weeks is December 31, 1899 (a Sunday).

However, the phase argument does not determine the period that is counted as the first period within a year. For dimensions of type WEEK, Period 1 in a given calendar year is always the first period that ends in that year. For example, suppose you specify a dimension of type WEEK with a four-week period ending on June 7, 1997. DEFINE works backward and forward from this date, forming weeks into four-week periods. For 1997, Period 1 is the period beginning on December 22, 1996 and ending on January 18, 1997.

##### Examples

Example 9-82 Defining a YEAR Dimension

The following statement defines a dimension of type YEAR that holds values for fiscal years that end on June 30.

    DEFINE fyear DIMENSION YEAR ENDING june

After defining the dimension, you can give it a description and a VNF (value name format). You can use a MAINTAIN statement to give values to the dimension.

    LD Fiscal years ending June 30
    VNF 'FY<ff>'
    MAINTAIN fyear ADD 'FY97' 'FY00'

Example 9-83 Using the Default Phrase for Date in an ENDING Phrase

This example illustrates how DEFINE automatically supplies a phase that begins with the date `'31DEC1899'` when you define a multiple-period dimension of type WEEK but you do not specify a BEGINNING phase or an ENDING phase argument. Assume that you issue the following statements

    DEFINE twoweek DIMENSION 2 WEEK
    DESCRIBE TWOWEEK

When you issue a DESCRIBE statement for `twoweek`, the following output is produced.

    DEFINE twoweek DIMENSION 2 WEEK ENDING '13Jan1900'

##### 9.35.3.3 DEFINE DIMENSION (conjoint)

The DEFINE DIMENSION (conjoint) command defines a conjoint dimension.

Conceptually, you can think of a conjoint dimension consisting of two structures:

- The dimension object itself. The values of the dimension are combinations of values of two or more other dimensions (that is, a conjoint tuples) that Oracle OLAP uses to determine the structure of any variables dimensioned by the conjoint dimension.

- An index between the conjoint dimension values and its base dimension values.

Composites are another object that you can use to dimension a variable using a list of dimension value combinations. See "Differences Between Conjoint Dimensions and Composites" for a discussion of the major differences between composites and conjoint dimensions.

##### Syntax

DEFINE name DIMENSION \<dims. . .\> index-algorithm  \[AW workspace\] \[SESSION\]

where `index-algorithm` specifies the algorithm that Oracle OLAP uses to create the index into the conjoint dimension. Valid values for `index-algorithm` are:

- `BTREE`
- `NOHASH`
- `HASH`

##### Parameters

name
The name of the conjoint dimension you are defining. For general information about this argument, see the main entry for the DEFINE command.

DIMENSION
The object type when you are defining a conjoint dimension.

dims
One or more previously defined dimensions that are the base dimensions of the conjoint dimension. Specify the dimensions in fastest to slowest-varying order as discussed in "Effect of Dimension Order on Variable Storage and Statement Looping". You must enclose the dimension list in angle brackets.

Typically, a base dimension of a conjoint dimension is a simple dimension, but it can also be another conjoint dimension. However, when you do have a simple dimension for one value of dims, you cannot also specify for dims a conjoint or concat dimension that has same simple dimension as one of its bases.

BTREE
Specifies the creation of a b-tree index to relate conjoint values to base dimension values. Typically, you specify BTREE as the index algorithm for a conjoint dimension.

**Tip:**

When you are unsure whether to specify BTREE or NOHASH, use NOHASH, because you can always use a CHGDFN statement to change a NOHASH conjoint into a BTREE conjoint, while you can use a CHGDFN statement to change a BTREE conjoint into a NOHASH conjoint only when the conjoint was originally defined as a NOHASH conjoint

NOHASH
Specifies that Oracle OLAP does not create an index for the conjoint dimension, but instead uses internal structures to relate conjoint values to base dimension values. Because no index is created for NOHASH, NOHASH decreases the number of structures associated with the conjoint dimension; and, in many cases, decreases the time it takes to load and access conjoint dimension values. However, NOHASH is used infrequently, as it is a complicated algorithm that, on occasion, can result in unpredictable performance.

HASH
(Default, but not recommended.) Specifies the creation of a has index to relate conjoint values to base dimension values.

**Tip:**

Even though HASH is the default, typically, you specify BTREE as the index algorithm for a conjoint dimension. When your conjoint dimension has more than 3 base dimensions, for best performance, use BTREE instead of HASH.

AW workspace
The name of an attached analytic workspace in which you want to define the dimension. Any objects dimensioned by the dimension must be defined in the same workspace. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Usage Notes

Differences Between Conjoint Dimensions and Composites

You can use either a composite or a conjoint dimension to dimension a variable with a list of dimension value combinations. Keep the following points in mind when deciding on which type of object to use:

- Object population maintenance—Conjoint dimensions offer the most control, while composites provide the greatest ease of use:

  - Oracle OLAP determines the dimension value combinations stored in a composite. Oracle OLAP populates a composite automatically when a variable dimensioned by composite is populated.

  - You determine the dimension value combinations that are stored in a composite. You must explicitly populate and maintain a conjoint dimension using MAINTAIN statements the same way you populate and maintain other dimensions.

- Dimension operations —You can perform dimension operations on conjoint dimensions, but not composites; however, you can only perform dimension operations on the base dimensions of composites. For example, you can LIMIT conjoint dimensions, but you must limit the base dimensions of a composite to limit your view to a subset of composite values; and you can define relations using conjoint dimensions, but not composites.

For more information on composites, see the DEFINE COMPOSITE command.

Relationship of Conjoint Dimensions to Base Dimensions

The values of the conjoint dimension are related to the base dimensions. You can specify data in a variable dimensioned by the conjoint dimension using the conjoint value combinations, the individual values of the base dimensions, or other dimensions related to either of the base dimensions of the conjoint dimension.

Defining a Subset of a Dimension's Values

You can have a conjoint dimension with only one base dimension, which enables you to create a subset of that dimension's values. You must still enclose that one base dimension within angle brackets.

Using Conjoint Dimension Values in Expressions

To refer to the value of a conjoint dimension in an expression, specify the value following these guidelines:

- Enclose the entire dimension value specification in angle brackets and then enclose this entire specification in single quotes; do not enclose the individual values in single quotes.

- Use the exact upper- and lowercase spellings for the base dimension values.

- When the specification includes a text value with an embedded blank, you must separate the dimension values with commas.

For example, when `item.org` is a conjoint dimension with base dimensions `item` and `org`, use the following format to refer to values of `item.org`.

    '<Expenses, Direct Sales>'

##### Examples

Example 9-84 Defining a Conjoint Dimension

Assume that you have defined and populated the simple dimensions `city`, `state`, and `region` and that they have the following values.

    CITY             STATE           REGION
    ---------       ----------       ------
    Princeton       New Jersey       East
    Newark          New Jersey       Central
    Patterson       New York
    New York        Illinois
    Chicago         Indiana

To define a conjoint dimension named `cityandstate` and add values to it use the following OLAP DML statements.

    DEFINE cityandstate DIMENSION <city state>
    MAINTAIN cityandstate add <'Princeton' 'New Jersey'>
    MAINTAIN cityandstate add <'Newark' 'New Jersey'>
    MAINTAIN cityandstate add <'Patterson' 'New Jersey'>
    MAINTAIN cityandstate add <'New York' 'New York'>
    MAINTAIN cityandstate add <'Chicago' 'Illinois'>
    MAINTAIN cityandstate add <'Princeton' 'Indiana'>

##### 9.35.3.4 DEFINE DIMENSION CONCAT

The DEFINE DIMENSION CONCAT commands defines a concat dimension. A concat dimension is a dimension that groups a set of base dimensions with duplicate values or different data types into one dimension.

When there are duplicate data values, you create a non-unique concat dimensions. For example, you would create a nonunique dimension for a geography hierarchy when "New York" is both the value at the city level and at the state level. When all of the data values in all of the base dimensions are unique, you can create a unique concat dimension.

**Tip:**

The way that you specify the values of concat dimension varies depending on whether the concat dimension is a unique or nonunique concat dimension. See "[Specifying a Value of a CONCAT Dimension](data-types-operators-and-expressions.md)" for more information.

##### Syntax

DEFINE name DIMENSION CONCAT(basedimlist. . .)\[UNIQUE\]  \[TEMP\] \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

DIMENSION CONCAT
The object type when you are defining a concat dimension.

basedimlist
One or more previously-defined dimensions that are the base dimensions of the concat dimension. Specify the dimensions in fastest to slowest-varying order as discussed in "Effect of Dimension Order on Variable Storage and Statement Looping". You must enclose the dimension list in parenthesis.

The types of dimensions that can be base dimensions varies depending on whether you are defining a unique or nonunique concat dimension:

- When defining a non-unique concat dimension, a base dimension can be a simple dimension of any data type, a conjoint dimension, or another concat dimension.

- When defining a unique concat dimension, a base dimension can be a simple dimension of type TEXT or ID, or another unique concat dimension if the data values of all of the base dimensions are unique and not duplicated in any of the base dimensions.

A composite cannot be the base dimension of a concat dimension.

Simple dimensions and conjoint dimensions are the bottom-level components of a concat dimension. When you specify a concat dimension as a base dimension when defining a concat, then the base dimensions of that inner concat are component dimensions of the outer concat.

The same dimension cannot appear more than once in the component dimensions of a concat dimension. However, in a concat, a conjoint dimension is an indivisible unit and Oracle OLAP does not consider the base dimensions of a conjoint in the definition of the concat. Therefore, a simple dimension can be a base dimension of a conjoint and that conjoint and the same simple dimension can be base dimensions (or components) of a concat dimension.

For example, the following definitions are permissible.

    DEFINE conjointdim.a DIMENSION <simpledim.b, simpledim.c>
    DEFINE conjointdim.b DIMENSION <simpledim.a, simpledim.b>
    DEFINE conjointdim.c DIMENSION <simpledim.a, conjointdim.a>
    DEFINE concatdim.a DIMENSION CONCAT (simpledim.a, conjointdim.a)
    DEFINE concatdim.b DIMENSION CONCAT (simpledim.a, conjointdim.b)
    DEFINE concatdim.c DIMENSION CONCAT (simpledim.b, conjointdim.b)
    DEFINE concatdim.d DIMENSION CONCAT (simpledim.a, concatdim.c)

In the definition of `concatdim.a`, the base dimensions are `simpledim.a` and `conjointdim.a`. In the definition of `concatdim.d`, the base dimensions are `simpledim.a` and `concatdim.c`. The component dimensions of `concatdim.d` are `simpledim.a`, `simpledim.b`, and `conjointdim.b`. `simpledim.a` and `simpledim.b` appear only once as component dimensions even though they are the base dimensions of `conjointdim.b` because the base dimensions of a conjoint are not component dimensions of a concat.

However, the following definition is not permitted because the same simple dimension is a base dimension of `concatdim.e` and a component of `concatdim.e` because it is a base dimension of `concatdim.b`.

    DEFINE concatdim.e DIMENSION CONCAT (simpledim.a, concatdim.b)

**Note:**

The simple dimensions in the basedimlist argument, and the simple dimensions that are base dimensions of any conjoint dimensions or concat dimensions in basedimlist, cannot have an INTEGER data type.

UNIQUE
Specifies that the text values of the base dimensions are unique. When you specify this keyword, the dimensions listed in basedimlist must be either simple text or ID dimensions or unique concat dimensions.

TEMP
Indicates that the dimension's values are only temporary and only for the current session. The dimension has a definition in the current workspace and can contain values during the current session. However, when you update and commit, only the definition of the dimension is saved. When you leave end your session or switch to another workspace, the data values are discarded. Each time you start the workspace, the values of a temporary dimension are `NA`.

AW workspace
The name of an attached analytic workspace in which you want to define the dimension. Any objects dimensioned by the dimension must be defined in the same workspace. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Examples

Example 9-85 Defining a CONCAT Dimension

Assume that you have defined and populated the simple dimensions `city`, `state`, and `region` and that they have the following values.

    CITY             STATE           REGION
    ---------       ----------       ------
    Princeton       New Jersey       East
    Newark          New Jersey       Central
    Patterson       New York
    New York        Illinois
    Chicago         Indiana

You define a concat dimension based on these dimensions using the following OLAP DML statement.

    DEFINE geog DIMENSION CONCAT(region cityandstate)

The values of `geog` are the following.

    <REGION: East>
    <REGION: Central>
    <CITYANDSTATE: <Princeton New Jersey>>
    <CITYANDSTATE: <Newark New Jersey>>
    <CITYANDSTATE: <Patterson New Jersey>>
    <CITYANDSTATE: <New York New York>>
    <CITYANDSTATE: <Chicago Illinois>>
    <CITYANDSTATE: <Princeton Indiana>>

##### 9.35.3.5 DEFINE DIMENSION ALIASOF

The DEFINE DIMENSION ALIASOF command defines a dimension alias for a simple dimension. An alias dimension has the same type and values as its base dimension. Typically, you define an alias dimension when you want to dimension a variable by the same dimension twice.

Additionally, You can use a LIMIT statement to limit alias dimensions and define variables and relations using an alias dimension. However, you cannot maintain an alias dimension directly; instead you maintain its base dimension using MAINTAIN.

##### Syntax

DEFINE name DIMENSION ALIASOF dimension \[TEMP\] \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

DIMENSION ALIASOF
The object type when you are defining a dimension. Indicates that the dimension being defined is an alias for another dimension.

dimension
The name of a simple dimension for which you want to define an alias. This dimension cannot be a concat or conjoint dimension, composite, or surrogate.

TEMP
Indicates that the dimension's values are only temporary and only for the current session. The dimension has a definition in the current workspace and can contain values during the current session. However, when you update and commit, only the definition of the dimension is saved. When you leave end your session or switch to another workspace, the data values are discarded. Each time you start the workspace, the values of a temporary dimension are `NA`.

AW workspace
The name of an attached analytic workspace in which you want to define the dimension. Any objects dimensioned by the dimension must be defined in the same workspace. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Examples

Example 9-86 Defining an Alias Dimension

Assume that your department has multiple projects that employees participate in and that an employee may be a leader of one project and a participant in another. Assume also that you want to track the hours that each employee participates in a project as either a leader or a participant. To keep track of this information, you can design a variable that is dimensioned by the time you want to track by (in this example, `year`), `project`, and two dimensions for employee—one dimension named `employee` for employee as participant and another dimension named `leader` for employee as leader. The following definitions support this structure.

    DEFINE year DIMENSION TEXT
    DEFINE project DIMENSION TEXT
    DEFINE employee DIMENSION TEXT
    DEFINE leader DIMENSION ALIASOF employee
    DEFINE hours VARIABLE INTEGER <year project employee leader>

The following statements populate all of the dimensions.

    MAINTAIN year ADD '2001' '2002' '2003'
    MAINTAIN project ADD 'projA' 'projB'
    MAINTAIN employee add 'Adams' 'Baker' 'Charles'

Note that you do not have to explicitly populate the alias dimension (that is, `leader`). When you populate the `employee` dimension, Oracle OLAP also populates its alias dimension `leader`.

    EMPLOYEE
    --------------
    Adams
    Baker
    Charles

    LEADER
    --------------
    Adams
    Baker
    Charles

You can limit a dimension without limiting its alias; or limit an alias without limiting the dimension for which it is an alias. For example, when you issue the following statements to limit `employee` to Adams for `project` ProjA in `year` 2001, a report displays all of the leaders of the projects that Adams participates in.

    LIMIT year TO '2001'
    LIMIT employee TO 'Adams'
    LIMIT project TO 'projA'
    REPORT DOWN leader ACROSS employee: hours

    PROJECT: projA
    YEAR: 2001
                   --HOURS---
                   -EMPLOYEE-
    LEADER           Adams
    -------------- ----------
    Adams                   1
    Baker                   2
    Charles                 1

On the other hand, when you limit `leader` to Adams for `project` ProjA in `year` 2001, a report displays all of the employees of the projects that Adams leads.

    LIMIT employee TO ALL
    LIMIT leader TO 'Adams'
    LIMIT project TO 'projA'
    REPORT DOWN leader ACROSS employee: hours

    PROJECT: projA
    YEAR: 2001
                   -------------HOURS--------------
                   ------------EMPLOYEE------------
    LEADER           Adams      Baker     Charles
    -------------- ---------- ---------- ----------
    Adams                   1          3          3

#### 9.35.4 DEFINE FORMULA

The DEFINE command with the FORMULA keyword adds a new formula object to an analytic workspace. You define a formula to save an expression. A formula can take the place of an expression you use repeatedly. The name of the formula takes the place of the text of the expression. Oracle OLAP does not store the data for a formula in a variable; instead it is calculated at run time each time it is requested.

**See Also:**

"[OLAP DML Formulas](formulas-models-aggregations-and-allocations.md)"

##### Syntax

DEFINE name FORMULA {expression \| \[ datatype \]\[\<dimensions...\>\]} \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

FORMULA
The object type when you are defining a formula.

expression
The calculation to be performed to produce values when you use the formula. It can be any valid expression, including a constant or the name of a variable as described in [OLAP DML Expressions](data-types-operators-and-expressions.md).

You can specify an expression for a formula when you define it or after you define using an EQ statement. When you define a formula without specify an expression, a formula returns `NA` with the specified data type.

**Note:**

Oracle OLAP does not automatically convert text in a formula to uppercase.

datatype
The intended data type for the formula when you do not specify a value for expression. You can use any of the data types that apply to variables. If you do not specify a value, the data type is determined at run time.

When you include an expression in the formula definition, DEFINE automatically determines the data type for a formula defined using expression. Later, when you add the expression using an EQ statement, its data type should match the type you specify now. When it does not, DEFINE converts the output to the specified type.

dimensions
The dimensions of the formula. Enclose the list in angle brackets. The `dimensions` argument is optional. When the formula is a single-cell value, you do not specify any dimensions. Also, when you include an expression in the definition, you do not specify a value. DEFINE automatically determines the dimensions.

However, when you do not include an expression in the definition, you must specify the dimensions. When you add the expression later using an EQ statement, the expression must have the same dimensions as the formula definition. When it does not, DEFINE forces the output to have the specified dimensions.

**Note:**

You cannot define a formula that is dimensioned by a composite.

AW workspace
The name of an attached workspace in which you want to define the formula. When the formula is dimensioned, it must be defined in the same workspace as its dimensions. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Usage Notes

Effect of Changing the Characteristics of Objects Used by a Formula

When you change the name, data type, or dimensions of any of the objects used by a formula, the formula is not automatically updated. The formula causes an error when objects it refers to have been deleted or are now the wrong data type.

Storing Complex Expressions and Calculations

To define a very complex calculation, you can define a program that uses a RETURN statement to return a value. You can then use the program as a function wherever you would use an expression or formula.

##### Examples

Example 9-87 Defining a Formula

This example adds a formula named `sales.diff` to an analytic workspace. This formula calculates the percent difference between total sales for the current year and last year.

The statements

    DEFINE sales.diff FORMULA LAGPCT(TOTAL(actual year) 1 year)
    DESCRIBE sales.diff

produce the following definition.

    DEFINE sales.diff FORMULA DECIMAL <year>
    EQ lagpct(TOTAL(actual year) 1 year)

#### 9.35.5 DEFINE MODEL

The DEFINE command with the MODEL keyword adds a new model object to an analytic workspace. A model is a set of interrelated equations. The calculations in an equation can be based either on variables or on dimension values. You can assign the results of the calculations directly to a variable or you can specify a dimension value for which data is being calculated. For example, in a financial application, all the equations might be based on the values of a line item dimension, and data would be calculated for line items such as total expenses and net income.

**Note:**

Defining a model merely creates a model object in the analytic workspace. You must also code a specification for the model, as described in MODEL.

##### Syntax

DEFINE name MODEL \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

MODEL
The object type when you are defining a model.

AW workspace
The name of an attached workspace in which you want to define the object. For more information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Examples

Example 9-88 Defining a Simple Model

This example shows a simple model named `income.calc` that calculates the line items in an income statement. The model equations are based on the `line` dimension in the `demo` workspace. First, define the model and give it an LD.

    DEFINE income.calc MODEL
    LD Model for calculating Income Statement items

Then use a MODEL statement to enter the specification for the model. For this example, you can enter model lines such as the ones in the following model description.

    DEFINE income.calc MODEL
    LD Model for calculating Income Statement items
    MODEL
    dimension line
    net.income = opr.income - taxes
    opr.income = gross.margin - (marketing+selling+r.d)
    gross.margin = revenue - cogs
    END

To solve the model for the `actual` variable, enter data in `actual` for the input line items (`Revenue`, `Cogs`, `Marketing`, `Selling`, `R.D`, and `Taxes`). Then execute the following statement.

    income.calc actual

#### 9.35.6 DEFINE PARTITION TEMPLATE

The DEFINE command with the PARTITION TEMPLATE keywords adds a new partition template object to an analytic workspace. A partition template is a specification for the partitions of a partitioned variable. A partitioned variable is stored as multiple rows in the relational table of LOBs that is the analytic workspace—each partition is a row in the table. You define both partitioned and unpartitioned variables using DEFINE VARIABLE statements. Before you can define a partitioned variable you must first define a partition template object.

##### Syntax

DEFINE name PARTITION TEMPLATE \<dimlist\>  PARTITION BY       {RANGE\|LIST} (dims_partitioned_by)  (\[partition_definition_statement...\]) \[AW workspace\]

where `partition_definition_statement` defines a partition. The syntax varies depending on whether you specify `RANGE` or `LIST`:

- For `RANGE`:

  PARTITION partition-name VALUES LESS THAN const-exp \<partition-dimlist\>

- For `LIST`:

  PARTITION partition-name VALUES (\[valuelist)\] \<partition-dimlist\>

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

dimlist
A list of all of the logical dimensions for the variable that you are partitioning. You must enclose the names of the dimensions in a single set of angle brackets (`<` `>`). You must define a dimension before you can include it in the definition of a partition template.

dims_partitioned_by
The subset of dimensions specified by dimlist that actually specify the partitions of the variable. For range and list partitioning (that is, when you specify either the RANGE or LIST keywords), you can specify only one dimension for dims_partitioned_by. You cannot partition a variable along an `INTEGER` dimension.

PARTITION partition-name
The name of the partition.

VALUES LESS THAN
Indicates that you are specifying a RANGE partition by comparing values.

constant-exp
A constant expression that has the same data type as the data type of the dimension specified for dims_partitioned_by.

partition-dimlist
A list of all of the dimensions of the partition template object (although the dimensions may be members of a composite). You must enclose the names of the dimensions in a single set of angle brackets (`<` `>`). Use this argument to specify the composite (if any) used to dimension the partitions that correspond to partition-name. When you do not specify a value then the partition is dimensioned densely by all of the dimensions of the partition template object.

VALUES
Indicates that you are specify a LIST partition by specifying values.

valuelist
A list of dimension values, separated by commas. You must surround text values with single quotes (for example, `'mytext'`). Specify values of conjoints by specify the values of the base dimensions, separated by a comma, in a single set of angle brackets (for example, `<'Value1', 'Value2'>`). Specify values of nonunique concat dimensions by specify the values of the base dimensions, separated by a colon, in a single set of angle brackets (for example, `<'Value1': 'Value2'>`).

**Tip:**

I f you want to use a valueset object to specify values, do not specify values for valuelist. Instead, omit valuelist from the partition template definition and use a [MAINTAIN ADD TO PARTITION](olap-dml-commands-h-z.md) statement to specify values for the partition.

##### Examples

See Example 9-101.

#### 9.35.7 DEFINE PROGRAM

The DEFINE command with the PROGRAM keyword adds a new OLAP DML program object to an analytic workspace. An OLAP DML program is a collection of OLAP DML statements that helps you accomplish some workspace management or analysis task. Defining a program merely creates a program object in the analytic workspace. You must also code the actual lines of the program.

**See Also:**

"[Creating OLAP DML Programs](olap-dml-programs.md)"

##### Syntax

DEFINE name PROGRAM \[datatype\|dimension\] \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

PROGRAM
The object type when you are defining a program.

datatype
The data type of the value to be returned by the program when it is called as a function. You can use any of the data types that apply to variables.

dimension
The name of a dimension, whose value the program returns when it is called as a function. The return value is a single value of the dimension, not a position (`INTEGER`). The dimension must be defined in the same workspace as the program.

AW workspace
The name of an attached workspace in which you want to define the program. When the program returns a dimension, the program must be defined in the same workspace as the dimension. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists.

##### Usage Notes

Returning Values

Use a RETURN statement in a program when you want it to return a value. The argument to the RETURN statement is an expression that specifies the value to return. When the expression does not match the declared data type or dimension, the value is converted (if possible) to the declared data type or dimension value.

When you do not specify a data type or dimension in the definition of a program, its return value is treated as worksheet data and Oracle OLAP converts any return value to the data type required by the calling context which may lead to unexpected results.

For a program to return a value, you must call the program as a function. That is, you must use it as an expression in a statement. In the following example, the program `isrecent` is being treated as a function. It is an argument to the REPORT command.

    REPORT isrecent(actual)

When the program returns values of a dimension, the program is in the output of the LISTBY function, and OBJ(ISBY) is `TRUE` for the dimension.

See the entries for the ARGUMENT, CALL, and [RETURN](olap-dml-commands-h-z.md) commands for more information about programs as user-defined functions.

##### Examples

Example 9-89 Basing Program Flow on Test Results

The `saleseval` program tests whether total sales for a month exceeds total planned sales for the month. The program executes different statements based on the results of the test.

    DEFINE SALESEVAL PROGRAM
    PROGRAM
    ARGUMENT onemonth MONTH
    VARIABLE excess DECIMAL
    ALLSTAT
    LIMIT month TO onemonth
    IF TOTAL(sales, month) GT TOTAL(sales.plan, month)
       THEN DO
         excess = (TOTAL(sales, month) - 
           - TOTAL(sales.plan, month)) -
           / TOTAL(sales.plan, month) * 100
         SHOW JOINCHARS('Sales exceeded plan by ' excess '%.') 
         DOEND
    ELSE SHOW JOINCHARS('We\'re not meeting plan. ' -
       'Let\'s get working!')
    REPORT DOWN product W 10 ACROSS district: sales - sales.plan
    END

When total sales for the month exceeds total planned sales for the month, the THEN statement lines are executed. The program calculates the percentage by which actual sales exceeds planned sales and places the result in a numeric variable called `excess`. The program then sends the results to the current outfile. The JOINCHARS function is used to combine the calculated expression `excess` with the text expression "Sales exceeded plan by" in the output.

When total sales does not exceed planned sales, the ELSE statement line is executed and a different message is produced.

After the THEN or ELSE statement lines are executed, control flows to the next line in the program, and a report of sales in excess of plan is produced.

#### 9.35.8 DEFINE RELATION

The DEFINE command with the RELATION keyword adds a new relation object to an analytic workspace. A relation describes a correspondence between the values of two or more dimensions. It can have dimensions, just like a variable, but the values of the relation must be values from the related dimension.

**Note:**

Defining a relation merely adds the definition of the relation to the analytic workspace; it does not populate the relation. To populate relations using the OLAP DML, you can issue OLAP DML SQL, FILEREAD, SET, or SET1 statements.

##### Syntax

DEFINE name RELATION related-dim \[\<dimensions...\>\] \[TEMP\] \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

RELATION
The object type when you are defining a relation.

related-dim
Specifies the dimension to which one or more dimensions are related. A relation is normally used to store information about the relationship between two dimensions; for example, the cities that belong in each region.

In the definition, the dimension having fewer values is normally specified as the related dimension (for example, regions). The dimension having more values is normally specified as a dimension of the relation (for example, cities).

\<dimensions...\>
The names of the dimensions of the relation. You must enclose the names of the dimensions in a single set of angle brackets (`< >`). You must define a dimension before including it in the definition of a relation. Do not include composites in the dimension list.

**Note:**

Oracle OLAP does not support the use of composites as dimensions for relations. Do not attempt to define them.

**Tip:**

When defining two relations between the same dimensions, use the RELATION command to identify which relation is the default relation.

TEMP
Indicates that the values of the relation are only temporary. The relation is defined in the current workspace and can contain values during the current session. However, when you update and commit the workspace, only the definition of the relation is saved. When you end the session or switch to another workspace, the data values are discarded. Each time you start the workspace, the values of a temporary relation are `NA`.

AW workspace
The name of an attached workspace in which you want to define the relation. The relation must be defined in the same workspace as its dimensions. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When the session ends, the object no longer exists. The behavior specified by the SESSION keyword differs from the behavior specified by the TEMP keyword which is that the values are temporary, but the object definition remains in the workspace in which you create it.

##### Examples

Example 9-90 Creating, Populating, and Totaling by a Relation

The following example defines a relation between `division` and `product`, stores the values of the relation, and then totals `units` by `division`, even though `units` is dimensioned by` product`. The following statement defines the `div.prod` relation.

    DEFINE div.prod RELATION division <product>

The following statements store values of `division` in `div.prod`.

    LIMIT product TO 'Tents' 'Canoes'
    div.prod = 'Camping'
    LIMIT product TO 'Racquets'
    div.prod = 'Sporting'
    LIMIT product TO 'Sportswear' 'Footwear'
    div.prod = 'Clothing'

You can use a REPORT statement to see the values stored in `div.prod`.

    report div.prod

This statement produces the following output.

    PRODUCT        DIV.PROD
    ------------- ----------
    Tents         Camping
    Canoes        Camping
    Racquets      Sporting
    Sportswear    Clothing
    Footwear      Clothing

The `div.prod` relation lets you look at division totals in a report, even though the data is dimensioned by `product`.

    REPORT TOTAL(units division)

#### 9.35.9 DEFINE SURROGATE

The DEFINE command with the SURROGATE keyword adds a new dimension surrogate object to an analytic workspace. A surrogate provides an alternative set of values for a dimension. You can use a surrogate rather than a dimension in a model, in a LIMIT command, in a qualified data reference, or in data loading with statements such as FILEREAD, FILEVIEW, SQL FETCH, and SQL IMPORT.

**Note:**

Defining a surrogate merely adds the definition of the dimension surrogate to the analytic workspace; it does not populate the surrogate. To populate surrogates using the OLAP DML, you can issue OLAP DML SQL, FILEREAD, SET, or SET1 statements.

##### Syntax

DEFINE name SURROGATE targetname type \[AW workspace\] \[SESSION\]

where `type` has the following syntax:

     \[TEXT\|NTEXT\] \[WIDTH n\]\|ID\|INTEGER\|NUMBER (precision\[, scale\] \| `datatime-datatype`)

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

SURROGATE
The object type when you are defining a dimension surrogate.

targetname
The name of the dimension for which you are creating a surrogate. See "Restrictions on the Use of Surrogates" for points to keep in mind when determining the target.

TEXT
NTEXT
ID
The data type for a dimension surrogate with text values. When all the values of a dimension surrogate are eight single-byte characters or less, give it a data type of ID. When one or more dimension values has more than eight single-byte characters, you must give it a data type of TEXT or NTEXT. For greater efficiency and ease of use, give dimensions a data type of ID whenever possible.

WIDTH n
For TEXT or NTEXT dimension surrogate, the width, in bytes, of the storage area of each value of an object. Valid width values are 1 through 4000. Specify a fixed width only when you are certain that the values of a particular dimension surrogate are of similar size. When a value exceeds the specified width, Oracle OLAP truncates it.

INTEGER
The data type for a dimension surrogate with values that are the ordinal positions (1, 2, and so on) of the values in its dimension. You might create an INTEGER type dimension surrogate for a `NUMBER` type dimension so that you can specify dimension values by position instead of by the value of the dimension. When you define an INTEGER type dimension surrogate, Oracle OLAP automatically assigns an `INTEGER` value to the surrogate for each of the positions in the dimension.

NUMBER
Specifies that the dimension surrogate has a data type of `NUMBER`. See "[Numeric Data Types](data-types-operators-and-expressions.md)" for more information.

precision
Specifies the total number of characters in the value of a dimension surrogate of type `NUMBER`.

scale
Specifies the number of characters that can be to the right of a decimal point of a dimension surrogate of type `NUMBER`.

datetime_datatype
Specifies a datetime data type (that is, `DATETIME` , `TIMESTAMP`, `TIMESTAMP_TZ`, or `TIMESTAMP-LTZ`). See "[Datetime and Interval Data Types](data-types-operators-and-expressions.md)" for more information.

AW workspace
The name of an attached workspace in which you want to define the dimension surrogate. The dimension for which you define the surrogate must be defined in the same workspace. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When you close the current session, the object no longer exists. Use this keyword when the definition of the targetname dimension includes SESSION.

##### Usage Notes

Restrictions on the Use of Surrogates

Keep the following restrictions in mind when determining a target for your surrogate:

- You cannot create a surrogate for a dimension that has a type of DAY, WEEK, MONTH, QUARTER, or YEAR or for a composite.

- When you create a surrogate for a conjoint, you cannot convert the conjoint to a composite.

You cannot specify a dimension surrogate as the dimension or related dimension argument when you define a concat dimension, a formula, a program, a relation, a valueset, or a variable. Additionally, in data loading you cannot create new dimension values using a dimension surrogate

##### Examples

Example 9-91 Creating an INTEGER Dimension Surrogate

The following statement creates an INTEGER type dimension surrogate for the `store_id` dimension.

    DEFINE storepos SURROGATE store_id INTEGER

Example 9-92 Creating a NUMBER Dimension Surrogate

The following statement creates an `NUMBER` type dimension surrogate for the `product` dimension, which is a TEXT dimension that has product names as values. The precision argument to the NUMBER keyword specifies that a value in `prodnum` can have no more than seven characters and the scale argument specifies that no more than three characters can be to the right of the decimal point.

    DEFINE prodnum SURROGATE product NUMBER(7, 3)

The following statement sets the first value of `prodnum` to `1083.375`.

    prodnum(product 1) = 1083.375

#### 9.35.10 DEFINE VALUESET

The DEFINE command with the VALUESET keyword adds a new valueset object to an analytic workspace. A valueset is a list of dimension values for one or more dimensions. You use a valueset to save dimension status lists across sessions.

**Note:**

Defining a valueset adds the definition of the valueset to the analytic workspace and sets all of its values to null (`NA`). To assign values to a valueset use the LIMIT command. You can also use a STATUS statement and the STATFIRST, INSTAT, and VALUES functions to work with a valueset.

##### Syntax

DEFINE name VALUESET dimension \[\<dims...\>\] \[NOORDER\] \[TEMP\] \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

VALUESET
The object type when you are defining a valueset.

dimension
The name of the previously-defined dimension whose values you want to store in the valueset.

dims
When defining a multi-dimensional valueset, the names of the previously-defined dimensions by which you want the valueset dimensioned.

NOORDER
For a dimensioned valueset (that is, a valueset for which you specify one or more value for dims), specifies that Oracle OLAP stores the valueset as a compressed bitmap. When you specify this keyword the order of the original status is lost.

TEMP
Indicates that the values of the valueset are only temporary. The valueset has a definition in the current workspace and can contain values during the current session. However, when you update and commit, only the definition of the valueset is saved. When you end the session or switch to another workspace, the values are discarded. Each time you start the workspace, the value of a temporary valueset is null.

AW workspace
The name of an attached workspace in which you want to define the valueset. The valueset must be defined in the same workspace as its dimensions. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When the session ends, the object no longer exists. The behavior specified by SESSION is different from the behavior specified by the TEMP keyword which is that the values are temporary but the object definition remains in the workspace in which you create it.

##### Examples

Example 9-93 Creating and Assigning Values to a Valueset

This example adds the valueset named `lineset` to the demonstration workspace. The `lineset` valueset is dimensioned by `line`, and therefore it can be limited by the current values of the `line` dimension. The LD statement attaches a description to the object.

The following statements 1) limit the `line `dimension and display the values in status, 2) create a valueset named `lineset` by defining valueset and limiting the valueset to those values currently in status for the line dimension, and 3) display the values of the lineset.

    LIMIT line TO FIRST 2
    STATUS line

    The current status of LINE is:
    REVENUE, COGS

    " Define the valueset and specify a long description for it

    DEFINE lineset VALUESET line
    LD Valueset for LINE dimension values
    " Assign the values that are currently in status for line
    " as the values of valueset
    LIMIT lineset TO line
    UPDATE

    SHOW lineset

    Revenue
    Cogs

Example 9-94 Creating and Assigning Values to a Multidimensional Valueset

Assume that your analytic workspace has the variables and dimensions with the following definitions.

    DEFINE geography DIMENSION TEXT
    DEFINE product DIMENSION TEXT
    DEFINE sales VARIABLE DECIMAL <geography product>
    DEFINE salestax VARIABLE DECIMAL <geography>

Assume also that the analytic workspace contains the following dimensions whose values are the names of variables and dimensions within the workspace.

    DEFINE all_variables DIMENSION TEXT
    MAINTAIN all_variables ADD 'sales' 'salestax'
    DEFINE all_dims DIMENSION TEXTMAINTAIN all_dims ADD 'geography' 'product'

The following statements create and populate a valueset for the values of `all_variables` and `all_dims`, and then report the values of that valueset.

    DEFINE variables_dims VALUESET all_dims <all_variables>
    " Assign all values of all_dims and all_variables to the valueset
    LIMIT variables_dims TO ALL
    REPORT variables_dims

    ALL_VARIABLES        VARIABLES_DIMS
    ---------------- ------------------------------
    sales            geography
                     product
    salestax         geography
                     product


To create a multidimensional valueset that has the correct dimensions related to the variables that use them, you issue the following statement that uses a QDR to limit the `all_dims` values for the` salestax` value of `all_variables`.

    LIMIT variables_dims(all_variables  'salestax') TO 'geography'
    REPORT variables_dims

    ALL_VARIABLES        VARIABLES_DIMS
    ---------------- ------------------------------
    sales            geography
                     product
    salestax         geography

#### 9.35.11 DEFINE VARIABLE

The DEFINE command with the VARIABLE keyword adds a new variable object to an analytic workspace. Variables store one type of data, which can be numeric, text, Boolean, or dates. Beside the data type of a variable, the definition that you create for a variable also determines the following characteristics of the variable:

- The number of elements that are actually created in the array that is the variable.

- The logical order of the variable's elements.

- Whether the variable's data is stored permanently or is only available for the session.

- The number of LOBs that Oracle OLAP creates for the variable's data.

You can also define local program variables using a [VARIABLE](olap-dml-commands-h-z.md) command. These variables exist only when the program is running.

**Note:**

Defining a variable merely adds the definition of the variable to the analytic workspace; it does not populate the variable. To populate variables using the OLAP DML, you can issue OLAP DML SQL, FILEREAD, SET, or SET1 statements.

##### Syntax

DEFINE name \[VARIABLE\] datatype \[\<dims...\>\] \[WITH NULLTRACKING\] \[WITH AGGCOUNT\] -      \[PERMANENT \| TEMP \] -      \[ RANSPACE64\] \[(partition-instance...)\] \[WIDTH n\] \[AW workspace\] \[SESSION\]

where:

- `dims` are the dimensions of the variable separated by commas. For a dimension of a variable you can specify a dimension object, a partition template object, a named uncompressed composite, a compressed composite, or an unnamed uncompressed composite using one of the following:

  - `dimension_name`
  - `partition_template_name`` <``dims``>`
  - `uncompressed_composite_name`` <[``basedims``...]>`
  - `compressed_composite_name`` <[``basedims``...]>`
  - `SPARSE <``basedims``...>`

  **Note:**

  The order in which you list the dims of a variable is the default order of the dimensions and behavior of a variety of statements (such as REPORT and UNRAVEL) and affects how the data for the variable is stored (as discussed in "Effect of Dimension Order on Variable Storage and Statement Looping". Also, when you define multiple objects with the same dimensions, most operations work much more efficiently when you list the dimensions in the same order in each definition.

- `partition-instance` are the partitions of the variable separated by commas. Use the following syntax to specify a partition.

       PARTITION partition-name  INTERNAL \[TEMP \| PERMANENT\]

##### Parameters

name
The name of the variable you are defining. For general information about this argument, see the main entry for the DEFINE command.

VARIABLE
The object type when you are defining a variable. You do not have to include the word VARIABLE, because it is the default.

datatype
The data type of the data to be stored in the variable. The data types, their abbreviations, and the range of acceptable values are shown in [Table 2-1](data-types-operators-and-expressions.md).

dimension_name
The name of a simple, concat, conjoint, or alias dimension that you have previously defined using a DEFINE DIMENSION statement. In this case, you specify the name of the dimension.

RANSPACE64
When defining a `TEXT`, `NTEXT`, or `RAW` variable, specify this keyword to increase the maximum number of characters for the values of the variable from nearly `2**32` to nearly `2**64`.

 partition-template-name\<dims\>
The name of a partition template object that you have previously defined using a DEFINE PARTITION TEMPLATE statement. For dims, specify the names of the dimensions of the partition template object. These dimensions must be the same dimensions as those used to define the partition template object.

uncompressed_composite_name \<\[basedims...\]\>
The name of an uncompressed composite previously defined using a DEFINE COMPOSITE statement. For the optional basedims argument, specify the names, separated by commas, of the dimensions used to define the composite.

compressed_composite_name \<basedims...\>
The name of a compressed composite previously defined using a DEFINE COMPOSITE statement. For the optional basedims argument, specify the names, separated by commas, of the dimensions used to define the composite.

When defining a variable that is dimensioned by a compressed composite, keep the following points in mind:

- A compressed composite can dimension only one variable or one partition of a variable. A compressed composite cannot be a shared composite.

- The compressed composite must be the last dimension in the variable's dimension list of the DEFINE VARIABLE statement that defines the variable.

SPARSE \<basedims...\>
Indicates that you want Oracle OLAP to create an unnamed composite and use it when dimensioning the variable. For the basedims argument, specify the names of the dimensions, separated by commas, for which the unnamed composite is created.

WITH NULLTRACKING
When the variable is dimensioned by a composite, specifies that Oracle OLAP create NA2 bits for the cells of the variable.

**See Also:**

"NA2 Bits and Null Tracking"

WITH AGGCOUNT
Specifies that Oracle OLAP automatically creates an `INTEGER` variable in which it stores the non-`NA` counts of the number of leaf nodes that contributed to aggregate values calculated for RELATION statements that have an AVERAGE, HWAVERAGE, or WAVERAGE operator. You must include this phrase to calculate average aggregations for a variable dimensioned by a compressed composite. For more information on Aggcount variables, see "Aggcount Variables".

PERMANENT
TEMP
Specifies that a variable or a partition of a variable is either permanent or temporary. After you update and commit, the definition of both permanent and temporary variables and partitions is always saved between sessions. Specifying permanent or temporary determines whether, after you update and commit, the values of a variable or a partition of a variable are saved or discarded when you end your session or switch to another workspace:

- Permanent variables and partitions­—Oracle OLAP saves the data values or a permanent variable or permanent partitions. When you start the workspace, the data values or a permanent variable or permanent partitions are the same as they were at the last commit.

- Temporary variables and partitions­—Oracle OLAP discards the data values of a temporary variable or temporary partition. Each time you start the workspace, the values of a temporary variable or temporary partition are `NA`.

Keep the following points in mind when specifying the PERMANENT and TEMP keywords:

- By default, a variable is permanent.

- Temporary variables can be dimensioned by partition template objects or by temporary dimensions.

- By default, a top-level partition of a variable has the same permanence as the variable that contains it. Specifically, a partition of a temporary variable is a temporary partition unless you use the PERMANENT keyword to make it a permanent partition, and a partition of a permanent variable is a permanent partition unless you use the TEMPORARY keyword to make it a temporary partition. To indicate different behavior, use either the PERMANENT or TEMP keyword.

- By default, a subpartition has the same permanence as its parent partition. To indicate different behavior, use either the PERMANENT or TEMP keyword.

WIDTH n
(You can abbreviate WIDTH as W.) The width, in bytes, of the storage area for each value of a variable. When you are using a multibyte character set, be sure to specify the number of bytes, not characters.

You specify fixed widths to create faster and more compact data storage formats. You can specify fixed widths for dimensioned TEXT, NTEXT, and INTEGER variables only, as described in the following list:

- For dimensioned TEXT and NTEXT variables, you can specify a width from 1 byte through 4,000 bytes. Specify a fixed width for such variables only when you are certain that the values of a particular variable are of similar size. You cannot assign a width to a scalar variable.

- For dimensioned INTEGER variables, you can specify a width of 1 byte only. Define a fixed width INTEGER variable only when you are certain that all the values for that variable are between -128 and 127.

The default widths for variables are: 2 bytes for SHORTINTEGER, 4 bytes for DATE, INTEGER, and SHORTDECIMAL, and 8 bytes for DECIMAL and ID. TEXT and NTEXT variables that do not have fixed widths are stored on two sets of pages. The first set contains 4-byte cells, each of which points to the actual text value that is stored in the other set of pages. The default width of 4 bytes for TEXT and NTEXT variables is for these 4-byte cells.

PARTITION partition-name INTERNAL
Specifies a partition of the variable where partition-name is the name of the partition.

When defining the partitions of a variable dimensioned by a compressed composite, keep the following points in mind:

- A compressed composite can dimension only one partition.

- The partitions of a variable dimensioned by a compressed composite must respect the parent-child relationships of the hierarchical dimensions. When an AGGREGATE command executes, data cannot be aggregated across partitions. To verify if a variable is partitioned correctly, use the [PARTITIONCHECK](olap-dml-functions-l-z.md) function.

AW workspace
The name of an attached workspace in which you want to define the variable. When the variable is dimensioned, it must be defined in the same workspace as its dimensions. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When the session ends, the object no longer exists. The behavior specified by SESSION is different than the behavior specified by the TEMP keyword which is that the values are temporary but the object definition remains in the workspace in which you create it.

##### Usage Notes

Aggcount Variables

When you include the WITH AGGCOUNT phrase in a DEFINE VARIABLE statement, Oracle OLAP automatically creates the variable specified in the DEFINE statement and a secondary variable (often called the Aggcount variable). The Aggcount variable is an `INTEGER` variable that Oracle OLAP uses when performing average aggregations for the defined variable. When resolving RELATION statements that have an AVERAGE, HAVERAGE, WAVERAGE, or HWAVERAGE operator and that do not have a COUNT NO phrase, Oracle OLAP stores the non-`NA` counts of the number of leaf nodes that contribute to the average aggregate values in the Aggcount variable.

Most statements that maintain a variable also automatically maintain an associated Aggcount variable. For example, an EXPORT statement exports both a variable and its associated Aggcount variable, and a CLEAR statement clears both the variable and the related portions of the associated Aggcount variable. Additionally, some OLAP DML statements are specific to the use of Aggcount objects. The following table lists these statements:

Table 9-6 OLAP DML Statements for Aggcount Variables

| Statement                             | Keywords           | Description                                                                                                               |
|:--------------------------------------|:-------------------|:--------------------------------------------------------------------------------------------------------------------------|
| DEFINE VARIABLE                       | WITH AGGCOUNT      | Defines a variable and an associated Aggcount variable.                                                                   |
| [AGGCOUNT](olap-dml-functions-a-k.md) |                    | Retrieves the values of the Aggcount variable associated with the specified variable.                                     |
| CHGDFN                                | ADD\|DROP AGGCOUNT | Adds or drops an Aggcount variable for the specified variable.                                                            |
| [OBJ](olap-dml-functions-l-z.md)      | HASAGGCOUNT        | Returns a `BOOLEAN` value that indicates whether or not a specified variable has an Aggcount variable associated with it. |

NA2 Bits and Null Tracking

Relational fact tables sometimes have null facts (that is, facts that have a null value). Typically, when Oracle OLAP creates a variable dimensioned by a composite, it does not create a composite tuple for an NA (or null) value. Given this typical behavior, OLAP DML variables would not correspond to their base relational fact table because the variables would eliminate the null facts.

To support OLAP DML composite-dimensioned variables that correspond to relational fact tables with null facts, Oracle OLAP has a special NA bit called an NA2 bit. These NA2 bits tracks whether or not each cell of the variable has null value because the underlying relational table has a null fact. When the corresponding fact table has a null fact, you want Oracle OLAP to intentionally include an NA value in the composite tuples for the variable and NA2 bits are used by Oracle OLAP to do just that. NA2 bits are used by Oracle OLAP when it populates variables using the [SQL IMPORT](olap-dml-commands-h-z.md) command, the AGGREGATE command, and variables that were created as materialized views. They are also used by Oracle OLAP when it populates a relational table using the OLAP_TABLE SQL function. Additionally, Oracle OLAP recognizes NA2 values when evaluating expressions using arithmetic and Boolean operators.

The OLAP DML provides the following statements for working with variables that have NA2 bits:

- To create a variable with NA2 bits, use the DEFINE VARIABLE statement with the NULLTRACKING phrase.

- To add NA2 bits to a variable that does not have NA2 bits, use the CHGDFN statement with the NULLTRACKING phrase.

- To remove NA2 bits from a variable that has NA2 bits, use the CHGDFN statement with the DROP NULLTRACKING phrase.

- For testing and debugging purposes, use the [NA2](olap-dml-functions-l-z.md) function to set one or more of the NA2 bit of a variable to TRUE. Use the [NAFLAG](olap-dml-functions-l-z.md) function to identify if one or more values of a variable are NA values and, if so, if the NA value is just the typical NA values that OLAP should ignore or both the typical NA value and also an NA2 value.

  **See Also:**

  [Adding Materialized View Capability to a Cube](../olaug/creating-dimensions-and-cubes.md) in Oracle OLAP User’s Guide

Defining Very Large Variables

Theoretically, a variable can contain up to `2**63` cells and a TEXT or NTEXT variable can contain up to 2 billion bytes. However, the page size determines if a variable can be stored entirely on a page or how many variables can be stored on a page. To calculate the maximum number of values for a variable of a given width that fit on one page, use the VALSPERPAGE program.

Effect of Dimension Order on Variable Storage and Statement Looping

The order in which you list the dimensions of a variable definition determines the order in which the elements of the variable are stored and, consequently, how the data is accessed. The first dimension in the variable definition is the fastest-varying dimension, and the last dimension is the slowest-varying dimension.

For example, assume your analytic workspace has an `opcosts` variable that contains the operating costs, by month, of each city in which you have offices. In the following definition for the `opcosts` variable, `month` is the fastest-varying dimension and `city` is the slowest-varying dimension.

    DEFINE opcosts VARIABLE DECIMAL <month city>

The data for a multidimensional variable is stored as a linear stream of values, in which the values of the fastest-varying dimension are clustered. For example, for the `opcosts` variable, the values for Boston for all the months are stored in a sequence, and then it stores the values for Chicago for all the months in a sequence, and so on.

When you define variables and other dimensioned objects, and when you write programs that loop over multidimensional expressions in nested loops, always try to maximize performance by matching the fastest-varying dimension with the inner loop.

Unnamed Composites

Oracle OLAP automatically defines an unnamed composite when a DEFINE VARIABLE statement with a `SPARSE <``dimlist``>` phrase executes. An unnamed composite can have either a b-tree or hash index. The type of index is determined by the value of the SPARSEINDEX option when Oracle OLAP defines an unnamed composite.

Once Oracle OLAP has created a definition for an unnamed composite for a certain dimension list, it uses that composite any time you define a variable with the same `SPARSE <``dimlist``>` phrase. Thus all variables that are defined with the same `SPARSE <``dimlist``>` phrase share the same unnamed composite. For more information on sharing composites, see "Shared Composites".

Variable Segments

Within a partition, variable data is stored in analytic workspace segments. An analytic workspace segment is a group of logically contiguous analytic workspace pages. By default, the segment sizes of a variable are automatically determined by Oracle OLAP. Each segment is the exactly the number of analytic workspace pages needed to store the values assigned by the one OLAP DML statement. You can explicitly specify a segment size for a variable using the SEGWIDTH keyword of the CHGDFN command. In this case, when you assign values to a variable, Oracle OLAP stores the data assigned by multiple OLAP DML statements into a segment until the segment is full.

##### Examples

Example 9-95 Defining an INTEGER Variable with One Regular Dimension

This example adds the variable `population` to an analytic workspace. It is dimensioned by `city`, which has already been defined in the workspace. The LD Statement attaches a description to the object. The statements

    DEFINE population INTEGER <city>
    LD Population in each city
    DESCRIBE population

produce the following description.

    DEFINE POPULATION VARIABLE INTEGER <CITY>
    LD Population in each city

Example 9-96 Defining a Single-Cell Variable

The following is a definition for a variable named `newdata` which is a single Boolean value. It has no dimensions. An application might set it to `YES` when new data is added to the workspace and to `NO` after a user views the data.

    DEFINE newdata BOOLEAN
    newdata = YES

Example 9-97 Defining NUMBER Variables

The following statement defines a `NUMBER` variable named `sales` that is dimensioned by `product` and `geography` with a precision of 16 digits and a scale of 4 digits.

    DEFINE sales VARIABLE NUMBER (16,4) <product, geography>

The following statements define a `NUMBER` variable named `numvar` with 5 significant digits and 2 decimal places. The number 1234567 is out of its range.

    DEFINE numvar VARIABLE NUMBER (5, 2)
    numvar = 1234567
    SHOW numvar
    NA

A negative scale defines a `NUMBER` variable named `numnegvar` with 5 significant digits and 2 rounded digits to the left of the decimal point. The number 1,234,567 is rounded up.

    DEFINE numnegvar VARIABLE NUMBER (5, -2)
    numnegvar = 1234567
    SHOW numnegvar
    1,234,600.00

Example 9-98 Defining a Variable Dimensioned by Two Regular Dimensions

Assume that you have an analytic workspace that contains the following definitions for dimensions, relations, and aggmaps.

    DEFINE GEOG_CITY DIMENSION TEXT
    DEFINE GEOG_STATE DIMENSION TEXT
    DEFINE GEOG_AREA DIMENSION TEXT
    DEFINE GEOG_CONT DIMENSION TEXT
    DEFINE GEOG DIMENSION CONCAT (GEOG_CITY GEOG_STATE GEOG_AREA GEOG_CONT)
    DEFINE PROD_UPC DIMENSION TEXT
    DEFINE PROD_FAMILY DIMENSION TEXT
    DEFINE PROD_DIV DIMENSION TEXT
    DEFINE PROD_TOP DIMENSION TEXT
    DEFINE PROD DIMENSION CONCAT (PROD_UPC PROD_FAMILY PROD_DIV PROD_TOP)
    DEFINE GEOGLEVEL DIMENSION TEXT
    DEFINE PRODLEVEL DIMENSION TEXT
    DEFINE GEOG.PARENT RELATION GEOG <GEOG>
    DEFINE PROD.PARENT RELATION PROD <PROD>
    DEFINE GEOG.LEVELREL RELATION GEOGLEVEL <GEOG>
    DEFINE PROD.LEVELREL RELATION PRODLEVEL <PROD>
    DEFINE GEOG.FAMILYREL RELATION GEOG <GEOG GEOGLEVEL>
    DEFINE PROD.FAMILYREL RELATION PROD <PROD PRODLEVEL>
    DEFINE SALES_DIMS_REG VARIABLE NUMBER (12,0) <PROD GEOG>
    DEFINE SALES_AGGMAP AGGMAP
    AGGMAP
      RELATION geog.parent
      RELATION prod.parent
    END

The two parent relations (`prod.parent `and `geog.parent`) have the following values.

    PROD                             PROD.PARENT
    ------------------------- -------------------------
    <PROD_UPC: ColorTV>       <PROD_FAMILY: TV>
    <PROD_UPC: BWTV>          <PROD_FAMILY: TV>
    <PROD_UPC: StndVCR>       <PROD_FAMILY: VCR>
    <PROD_UPC: StrVCR>        <PROD_FAMILY: VCR>
    <PROD_FAMILY: VCR>        <PROD_DIV: VideoDiv>
    <PROD_FAMILY: TV>         <PROD_DIV: VideoDiv>
    <PROD_DIV: VideoDiv>      <PROD_TOP: Total Prod>
    <PROD_TOP: Total Prod>    NA
    GEOG                             GEOG.PARENT
    ------------------------- -------------------------
    <GEOG_CITY: Canberra>     <GEOG_STATE: ACT>
    <GEOG_CITY: Sydney>       <GEOG_STATE: NSW>
    <GEOG_CITY: Darwin>       <GEOG_STATE: NT>
    <GEOG_CITY: Brisbane>     <GEOG_STATE: QLD>
    <GEOG_CITY: Adelaide>     <GEOG_STATE: SA>
    <GEOG_CITY: Hobart>       <GEOG_STATE: TAS>
    <GEOG_CITY: Melbourne>    <GEOG_STATE: VIC>
    <GEOG_CITY: Perth>        <GEOG_STATE: WA>
    <GEOG_STATE: ACT>         <GEOG_AREA: Aust Terr>
    <GEOG_STATE: NSW>         <GEOG_AREA: Aust State>
    <GEOG_STATE: NT>          <GEOG_AREA: Aust Terr>
    <GEOG_STATE: QLD>         <GEOG_AREA: Aust State>
    <GEOG_STATE: SA>          <GEOG_AREA: Aust State>
    <GEOG_STATE: TAS>         <GEOG_AREA: Aust State>
    <GEOG_STATE: VIC>         <GEOG_AREA: Aust State>
    <GEOG_STATE: WA>          <GEOG_AREA: Aust State>
    <GEOG_AREA: Aust State>   <GEOG_CONT: Australia>
    <GEOG_AREA: Aust Terr>    <GEOG_CONT: Australia>
    <GEOG_CONT: Australia>    NA

Assume that you aggregate `sales_dims_reg `using `sales_aggmap`. Now assume that you issue the following REPORT statement for a report of the `sales_dims_reg` variable.

    REPORT sales_dims_reg->REPORT sales_dims_reg


As you can see from the output of the REPORT statement, the `sales_dims_reg` variable is a sparsely populated variable with 152 cells, many of which contain `NA` values.

                              ----------------------------SALES_DIMS_REG-----------------------------
                              ---------------------------------PROD----------------------------------
                                                                                    <PROD_DI
                              <PROD_UP          <PROD_UP <PROD_UP <PROD_FA <PROD_FA    V:    <PROD_TO
                                 C:    <PROD_UP    C:       C:     MILY:    MILY:   VideoDiv P: Total
    GEOG                      ColorTV> C: BWTV> StndVCR> StrVCR>    VCR>     TV>       >      Prod>
    ------------------------- -------- -------- -------- -------- -------- -------- -------- --------
    <GEOG_CITY: Canberra>     11,592.0       NA 38,356.0 3,444.00 41,800.0 11,592.0 53,392.0 53,392.0
    <GEOG_CITY: Sydney>             NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_CITY: Darwin>       24,868.0       NA 22,104.0 32,667.0 54,771.0 24,868.0 79,639.0 79,639.0
    <GEOG_CITY: Brisbane>     49,556.0       NA 48,239.0 24,285.0 72,524.0 49,556.0  122,080  122,080
    <GEOG_CITY: Adelaide>           NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_CITY: Hobart>       17,223.0       NA 18,872.0 48,780.0 67,652.0 17,223.0 84,875.0 84,875.0
    <GEOG_CITY: Melbourne>          NA 22,000.0       NA       NA       NA 22,000.0 22,000.0 22,000.0
    <GEOG_CITY: Perth>              NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: ACT>         11,592.0       NA 38,356.0 3,444.00 41,800.0 11,592.0 53,392.0 53,392.0
    <GEOG_STATE: NSW>               NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: NT>          24,868.0       NA 22,104.0 32,667.0 54,771.0 24,868.0 79,639.0 79,639.0
    <GEOG_STATE: QLD>         49,556.0       NA 48,239.0 24,285.0 72,524.0 49,556.0  122,080  122,080
    <GEOG_STATE: SA>                NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: TAS>         17,223.0       NA 18,872.0 48,780.0 67,652.0 17,223.0 84,875.0 84,875.0
    <GEOG_STATE: VIC>               NA 22,000.0       NA       NA       NA 22,000.0 22,000.0 22,000.0
    <GEOG_STATE: WA>                NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_AREA: Aust State>   66,779.0 22,000.0 67,111.0 73,065.0  140,176 88,779.0  228,955  228,955
    <GEOG_AREA: Aust Terr>    36,460.0       NA 60,460.0 36,111.0 96,571.0 36,460.0  133,031  133,031
    <GEOG_CONT: Australia>     103,239 22,000.0  127,571  109,176  236,747  125,239  361,986  361,986

Because the `sales_dims_reg` variable is dimensioned by two regular dimensions (rather than by composites or concat dimensions), the values of all of its cells (even those with an `NA` value) are stored in variable. You can confirm the number of physical values stored in the workspace by issuing the following statement.

    SHOW OBJ(NUMVALS 'sales_dims_reg')
    152.00

The result of the statement is that the value `152.00 `displays which indicates that every value in the 152 cells of the `sales_dims_reg` variable (even the `NA` values) are stored as part of the variable.

Example 9-99 Defining a Variable Dimensioned by an Uncompressed Composite

Assume that you have created an analytic workspace with the same dimensions, relations, and aggmap as those in Example 9-98. Now assume that you define a composite and a variable dimensioned by that composite by issuing the following statements.

    DEFINE COMP_PROD_GEOG COMPOSITE <PROD GEOG>
    DEFINE SALES_DIMS_COMPOSITE VARIABLE NUMBER (12,2) <COMP_PROD_GEOG <PROD GEOG>>

Assume that you populate `sales_dims_composite` with the same base values as you did `sales_dims_reg` in Example 9-98, and that you aggregate `sales_dims_composite` using the same aggmap (that is, `sales_aggmap`) and issue the following. REPORT statement for the `sales_dims_composite` variable.

    REPORT sales_dims_composite


A report for the `sales_dims_composite` variable displays the same 152 cells as the report for the `sales_dims_reg` variable.

                             -------------------------SALES_DIMS_COMPOSITE--------------------------
                              ---------------------------------PROD----------------------------------
                                                                                    <PROD_DI
                              <PROD_UP          <PROD_UP <PROD_UP <PROD_FA <PROD_FA    V:    <PROD_TO
                                 C:    <PROD_UP    C:       C:     MILY:    MILY:   VideoDiv P: Total
    GEOG                      ColorTV> C: BWTV> StndVCR> StrVCR>    VCR>     TV>       >      Prod>
    ------------------------- -------- -------- -------- -------- -------- -------- -------- --------
    <GEOG_CITY: Canberra>     11,592.0       NA 38,356.0 3,444.00 41,800.0 11,592.0 53,392.0 53,392.0
    <GEOG_CITY: Sydney>             NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_CITY: Darwin>       24,868.0       NA 22,104.0 32,667.0 54,771.0 24,868.0 79,639.0 79,639.0
    <GEOG_CITY: Brisbane>     49,556.0       NA 48,239.0 24,285.0 72,524.0 49,556.0  122,080  122,080
    <GEOG_CITY: Adelaide>           NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_CITY: Hobart>       17,223.0       NA 18,872.0 48,780.0 67,652.0 17,223.0 84,875.0 84,875.0
    <GEOG_CITY: Melbourne>          NA 22,000.0       NA       NA       NA 22,000.0 22,000.0 22,000.0
    <GEOG_CITY: Perth>              NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: ACT>         11,592.0       NA 38,356.0 3,444.00 41,800.0 11,592.0 53,392.0 53,392.0
    <GEOG_STATE: NSW>               NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: NT>          24,868.0       NA 22,104.0 32,667.0 54,771.0 24,868.0 79,639.0 79,639.0
    <GEOG_STATE: QLD>         49,556.0       NA 48,239.0 24,285.0 72,524.0 49,556.0  122,080  122,080
    <GEOG_STATE: SA>                NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: TAS>         17,223.0       NA 18,872.0 48,780.0 67,652.0 17,223.0 84,875.0 84,875.0
    <GEOG_STATE: VIC>               NA 22,000.0       NA       NA       NA 22,000.0 22,000.0 22,000.0
    <GEOG_STATE: WA>                NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_AREA: Aust State>   66,779.0 22,000.0 67,111.0 73,065.0  140,176 88,779.0  228,955  228,955
    <GEOG_AREA: Aust Terr>    36,460.0       NA 60,460.0 36,111.0 96,571.0 36,460.0  133,031  133,031
    <GEOG_CONT: Australia>     103,239 22,000.0  127,571  109,176  236,747  125,239  361,986  361,986

However, because the `sales_dims_comp` variable is dimensioned by a composite, the 65 cells that display as `NA` values are not stored in the variable. You can confirm the number of physical values that are stored in the workspace by issuing the following statement that calls the OBJ function with the NUMVALS keyword on `sales_dims_composite`.

    SHOW OBJ(NUMVALS 'sales_dims_composite')
    87.00

The result of the statement is that the value `87.00 `displays which indicates that only the 87 non-`NA` values are stored as part of the `sales_dims_composite` variable.

Example 9-100 Defining a Variable Dimensioned by a Compressed Composite

Assume that you have created an analytic workspace with the same dimensions, relations, and aggmap as those in Example 9-98. Now assume that you define a composite and a variable dimensioned by that composite by issuing the following statements.

    DEFINE CC_COMP_PROD_GEOG COMPOSITE <PROD GEOG> COMPRESSED
    DEFINE SALES_DIMS_COMP_COMPOSITE VARIABLE NUMBER (12,0) <CC_COMP_PROD_GEOG <PROD GEOG>>

Assume that you populate `sales_dims_composite` with the same base values as you did `sales_dims_reg` in Example 9-98, and that you aggregate `sales_dims_comp_composite` using the same aggmap (that is, `sales_aggmap`). Now you issue the following statement.

    REPORT sales_dims_comp_composite


A report for the `sales_dims_comp_comp_composite` variable displays the same 152 cells as the report for the `sales_dims_reg` variable.

                              -----------------------SALES_DIMS_COMP_COMPOSITE-----------------------
                              ---------------------------------PROD----------------------------------
                                                                                    <PROD_DI
                              <PROD_UP          <PROD_UP <PROD_UP <PROD_FA <PROD_FA    V:    <PROD_TO
                                 C:    <PROD_UP    C:       C:     MILY:    MILY:   VideoDiv P: Total
    GEOG                      ColorTV> C: BWTV> StndVCR> StrVCR>    VCR>     TV>       >      Prod>
    ------------------------- -------- -------- -------- -------- -------- -------- -------- --------
    <GEOG_CITY: Canberra>     11,592.0       NA 38,356.0 3,444.00 41,800.0 11,592.0 53,392.0 53,392.0
    <GEOG_CITY: Sydney>             NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_CITY: Darwin>       24,868.0       NA 22,104.0 32,667.0 54,771.0 24,868.0 79,639.0 79,639.0
    <GEOG_CITY: Brisbane>     49,556.0       NA 48,239.0 24,285.0 72,524.0 49,556.0  122,080  122,080
    <GEOG_CITY: Adelaide>           NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_CITY: Hobart>       17,223.0       NA 18,872.0 48,780.0 67,652.0 17,223.0 84,875.0 84,875.0
    <GEOG_CITY: Melbourne>          NA 22,000.0       NA       NA       NA 22,000.0 22,000.0 22,000.0
    <GEOG_CITY: Perth>              NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: ACT>         11,592.0       NA 38,356.0 3,444.00 41,800.0 11,592.0 53,392.0 53,392.0
    <GEOG_STATE: NSW>               NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: NT>          24,868.0       NA 22,104.0 32,667.0 54,771.0 24,868.0 79,639.0 79,639.0
    <GEOG_STATE: QLD>         49,556.0       NA 48,239.0 24,285.0 72,524.0 49,556.0  122,080  122,080
    <GEOG_STATE: SA>                NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_STATE: TAS>         17,223.0       NA 18,872.0 48,780.0 67,652.0 17,223.0 84,875.0 84,875.0
    <GEOG_STATE: VIC>               NA 22,000.0       NA       NA       NA 22,000.0 22,000.0 22,000.0
    <GEOG_STATE: WA>                NA       NA       NA       NA       NA       NA       NA       NA
    <GEOG_AREA: Aust State>   66,779.0 22,000.0 67,111.0 73,065.0  140,176 88,779.0  228,955  228,955
    <GEOG_AREA: Aust Terr>    36,460.0       NA 60,460.0 36,111.0 96,571.0 36,460.0  133,031  133,031
    <GEOG_CONT: Australia>     103,239 22,000.0  127,571  109,176  236,747  125,239  361,986  361,986

However, because the `sales_dims_comp_comp` variable is dimensioned by a compressed composite not all of values in all of the cells are stored in the variable. The 65 cells that display as `NA` values are not stored in variable, Also, the values that are "passed up" the hierarchy are stored only once — at the lowest level of the hierarchy.

You can confirm the number of physical values stored in the workspace by issuing the following statement that calls the OBJ function with the NUMVALS keyword on `sales_dims_comp_composite`.

    SHOW OBJ(NUMVALS 'sales_dims_comp_composite')
    38.00

The result of the statement is that the value `38.00 `displays which indicates that only 38 values are stored as part of the `sales_dims_comp_composite` variable. These values are shown in the following table.

| GEOG                  | PROD_UPC:ColorTV | PROD_UPC:BWTV | PROD_UPC:StandVCR | PROD_UPC:StrVCR | PROD_FAMILY: VCR | PROD_FAMILY: TV | PROD_DIV: VideoDiv |
|:----------------------|:-----------------|:--------------|:------------------|:----------------|:-----------------|:----------------|:-------------------|
| GEOG_CITY: Canberra   | 11,592.0         |               | 38,356.0          | 3,444.00        | 41,800.0         |                 | 53,392.0           |
| GEOG_CITY: Darwin     | 24,868.0         |               | 22,104.0          | 32,667.0        | 54,771.0         |                 | 79,639.0           |
| GEOG_CITY: Brisbane   | 49,556.0         |               | 48,239.0          | 24,285.0        | 72,524.0         |                 | 122,080            |
| GEOG_CITY: Hobart     | 17,223.0         |               | 18,872.0          | 48,780.0        | 67,652.0         |                 | 84,875.0           |
| GEOG_CITY: Melbourne  |                  | 22,000.0      |                   |                 |                  |                 |                    |
| GEOG_AREA: Aust State | 66,779.0         |               | 67,111.0          | 73,065.0        | 140,176          | 88,779.0        | 228,955            |
| GEOG_AREA: Aust Terr  | 36,460.0         |               | 60,460.0          | 36,111.0        | 96,571.0         |                 | 133,031            |
| GEOG_Cont: Australia  | 103,239          |               | 127,57            | 109,176         | 236,747          | 125,239         | 361,986            |

Example 9-101 Defining a Variable with Partitions

Assume that you want to define a `sales` variable that is dimensioned by product and time and that is partitioned so that each year's data is in a separate partition.

Assume that the analytic workspace contains a `products` dimension, a `time` dimension that is a simple hierarchical dimension with three levels of data (day, month, and year), and a `time_parentrel` relation that represents the child-parent relationships between the values of time.

    DEFINE TIME DIMENSION TEXT
    DEFINE PRODUCT DIMENSION TEXT
    DEFINE TIME_PARENTREL RELATION TIME <TIME>

For simplicity's sake, in this example the `time` and `product` dimensions are only partially populated and have only the following values.

    TIME
    --------------
    2003
    2002
    Dec2003
    Jan2003
    Dec2002
    Jan2002
    31Dec2003
    01Dec2003
    31Jan2003
    01Jan2003
    31Dec2002
    01Dec2002
    31Jan2002
    01Jan2002

    PRODUCT
    -------
    00001
    00002

To create the partitioned variable, take the following steps:

1.  Define a partition template that defines one partition for each year's data.

        DEFINE partition_sales_by_year PARTITION TEMPLATE <time product> -
        PARTITION BY LIST (time)(-
        PARTITION time_2003 VALUES ('2003', 'Dec2003', 'Jan2003', '31Dec2003', '01Dec2003', '31Jan2003', '01Jan2003') <time product>-
        PARTITION time_2002 VALUES ('2002', 'Dec2002', 'Jan2002', '31Dec2002', '01Dec2002', '31Jan2002', '01Jan2002') <time product>)

    (note that for simplicity's sake, only some of each year's dimension values are specified for each partition in this example. Typically, when you want to specify a large number of values for a partition, you do not do so within the DEFINE PARTITION STATEMENT statement. Instead, you define the partition without specifying any values, and then later specify the values using [MAINTAIN ADD TO PARTITION](olap-dml-commands-h-z.md) or [MAINTAIN MOVE TO PARTITION](olap-dml-commands-h-z.md) statements as illustrated in [Example 10-53](olap-dml-commands-h-z.md).)

2.  Define a partitioned `sales` variable with the partitions defined by the partition template named `partition_sales_by_year`.

        DEFINE sales DECIMAL <partition_sales_by_year<time product>>

3.  After you populate sales with day values, you can issue the following REPORT statement to see which `sales` values are in which partition.

        REPORT DOWN PARTITION(partition_sales_by_year) time product sales

        PARTITION(PARTITION_SALES_BY_YEAR)     TIME     PRODUCT     SALES
        ----------------------------------- ---------- ---------- ----------
        TIME_2003                           2003       00001              NA
        TIME_2003                           Dec2003    00001              NA
        TIME_2003                           Jan2003    00001              NA
        TIME_2003                           31Dec2003  00001           14.78
        TIME_2003                           01Dec2003  00001           15.52
        TIME_2003                           31Jan2003  00001           13.61
        TIME_2003                           01Jan2003  00001           10.39
        TIME_2003                           2003       00002              NA
        TIME_2003                           Dec2003    00002              NA
        TIME_2003                           Jan2003    00002              NA
        TIME_2003                           31Dec2003  00002           16.05
        TIME_2003                           01Dec2003  00002           12.27
        TIME_2003                           31Jan2003  00002           10.83
        TIME_2003                           01Jan2003  00002           11.07
        TIME_2002                           2002       00001              NA
        TIME_2002                           Dec2002    00001              NA
        TIME_2002                           Jan2002    00001              NA
        TIME_2002                           31Dec2002  00001           18.80
        TIME_2002                           01Dec2002  00001           13.64
        TIME_2002                           31Jan2002  00001           12.41
        TIME_2002                           01Jan2002  00001           16.97
        TIME_2002                           2002       00002              NA
        TIME_2002                           Dec2002    00002              NA
        TIME_2002                           Jan2002    00002              NA
        TIME_2002                           31Dec2002  00002           17.47
        TIME_2002                           01Dec2002  00002           16.58
        TIME_2002                           31Jan2002  00002           18.94
        TIME_2002                           01Jan2002  00002           18.36

Example 9-102 Defining a Fixed-Width TEXT Variable

The following statement defines a TEXT variable named `lastname` dimensioned by `employee`. Values in `lastname` are limited to 20 characters, so that longer values are truncated.

    DEFINE lastname TEXT <employee> WIDTH 20

Example 9-103 Defining a Variable That Uses a Named B-Tree Composite

Assume that you have the following dimensions in your analytic workspace.

    DEFINE month DIMENSION TEXT
    DEFINE product DIMENSION TEXT
    DEFINE region DIMENSION TEXT

When your company does promotional marketing for certain products in some but not all regions, then your variable data is sparse along the `product` and `region` dimensions. Therefore, suppose you define a composite named `proddist`, whose base dimensions are `product` and `region`. There are dimension-value combinations in the composite only for those values that have data. For example, when you run a promotion for tents but not skis, then the composite includes the tents and region combinations, but not the skis and region combinations.

The following statement creates a b-tree composite named `proddist` whose base dimensions are `product` and `district`, and a variable called `promo` that is dimensioned by `month` and `proddist`.

    DEFINE proddist COMPOSITE <product region>
    DEFINE promo VARIABLE INTEGER <month proddist <product district>>

For simplicity's sake assume that you have only stored the following dimension data in your analytic workspace.

    PRODUCT
    --------------
    Tents
    Skis

    REGION
    --------------
    Northeast
    Southwest

    MONTH
    --------------
    Jan2003
    Feb2003
    Mar2003
    Apr2003
    May2003
    Jun2003
    Jul2003
    Aug2003
    Sep2003
    Oct2003
    Nov2003
    Dec2003

You decide to run a promotional sales for skis in the Northeast region in the month of September, 2003 at a cost of \$5,000. Once you populate `promo` with this, `promo` contains only 12 cells—each cell is dimensioned by a value of `month` and the composite tuple value of `<'Skis' 'Northeast'>` for `proddist`. The cell for September 2003 contains the value \$5,000, and all of the other cells contain `NA`. No other NA values are stored in promo; no cells are created for any other values of `product` or `region`.

Example 9-104 Defining a Variable with Null Tracking

Assume that you have the following objects defined in your analytic workspace.

    DEFINE GEOG DIMENSION TEXT
    LD A dimension with a simple hierarchy for geography

    DEFINE geog_levellist DIMENSION TEXT
    LD List of Levels in in the hierarchy of the geog dimension

    DEFINE GEOG_PARENTREL RELATION GEOG <GEOG>
    LD Self-relation for geog showing parents of each value in the hierarchy

    DEFINE GEOG_LEVELREL RELATION GEOG_LEVELLIST <GEOG>
    LD Level of each dimension member for geog

    DEFINE product DIMENSION TEXT
    LD A nonhierarchical dimension

    DEFINE time DIMENSION TEXT
    LD A hierarchical text dimension for time

    DEFINE time_levellist DIMENSION TEXT
    LD List of Levels in hierarchy of the time dimension

    DEFINE time_parentrel RELATION time <time>
    LD A self-relation for time show parents of each value in the hierarchy

    DEFINE TIME_LEVELREL RELATION TIME_LEVELLIST <TIME>
    LD Level of each dimension member for time

    DEFINE prod_geog COMPOSITE <product geog> COMPRESSED

Now assume that you define a `sales` variable that you want to have dimensioned by `time` and the `prod_geog` composite. You want this variable to have null tracking because you eventually populate it using SQL IMPORT and you know that some facts in the fact table have null values. To do this you issue the following statement that includes the WITH NULLTRACKING phrase.

    DEFINE sales VARIABLE DECIMAL <time prod_geog<product geog>> WITH NULLTRACKING

For testing purposes, you populate the variable using the RANDOM function. After you populate the variable in this way, you issue a report on it that shows the NA values in the variable.

    REPORT DOWN time ACROSS geog: sales

    PRODUCT: TVs
                   -----------------------SALES-----------------------
                   -----------------------GEOG------------------------
    TIME              Boston    Springfield    Hartford    All Places
    -------------- ------------ ------------ ------------ ------------
    2007                     NA           NA           NA           NA
    2008                     NA           NA           NA           NA
    All years                NA           NA           NA           NA
    Jan07                    NA           NA           NA           NA
    Feb07                    NA           NA           NA           NA
    Mar07                    NA           NA           NA           NA
    Apr07                    NA           NA           NA           NA
    May07                    NA           NA           NA           NA
    Jun07                    NA           NA           NA           NA
    Jul07                    NA           NA           NA           NA
    Aug07                    NA           NA           NA           NA
    Sep07                    NA           NA           NA           NA
    Oct07                    NA           NA           NA           NA
    Nov07                    NA           NA           NA           NA
    Dec07                    NA           NA           NA           NA
    Jan08                    NA           NA           NA           NA
    Feb08                    NA           NA           NA           NA
    Mar08                    NA           NA           NA           NA
    Apr08                    NA           NA           NA           NA
    May08                    NA           NA           NA           NA
    Jun08                    NA           NA           NA           NA
    Jul08                    NA           NA           NA           NA
    Aug08                    NA           NA           NA           NA
    Sep08                    NA           NA           NA           NA
    Oct08                    NA           NA           NA           NA
    Nov08                    NA           NA           NA           NA
    Dec08                    NA           NA           NA           NA

    PRODUCT: Radios
                   -----------------------SALES-----------------------
                   -----------------------GEOG------------------------
    TIME              Boston    Springfield    Hartford    All Places
    -------------- ------------ ------------ ------------ ------------
    2007                     NA           NA           NA           NA
    2008                     NA           NA           NA           NA
    All years                NA           NA           NA           NA
    Jan07                 24.59        23.70        33.12        28.65
    Feb07                 22.78        21.42        26.28        37.06
    Mar07                 25.74        32.08        22.75        24.62
    Apr07                 22.23        23.21        20.79        28.68
    May07                 20.51        29.71        30.35        33.05
    Jun07                 34.43        35.96        33.85        39.34
    Jul07                 24.86        38.02        36.78        31.22
    Aug07                 39.05        21.08        35.80        33.81
    Sep07                 34.38        21.69        25.04        33.40
    Oct07                 33.82        39.27        20.28        24.39
    Nov07                 25.48        23.03        32.45        39.94
    Dec07                 25.14        30.66        33.75        23.37
    Jan08                    NA           NA           NA           NA
    Feb08                    NA           NA           NA           NA
    Mar08                    NA           NA           NA           NA
    Apr08                    NA           NA           NA           NA
    May08                    NA           NA           NA           NA
    Jun08                    NA           NA           NA           NA
    Jul08                    NA           NA           NA           NA
    Aug08                    NA           NA           NA           NA
    Sep08                    NA           NA           NA           NA
    Oct08                    NA           NA           NA           NA
    Nov08                    NA           NA           NA           NA
    Dec08                    NA           NA           NA           NA

For testing purposes, you also generate a report using the NAFLAG function to retrieve the type of NAs that are in the variable. As the following report shows, because it was populated using RANDOM, all of the NAs are the typical NA values; they are not NA2 values.

    REPORT DOWN time ACROSS geog: NAFLAG(sales)

    PRODUCT: TVs
                   -------------------NAFLAG(SALES)-------------------
                   -----------------------GEOG------------------------
    TIME              Boston    Springfield    Hartford    All Places
    -------------- ------------ ------------ ------------ ------------
    2007                      1            1            1            1
    2008                      1            1            1            1
    All years                 1            1            1            1
    Jan07                     1            1            1            1
    Feb07                     1            1            1            1
    Mar07                     1            1            1            1
    Apr07                     1            1            1            1
    May07                     1            1            1            1
    Jun07                     1            1            1            1
    Jul07                     1            1            1            1
    Aug07                     1            1            1            1
    Sep07                     1            1            1            1
    Oct07                     1            1            1            1
    Nov07                     1            1            1            1
    Dec07                     1            1            1            1
    Jan08                     1            1            1            1
    Feb08                     1            1            1            1
    Mar08                     1            1            1            1
    Apr08                     1            1            1            1
    May08                     1            1            1            1
    Jun08                     1            1            1            1
    Jul08                     1            1            1            1
    Aug08                     1            1            1            1
    Sep08                     1            1            1            1
    Oct08                     1            1            1            1
    Nov08                     1            1            1            1
    Dec08                     1            1            1            1

    PRODUCT: Radios
                   -------------------NAFLAG(SALES)-------------------
                   -----------------------GEOG------------------------
    TIME              Boston    Springfield    Hartford    All Places
    -------------- ------------ ------------ ------------ ------------
    2007                      1            1            1            1
    2008                      1            1            1            1
    All years                 1            1            1            1
    Jan07                     0            0            0            0
    Feb07                     0            0            0            0
    Mar07                     0            0            0            0
    Apr07                     0            0            0            0
    May07                     0            0            0            0
    Jun07                     0            0            0            0
    Jul07                     0            0            0            0
    Aug07                     0            0            0            0
    Sep07                     0            0            0            0
    Oct07                     0            0            0            0
    Nov07                     0            0            0            0
    Dec07                     0            0            0            0
    Jan08                     1            1            1            1
    Feb08                     1            1            1            1
    Mar08                     1            1            1            1
    Apr08                     1            1            1            1
    May08                     1            1            1            1
    Jun08                     1            1            1            1
    Jul08                     1            1            1            1
    Aug08                     1            1            1            1
    Sep08                     1            1            1            1
    Oct08                     1            1            1            1
    Nov08                     1            1            1            1
    Dec08                     1            1            1            1

Again, for testing purposes, you use the NA function to set an NA2 bit on the variable cells dimensioned by the months of 2008. The following code shows the result of issuing a SHOW of the NA2 function and using that function to set the NA2 bit on the cells dimensioned by the months in 2008.

    SHOW NA2
    NA

    LIMIT time TO 'Jan08' 'Feb08' 'Mar08' 'Apr08' 'May08' 'Jun08' 'Jul08' 'Aug08' 'Sep08' 'Oct08' 'Nov08' 'Dec08'

    saleswithnull= NA2


For brevity's sake assume that your test now issues the following three LIMIT statements and then reports on the sales variable and the NAFLAG function against the sales variable. As the NAFLAG report illustrate, the value `Jan08` which is a month to which an NA2 value was assigned returns the value of `2` for NAFLAG, while the NAFLAG report still returns the value of `1` for the year `2008`.

    LIMIT product to 'Radios'
    LIMIT time TO 'Jan08' '2008'
    LIMIT geog TO 'Boston' 'All Places'

    REPORT DOWN time ACROSS geog: sales

    PRODUCT: Radios
                   ----------SALES----------
                   ----------GEOG-----------
    TIME              Boston     All Places
    -------------- ------------ ------------
    Jan08                    NA           NA
    2008                     NA           NA

    REPORT DOWN time ACROSS geog: NAFLAG(sales)


    PRODUCT: Radios
                   ------NAFLAG(SALES)------
                   ----------GEOG-----------
    TIME              Boston     All Places
    -------------- ------------ ------------
    Jan08                     2            2
    2008                      1            1

Now assume that you issue the following code to remove the NA2 bits from the sales variable.

    CHGDFN sales DROP NULLTRACKING

A DESCRIBE of the sales variable shows that it no longer has the WITH NULLTRACKING phrase in its definition while a report of the results of NAFLAG show that the NA values are now just the typical NA values without an NA2 bit.

    DESCRIBE sales

    DEFINE SALES VARIABLE DECIMAL <TIME PROD_GEOG <PRODUCT GEOG>>

    REPORT DOWN time ACROSS geog: sales

    PRODUCT: Radios
                   ----------SALES----------
                   ----------GEOG-----------
    TIME              Boston     All Places
    -------------- ------------ ------------
    Jan08                    NA           NA
    2008                     NA           NA

    "Report on the type of NA values in the sales variable
    REPORT DOWN time ACROSS geog: NAFLAG(sales)

    PRODUCT: Radios
                   ------NAFLAG(SALES)------
                   ----------GEOG-----------
    TIME              Boston     All Places
    -------------- ------------ ------------
    Jan08                     1            1
    2008                      1            1

#### 9.35.12 DEFINE WORKSHEET

The DEFINE command with the WORKSHEET keyword adds a new worksheet object to an analytic workspace. A worksheet, like a spreadsheet, is a two-dimensional object that is dimensioned by a worksheet row and a worksheet column. It can temporarily store data that you want to transfer between spreadsheet packages and workspace dimensions and variables.

When you first define a worksheet, it does not contain any values. You can populate a worksheet with values from an existing spreadsheet by using an [IMPORT (spreadsheet)](olap-dml-commands-h-z.md) statement or add or delete values from worksheet row and a worksheet column dimensions with a MAINTAIN statement.

##### Syntax

DEFINE name WORKSHEET \[\<column-dim row-dim\>\] \[TEMP\] \[AW workspace\] \[SESSION\]

##### Parameters

name
The name of the object you are defining. For general information about this argument, see the main entry for the DEFINE command.

WORKSHEET
The object type when you are defining a worksheet.

\<column-dim row-dim\>
The names of the dimensions of the worksheet. When you supply this argument, you must give the names of two `INTEGER` dimensions for column-dim and row-dim. When you omit this argument, the worksheet is dimensioned automatically by `WKSCOL` and `WKSROW`. See "Worksheet Dimensions" for more information.

TEMP
Indicates that the worksheet is only temporary. The worksheet is defined in the specified workspace and can contain values during the current session. However, when you update and commit, only the definition of the worksheet is saved. When you end your session or switch to another workspace, the data values are discarded.

AW workspace
The name of an attached workspace in which you want to define the worksheet. The worksheet must be defined in the same workspace as its dimensions. For general information about this argument, see the main entry for the DEFINE command.

SESSION
Specifies that the object exists only in the current session. When the session ends, the object no longer exists. The behavior specified by SESSION is different than the behavior specified by the TEMP keyword which is that the values are temporary but the object definition remains in the workspace in which you create it.

##### Usage Notes

Worksheet Dimensions

A worksheet must always be dimensioned by two dimensions that represent a worksheet row and a worksheet column. The worksheet row and worksheet column dimensions can either be automatically created by Oracle OLAP or explicitly created by you:

- If you have not created worksheet row and worksheet column dimensions and specified their names in the column-dim and row-dim arguments of DEFINE WORKSHEET, then Oracle OLAP automatically creates the following dimensions:

  - For the worksheet row, an INTEGER dimension named `WKSROW` with values from 1 to 63.

  - For the worksheet column, an INTEGER dimension named `WKSROW` with values from 1 to 63.

  **Note:**

  When `WKSCOL` and `WKSROW` already exist in any attached workspace, Oracle OLAP cannot create them in the current worksheet. In this case, the DEFINE WORKSHEET command fails to create a worksheet with these default dimensions. (Note, also, that `WKSCOL` and `WKSROW` do not appear in a worksheet description generated using DESCRIBE.)

- You create worksheet row and a worksheet column dimensions the same way you create any other simple dimension by issuing the following statements:

  1.  Create two simple INTEGER dimensions using a DEFINE DIMENSION (simple) statement. One dimension is for row numbers and the other is for column numbers.

  2.  Using MAINTAIN statements, populate one dimension with integers that represent row numbers and populate the other with integers that represent column numbers.

##### Examples

Example 9-105 Defining a Worksheet

These statements define a temporary worksheet named `travelexp`, which is dimensioned by `columns` and `rows`.

    DEFINE itemsheet WORKSHEET
    DEFINE columns INT DIMENSION
    MAINTAIN columns ADD 5
    DEFINE rows INT DIMENSION
    MAINTAIN rows ADD 10
    DEFINE travelexp WORKSHEET <columns rows> TEMPORARY

Example 9-106 Importing Spreadsheet Data

You can import data from a spreadsheet to a worksheet. When all the cells contain the same type of data, you can use UNRAVEL to transfer the data to a variable with one statement. You can also limit the worksheet dimensions to a smaller group of cells and use UNRAVEL to transfer each group to a separate variable. To transfer imported data from a worksheet named `itemsheet` to a variable named `items`, you might use the following statements.

    DEFINE itemsheet WORKSHEET
    IMPORT itemsheet FROM dif FILE 'file name'
    LIMIT WKSCOL TO FIRST 3
    LIMIT WKSROW TO FIRST 10
    items = UNRAVEL(itemsheet)

### 9.36 DELETE

The DELETE command deletes one or more objects from an analytic workspace. The deletion becomes permanent when you execute UPDATE and COMMIT statements.

Before you delete an object, you must first delete all of its associated objects. For example, before you can delete a dimension, you must first delete any variables dimensioned by it. Also, you cannot delete an object when a PERMIT statement denies you the right to change its permission.

**Tip:**

When you see an error message when you try to delete an object, then the name of that object might be a reserved word. (Use RESERVED to identify reserved words.) When this is the case, use a RENAME statement to give the object a new name, and then delete it.

#### Syntax

DELETE name... \[AW workspace\]

#### Parameters

name...
The names of one or more objects, separated by spaces or commas. DELETE removes the definitions of these objects from the appropriate workspace.

You can specify a qualified object name or use the AW argument to indicate the attached workspace in which each object can be found. Do not use both qualified object names and the AW argument in the same DELETE command.

**Note:**

Oracle OLAP does not warn you when you delete an object that has the same name as an existing object in another attached workspace. Also, when the NAME dimension is limited to less than all its values, DELETE automatically sets the status of NAME to ALL

AW workspace
The name of an attached workspace in which you want to delete all the specified objects. When you do not use a qualified object name or the AW argument to specify an analytic workspace, objects are deleted in the current workspace.

#### Examples

Example 9-107 Deleting a Dimension

Suppose you have a dimension named `city` and a variable named `population` that you want to delete. The variable `population` is the only object that is dimensioned by or makes use of `city`, so you can delete them both in a single DELETE command when you place the variable before the dimension.

    DELETE population city

Placing `city` before `population` in the preceding statement would produce an error.

### 9.37 DESCRIBE

The DESCRIBE command produces a report that shows the definition of one or more workspace objects. An object definition that you see in the output from a DESCRIBE command might include a description (LD), a value name format (VNF) for a time dimension, an expression associated with a FORMULA, permission specified a PERMIT statements, or the contents of a calculation specification (for example, the contents of a program). You can use DESCRIBE to show the definition of an object even when you do not have permission to access the object or to change its permission. Some parts of some object definitions are not reported on as described in "What's Not in the Report Output by DESCRIBE".

#### Syntax

DESCRIBE \[names\]

#### Parameters

names
The names of one or more workspace objects, separated by spaces or commas. When you omit this argument, DESCRIBE shows the definition of all objects in the current status of the NAME dimension. Consequently, when you omit this argument you can use a LIMIT command in combination with DESCRIBE to report the definitions of a particular group of objects in your workspace, as illustrated in Example 9-109.

#### Usage Notes

What's Not in the Report Output by DESCRIBE

Some parts of the object definitions do not appear in the output of DESCRIBE:

- When a PERMIT statement denies you the right to change the permission of an object, DESCRIBE does not include the permission associated with the definition of the object.

- For a worksheet definition, the DESCRIBE report does not include the default dimensions, `WKSCOL` and `WKSROW`. However, it does include user-defined dimensions when they have been used to define a worksheet. See Example 9-110.

- Properties and triggers associated with objects are not displayed. To see the properties and triggers associated with an object, you must use the FULLDSC program.

- When you define a composite or conjoint has the default index type, that information is not displayed.

- Dimensioned BOOLEAN variables that are in older 1 or 2 byte formats are listed as WIDTH 1 and WIDTH 2. The width of BOOLEAN variables created in single-bit format is not listed.

Creating Objects with DESCRIBE Output

You can use the output from the DESCRIBE command to create objects in other workspaces, because each line of the output is a valid statement. For example, you can execute an OUTFILE statement to send subsequent output to a file, and then execute a DESCRIBE command. You can then access another workspace and use an INFILE statement to read the DESCRIBE output. The same object is created in that workspace.

#### Examples

Example 9-108 Describing Variables

This example produces a report of the definitions of the two variables, `sales` and `price`. The statement

    DESCRIBE sales price

produces the following output.

    DEFINE SALES VARIABLE DECIMAL <MONTH PRODUCT DISTRICT>
    LD Sales Revenue
    DEFINE PRICE VARIABLE DECIMAL <MONTH PRODUCT>
    LD Wholesale Unit Selling Price

Example 9-109 Describing All Relations

Suppose you want to look at the definitions of all the relations in your workspace. First limit the NAME dimension, using the OBJ function. After limiting NAME, use DESCRIBE with no arguments to produce a report of the definitions. The following statements produce a description of the relations in the analytic workspace.

    LIMIT NAME TO OBJ(TYPE) EQ 'RELATION'
    DESCRIBE

    DEFINE REGION.DISTRICT RELATION REGION <DISTRICT>
    LD REGION for each DISTRICT 
    DEFINE DIVISION.PRODUCT RELATION DIVISION <PRODUCT>
    LD DIVISION for each PRODUCT 
    DEFINE MLV.MARKET RELATION MARKETLEVEL <MARKET>
    DEFINE MARKET.MARKET RELATION MARKET <MARKET> 
    LD Self-relation for the Market Dimension

Because the values returned by OBJ(TYPE) are always in uppercase, you have to use 'RELATION' rather than 'relation' in your LIMIT command to obtain a match.

Example 9-110 Describing a Worksheet

The dimensions of a worksheet appear in the description only when they are user-defined dimensions. The default dimensions `WKSCOL` and `WKSROW` are not included in the description. The statements

    DEFINE work1 WORKSHEET
    DEFINE columns DIMENSION INTEGER
    DEFINE rows DIMENSION INTEGER
    DEFINE work2 WORKSHEET <columns rows>
    DESCRIBE work1 work2

produce the following output.

    DEFINE WORK1 WORKSHEET
    DEFINE WORK2 WORKSHEET <COLUMNS ROWS>

### 9.38 DO ... DOEND

Within an OLAP DML program, the DO and DOEND commands bracket a group of one or more statements in a program. DO and DOEND are normally used to bracket one of the following:

- A group of statements that are to be executed under a condition specified by an IF command

- A group of statements in a repeating loop introduced by FOR or WHILE

- The CASE labels for a SWITCH command.

You can put one DO statement inside another to nest groups of statements. You can nest as many groups as you want, if each DO statement has a corresponding DOEND to indicate the end of its statement group.

#### Syntax

DO      statement1      ...      statementN DOEND

#### Parameters

statement
One or more OLAP DML statements, user-defined programs, or both.

#### Usage Notes

TEMPSTAT Statement and DOEND Statement

Within a FOR loop of a program, when a DO/DOEND phrase follows TEMPSTAT, status is restored when the DOEND, BREAK, or GOTO is encountered.

#### Examples

Example 9-111 DO and DOEND with the FOR Statement

Suppose you want to use the ROW command to produce a report that shows the unit sales of tents for each of 2 months. Use DO ... DOEND to bracket the ROW and BLANK statements you want to execute repeatedly for each value of the `month` dimension. You might write the following program.

    LIMIT month TO 'Jan96' to 'Feb96'
    ROW district
    ROW UNDER '-' VALONLY name.product
    FOR month
        DO
          ROW INDENT 5 month WIDTH 6 UNITS
          BLANK
        DOEND

The program produces the following output.

    BOSTON
    3-Person Tents
    --------------
         Jan96              307
         Feb96              209

### 9.39 EDIT

The EDIT command displays an OLAP Worksheet Edit window. The command is available only when you are using OLAP Worksheet to access Oracle OLAP.

For information about using an OLAP Worksheet Edit window, see the OLAP Worksheet Help.

#### Syntax

EDIT {PROGRAM\|MODEL\|AGGMAP\|FORMULA} object-name

#### Parameters

PROGRAM
MODEL
AGGMAP
FORMULA
Indicates whether the object to be edited is a program, a model, an aggmap, or a formula.

object-name
A text expression that specifies the name of an existing program, model, aggmap, or formula. Before editing one of these objects, use a DEFINE statement to create it in an analytic workspace.

#### Usage Notes

Editing a Newly Defined Aggmap to Code an Allocation Specification

When an aggmap is first defined it does not have any contents and its type is `NA`. When you use the EDIT command for an aggmap whose type has not yet been specified, OLAP Worksheet automatically makes the aggmap an aggregation specification by inserting an AGGMAP statement into the contents of the aggmap.

Consequently, when you plan to use an aggmap as an allocation specification, use the following statements to identify it as an allocation specification before the first time you open an OLAP Worksheet Edit window for it.

         CONSIDER aggmap-name
         ALLOCMAP 'END'

#### Examples

Example 9-112 Editing a Program

The following statement, executed in the OLAP Worksheet, places the `myprog` program in an OLAP Worksheet EDIT window.

    EDIT myprog

Example 9-113 Editing a Model

The following statement, executed in the OLAP Worksheet, places a model called `myModel` in an OLAP Worksheet Edit window.

    EDIT MODEL myModel

### 9.40 EQ

The EQ command specifies a new expression for an already defined formula. To use EQ to assign an expression to a formula definition, the definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER command to make it the current definition.

An alternative to the EQ command is the EDIT FORMULA command, which is available only in OLAP Worksheet. The EDIT FORMULA command opens an Edit window in which you can add, delete, or change the expression to be calculated for a formula.

Be sure to distinguish between the EQ command described here and the EQ operator used to compare values of the same type.

#### Syntax

EQ \[expression\]

#### Parameters

expression
The calculation that is performed to produce values when you use the formula. When you do not specify an expression, the EQ command sets the expression to `NA`. The formula text is not converted to uppercase.

#### Usage Notes

Data Type and Dimensions

Typically, the data type and dimensions of the new expression match the specified data type and dimensions in the definition of the formula. When they do not, the resulting values are converted to the formula's data type and the results are forced into the formula's dimensionality. The DESCRIBE command shows the formula's data type and dimensions. You can find out the data type and dimensions of the new expression by parsing it. See Example 9-115.

You cannot use the EQ command to change the data type or dimensions of a formula. To make changes in these, you must delete the formula and redefine it.

#### Examples

Example 9-114 Adding an EQ

This example specifies a new expression for the `f1` formula with the following definition.

    DEFINE f1 FORMULA INTEGER <month line division>
    EQ actual * 2

The statements

    CONSIDER f1
    EQ actual * 3
    DESCRIBE f1

produce the following definition of the formula with a new EQ.

    DEFINE F1 FORMULA INTEGER <MONTH LINE DIVISION>
    EQ actual * 3

Example 9-115 Using PARSE with EQ

The following example supposes that your workspace already has a formula named `line.totals`. The PARSE and SHOW INFO statements check the dimensionality and data type of an expression. The CONSIDER and EQ statements assign the expression to the `line.totals` formula. The `line.totals` formulas has the following definition.

    DEFINE line.totals FORMULA DECIMAL <year line>

The statements

    PARSE 'total(actual line year)'
    SHOW INFO(PARSE DIMENSION)

produce the following output.

    YEAR
    LINE

The statement

    SHOW INFO(PARSE DATA)

produces the following output.

    DECIMAL

The output from INFO(PARSE) shows that the expression has the same dimensionality and data type as the `line.totals` formula. The statements

    CONSIDER line.totals
    EQ TOTAL(actual line year)
    DESCRIBE line.totals

show the definition of `line.totals` with its new EQ.

    DEFINE LINE.TOTALS FORMULA DECIMAL <YEAR LINE>
    EQ total(actual line year)

### 9.41 EXPORT

The EXPORT command copies workspace objects from your analytic workspace to an external file. You can use EXPORT to copy both data and object definitions from your workspace to an EIF file, or you can use it to copy an OLAP DML worksheet object to a spreadsheet file.

Because the syntax of the EXPORT command is different depending on whether it is being used to produce an EIF file or a spreadsheet file, two separate entries are provided:

- EXPORT (EIF))

- EXPORT (spreadsheet)

#### 9.41.1 EXPORT (EIF)

The EXPORT (to EIF) command copies data and definitions from your Oracle OLAP analytic workspace to an EIF file. EXPORT also copies all dimensions of the exported data, even when you do not specify them in the command. The status of the data's dimensions in Oracle OLAP determines which values are exported.

**Tip:**

There are several options that determine how EIF files are imported and exported. These options are listed in "[EIF Options](olap-dml-options.md)".

EXPORT (to EIF) is commonly used with [IMPORT (EIF)](olap-dml-commands-h-z.md) to copy one Oracle OLAP workspace to another. You export objects from the source workspace to an EIF file and then import the objects from the EIF file into the target workspace. The source and target workspaces can reside on the same platform or on different platforms.

##### Syntax

EXPORT export_item TO EIF FILE file-name \[LIST\] \[NOPROP\] -      \[NOREWRITE\|REWRITE\] \[FILESIZE n \[K, M, or G\]\] -       \[NOTEMPDATA\] \[NLS_CHARSET charset-exp\] \[AGGREGATE \| NOAGGR\] -      \[API \|  NOAPI\]

where `export_item` is one of the following:

- `     ALL`
- `     ``name ``[AS ``newname``]`
- `     ``exp ``[SCATTER AS ``scattername ``[TYPE ``scattertype``] [EXCLUDING (``concatbasedim ``. . .)]`
- `     ``exp ``AS ``name ``[EXCLUDING (``concatbasedim ``. . .)]`

##### Parameters

ALL
Specifies that Oracle OLAP exports all the objects currently in the status of NAME (and, therefore, not necessarily all objects in the workspace).

**Note:**

When you want to export cube metadata (that is, when the default API keyword is in effect), you must export all of the objects in the workspace (that is, you must specify the ALL keyword for export_item). You cannot export cube metadata when you export only some workspace objects.

name
The name of an analytic workspace object or option to be exported. You can list multiple names for export.

AS newname
Specifies a new name for the analytic workspace object or option. When you specify an expression, or a local variable, or a local valueset, then you must use AS name to provide a name for the object that [IMPORT (EIF)](olap-dml-commands-h-z.md) uses to receive the data

**Note:**

You cannot rename dimensions.

exp
An expression to be computed and exported. You can list multiple names for export.

SCATTER AS scattername \[TYPE scattertype\]
When you want to export a large multidimensional object that may require multiple passes to write into memory, then you can use SCATTER AS scattername to improve file I/O performance. You must first define one or two new single-dimension text variables (scattername and scattertype) and assign text values and their corresponding data types to scattername. When you use SCATTER AS scattername, this tells Oracle OLAP to export the multidimensional expression as separate variables in the slices you have specified in scattername. When each of the slice variables is to have the same data type, you can simply make exp have that data type, in which case you do not have to use TYPE scattertype.

EXCLUDING (concatbasedim  . . .)
The EXCLUDING phrase applies only to a concat dimension that you specify with the name argument. The value you specify for concatbasedim, specifies the base dimensions of the concat that Oracle OLAP does not export.

ALL
Specifies that Oracle OLAP exports all the objects currently in the status of NAME (and, therefore, not necessarily all objects in the workspace).

TO EIF FILE
Indicates that you want to create an EIF file.

file-name
A text expression that is the name of the file to which output should be written. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use the CDA command to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

LIST
Sends to the current outfile the definition of each object as it begins to export it. For dimensions, EXPORT indicates the number of values being exported, and for composites, it lists the number of dimension value combinations. EXPORT also produces a message that shows the total number of bytes read every two minutes and after the export procedure.

NOPROP
Prevents any properties that you have assigned to each object using a PROPERTY from being written to the EIF file.

NOREWRITE
REWRITE
Specifies whether EXPORT overwrites the target file when it already exists. NOREWRITE (the default) leaves an existing target file intact and sends an error message to the current outfile. REWRITE causes EXPORT to replace the existing file with the new EIF file.

FILESIZE n \[K\|M\|G\]
Sets the maximum size of each component file (main file and extension files) for EIF files. When a file's size grows beyond the value of FILESIZE or the current disk or location becomes full, Oracle OLAP creates an EIF extension file. See"EIF Extension Files".

FILESIZE affects component files created after it is set. Previous component files may have various sizes, determined by the FILESIZE setting at the time each one was created or by the size it reached when its disk was full.

When you do not specify `K`, `M`, or `G`, the value you specify for n is interpreted as bytes. When you specify `K`, `M`, or `G` after the value n, the value is interpreted as kilobytes, megabytes, or gigabytes, respectively.

You can set FILESIZE to any value between 81,920 bytes (80K) and 2,147,479,552 bytes (2G).

NOTEMPDATA
Prevents data in TEMP variables from being written to the EIF file.

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when exporting text data to the file specified by file-name which allows Oracle OLAP to convert the data accurately into that character set. This argument must be the last one specified. When this argument is omitted, then Oracle OLAP exports the data in the database character set, which is recorded in the NLS_LANG option.

AGGREGATE
Export aggregated data. (Default behavior.)

NOAGGR
Do not export aggregated data.

API
(Default) Export any cube metadata defined for the specified items.

NOAPI
Do not export any cube metadata defined for the specified items.

##### Usage Notes

Exporting and Importing Between Different Platforms

When you transfer an EIF file between computers, use a binary transfer to overcome file-format incompatibilities between platforms. The EIF file must have been created with the EIFVERSION set to a version that is less than or equal to the version number of the target workspace. See the [EIFVERSION](olap-dml-options.md) option for information about verifying the target version number.

Exporting Relations

When you export a relation, EXPORT exports the definition and the values in status for the related dimension and the dimensions of the relation.

Exporting Conjoint Dimensions

When you export a conjoint dimension, ensure that the status of the base dimensions and the status of the conjoint dimension match. Because there is an implicit relation between conjoint and base dimensions, Oracle OLAP exports the base dimensions with the conjoint dimension, but it cannot export all the conjoint dimension values in the current status when the related base values are not also in status.

Exporting Dimension Surrogates

When you export a dimension surrogate, Oracle OLAP also exports the dimension of the surrogate. For more information, see "[Importing and Exporting Dimension Surrogates](olap-dml-commands-h-z.md)".

Reducing Workspace Size

When you have added and then deleted many objects or dimension values, you might want to use EXPORT (from EIF) with the [IMPORT (EIF)](olap-dml-commands-h-z.md) command to remove extra space from your analytic workspace. You can make your workspace smaller, perhaps substantially so. To do this, use the EXPORT command with the ALL keyword to put all the data in an EIF file, create another workspace with a different name, and then import the EIF file into the new workspace. You can then delete the old workspace and refer to the new one with the same workspace alias that you used for the original one.

Preserving the Type of a Conjoint Dimension

When you export a HASH, BTREE, or NOHASH conjoint dimension to an EIF file, the conjoint type is exported along with its definition in the EIF file. When you then import the conjoint dimension into an analytic workspace, Oracle OLAP preserves the conjoint type when you import into a new dimension or a dimension already using that conjoint type. When you import the dimension into an existing dimension that does not use the same conjoint type, Oracle OLAP does not preserve the original conjoint type that was saved in the EIF file.

Exporting Unnamed Composites

When you export or import an object with an unnamed composite in its definition, the composite is automatically exported or imported with the object. You cannot import or export an unnamed composite independently.

EIF Extension Files

EIF extension file names have the structure filename.ennn, where nnn is a three-digit number beginning with 001. For example, assume you have an EIF file named `export.eif`, the extension files are named `export.e001`, `export.e002`, and so on. You can set the extension to three characters by using the EIFSHORTNAMES option. Extension files are created in the same directory object as the original EIF file, unless you specify a different one with the EIFEXTENSIONPATH option.

Saving SEGWIDTH Setting Information

When you use the SEGWIDTH keyword of the CHGDFN command to specify the length of variable segments, segment information cannot be exported and imported automatically. You can save your SEGWIDTH settings by exporting the entire workspace, creating a new workspace, importing only the workspace objects into the new workspace, specifying segmentation, and then importing the variable data into the new workspace.

Exporting Objects with the Same Name From Two Different Workspaces

When you want to export two objects that have the same name from two different workspaces, you must rename one of them in the EIF file by exporting it with the AS keyword. Objects in an EIF file cannot have duplicate names.

Exporting a PERMIT_READ or PERMIT_WRITE Program

The contents of a [PERMIT_READ](olap-dml-programs.md) or a [PERMIT_WRITE](olap-dml-programs.md) program is emptied when exported. To successfully copy the contents of these programs to and from analytic workspaces, rename them before using EXPORT (to EIF); and then, after using IMPORT (from EIF) to copy them into an analytic workspace, name them back to PERMIT_READ or PERMIT_WRITE.

Exporting TEXT and NTEXT Values

You can export and import TEXT and NTEXT values. Both data types can be exported to a single EIF file.

- Exported TEXT values are stored in the EIF file using the character set specified for the file in the EXPORT command.

- Exported NTEXT values are stored in the EIF file as NTEXT (UTF8 Unicode).

- NTEXT values imported into TEXT objects are converted into the database character set which can result in data loss when the NTEXT values cannot be represented in the database character set.

- TEXT values imported into NTEXT objects are converted into the NTEXT (UTF8 Unicode) character set.

##### Examples

Example 9-116 Exporting Variables

Suppose you want to export the values in status and the dimensions of two variables called `actual` and `budget` from your current Oracle OLAP workspace to a disk file called `finance.eif` in your current directory object. Use the following statement.

    EXPORT actual budget TO EIF FILE 'finance.eif'

Example 9-117 Exporting a Large Object

Suppose you want to export a large, multidimensional object that is likely to require multiple passes to write into memory. To improve file I/O performance, you can create a single-dimension variable to tell Oracle OLAP how to slice the multidimensional variable into smaller pieces. Suppose, also, that the large object is the `sales` variable, which is dimensioned by `month`, `product`, and `district`. To specify how `sales` should be sliced, create a single-dimension variable, as shown in the following statement.

    DEFINE salescatter VARIABLE TEXT <district>

Because `salescatter` is dimensioned by `district`, this tells Oracle OLAP to divide `sales` into `district` slices. Because `district` has six values, `sales` is divided into six slices. Each slice must be named. To do so, assign values to each `district` in `salescatter`. You can then assign the appropriate data type to each slice, for example, by using a QDR (qualified data reference), when desired.

To export SALES, execute the following statement.

    EXPORT sales SCATTER AS salescatter TYPE TYPEVAR TO EIF FILE 'slice.eif'

To import the variables, specify which of the named slices you want, as in the following statement.

    IMPORT dist1 dist2 dist3 dist4 dist5 dist6 FROM EIF FILE 'slice.eif'

Alternatively, you can import all of the variables.

    IMPORT ALL FROM EIF FILE 'slice.eif'

#### 9.41.2 EXPORT (spreadsheet)

The EXPORT (to spreadsheet) command copies an Oracle OLAP worksheet object that you have created to a spreadsheet file and automatically translate it into the appropriate format. An analytic worksheet's dimensions form the columns and rows of the spreadsheet file. The current status of these dimensions determines which part of a worksheet is exported.

You can also export an analytic worksheet to an EIF file as described in EXPORT (EIF). EXPORT (to spreadsheet) is commonly used to copy part of your Oracle OLAP workspace into a file that can be read by other software, such as Lotus 1-2-3, or Symphony.

##### Syntax

EXPORT worksheetname TO {WKS\|WK1\|WRK\|WR1\|DIF} FILE file-name -      \[STATRANK\] \[NOREWRITE\|REWRITE\] \[NLS_CHARSET charset-exp\]

##### Parameters

worksheetname
An Oracle OLAP worksheet object that you have created. In any one EXPORT (to spreadsheet) command, you can export only one worksheetname to one spreadsheet file.

WKS
Indicates that you want to export an Oracle OLAP worksheet to a 1-2-3 file, version 1.

WK1
Indicates that you want to export an Oracle OLAP worksheet to a 1-2-3 file, version 2.

WRK
Indicates that you want to export an Oracle OLAP worksheet to a Symphony file, version 1.0.

WR1
Indicates that you want to export an Oracle OLAP worksheet to a Symphony file, version 1.1.

DIF
Indicates that you want to export an Oracle OLAP worksheet to a data interchange format file.

FILE file-name
FILE specifies the file that you are creating. For file-name, specify a text expression that is the name of the file. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use the CDA command to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

STATRANK
Specifies that the row and column numbers exported with worksheet data should be the current status rankings of the `WKSROW` and `WKSCOL` dimensions.

NOREWRITE
(Default) Specifies that Oracle OLAP does not overwrite the target file when it already exists, but instead displays an error.

REWRITE
Specifies that Oracle OLAP overwrites the target file when it already exists.

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when exporting text data to the worksheet file specified by file-name which allows Oracle OLAP to convert the data accurately into that character set.

For information about the character sets that you can specify, see Oracle Database Globalization Support Guide.

This argument must be the last one specified. When this argument is omitted, then Oracle OLAP exports the data in the database character set, which is recorded in the NLS_LANG option.

##### Examples

Example 9-118 Limiting Before Exporting

This example exports part of a pricing worksheet by limiting its dimensions, `WKSCO`L and `WKSROW`, before the EXPORT command.

    LIMIT WKSCOL TO 2 TO 4
    LIMIT WKSROW TO 3 TO 4
    EXPORT pricing TO WRK FILE 'price1.wrk'

### 9.42 FCCLOSE

The FCCLOSE command closes a forecasting context. When Oracle OLAP closes a forecasting context, only data in the variables specified in the FCEXEC command remain available to applications. Oracle OLAP purges all other data, including temporary pages, associated with the forecast.

You must use the FCCLOSE command in combination with other OLAP DML statements as outlined in "[Forecasting Programs](olap-dml-programs.md)".

#### Syntax

FCCLOSE handle-expression

#### Parameters

handle-expression
An `INTEGER` expression that is the handle to forecast context previously opened using the FCOPEN function.

#### Examples

For an example of a forecasting program, see Example 9-119.

### 9.43 FCEXEC

The FCEXEC command executes a forecast based on the parameters options specified by the FCSET command for the forecast. The FCEXEC command implicitly loops over all the dimensions of the expression other than the time dimension.

You must use the FCEXEC command in combination with other OLAP DML statements as outlined in "[Forecasting Programs](olap-dml-programs.md)".

#### Syntax

FCEXEC handle-expression \[choice\] time-series-expression

where `choice` is one or more of the following:

-      `TIME` `time-dimension`
-      `TRADINGDAYS` `expression`
-      `INTO` `name`
-      `SEASONAL` `name`
-      `SMSEASONAL` `name`
-     ` BACKCAST`

#### Parameters

handle-expression
An `INTEGER` expression that specifies the handle to a forecasting context previously opened using the FCOPEN function.

TIME time-dimension
The name of the time dimension. You do not have to specify this parameter when one dimension of the time-series-expression is of type DAY, WEEK, MONTH, QUARTER, or YEAR.

TRADINGDAYS expression
An `INTEGER` expression that specifies the number of business days in the unit of time of the time data type (that is, DAY, WEEK, MONTH, or YEAR) of the time-series-expression. By default the value is the total number of days in the unit of time.

INTO name
The name of the Oracle OLAP variable in which the forecasting engine stores the forecast data. This variable must be dimensioned by the time dimension and any other dimensions of the time-series-expression that have multiple values in status. (This variable can have additional dimensions. However, in this case, when Oracle OLAP executes the forecast, it limits each of these additional dimensions to the first value in the dimension's status list.).

**Note:**

When you do not specify INTO and the time-series-expression names an Oracle OLAP variable, the forecasting engine populates the input variable with the output data of the forecast, thus overwriting the original data.

SEASONAL name
The name of the variable that the forecasting engine populates with the data that represents seasonal factors.The forecasting engine produces only one cycle of factors and stores these values into this variable beginning with the first time period in status. This variable must be dimensioned by the time dimension and any other dimensions of the time-series-expression that have multiple values in status. (This variable can have additional dimensions. However, in this case, when the forecasting engine executes the forecast, Oracle OLAP limits each of these additional dimensions to the first value in the dimension's status list.)

SMSEASONAL name
The name of the variable that the forecasting engine populates with the data that represents smoothed seasonal factors. The forecasting engine produces only one cycle of factors and stores these values into this variable beginning with the first time period in status; all other values are set to `NA`. This variable must be dimensioned by the time dimension and any other dimensions of the time-series-expression that have multiple values in status. (This variable can have additional dimensions. However, in this case, when the forecasting engine executes the forecast, Oracle OLAP limits each of these additional dimensions to the first value in the dimension's status list.)

BACKCAST
The BACKCAST keyword specifies that the forecasting engine returns fitted historical data. Typically this data is available only for a subset of the historical periods (sometimes called the "fit window"). The forecasting engine sets the value of the data that corresponds to the historical time periods that are outside of the fit window to `NA`.

**Note:**

When you specify a value for BACKCAST and do not specify a value for INTO variable, the forecasting engine populates the source variable with the backcasted data, thus overwriting the original data.

time-series-expression
An expression that specifies the data from which FCEXEC calculates values. The time-series-expression must be a numeric expression that is dimensioned by time-dimension. The time-series-expression may also be dimensioned by other dimensions. In this case, FCEXEC implicitly loops over all the dimensions of the expression other than the time dimension. The maximum status length of the time-series-expression is 5000.

#### Usage Notes

Forecasting a Single Value

The FCEXEC command implicitly loops over all the dimensions of the time-series expression other than the time dimension. When you want to forecast only one value of a multidimensional time-series expression, then you must limit the status of all non-time dimensions to a single value before you execute the FCEXEC command.

#### Examples

Example 9-119 A Forecasting Program

Suppose you define a program named `autofcst` to perform a forecast from the data that is in an input variable named `fcin1`. The `fcin1` variable is dimensioned by a time dimension named `timedim`. Assume that you have defined a program named `autofcst` with the following definition and specification.

    DEFINE autofcst PROGRAM
    PROGRAM
    " Using the Automatic forecasting method 
    " Suppose you want to create a forecast from the data in 
    " an input variable named fcin1 that is dimensionsed by 
    " a time dimension named timedim. 
    "
    " Open a forecasting context
    hndl = FCOPEN('MyForecast')
    " Initialize the target variables
    fcout1 = NA
    fcseas1 = NA
    fcsmseas1 = NA
    " Specify that the forecast be of the AUTOMATIC type
    fcset hndl method 'automatic'
    " Execute the forecast
    FCEXEC hndl time timedim INTO fcout1 -
          seasonal fcseas1 smseasonal fcsmseas1 backcast fcin1
    " Create a report showing the input and output of the forecast
    REPORT DOWN timedim fcin1 fcout1 fcseas1 fcsmseas1
    " Run a program named queryall to retrieve the characteristics 
    " of the forecasting trials 
    QUERYALL
    " Close the forecasting context
    FCCLOSE hndl
    END

The `autofcst` program opens a forecasting context, sets the option of the forecast to AUTOMATIC, reports on the forecasted data, and queries and reports the characteristics of the various trials that Oracle OLAP performed to determine the method to use, and closes the forecasting context.

The `autofcst` program contains the following report command that displays a report of the input to and the output from the forecast.

    REPORT DOWN timedim fcin1 fcout1 fcseas1 fcsmseas1

The sample report created by this statement follows.

    TIMEDIM          FCIN1      FCOUT1    FCSEAS1   FCSMSEAS1
    -------------- ---------- ---------- ---------- ----------
    Jan97                  NA         NA 1.06725482 1.02926773
    Feb97                  NA         NA .978607917 .945762221
    Mar97                  NA         NA 1.12699278 .860505188
    Apr97                  NA         NA .576219022 .905284834
    May97                  NA         NA .920601317 .907019312
    Jun97                  NA         NA 0.91118344  1.0580697
    Jul97                  NA         NA 1.07886483 1.05597234
    Aug97                  NA         NA 1.08101034   1.054612
    Sep97                  NA         NA 1.08077427 1.05361672
    Oct97               2,914         NA 1.08351799 1.05380407
    Nov97               2,500         NA 1.01126778 1.04504316
    Dec97               2,504         NA 1.08370549 1.03104272
    Jan98               3,333         NA         NA         NA
    Feb98               2,512         NA         NA         NA
    Mar98               2,888         NA         NA         NA
    ...                 ...           ...        ...        ...
    Jan01                  NA 3,371.7631         NA         NA
    Feb01                  NA 2,736.4811         NA         NA
    Mar01                  NA 3,408.3656         NA         NA
    Apr01                  NA 714.277175         NA         NA
    May01                  NA 2,502.9315         NA         NA
    Jun01                  NA 3,195.3626         NA         NA
    Jul01                  NA 3,911.6058         NA         NA
    Aug01                  NA  4,000.651         NA         NA
    Sep01                  NA 4,220.2658         NA         NA
    Oct01                  NA 3,416.0208         NA         NA
    Nov01                  NA 2,827.3943         NA         NA
    Dec01                  NA 2,990.8629         NA         NA

The `queryall` program and a sample report created from its output is shown in [Example 7-87](olap-dml-functions-a-k.md).

### 9.44 FCSET

The FCSET command specifies the characteristics that you want the Geneva Forecasting engine to use when executing a forecasting context created using a FCOPEN statement.

You must use a FCSET statement in combination with other OLAP DML statements as outlined in "[Forecasting Programs](olap-dml-programs.md)".

#### Syntax

FCSET handle-expression forecast-characteristic

where` forecast-characteristic` has the following syntax:

-      \[ALLOCLAST {YES\|NO}\]
-      \[ALPHA {MAX\|MIN\|STEP} decimal\]...
-      \[APPROACH {'APPAUTO'\|'APPMANUAL'\]
-      \[BETA {MAX\|MIN\|STEP} decimal\]...
-      \[COMPSMOOTH {YES\|NO}\]
-      \[CYCDECAY {MAX\|MIN} decimal\]...
-      \[GAMMA {MAX\|MIN\|STEP} decimal\]...
-      \[HISTPERIODS integer\]
-      \[MAXFACTOR decimal\]
-      \[METHOD 'method'\]
-      \[MINFCFACTOR decimal\]
-      \[MPTDECAY {MAX\|MIN} decimal\]...
-      \[NTRIALS integer\]
-      \[PERIODICITY cycle-spec\]
-      \[RATIO decimal\]
-      \[SMOOTHING {YES\|NO}\]
-      \[TRANSFORM {'TRNOSEA'\|'TRSEA'\|'TRMPT'}\]
-      \[TRENDHOLD {MAX\|MIN\|STEP} decimal\]...
-      \[WINDOWLEN integer\]

#### Parameters

handle-expression
An `INTEGER` expression that is the handle to forecast context that you want to query and that was previously opened using the FCOPEN function.

ALLOCLAST {NO\|YES}
Indicates whether the forecast engine reduces the risk of over-adjustment by allocating or forecasting the last cycle.

- `NO` specifies that the forecast engine forecasts the last cycle. (Default)

- `YES` specifies that the forecast engine forecasts only the average value for one period of the cycle. That average value is then multiplied by factors to give the remaining points in that period. For example, when the last cycle has 24-hour periods, only an average hourly value is forecast, which is then multiplied by 24 hourly factors to give the value for each hour.

ALPHA {MAX\|MIN\|STEP} decimal
For the single exponential smoothing, double exponential smoothing, and Holt-Winters forecasting methods, specifies the value for Alpha which is the baseline parameter that is used for those methods.

- `ALPHA MAX` `decimal`, specifies the maximum value of Alpha. For decimal, you can specify any decimal value from 0.0 through 1.0. The default value of decimal is 0.3.

- `ALPHA MIN` `decimal` specifies the minimum value of Alpha. For decimal, you can specify any decimal value from 0.0 through 1.0. The default value of decimal is 0.1.

- `ALPHA STEP` `decimal` specifies the value of the interval that the forecasting engine uses when it determines the value of Alpha. For decimal, you can specify any decimal value from 0.05 through 0.2 if the value evenly divides the difference between the values of ALPHA MAX and ALPHA MIN. The default value of decimal is 0.1.

APPROACH {'APPAUTO'\|'APPMANUAL'}
Specifies the approach that the forecasting engine takes when it executes the forecast.

- `'APPAUTO'` is the default approach which invokes the Geneva forecasting expert system which tests all of possible forecasting methods and options for these methods and chooses and uses the method that best fits the data. When you specify this value, the expert system ignores any value that you specify for the METHOD keyword.

  Once the method is chosen, the expert system chooses alpha, beta, gamma, trend hold, cyclical decay and MPT transformation settings from the maximum and minimum settings you code. To set these values for the APPAUTO approach, you specify the same value for both minimum and maximum. For example, to specify a value of `.2` for alpha, set ALPHA MIN to `.2` and ALPHA MAX to `.2`. The expert system uses any other global parameters that you have set. (Default)

- `'APPMANUAL'` indicates that the Geneva Forecasting engine uses the method and options you specify in this FCSET statement when executing the forecast.

BETA {MAX\|MIN\|STEP} decimal
For the double exponential smoothing and Holt-Winters forecasting methods, specifies the value of Beta. Beta is the trend parameter that controls the estimate of the trend.

- `BETA MAX` `decimal` specifies the maximum value of Beta. For decimal, you can specify any decimal value from `0.0` through `1.0`. The default value is `0.3`.

- `BETA MIN` `decimal` specifies the minimum value of Beta. For decimal, you can specify any decimal value from `0.0` through `1.0`. The default value is `0.1`.

- `BETA STEP` `decimal` specifies the value of the interval that the forecasting engine uses when it determines the value of Beta. For decimal, you can specify any decimal value from `0.05` through `0.2` if the value evenly divides the difference between the values of BETA MAX and BETA MIN. The default value of decimal is `0.1`.

COMPSMOOTH {YES\|NO}
Indicates whether optimization should be done on the median smoothed data series.

- `NO` specifies that the methods are done using the original historical time series data. (Default)

- `YES` specifies that optimization is done on the median smoothed data series, which results in more smoothed or "baseline" forecasts.

CYCDECAY {MAX\|MIN} decimal
For linear and nonlinear regression methods, specifies the value of the cyclical decay. Cyclical decay pertains to how seriously the forecasting engine considers deviations from baseline activity when it performs linear and nonlinear regressions.

- `CYCDECAY` `MAX` `decimal`, specifies the maximum value of the cyclical decay parameter. For decimal, you can specify any decimal value from `0.2 `through `1.0` when the difference between the values of CYCDECAY MIN and CYCDECAY MAX is evenly divided by `0.4`. The default value of decimal is `1.0`.

- `CYCDECAY` `MIN` `decimal`, specifies the minimum value of the cyclical decay parameter. For decimal, you can specify any decimal value from 0.2 through 1.0 when the difference between the values of CYCDECAY MIN and CYCDECAY MAX is evenly divided by 0.4. The default value of decimal is 0.2.

GAMMA {MAX\|MIN\|STEP} decimal
For the Holt-Winters forecasting method, specifies the value of Gamma which is the seasonal parameter used by that method.

- `GAMMA MAX` `decimal` specifies the maximum value of Gamma. For decimal, you can specify any decimal value from `0.0` through `1.0`. The default value of decimal is `0.3`.

- `GAMMA MIN` `decimal` specifies the minimum value of Gamma. For decimal, you can specify any decimal value from `0.0` through `1.0`. The default value of decimal is `0.1`.

- `GAMMA STEP` `decimal` specifies the value of the interval that the forecasting engine uses when it determines the value of Gamma. For decimal, you can specify any decimal value from `0.05` through `0.2` when the value evenly divides the difference between the values of GAMMA MAX and GAMMA MIN. The default value of decimal is `0.1`.

HISTPERIODS integer
The number of historical periods. For `integer`, you can specify any `INTEGER` value from `1` through `50000`, which is the maximum number of time dimension values that can be present in the time-series expression specified in the FCEXEC command. (Note that the number of forecast periods is derived by subtracting the value of HISTPERIODS from the STATLEN of the dimension of the time-series expression.)

MAXFCFACTOR decimal
Specifies the upper bound on the forecast data. The number you specify for decimal indicates a multiple of the largest value in the historical series. For example, when you specify `10.0`, the upper bound is 10 times the largest value in the historical series. The default value is `100.0`.

METHOD 'method''
Specifies the forecasting method that you want the forecasting engine to use. Values that you specify for method are ignored unless the value of `APPROACH` is set to `'APPMANUAL'`.

You can specify one of the following keywords for method:

- `AUTOMATIC` specifies that the forecasting engine determines and uses the method that is the best fit for the data. (Default)

- `LINREG` specifies the linear regression method in which a linear relationship `(y=a*x+b)` is fitted to the data.

- `NLREG1` specifies a nonlinear regression method in which a linear relationship `(y'=a*x'+b)` is fitted to a transformation of the original data; in this case, `x'=log(x) and y'=log(y)` which results in the development of a polynomial model between `x` and `y(y=c*x^a)`.

- `NLREG2` specifies a nonlinear regression method in which a linear relationship `(y'=a*x'+b) `is fitted to a transformation of the original data; in this case, `x'=x and y'=ln(y)` which results in the development of an exponential model between x and `y(y=c*êax)`.

- `NLREG3` specifies a nonlinear regression method in which a linear relationship `(y'=a*x'+b)` is fitted to a transformation of the original data; in this case, `x'=log(x)` and `y'=y` which results in the development of a logarithmic model between x and `y(y=a*log(x)+b)`.

- `NLREG4` specifies a nonlinear regression method in which a linear relationship `(y'=a*x'+b)` is fitted to a transformation of the original data; in this case, `x'=1/x and y'=1/y` which results in the development of an asymptotic curve `(y=x/(a+bx))`.

- `NLREG5` specifies a nonlinear regression method in which a linear relationship `(y'=a'*x+b)` is fitted to a transformation of the original data; in this case, `x'=x and y'=ln(y/(K-y))` which results in the development of an exponential asymptotic curve `(y=cKêax/(1+cêax))`.

- `SESMOOTH` specifies the single exponential smoothing method in which the current estimate is taken as a geometrically weighted average of past values, and all future values are given this same value. This method is intended for short term forecasts of non-seasonal data.

- `DESMOOTH` specifies the double exponential smoothing method in which the current estimate is taken as a geometrically weighted average of past values, and this is added to a trend term calculated by the same method. Single exponential smoothing is therefore applied to both the series and the trend term.

- `CROSTON` specifies the Croston's Intermittent Demand method. The Croston's Intermittent Demand method is a forecasting method which is a variant of exponential smoothing that can be used for intermittent data (that is data where more than half of the observations are zero). This method first estimates the interval between positive demands, and then estimates the magnitude of the demand when positive.

- `HOLT/WINTERS` specifies the Holt-Winters method that is used on seasonal data, in which double exponential smoothing methods with trend damping are combined with multiplicative seasonal factors, which are estimated using single exponential smoothing.

MINFCFACTOR decimal
Specifies the lower bound on the forecast data. The number you specify indicates a multiple of the smallest value in the historical series. For decimal, you can specify any decimal value from `0.0` through `1.0`. For example, when you specify `0.5` the lower bound is half the smallest value in the historical series. The default value of decimal is `0.0`.

MPTDECAY {MAX\|MIN} decimal
Specifies the value of the parameter that the forecasting engine uses when it adjusts the decay of estimates of base values that it uses when it unravels the predictions on a moving periodic total (MPT) series.

- `MPTDECAY MAX` `decimal` specifies the maximum value of the parameter that the forecasting engine uses when it adjusts the decay of estimates of base values that it uses when it unravels the predictions on a moving periodic total (MPT) series. For decimal, you can specify any decimal value from `0.2` through `1.0` when the difference between the values of MPTDECAY MIN and MPTDECAY MAX is evenly divided by `0.4`. The default value of decimal is `1.0`.

- `MPTDECAY MIN` `decimal` specifies the minimum value of the parameter that the forecasting engine uses when it adjusts the decay of estimates of base values that it uses when it unravels the predictions on a moving periodic total (MPT) series. For decimal, you can specify any decimal value from `0.2` through `1.0` when the difference between the values of MPTDECAY MIN and MPTDECAY MAX is evenly divided by `0.4`. The default value of decimal is `0.2`.

NTRIALS integer
Specifies the number of trials that the forecasting engine runs to determine the forecast. For integer, you can specify any `INTEGER` value from `1` through `3`. The default value of decimal is `3`.

PERIODICITY cycle-spec
Specifies either the number of periods for a single cycle or the number of periods in each of a set of nested cycles.

You do not have to specify this parameter when you are using a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. In this case, the forecasting engine derives the periodicity from the number of time dimension periods that constitute a year (for example, there are 52 WEEK periods in a year).

When you are not using a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, the default value for cycle-spec is `1`, which specifies that the data is not grouped at all (that is, each period is logically independent).

Cycles are groupings of time periods that repeat through the time span of the data. For example, daily periods can be grouped into a weekly cycle and weekly periods can be grouped into a yearly cycle. In this case, the cycles are said to be nested, with the yearly cycle more aggregate than the weekly cycle, and the weekly cycle more detailed than the yearly cycle. By specifying cycles at a more detailed level, you allow OLAP to conduct a finer-grained search for factors that affect the data.

- To specify a single cycle, set cycle-spec to an `INTEGER` from `1` through `25000`. The `INTEGER` indicates the number of periods into which the cycle should be divided. For example, the `INTEGER 12` specifies that the cycle should be divided into 12 periods.

- To specify a series of nested cycles, set cycle-spec to a series of up to six `INTEGER` values enclosed in parentheses and separated by commas. Each value in the series is the number of periods in a nested cycle. The cycles are ordered from most aggregate to least aggregate. For example, when cycle-spec is `(52,7)`, this indicates two cycles in which the most aggregate cycle is divided into 52 periods and each of those periods is divided into seven periods. In this example, the year is divided into 52 weeks, and each of those weeks is divided into seven days.

RATIO decimal
Specifies the ratio of the size of the window that the forecasting engine uses for smoothing and the total number of historical periods. The forecasting engine uses this value to determine the number of backcast periods. You can specify any decimal value from `1/26` through `1/2`. The default value of decimal is `1/3`.

SMOOTHING {YES\|NO}
Indicates whether the forecasting engine should smooth the data for the forecast. The default value is `NO`. Specify `YES` when you want the forecasting engine to smooth the data.

TRANSFORM {'TRNOSEA'\|'TRSEA'\|'TRMPT'}
The data filter that the forecasting engine uses when executing the forecast.

- `'TRNOSEA'` indicates that the forecasting engine does not seasonally adjust the data. (Default)

- `'TRSEA'` indicates that the forecasting engine transforms using a filter that seasonally adjusts the data.

- `'``TRMPT' `indicates that the forecasting engine transforms using a moving periodic total (MPT) filter.

TRENDHOLD {MAX\|MIN\|STEP} decimal
For the double exponential smoothing and Holt-Winters forecasting methods, specifies the value of the trend hold parameter that indicates trend reliability for those methods.

- `TRENDHOLD MAX ``decimal` specifies the maximum value of the trend hold parameter. For decimal, you can specify any decimal value from `0.0` through `1.0`. The default value of decimal is `0.8`.

- `TRENDHOLD MIN ``decimal` specifies the minimum value of the trend hold parameter. For decimal, you can specify any decimal value from `0.0` through `1. 0`. The default value of decimal is `0.4`.

- `TRENDHOLD STEP ``decimal` specifies the value of the interval that the forecasting engine uses when it determines the value of the trend hold parameter. For decimal, you can specify any decimal value from `0.1` through `0.2`. The value of decimal must evenly divide the difference between the values of TRENDHOLD MAX and TRENDHOLD MIN. The default value of decimal is `0.2`.

WINDOWLEN integer
Specifies the number of points that the forecasting engine uses when it determines median values when it performs median smoothing. Median smoothing eliminates extreme variations in the data by replacing each data point in a series by the median value of itself and its neighbors. For integer, you can specify any `INTEGER` value from `1` through `13`. The default value of integer is `3`.

#### Examples

For an example of a forecasting program, see Example 9-119.

### 9.45 FETCH

The FETCH command specifies how analytic workspace data is retrieved for use in the relational table created by the `OLAP_TABLE` function which you use to access analytic workspace data using SQL.

You can only use the FETCH command in the `OLAP_command` parameter of the `OLAP_TABLE` function; you cannot use it in any other context.

Within the `OLAP_TABLE` function, the FETCH keyword specifies explicitly how analytic workspace data is mapped to a table object. The FETCH keyword is provided for Express applications that are migrating to Oracle Database.

**Note:**

Use the FETCH keyword in OLAP_TABLE only when you are upgrading an Express application that used the FETCH command for SNAPI. When you are upgrading an Express application, note that the syntax is the same here as in Express 6.3. You can use the same FETCH commands that you used previously.

When using FETCH as an argument in `OLAP_TABLE`, you must enter the entire statement on one line, without line breaks or continuation marks of any type.

To fetch or import data from an relational table into analytic workspace objects using SQL commands embedded in the OLAP DML, use the OLAP DML SQL command.

**See Also:**

For more information on the `OLAP_TABLE` function, see the Oracle OLAP DML Reference manual

#### Syntax

FETCH expression... \[TAG tag-exp\] \[LABELED\] \[`data-order`\]

where `data-order` is one of the following:

-      USING \<order-dim...\>
-      ACROSS across-dim...
-      DOWN down-dim...
-      ACROSS across-dim... DOWN down-dim...

#### Parameters

expression...
One expression for each target column, in the same order they appear in the row definition. Separate expressions with spaces or commas.

TAG tag-exp
This keyword is ignored; it is retained in the syntax only for backward compatibility.

LABELED
This keyword is ignored; it is retained in the syntax only for backward compatibility. All fetches are labeled.

USING \<order-dim...\>
Orders the data block according to the dimension list specified in \<order-dim...\>. Specify dimensions or composites or a combination of the two within angle brackets. Dimensions are ordered from fastest to slowest varying, with the first dimension being the fastest varying. When you specify a USING clause, then you cannot specify ACROSS or DOWN.

ACROSS across-dim...
Orders the data block in columns and rows and specifies the column dimensions. For across-dim, specify a list of one or more dimensions, composites, the NONE keyword, or a combination of these. When you specify two or more ACROSS dimensions, then they vary from slowest to fastest, with the first dimension being the slowest.

When you specify ACROSS but not DOWN, then all unspecified dimensions default to DOWN dimensions, which vary from fastest to slowest in the order that the dimensions appear in the object definitions. However, adding the NONE keyword to the ACROSS dimension list fetches only the first value in status for the unspecified DOWN dimensions.

When you specify an ACROSS clause, then you cannot specify a USING clause.

DOWN down-dim...
Orders the data block in columns and rows and specifies the row dimensions. For down-dim, specify a list of one or more dimensions, composites, the `NONE` keyword, or a combination of these. When you specify two or more `DOWN` dimensions, then they vary from slowest to fastest, with the first dimension being the slowest.

When you specify DOWN but not ACROSS, then all unspecified dimensions default to ACROSS dimensions, which vary from fastest to slowest in the order that the dimensions appear in the object definitions. However, adding the NONE keyword to the DOWN dimension list fetches only the first value in status for the unspecified ACROSS dimensions.

When you specify a DOWN clause, you cannot specify a USING clause.

#### Usage Notes

Default Data Order

When you do not specify a USING or DOWN/ACROSS clause, the dimensions of the data vary from fastest to slowest in the order they are listed in the workspace object definitions.

Using Expressions with Different Dimensionality

When you specify multiple expressions with different dimensionality in one FETCH command, the ordering of the dimensions from fastest to slowest varying is not predictable.

Maximum Size of Data Block

You can use MAXFETCH to set an upper limit on the size of a data block generated by FETCH.

Variables Defined with Composites

For variables defined with composites, you can specify the composites instead of the base dimensions in the ACROSS, DOWN, and USING clauses of FETCH which minimizes the number of NA fields in the resulting data block. When a variable has been defined with a named composite, you can specify the name of the composite after the USING, DOWN or ACROSS keyword. You specify unnamed composites with the syntax used to define them. For example, a variable d.sales with the following definition

    DEFINE d.sales VARIABLE DECIMAL <month SPARSE<product district>>

could be fetched with the expression `SPARSE<product district>` immediately following a USING, DOWN, or ACROSS keyword.

#### Examples

For an example of using FETCH in `OLAP_TABLE`, see the examples for OLAP_TABLE in the Oracle OLAP DML Reference manual.

### 9.46 FILECLOSE

The FILECLOSE command closes an open file. When the file has not been opened, an error occurs.

#### Syntax

FILECLOSE fileunit

#### Parameters

fileunit
An I`NTEGER` fileunit number assigned to an open file by a previous call to the FILEOPEN function or by an OUTFILE command.

#### Usage Notes

LOG Command

You must use the LOG command with the EOF keyword, rather than FILECLOSE, to close a file that was opened with the LOG command.

#### Examples

Example 9-120 Program That Opens and Closes a File

Suppose you have a program called READFILE that takes a file name as its first argument. The following lines from the program open the file and then close it.

    fil.unit = FILEOPEN(arg(1), read)
       ... (Commands to read and process data)
    FILECLOSE fil.unit

### 9.47 FILECOPY

The FILECOPY command copies the contents of one file (the source file) to another file (the target file). When the target file already exists, the file is overwritten with the copy.

#### Syntax

FILECOPY source-file-name target-file-name

#### Parameters

source-file-name
A text expression specifying the name of the file you want to copy from. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use the CDA command to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

target-file-name
A text expression specifying the name of the file you want to copy to. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

#### Examples

Example 9-121 Copying a File

The following statement copies the file `log.txt` from your session's current directory object to file `oldlog.txt` in the same directory.

    FILECOPY 'log.txt' 'oldlog.txt'

### 9.48 FILEDELETE

The FILEDELETE command deletes a file from the operating system disk space.

#### Syntax

FILEDELETE file-name

#### Parameters

file-name
A text expression specifying the name of the file you want to delete. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use the CDA command to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

#### Examples

Example 9-122 Specifying the File Using a Variable

The following statement deletes the file whose name is stored in a text variable called `filevar`.

    FILEDELETE filevar

### 9.49 FILEMOVE

The FILEMOVE command changes the name or location of a file that you specify. The new file name may be the same or different from the original name.

#### Syntax

FILEMOVE old-file-name new-file-name

#### Parameters

old-file-name
A text expression specifying the name of the file you want to move or rename. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use the CDA command to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

new-file-name
A text expression specifying the new name or location for the file. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

#### Examples

Moving a File

The following statement moves the file `log.txt` from your session's current directory object to file `oldlog.txt` in a directory object called `backup`.

    FILECOPY 'log.txt' 'backup/oldlog.txt'

### 9.50 FILEPAGE

The FILEPAGE command forces a page break in your output when PAGING is on. FILEPAGE can send the page break conditionally, depending on how many lines are left on the current page

#### Syntax

FILEPAGE fileunit \[n\]

#### Parameters

fileunit
A fileunit number assigned to a file that is opened in WRITE or APPEND mode by a previous call to the FILEOPEN function or by the OUTFILE command.

n
A positive `INTEGER` expression that indicates a page break should occur when there are fewer than n lines left on the page. When the number of lines left equals or exceeds n, or n equals zero, no page break occurs. When n is greater than PAGESIZE, a page break occurs when LINENUM is not zero. When n is negative or omitted, a page break always occurs.

Oracle OLAP calculates the number of available lines left on the page using the values of the options that specify the page size, the current line number, and the bottom margin. The number, which is stored in LINELEFT, is calculated according to the following formula.

LINESLEFT = PAGESIZE - LINENUM - BMARGIN 

#### Usage Notes

Using PAGE Instead of FILEPAGE

The PAGE command has the same effect as specifying the FILEPAGE command for the fileunit number OUTFILEUNIT, which is the number of the current outfile destination. The following two statements are equivalent.

    FILEPAGE OUTFILEUNIT
    PAGE

#### Examples

Example 9-123 Using the FILEPAGE Command

In the following program fragment, you might send a FILEPAGE statement when you know the next group of products does not fit on the page. The program takes as arguments the name of the output file, and three `month` dimension values.

    fil.unit = FILEOPEN(ARG(1) WRITE)
    LIMIT month TO &ARG(2) &ARG(3) &ARG(4)
    COMMAS = NO
    DECIMALS = 0
    FOR district
      DO
        FILEPAGE fil.unit STATLEN(product)
        FOR product
        DO
          FIL.TEXT = product
          FOR month
            JOINCHARS(fil.text  ' ' CONVERT(sales TEXT))
          FILEPUT fil.unit fil.text
        DOEND
        FILEPUT fil.unit ''
      DOEND
    FILECLOSE fil.unit

### 9.51 FILEPUT

The FILEPUT command writes data that is specified in a text expression to a file that is opened in WRITE or APPEND mode.

#### Syntax

FILEPUT fileunit {text-exp\|FROM infileunit} \[EOL\|NOEOL\]

#### Parameters

fileunit
A fileunit number assigned to a file that is opened for writing (WRITE or APPEND mode) by a previous call to the FILEOPEN function or by the OUTFILE command.

text-exp
A text expression that contains data for output.

**Note:**

When you specify NTEXT data to be written to a file, FILEPUT translates the text to the character set of the file. When that character set cannot represent all of the NTEXT characters, then data is lost.

FROM infileunit
Transfers a record read from infileunit by the FILENEXT function directly to the file specified by fileunit. When you specify this clause, you can write selected records to an output file while continuing to process data with the FILEVIEW command.

**Note:**

When you use the keyword phrase FROM infileunit, you cannot mix binary and non-binary files. When either file was opened with the BINARY keyword, the other must be binary too.

EOL
(Default) Specifies that a newline character is appended to the output string and written to the file.

NOEOL
Specifies that no newline character is added to the text written to the file.

#### Examples

Example 9-124 Writing Data to a File Using FILEPUT

Following is an example of a program that writes a file of sales data for three months. The name of the file is the first argument. The following program excerpt opens the file, writes the lines of data to the file, then closes it. This program takes four arguments on the statement line after the program name: the file name of the input data and three month names.

    DEFINE salesdata PROGRAM
    LD Write Sales Data To File. Args: File Name, 3 Month Names
    PROGRAM
    VARIABLE fil.unit INTEGER
    VARIABLE fil.text TEXT
    fil.unit = FILEOPEN(ARG(1) WRITE)
    LIMIT month TO &ARG(2) &ARG(3) &ARG(4)
    LIMIT product TO ALL
    LIMIT district TO ALL
    COMMAS = NO
    DECIMALS = 0
    FOR district
      DO
        FOR product
        DO
          fil.text = product
          FOR month
            fil.text = JOINCHARS(fil.text  ' ' -
              CONVERT(sales TEXT))
          FILEPUT fil.unit fil.text
        DOEND
        FILEPUT fil.unit ''
      DOEND
     
    FILECLOSE fil.unit
    END

Example 9-125 Preprocessing Data

The following example uses a data file with the 1996 sales figures for the products sold in each district. Only the records that begin with "A" are important right now, but you want to save the rest of the records in a separate file for later processing. The following program excerpt uses FILENEXT to retrieve each record and FILEVIEW to find out what kind of record it is. A second FILEVIEW statement processes the record when it is type "A." When not, a FILEPUT statement writes it to the output file.

    DEFINE rectype VARIABLE ID
    LD One Letter Code Identifying The Record Type
    VARIABLE in.unit INTEGER
    VARIABLE out.unit INTEGER
    . . .
    in.unit = FILEOPEN( GET(TEXT PROMPT 'Input Filename: ') READ)
    out.unit = FILEOPEN( GET(TEXT PROMPT 'Output Filename: ') -
       WRITE)
     
    WHILE FILENEXT(in.unit)
       DO
         FILEVIEW in.unit WIDTH 1 rectype
         IF rectype EQ 'A'
           THEN FILEVIEW COLUMN 2 WIDTH 8 district SPACE 2 -
             WIDTH 8 product ACROSS month year Yr96: saleS
           ELSE FILEPUT out.unit FROM in.unit
      DOEND
    FILECLOSE in.unit
    FILECLOSE out.unit
    . . .
    END

### 9.52 FILEREAD

The FILEREAD command reads records from an input file and processes data according to action statements that you specify. FILEREAD handles binary data, packed decimal data, and text. It can handle decimal data written in E-notation (such as `.1E+9`) or M-notation (such as `10M`). It can convert the data to any appropriate data type before storing it in an Oracle OLAP variable, dimension, composite, or relation.

#### Syntax

FILEREAD fileunit \[STOPAFTER n\] \[file-format\] {\[attribute...\] action-statement1}      \[\[attribute...\] action-statementN...\]

where:

- `file-format` specifies the format of the records in the input file. Use one of the following:

  - `RULED`
  - `CSV [DELIMITER`` dchar``]`
  - `STRUCTURED [TEXTSTART ``schar``] [TEXTEND ``echar``] [DELIMITER ``dchar``] `

- `attribute` provide information that is used by action statements.

  - {COLUMN\|COL} n
  - {SPACE\|SP} n
  - {FIELD\|FLD} n
  - {WIDTH\|W} n
  - data-type
  - dimension-value-handling
  - BINARY \| PACKED \| SYMBOLIC
  - TRANSLATE \| NOTRANSLATE
  - SCALE n
  - ZPUNCH \| ZPUNCHL
  - LSET 'text'
  - RSET 'text'
  - stripping
  - NAVALUE val
  - NASPELL 'text'
  - ZSPELL 'text'
  - YESSPELL 'text'
  - NOSPELL 'text'
  - ZEROFILL

  For information on the placement of attributes in action statements, see "Placement of Field Attributes in FILEREAD".

- `action-statements` perform processing, such as assignment statements and IF statements. An action-statement can be one of the following:

  - `assignment-statement`
  - IF-`statement`
  -  `SELECT-statement`
  - ACROSS-`statement``:` `action-statement`
  - `<``action-statement-group``>`

#### Parameters

fileunit
A fileunit number assigned to a file that is opened for reading (READ mode) by a previous call to the FILEOPEN function.

STOPAFTER n
The number of records to read from the input file. When STOPAFTER is left out, or specified with a negative number or an `NA`, FILEREAD processes the whole file. See "STOPAFTER Keyword".

RULED
Specifies that the record is organized in fixed-width columns, that is, character-by-character or byte-by-byte. All lines must have the same format. RULED is the default file format. Use the COLUMN, SPACE, and WIDTH attributes to specify the location of the data in the records.

CSV \[DELIMITER dchar\]
CSV specifies that the data is in CSV (comma-delimited values) format. You must use the FIELD and SPACE attributes to specify the location of the data in the record.

dchar is a text expression that specifies a single character that you want Oracle OLAP to interpret as the general field delimiter in a structured file. Oracle OLAP uses the general field delimiter to identify both numeric and text fields. The default character is a comma (`,`).

CSV files are a common output format that is generated by spreadsheet programs. Each line of characters in a source file is treated as a single record. Each field in the record is separated by a comma by default. You can use the DELIMITER keyword to specify some other character as field delimiter.

When a group of characters in the input record is enclosed by double quotation marks, all of the following rules apply:

- When the group includes the delimiter character, it is treated as a literal instead of as a delimiter.

- When a double quotation mark (`"`) is included in the group of characters, then it must be followed by another double quotation mark.

- When a linefeed character (`\n`) is included in the group of characters, then it is ignored.

- Any spaces or tabs that occur before or after the double quotation marks that enclose the group of characters is ignored.

STRUCTURED
Specifies that the record is in "structured prn" format. You must use the FIELD and SPACE attributes to specify the location of the data in the record.

Structured files are a common output format for PC software. They are text files in which the fields are composed of groups of characters. A group of characters is defined by two conditions: text enclosed in double quotes, or a sequence of numbers that is uninterrupted except by a decimal point. Consequently, an unquoted sequence of numbers containing a decimal point is stored as a single value; however, an unquoted sequence of numbers containing commas or other delimiters to mark off thousands is split into several values rather than stored as a single value. Any unquoted, non-numeric characters are ignored, except a minus sign that immediately precedes a number is considered to be part of the number. A space cannot separate the minus sign from the number.

When your file format does not conform to the pattern described here, you can use the TEXTSTART, TEXTEND, and DELIMITER keywords that let you customize the delimiters FILEREAD uses to identify the start and end of each field.

TEXTSTART schar
Specifies a single character that you want Oracle OLAP to interpret as the start of a text field in a structured file. schar is the value of the character. The default character is a double quote (`"`).

TEXTEND echar
Specifies a single character that you want Oracle OLAP to interpret as the end of a text field in a structured file. echarr is the value of the character. The default character is a double quote (`"`).

DELIMITER dchar
Specifies a single character that you want Oracle OLAP to interpret as the general field delimiter in a structured file. Oracle OLAP uses the general field delimiter to identify both numeric and text fields. dchar is the value of the character. The default character is a comma (`,`).

{COLUMN\|COL} n
The column in which the field starts in the input record. By default, field 1 begins in column 1 and subsequent fields begin in the column following the previous field. The current field's default column is the sum of the previous field's first column plus its width plus any spaces specified for the current field.

Table 9-7 File Attributes

| Syntax                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| {COLUMN\|COL} n          | The column in which the field starts in the input record. By default, field 1 begins in column 1 and subsequent fields begin in the column following the previous field. The current field's default column is the sum of the previous field's first column plus its width plus any spaces specified for the current field.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| {SPACE\|SP} n            | The number of spaces between a field and the preceding field. In a structured PRN file, the number of fields between the preceding and current field. The default is `0`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| {FIELD\|FLD} n           | In a structured PRN file only, the field from which to extract the data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| {WIDTH\|W} n             | For unstructured records, the number of columns the field occupies in the input record. When there is no default, WIDTH must be included for ruled records or FILEREAD generates an error. The default is derived from the data type according to the following list:<br>• BINARY input format with `INTEGER`, `SHORTINTEGER`, or `SHORTDECIMAL` target data type has a default of 4 columns.<br>• BINARY input format with `DECIMAL` or `NUMBER` target data type has a default of 8 columns.<br>• BINARY input format with `BOOLEAN` target data type has a default of 2 columns.<br>• PACKED input format with any type of target data type has no default.<br>• SYMBOLIC input format with `ID` target data type has a default of 8 columns.<br>• SYMBOLIC input format with a target data type that is not `ID` has no default.<br>The maximum width is 4,000 characters for text input.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| data-type                | One of the following keywords: INTEGER, SHORTINTEGER, DECIMAL, SHORTDECIMAL, NUMBER, TEXT, ID, DATE, VNF, RAW DATE, BOOLEAN.<br>• For text data, the data type to which the input is converted before it is stored in your analytic workspace.<br>• For binary data, the data type of the data in the input record.<br>• Except for dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR, the default is the data type of the target object.<br>• For dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR, the default is VNF.<br>• For DATE variables and dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR, RAW DATE indicates the input values are positive `INTEGER` values that represent the number of days since December 31, 1899, or negative `INTEGER` values that represent the number of days before December 31, 1899.<br>See "Specifying a Target Object that has NTEXT Values".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| dimension-value-handling | When the target object is a dimension or dimension surrogate, one of the following keyword clauses that specifies whether or not to add new values to the target object:<br>• MATCH<br>• Do not add new values to the dimension or dimension surrogate. Instead, when the target object is a dimension and then values in the input field must match current dimension values. For each record processed, the dimension is temporarily limited to the value in the record. When the value does not exist, FILEREAD generates an error. This attribute also applies when the target object is a dimension surrogate.<br>• APPEND \[LAST \|FIRST \| BEFORE pos \| AFTER pos\]<br>• Add new values to the dimension by appending the values. The field contains new dimension values and may contain existing values as well. New values are added to the dimension list and the status is limited to the current value. The status is set to ALL after FILEREAD finishes. For time dimensions, Oracle OLAP automatically fills in any "missing" periods between the existing ones and the new ones. When the target object is a non-time dimension, you can specify how Oracle OLAP appends the value using one of the following keywords: LAST which adds the value to the end of the dimension list; FIRST which adds the value to the beginning of the list; BEFORE pos which adds the value before the specified value or `INTEGER` position; and AFTER pos which adds the value after the specified value or `INTEGER` position.<br>• ASSIGN<br>• Add new values to the dimension surrogate by assigning the values. This attribute applies only to a dimension surrogate. It assigns the new value to the surrogate. |
| input-field-format       | One of the following keywords that specifies the format of the input field:<br>• SYMBOLIC which specifies that the format of the input field is ASCII or EBCDIC text.<br>• BINARY which specifies that the format of the input field is binary.<br>• PACKED which specifies that the format of the input field is packed decimal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| TRANSLATE\|NOTRANSLATE   | Whether or not Oracle OLAP translates the data from the format of the original operating system, as identified by a FILESET ORIGIN statement. Specify TRANSLATE when you want Oracle OLAP to translate the data; or specify NOTRANSLATE when you do not want Oracle OLAP to translate the data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| SCALE n                  | The number of digits to the right of the assumed decimal or binary point. The default is 0. When the input data is text, a decimal point in the input overrides the number specified by SCALE.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ZPUNCH\|ZPUNCHL          | Provides information about how the input zone is overpunched. Specify ZPUNCH when the input is zone overpunched. Specify ZPUNCHL when the input is zone overpunched on the left.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| LSET 'text'              | For text input and TEXT or ID target objects, adds text to the left of the value before storing. When text is a multiline value, only the first line is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| RSET 'text'              | For text input and TEXT or ID target objects, adds text to the right of the value before storing. When text is a multiline value, only the first line is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| stripping                | For text input, one of the following keywords that indicates if spaces or nulls are stripped from input value before storing in the target object:<br>• `NOSTRIP`<br>• No spaces or nulls are stripped from the input.<br>• `STRIP`<br>• Spaces and nulls are stripped from both left and right of the input.<br>• `LSTRIP `<br>• Spaces and nulls are stripped from the left of the input.<br>• `RSTRIP`<br>• Spaces and nulls are stripped from the right of the input.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

NAVALUE val
For binary or packed input, specifies that when the input is the specified numeric value, `NA` is assigned to the target object.

NASPELL 'text'
For text input, specifies that Oracle OLAP stores text as NA. When the input is the specified text, NA is assigned to the target object. Text can be a multiline string listing several possible NA values. In addition to the values specified for text, when the input is NA, then NA is assigned to the target object.

ZSPELL 'text'
For textual numeric input, specifies that Oracle OLAP stores text as 0. When the input is the specified text, zero is assigned to the target object. Text can be a multiline string that lists several possible zero values. In addition to the values specified for text, when the input is `0`, then `0` is assigned to the target object.

YESSPELL 'text'
For text input that is BOOLEAN, specifies that Oracle OLAP stores text as YES. When the input is text then YES is assigned to the target object. Text can be a multiline string that lists several possible YES values. In addition to the values specified in text, when the input is `YES`, ON, or TRUE, `YES` is assigned to the target object.

NOSPELL 'text'
For text input that is BOOLEAN, specifies that Oracle OLAP stores text as NO. When the input is text then NO is assigned to the target object. Text can be a multiline string that lists several possible NO values. In addition to the values specified in 'text,' when the input is NO, OFF, or FALSE, NO is assigned to the target object.

ZEROFILL
For text numeric input, specifies that Oracle OLAP fills any spaces in the resulting text with zeros. Any spaces in the input are replaced with zeros. The default is no filling with zeros.

action-statement
You may specify one or more action statements to be performed each time a record is retrieved from the input file. Typically, you use action statements to set dimension status and assign data retrieved from the input record to a target object in Oracle OLAP. However, you may specify action statements that do not reference the data in the input record. For example, one of your action statements might be an assignment statement that simply increments a counter. Alternatively, an action statement might use the input data in some kind of processing, but not actually assign it to a target object in Oracle OLAP.

In your list of action statements, be sure to process dimensions before variables. FILEREAD processes each action statement from left to right for each input record. When an action statement performs dimension processing, the resulting status remains in effect for subsequent action statements. When you do not first specify action statements that limit a variable's dimensions, FILEREAD uses the first value in status to target a cell in the variable. Unless you specify an ACROSS phrase, FILEREAD assigns a single value from a field in an input record to a single cell in an Oracle OLAP variable. By default, FILEREAD does not loop over a variable's dimensions when assigning data to the variable. See "Field Order".

Use the VALUE keyword in FILEREAD action statements to represent the value in a particular field of the input record. VALUE represents this data, formatted according to the FILEREAD attributes you have specified. When the field in the record is blank, FILEREAD considers its value to be `NA`. By default, the data type of VALUE is the data type of the target object. However, you can specify a different data type with an attribute keyword.

**Note:**

When you have already specified action statements for use with FILEREAD, you can reuse the code with SQL FETCH and SQL IMPORT by simply adjusting the assignment statements and eliminating the VALUE keyword (if necessary). Most of the FILEREAD attributes (except for the attributes that control dimension processing) are not meaningful for SQL loading and are ignored when executing within SQL FETCH and SQL IMPORT.

assignment-statement
An assignment statement lets you assign a value to an Oracle OLAP object. An assignment statement has the following form.

     object \[= expression\]

`object` is the target where the data is assigned and stored. The object can be an Oracle OLAP variable, dimension, dimension surrogate, composite, or relation.

`expression` is the source of the data value to be assigned to the target.

**Note:**

In a SQL FETCH or a SQL IMPORT assignment statement, the expression component is not optional. However, a FILEREAD assignment statement may consist only of an object name. In this case, the input data is assigned directly to object. An expression in a FILEREAD assignment statement may include the VALUE keyword.

IF-statement
An IF statement lets you perform some action depending on whether a Boolean expression is `TRUE` or `FALSE`. An IF statement has the following form.

     IF bool-exp         THEN action       \[ELSE action\]

IF evaluates the Boolean expression. When it is TRUE, the THEN action occurs. When it is FALSE, the ELSE action (if specified) occurs. When the Boolean expression is `NA`, no action occurs.

An action can be one of the following:

- NULL (no action occurs)

- An assignment statement

- A SELECT statement

- An IF statement

- A DO … DOEND statement containing action-statements

A FILEREAD IF statement may contain invocations of the VALUE keyword. You can use a FILEREAD IF statement to process varying record types (such as records with different structures or different target objects) with one FILEREAD statement.

In FILEREAD, the VALUE keyword can be used more than once to represent different values from the same record. For each instance, specify the column from which to read each value.

SELECT statement
A SELECT statement lets you perform some action based on the value of an expression. A SELECT statement has the following form.

     SELECT select-expression         \[WHEN expression1 action         \[WHEN expression2 action . . .\]      \[ELSE action\]

SELECT evaluates the SELECT expression and then sequentially compares the result with the WHEN expressions. When the first match is found, the associated action occurs. When no match is found, the ELSE action (if specified) occurs.

An action for a SELECT statement is the same as an action for an IF statement.

A FILEREAD SELECT statement may contain invocations of the VALUE keyword. You can use a FILEREAD SELECT statement to process varying record types (such as records with different structures or different target objects) with one FILEREAD statement.

ACROSS-statement: action-statement
An ACROSS statement causes the following action statement to execute once for every value in status of the ACROSS dimension. When you want the looping to apply to multiple action statements, enclose the action statements in angle brackets.

An ACROSS statement has the following syntax.

     ACROSS dimension \[limit-clause\]:

        action-statement

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

The following example limits `month` to the last six values, no matter what the current status of `month` is.

    ACROSS month last 6: units

In a FILEREAD ACROSS statement, you can specify attributes to indicate the position in the record where Oracle OLAP begins reading the fields specified by the ACROSS phrase. To specify the position, use the attributes FIELD, SPACE, and COLUMN. A position attribute is optional when the series of fields specified in the ACROSS phrase begins in the next field for structured records, or the next byte for ruled records.

\<action-statement-group\>
You can group several action statements by enclosing them in angle brackets. An action-statement-group has the following form.

     \<action-statement1 -      \[action-statement2 . . .\]\>

A typical use for action statement groups is after an ACROSS statement. With the angle bracket syntax, you can cause multiple action statements to execute for every value in status of the ACROSS dimension.

#### Usage Notes

Reading One Record at a Time

As an alternative to FILEREAD, you can use the FILENEXT function to read one record at a time with one or more FILEVIEW statements to process the fields in the record.

Field Order

When an input record contains both dimension values and variable data, the dimension values must be the first fields that are read in the record, and the variable data values must be read after those dimension values. To do this, you can either order the fields in the input record itself or you can use FILEREAD attributes to specify the field positions explicitly. (See the description for the attribute argument.)

To organize the input records so that you do not have to use position attributes with FILEREAD, put all of the dimension values in the first fields of the record and put the variable data values in the last fields of the record. For example, suppose that you have data for two variables (`units` and `sales`) that share the same dimensions in the same order (`time`, `product`, and `geography`). In this case, the first three fields in the input record should contain dimension values, while the fourth and fifth fields should contain variable data, such as in the following sample input record.

    Sep99    Snowshoes    Boston    35    5565.95

STOPAFTER Keyword

By default, FILEREAD automatically reads all the records in a file in sequential order. When you want to process only the first part of a file, use the STOPAFTER keyword. FILEREAD processes the number of records you specify, then stops. You can then close the file.

When you want to skip the first part of the file and process the remaining records, you can use the STOPAFTER keyword and omit the field descriptions. FILEREAD reads the number of records you specify without processing the data. Then you issue a second FILEREAD statement with field descriptions for processing the input. The following program lines illustrate this method.

    LIMIT district TO 'Boston'
    unit = FILEOPEN('bostdata' READ)
    FILEREAD unit STOPAFTER 25
    FILEREAD unit WIDTH 8 product SPACE 2 ACROSS month 13 TO 24:-
       WIDTH 4 PACKED sales

Dimension Maintenance

When the target object of a field description is a dimension, you can specify whether or not to use the data in the file to add values to the dimension. The dimension attributes are MATCH and APPEND. When you are adding values to a dimension with APPEND, you can specify a dimension position attribute (`LAST`, `FIRST`, `BEFORE` `pos`, `AFTER` `pos`) immediately after APPEND.

In an assignment statement of the form `object=expression`, dimension attributes cannot appear on the right side of the equal sign, but must be specified before the target object. The only exception is when dimensions as target objects also appear on the right side, such as when you are maintaining a conjoint dimension. See Example 9-130.

Dimension Position Numbers

When your input data consists of dimension position numbers, rather than dimension values, specify the conversion type as INTEGER in the field description, even though the dimension has a type of TEXT, ID, DAY, WEEK, MONTH, QUARTER, or YEAR.

    FILEREAD unit COLUMN 1 WIDTH 8 INTEGER month

When the input contains position numbers, you cannot use the APPEND keyword to add new values to a dimension of type TEXT, ID, DAY, WEEK, MONTH, QUARTER, or YEAR, because the new position numbers have no associated value to be added.

Conjoint Dimension Maintenance

When a conjoint dimension is the target object, you can read its values using one of two methods:

- Method One—When the input contains values or position numbers of the base dimensions, you must specify a dimension list surrounded by angle brackets after the equal sign, as shown in the following two sample lines.

      FILEREAD unit proddist = <COL 1 W 10 product COL 20 -
         W 8 district>
      FILEREAD unit proddist = <COL 1 W 10 INTEGER product COL 20 -
         W 8 INTEGER district>

  The preceding examples show values of the `product` and `district` dimensions being used to designate a value of the `proddist` concat dimension You could also use the APPEND attribute when you needed to maintain any of the dimensions. However, when you needed to process the values of `product` or `district` first, so that the syntax would require an equal sign inside the angle brackets, you would have to use an alternative method. (Nested equal signs are not allowed.) For this method you would read and process the base dimension values first, and then use the dimensions, without any field attributes, in the dimension list for the conjoint dimension. For example, to convert the base dimension values of a conjoint dimension to uppercase, use a statement similar to the following.

      FILEREAD unit COL 14 W 8 product = UPCASE(VALUE) -
         COL 5 W 8 district = UPCASE(VALUE) -
         proddist = <product, district>

- Method Two—When the input contains position numbers of the conjoint dimension itself, you must specify the INTEGER keyword.

      FILEREAD unit INTEGER proddist

FILEREAD with Variables Dimensioned by Composites

When reading data into a variable dimensioned by a composite, FILEREAD automatically creates any missing target cells that are being assigned non-`NA` values. This process also adds to the composite all the dimension value combinations that correspond to those new cells. Thus, both the target object and the composite might be larger after an assignment.

Variables Dimensioned by Composites and Efficiency

When you use the automatic composite maintenance feature of FILEREAD to load data into variables dimensioned by composites, be aware of potential performance problems that might later occur when you attempt to access the variables' data. The position of a composite in the dimension list of a variable indicates whether or not performance might later become an issue.

When the composite appears at the end of the dimension list in the variable's definition (the slowest-varying position), you can use FILEREAD just as you would for a variable whose dimension list does not include composites. For example, you could use the same FILEREAD statements to read data into the variables `newsales` and `newsales.cp` (with the following definitions) without sacrificing efficiency.

    DEFINE newsales VARIABLE DECIMAL <product district month>
    DEFINE newsales.cp VARIABLE DECIMAL <product SPARSE<district month>> 

`newsales.cp` is dimensioned by three dimensions, the last two of which are in a composite. When, however, you have a variable like `newsales2.cp` (with the following definition) there can be performance implications for accessing data loaded with FILEREAD.

    DEFINE newsales.cp VARIABLE DECIMAL <SPARSE<district month> product > 

In this case, you can use one of two methods to avoid performance problems:

- You can use CHGDFN with the SEGWIDTH keyword to change the segment size for the variable before using FILEREAD. CHGDFN SEGWIDTH lets you specify the size of a variable's segments. A segment is a portion of the total number of values a variable holds. The number of segments in a variable affects the performance of data loading and data accessing. The segment size that you specify with a CHGDFN SEGWIDTH statement is used not only for the variable you designate as varname, but also for all other variables and relations that are defined with the same combination of dimensions and composites in the same order.

- You can explicitly add composite values just as you would for a conjoint dimension. You can use this method both for named and unnamed composites. See "Composite Maintenance".

Composite Maintenance

When you want to explicitly maintain composites with FILEREAD, use the same syntax that you use to maintain conjoint dimensions. When the composite is unnamed, refer to it with the form `SPARSE<dim1 dim2 ...>`. See "FILEREAD with Variables Dimensioned by Composites" and "Variables Dimensioned by Composites and Efficiency"to evaluate the advantages of explicit versus automatic composite maintenance with FILEREAD.

Using DWMQY Dimensions with FILEREAD

When the target object of a field is a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, the default conversion type is VNF. Therefore, you do not have to specify a conversion type when the input values are formatted according to the VNF of the target dimension (or the default VNF when the dimension does not have a VNF of its own).

When the target object of a field is a DATE variable or a dimension of type DAY, WEEK, MONTH, QUARTER, and YEAR, FILEREAD interprets the values correctly when they are in a valid input style for dates as described in DATEORDER. For dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR, you must specify DATE as the conversion type. For values of a DATE variable, DATE is the default conversion type, so the DATE keyword is optional.

FILEREAD also interprets values of a time dimension or a DATE variable correctly when they are `INTEGER` values that represent dates (`1` = `January` `1,` `1900`). In this case, you must specify RAW DATE as the conversion type.

Blank Fields

When a field is blank, its value is `NA` and `NA` is assigned to the target variable. Examples of blank fields are a text field filled with spaces, a field that begins beyond the end of the record, or a field in a structured file that has nothing, not even a space, between the field delimiters.

Placement of Field Attributes in FILEREAD

Normally, the field attributes immediately precede the target object or the expression on the right of the equal sign.

     attributes object

However, when you want an attribute to apply to several fields, specify the attribute followed by the list of target objects surrounded by angle brackets. You can also include attributes that apply to one object by typing them inside the brackets before the object to which they apply.

     attributes0 \<attributes1 object1=expression object2 attributes3 object3\>

Angle brackets are also used to surround the base values of a conjoint dimension value.

Handling Errors When FILEREAD Encounters an Error

When FILEREAD encounters an error, you can control what happens with an error trap and appropriate processing. Errors can be caused by attempts to convert data to an incompatible data type or by encountering invalid dimension values. You can use the FILEERROR function to get more information about what caused the error. After processing the error, you can use a TRAP statement to turn error trapping back on and GOTO to branch back to the FILEREAD statement. Processing continues with the next record. See Example 9-128.

Specifying a Target Object that has NTEXT Values

When you specify a target object of type NTEXT for data from a structured or CSV file, FILEREAD translates the data from the file into the database character set before storing the values (even though they are assigned to an NTEXT object) which can result in data loss when the data from the file cannot be represented in the database character set. For data from a ruled file, which has fixed-width columns, FILEREAD does not translate into the database characters set, so there is no data loss.

#### Examples

Example 9-126 Dimension Values and Data

Suppose your analytic workspace contains six-character product identification numbers. You must import both product names and a value for the number of units sold each month. The data file for the last quarter has the following format.

    Jan951234aa00Chocolate Chip Cookies        123
    Jan951099bb00Oatmeal Cookies               145
    Jan952355cc00Sugar Cookies                 223
    Jan955553ee00Ginger Snap Cookies           233
    Feb951234aa00Chocolate Chip Cookies        123
    Feb951099bb00Oatmeal Cookies               O145
    Feb952355cc00Sugar Cookies                 SS223
    Feb955553ee00Ginger Snap Cookies           G233
    Mar952355cc00Sugar oCookies                 223
    Mar955553ee00Ginger Snap Cookies           233
    Mar953222dd00Brownies                      432

The dimension and variables have the following definitions.

    DEFINE month DIMENSION MONTH
    DEFINE productid DIMENSION ID
    DEFINE productname VARIABLE TEXT <productid> 
    DEFINE units.sold VARIABLE INTEGER <month productid> 

The following program uses FILEREAD to add any new values for `month` and `productid` to the analytic workspace and to put the data in the correct variables. Maintain dimensions in one FILEREAD statement, close the file, and process it again to get the associated data.

    DEFINE read.product PROGRAM
    PROGRAM
    VARIABLE fi INT
    fi = FILEOPEN('Dr.Dat' READ)
    FILEREAD fi COLUMN 1 APPEND WIDTH 5 month -
       COLUMN 6 APPEND WIDTH 6 productid
    FILECLOSE fi
     
    fi = FILEOPEN('Dr.Dat' READ)
    FILEREAD fi COLUMN 1 WIDTH 5 month -
       COLUMN 6 WIDTH 6 productid -
       COLUMN 12 WIDTH 30 productname -
       COLUMN 44 WIDTH 22 units.sold
    FILECLOSE fi
    END

Example 9-127 Dimension Surrogate Values

This example uses one FILEREAD operation to add a value to the `product` dimension and assign a value to `prodnum`, which is a `NUMBER` dimension surrogate for the `product` dimension. It uses a second FILEREAD to assign a value to the `units` variable, which is dimensioned by `month`, `product`, and `district`. The data file for the dimension and surrogate values has the following format.

    Kiyaks400

The following statements define a fileunit, open the file, read its contents and append a value to the `product` dimension and assign a value to the `prodnum` surrogate, and close the file.

    DEFINE funit INT
    funit = FILEOPEN('Ds.Dat' READ)
    FILEREAD funit COL 1 APPEND W 6 product COL 7 ASSIGN W 3 prodnum
    FILECLOSE funit

The data file for the variable value has the following format.

    Jan02400Boston416

The following statements open the file, read its contents, match the value of the `prodnum` surrogate and assign a value to the `units` variable, and close the file.

    funit = FILEOPEN('Var.Dat' READ)
    FILEREAD funit COL 1 W 5 month COL 6 MATCH W 3 prodnum -
      COL 9 W 6 district COL 15 W 3 INTEGER units
    FILECLOSE funit

Example 9-128 Error Handling

When your input file has data that does not match the format specifications, or when it has a dimension value that is not part of the analytic workspace when you are using the default MATCH attribute, you get an error. You can use error processing at the trap label to check for that kind of error, skip the bad record, and continue processing the file. You can also use a FILEPUT statement to store the bad records in a separate file (see the FILEPUT command).

In the following example, the statements at the trap label check whether the file was successfully opened (`fil.unit` has an `INTEGER` value) and whether the user interrupted the program. When these are not the reason for the error, the program assumes it encountered a bad record, resets the trap, and branches back to the FILEREAD statement to continue processing with the next record.

    DEFINE read.price PROGRAM
    PROGRAM
    VARIABLE fil.unit INTEGER
    TRAP ON ERROR
    fil.unit = FILEOPEN( ARG(1) READ)
    LIMIT month TO &ARG(2)
    NEXT:
    FILEREAD fil.unit - 
      WIDTH 8 product -
      WIDTH 4 BINARY price
    FILECLOSE fil.unit
    RETURN
    error:
    IF fil.unit EQ NA
      THEN RETURN
    IF ERRORNAME NE 'attn' AND ERRORNAME NE 'quit'
      THEN DO
        SHOW JOINCHARS('Record ' RECNO(fil.unit) ' is Invalid.')
        TRAP ON ERROR
        GOTO NEXT
      DOEND
    FILECLOSE fil.unit
    END

Example 9-129 Preprocessing File Data Before Assigning to an analytic workspace Object

You can also process the data in each field before assigning it to a variable or dimension in the analytic workspace. Suppose your data file has product identifiers that are six-digit numbers, and your analytic workspace has a `product` dimension whose values are these same product numbers, preceded by a "P." You can process the identifiers in the file by adding a "P" at the beginning of each value.

    FILEREAD unit COLUMN 1 WIDTH 6 APPEND LSET 'p' product

Example 9-130 Maintaining Conjoint Dimensions with File Data

To maintain a conjoint dimension with FILEREAD, you first maintain its base dimensions by appending any new values from the input file. Then you assign the resulting combination of base dimension values to the conjoint dimension. The following example gets base dimension values from two separate fields, appends the values to the base dimensions, then appends the combination to the conjoint dimension.

    FILEREAD unit APPEND proddist = <W 8 product, W 8 district>

In the preceding statement, the angle brackets automatically cause APPEND to apply to all three dimensions. When you do not want to add new values to the base dimensions, but want only to add new conjoint dimension values, you must explicitly state the keyword MATCH or change the order of the target objects, as shown in the two following statements.

    fileread unit APPEND proddist = <W 8 MATCH product,W 8 MATCH district>

or

    FILEREAD unit W 8 product W 8 district APPEND proddist = <product, district>

Example 9-131 Reading Data From a Structured PRN File

Suppose you want to read data from a structured PRN file with values of the `product` dimension in field two, values of the `district` dimension in field three, and several months of sales values beginning in field six. You could read the first 10 records in the file with the following statement.

    FILEREAD unit STOPAFTER 10 STRUCTURED FIELD 2 product -
       district FIELD 6 ACROSS month: sales

### 9.53 FILESET

The FILESET command sets the paging attributes of a specified fileunit.

#### Syntax

FILESET fileunit attrib-arg1 exp1 \[attrib-argN expN ...\]

where `attrib-arg` is one of the following:

- `BMARGIN`
- `LINENUM`
- `LSIZE`
- `ORIGIN`
- `PAGENUM`
- `PAGEPRG`
- `PAGESIZE`
- `PAGING`
- `PAUSEATPAGEEND`
- `TABEXPAND`
- `TMARGIN`

#### Parameters

fileunit
A fileunit number that is assigned to a file opened previously using a FILEOPEN statement or by an OUTFILE statement. You can set attributes only for an open file. An attribute argument specifies the file characteristic to change. The attribute must be appropriate for the fileunit specified; otherwise, Oracle OLAP returns an error. You can set several attributes in one FILESET statement by listing the attribute name and its new value in pairs.

BMARGIN
Specifies the number of blank lines that constitute the bottom margin.

LINENUM
Specifies the current line number. Resets after each page break when PAGING is on; otherwise, keeps incrementing.

LSIZE
Specifies the maximum line length for text output files, or the record length for binary input files.

ORIGIN
Specifies the type of system on which the file was created. The default value of the ORIGIN attribute reflects the system you are currently working on, so you must set ORIGIN when the file originated on a different system. The setting of ORIGIN affects how data reading statements interpret the files. For example, data reading statements use this information to decide whether bytes of binary data have to be reversed, and so forth. The following table helps you make the right choice. When your system is not listed, try using PC or HP as the value of ORIGIN. When one value does not work, the other one should.

Table 9-8 Values for ORIGIN Clause of FILESET

| Value    | Hardware or Operating System                           |
|:---------|:-------------------------------------------------------|
| ALPHA    | Any DEC workstation using an Alpha processor           |
| AVMS     | A DEC Alpha processor running on VM                    |
| HP       | HP MPE XL                                              |
| HPS700   | HP Series 700 Workstation                              |
| HPS800   | HP Series 800 Workstation                              |
| IBMPC    | An Intel processor running DOS, Windows, or Windows N  |
| INTEL5   | Any Intel5 processor running UNIX                      |
| MIPS     | Any MIPS system                                        |
| MVS      | IBM MVS/TSO                                            |
| NTALPHA  | A DEC Alpha processor running Windows NT               |
| PC       | An Intel processor running DOS, Windows, or Windows NT |
| RS6000   | Any IBM RS6000 processor running IBM AIX               |
| SOLARIS2 | Any workstation running Solaris2                       |
| SUNOS4   | Any workstation running SunOS4                         |
| VAX      | VAX VMS (floating point in G format only)              |
| VM       | VM/CMS                                                 |

PAGENUM
Specifies the current page number.

PAGEPRG
Specifies the OLAP DML program that produces page titles and headings when output is paged.

PAGESIZE
Specifies the number of lines on each page.

PAGING
Specifies if the output is formatted in pages which is equivalent to setting the PAGING option to YES.

PAUSEATPAGEEND
Specifies if Oracle OLAP should pause after each page.

TABEXPAND
Specifies if tab characters should be expanded. When TABEXPAND is zero, tab characters are not expanded. A value greater than 0 indicates the distance, in bytes, between tab stops. The default value of TABEXPAND is `8`.

TMARGIN
Specifies the number of blank lines that constitute the top margin.

exp
An expression that contains the new value for the attribute being set. The data type of the expression must be the same as the data type of the attribute.

#### Examples

Example 9-132 Setting Paging for a Report

When you are sending output to a report in a disk file, you might set the following attributes to indicate that the report is organized in pages and that the first page is 1.

    DEFINE fil.unit INTEGER
    fil.unit = FILEOPEN('REPORT' WRITE)
    FILESET fil.unit PAGING YES PAGENUM 1

### 9.54 FILEVIEW

The FILEVIEW command works with the FILENEXT function to read one record at a time of an input file, process the data, and store the data in Oracle OLAP dimensions and variables according to the descriptions of the fields. Use FILENEXT to read the record, then use one or more FILEVIEW statements to process the fields as needed. FILEVIEW has the same attributes as FILEREAD for specifying the format of the input and the processing of the output.

#### Syntax

FILEVIEW fileunit \[field-desc...\]

#### Parameters

fileunit
A fileunit number that is assigned to a file opened for reading (READ mode) in a previous call to the FILEOPEN function.

field-desc
A field description describes how to process one or more fields in each input record. Attributes in the field description specify how to format the input data. FILEVIEW reads each field according to the format specification and assigns the input data to the specified object. You can assign the data to the object directly or you can specify an expression to manipulate the data before you assign it. One field description can assign data from one input field to one Oracle OLAP object. Alternately you can use the ACROSS keyword to assign several values in the input record to a variable that is dimensioned by the fastest varying dimension. Because field attributes include the column number in the input record, you can process input fields in any order.

The format for the field description is as follows.

     \[\[pos\] ACROSS dim \[limit-clause\]:\] \[attribs\] object \[= exp\]

pos
One or more attributes that specify the position in the record where Oracle OLAP begins reading the fields specified by the ACROSS description. To specify the position, use the attributes FIELD, SPACE, and COLUMN (see the FILEREAD command). The pos argument is optional when the series of fields specified in the ACROSS phrase begins in the next field for structured records, or the next byte for ruled records.

ACROSS-statement: action-statement
Specifies the dimension of one or more data fields in the input record. FILEVIEW assigns the data in the fields to a variable according to the values in the current status of dim. Typically, each field description processes one value. However, using the ACROSS keyword, you can process one input value for each dimension value currently in the status. When you want the looping to apply to multiple action statements, enclose the action statements in angle brackets.

An ACROSS statement has the following syntax.

     ACROSS dimension \[limit-clause\]:

        action-statement

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see [LIMIT (using values) command](olap-dml-commands-h-z.md), [LIMIT using LEVELREL command](olap-dml-commands-h-z.md), [LIMIT (using parent relation)](olap-dml-commands-h-z.md), [LIMIT (using related dimension) command](olap-dml-commands-h-z.md), [LIMIT NOCONVERT command](olap-dml-commands-h-z.md), and [LIMIT command (using POSLIST)](olap-dml-commands-h-z.md).

The following example limits `month` to the last six values, no matter what the current status of `month` is.

    ACROSS month last 6: units

attribs
One or more attributes that tell Oracle OLAP the position in the record and the format of the input data. (See the FILEREAD command for an explanation of the available attributes.)

object \[= exp\]
An Oracle OLAP variable, dimension, or relation to which the input data is assigned. When = exp is missing, the data is assigned implicitly to the object. When = exp is present, the data is processed according to the expression and then assigned to object.

You can use the keyword VALUE to represent the value in a particular field of a record. VALUE represents the data from the file, formatted according to the FILEREAD attributes you use. When the field in the record is blank, FILEREAD considers its value to be `NA`. By default, the data type of VALUE is the data type of the target object. However, you can specify a different data type with an attribute keyword. VALUE can be used more than once to represent different values from the same record. For each instance, specify the column from which to read each value, as shown in the following example code.

    sales = if col 1 w 1 text value eq 'A' then col 2 w 8 value -
       else col 10 w 8 value

In this example, the default data type of VALUE is decimal, which is the data type of the target object `sales`. However, the first instance of VALUE is compared to a text expression, so you must use the attribute TEXT to specify its data type.

SELECT exp
The SELECT field-description keyword processes varying record types (such as records with different structures or different target objects) with one FILEVIEW statement. Within a field description, you can use the following syntax:

     SELECT exp -       \[WHEN exp action \[WHEN exp action ...\]\] -      \[ELSE action\]      IF bool-exp THEN action \[ELSE action\]      DO        field-desc        \[field-desc\]        ...      DOEND

The action argument is one of the following:

- NULL (no action occurs)

- field-description, including nested IF and SELECT statements.

SELECT evaluates the first expression, which may contain invocations of the VALUE keyword, and which has a default data type of TEXT. SELECT then sequentially compares the result with the WHEN expressions. When the first match is found, the associated action occurs. When no match is found, the ELSE action (if specified) occurs.

IF bool-exp
The IF field-description keyword processes varying record types (such as records with different structures or different target objects) with one FILEVIEW statement. Within a field description, you can use the following syntax.

     IF bool-exp THEN action \[ELSE action\]

action is the same as described for SELECT.

IF evaluates the Boolean expression, which may contain invocations of the VALUE keyword. IF performs the THEN action when the expression is TRUE or the ELSE action, if specified, when the expression is FALSE. No action occurs when the expression is `NA`.

#### Usage Notes

Record Order

FILEVIEW can process the fields in a record in any order. List the field descriptions in the order you want to process them, identifying the fields with explicit column numbers. You can also use several FILEVIEW statements on the same record to do different processing depending on the data you find in the record.

Alternative OLAP DML Statement

When you want to process all the records in a file in the same way, without complicated optional processing, a FILEREAD statement is easier to use.

Dimension Values

When the target object of a field description is a dimension, you can specify whether the data in the file is used to add values to the dimension or not. The dimension attributes are MATCH and APPEND:

- MATCH -- Any value encountered in a field must already be a value of the dimension. FILEVIEW temporarily limits status to that value. When it is not already a dimension value, FILEVIEW generates an error. After executing a FILEVIEW statement, the dimension status is the same as before the execution of the statement.

- APPEND -- The values in the field can already exist or they can be new. When the value exists, FILEVIEW limits status to that value; when it does not, FILEVIEW adds the value and then limits status. The dimension is limited to ALL when FILEVIEW is finished.

For more information about handling dimensions, see the FILEREAD command.

Handling Errors When FILEVIEW Encounters an Error

When FILEVIEW encounters an error, you can control what happens with an error trap and appropriate processing. Errors can be caused by attempts to convert data to an incompatible data type or by encountering invalid dimension values. You can use the FILEERROR function to find out what type of error occurred. After processing the error, you can use GOTO to branch back to the FILEVIEW statement.

Attribute List

For a complete list of the attributes for FILEVIEW and FILEREAD and for more information about processing `NA` values, reading date values, reading multidimensional data, storing NTEXT values, and specifying attributes, see the FILEREAD command.

FILEVIEW with Composites

The discussions of composites and variables dimensioned by composites in FILEREAD also apply to FILEVIEW.

#### Examples

Example 9-133 Varying Months

The following program processes an input file that contains sales data for a variable number of months. The file has the following records:

- Record 1 -- Title (to be ignored).

- Record 2 -- Column labels. Month names are used to set the status of `month`. The number of months is unknown before processing the file.

- Record 3 -- Dashes underlining column labels (to be ignored).

- Record 4 -- Blank.

- Record 5 to end -- There are three record types for Record 5—one for each type of line to be read.

One record type for Record 5 represents a detail line with the contents shown in the following table.

| Column | Width            | Format   | Data                                                                                                                                                   |
|:-------|:-----------------|:---------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1      | 8                | Symbolic | District name or blank (When the district name is blank on a detail line, the most recent line containing a district determines the current district.) |
| 10     | 10               | Symbolic | Product name                                                                                                                                           |
| 21     | 10               | Symbolic | Sales for first month                                                                                                                                  |
| 33     | 10               | Symbolic | Sales for second month                                                                                                                                 |
| 45     | To end of record | Symbolic | Sales for additional months                                                                                                                            |

Another record type in Record 5 represents a totals line with the contents shown in the following table.

| Column | Width            | Data   |
|:-------|:-----------------|:-------|
| 1      | 18               | Blank  |
| 21     | To end of record | Totals |

A third record type of Record 5 contains dashes or equal signs as row separators as illustrated in the following table.

| Column | Width            | Data                            |
|:-------|:-----------------|:--------------------------------|
| 1      | 18               | Blank                           |
| 21     | To end of record | Dashes (--) or equal signs (==) |

This is a report of the sample file.

      
                                 This is the Title
                        Jan95      Feb95      Mar95      Apr95
                        ---------- ---------- ---------- ----------
     
    Boston   Tents       32,153.52  32,536.30  43,062.75  57,608.39
             Canoes      66,013.92  76,083.84  91,748.16 125,594.28
             Racquets    52,420.86  56,837.88  58,838.04  69,338.88
             Sportswear  53,194.70  58,913.40  62,797.80  67,869.10
             Footwear    91,406.82  86,827.32 100,199.46 107,526.66
                        ---------- ---------- ---------- ----------
                        295,189.82 311,198.74 356,646.21 427,937.31
                        ---------- ---------- ---------- ----------
    Atlanta  Tents       40,674.20  44,236.55  51,227.06  78,469.37
               .
               .
               .
             Footwear    53,284.54  57,331.30  59,144.76  70,516.98
                        ---------- ---------- ---------- ----------
                        231,780.46 245,812.33 275,622.68 355,784.92
                        ---------- ---------- ---------- ----------
                         1,813,326  1,985,731  2,185,174  2,638,409
                        ========== ========== ========== ==========

The program figures out which months are covered in the file, then reads the detail lines and assigns the sales data to the appropriate district and month. The program ignores total lines and underlines when FILEVIEW finds columns 1 through 19 blank. The program takes the name of the data file as an argument.

    DEFINE salesdata PROGRAM
    LD Store Several Months of Sales Data in an Analytic Workspace
    PROGRAM
    VARIABLE fil.unit INTEGER
    VARIABLE flag BOOLEAN
    VARIABLE mname TEXT
    VARIABLE label TEXT
    VARIABLE savedist TEXT
     
    TRAP ON error NOPRINT
    PUSH month district
    fil.unit = FILEOPEN(ARG(1) READ)
     
    IF FILENEXT(fil.unit) NE YES    "Skip Record 1
      THEN SIGNAL noread
    IF FILENEXT(fil.unit) NE YES    "Process Record 2 
      THEN SIGNAL noread
    FILEVIEW fil.unit COLUMN 21 ACROSS month: -
      WIDTH 10 mname = JOINLINES( mname VALUE)
    LIMIT month TO mname
    IF FILENEXT(fil.unit) NE YES     "Skip Record 3
      THEN SIGNAL noread
    IF FILENEXT(fil.unit) NE YES     "Skip Record 4
      THEN SIGNAL noread
     
    WHILE FILENEXT(fil.unit)  "Process Record 5 To End Of File
       DO
       "Store Value In Local Label Variable
       FILEVIEW fil.unit COLUMN 1 WIDTH 18 label  
       IF label NE NA         "Check For NA (Blank Field)
         THEN DO              "Get District Value If Present
          IF EXTCHARS(label, 1, 8) NE '      ' 
             "Set District Status
             THEN savedist = BLANKSTRIP(EXTCHARS(label, 1, 8)) 
           FILEVIEW fil.unit -
             COLUMN 1 WIDTH 8 district = IF VALUE NE NA THEN -
                VALUE ELSE savedist -
             COLUMN 10 WIDTH 10 product -
             COLUMN 19 ACROSS month: WIDTH 10 SPACE 2 -
                SCALE 2 newsales
          DOEND
    NEXT:
      DOEND
     
    FILECLOSE fil.unit
    POP month district
    RETURN
    error:
    IF fil.unit EQ NA
      THEN SHOW JOINCHARS('Can\'t Open Data File ' ARG(1) '.')
    ELSE IF ERRORNAME NE 'attn' AND ERRORNAME NE 'QUIT'
      THEN DO 
        SHOW JOINCHARS('RECORD ' RECNO(fil.unit) ' is invalid.')
        GOTO NEXT
      DOEND
    ELSE IF ERRORNAME EQ 'noread'
      THEN DO
        SHOW 'File Too Short.'
        FILECLOSE fil.unit
      DOEND
    ELSE DO
      SHOW 'Data Import Interrupted.' 
      FILECLOSE fil.unit
    DOEND
    POP month district
    RETURN

Example 9-134 Additional Processing

When you want to save the dimension value that FILEVIEW read for display or further processing, you can read the field again and save the value in a variable. These lines in a program display the name of the month that FILEVIEW read. The FILEVIEW command saves the month value in column 1 in a variable called `mname`.

    WHILE FILENEXT(fil.unit)
    DO
      FILEVIEW fil.unit WIDTH 8 month WIDTH 5 INTEGER units -
           COLUMN 1 WIDTH 8 mname
      SHOW mname PROMPT
    DOEND

Example 9-135 Using the VALUE Keyword as a Function

Suppose you want to read and report data from a disk file similar to the following, named `numbers.dat`, which has columns 15 characters wide.

               1.0            2.0            3.0            4.0            5.0 
              -1.0           -2.0           -3.0           -4.0           -5.0
               0.0            0.0            1.43900000E+03                1.39900000E+03

You can read this data using the VALUE keyword as a function with FILEVIEW in a program similar to the following one (named `try`). However, this first example does not work. The FILEVIEW command skips fields. The reason for the data skipping is that each time FILEREAD fetches a field from the current record, it updates the column pointer to point past the field. When the next fetch does not specify a position (using the COLUMN, SPACE, or FIELD attribute), data is read from the default position established by the previous fetch. This behavior is typically desirable; however it does not work when multiple fetches are needed to perform a single assignment (for example, when the VALUE function is coded twice in the same IF...THEN...ELSE command block, as shown here). The NAMELIST and DIRLIST attributes return one value for multiple versions of a particular file name in the directory. The NAMELIST attribute also returns only one value for multiple files in the directory with the same root file name but different file types.

    DEFINE try PROGRAM
    PROGRAM
    VARIABLE funit INTEGER
    DEFINE dvar VARIABLE DECIMAL <year>
    PUSH year
    LIMIT year TO LAST 5
    TRAP ON ERROR
    funit=FILEOPEN('numbers.dat' R)
     
    WHILE FILENEXT(funit)
       DO
       FILEVIEW funit ACROSS year: W 15 TEXT dvar = -
          IF FINDCHARS(VALUE, 'e') EQ 0 -  "Incorrect Use of Value
          THEN CONVERT(VALUE, dec) -       "Results in Skipped
          ELSE -9999.99                    "Fields
          REPORT DOWN year dvar
       DOEND
    error:
    FILECLOSE funit
    DELETE dvar
    POP year
    END

When you execute the `try` program,

    try

the output skips numbers, as in the following.

     
    YEAR              DVAR
    -------------  ----------
    Yr93                 2.00
    Yr94                 4.00
    Yr95                   NA
    Yr96            -9,999.99
    Yr97            -9,999.99
       
    YEAR              DVAR
    -------------  ----------
    Yr93                -2.00
    Yr94                -4.00
    Yr95                   NA
    Yr96            -9,999.99
    Yr97            -9,999.99
       
    YEAR              DVAR
    -------------  ----------
    Yr93                 0.00
    Yr94            -9,999.99
    Yr95            -9,999.99
    Yr96            -9,999.99
    Yr97            -9,999.99

However, when the SPACE attribute is used to make the second VALUE back up some distance so it reads the same field that the first VALUE read, everything works fine. SPACE can be used in the preceding sample program by changing the THEN clause to the following clause.

    THEN CONVERT(SPACE -15 VALUE, dec) -

Now when you execute the program,

    try

the output looks like this.

       
    YEAR              DVAR
    -------------  ----------
    Yr93                 1.00
    Yr94                 2.00
    Yr95                 3.00
    Yr96                 4.00
    Yr97                 5.00
       
    YEAR              DVAR
    -------------  ----------
    Yr93                -1.00
    Yr94                -2.00
    Yr95                -3.00
    Yr96                -4.00
    Yr97                -5.00
       
    YEAR              DVAR
    -------------  ----------
    Yr93                 0.00
    Yr94                 0.00
    Yr95            -9,999.99
    Yr96            -9,999.99
    Yr97            -9,999.99

### 9.55 FOR

Within an OLAP DML program, the FOR command specifies one or more dimensions whose status controls the repetition of one or more statements. These statements, along with the FOR statement itself, are often called a FOR loop.

#### Syntax

FOR dimension...      statement

#### Parameters

dimension
One or more dimensions whose current status controls the repetition of one or more statements. The statements are repeated for each combination of the values of the specified dimensions in the current status. When two or more dimensions are specified, the first one varies the slowest. You can specify a composite instead of a dimension.

statement
The statement to be repeated. To repeat two or more statements, enclose them between DO and DOEND.

         DO
           statement1
              ...
           statementN
         DOEND

When you are repeating only one statement after FOR, you can omit DO and DOEND.

#### Usage Notes

FOR Dimension

A FOR statement loops over the values in status of the specified dimension. After the last dimension value, dimension status is restored to what it was before the loop, and execution of the program resumes with the next statement.

Status Inside a Loop

The TEMPSTAT command limits the dimension you are looping over inside a FOR loop or inside a loop that is automatically generated by a REPORT statement.

No Sorting

Because current status defines and controls a FOR loop, you cannot sort the FOR dimension within the loop.

Assignment Statements and Other Looping Statements

An OLAP DML assignment statement (SET), and some other OLAP DML statements automatically loop over dimension status and do so more efficiently than a FOR loop. Be careful not to cause extra looping by putting an assignment statement or one of these statements in a FOR loop.

Branching

You can use BREAK, CONTINUE, and GOTO statements to branch within, or out of, a FOR loop, thereby altering the sequence of statement execution.

Nested FOR Statements

FOR statements can be nested within a FOR loop to any depth when matching DO and DOEND statements are supplied where appropriate.

#### Examples

Example 9-136 Using FOR in a DO Loop to Repeat ROW Commands

In a report program, you want to show the unit sales of tents for each of three months. Use the following FOR statement with a DO/DOEND sequence to repeat ROW commands and BLANK commands for each value of the `month` dimension.

    LIMIT product TO tents
    LIMIT month TO 'Jan96' TO 'Mar96'
    ROW district
    ROW UNDER '-' VALONLY name.product
    BLANK
    FOR month
        DO
          ROW INDENT 5 month WIDTH 6 UNITS
          BLANK
        DOEND

The program lines produce the following report.

    BOSTON
    3-Person Tents
    --------------
     
         Jan96              307
         Feb96              209
         Mar96              277

Example 9-137 Using a FOR Statement for Looping Over Values

The FOR command executes the commands in the loop for each value in the current status of the dimension. You must limit the dimension to the desired values before executing a FOR statement. For example, you can produce a series of output lines that show the price for each product.

    LIMIT month TO FIRST 1
    LIMIT product TO ALL
    FOR product
    SHOW JOINCHARS('Price for ' product ': $' price)

Each output line has the following format.

    Price for TENTS: $165.50

When your data is multidimensional, you can specify multiple dimensions in a FOR statement to control the order of processing. For example, you can use the following statement to control the order in which dimension values of the `units` data are processed.

    FOR month district product
       units = ...

When this assignment statement is executed, the `month` dimension varies the slowest, the `district` dimension varies the next slowest, and the `product` dimension varies the fastest. Thus, a loop is performed over all products for the first district before doing the next district, and over all districts for the first month before doing the next month.

Within the FOR loop, each specified dimension is temporarily limited to a single value while it executes the statements in the loop. You can therefore work with specific combinations of dimension values within the loop.

Example 9-138 Using DO/DOEND in a FOR Loop

When actual figures for unit sales are stored in a variable called `units` and projected figures for unit sales are stored in a variable called `units.plan`, then the code in your loop can compare these figures for the same combination of dimension values.

    LIMIT month TO FIRST 1
    LIMIT product TO ALL
    LIMIT district TO ALL
    FOR district product
       DO
         IF (units.plan - units)/units.plan GT .1
         THEN SHOW JOINCHARS(-
           'Unit sales for ' product ' in ' -
           district ' are not within 10% of plan.')
       DOEND

These lines of code are processed in the following manner.

1.  The data is limited to a specific month.

2.  All the districts and products are placed in status, and the FOR loop is entered.

3.  In the FOR loop, the actual figure is tested against the planned figure. When the unit sales figure for `Tents` in `Boston` is more than 10 percent below the planned figure, then the following message is sent to the current outfile.

        Unit sales for TENTS in BOSTON are not within 10% of plan.

4.  After processing all the products, the FOR loop is complete for the first district.

5.  The loop is executed for the second district, and so on.

    Note that while the FOR loop executes, each dimension that is specified in a FOR statement is limited temporarily to a single value. When you specify `district` in the FOR loop, but not `product`, then all the values of `product` are in status while the FOR loop executes. The IF...THEN...ELSE command then tests data for only the first value of the `product` dimension.

### 9.56 FORECAST

Use the FORECAST command to forecast data by one of three methods: straight-line trend, exponential growth, or Holt-Winters extrapolation. FORECAST performs the calculation according to the method you specify and optionally stores the result in a variable in your analytic workspace.

You can then execute FORECAST.REPORT to produce a standard report of the forecast. You can also use the INFO function to obtain portions of the results for use in your own customized reports or for further analysis.

**Tip:**

Most applications forecast data using a forecasting context rather than using a FORECAST statement. See "[Forecasting Programs](olap-dml-programs.md)" for more information.

#### Syntax

FORECAST \[LENGTH n\] -      \[METHOD {TREND\|EXPONENTIAL\|WINTERS PERIODICITY p \[argument...\]}\] -      \[TIME dimension\] \[FCNAME name\] time-series

where `argument` is one or more of the following clauses that specify the characteristics of the forecast:

- `     ALPHA ``n`
- `     BETA ``n`
- `     GAMMA ``n`
- `     STSMOOTHED ``n ``STSEASONAL ``n-series ``STTREND ``n`
- `     FCSMOOTHED ``name`
- `     FCSEASONAL ``name`
- `     FCTREND ``name`

#### Parameters

LENGTH n
Specifies the number of periods to forecast. The default is zero. When you supply a LENGTH, you must also supply the FCNAME option.

METHOD TREND
(Default) Specifies that the forecasting technique is a straight-line extrapolation of historical data.

METHOD EXPONENTIAL
Specifies that the forecasting technique is an extrapolation of historical data using a constant period-to-period percentage growth.

METHOD WINTERS
Specifies that the forecasting technique is the Holt-Winters method, an extrapolation method that allows for both a linear trend and seasonal fluctuations in the data. Oracle OLAP first constructs three statistically related series for each time period of the historical data. (See "Holt-Winters Constructed Series".) Then, Oracle OLAP produces a forecast from the three series for the specified number of periods into the future.

You can supply several arguments that affect the results of the Holt-Winters forecast. The only required one is PERIODICITY. For the others, Oracle OLAP chooses a reasonable value based on the data available.

PERIODICITY p
The length of the seasonal cycle, where p is an expression that specifies an `INTEGER` greater than or equal to 2. For example, when the data you are analyzing has monthly values, then p is 12.

PERIODICITY is required when you use the METHOD WINTERS keyword.

ALPHA n
BETA n
GAMMA n
Smoothing constants for the first three series calculated for the Holt-Winters forecast (See "Holt-Winters Constructed Series"). ALPHA is for the smoothed data series; BETA is for the seasonal index series; and GAMMA is for the trend series. The value n is a decimal expression greater than 0 and less than or equal to 1. Each value is optional. When you omit one, Oracle OLAP calculates an optimal smoothing constant for that series that minimizes the Mean Absolute Percent Error of the one-period-ahead forecasts in the historical time periods.

STSMOOTHED n STSEASONAL n-series STTREND n
STSMOOTHED specifies the starting value of the smoothed data series (See "Holt-Winters Constructed Series"). The value n is a decimal expression greater than 0. When you specify STSMOOTHED, you must also specify STSEASONAL and STTREND. When you omit it, Oracle OLAP calculates a starting value.

STSEASONAL specifies the starting values for the seasonal index series (See "Holt-Winters Constructed Series"). N-series is an array of decimal values, one for each period in a seasonal cycle. The number of values needed equals the number specified for PERIODICITY (See "Holt-Winters Starting Values"). When you specify STSEASONAL, you must also specify STSMOOTHED and STTREND. When you omit it, Oracle OLAP calculates the starting values.

STTREND specifies the starting value of the trend series (See "Holt-Winters Constructed Series"). N is a decimal value. When you specify STTREND, you must also specify STSMOOTHED and STSEASONAL. When you omit it, Oracle OLAP calculates a starting value.

FCSMOOTHED name
FCSEASONAL name
FCTREND name
Numeric variables in which Oracle OLAP can store the data calculated for the smoothed data series, the seasonal index series, and the trend series (See "Holt-Winters Constructed Series"). The variable specified by name must have the TIME dimension as one of its dimensions. The series calculations produce DECIMAL results, but Oracle OLAP converts the values to the data type of name before storing them. You can save any or all of the preliminary series. When you do not save a series, Oracle OLAP discards the values after completing the forecast.

TIME dimension
The name of the dimension considered to be the time dimension. The current status of dimension determines the number of periods of historical data used to calculate the forecast. The status of the time dimension must be an increasing, consecutive range of values. LENGTH specifies how many values immediately beyond this range is forecast.

When time-series has only one dimension, the time dimension defaults to that. When time-series has multiple dimensions and one dimension has a type of DAY, WEEK, MONTH, QUARTER, or YEAR, then the time dimension defaults to that type. Otherwise, you must specify the time dimension, even when the additional dimensions are limited to a single value. FORECAST only uses the first value in the status for dimensions other than the time dimension.

FCNAME name
The name of a numeric variable in which to store the values calculated by FORECAST. Name must be dimensioned by the time dimension; it can have other dimensions as well. When the data type of name is not decimal, FORECAST converts the values to the appropriate data type.

Fitted values, which correspond to the historical data, are stored in name for the current status of the time dimension. Forecasted values are stored in name for the number of periods specified by LENGTH. These forecasted periods immediately follow the current status of the time dimension.

For the Holt-Winters method, the fitted values are one-period-ahead forecasts calculated at the previous period. The final forecasted values are extrapolated from the fitted data.

For the TREND and EXPONENTIAL methods, FORECAST obtains the fitted values by evaluating the regression equation over the current status of the time dimension.

time-series
An expression that specifies the time series to be forecast. Time-series must be a numeric expression that is dimensioned by the time dimension. When time-series has other dimensions, FORECAST uses the first value only in their current status. The time-series is the historical data from which FORECAST calculates fitted and forecasted values. (See the explanation for FCNAME.)

#### Usage Notes

Forecasting Multidimensional Expressions

When you want to forecast all the values of a multidimensional expression, you can use a program that puts a FORECAST statement inside one or more FOR loops to loop over all the remaining dimensions of the expression.

Obtaining Portions of Results

YOu can obtain portions of the results of FORECAST for your own reports or further analysis, using an INFO statement.

Order of Arguments

You can specify the arguments for FORECAST in any order, except that time-series, the expression specifying the data to be forecast, must be last.

Time-series Data Handling

Each method has its own criteria for handling the input data specified in time-series.

- TREND -- Requires at least two values that are not `NA`; accepts zero and negative values; ignores `NA` values

- EXPONENTIAL -- Requires at least two positive values; ignores zero, negative, and `NA` values

- WINTERS -- Accepts zero and negative values; fills in `NA` values by calculating a weighted moving average

Zero Values

All methods allow zero values in the historical data, specified by time-series, but those time periods are excluded from the Mean Absolute Percent Error (MAPE) calculation.

Holt-Winters Constructed Series

The Holt-Winters forecasting method constructs three statistically related series, which are used to make the actual forecast. These series are:

1.  The smoothed data series, which is the original data with seasonal effects and random error removed.

2.  The seasonal index series, which is the seasonal effect for each period. A value greater than one represents a seasonal increase in the data for that period, and a value less than one is a seasonal decrease in the data. The Holt-Winters method allows seasonal effects to vary over time, so there is a seasonal index value for every historical period.

3.  The trend series, which is the change in the data for each period with the seasonal effects and random error removed. The Holt-Winters method allows the trend effect to vary over time, so there is a trend value for every historical period.

Holt-Winters Omitted Arguments

For the Holt-Winters method, when you omit the STSMOOTHED, STTREND, and STSEASONAL phrases, Oracle OLAP calculates the necessary starting values using an algorithm from Statistical Methods for Forecasting by Abraham and Ledolter. Let Oracle OLAP calculate the starting values when you have little experience with Holt-Winters forecasting.

Holt-Winters Starting Values

When you specify starting values, Oracle OLAP obtains the STSEASONAL starting values by unraveling the values to make a list. The list must have at least the number of values as specified by PERIODICITY. Any more values are ignored; fewer values cause an error. The STSEASONAL expression can be multidimensional and does not have to have the same dimensions as the historical data. (For information about the order of the list when a dimensioned expression is unraveled, see the [UNRAVEL](olap-dml-functions-l-z.md) function.)

Getting Calculated Values

You can find out the values that Oracle OLAP calculates for ALPHA, BETA, and GAMMA and for STSMOOTHED, STSEASONAL, and STTREND by using the INFO function.

Getting a Report of the Forecast

The FORECAST.REPORT program produces a standard report of a forecast created using the FORECAST command.

The report shows the parameters of the forecast, including the forecast formula and Mean Absolute Percent Error, followed by a display of the forecasted values. To produce this report, type the following.

FORECAST.REPORT

#### Examples

Example 9-139 Using the EXPONENTIAL Method

The following statements create a variable called `fcst.sales`, limit the dimensions of the `sales` variable, use the EXPONENTIAL method to forecast sportswear sales for the Chicago district for 1997, and store the results of the calculation in `fcst.sales`.

    DEFINE fcst.sales DECIMAL <month>
    LIMIT product TO 'Sportswear'
    LIMIT district TO 'Chicago'
    LIMIT month TO 'Jan95' TO 'Dec96'
    FORECAST LENGTH 12 METHOD EXPONENTIAL FCNAME fcst.sales -
    time month sales

You can now execute FORECAST.REPORT to see the values that have been generated. Running the FORECAST.REPORT program for that forecast produces the following report.

                         Forecasting Analysis
                         ====================
     
                     Variable to Forecast: SALES
                       Forecast dimension: MONTH
                          Forecast method: EXPONENTIAL
              Mean absolute percent error: 16.64%
     
            Forecast Equation: SALES = 87718.0009541883 *
                               (1.00553383457899 ** MONTH)
     
    MONTH                   Actual Value    Fitted Value
    --------------------    ------------    ------------
    Jan95                      72,123.47       88,203.42
    Feb95                      80,071.75       88,691.52
    Mar95                      78,812.69       89,182.33
    Apr95                      97,413.26       89,675.85
    May95                      94,406.65       90,172.10
      ...                        ...               ...
    Dec96                      72,095.02      100,140.38
      ...                        ...               ...

Example 9-140 Using the WINTERS Method

The following statements limit the `month` dimension, then calculate a forecast that takes into account seasonal influences, using the WINTERS method.

    DEFINE fcst.sales DECIMAL <montH>
    LIMIT month TO year 'Yr95' 'Yr96'
    FORECAST LENGTH 12 METHOD WINTERS -
    PERIODICITY 12, ALPHA .5, BETA .5, GAMMA .5 -
    time month, FCNAME fcst.sales, sales

You can now execute FORECAST.REPORT to see the values that have been generated. Running the FORECAST.REPORT program for that forecast produces the following report.

                         Forecasting Analysis
                         ====================
     
                     Variable to Forecast: SALES
                       Forecast dimension: MONTH
                          Forecast method: WINTERS
                                    Alpha: 0.50
                                     Beta: 0.50
                                    Gamma: 0.50
                              Periodicity: 12
              Mean absolute percent error: 0.20%
     
    MONTH                   Actual Value    Fitted Value
    --------------------    ------------    ------------
    Jan95                      72,123.47       72,154.67
    Feb95                      80,071.75       80,027.51
    Mar95                      78,812.69       79,171.08
    Apr95                      97,413.26       97,200.81
    May95                      94,406.65       94,464.71
     ....                         ...             ...
    Dec97                                      77,867.23

### 9.57 FORECAST.REPORT

The FORECAST.REPORT program produces a standard report of a forecast created using the FORECAST command.

The report shows the parameters of the forecast, including the forecast formula and Mean Absolute Percent Error, followed by a display of the forecasted values.

#### Syntax

FORECAST.REPORT

#### Examples

Example 9-141 Report of Forecast Using the EXPONENTIAL Method

Assume that you have performed the forecast illustrated in Example 9-139. Running the FORECAST.REPORT program for that forecast produces the following report.

                         Forecasting Analysis
                         ====================
     
                     Variable to Forecast: SALES
                       Forecast dimension: MONTH
                          Forecast method: EXPONENTIAL
              Mean absolute percent error: 16.64%
     
            Forecast Equation: SALES = 87718.0009541883 *
                               (1.00553383457899 ** MONTH)
     
    MONTH                   Actual Value    Fitted Value
    --------------------    ------------    ------------
    Jan95                      72,123.47       88,203.42
    Feb95                      80,071.75       88,691.52
    Mar95                      78,812.69       89,182.33
    Apr95                      97,413.26       89,675.85
    May95                      94,406.65       90,172.10
      ...                        ...               ...
    Dec96                      72,095.02      100,140.38
      ...                        ...               ...

Example 9-142 Report of Forecast Using the WINTERS Method

Assume that you have performed the forecast illustrated in Example 9-140. Running the FORECAST.REPORT program for that forecast produces the following report.

                         Forecasting Analysis
                         ====================
     
                     Variable to Forecast: SALES
                       Forecast dimension: MONTH
                          Forecast method: WINTERS
                                    Alpha: 0.50
                                     Beta: 0.50
                                    Gamma: 0.50
                              Periodicity: 12
              Mean absolute percent error: 0.20%
     
    MONTH                   Actual Value    Fitted Value
    --------------------    ------------    ------------
    Jan95                      72,123.47       72,154.67
    Feb95                      80,071.75       80,027.51
    Mar95                      78,812.69       79,171.08
    Apr95                      97,413.26       97,200.81
    May95                      94,406.65       94,464.71
     ....                         ...             ...
    Dec97                                      77,867.23

### 9.58 FULLDSC

The FULLDSC program produces a report that lists the definition of one or more workspace objects, including the properties and triggers of the object(s).

#### Syntax

FULLDSC \[names\]

#### Parameters

names
The names of one or more workspace objects, separated by spaces or commas. FULLDSC shows the full definition of each object specified. When you omit this argument, FULLDSC shows the definition of all objects in the current status of the NAME dimension.

#### Usage Notes

Output of FULLDSC

The FULLDSC program is an extension to the DESCRIBE command. That is, the object definition that you list with FULLDSC includes the definition components that are listed by the DESCRIBE command, followed by any properties that are assigned to the object. Each property is listed on its own line with the word PROPERTY, the name of the property, and its value.

Limiting the Objects Described

Normally, the status of NAME is ALL, so FULLDSC with no argument produces a report that includes the definitions of all objects in your current workspace. However, you can use the LIMIT command in combination with FULLDSC to report the definitions of a particular group of objects in your workspace. Use LIMIT first to limit the status of the NAME dimension to the names of the objects whose definitions you want to see. Then execute a FULLDSC statement with no arguments to list the definitions.

Paginated Output

You can produce paginated output with a FULLDSC statement by setting PAGING to `YES` before using FULLDSC.

Creating Objects with FULLDSC Output

You can use the output from a FULLDSC statement to create objects in other workspaces, because each line of the output is a valid statement. For example, you can execute an OUTFILE statement to send subsequent output to a file, and then execute a FULLDSC statement. You can then access another workspace, and use an INFILE statement to read the FULLDSC output. The same object is created in that workspace.

The output produced by FULLDSC might not exactly reproduce the original PROPERTY statements that created the properties of the object because the original name and value expressions are not saved. In addition, FULLDSC sets the DECIMALS option to 255, which drops trailing zeros. See "Example 9-143".

#### Examples

**Note:**

[Example 10-160](olap-dml-commands-h-z.md)

Example 9-143 Listing the Properties of a Variable

This example produces a report of the full definition of the `actual` variable, to which the properties DECPLACE and REPPRG have been added. The statement

    FULLDSC actual

produces the following output.

    DEFINE ACTUAL VARIABLE DECIMAL <LINE DIVISION MONTH>
    LD Actual $ Financials
    PROPERTY 'DECPLACE' 4
    PROPERTY 'REPPRG' 'qtrrep'

Suppose the DECPLACE property had been specified with the following statement, where PRPNAME is a variable whose value is DECPLACE.

    PROPERTY prpname 4.00

The output from FULLDSC would be the same as that shown in the preceding example; the value 4.00 would be shown as 4. Therefore, when you created an object using the INFILE technique with the FULLDSC output, the newly created property value would have a type of INTEGER (based on the value 4) even though the original property value had a type of DECIMAL (based on the value 4.00). In most cases, this difference is immaterial, because the appropriate conversions are performed when the property values are used.

### 9.59 GOTO

Within an OLAP DML program, the GOTO command alters the sequence of statement execution within a program.

#### Syntax

GOTO label

#### Parameters

label
The name of a label elsewhere in the program constructed following the "Guidelines for Constructing a Label". Execution of the program branches to the line directly following the specified label.

Note that label, as specified in GOTO, must not be followed by a colon. However, the actual label elsewhere in the program must end with a colon.

#### Usage Notes

Guidelines for Constructing a Label

When you use control structures to branch to a particular location, you must provide a label for the location to identify it clearly. When creating a label, follow these guidelines:

- The first character in the label must be a letter, period (`.`), or underscore (`_`).

- The remaining characters in a label can be any combination of letters, numbers, periods, or underscores.

- A label must be followed immediately by a colon (`:`).

- Ensure that the first eight bytes in the label are unique. (Remember that, in your character set, a byte might or might not be equivalent to one character.) A label can contain up to 3999 bytes (the maximum length of a text line minus 1 byte for the colon that identifies a label). However, because only the first eight bytes of a label name are used, you can experience problems with label names greater than eight bytes when the first eight bytes are not unique.

Missing GOTO Label

When an actual label that corresponds to label does not exist elsewhere in the same program, execution stops with an error.

GOTO with IF and WHILE

A GOTO statement can be used with IF...THEN...ELSE or WHILE to set up conditional branching, using the following syntax.

IF boolean-expression    THEN GOTO label1    ELSE GOTO label2

However, to preserve the clarity of your programming logic, minimize your use of GOTO. You can often replace GOTO with one or more statements executed conditionally using FOR, IF...THEN...ELSE, or WHILE. You can also use a SWITCH command to handle different cases within the same program.

GOTO with FOR

You can use a GOTO statement in a FOR loop to branch within, or out of, the loop which changes the sequence of statement execution, depending on where the GOTO statement and the label are positioned.

- A GOTO in a FOR loop that branches to a label within the same loop makes execution continue at the label without affecting the current dimension status. Subsequent repetitions of the loop continue normally. To branch to the end of the loop, just before the DOEND statement, consider using a CONTINUE statement instead.

- A GOTO in a FOR loop that branches to a label outside the loop terminates the effect of the FOR statement. Execution continues at the specified label and dimension status is restored to what it was before the loop. To branch to the statement immediately following the DOEND of a loop, consider using a BREAK statement instead.

When you use a GOTO statement outside a FOR loop to branch into the loop (that is, to a label inside the loop), an error occurs after execution passes through the rest of the loop once.

TEMPSTAT and GOTO Statements

Within a FOR loop of a program, when a DO ... DOEND phrase follows TEMPSTAT, status is restored when the DOEND, BREAK, or GOTO is encountered.

Alternatives to GOTO Statement

While GOTO makes it easy to branch within a program, frequent use of it can obscure the logic of your program, making it difficult to follow its flow, particularly when you have a complex program with several labels and GOTO statements that skip over large portions of code.

To keep the logic of your programs clear, minimize your use of GOTO.

Sometimes a GOTO statement is the best programming technique, but often there are better alternatives. For example:

- Instead of using GOTO statements in a FOR statement, you can often place your alternative sets of statements between DO ... DOEND statements within an IF...THEN...ELSE command itself.

- When each set of statements is long or you want to use them in multiple places in your program, then you might consider placing them in subprograms. Then, you can use an IF...THEN...ELSE command to choose between two different programs, or use a SWITCH command to choose among many different programs.

Example 9-137 illustrates how the FOR command loops over values. Example 9-138 illustrates using DO ... DOEND within a FOR loop.

#### Examples

Example 9-144 Using GOTO with IF

This example shows a program that produces a report for one of three areas, depending on what argument the user supplies when running the program. When the user specifies `EAST`, `WEST`, or `CENTRAL`, execution branches to a corresponding label, and the statements following it (statement group 1, 2, or 3) are executed. When the user specifies anything else, execution branches to the `argerror` label, after which statements handle the error.

    DEFINE flexrpt PROGRAM
    PROGRAM
    IF NOT INLIST('East\nWest\nCentral', UPCASE(ARG(1)))
       THEN GOTO argerror
     
    SWITCH &UPCASE(ARG(1))
    DO
    CASE 'EAST':
       ..." (statement group 1)
       BREAK
    CASE 'WEST':
       ... "(statement group 2)
       BREAK
    CASE 'CENTRAL':
       ..." (statement group 3)
       BREAK
    DOEND
     
    argerror:
       ..." statements to handle error)
       
    END

### 9.60 GROUPINGID command

The GROUPINGID command populates a previously-defined object with the grouping ids for the values of a hierarchical dimension, and creates and populates the [\$GID_DEPTH](olap-dml-properties.md) system property.

A grouping id is a numeric value that corresponds to a level of a hierarchical dimension. The grouping id for the lowest-level of the hierarchy is `0` (zero). Grouping ids are especially useful for identifying values of different levels of a hierarchical dimension. Dimension values in the same level of the hierarchy have the same value for their grouping id. Selecting dimension values for a specific level is easier with grouping ids because the desired values can be identified with a single condition of groupingid = n.

Typically, you use a GROUPINGID statement when you are planning on accessing analytic workspace data in SQL using the `OLAP_TABLE `function.

**See Also:**

"Gidrel Relation"in [Objects that Support the Use of Hierarchies](olap-dml-basic-concepts.md) for more information and the GROUPING_ID function in Oracle Database SQL Language Reference for more information on grouping ids

#### Syntax

GROUPINGID \[parent-relation\] INTO  destination-object -     {USING level-relation} \[INHIERARCHY {inh-variable \| inh-valueset}\] \[LEVELORDER lo-valueset\] -    \[ROLLUP \| GROUPSET\]

where `destination-object `is one of the following:

- `grouping-relation`
- `grouping-variable`
- `grouping-surrogate`

#### Parameters

parent-relation
A self-relation for a hierarchical dimension. This self-relation is dimensioned by a hierarchical dimension. The values of the self-relation are the parents of each value in the hierarchical dimension. The parent-relation argument is optional only when you use the GROUPINGID command to populate a surrogate and the GROUPINGID command includes a LEVELORDER clause.

grouping-relation
The name of a previously-defined relation. One dimension of grouping-relation must be the hierarchical dimension. The values of grouping-relation are calculated and populated when the GROUPINGID command executes. When you specify a relation as the destination object, Oracle OLAP automatically creates and sets the [\$GID_DEPTH](olap-dml-properties.md) property on the relation when it populates it.

grouping-variable
The name of a previously-defined numeric variable. One dimension of grouping-variable must be the hierarchical dimension. The data type of grouping-variable can be any numeric type including `NUMBER`. The values of grouping-variable are calculated and populated when the GROUPINGID command executes.See the DEFINE VARIABLE command for information on defining variables.

grouping-surrogate
The name of a previously-defined surrogate for the hierarchical dimension. The values of grouping-surrogate are calculated and populated when the GROUPINGID command executes. See the DEFINE SURROGATE command for information on defining surrogates.

USING
Specifies that the level of the values of the hierarchical dimension are to be considered when creating grouping ids.

level-relation
A relation that is dimensioned by the hierarchical dimension. For each value of the hierarchical dimension, the relation has its value the name of the level for the dimension's value.

INHIERARCHY
Specifies that only some values of the hierarchical dimension are to be considered when creating grouping ids.

**Note:**

You cannot specify an INHIERARCHY clause when you specify ROLLUP or GROUPSET.

inh-variable
A BOOLEAN variable that is dimensioned by the hierarchical dimension and, when the hierarchical dimension is a multi-hierarchical dimension, by a dimension that is the names of the hierarchies. The values of the variable are `TRUE` when the dimension value is in a hierarchy and `FALSE` when it is not.

inh-valueset
The name of a valueset object whose values identify the hierarchical dimension values to be considered when creating grouping ids. Values not included in the valueset are ignored.

LEVELORDER
Specifies the top-down order of the levels when creating grouping ids.

lo-valueset
The name of a valueset object whose values are the names of the levels to be used when creating grouping ids. The order of the values in the valueset object determine the grouping id assigned.

ROLLUP
Specifies that Oracle OLAP creates the grouping ids in the same manner as SQL does when you specify ROLLUP in a SQL `SELECT` statement.

**See Also:**

Rollup cube clause in Oracle Database SQL Language Reference

The ROLLUP keyword is valid only when the destination object is a relation. When you specify this keyword, [\$GID_TYPE](olap-dml-properties.md) and [\$GID_LIST](olap-dml-properties.md) properties.

GROUPSET
Specifies that Oracle OLAP creates the grouping ids in the same manner as SQL does when you specify GROUPING SET in a SQL `SELECT` statement.

**See Also:**

[Grouping sets clause](../sqlrf/SELECT.md) in Oracle Database SQL Language Reference for more information

The GROUPSET keyword is valid only when the destination object is a relation. When you specify this keyword, Oracle OLAP also creates and populates two properties on the grouping id relation: the [\$GID_TYPE](olap-dml-properties.md) and [\$GID_LIST](olap-dml-properties.md) properties.

#### Examples

Example 9-145 Using GROUPINGID Command to Populate a Relation with Grouping Ids

Assume your analytic workspace contains the following objects.

    DEFINE GEOG DIMENSION TEXT
    LD A dimension with two hierarchies for geography

    DEFINE geog_hierlist DIMENSION TEXT
    LD List of Hierarchies for geog dimension

    DEFINE GEOG_INHIER VALUESET GEOG <GEOG_HIERLIST>
    LD A valueset of geog that are just the values in each hierarchy

    DEFINE GEOG_PARENTREL RELATION GEOG <GEOG GEOG_HIERLIST>
    LD Self-relation for geog showing parents of each value

    DEFINE GEOG_INHIER VALUESET GEOG <GEOG_HIERLIST>
    LD A valueset of geog that are just the values in each hierarchy

    DEFINE GEOG_LEVELREL RELATION GEOG_LEVELLIST <GEOG GEOG_HIERLIST>
    LD Level of each dimension member for geog

Assume that those objects have the values shown in the following reports.

    REPORT geog_hierlist

    GEOG_HIERLIST
    --------------
    Political_Geog
    Sales_Geog

    REPORT DOWN geog W 20 geog_parentrel

                   -------------GEOG_PARENTREL--------------
                   --------------GEOG_HIERLIST--------------
    GEOG              Political_Geog         Sales_Geog
    -------------- -------------------- --------------------
    Boston         MA                   MA
    Springfield    MA                   MA
    Hartford       CT                   CT
    Mansfield      CT                   CT
    Montreal       Quebec               Quebec
    Walla Walla    WA                   WA
    Portland       WA                   WA
    Oakland        CA                   CA
    San Diego      CA                   CA
    MA             USA                  East
    CT             USA                  East
    WA             USA                  West
    CA             USA                  West
    Quebec         Canada               East
    East           NA                   All Regions
    West           NA                   All Regions
    All Regions    NA                   NA
    USA            All Countries        NA
    Canada         All Countries        NA
    All Countries  NA                   NA

    ->REPORT W 20 geog_inhier

    GEOG_HIERLIST      GEOG_INHIER
    -------------- --------------------
    Political_Geog Boston
                   Springfield
                   Hartford
                   Mansfield
                   Montreal
                   Walla Walla
                   Portland
                   Oakland
                   San Diego
                   MA
                   CT
                   WA
                   CA
                   Quebec
                   USA
                   Canada
                   All Countries
    Sales_Geog     Boston
                   Springfield
                   Hartford
                   Mansfield
                   Montreal
                   Walla Walla
                   Portland
                   Oakland
                   San Diego
                   MA
                   CT
                   WA
                   CA
                   Quebec
                   East
                   West
                   All Regions

    ->REPORT DOWN geog W 20 geog_levelrel

                   --------------GEOG_LEVELREL--------------
                   --------------GEOG_HIERLIST--------------
    GEOG              Political_Geog         Sales_Geog
    -------------- -------------------- --------------------
    Boston         City                 City
    Springfield    City                 City
    Hartford       City                 City
    Mansfield      City                 City
    Montreal       City                 City
    Walla Walla    City                 City
    Portland       City                 City
    Oakland        City                 City
    San Diego      City                 City
    MA             State-Prov           State-Prov
    CT             State-Prov           State-Prov
    WA             State-Prov           State-Prov
    CA             State-Prov           State-Prov
    Quebec         State-Prov           State-Prov
    East           NA                   Region
    West           NA                   Region
    All Regions    NA                   All Regions
    USA            Country              NA
    Canada         Country              NA
    All Countries  All Countries        NA


To create grouping ids for the values of geog, you first define a GID dimension with the following definition and you populate it with more values than you expect to have for grouping ids.

    DEFINE GID_DIMENSION DIMENSION NUMBER (16,0)

Next you define a relation to hold the grouping ids.

    DEFINE GEOG_GIDREL RELATION GID_DIMENSION <GEOG GEOG_HIERLIST>

Now you execute the GROUPINGID command to populate the geog_gidrel relation.

    GROUPINGID geog_parentrel INTO geog_gidrel USING geog_levelrel -
           INHIERARCHY geog_inhier

A report of geog_gidrel shows that the relation is now populated.

    REPORT down geog w 20 geog_gidrel

                   ---------------GEOG_GIDREL---------------
                   --------------GEOG_HIERLIST--------------
    GEOG              Political_Geog         Sales_Geog
    -------------- -------------------- --------------------
    Boston         0                    0
    Springfield    0                    0
    Hartford       0                    0
    Mansfield      0                    0
    Montreal       0                    0
    Walla Walla    0                    0
    Portland       0                    0
    Oakland        0                    0
    San Diego      0                    0
    MA             1                    1
    CT             1                    1
    WA             1                    1
    CA             1                    1
    Quebec         1                    1
    East           NA                   3
    West           NA                   3
    All Regions    NA                   7
    USA            3                    NA
    Canada         3                    NA
    All Countries  7                    NA


When you execute a FULLDSC of geog_gidrel, you can see that the \$GID_DEPTH property has been created and populated for `geog_gidrel`.

    DEFINE GEOG_GIDREL RELATION GID_DIMENSION <GEOG GEOG_HIERLIST>
    PROPERTY '$GID_DEPTH' 4

Example 9-146 Using GROUPINGID to Populate a Variable with Grouping Ids

Assume that you have the following objects in your analytic workspace.

    DEFINE geography DIMENSION TEXT WIDTH 12
    LD Geography Dimension Values
    DEFINE geography.parent RELATION geography <geography>
    LD Child-parent relation for geography
    DEFINE geography.hierarchyid DIMENSION INTEGER
    LD Dimension whose values are ids for hierarchies in geography

To create a grouping id variable for the `Standard` hierarchy of geography, define a child-parent relation of only those values that are in the hierarchy whose grouping ids you want to generate, and define a variable to hold the grouping ids. Examples of these definitions follow.

    DEFINE geog.gid INTEGER VARIABLE <geography>
    DEFINE geography.newparent RELATION geography <geography>

Then populate these variables using statements similar to these.

    " Populate the child-parent relation for hierarchy 1
    geography.newparent = geography.parent(geography.hierarchyid 1)
    " Populate the grouping id variables
    GROUPINGID geography.newparent INTO geog.gid

Reports for the new objects created by this code (`geography.newparen`t and `geog.gid`) follow.

    REPORT geography.newparent

    GEOGRAPHY          GEOGRAPHY.NEWPARENT
    ---------------- ----------------
    World            NA
    Americas         World
    Canada           Americas
    Toronto          Canada
    Montreal         Canada
    Ottawa           Canada
    Vancouver        Canada
    Edmonton         Canada
    Calgary          Canada
    Usa              Americas
    Boston           Usa
    Losangeles       Usa
    Dallas           Usa
    Denver           Usa
    Newyork          Usa
    Chicago          Usa
    Seattle          Usa
    Mexico           Americas
    ...              ...
    Japan            Asia
    Tokyo            Japan
    Osaka            Japan
    Kyoto            Japan
    China            Asia
    Beijing          China
    Shanghai         China
    ...              ...
    India            Asia
    Ireland          Europe
    Taiwan           Asia
    Thailand         Asia

    REPORT geog.gid
    GEOGRAPHY            GEOG.GID
    ---------------- ----------------
    World                           7
    Americas                        3
    Canada                          1
    Toronto                         0
    Montreal                        0
    Ottawa                          0
    Vancouver                       0
    Edmonton                        0
    Calgary                         0
    Usa                             1
    Boston                          0
    Losangeles                      0
    Dallas                          0
    Denver                          0
    Newyork                         0
    Chicago                         0
    Seattle                         0
    Mexico                          1
    ...                             ...
    Japan                           1
    Tokyo                           0
    Osaka                           0
    Kyoto                           0
    China                           1
    Beijing                         0
    Shanghai                        0
    ...                             ...
    India                           1
    Ireland                         1
    Taiwan                          1
    Thailand                        1
