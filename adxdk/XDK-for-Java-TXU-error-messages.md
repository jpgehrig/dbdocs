Error messages are listed for applications that use Oracle XML Developer's Kit (XDK) for Java during the execution of TXU interfaces.

### B.1 DLF Error Messages

Data Loading Format (DLF) error messages are in the range TXU-0100 through TXU-0199.

#### TXU-0100: parameter string in query string not found

Cause: There is not a placeholder for the parameter in the query

Action: Supply a parameter whose id can be found as an associated placeholder in the associated query

#### TXU-0101: incompatible attributes col and constant coexist at string in query string

Cause: Attributes 'col' and 'constant' cannot coexist

Action: Remove either 'col' or 'constant' attribute

#### TXU-0102: node string not found

Cause: The document lacks an expected node

Action: Supply the missing node

#### TXU-0103: element string lacks content

Cause: The element has no data

Action: Supply content

#### TXU-0104: element string with SQL string lacks col or constant attribute

Cause: The element lacks a required attribute of 'col' or 'constant'

Action: Supply either 'col' or 'constant' attribute

#### TXU-0105: SQL exception string while processing SQL string

Cause: An error occurred during the SQL execution

Action: Resolve the error in the SQL statement

#### TXU-0106: no data for column string selected by SQL string

Cause: The SQL query returned no data

Action: Supply data or modify your query

#### TXU-0107: datatype string not supported

Cause: An attempt to process an unsupported data type was made

Action: Change the data type to a supported one

#### TXU-0108: missing maxsize attribute for column string

Cause: The size-unit attribute is specified but maxsize is not.

Action: Supply the maxsize attribute, too

#### TXU-0109: a text length of string for string exceeds the allowed maximum of string

Cause: The length of the text data is too long

Action: Shorten the data so it fits in the limit, or enlarge the maxsize attribute and ensure the database column is large enough

#### TXU-0110: undeclared column string in row string

Cause: A column in the data section is not declared in the columns section

Action: Modify the column name to a declared one

#### TXU-0111: lacking column data for string in row string

Cause: A column is declared but the data is missing.

Action: Supply the col element whose name attribute matches the column name

#### TXU-0112: undeclared query parameter string for column string

Cause: The query parameter refers to an undeclared column

Action: Specify a declared column

#### TXU-0113: incompatible attribute string with a query on column string

Cause: A column with a query cannot have the specified attribute

Action: Remove either the attribute or query

#### TXU-0114: DLF parse error (string) on line string, character string in string

Cause: The format is in error as reported

Action: Correct the erroneous part

#### TXU-0115: The specified date string string has an invalid format

Cause: The specified date string does not match the specified formatstring.

Action: Make sure the date string is in an appropriate date format

### B.2 TransX Informational Messages

TransX informational messages are in the range TXU-0200 throughTXU-0299.

#### TXU-0200: duplicate row at string

Cause: A duplicate row exists in the database

Action: This message appears on the DuplicateRowException to inform applications of existance of one or more duplicate rows already stored in the database

### B.3 TransX Error Messages

TransX error messages are in the range TXU-0300 through TXU-0399.

#### TXU-0300: document string not found

Cause: The document could not be located

Action: Modify the document location or supply the document at the location

#### TXU-0301: file string could not be read

Cause: An I/O error happened when reading the file

Action: Resolve the I/O problem

#### TXU-0302: archive string not found

Cause: The archive file could not be located

Action: Ensure that the CLASSPATH includes TransX correctly and only once

#### TXU-0303: schema string not found in string

Cause: The schema definition of DLF could not be located

Action: Get an unbroken copy of a TransX archive

#### TXU-0304: archive path for string not found

Cause: The path for the archive could not be determined

Action: Ensure that the CLASSPATH includes TransX correctly and only once

#### TXU-0305: no database connection on string call for string

Cause: The operation was attempted without a database connection

Action: Open a connection first

#### TXU-0306: null tablename given; access denied

Cause: The table name is not provided

Action: Specify a table name

#### TXU-0307: lookup-keys could not be determined string

Cause: The data dictionary is corrupted

Action: Restore the data dictionary

#### TXU-0308: binary file string not found

Cause: The file name is invalid

Action: Supply a good file name

#### TXU-0309: a file size of string exceeds the allowed maximum of 2,000 bytes

Cause: The file is too large

Action: Reduce the file size

### B.4 Assertion Error Messages

Assertion error messages are in the range TXU-0400 through TXU-0499.

#### TXU-0400: missing SQL statement element on string

Cause: An internal assertion was not successful

Action: Contact Oracle customer support

#### TXU-0401: missing node string

Cause: An internal assertion was not successful

Action: Contact Oracle customer support

#### TXU-0402: invalid flag string

Cause: An internal assertion was not successful

Action: Contact Oracle customer support

#### TXU-0403: internal error string

Cause: An internal assertion was not successful

Action: Contact Oracle customer support

#### TXU-0404: unexpected Exception string

Cause: An internal assertion was not successful

Action: Contact Oracle customer support
