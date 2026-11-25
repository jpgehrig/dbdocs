Error messages are listed for applications that use Oracle XML Developer's Kit (XDK) for Java during the execution of the XML SQL Utility (XSU) interfaces.

### C.1 Generic Error Messages

Generic error messages are in the range XSUE-0000 through XSUE-0099.

#### XSUE-0000: Internal Error -- Exception Caught string

#### XSUE-0001: Internal Error -- string

#### XSUE-0002: string is not a scalar column. The row id attribute can only get values from scalar columns.

#### XSUE-0003: string is not a valid column name.

#### XSUE-0004: This object has been closed. If you would like the object not to be closed implicitly between calls, see the string method.

#### XSUE-0005: The row-set enclosing tag and the row enclosing tag are both omitted; consequently, the result can consist of at most one row which contains exactly one column which is not marked to be an XML attribute.

#### XSUE-0006: The row enclosing tag or the row-set enclosing tag is ommitted; consequently to get a well formed XML document, the result can only consist of a single row with multiple columns or multiple rows with exactly one column which is not marked to be an XML attribute.

#### XSUE-0007: Parsing of the sqlname failed -- invalid arguments.

#### XSUE-0008: Character string is not allowed in an XML tag name.

#### XSUE-0009: this method is not supported by string class. Please use string instead.

#### XSUE-0010: The number of bind names does not equal the number of bind values.

#### XSUE-0011: The number of bind values does not match the number of binds in the SQL statement.

#### XSUE-0012: Bind name identifier string does not exist in the sql query.

#### XSUE-0013: The bind identifier has to be of non-zero length.

#### XSUE-0014: Root node supplied is null.

#### XSUE-0015: Invalid LOB locator specified.

#### XSUE-0016: File string does not exit.

#### XSUE-0017: Can not create oracle.sql.STRUCT object of a type other than oracle.sql.STRUCT (i.e. ADT).

#### XSUE-0018: Null is not a valid DocumentHandler.

#### XSUE-0019: Null and empty string are not valid namespace aliases.

#### XSUE-0020: to use this method you will have to override it in your subclass.

#### XSUE-0021: You are using an old version of the gss library; thus, sql-xml name escaping is not supported.

#### XSUE-0022: cannot create XMLType object from opaque base type: string

### C.2 Query Error Messages

Query error messages are in the range XSUE-0100 through XSUE-0199.

#### XSUE-0100: Invalid context handle specified.

#### XSUE-0101: In the FIRST row of the resultset there is a nested cursor whose parent cursor is empty; when this condition occurs we are unable to generate a dtd.

#### XSUE-0102: string is not a valid IANA encoding.

#### XSUE-0103: The resultset is a "TYPE_FORWARD_ONLY" (non-scrollable); consequently, xsu can not reposition the read point. Furthermore, since the result set has been passed to the xsu by the caller, the xsu can not recreate the resultset.

#### XSUE-0104: input character is invalid for well-formed XML: string

### C.3 DML Error Messages

Data manipulation language (DML) error messages are in the range XSUE-0200 through XSUE-0299.

#### XSUE-0200: The XML element tag string does not match the name of any of the columns/attributes of the target database object.

#### XSUE-0201: NULL is an invalid column name.

#### XSUE-0202: Column string, specified to be a key column, does not not exits in table string.

#### XSUE-0203: Column string, specified as column to be updated, does not exist in the table string.

#### XSUE-0204: Invalid REF element - string - attribute string missing.

#### XSUE-0206: Must specify key values before calling update routine. Use the string function.

#### XSUE-0207: UpdateXML: No columns to update. The XML document must contain some non-key columns to update.

#### XSUE-0208: The key column array must be non empty.

#### XSUE-0209: The key column array must be non empty.

#### XSUE-0210: No rows to modify -- the row enclosing tag missing. Specify the correct row enclosing tag.

#### XSUE-0211: string encountered during processing ROW element string in the XML document.

#### XSUE-0212: string XML rows were successfully processed.

#### XSUE-0213: All prior XML row changes were rolled back.
