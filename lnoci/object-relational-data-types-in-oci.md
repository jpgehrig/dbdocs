This chapter describes the purpose and structure of each of the data types that can be manipulated by the OCI data type mapping and manipulation functions.

This chapter also summarizes the different function groups giving lists of available functions and their purposes. In addition, provides information about how to use these data types in bind and define operations within an OCI application.

This chapter contains these topics:

- Overview of OCI Functions for Objects

- About Mapping Oracle Data Types to C

- About Manipulating C Data Types with OCI

- Date (OCIDate)

- Datetime and Interval (OCIDateTime, OCIInterval)

- Number (OCINumber)

- Fixed or Variable-Length String (OCIString)

- Raw (OCIRaw)

- Collections (OCITable, OCIArray, OCIColl, OCIIter)

- About Multilevel Collection Types

- REF (OCIRef)

- Object Type Information Storage and Access

- AnyType, AnyData, and AnyDataSet Interfaces

- About Binding Named Data Types

- About Defining Named Data Types

- About Binding and Defining Oracle C Data Types

- SQLT_NTY Bind and Define Examples

### 20.1 Overview of OCI Functions for Objects

The OCI data type mapping and manipulation functions provide the ability to manipulate instances of predefined Oracle C data types.

These data types are used to represent the attributes of user-defined data types, including object types in Oracle Database.

Each group of functions within OCI is distinguished by a particular naming convention. The data type mapping and manipulation functions, for example, can be easily recognized because the function names start with the prefix OCI, followed by the name of a data type, as in `OCIDateFromText()` and `OCIRawSize()`. As will be explained later, the names can be further subdivided into function groups that operate on a particular type of data.

The predefined Oracle C types on which these functions operate are also distinguished by names that begin with the prefix OCI, as in `OCIDate` or `OCIString`.

The data type mapping and manipulation functions are used when an application must manipulate, bind, or define attributes of objects that are stored in an Oracle database, or that have been retrieved by a SQL query. Retrieved objects are stored in the client-side object cache.

The OCI client must allocate a descriptor before performing a bind or define operation. `OCIStmtExecute()` and `OCIStmtFetch2()` cannot allocate the memory for the descriptors if they are not allocated by `OCIDescriptorAlloc()`.

These functions are valid only when an OCI application is running in object mode. For information about initializing OCI in object mode and creating an OCI application that accesses and manipulates objects, see [About Initializing the Environment and the Object Cache](oci-object-relational-programming.md).

**Note:**

Operations on object types such as `OCIDate`, allow the address of the result to be the same as that of one of the operands.

**See Also:**

- [OCIDateFromText()](oci-date-datetime-and-interval-functions.md)

- [OCIRawSize()](oci-raw-functions.md)

- [Object Advanced Topics in OCI](object-advanced-topics-in-oci.md) for more information about retrieved objects being stored in the client-side object cache

- [OCIStmtExecute()](statement-functions.md)

- [OCIStmtFetch2()](statement-functions.md)

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)

- [Oracle Database Object-Relational Developer's Guide](../adobj/key-features-object-relational-model.md) for detailed information about object types, attributes, and collection data types

### 20.2 About Mapping Oracle Data Types to C

Oracle provides a rich set of predefined data types with which you can create tables and specify user-defined data types (including object types).

Object types extend the functionality of Oracle Database by allowing you to create data types that precisely model the types of data with which they work. This can provide increased efficiency and ease-of-use for programmers who are accessing the data.

You can use `NCHAR` and `NVARCHAR2` as attributes in objects and map to `OCIString *` in C.

Database tables and object types are based upon the data types supplied by Oracle. These tables and types are created with SQL statements and stored using a specific set of Oracle internal data types, like `VARCHAR2` or `NUMBER`. For example, the following SQL statements create a user-defined `address` data type and an object table to store instances of that type:

    CREATE TYPE address AS OBJECT
    (street1    varchar2(50),
    street2     varchar2(50),
    city        varchar2(30),
    state       char(2),
    zip         number(5));
    CREATE TABLE address_table OF address;

The new `address` type could also be used to create a regular table with an object column:

    CREATE TABLE employees
    (name         varchar2(30),
    birthday      date,
    home_addr     address);

An OCI application can manipulate information in the `name` and `birthday` columns of the `employees` table using straightforward bind and define operations in association with SQL statements. Accessing information stored as attributes of objects requires some extra steps.

The OCI application first needs a way to represent the objects in a C language format. This is accomplished by using the Object Type Translator (OTT) to generate C struct representations of user-defined types. The elements of these structs have data types that represent C language mappings of Oracle data types.

An additional C type, `OCIInd`, is used to represent null indicator information corresponding to attributes of object types.

This section includes the following topic: OCI Type Mapping Methodology.

**See Also:**

- [Table 24-1](using-object-type-translator-in-oci.md) for the available Oracle types and their C mappings you can use as object attribute types

- [Using the Object Type Translator with OCI](using-object-type-translator-in-oci.md) for more information and examples about using OTT

#### 20.2.1 OCI Type Mapping Methodology

Oracle followed a distinct design philosophy when specifying the mappings of Oracle predefined types.

The current system has the following benefits and advantages:

- The actual representation of data types like `OCINumber` is opaque to client applications, and the data types are manipulated with a set of predefined functions. This allows the internal representation to change to accommodate future enhancements without breaking user code.

- The implementation is consistent with object-oriented paradigms in which class implementation is hidden and only the required operations are exposed.

- This implementation can have advantages for programmers. Consider writing a C program to manipulate Oracle number variables without losing the accuracy provided by Oracle numbers. To do this operation in Oracle Database Release 7, you would have had to issue a "`SELECT ... FROM DUAL`" statement. In later releases, this is accomplished by invoking the `OCINumber*()` functions.

### 20.3 About Manipulating C Data Types with OCI

Shows how you can manipulate C data types with OCI and shows the various function prefixes, along with example function names and the data types on which the functions operate.

In an OCI application, the manipulation of data may be as simple as adding together two integer variables and storing the result in a third variable:

    int    int_1, int_2, sum;
    ...
    /* some initialization occurs */
    ...
    sum = int_1 + int_2;

The C language provides a set of predefined operations on simple types such as `integer`. However, the C data types listed in [Table 24-1](using-object-type-translator-in-oci.md) are not simple C primitives. Types such as `OCIString` and `OCINumber` are actually structs with a specific Oracle-defined internal structure. It is not possible to simply add together two `OCINumber`s and store the value in the third.

The following is not valid:

    OCINumber    num_1, num_2, sum;
    ...
    /* some initialization occurs */
    ...
    sum = num_1 + num_2;           /* NOT A VALID OPERATION */

The OCI data type mapping and manipulation functions are provided to enable you to perform operations on these new data types. For example, the preceding addition of `OCINumber`s could be accomplished as follows, using the `OCINumberAdd()` function:

    OCINumber    num_1, num_2, sum;
    ...
    /* some initialization occurs */
    ...
    OCINumberAdd(errhp, &num_1, &num_2, &sum): /* errhp is error handle */

OCI provides functions to operate on each of the new data types. The names of the functions provide information about the data types on which they operate. The first three letters, OCI, indicate that the function is part of OCI. The next part of the name indicates the data type on which the function operates. Table 20-1 shows the various function prefixes, along with example function names and the data types on which the functions operate.

Table 20-1 Function Prefix Examples

| Function Prefix | Example                 | Operates on                            |
|:----------------|:------------------------|:---------------------------------------|
| `OCIColl`       | `OCICollGetElem()`      | `OCIColl, OCIIter, OCITable, OCIArray` |
| `OCIDate`       | `OCIDateDaysBetween()`  | `OCIDate`                              |
| `OCIDateTime`   | `OCIDateTimeSubtract()` | `OCIDate, OCIDateTime`                 |
| `OCIInterval`   | `OCIIntervalToText()`   | `OCIInterval`                          |
| `OCIIter`       | `OCIIterInit()`         | `OCIIter`                              |
| `OCINumber`     | `OCINumberAdd()`        | `OCINumber`                            |
| `OCIRaw`        | `OCIRawResize()`        | `OCIRaw *`                             |
| `OCIRef`        | `OCIRefAssign()`        | `OCIRef *`                             |
| `OCIString`     | `OCIStringSize()`       | `OCIString *`                          |
| `OCITable`      | `OCITableLast()`        | `OCITable *`                           |

The structure of each of the data types is described later in this chapter, along with a list of the functions that manipulate that type.

This section includes the following topic: Precision of Oracle Number Operations.

#### 20.3.1 Precision of Oracle Number Operations

Oracle numbers have a precision of 38 decimal digits.

All Oracle number operations are accurate to the full precision, with the following exceptions:

- Inverse trigonometric functions are accurate to 28 decimal digits.

- Other transcendental functions, including trigonometric functions, are accurate to approximately 37 decimal digits.

- Conversions to and from native floating-point types have the precision of the relevant floating-point type, not to exceed 38 decimal digits.

### 20.4 Date (OCIDate)

The Oracle date format is mapped in C by the `OCIDate` type, which is an opaque C struct. Elements of the struct represent the year, month, day, hour, minute, and second of the date.

The specific elements can be set and retrieved using the appropriate OCI functions.

The `OCIDate` data type can be bound or defined directly using the external typecode `SQLT_ODT` in the bind or define call.

Unless otherwise specified, the term date in these function calls refers to a value of type `OCIDate`.

**See Also:**

[OCI Data Type Mapping and Manipulation Functions](oci-data-type-mapping-and-manipulation-functions.md) for the prototypes and descriptions of all the functions

This section includes the following topic: Date Example.

#### 20.4.1 Date Example

Shows how to manipulate an attribute of type `OCIDate` using OCI calls.

Example 20-1 provides examples of how to manipulate an attribute of type `OCIDate` using OCI calls. For this example, assume that `OCIEnv` and `OCIError` have been initialized.

The output is:

    For: FRIDAY   , OCTOBER   05, 1990
    The last day of the month is: WEDNESDAY, OCTOBER   31, 1990
    The next Wednesday is: WEDNESDAY, OCTOBER   10, 1990

Example 20-1 Manipulating an Attribute of Type OCIDate

    #define FMT "DAY, MONTH DD, YYYY"
    #define LANG "American"
    struct person
    {
    OCIDate start_date;
    };
    typedef struct person person;

    OCIError *err;
    person *tim;
    sword status;                      /* error status */
    uword invalid;
    OCIDate last_day, next_day;
    text buf[100], last_day_buf[100], next_day_buf[100];
    ub4 buflen = sizeof(buf);

    /* Pin tim person object in the object cache. */
    /*  For this example, assume that
    /* tim is pointing to the pinned object. */
    /* set the start date of tim */

    OCIDateSetTime(&tim->start_date,8,0,0);
    OCIDateSetDate(&tim->start_date,1990,10,5);

    /* check if the date is valid */
    if (OCIDateCheck(err, &tim->start_date, &invalid) != OCI_SUCCESS)
    /* error handling code */

    if (invalid)
    /* error handling code */

    /* get the last day of start_date's month */
    if (OCIDateLastDay(err, &tim->start_date, &last_day) != OCI_SUCCESS)
    /* error handling code */

    /* get date of next named day */
    if (OCIDateNextDay(err, &tim->start_date, "Wednesday",    strlen("Wednesday"),
    &next_day) != OCI_SUCCESS)
    /* error handling code */
    /* convert dates to strings and print the information */
    /* first convert the date itself*/
    buflen = sizeof(buf);
    if (OCIDateToText(err, &tim->start_date, FMT, sizeof(FMT)-1, LANG,
        sizeof(LANG)-1,             &buflen, buf) != OCI_SUCCESS)
    /* error handling code */

    /* now the last day of the month */
    buflen = sizeof(last_day_buf);
    if (OCIDateToText(err, &last_day, FMT, sizeof(FMT)-1, LANG,    sizeof(LANG)-1,
    &buflen, last_day_buf) != OCI_SUCCESS)
    /* error handling code */

    /* now the first Wednesday after this date */
    buflen = sizeof(next_day_buf);
    if (OCIDateToText(err, &next_day, FMT, sizeof(FMT)-1, LANG,
       sizeof(LANG)-1, &buflen, next_day_buf) != OCI_SUCCESS)
    /* error handling code */

    /* print the information */
    printf("For: %s\n", buf);
    printf("The last day of the month is: %s\n", last_day_buf);
    printf("The next Wednesday is: %s\n", next_day_buf);

**See Also:**

- [OCI Environment Initialization](oci-programming-basics.md) for information about initializing `OCIEnv` and `OCIError`

- [Object Cache Operations](object-advanced-topics-in-oci.md) for information about pinning.

### 20.5 Datetime and Interval (OCIDateTime, OCIInterval)

The `OCIDateTime` data type is an opaque structure used to represent Oracle time-stamp data types (`TIMESTAMP`, `TIMESTAMP` `WITH` `TIME` `ZONE`, `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`) and the `ANSI DATE` data type.

You can set or retrieve the data in these types (that is, year, day, fractional second) using the appropriate OCI functions.

The `OCIInterval` data type is also an opaque structure and is used to represent Oracle interval data types (`INTERVAL` `YEAR` `TO` `MONTH`, `INTERVAL` `DAY` `TO` `SECOND`).

You can bind and define `OCIDateTime` and `OCIInterval` data using the following external typecodes shown in Table 20-2 in the bind or define call.

Table 20-2 Binding and Defining Datetime and Interval Data Types

| OCI Data Type | Type of Data                   | External Typecode for Binding/Defining |
|:--------------|:-------------------------------|:---------------------------------------|
| `OCIDateTime` | ANSI DATE                      | SQLT_DATE                              |
| `OCIDateTime` | TIMESTAMP                      | SQLT_TIMESTAMP                         |
| `OCIDateTime` | TIMESTAMP WITH TIME ZONE       | SQLT_TIMESTAMP_TZ                      |
| `OCIDateTime` | TIMESTAMP WITH LOCAL TIME ZONE | SQLT_TIMESTAMP_LTZ                     |
| `OCIInterval` | INTERVAL YEAR TO MONTH         | SQLT_INTERVAL_YM                       |
| `OCIInterval` | INTERVAL DAY TO SECOND         | SQLT_INTERVAL_DS                       |

In general, functions that operate on `OCIDateTime` data are also valid for `OCIDate` data.

This section includes the following topics:

- About Datetime Functions

- Datetime Example

- About Interval Functions

**See Also:**

- Table 20-3 and Table 20-4 for information about OCI functions that operate on datetime and interval data

- [OCI Date, Datetime, and Interval Functions](oci-date-datetime-and-interval-functions.md) for more detailed information about datetime and interval functions

#### 20.5.1 About Datetime Functions

Lists and describes functions that operate on `OCIDateTime` values.

The following functions operate on `OCIDateTime` values. Some of these functions also perform arithmetic operations on datetime and interval values. Some functions may only work for certain datetime types. The possible types are:

- `SQLT_DATE` - `DATE`

- `SQLT_TIMESTAMP` - `TIMESTAMP`

- `SQLT_TIMESTAMP_TZ` - `TIMESTAMP` `WITH` `TIME` `ZONE`

- `SQLT_TIMESTAMP_LTZ` - `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`

See the individual function descriptions listed in Table 20-3 for more information about input types that are valid for a particular function.

Table 20-3 Datetime Functions

| Function                                                                      | Purpose                                                                                                              |
|:------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| [OCIDateTimeAssign()](oci-date-datetime-and-interval-functions.md)            | Performs datetime assignment                                                                                         |
| [OCIDateTimeCheck()](oci-date-datetime-and-interval-functions.md)             | Checks if the given date is valid                                                                                    |
| [OCIDateTimeCompare()](oci-date-datetime-and-interval-functions.md)           | Compares two datetime values                                                                                         |
| [OCIDateTimeConstruct()](oci-date-datetime-and-interval-functions.md)         | Constructs a datetime descriptor                                                                                     |
| [OCIDateTimeConvert()](oci-date-datetime-and-interval-functions.md)           | Converts one datetime type to another                                                                                |
| [OCIDateTimeFromArray()](oci-date-datetime-and-interval-functions.md)         | Converts an array containing a date to an `OCIDateTime` descriptor                                                   |
| [OCIDateTimeFromText()](oci-date-datetime-and-interval-functions.md)          | Converts the given string to Oracle datetime type in the `OCIDateTime` descriptor, according to the specified format |
| [OCIDateTimeGetDate()](oci-date-datetime-and-interval-functions.md)           | Gets the date (year, month, day) portion of a datetime value                                                         |
| [OCIDateTimeGetTime()](oci-date-datetime-and-interval-functions.md)           | Gets the time (hour, minute, second, fractional second) from datetime value                                          |
| [OCIDateTimeGetTimeZoneName()](oci-date-datetime-and-interval-functions.md)   | Gets the time zone name portion of a datetime value                                                                  |
| [OCIDateTimeGetTimeZoneOffset()](oci-date-datetime-and-interval-functions.md) | Gets the time zone (hour, minute) portion of a datetime value                                                        |
| [OCIDateTimeIntervalAdd()](oci-date-datetime-and-interval-functions.md)       | Adds an interval to a datetime to produce a resulting datetime                                                       |
| [OCIDateTimeIntervalSub()](oci-date-datetime-and-interval-functions.md)       | Subtracts an interval from a datetime and stores the result in a datetime                                            |
| [OCIDateTimeSubtract()](oci-date-datetime-and-interval-functions.md)          | Takes two datetimes as input and stores their difference in an interval                                              |
| [OCIDateTimeSysTimeStamp()](oci-date-datetime-and-interval-functions.md)      | Gets the system current date and time as a time stamp with time zone                                                 |
| [OCIDateTimeToArray()](oci-date-datetime-and-interval-functions.md)           | Converts an `OCIDateTime` descriptor to an array                                                                     |
| [OCIDateTimeToText()](oci-date-datetime-and-interval-functions.md)            | Converts the given date to a string according to the specified format                                                |
| [OCIDateZoneToZone()](oci-date-datetime-and-interval-functions.md)            | Converts the date from one time zone to another time zone                                                            |

#### 20.5.2 Datetime Example

Shows how to use an `OCIDateTime` data type to select data from a `TIMESTAMP WITH LOCAL TIME ZONE` column.

The code fragment in Example 20-2 shows how to use an `OCIDateTime` data type to select data from a `TIMESTAMP WITH LOCAL TIME ZONE` column.

Example 20-2 Manipulating an Attribute of Type OCIDateTime

    ...

    /* allocate the program variable for storing the data */
    OCIDateTime *tstmpltz = (OCIDateTime *)NULL;

    /* Col1 is a time stamp with local time zone column */
    OraText *sqlstmt = (OraText *)"SELECT col1 FROM foo";

    /* Allocate the descriptor (storage) for the data type */
    status = OCIDescriptorAlloc(envhp,(void  **)&tstmpltz, OCI_DTYPE_TIMESTAMP_LTZ,
             0, (void  **)0);
    ....

    status = OCIStmtPrepare (stmthp, errhp, sqlstmt, (ub4)strlen ((char *)sqlstmt),
             (ub4)OCI_NTV_SYNTAX, (ub4)OCI_DEFAULT);

    /* specify the define buffer for col1 */
    status = OCIDefineByPos(stmthp, &defnp, errhp, 1, &tstmpltz, sizeof(tstmpltz),
             SQLT_TIMESTAMP_LTZ, 0, 0, 0, OCI_DEFAULT);

    /* Execute and Fetch */
    OCIStmtExecute(svchp, stmthp, errhp, 1, 0,(OCISnapshot *) NULL,
             (OCISnapshot *)NULL, OCI_DEFAULT)

    At this point tstmpltz contains a valid time stamp with local time zone data. You
    can get the time zone name of the datetime data using:

    status = OCIDateTimeGetTimeZoneName(envhp, errhp, tstmpltz, (ub1 *)buf,
             (ub4 *)&buflen);
    ...

#### 20.5.3 About Interval Functions

Lists and describes the interval functions.

The functions listed in Table 20-4 operate exclusively on interval data. In some cases it is necessary to specify the type of interval involved. Possible types include:

- `SQLT_INTERVAL_YM` - interval year to month

- `SQLT_INTERVAL_DS` - interval day to second

See the individual function descriptions for more detailed information.

Table 20-4 Interval Functions

| Function                                                                 | Purpose                                                                        |
|:-------------------------------------------------------------------------|:-------------------------------------------------------------------------------|
| [OCIIntervalAdd()](oci-date-datetime-and-interval-functions.md)          | Adds two intervals to produce a resulting interval                             |
| [OCIIntervalAssign()](oci-date-datetime-and-interval-functions.md)       | Copies one interval to another                                                 |
| [OCIIntervalCheck()](oci-date-datetime-and-interval-functions.md)        | Checks the validity of an interval                                             |
| [OCIIntervalCompare()](oci-date-datetime-and-interval-functions.md)      | Compares two intervals                                                         |
| [OCIIntervalDivide()](oci-date-datetime-and-interval-functions.md)       | Divides an interval by an Oracle `NUMBER` to produce an interval               |
| [OCIIntervalFromNumber()](oci-date-datetime-and-interval-functions.md)   | Converts an Oracle `NUMBER` to an interval                                     |
| [OCIIntervalFromText()](oci-date-datetime-and-interval-functions.md)     | When given an interval string, converts the interval represented by the string |
| [OCIIntervalFromTZ()](oci-date-datetime-and-interval-functions.md)       | Returns an interval when given an input string of time zone form               |
| [OCIIntervalGetDaySecond()](oci-date-datetime-and-interval-functions.md) | Gets values of day, hour, minute, and second from an interval                  |
| [OCIIntervalGetYearMonth()](oci-date-datetime-and-interval-functions.md) | Gets year and month from an interval                                           |
| [OCIIntervalMultiply()](oci-date-datetime-and-interval-functions.md)     | Multiplies an interval by an Oracle `NUMBER` to produce an interval            |
| [OCIIntervalSetDaySecond()](oci-date-datetime-and-interval-functions.md) | Sets day, hour, minute, and second in an interval                              |
| [OCIIntervalSetYearMonth()](oci-date-datetime-and-interval-functions.md) | Sets year and month in an interval                                             |
| [OCIIntervalSubtract()](oci-date-datetime-and-interval-functions.md)     | Subtracts two intervals and stores the result in an interval                   |
| [OCIIntervalToNumber()](oci-date-datetime-and-interval-functions.md)     | Converts an interval to an Oracle `NUMBER`                                     |
| [OCIIntervalToText()](oci-date-datetime-and-interval-functions.md)       | When given an interval, produces a string representing the interval            |

**See Also:**

[OCI Date, Datetime, and Interval Functions](oci-date-datetime-and-interval-functions.md) for complete lists of the names and purposes and more detailed information about these functions

### 20.6 Number (OCINumber)

The `OCINumber` data type is an opaque structure used to represent Oracle numeric data types (`NUMBER,` `FLOAT,` `DECIMAL`, and so forth).

You can bind or define this type using the external typecode `SQLT_VNU` in the bind or define call.

Unless otherwise specified, the term number in these functions refers to a value of type `OCINumber`.

This section includes the following topic: OCINumber Examples.

**See Also:**

[Table 28-11](oci-NUMBER-functions.md)for the prototypes and descriptions for all the OCI `NUMBER` functions

#### 20.6.1 OCINumber Examples

Shows how to manipulate an attribute of type `OCINumber`, how to convert values in `OCINumber` format returned from `OCIDescribeAny()` calls to unsigned integers, and how to convert a numeric type returned from an `OCIDescribeAny()` call in `OCINumber` format, such as `OCI_ATTR_MAX` or `OCI_ATTR_MIN`, to an unsigned C integer.

The code fragment in Example 20-3 shows how to manipulate an attribute of type `OCINumber`. The code fragment in Example 20-4 shows how to convert values in `OCINumber` format returned from `OCIDescribeAny()` calls to unsigned integers.

Example 20-4 shows how to convert a numeric type returned from an `OCIDescribeAny()` call in `OCINumber` format, such as `OCI_ATTR_MAX` or `OCI_ATTR_MIN`, to an unsigned C integer.

Example 20-3 Manipulating an Attribute of Type OCINumber

    /* Example 1  */
    struct person
    {
    OCINumber sal;
    };
    typedef struct person person;
    OCIError *err;
    person* steve;
    person* scott;
    person* jason;
    OCINumber  *stevesal;
    OCINumber  *scottsal;
    OCINumber *debsal;
    sword   status;
    int     inum;
    double  dnum;
    OCINumber ornum;
    text   buffer[21];
    ub4     buflen;
    sword   result;

    /* For this example, assume OCIEnv and OCIError are initialized. */
    /* For this example, assume that steve, scott, and jason are pointing to
      person objects that have been pinned in the object cache. */
    stevesal = &steve->sal;
    scottsal = &scott->sal;
    debsal = &jason->sal;

    /* initialize steve's salary to be $12,000 */
    inum = 12000;
    status = OCINumberFromInt(err, &inum, sizeof(inum), OCI_NUMBER_SIGNED,
        stevesal);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberFromInt */;

    /* initialize scott's salary to be the same as steve's */
    OCINumberAssign(err, stevesal, scottsal);

    /* initialize jason's salary to be 20% more than steve's */
    dnum = 1.2;
    status = OCINumberFromReal(err, &dnum, sizeof(dnum), &ornum);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberFromReal */;
    status = OCINumberMul(err, stevesal, &ornum, debsal);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberMul */;

    /* give scott a 50% raise */
    dnum = 1.5;
    status = OCINumberFromReal(err, &dnum, sizeof(dnum), &ornum);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberFromReal */;
    status = OCINumberMul(err, scottsal, &ornum, scottsal);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberMul */;

    /* double steve's salary */
    status = OCINumberAdd(err, stevesal, stevesal, stevesal);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberAdd */;

    /* get steve's salary in integer */
    status = OCINumberToInt(err, stevesal, sizeof(inum), OCI_NUMBER_SIGNED, &inum);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberToInt */;

    /* inum is set to 24000 */
    /* get jason's salary in double */
    status = OCINumberToReal(err, debsal, sizeof(dnum), &dnum);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberToReal */;

    /* dnum is set to 14400 */
    /* print scott's salary as DEM0001'8000.00 */
    buflen = sizeof(buffer);
    status = OCINumberToText(err, scottsal, (text *)"C0999G9999D99", 13,
             (text *)"NLS_NUMERIC_CHARACTERS='.'' NLS_ISO_CURRENCY='Germany'",
             54, &buflen, (text *)buffer);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberToText */;
    printf("scott's salary = %s\n", buffer);

    /* compare steve and scott's salaries */
    status = OCINumberCmp(err, stevesal, scottsal, &result);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberCmp */;

    /* result is positive */
    /* read jason's new salary from string */
    status = OCINumberFromText(err, (text *)"48'000.00", 9, (text
    *)"99G999D99", 9,
        (text *)"NLS_NUMERIC_CHARACTERS='.''", 27, debsal);
    if (status != OCI_SUCCESS)  /* handle error from OCINumberFromText */;
    /* jason's salary is now 48000.00 */

Example 20-4 Converting Values in OCINumber Format Returned from OCIDescribeAny() Calls to Unsigned Integers

    /* Example 2 */
    ub4  max_seq_val  = 0;
    ub1 *max_valp     = NULL;
    ub4  max_val_size;
    OCINumber max_val;
        OCINumberSetZero(_errhp, &max_val);
        OCIParam* parmdp = 0;
        status = OCIAttrGet ((void *)_dschp, (ub4)OCI_HTYPE_DESCRIBE, &parmdp, 0,
                             (ub4)OCI_ATTR_PARAM, _errhp);
    if (isError (status, _errhp))
    {
    return 0;
    }
    status = OCIAttrGet ((void *)parmdp, (ub4)OCI_DTYPE_PARAM, &max_valp,
                         &max_val_size, (ub4)OCI_ATTR_MAX, _errhp);
    //create an OCINumber object from the ORACLE NUMBER FORMAT
    max_val.OCINumberPart[0] = max_val_size; //set the length byte
    memcpy(&max_val.OCINumberPart[1], max_valp, max_val_size); //copy the actual bytes
    //now convert max_val to an unsigned C integer, max_seq_val
    status = OCINumberToInt(_errhp, &max_val, sizeof(max_seq_val),
                            OCI_NUMBER_UNSIGNED, &max_seq_val);

### 20.7 Fixed or Variable-Length String (OCIString)

Fixed or variable-length string data is represented to C programs as an `OCIString *`.

The length of the string does not include the NULL character.

For binding and defining variables of type `OCIString *` use the external typecode `SQLT_VST`.

This section includes the following topics:

- About String Functions

- String Example

**See Also:**

[Table 28-16](oci-string-functions.md) for the prototypes and descriptions for all the string functions

#### 20.7.1 About String Functions

Lists and describes functions that allow the C programmer to manipulate an instance of a string.

Table 20-5 shows the functions that allow the C programmer to manipulate an instance of a string.

Table 20-5 String Functions

| Function                                         | Purpose                                                               |
|:-------------------------------------------------|:----------------------------------------------------------------------|
| [OCIStringAllocSize()](oci-string-functions.md)  | Get allocated size of string memory in code points (Unicode) or bytes |
| [OCIStringAssign()](oci-string-functions.md)     | Assign one string to another string                                   |
| [OCIStringAssignText()](oci-string-functions.md) | Assign the source text string to the target string                    |
| [OCIStringPtr()](oci-string-functions.md)        | Get a pointer to the text of a given string                           |
| [OCIStringResize()](oci-string-functions.md)     | Resize the memory of a given string                                   |
| [OCIStringSize()](oci-string-functions.md)       | Get the size of a given string                                        |

#### 20.7.2 String Example

Assigns a text string to a string, then gets a pointer to the string part of the string, and the string size, and prints it out.

Example 20-5 assigns a text string to a string, then gets a pointer to the string part of the string, and the string size, and prints it out.

Note the double indirection used in passing the `vstring1` parameter in `OCIStringAssignText()`.

Example 20-5 Manipulating an Attribute of Type OCIString

    OCIEnv       *envhp;
    OCIError     *errhp;
    OCIString     *vstring1 = (OCIString *)0;
    OCIString     *vstring2 = (OCIString *)0;
    text          c_string[20];
    text         *text_ptr;
    sword        status;

    strcpy((char *)c_string, "hello world");
    /* Assign a text string to an OCIString */
    status = OCIStringAssignText(envhp, errhp, c_string,
          (ub4)strlen((char *)c_string),&vstring1);
    /* Memory for vstring1 is allocated as part of string assignment */

    status = OCIStringAssignText(envhp, errhp, (text *)"hello again",
           (ub4)strlen("This is a longer string."),&vstring1);
    /* vstring1 is automatically resized to store the longer string */

    /* Get a pointer to the string part of vstring1 */
    text_ptr = OCIStringPtr(envhp, vstring1);
    /* text_ptr now points to "hello world" */
    printf("%s\n", text_ptr);

**See Also:**

[OCIStringAssignText()](oci-string-functions.md)

### 20.8 Raw (OCIRaw)

Variable-length raw data is represented in C using the `OCIRaw * `data type.

For binding and defining variables of type `OCIRaw *`, use the external typecode `SQLT_LVB`.

This section includes the following topics:

- About Raw Functions

- Raw Example

**See Also:**

[Table 28-14](oci-raw-functions.md) for the prototypes and descriptions for all the raw functions

#### 20.8.1 About Raw Functions

Lists and describes the Raw functions.

Table 20-6 shows the functions that perform OCIRaw operations.

Table 20-6 Raw Functions

| Function                                    | Purpose                                       |
|:--------------------------------------------|:----------------------------------------------|
| [OCIRawAllocSize()](oci-raw-functions.md)   | Get the allocated size of raw memory in bytes |
| [OCIRawAssignBytes()](oci-raw-functions.md) | Assign raw data (ub1 \*) to OCIRaw \*         |
| [OCIRawAssignRaw()](oci-raw-functions.md)   | Assign one OCIRaw \* to another               |
| [OCIRawPtr()](oci-raw-functions.md)         | Get pointer to raw data                       |
| [OCIRawResize()](oci-raw-functions.md)      | Resize memory of variable-length raw data     |
| [OCIRawSize()](oci-raw-functions.md)        | Get size of raw data                          |

#### 20.8.2 Raw Example

Shows how to set up a raw data block and obtain a pointer to its data.

Example 20-6 shows how to set up a raw data block and obtain a pointer to its data.

Note the double indirection in the call to `OCIRawAssignBytes()`.

Example 20-6 Manipulating an Attribute of Type OCIRaw

    OCIEnv      *envhp;
    OCIError    *errhp;
    sword       status;
    ub1         data_block[10000];
    ub4         data_block_len = 10000;
    OCIRaw      *raw1 = (OCIRaw *) 0;
    ub1 *raw1_pointer;

    /* Set up the RAW */
    /* assume 'data_block' has been initialized */
    status = OCIRawAssignBytes(envhp, errhp, data_block, data_block_len,
    &raw1);

    /* Get a pointer to the data part of the RAW */
    raw1_pointer = OCIRawPtr(envhp, raw1);

**See Also:**

[OCIRawAssignBytes()](oci-raw-functions.md)

### 20.9 Collections (OCITable, OCIArray, OCIColl, OCIIter)

Oracle Database provides two types of collections: variable-length arrays (`varray`s) and nested tables. In C applications, varrays are represented as `OCIArray *`, and nested tables are represented as `OCITable *`.

Both of these data types (along with `OCIColl` and `OCIIter`, described later) are opaque structures.

A variety of generic collection functions enable you to manipulate collection data. You can use these functions on both varrays and nested tables. In addition, there is a set of functions specific to nested tables.

This section includes the following topics:

- Generic Collection Functions

- About Collection Data Manipulation Functions

- About Collection Scanning Functions

- Varray/Collection Iterator Example

- About Nested Table Manipulation Functions

- About Nested Table Manipulation Functions

You can allocate an instance of a varray or nested table using `OCIObjectNew()` and free it using `OCIObjectFree()`.

**See Also:**

- About Nested Table Manipulation Functions

- [OCIObjectNew()](oci-miscellaneous-object-functions.md)

- [OCIObjectFree()](oci-pin-unpin-and-free-functions.md)

- [OCI Collection and Iterator Functions](oci-collection-and-iterator-functions.md) for the prototypes and descriptions for these functions

#### 20.9.1 Generic Collection Functions

Oracle Database provides two types of collections: variable-length arrays (varrays) and nested tables.

Both varrays and nested tables can be viewed as subtypes of a generic collection type.

In C, a generic collection is represented as `OCIColl *`, a varray is represented as `OCIArray *`, and a nested table is represented as `OCITable *`. Oracle provides a set of functions to operate on generic collections (such as `OCIColl *`). These functions start with the prefix `OCIColl`, as in `OCICollGetElem()`. The `OCIColl*()` functions can also be called to operate on varrays and nested tables.

The generic collection functions are grouped into two main categories:

- Manipulating varray or nested table data

- Scanning through a collection with a collection iterator

The generic collection functions represent a complete set of functions for manipulating varrays. Additional functions are provided to operate specifically on nested tables. They are identified by the prefix `OCITable`, as in `OCITableExists().`

**Note:**

Indexes passed to collection functions are zero-based.

**See Also:**

- [OCITableExists()](oci-table-functions.md)

- About Nested Table Manipulation Functions

#### 20.9.2 About Collection Data Manipulation Functions

Lists and describes the collection data manipulation functions.

Table 20-7 shows the generic functions that manipulate collection data.

Table 20-7 Collection Functions

| Function                                                          | Purpose                                               |
|:------------------------------------------------------------------|:------------------------------------------------------|
| [OCICollAppend()](oci-collection-and-iterator-functions.md)       | Append an element to the end of a collection          |
| [OCICollAssign()](oci-collection-and-iterator-functions.md)       | Assign one collection to another                      |
| [OCICollAssignElem()](oci-collection-and-iterator-functions.md)   | Assign element at given index                         |
| [OCICollGetElem()](oci-collection-and-iterator-functions.md)      | Get pointer to an element when given its index        |
| [OCICollGetElemArray()](oci-collection-and-iterator-functions.md) | Get array of elements from a collection               |
| [OCICollIsLocator()](oci-collection-and-iterator-functions.md)    | Indicate whether a collection is locator-based or not |
| [OCICollMax()](oci-collection-and-iterator-functions.md)          | Get upper bound of collection                         |
| [OCICollSize()](oci-collection-and-iterator-functions.md)         | Get current size of collection                        |
| [OCICollTrim()](oci-collection-and-iterator-functions.md)         | Trim n elements from the end of the collection        |

#### 20.9.3 About Collection Scanning Functions

Lists and describes the collection scanning functions.

Table 20-8 shows the generic functions that enable you to scan collections with a collection iterator. The iterator is of type `OCIIter`, and is created by first calling `OCIIterCreate()`.

Table 20-8 Collection Scanning Functions

| Function                                                        | Purpose                                                         |
|:----------------------------------------------------------------|:----------------------------------------------------------------|
| [OCIIterCreate()](oci-collection-and-iterator-functions.md)     | Create an iterator to scan the elements of a collection         |
| [OCIIterDelete()](oci-collection-and-iterator-functions.md)     | Delete a collection iterator                                    |
| [OCIIterGetCurrent()](oci-collection-and-iterator-functions.md) | Get a pointer to the current element pointed to by the iterator |
| [OCIIterInit()](oci-collection-and-iterator-functions.md)       | Initialize an iterator to scan the given collection             |
| [OCIIterNext()](oci-collection-and-iterator-functions.md)       | Get a pointer to the next iterator collection element           |
| [OCIIterPrev()](oci-collection-and-iterator-functions.md)       | Get pointer to the previous iterator collection element         |

#### 20.9.4 Varray/Collection Iterator Example

Shows how to create and use a collection iterator to scan through a varray.

Example 20-7 creates and uses a collection iterator to scan through a varray.

Example 20-7 Using Collection Data Manipulation Functions

    OCIEnv       *envhp;
    OCIError     *errhp;
    text         *text_ptr;
    sword        status;
    OCIArray     *clients;
    OCIString    *client_elem;
    OCIIter      *iterator;
    boolean      eoc;
    void         *elem;
    OCIInd       *elemind;

    /* Assume envhp, errhp have been initialized */
    /* Assume clients points to a varray */

    /* Print the elements of clients */
    /* To do this, create an iterator to scan the varray */
    status = OCIIterCreate(envhp, errhp, clients, &iterator);

    /* Get the first element of the clients varray */
    printf("Clients' list:\n");
    status = OCIIterNext(envhp, errhp, iterator, &elem,
                        (void  **) &elemind, &eoc);

    while (!eoc && (status == OCI_SUCCESS))
    {
      client_elem = *((OCIString **)elem);
                                 /* client_elem points to the string */

     /*
        the element pointer type returned by OCIIterNext() through 'elem' is

        the same as that of OCICollGetElem(). See OCICollGetElem() for
        details.  */

      /*
        client_elem points to an OCIString descriptor, so to print it out,
        get a pointer to where the text begins
      */
      text_ptr = OCIStringPtr(envhp, client_elem);

      /*
        text_ptr now points to the text part of the client OCIString, which
    is a
    NULL-terminated string
      */
      printf("  %s\n", text_ptr);
      status = OCIIterNext(envhp, errhp, iterator, &elem,
                          (void  **)&elemind, &eoc);
    }

    if (status != OCI_SUCCESS)
    {
      /* handle error */
    }

    /* destroy the iterator */
    status = OCIIterDelete(envhp, errhp, &iterator);

#### 20.9.5 About Nested Table Manipulation Functions

As its name implies, one table may be nested, or contained within another, as a variable, attribute, parameter, or column.

Nested tables may have elements deleted by the `OCITableDelete()` function.

For example, suppose a table is created with 10 elements, and `OCITableDelete()` is used to delete elements at index 0 through 4 and 9. The first existing element is now element 5, and the last existing element is element 8.

As noted previously, the generic collection functions may be used to map to and manipulate nested tables. In addition, Table 20-9 shows the functions that are specific to nested tables. They should not be used on varrays.

Table 20-9 Nested Table Functions

| Function                                   | Purpose                                                       |
|:-------------------------------------------|:--------------------------------------------------------------|
| [OCITableDelete()](oci-table-functions.md) | Delete an element at a given index                            |
| [OCITableExists()](oci-table-functions.md) | Test whether an element exists at a given index               |
| [OCITableFirst()](oci-table-functions.md)  | Return the index for the first existing element of a table    |
| [OCITableLast()](oci-table-functions.md)   | Return the index for the last existing element of a table     |
| [OCITableNext()](oci-table-functions.md)   | Return the index for the next existing element of a table     |
| [OCITablePrev()](oci-table-functions.md)   | Return the index for the previous existing element of a table |
| [OCITableSize()](oci-table-functions.md)   | Return the table size, not including any deleted elements     |

This section includes the following topic: Nested Table Element Ordering.

##### 20.9.5.1 Nested Table Element Ordering

When a nested table is fetched into the object cache, its elements are given a transient ordering, numbered from zero to the number of elements, minus 1.

For example, a table with 40 elements would be numbered from 0 to 39.

You can use these position ordinals to fetch and assign the values of elements (for example, fetch to element i, or assign to element j, where i and j are valid position ordinals for the given table).

When the table is copied back to the database, its transient ordering is lost. Delete operations may be performed against elements of the table. Delete operations create transient holes; that is, they do not change the position ordinals of the remaining table elements.

#### 20.9.6 Nested Table Locators

You can retrieve a locator to a nested table. A locator is like a handle to a collection value, and it contains information about the database snapshot that exists at the time of retrieval.

This snapshot information helps the database retrieve the correct instantiation of a collection value at a later time when collection elements are fetched using the locator.

Unlike a LOB locator, a collection locator cannot be used to modify a collection instance; it only locates the correct data. Using the locator enables an application to return a handle to a nested table without having to retrieve the entire collection, which may be quite large.

A user specifies when a table is created if a locator should be returned when a collection column or attribute is fetched, using the `RETURN` `AS` `LOCATOR` specification.

You can use the `OCICollIsLocator()` function to determine whether a collection is locator-based or not.

**See Also:**

- [OCICollIsLocator()](oci-collection-and-iterator-functions.md)

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md)

### 20.10 About Multilevel Collection Types

The collection element itself can be directly or indirectly another collection type.

Multilevel collection type is the name given to such a top-level collection type.

Multilevel collections have the following characteristics:

- They can be collections of other collection types.

- They can be collections of objects with collection attributes.

- They have no limit to the number of nesting levels.

- They can contain any combination of varrays and nested tables.

- They can be used as columns in tables.

OCI routines work with multilevel collections. The following routines can return in parameter `*elem` an `OCIColl*`, which you can use in any of the collection routines:

- `OCICollGetElem()`

- `OCIIterGetCurrent()`

- `OCIIterNext()`

- `OCIIterPrev()`

The following functions take a collection element and add it to an existing collection. Parameter `elem` could be an `OCIColl*` if the element type is another collection:

- `OCICollAssignElem()`

- `OCICollAppend()`

This section includes the following topic: Multilevel Collection Type Example.

**See Also:**

- [OCICollGetElem()](oci-collection-and-iterator-functions.md)

- [OCIIterGetCurrent()](oci-collection-and-iterator-functions.md)

- [OCIIterNext()](oci-collection-and-iterator-functions.md)

- [OCIIterPrev()](oci-collection-and-iterator-functions.md)

- [OCICollAssignElem()](oci-collection-and-iterator-functions.md)

- [OCICollAppend()](oci-collection-and-iterator-functions.md)

#### 20.10.1 Multilevel Collection Type Example

Shows how to iterate over the multilevel collection.

The following types and tables are used for Example 20-8.

    type_1 (a NUMBER, b NUMBER)
    NT1 TABLE OF type_1
    NT2 TABLE OF NT1

The code fragment in Example 20-8 iterates over the multilevel collection.

Example 20-8 Using Multilevel Collection Data Manipulation Functions

    ...
    OCIColl *outer_coll;
    OCIColl *inner_coll;
    OCIIter *itr1, *itr2;
    Type_1 *type_1_instance;
    ..
    /* assume that outer_coll points to a valid coll of type NT2 */
    checkerr(errhp, OCIIterCreate(envhp, errhp, outer_coll, &itr1));
    for(eoc = FALSE;!OCIIterNext(envhp, errhp, itr1, (void  **) &elem,
                                   (void  **) &elem_null, &eoc) && !eoc;)
    {
       inner_coll = (OCIColl *)elem;
       /* iterate over inner collection.. */
       checkerr(errhp, OCIIterCreate(envhp, errhp, inner_coll, &itr2));
       for(eoc2 = FALSE;!OCIIterNext(envhp, errhp, itr2, (void  **)&elem2,
                  (void  **) &elem2_null, &eoc2) && !eoc2;)
           {
            type_1_instance = (Type_1 *)elem2;
            /* use the fields of type_1_instance */
           }
       /* close iterator over inner collection */
       checkerr(errhp, OCIIterDelete(envhp, errhp, &itr2));
    }
    /* close iterator over outer collection */
    checkerr(errhp, OCIIterDelete(envhp, errhp, &itr1));
    ...

### 20.11 REF (OCIRef)

A `REF` (reference) is an identifier to an object.

It is an opaque structure that uniquely locates the object. An object may point to another object by way of a `REF`.

In C applications, the `REF` is represented by `OCIRef*`.

This section includes the following topic:

- About REF Manipulation Functions

- REF Example

**See Also:**

[Table 28-15](oci-REF-functions.md) for the prototypes and descriptions for all the `REF` manipulation functions

#### 20.11.1 About REF Manipulation Functions

Lists and describes `REF` manipulation functions.

Table 20-10 shows the functions that perform `REF` operations.

Table 20-10 REF Manipulation Functions

| Function                                | Purpose                                                         |
|:----------------------------------------|:----------------------------------------------------------------|
| [OCIRefAssign()](oci-REF-functions.md)  | Assign one `REF` to another                                     |
| [OCIRefClear()](oci-REF-functions.md)   | Clear or nullify a `REF`                                        |
| [OCIRefFromHex()](oci-REF-functions.md) | Convert a hexadecimal string to a `REF`                         |
| [OCIRefHexSize()](oci-REF-functions.md) | Return the size of a hexadecimal string representation of `REF` |
| [OCIRefIsEqual()](oci-REF-functions.md) | Compare two `REF`s for equality                                 |
| [OCIRefIsNull()](oci-REF-functions.md)  | Test whether a `REF` is `NULL`                                  |
| [OCIRefToHex()](oci-REF-functions.md)   | Convert a `REF` to a hexadecimal string                         |

#### 20.11.2 REF Example

Shows how to test two `REF`s for `NULL`, compares them for equality, and assigns one `REF` to another.

Example 20-9 tests two `REF`s for `NULL`, compares them for equality, and assigns one `REF` to another. Note the double indirection in the call to `OCIRefAssign()`.

Example 20-9 Using REF Manipulation Functions

    OCIEnv       *envhp;
    OCIError     *errhp;
    sword        status;
    boolean      refs_equal;
    OCIRef       *ref1, *ref2;

    /* assume REFs have been initialized to point to valid objects */
    /*Compare two REFs for equality */
    refs_equal = OCIRefIsEqual(envhp, ref1, ref2);
    printf("After first OCIRefIsEqual:\n");
    if(refs_equal)
       printf("REFs equal\n");
    else
       printf("REFs not equal\n");

    /*Assign ref1 to ref2 */
    status = OCIRefAssign (envhp, errhp, ref1, &ref2);
    if(status != OCI_SUCCESS)
    /*error handling*/

    /*Compare the two REFs again for equality */
    refs_equal = OCIRefIsEqual(envhp, ref1, ref2);
    printf("After second OCIRefIsEqual:\n");
    if(refs_equal)
       printf("REFs equal\n");
    else
       printf("REFs not equal\n");

**See Also:**

[OCIRefAssign()](oci-REF-functions.md)

### 20.12 Object Type Information Storage and Access

The OCI data types and type descriptors are discussed in this section.

This section includes the following topic: Descriptor Objects.

#### 20.12.1 Descriptor Objects

Lists and describes the descriptor objects.

When a given type is created with the `CREATE TYPE` statement, it is stored in the server and associated with a type descriptor object (TDO). In addition, the database stores descriptor objects for each data attribute of the type, each method of the type, each parameter of each method, and the results returned by methods. Table 20-11 lists the OCI data types associated with each type of descriptor object.

Table 20-11 Descriptor Objects

| Information Type                                                     | OCI Data Type |
|:---------------------------------------------------------------------|:--------------|
| Type                                                                 | OCIType       |
| Type Attributes Collection Elements Method Parameters Method Results | OCITypeElem   |
| Method                                                               | OCITypeMethod |

Several OCI functions (including `OCIBindObject()` and `OCIObjectNew()`) require a TDO as an input parameter. An application can obtain the TDO by calling `OCITypeByName()`, which gets the type's TDO in an `OCIType` variable. Once you obtain the TDO, you can pass it, as necessary, to other calls.

**See Also:**

- [OCIBindObject()](bind-define-describe-functions.md)

- [OCIObjectNew()](oci-miscellaneous-object-functions.md)

- [OCITypeByName()](oci-type-information-accessor-functions.md)

### 20.13 AnyType, AnyData, and AnyDataSet Interfaces

The AnyType, AnyData, and AnyDataSet interfaces allow you to model self-descriptive data.

You can store heterogeneous data types in the same column and query the type of data in an application.

These definitions are used in the discussion in the following sections:

- Persistent types. Types that are created using the SQL statement `CREATE TYPE`. They are stored persistently in the database.

- Transient types. Anonymous type descriptions that are not stored persistently in the database. They are created by programs as needed. They are useful for exchanging type information, if necessary, between various components of an application in a dynamic fashion.

- Self-descriptive data. Data encapsulating type information with its actual contents. The `OCIAnyData` data type models such data in OCI. A data value of most SQL types can be converted to an OCIAnyData that can then be converted back to the old data value. The type `SYS.ANYDATA` models such data in SQL or PL/SQL.

- Self-descriptive dataset. Encapsulation of a set of data instances (all of the same type) along with their type description. They should all have the same type description. The `OCIDataAnySet` data type models this data in OCI. The type `SYS.ANYDATASET` models such data in SQL or PL/SQL.

Interfaces are available in both OCI (C language) and in SQL and PL/SQL for constructing and manipulating these type descriptions and self-descriptive data. The following sections describe the relevant OCI interfaces.

This section includes the following topics:

- About Type Interfaces

- About OCIAnyData Interfaces

- NCHAR Typecodes for OCIAnyData Functions

- About OCIAnyDataSet Interfaces

**See Also:**

- [Persistent Objects, Transient Objects, and Values](oci-object-relational-programming.md)

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for an overview in the section about Oracle-supplied types

#### 20.13.1 About Type Interfaces

You can use the type interfaces to construct named and anonymous transient object types (structured with attributes) and collection types.

Use the `OCITypeBeginCreate()` call to begin type construction of transient object types and collection types (the typecode parameter determines which one is being constructed).

You must allocate a parameter handle using `OCIDescriptorAlloc()`. Subsequently, you set type information (for attributes of an object type and for the collection element's type) by using `OCIAttrSet()`. For object types, as shown in Example 20-10, use `OCITypeAddAttr()` to add the attribute information to the type. After adding information for the last attribute, you must call `OCITypeEndCreate()`.

For collection types, as shown in Example 20-11, use `OCITypeSetCollection()` to set the information on the collection element type. Subsequently, call `OCITypeEndCreate()` to finish construction.

You can use the `OCIDescribeAny()` call to obtain the `OCIType `corresponding to a persistent type.

Example 20-10 Using Type Interfaces to Construct Object Types

    OCITypeBeginCreate( ...)        /* Begin Type Creation */
    OCIDescriptorAlloc(...)
    OCIAttrSet(...)
    OCITypeAddAttr(...)             /* Add attribute 1 */
    OCIAttrSet(...)
    OCITypeAddAttr(...)             /* Add attribute 2 */
    ...
    OCITypeEndCreate(...)           /* End Type Creation */

Example 20-11 Using Type Interfaces to Construct Collection Types

    OCITypeBeginCreate( ...)        /* Begin Type Creation */
    OCIDescriptorAlloc(...)
    OCIAttrSet(...)
    OCITypeSetCollection(...)       /* Set information on collection element */
    OCITypeEndCreate(...)           /* End Type Creation */

This section includes the following topics:

- About Creating a Parameter Descriptor for OCIType Calls

- About Obtaining the OCIType for Persistent Types

- Type Access Calls

- Extensions to OCIDescribeAny()

**See Also:**

- [OCITypeBeginCreate()](oci-type-interface-functions.md)

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)

- [OCIAttrSet()](handle-and-descriptor-functions.md)

- [OCITypeAddAttr()](oci-type-interface-functions.md)

- [OCITypeEndCreate()](oci-type-interface-functions.md)

- [OCITypeSetCollection()](oci-type-interface-functions.md)

- [OCITypeEndCreate()](oci-type-interface-functions.md)

##### 20.13.1.1 About Creating a Parameter Descriptor for OCIType Calls

You can use the `OCIDescriptorAlloc()` call to allocate an `OCIParam` (with the parent handle being the environment handle).

Subsequently, you can call `OCIAttrSet()` with the following allowed attribute types to set relevant type information:

- `OCI_ATTR_PRECISION`

To set numeric precision. Pass a `(ub1 *)` attribute value to the buffer holding the precision value.

- `OCI_ATTR_SCALE`

To set numeric scale. Pass a `(sb1 *)` attribute value to the buffer that is holding the scale value.

- `OCI_ATTR_CHARSET_ID`

To set the character set ID for character types. Pass a `(ub2 *)` attribute value to the buffer holding the char set ID.

- `OCI_ATTR_CHARSET_FORM`

To set the character set form for character types. Pass a `(ub1 *)` attribute value to the buffer holding the character set form value.

- `OCI_ATTR_DATA_SIZE`

Length of `VARCHAR2`, `RAW`, and so on. Pass a `(ub2 *)` attribute value to the buffer holding the length.

- `OCI_ATTR_TYPECODE`

To set typecode. Pass a `(ub2 *)` attribute value to the buffer holding the typecode. This attribute must be set first.

- `OCI_ATTR_TDO`

To set `OCIType `of an object or collection attribute. Pass an `(OCIType *)` attribute value to the `OCIType` corresponding to the attribute. Ensure that the `OCIType` is pinned when this `OCIParam` is used during `AnyType` construction. If it is a transient type attribute, its allocation duration should be at least as much as the top-level `OCIType` being created. Otherwise, an exception is returned.

- For built-in types, the following typecodes are acceptable (permissible values for `OCI_ATTR_TYPECODE`) for SQL type attributes:

  `OCI_TYPECODE_DATE`, `OCI_TYPECODE_NUMBER`,

  `OCI_TYPECODE_VARCHAR`, `OCI_TYPECODE_RAW`,

  `OCI_TYPECODE_CHAR`, `OCI_TYPECODE_VARCHAR2`,

  `OCI_TYPECODE_VARCHAR`, `OCI_TYPECODE_BLOB`,

  `OCI_TYPECODE_BFILE`, `OCI_TYPECODE_CLOB`,

  `OCI_TYPECODE_TIMESTAMP`, `OCI_TYPECODE_TIMESTAMP_TZ`,

  `OCI_TYPECODE_TIMESTAMP_LTZ`,

  `OCI_TYPECODE_INTERVAL_YM`, and `OCI_TYPECODE_INTERVAL_DS`.

- If the attribute or collection element type is itself another transient type, set `OCI_ATTR_TYPECODE` to `OCI_TYPECODE_OBJECT` or `OCI_TYPECODE_REF` (for `REF`s) or `OCI_TYPECODE_VARRAY` or `OCI_TYPECODE_TABLE` and set the `OCI_ATTR_TDO` to the `OCIType` corresponding to the transient type.

- For user-defined type attributes, the permissible values for `OCI_ATTR_TYPECODE` are:

  - `OCI_TYPECODE_OBJECT` (for an Object Type)

  - `OCI_TYPECODE_REF` (for a `REF` type)

  - and `OCI_TYPECODE_VARRAY` or `OCI_TYPECODE_TABLE` (for collections)

  The `OCI_ATTR_TDO` should be set in these cases to the appropriate user-defined type's `OCIType`.

**See Also:**

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)

- [OCIAttrSet()](handle-and-descriptor-functions.md)

##### 20.13.1.2 About Obtaining the OCIType for Persistent Types

You can use the `OCIDescribeAny()` call to obtain the `OCIType` corresponding to a persistent type.

This is shown in the following example:

    OCIDescribeAny(svchp, errhp. (void  *)"HR.EMPLOYEES",
                   (ub4)strlen("HR.EMPLOYEES"),
                   (ub1)OCI_OTYPE_NAME, (ub1)OCI_DEFAULT, OCI_PTYPE_TYPE, dschp);

From the describe handle (`dschp`), you can use `OCIAttrGet()` calls to obtain the `OCIType`.

**See Also:**

- [OCIDescribeAny()](bind-define-describe-functions.md)

- [OCIAttrGet()](handle-and-descriptor-functions.md)

##### 20.13.1.3 Type Access Calls

`OCIDescribeAny()` can be called with these transient type descriptions for a dynamic description of the type.

The `OCIType` pointer can be passed directly to `OCIDescribeAny()` (with `objtype` set to `OCI_OTYPE_PTR`). This provides a way to obtain attribute information by name and position.

**See Also:**

[OCIDescribeAny()](bind-define-describe-functions.md)

##### 20.13.1.4 Extensions to OCIDescribeAny()

For transient types that represent built-in types (created with a built-in typecode), the parameter handle that describes these types (which are of type `OCI_PTYPE_TYPE`) .

The parameter handle that describes these transient types supports the following extra attributes:

- `OCI_ATTR_DATA_SIZE`

- `OCI_ATTR_TYPECODE`

- `OCI_ATTR_DATA_TYPE`

- `OCI_ATTR_PRECISION`

- `OCI_ATTR_SCALE`

- `OCI_ATTR_CHARSET_ID`

- `OCI_ATTR_CHARSET_FORM`

- `OCI_ATTR_LFPRECISION`

- `OCI_ATTR_FSPRECISION`

These attributes have the usual meanings they have while describing a type attribute.

**Note:**

These attributes are supported only for transient built-in types. The attributes `OCI_ATTR_IS_TRANSIENT_TYPE` and `OCI_ATTR_IS_PREDEFINED_TYPE` are true for these types. For persistent types, these attributes are supported only from the parameter handle of the type's attributes (which are of type `OCI_PTYPE_TYPE_ATTR`).

#### 20.13.2 About OCIAnyData Interfaces

An `OCIAnyData` encapsulates type information and a data instance of that type (that is, self-descriptive data).

An `OCIAnyData` can be created from any built-in or user-defined type instance by using the `OCIAnyDataConvert()` call. This call does a conversion (cast) to an `OCIAnyData`.

Alternatively, object types and collection types can be constructed piece by piece (an attribute at a time for object types or a collection element at a time) by calling `OCIAnyDataBeginCreate()` with the type information (`OCIType`). Subsequently, you can use `OCIAnyDataAttrSet()` for object types and use `OCIAnyDataCollAddElem()` for collection types. Finally, use the `OCIAnyDataEndCreate()` call to finish the construction process.

Subsequently, you can invoke the access routines. To convert (cast) an `OCIAnyData` to the corresponding type instance, you can use `OCIAnyDataAccess()`.

An `OCIAnyData` that is based on an object or collection type can also be accessed piece by piece.

Special collection construction and access calls are provided for performance improvement. You can use these calls to avoid unnecessary creation and copying of the entire collection in memory, as shown in Example 20-12.

or

    OCIAnyDataCollAddElem(...)    /* Element-wise construction for collections */

    OCIAnyDataEndCreate(...)      /* End OCIAnyData Creation */

Example 20-12 Using Special Construction and Access Calls for Improved Performance

    OCIAnyDataConvert(...)        /* Cast a built-in or user-defined type instance
                                     to an OCIAnyData in 1 call. */

    OCIAnyDataBeginCreate(...)    /* Begin AnyData Creation */

    OCIAnyDataAttrSet(...)        /* Attribute-wise construction for object types */

#####

**See Also:**

- [OCIAnyDataConvert()](oci-any-data-interface-functions.md)

- [OCIAnyDataBeginCreate()](oci-any-data-interface-functions.md)

- [OCIAnyDataAttrSet()](oci-any-data-interface-functions.md)

- [OCIAnyDataCollAddElem()](oci-any-data-interface-functions.md)

- [OCIAnyDataEndCreate()](oci-any-data-interface-functions.md)

- [OCIAnyDataAccess()](oci-any-data-interface-functions.md)

#### 20.13.3 NCHAR Typecodes for OCIAnyData Functions

The function `OCIAnyDataTypeCodeToSqlt()` converts the `OCITypeCode` for an OCIAnyData value to the SQLT code that corresponds to the representation of the value as returned by the OCIAnyData API.

The following typecodes are used in the OCIAnyData functions only:

- `OCI_TYPECODE_NCHAR`

- `OCI_TYPECODE_NVARCHAR2`

- `OCI_TYPECODE_NCLOB`

In calls to other functions, such as `OCIDescribeAny()`, these typecodes are not returned, and you must use the character set form to determine if the data is `NCHAR` (if character set form is SQLCS_NCHAR).

`OCIAnyDataTypeCodeToSqlt()` converts `OCI_TYPECODE_CHAR` and `OCI_TYPECODE_VARCHAR2` to the output values `SQLT_VST` (which corresponds to the `OCIString` mapping) with a character set form of `SQLCS_IMPLICIT`. `OCI_TYPECODE_NVARCHAR2` also returns `SQLT_VST` (`OCIString` mapping is used by OCIAnyData API) with a character set form of `SQLCS_NCHAR`.

**See Also:**

- [OCIDescribeAny()](bind-define-describe-functions.md)

- [OCIAnyDataTypeCodeToSqlt()](oci-any-data-interface-functions.md)

#### 20.13.4 About OCIAnyDataSet Interfaces

An `OCIAnyDataSet` encapsulates type information and a set of instances of that type. To begin the construction process, call `OCIAnyDataSetBeginCreate()`.

Call `OCIAnyDataSetAddInstance()` to add a new instance; this call returns the `OCIAnyData` corresponding to that instance.

Then, you can invoke the OCIAnyData functions to construct this instance. Call `OCIAnyDataSetEndCreate()` when all instances have been added.

For access, call `OCIAnyDataSetGetInstance()` to get the `OCIAnyData` corresponding to the instance. Only sequential access is supported. Subsequently, you can invoke the OCIAnyData access functions, as in the following example:

    OCIAnyDataSetBeginCreate(...)   /* Begin AnyDataSet Creation */
    OCIAnyDataSetAddInstance(...)   /* Add a new instance to the AnyDataSet */
                                    /* Use the OCIAnyData*() functions to create
                                       the instance */
    OCIAnyDataSetEndCreate(...)     /* End OCIAnyDataSet Creation */

**See Also:**

- [OCIAnyDataSetBeginCreate()](oci-any-data-set-interface-functions.md)

- [OCIAnyDataSetAddInstance()](oci-any-data-set-interface-functions.md)

- [OCIAnyDataSetEndCreate()](oci-any-data-set-interface-functions.md)

- [OCIAnyDataSetGetInstance()](oci-any-data-set-interface-functions.md)

- [OCI Any Type and Data Functions](oci-any-type-and-data-functions.md) for complete descriptions of all the calls in these interfaces

### 20.14 About Binding Named Data Types

This section provides information about binding named data types (such as objects and collections) and `REF`s.

This section includes the following topics:

- Named Data Type Binds

- About Binding REFs

- Information for Named Data Type and REF Binds

- Information Regarding Array Binds

#### 20.14.1 Named Data Type Binds

For a named data type (object type or collection) bind, a second bind call is necessary following `OCIBindByName()` or `OCIBindByName2()` or `OCIBindByPos()` or `OCIBindByPos2()`.

The `OCIBindObject()` call sets up additional attributes specific to the object type bind. An OCI application uses this call when fetching data from a table that has a column with an object data type.

The `OCIBindObject()` call takes, among other parameters, a type descriptor object (TDO) for the named data type. The TDO of data type `OCIType` is created and stored in the database when a named data type is created. It contains information about the type and its attributes. An application can obtain a TDO by calling `OCITypeByName()`.

The `OCIBindObject()` call also sets up the indicator variable or structure for the named data type bind.

When binding a named data type, use the `SQLT_NTY` data type constant to indicate the data type of the program variable being bound. `SQLT_NTY` indicates that a C struct representing the named data type is being bound. A pointer to this structure is passed to the bind call.

With inheritance and instance substitutability, you can bind a subtype instance where the supertype is expected.

Working with named data types may require the use of three bind calls in some circumstances. For example, to bind a static array of named data types to a PL/SQL table, three calls must be invoked: `OCIBindByName()` or `OCIBindByName2()`, `OCIBindArrayOfStruct()`, and `OCIBindObject()`.

**See Also:**

- [Fetching Embedded Objects](oci-object-relational-programming.md) for information about using these data types to fetch an embedded object from the database

- Information for Named Data Type and REF Binds

- Descriptor Objects

- [OCIBindByName()](bind-define-describe-functions.md) or [OCIBindByName2()](bind-define-describe-functions.md)

- [OCIBindByPos()](bind-define-describe-functions.md) or [OCIBindByPos2()](bind-define-describe-functions.md)

- [OCIBindObject()](bind-define-describe-functions.md)

- [OCITypeByName()](oci-type-information-accessor-functions.md)

- [OCIBindArrayOfStruct()](bind-define-describe-functions.md)

#### 20.14.2  About Binding REFs

As with named data types, binding `REF`s is a two-step process.

First, call `OCIBindByName()` or `OCIBindByName2()` or `OCIBindByPos()` or `OCIBindByPos2()`, and then call `OCIBindObject()`.

`REF`s are bound using the `SQLT_REF` data type. When `SQLT_REF` is used, then the program variable being bound must be of type `OCIRef *`.

With inheritance and `REF` substitutability, you can bind a `REF` value to a subtype instance where a `REF` to the supertype is expected.

**See Also:**

- [Retrieving an Object Reference from the Server](oci-object-relational-programming.md) for information about binding and pinning `REF`s to objects

- Information for Named Data Type and REF Binds for additional important information

- [OCIBindByName()](bind-define-describe-functions.md) or [OCIBindByName2()](bind-define-describe-functions.md)

- [OCIBindByPos()](bind-define-describe-functions.md) or [OCIBindByPos2()](bind-define-describe-functions.md)

- [OCIBindObject()](bind-define-describe-functions.md)

#### 20.14.3 Information for Named Data Type and REF Binds

Remember the following important information when you work with named data type and `REF` binds.

It includes pointers about memory allocation and indicator variable usage.

- If the data type being bound is `SQLT_NTY`, the indicator struct parameter of the `OCIBindObject()` call (`void ** indpp`) is used, and the scalar indicator is completely ignored.

- If the data type is `SQLT_REF`, the scalar indicator is used, and the indicator struct parameter of `OCIBindObject()` is completely ignored.

- The use of indicator structures is optional. The user can pass a `NULL` pointer in the `indpp` parameter for the `OCIBindObject()` call. During the bind, therefore, the object is not atomically `NULL` and none of its attributes are `NULL`.

- The indicator struct size pointer, `indsp`, and program variable size pointer, `pgvsp`, in the `OCIBindObject()` call are optional. Users can pass `NULL` if these parameters are not needed.

**See Also:**

[OCIBindObject()](bind-define-describe-functions.md)

#### 20.14.4 Information Regarding Array Binds

For doing array binds of named data types or `REF`s, for array inserts or fetches, the user must pass in an array of pointers to buffers (preallocated or otherwise) of the appropriate type.

Similarly, an array of scalar indicators for `SQLT_REF` types or an array of pointers to indicator structs for `SQLT_NTY` types must be passed.

**See Also:**

[Named Data Types: Object, VARRAY, Nested Table](data-types.md) for more information about `SQLT_NTY`

### 20.15 About Defining Named Data Types

This section provides information about defining named data types (for example, objects, collections) and `REF`s.

This section includes the following topics:

- About Defining Named Data Type Output Variables

- About Defining REF Output Variables

- Information for Named Data Type and REF Defines, and PL/SQL OUT Binds

#### 20.15.1 About Defining Named Data Type Output Variables

For a named data type (object type, nested table, varray) define, two define calls are necessary.

The application should first call `OCIDefineByPos()` or `OCIDefineByPos2()`, specifying `SQLT_NTY` in the `dty` parameter. Following `OCIDefineByPos()` or `OCIDefineByPos2()`, the application must call `OCIDefineObject()` to set up additional attributes pertaining to a named data type define. In this case, the data buffer pointer in `OCIDefineByPos()` or `OCIDefineByPos2()` is ignored.

Specify the `SQLT_NTY` data type constant for a named data type define. In this case, the application fetches the result data into a host-language representation of the named data type. In most cases, this is a C struct generated by the Object Type Translator.

To make an `OCIDefineObject()` call, a pointer to the address of the C struct (preallocated or otherwise) must be provided. The object may have been created with `OCIObjectNew()`, allocated in the cache, or with user-allocated memory.

However, in the presence of inheritance, Oracle strongly recommends using objects in the object cache and not passing objects allocated out of user memory from the stack. Otherwise, due to instance substitutability, the server may send back a subtype instance when the client is expecting a supertype instance. This requires the server to dynamically resize the object, which is possible only for objects in the cache.

**See Also:**

- Information for Named Data Type and REF Defines, and PL/SQL OUT Binds for more important information about defining named data types

- [OCIDefineByPos()](bind-define-describe-functions.md) or [OCIDefineByPos2()](bind-define-describe-functions.md)

- [OCIDefineObject()](bind-define-describe-functions.md)

- [OCIObjectNew()](oci-miscellaneous-object-functions.md)

#### 20.15.2 About Defining REF Output Variables

As with named data types, defining for a `REF` output variable is a two-step process.

The first step is a call to `OCIDefineByPos()` or `OCIDefineByPos2()`, and the second is a call to `OCIDefineObject()`. Also as with named data types, the `SQLT_REF` data type constant is passed to the `dty` parameter of `OCIDefineByPos()`.

`SQLT_REF` indicates that the application is fetching the result data into a variable of type `OCIRef *`. This `REF` can then be used as part of object pinning and navigation.

**See Also:**

- [OCIDefineByPos()](bind-define-describe-functions.md) or [OCIDefineByPos2()](bind-define-describe-functions.md)

- [OCIDefineObject()](bind-define-describe-functions.md)

- Information for Named Data Type and REF Defines, and PL/SQL OUT Binds for more important information about defining `REF`s

- [About Working with Objects in OCI](oci-object-relational-programming.md) for more information about object pinning and navigation

#### 20.15.3 Information for Named Data Type and REF Defines, and PL/SQL OUT Binds

Consider the following important information as you work with named data type and `REF` defines. It includes pointers about memory allocation and indicator variable usage.

A PL/SQL OUT bind refers to binding a placeholder to an output variable in a PL/SQL block. Unlike a SQL statement, where output buffers are set up with define calls, in a PL/SQL block, output buffers are set up with bind calls.

- If the data type being defined is `SQLT_NTY`, then the indicator struct parameter of the `OCIDefineObject()` call (`void ** indpp`) is used, and the scalar indicator is completely ignored.

- If the data type is `SQLT_REF`, then the scalar indicator is used, and the indicator struct parameter of `OCIDefineObject()` is completely ignored.

- The use of indicator structures is optional. The user can pass a `NULL` pointer in the `indpp` parameter for the `OCIDefineObject()` call. During a fetch or PL/SQL OUT bind, therefore, the user is not interested in any information about being null.

- In a SQL define or PL/SQL OUT bind, you can pass in preallocated memory for either the output variable or the indicator. Then that preallocated memory is used to store result data, and any secondary memory (out-of-line memory), is deallocated. The preallocated memory must come from the cache (the result of an `OCIObjectNew()` call).

  **Note:**

  If you want your client application to allocate memory from its own private memory space, instead of the cache, your application must ensure that there is no secondary out-of-line memory in the object.

To preallocate object memory for an object define with type `SQLT_NTY`, client applications must use the `OCIObjectNew()` function. A client application should not allocate the object in its own private memory space, such as with `malloc()` or on the stack. The `OCIObjectNew()` function allocates the object in the object cache. The allocated object can be freed using `OCIObjectFree()`.

**Note:**

There is no change to the behavior of `OCIDefineObject()` when the user does not preallocate the object memory and instead initializes the output variable to null pointer value. In this case, the object is implicitly allocated in the object cache by the OCI library.

- In a SQL define or PL/SQL OUT bind, if the user passes in a `NULL` address for the output variable or the indicator, memory for the variable or the indicator is implicitly allocated by OCI.

- If an output object of type `SQLT_NTY` is atomically `NULL` (in a SQL define or PL/SQL OUT bind), only the `NULL` indicator struct gets allocated (implicitly if necessary) and populated accordingly to indicate the atomic nullity of the object. The top-level object does not get implicitly allocated.

- An application can free indicators by calling `OCIObjectFree()`. If there is a top-level object (as with a non-atomically `NULL` object), then the indicator is freed when the top-level object is freed with `OCIObjectFree()`. If the object is atomically null, then there is no top-level object, so the indicator must be freed separately.

- The indicator struct size pointer, `indszp`, and program variable size pointer, `pvszsp`, in the `OCIDefineObject()` call are optional. Users can pass `NULL` if these parameters are not needed.

This section includes the following topic: Information About Array Defines.

**See Also:**

- [About Binding Placeholders in PL/SQL](binding-and-defining-in-oci.md) for more information

- [OCIDefineObject()](bind-define-describe-functions.md)

- [OCIObjectNew()](oci-miscellaneous-object-functions.md)

- [OCIObjectFree()](oci-pin-unpin-and-free-functions.md)

- [OCI Navigational and Type Functions](oci-navigational-and-type-functions.md) for details about `OCIObjectNew()` and `OCIObjectFree()`

- [OCIDefineObject()](bind-define-describe-functions.md)

##### 20.15.3.1 Information About Array Defines

To perform array defines of named data types or `REF`s, the user must pass in an array of pointers to buffers (preallocated or otherwise) of the appropriate type.

Similarly, an array of scalar indicators (for `SQLT_REF` types) or an array of pointers to indicator structs (for `SQLT_NTY` types) must be passed.

### 20.16 About Binding and Defining Oracle C Data Types

This section summarizes information about binding and defining Oracle C named data types

Previous chapters of this book have discussed OCI bind and define operations. [About Binding Placeholders in OCI](using-sql_statements-in-oci.md) discussed the basics of OCI bind operations, whereas [About Defining Output Variables in OCI](using-sql_statements-in-oci.md) discussed the basics of OCI define operations. Information specific to binding and defining named data types and `REF`s was described in [Binding and Defining in OCI](binding-and-defining-in-oci.md).

The sections covering basic bind and define functionality showed how an application could use a scalar variable or array of scalars as an input (bind) value in a SQL statement, or as an output (define) buffer for a query.

The sections covering named data types and `REF`s showed how to bind or define an object or reference. [Pinning an Object](oci-object-relational-programming.md) expanded on this to talk about pinning object references, [Fetching Embedded Objects](oci-object-relational-programming.md) discussed fetching embedded instances, and [Object Navigation](object-advanced-topics-in-oci.md) discussed object navigation.

The purpose of this section is to cover binding and defining of individual attribute values, using the data type mappings explained in this chapter.

Variables of one of the types defined in this chapter, such as `OCINumber` or `OCIString`, can typically be declared in an application and used directly in an OCI bind or define operation because the appropriate data type code is specified. Table 20-12 lists the data types that you can use for binds and defines, along with their C mapping, and the OCI external data type that must be specified in the dty (data type code) parameter of the bind or define call.

Table 20-12 Data Type Mappings for Binds and Defines

| Data Type               | C Mapping         | OCI External Data Type and Code                       |
|:------------------------|:------------------|:------------------------------------------------------|
| Oracle `NUMBER`         | `OCINumber`       | VARNUM (SQLT_VNU)                                     |
| Oracle `DATE`           | `OCIDate`         | SQLT_ODT                                              |
| `BLOB`                  | `OCILobLocator *` | SQLT_BLOB                                             |
| `CLOB`, `NCLOB`         | `CILobLocator *`  | SQLTY_LOB                                             |
| `VARCHAR2`, `NVARCHAR2` | `OCIString *`     | SQLT_VST <sup>Foot 1</sup>                            |
| `RAW`                   | `OCIRaw *`        | SQLT_LVB <sup>Foot 1</sup>                            |
| `CHAR`, `NCHAR`         | `OCIString *`     | SQLT_VST                                              |
| Object                  | `struct *`        | Named Data Type (SQLT_NTY)                            |
| `REF`                   | `OCIRef *`        | REF (SQLT_REF)                                        |
| `VARRAY`                | `OCIArray *`      | Named Data Type (SQLT_NTY)                            |
| Nested Table            | `OCITable *`      | Named Data Type (SQLT_NTY)                            |
| `DATETIME`              | `OCIDateTime *`   | See Datetime and Interval (OCIDateTime, OCIInterval). |
| `INTERVAL`              | `OCIInterval *`   | See Datetime and Interval (OCIDateTime, OCIInterval). |

<sup>Footnote 1</sup>

Before fetching data into a define variable of type `OCIString *`, the size of the string must first be set using the `OCIStringResize()` routine. This may require a describe operation to obtain the length of the select-list data. Similarly, an `OCIRaw *` must be first sized with `OCIStringResize()`.

The following sections presents examples of how to use C-mapped data types in an OCI application:

- Bind and Define Examples

- Salary Update Examples

**See Also:**

- [Data Types](data-types.md) for a discussion of OCI external data types, and a list of data typecodes

- [OCIStringResize()](oci-string-functions.md)

#### 20.16.1 Bind and Define Examples

Shows how you can use variables of type `OCINumber` in OCI bind and define operations

The examples in this section demonstrate how you can use variables of type `OCINumber` in OCI bind and define operations.

Assume, for this example, that the following `person` object type was created:

    CREATE TYPE person AS OBJECT
    (name     varchar2(30),
    salary     number);

This type is then used to create an `employees` table that has a column of type `person`.

    CREATE TABLE employees
    (emp_id    number,
    job_title  varchar2(30),
    emp        person);

The Object Type Translator (OTT) generates the following C struct and null indicator struct for `person`:

    struct person
    {   OCIString * name;
       OCINumber salary;};
    typedef struct person person;

    struct person_ind
    {   OCIInd  _atomic;
       OCIInd  name;
       OCIInd  salary;}
    typedef struct person_ind person_ind;

Assume that the `employees` table has been populated with values, and an OCI application has declared a `person` variable:

    person *my_person;

The application then fetches an object into that variable through a `SELECT` statement, such as:

    text *mystmt = (text *) "SELECT person FROM employees
                            WHERE emp.name='Andrea'";

This requires defining `my_person` to be the output variable for this statement, using appropriate OCI define calls for named data types, as described in [Advanced Define Operations in OCI](binding-and-defining-in-oci.md). Executing the statement retrieves the `person` object named `Andrea` into the `my_person` variable.

Once the object is retrieved into `my_person`, the OCI application has access to the attributes of `my_person`, including the name and the salary.

The application could go on to update another employee's salary to be the same as Andrea's, as in the following example:

    text *updstmt = (text *) "UPDATE employees SET emp.salary = :newsal
                                WHERE emp.name = 'MONGO'";

Andrea's salary (stored in `my_person->salary`) would be bound to the placeholder `:newsal`, specifying an external data type of `VARNUM` (data type code=6) in the bind operation:

    OCIBindByName(...,":newsal",...,&my_person->salary,...,6,...);
    OCIStmtExecute(...,updstmt,...);

Executing the statement updates Mongo's salary in the database to be equal to Andrea's, as stored in `my_person.`

Conversely, the application could update Andrea's salary to be the same as Mongo's, by querying the database for Mongo's salary, and then making the necessary salary assignment:

    text *selstmt = (text *) "SELECT emp.salary FROM employees
                               WHERE emp.name = 'MONGO'";
    OCINumber mongo_sal;
    ...
    OCIDefineByPos(...,1,...,&mongo_sal,...,6,...);
    OCIStmtExecute(...,selstmt,...);
    OCINumberAssign(...,&mongo_sal, &my_person->salary);

In this case, the application declares an output variable of type `OCINumber` and uses it in the define step. The application also defines an output variable for position 1, and uses the appropriate data type code (6 for `VARNUM`).

The salary value is fetched into the `mongo_sal` `OCINumber`, and the appropriate OCI function, `OCINumberAssign()`, is used to assign the new salary to the copy of the `Andrea` object currently in the cache. To modify the data in the database, the change must be flushed to the server.

**See Also:**

- [Using the Object Type Translator with OCI](using-object-type-translator-in-oci.md) for a complete discussion of OTT

- [OCINumberAssign()](oci-NUMBER-functions.md)

#### 20.16.2 Salary Update Examples

Shows how the flow of calls is used to perform certain OCI tasks.

The examples in the previous section demonstrate the flexibility that the Oracle data types provide for bind and define operations. This section shows how you can perform the same operation in several different ways. You can use these data types in variety of ways in OCI applications.

The examples in this section demonstrate the flow of calls used to perform certain OCI tasks. An expanded pseudocode is used for these examples. Actual function names are used, but for simplicity not all parameters and typecasts are filled in. Other necessary OCI calls, such as handle allocations, have been omitted.

##### The Scenario

The scenario for these examples is as follows:

- An employee named `BRUCE` exists in the `employees` table for a hospital. See `person` type and `employees` table creation statements in the previous section.

- Bruce's current job title is `RADIOLOGIST`.

- Bruce is being promoted to `RADIOLOGY_CHIEF`, and along with the promotion comes a salary increase.

- Hospital salaries are in whole dollar values, are set according to job title, and are stored in a table called `salaries`, defined as follows:

      CREATE TABLE salaries
      (job_title   varchar2(20),
      salary       integer));

- Bruce's salary must be updated to reflect his promotion.

To update Bruce's salary to reflect the promotion, the application must retrieve the salary corresponding to `RADIOLOGY_CHIEF` from the `salaries` table, and update Bruce's salary. A separate step would write his new title and the modified object back to the database.

Assume that a variable of type `person` has been declared as follows:

    person * my_person;

The object corresponding to Bruce has been fetched into `person`. The following sections present three different ways in which the salary update could be performed.

This section includes the following topics:

- Method 1 - Fetch, Convert, Assign

- Method 2 - Fetch and Assign

- Method 3 - Direct Fetch

- Summary and Notes

##### 20.16.2.1 Method 1 - Fetch, Convert, Assign

Shows how to fetch the new salary, convert the integer data type to `OCINumber`, then assign the new salary to an employee.

Example 20-13 uses the following method:

1.  Do a traditional OCI define using an integer variable to retrieve the new salary from the database.
2.  Convert the integer to an `OCINumber.`
3.  Assign the new salary to Bruce.

Example 20-13 Method 1 for a Salary Update: Fetch, Convert, and Assign

    #define INT_TYPE 3        /* data type code for sword integer define */

    text *getsal = (text *) "SELECT salary FROM salaries
                            WHERE job_title='RADIOLOGY_CHIEF'";
    sword    new_sal;
    OCINumber   orl_new_sal;
    ...
    OCIDefineByPos(...,1,...,new_sal,...,INT_TYPE,...);
                            /* define int output */
    OCIStmtExecute(...,getsal,...);
                            /* get new salary as int */
    OCINumberFromInt(...,new_sal,...,&orl_new_sal);
                            /* convert salary to OCINumber */
    OCINumberAssign(...,&orl_new_sal, &my_person->salary);
                            /* assign new salary */

##### 20.16.2.2 Method 2 - Fetch and Assign

Shows how to fetch the salary and get it as an `OCINumber` and then assign the new salary to an employee.

This method (Example 20-14) eliminates one of the steps described in Method 1.

1.  Define an output variable of type `OCINumber`, so that no conversion is necessary after the value is retrieved.
2.  Assign the new salary to Bruce.

Example 20-14 Method 2 for a Salary Update: Fetch and Assign, No Convert

    #define VARNUM_TYPE 6         /* data type code for defining VARNUM */

    text *getsal = (text *) "SELECT salary FROM salaries
                                  WHERE job_title='RADIOLOGY_CHIEF'";
    OCINumber   orl_new_sal;
    ...
    OCIDefineByPos(...,1,...,orl_new_sal,...,VARNUM_TYPE,...);
                                         /* define OCINumber output */
    OCIStmtExecute(...,getsal,...);      /* get new salary as OCINumber */
    OCINumberAssign(...,&orl_new_sal, &my_person->salary);
                                         /* assign new salary */

##### 20.16.2.3 Method 3 - Direct Fetch

Shows how to do the entire operation with a single define and fetch.

This method (Example 20-15) accomplishes the entire operation with a single define and fetch. No intervening output variable is used, and the value retrieved from the database is fetched directly into the salary attribute of the object stored in the cache.

Because the object corresponding to Bruce is pinned in the object cache, use the location of his salary attribute as the define variable, and execute or fetch directly into it.

Example 20-15 Method 3 for a Salary Update: Direct Fetch

    #define VARNUM_TYPE 6         /* data type code for defining VARNUM */

    text *getsal = (text *) "SELECT salary FROM salaries
                                WHERE job_title='RADIOLOGY_CHIEF'";
    ...
    OCIDefineByPos(...,1,...,&my_person->salary,...,VARNUM_TYPE,...);
                /* define bruce's salary in cache as output variable */
    OCIStmtExecute(...,getsal,...);
                 /* execute and fetch directly */

##### 20.16.2.4 Summary and Notes

Summarizes what the previous examples demonstrated and highlights additional information.

As the previous three examples show, the C data types provide flexibility for binding and defining. In these examples an integer can be fetched, and then converted to an `OCINumber` for manipulation. You can use an `OCINumber` as an intermediate variable to store the results of a query. Or, data can be fetched directly into a desired `OCINumber` attribute of an object.

**Note:**

In these examples it is important to remember that in OCI, if an output variable is defined before the execution of a query, the resulting data is prefetched directly into the output buffer.

In the preceding examples, extra steps would be necessary to ensure that the application writes changes to the database permanently. These might involve SQL `UPDATE` calls and OCI transaction commit calls.

These examples all dealt with define operations, but a similar situation applies for binding.

Similarly, although these examples dealt exclusively with the `OCINumber` type, a similar variety of operations are possible for the other Oracle C types described in the remainder of this chapter.

### 20.17 SQLT_NTY Bind and Define Examples

The following code fragments demonstrate the use of the `SQLT_NTY` named data type in the bind call including `OCIBindObject()` and the `SQLT_NTY` named data type in the define call including `OCIDefineObject()`.

In each example, a previously defined SQL statement is being processed.

This section includes the following topics:

- SQLT_NTY Bind Example

- SQLT_NTY Define Example

**See Also:**

- [OCIBindObject()](bind-define-describe-functions.md)

- [OCIDefineObject()](bind-define-describe-functions.md)

#### 20.17.1 SQLT_NTY Bind Example

Shows how to use the `SQLT_NTY` named data type in the bind call including `OCIBindObject()`.

Example 20-16 shows how to use the `SQLT_NTY` named data type in the bind call including `OCIBindObject()`.

Example 20-16 Using the SQLT_NTY Bind Call Including OCIBindObject()

    /*
    ** This example performs a SQL insert statement
    */
    void insert(envhp, svchp, stmthp, errhp, insstmt, nrows)
    OCIEnv *envhp;
    OCISvcCtx *svchp;
    OCIStmt *stmthp;
    OCIError *errhp;
    text *insstmt;
    ub2   nrows;
    {
      OCIType *addr_tdo = (OCIType *)0 ;
      address  addrs;
      null_address naddrs;
      address *addr = &addrs;
      null_address *naddr = &naddrs;
      sword custno =300;
      OCIBind *bnd1p, *bnd2p;
      ub2 i;

      /* define the application request  */
      checkerr(errhp, OCIStmtPrepare(stmthp, errhp, (text *) insstmt,
               (ub4) strlen((char *)insstmt),
               (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT));

      /* bind the input variable */
     checkerr(errhp, OCIBindByName(stmthp, &bnd1p, errhp, (text *) ":custno",
              (sb4) -1, (void  *) &custno,
              (sb4) sizeof(sword), SQLT_INT,
              (void  *) 0, (ub2 *)0, (ub2 *)0, (ub4) 0, (ub4 *) 0,
              (ub4) OCI_DEFAULT));

      checkerr(errhp, OCIBindByName(stmthp, &bnd2p, errhp, (text *) ":addr",
              (sb4) -1, (void  *) 0,
              (sb4) 0, SQLT_NTY, (void  *) 0, (ub2 *)0, (ub2 *)0,
              (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT));

      checkerr(errhp,
                    OCITypeByName(envhp, errhp, svchp, (const text *)
                    SCHEMA, (ub4) strlen((char *)SCHEMA),
                    (const text *)"ADDRESS_VALUE",
                    (ub4) strlen((char *)"ADDRESS_VALUE"),
                    (text *)0, 0, OCI_DURATION_SESSION,
                    OCI_TYPEGET_HEADER, &addr_tdo));

      if(!addr_tdo)
      {
        printf("Null tdo returned\n");
        return;
      }

      checkerr(errhp, OCIBindObject(bnd2p, errhp, addr_tdo, (void  **) &addr,
            (ub4 *) 0, (void  **) &naddr, (ub4 *) 0));

**See Also:**

[OCIBindObject()](bind-define-describe-functions.md)

#### 20.17.2 SQLT_NTY Define Example

Shows how to use the `SQLT_NTY` named data type in the define call including `OCIDefineObject()`.

Example 20-17 shows how to use the `SQLT_NTY` named data type in the define call including `OCIDefineObject()`.

Example 20-17 Using the SQLT_NTY Define Call Including OCIDefineObject()

    /*
    ** This example executes a SELECT statement from a table that includes
    ** an object.
    */

    void selectval(envhp, svchp, stmthp, errhp)
    OCIEnv *envhp;
    OCISvcCtx *svchp;
    OCIStmt *stmthp;
    OCIError *errhp;
    {
      OCIType *addr_tdo = (OCIType *)0;
      OCIDefine *defn1p, *defn2p;
      address *addr = (address *)NULL;
      sword custno =0;
      sb4 status;

      /* define the application request  */
      checkerr(errhp, OCIStmtPrepare(stmthp, errhp, (text *) selvalstmt,
                            (ub4) strlen((char *)selvalstmt),
                            (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT));

      /* define the output variable */
    checkerr(errhp, OCIDefineByPos(stmthp, &defn1p, errhp, (ub4) 1, (void  *)
           &custno, (sb4) sizeof(sword), SQLT_INT, (void  *) 0, (ub2 *)0,
           (ub2 *)0, (ub4) OCI_DEFAULT));

    checkerr(errhp, OCIDefineByPos(stmthp, &defn2p, errhp, (ub4) 2, (void  *)
            0, (sb4) 0, SQLT_NTY, (void  *) 0, (ub2 *)0,
            (ub2 *)0, (ub4) OCI_DEFAULT));

    checkerr(errhp,
                   OCITypeByName(envhp, errhp, svchp, (const text *)
                   SCHEMA, (ub4) strlen((char *)SCHEMA),
                   (const text *) "ADDRESS_VALUE",
                   (ub4) strlen((char *)"ADDRESS_VALUE"),
                   (text *)0, 0, OCI_DURATION_SESSION,
                   OCI_TYPEGET_HEADER, &addr_tdo));

      if(!addr_tdo)
      {
        printf("NULL tdo returned\n");
        return;
      }

      checkerr(errhp, OCIDefineObject(defn2p, errhp, addr_tdo, (void  **)
           &addr, (ub4 *) 0, (void  **) 0, (ub4 *) 0));

      checkerr(errhp, OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
           (OCISnapshot *) NULL, (OCISnapshot *) NULL, (ub4) OCI_DEFAULT));

**See Also:**

[OCIDefineObject()](bind-define-describe-functions.md)
