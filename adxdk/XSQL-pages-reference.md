Reference information is presented for the XSQL pages framework.

XSQL Configuration File Parameters describes settings in the XSQL configuration file. Table 33-1 lists the legal built-in actions for XSQL pages.

Table 33-1 Built-In XSQL Elements and Action Handler Classes

| XSQL Action Element                    | Handler Class in oracle.xml.xsql.actions | Purpose                                                                                                                                                             |
|:---------------------------------------|:-----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `<xsql:action>`                        | `XSQLExtensionActionHandler`             | Invoke a user-defined action handler, implemented in Java, for executing custom logic and including custom Extensible Markup Language (XML) data in your XSQL page. |
| `<xsql:delete-request>`                | `XSQLDeleteRequestHandler`               | Delete an existing row in the database based on the posted XML document supplied in the request.                                                                    |
| `<xsql:dml>`                           | `XSQLDMLHandler`                         | Execute a structured query language (SQL) data manipulation language (DML) statement or a Procedural Language/Structured Query Language (PL/SQL) anonymous block.   |
| `<xsql:if-param>`                      | `XSQLIfParamHandler`                     | Conditionally include XML content or other XSQL actions.                                                                                                            |
| `<xsql:include-owa>`                   | `XSQLIncludeOWAHandler`                  | Include the results of a stored procedure that uses the Oracle Web Agent (OWA) packages in the database to generate XML.                                            |
| `<xsql:include-param>`                 | `XSQLGetParameterHandler`                | Include a parameter and its value as an element in the XSQL page.                                                                                                   |
| `<xsql:include-posted-include-posted>` | `XSQLIncludePostedXMLHandler`            | Include the XML document that has been posted in the request into the XSQL page.                                                                                    |
| `<xsql:include-request-params>`        | `XSQLIncludeRequestHandler`              | Include all request parameters as XML elements in the XSQL page.                                                                                                    |
| `<xsql:include-xml>`                   | `XSQLIncludeXMLHandler`                  | Include arbitrary XML resources at any point in your page by relative or absolute URL.                                                                              |
| `<xsql:include-xsql>`                  | `XSQLIncludeXSQLHandler`                 | Include the results of one XSQL page at any point inside another.                                                                                                   |
| `<xsql:insert-param>`                  | `XSQLInsertParameterHandler`             | Insert the XML document contained in the value of a single parameter.                                                                                               |
| `<xsql:insert-request>`                | `XSQLInsertRequestHandler`               | Insert the XML document or HTML form posted in the request into a table or view.                                                                                    |
| `<xsql:query>`                         | `XSQLQueryHandler `                      | Execute an arbitrary SQL statement and include its result in canonical XML format.                                                                                  |
| `<xsql:ref-cursor-function>`           | `XSQLRefCursorFunctionHandler `          | Include the canonical XML representation of the result set of a cursor returned by a PL/SQL stored function.                                                        |
| `<xsql:set-cookie>`                    | `XSQLSetCookieHandler `                  | Set an HTTP Cookie.                                                                                                                                                 |
| `<xsql:set-page-param>`                | `XSQLSetPageParamHandler `               | Set an HTTP-Session level parameter. Set a page-level (local) parameter that can be referred to in subsequent SQL statements in the page.                           |
| `<xsql:set-session-param>`             | `XSQLSetSessionParamHandler `            | Set an HTTP-Session level parameter.                                                                                                                                |
| `<xsql:set-stylesheet-param>`          | `XSQLStylesheetParameterHandler `        | Set the value of a top-level Extensible Stylesheet Language Transformation (XSLT) parameter.                                                                        |
| `<xsql:update-request>`                | `XSQLUpdateRequestHandler `              | Update an existing row in the database based on the posted XML document supplied in the request.                                                                    |

### 33.1 XSQL Configuration File Parameters

You can use the XSQL configuration file to tune your XSQL pages environment. The available configuration settings are described.

Table 33-2 XSQL Configuration File Settings

| Configuration Setting Name                                                                                                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `XSQLConfig/servlet/output-buffer-size`                                                                                                                                     | Sets the size in bytes of the buffered output stream. If the servlet engine already buffers I/O to the servlet output stream, you can set to `0` (the default) to avoid additional buffering. Any nonnegative integer is valid.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `XSQLConfig/servlet/suppress-mime-charset/media-type`                                                                                                                       | The XSQL servlet sets the HTTP `ContentType` header to indicate the Multipurpose Internet Mail Extensions (MIME) type of the resource returned to the request. By default, the servlet includes the optional character set data in the MIME type. For a particular MIME type, you can suppress the inclusion of the character set data by including a `<media-type>` element, with the desired MIME type as its contents. You can list any number of `<media-type>` elements. Valid value is any string.                                                                                                                                                                                                                                                                                                                                                                                 |
| `XSQLConfig/processor/character-set-conversion/`<br>`default-charset `<br>Note: Setting name is a single line. It is displayed on two lines due to space constraints.       | Performs character set conversion by default on the value of HTTP parameters to compensate for the default character set used by most servlet engines. The default base character set used for conversion is the Java `8859_1`, which corresponds to the Internet Assigned Numbers Authority (IANA) `ISO-8859-1` set. If your servlet engine uses a different character set as its base, then you can specify this value here.<br>To suppress character set conversion, specify the empty element `<none/>` as the content of the `<default-charset>` element instead of a character set name. This technique is useful if you are working with parameter values that are correctly representable with your servlet default character set. It eliminates overhead associated with performing the character set conversion.<br>Valid values are any Java character set name or `<none/>`. |
| `XSQLConfig/processor/reload-connections-on-error`                                                                                                                          | Connection definitions are cached when the XSQL pages processor is initialized. Set to `yes` (default) to cause the processor to reread the `XSQLConfig.xml` file to reload connection definitions if an attempt is made to request a connection name that is not in the cached connection list. The `yes` setting is useful for adding new `<connection>` definitions to the file while the servlet is running. Set to `no` to avoid reloading the connection definition file when a connection name is not found in the in-memory cache. Valid values are `yes` and `no`.                                                                                                                                                                                                                                                                                                              |
| `XSQLConfig/processor/default-fetch-size`                                                                                                                                   | Sets the default value of the row fetch size for retrieving information from SQL queries. It takes effect only when you use the Oracle JDBC driver; otherwise the setting is ignored. This technique reduces network round trips to the database from the servlet engine running in a different tier.<br>Default is `50`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `XSQLConfig/processor/page-cache-size`                                                                                                                                      | Sets the size of the cache for XSQL page templates and so determines the maximum number of XSQL pages that are cached. Least recently used pages move out of the cache if you go above this number. Default is `25`. Any nonzero positive integer is valid.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `XSQLConfig/processor/stylesheet-cache-size`                                                                                                                                | Sets the size of the cache for XSLT stylesheets and so determines the maximum number of XSQL pages that are cached. Least recently used pages move out of the cache if you go above this number. Default is `25`. Any nonzero positive integer is valid.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `XSQLConfig/processor/stylesheet-pool/initial`                                                                                                                              | Each cached stylesheet is a pool of cached stylesheet instances to improve throughput. Sets the initial number of stylesheets to be allocated in each stylesheet pool.<br>Default is `1`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `XSQLConfig/processor/stylesheet-pool/increment`                                                                                                                            | Sets the number of stylesheets allocated when the stylesheet pool must grow due to increased load on the server.<br>Default is `1`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `XSQLConfig/processor/stylesheet-pool/timeout-seconds`                                                                                                                      | Sets the number of seconds of inactivity before a stylesheet instance in the pool is removed to free resources as the pool tries to shrink back to its initial size.<br>Default is `60`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `XSQLConfig/processor/connection-pool/initial`                                                                                                                              | Controls the initial number of Java Database Connectivity (JDBC) connections allocated in each connection pool. The XSQL pages processor's default connection manager implements connection pooling to improve throughput.<br>Default is `2`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `XSQLConfig/processor/connection-pool/increment`                                                                                                                            | Sets the number of connections allocated when the connection pool must grow due to increased load on the server.<br>Default is `1`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `XSQLConfig/processor/connection-pool/timeout-seconds`                                                                                                                      | Sets the number of seconds of inactivity before a JDBC connection in the pool is removed to free resources as the pool tries to shrink back to its initial size.<br>Default is `60`. Valid value is any nonzero positive integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `XSQLConfig/processor/connection-pool/dump-allowed`                                                                                                                         | Determines whether a diagnostic report of connection pool activity can be requested by passing the `dump-pool=y` parameter in the page request.<br>Default is `no`. Valid value is `yes` or `no`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `XSQLConfig/processor/connection-manager/factory`                                                                                                                           | Specifies the fully qualified Java class name of the XSQL connection manager factory implementation. If not specified, default is `XSQLConnectionManagerFactoryImpl`.<br>Valid value is any class name that implements the `XSQLConnectionManagerFactory` interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `XSQLConfig/processor/owa/fetch-style`                                                                                                                                      | Sets the default OWA Page Buffer fetch style used by the `<xsql:include-owa>` action. Valid values are `CLOB` (default) or `TABLE`.<br>If set to `CLOB`, then the processor uses a temporary `CLOB` to retrieve the OWA page buffer. If set to `TABLE`, then the processor uses a more efficient approach that requires the Oracle Database user-defined type `XSQL_OWA_ARRAY`. Create this type with this data definition language (DDL) statement:<br>`CREATE TYPE xsql_owa_array AS TABLE OF VARCHAR2(32767)`                                                                                                                                                                                                                                                                                                                                                                         |
| `XSQLConfig/processor/timing/page`                                                                                                                                          | Determines whether the XSQL page processor adds an `xsql-timing` attribute to the document element of the page whose value reports the elapsed number of milliseconds required to process the page.<br>Valid values are `yes` or `no` (default).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `XSQLConfig/processor/timing/action`                                                                                                                                        | Determines whether a the XSQL page processor adds comment to the page just before the action element whose contents reports the elapsed number of milliseconds required to process the action.<br>Valid values are `yes` or `no` (default).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `XSQLConfig/processor/logger/factory`                                                                                                                                       | Specifies the fully qualified Java class name of a custom XSQL logger factory implementation. If not set, then no logger is used.<br>Valid value is any class name that implements the `XSQLLoggerFactory` interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `XSQLConfig/processor/error-handler/class`                                                                                                                                  | Specifies the fully qualified Java class name of a custom XSQL error handler. The specified handler is the default error handler implementation. If not set, then the default error handler is used.<br>Valid value is any class name that implements the `XSQLErrorHandler` interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `XSQLConfig/processor/xml-parsing/preserve-whitespace`                                                                                                                      | Determines whether the XSQL pages processor preserves white space when parsing XSQL pages and XSLT stylesheets.<br>Valid values are `true` (default) or `false`. Changing the default to false can slightly speed up processing of XSQL pages and stylesheets because ignoring white space while parsing is faster than preserving it.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `XSQLConfig/processor/security/stylesheet/defaults/`<br>`allow-client-style`<br>Note: Setting name is a single line. It is displayed on two lines due to space constraints. | Prevents client overriding of the stylesheet. Valid values are `yes` and `no`.<br>During development it is sometimes useful to use the XSQL stylesheet override feature by providing a value for the `xml-stylesheet` parameter in the request. You can use the `xml-stylesheet=none` combination to temporarily disable the application of the stylesheet for debugging purposes.<br>You can add the `allow-client-style="no"` attribute to the document element of each XSQL page to prohibit client overriding of the stylesheet in production applications. This setting can globally change the default behavior for `allow-client-style` in a single place.<br>This setting specifies only default behavior. If the attribute value is explicitly specified on the document element for a given XSQL page, its value takes precedence over this global default.                    |
| `XSQLConfig/processor/security/stylesheet/`<br>`trusted-hosts/host`<br>Note: Setting name is a single line. It is displayed on two lines due to space constraints.          | Specifies that any absolute URL to an XSLT stylesheet must be from a trusted host whose name is listed in the configuration file. List any number of `<host>` elements inside the `<trusted-hosts>` element. The name of the local machine, `localhost`, and `127.0.0.1` are trusted hosts by default. Valid values are any host name or IP address.<br>The XSLT processor supports Java extension functions. Typically, XSQL pages refer to XSLT stylesheets with relative URLs.                                                                                                                                                                                                                                                                                                                                                                                                        |
| `XSQLConfig/http/proxyhost`                                                                                                                                                 | Sets the name of the HTTP proxy server to use when processing `URL`s with the HTTP protocol.<br>Valid value is any host name or Internet Protocol (IP) address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `XSQLConfig/http/proxyport`                                                                                                                                                 | Sets the port number of the HTTP proxy server to use when processing URLs with the HTTP protocol.<br>Valid value is any nonzero integer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `XSQLConfig/connectiondefs/connection`                                                                                                                                      | Defines a short name and the JDBC details for a named connection used by the XSQL pages processor.<br>You may supply any number of `<connection>` element children of `<connectiondefs>`. Each connection definition must supply a `name` attribute and may supply children elements `<username>, <password>, <driver>, <dburl>`, and `<autocommit>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `XSQLConfig/connectiondefs/connection/username`                                                                                                                             | Defines the user name for the current connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `XSQLConfig/connectiondefs/connection/password`                                                                                                                             | Defines the password for the current connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `XSQLConfig/connectiondefs/connection/dburl`                                                                                                                                | Defines the JDBC connection URL for the current connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `XSQLConfig/connectiondefs/connection/driver`                                                                                                                               | Specifies the fully qualified Java class name of the JDBC driver used for the current connection. If not specified, defaults to `oracle.jdbc.driver.OracleDriver`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `XSQLConfig/connectiondefs/connection/autocommit`                                                                                                                           | Explicitly sets the Auto Commit flag for the current connection. If not specified, the connection uses the JDBC driver default setting for Auto Commit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `XSQLConfig/serializerdefs/serializer`                                                                                                                                      | Defines a named custom serializer implementation. You can supply any number of `<serializer>` element children of `<serializerdefs>`. Each must specify both a `<name>` and a `<class>` child element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `XSQLConfig/serializerdefs/serializer/name`                                                                                                                                 | Defines the name of the current custom serializer definition.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `XSQLConfig/connectiondefs/connection/class`                                                                                                                                | Specifies the fully qualified Java class name of the current custom serializer. The class must implement the `XSQLDocumentSerializer` interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

### 33.2 \<xsql:action\>

Element `<xsql:action>` is described.

#### Purpose

Invokes a user-defined action handler, implemented in Java, for executing custom logic and including custom XML data in a XSQL page. The Java class invoked with this action must implement the `oracle.xml.xsql.XSQLActionHandler` interface.

Use `<xsql:action>` to perform tasks that are not handled by the built-in action handlers. Custom actions can supply arbitrary XML content to the data page and perform arbitrary processing.

#### Usage Notes

The XSQL page processor processes the actions in a page in this way:

1.  Constructs an instance of the action handler class with the default constructor.

2.  Initializes the handler instance with the action element object and the page processor context by invoking the method `init(Element actionElt, XSQLPageRequest context)`.

3.  Invokes the method that allows the handler to handle the action `handleAction(Node result)`.

#### Syntax

The syntax for this action is as follows, where `handler` is a single, required attribute named whose value is the fully qualified Java class name of the invoked action, `yourpackage` is the Java package, and `YourCustomHandler` is the Java class:

    <xsql:action handler="yourpackage.YourCustomHandler"/>

Some action handlers expect text content or element content to appear inside the `<xsql:action>` element. In this case, use syntax such as:

    <xsql:action handler="yourpackage.YourCustomHandler">
      Some_text
    </xsql:action>

You can also use this syntax:

    <xsql:action handler="yourpackage.YourCustomHandler">
      <some>
        <other/>
        <elements/>
        <here/>
      </some>
    </xsql:action>

#### Attributes

The only required attribute is `handler`, but you can supply additional attributes to the handler. For example, if `yourpackage.YourCustomHandler` is expecting attributes named `param1` and `param2`, then use this syntax:

    <xsql:action handler="yourpackage.YourCustomHandler" param1="xxx" param2="yyy">

#### Examples

The following example shows an XSQL page that invokes the `myactions.StockQuotes` Java class. It includes stock quotes from Google for any symbols passed in with the `symbol` parameter. If this parameter is not supplied, it supplies a default list.

Retrieving Stock Quotes

    <?xml version="1.0"?>
    <page xmlns:xsql="urn:oracle-xsql">
      <xsql:action handler="myactions.StockQuotes"
                   symbols="{@symbol}"
                   symbol="ORCL,SAP,MSFT,IBM"/>
    </page>

### 33.3 \<xsql:delete-request\>

Element `<xsql:delete-request>` is described.

#### Purpose

Accepts data posted from an XML document or HTML form and uses the [XML SQL Utility (XSU)](glossary.md) to delete the content of an XML document in canonical form from a target table or view.

By combining XSU with XSLT, you can transform XML into the canonical format expected by a given table. Afterward, you can use XSU to delete the resulting canonical XML. For a specified database table, the canonical XML form is given by one row of XML output from a `SELECT *` query against the table.

#### Syntax

The syntax for this action is as follows, where `table_name` is the name of a table and `key` is a list of one or more columns to use as the unique key:

    <xsql:delete-request table="table_name" key-columns="key"/>

#### Attributes

Table 33-3 lists the optional attributes that you can use on the` <xsql:delete-request>` action. Required attributes are in bold

Table 33-3 Attributes for \<xsql:delete-request\>

| Attribute Name                      | Description                                                                                                                                                                                                                                              |
|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table = "string"`                  | Name of the table, view, or synonym to use for deleting the XML data.                                                                                                                                                                                    |
| `key-columns = "string string ..."` | Space-delimited or comma-delimited list of one or more column names. The processor uses the values of these names in the posted XML document to identify the existing rows to delete.                                                                    |
| `transform = "URL"`                 | Relative or absolute URL of the XSLT transformation to use to transform the document to be deleted into canonical ROWSET/ROW format.                                                                                                                     |
| `columns = "string"`                | Relative or absolute URL of the XSLT transformation to use to transform the document to be deleted into canonical ROWSET/ROW format.                                                                                                                     |
| `commit = "boolean"`                | If set to `yes` (default), invokes `COMMIT` on the current connection after a successful execution of the deletion. Valid values are `yes` and `no`.                                                                                                     |
| `commit-batch-size = "integer"`     | If a positive, nonzero `integer` is specified, then after each batch of `integer` deleted records, the processor issues a `COMMIT`. The default batch size is zero (0) if not specified, which means that the processor does not commit interim batches. |
| `date-format = "string"`            | Date format mask to use for interpreting date field values in XML being deleted. Valid values are those documented for the `java.text.SimpleDateFormat` class.                                                                                           |
| `error-param = "string"`            | Name of a page-private parameter that must be set to the string `Error` if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                      |

#### Examples

The following example specifies that the posted XML document is to be transformed with the `style.xsl` stylesheet and then deleted from the `departments` table. The `departments.department_id` column is the primary key for the deletion.

Deleting Rows

    <?xml version="1.0"?>
    <xsql:delete-request table="departments"       transform="style.xsl"
     connection="demo" key-columns="department_id" xmlns:xsql="urn:oracle-xsql"/>

### 33.4 \<xsql:dml\>

Element `<xsql:dml>` is described.

#### Purpose

Executes a DML or DDL statement or a PL/SQL block. Typically, you use this tag to include statements that would be executed or rolled back together.

This action requires a database connection provided as a `connection="connname"` attribute on the document element of the XSQL page in which it appears.

#### Usage Notes

You cannot set parameter values by binding them in the position of `OUT` variables with `<xsql:dml>`. Only `IN` parameters are supported for binding.

#### Syntax

The syntax for the action is as follows, where `DML_DDL_or_PLSQL` is a placeholder for a legal DML statement, DDL statement, or PL/SQL block:

    <xsql:dml>
      DML_DDL_or_PLSQL
    </xsql:dml>

#### Attributes

Table 33-4 lists the optional attributes that you can use on the` <xsql:dml>` action.

Table 33-4 Attributes for \<xsql:dml\>

| Attribute Name                | Description                                                                                                                                                                                               |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `commit = "boolean"`          | If set to `yes`, invokes commit on the current connection after a successful execution of the DML statement. Valid values are `yes` and `no` (default).                                                   |
| `bind-params = "string"`      | Ordered, space-delimited list of one or more XSQL parameter names. The values of these parameters are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement. |
| `error-param = "string"`      | Name of a page-private parameter that must be set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                     |
| `error-statement = "boolean"` | If set to `no`, suppresses the inclusion of the offending SQL statement in any `<xsql-error>` element generated. Valid values are `yes` (default) and `no`.                                               |

#### Examples

The following example inserts the user name stored in the `webuser` cookie into a `request_log` table. Using bind variables guards against SQL injection attacks.

Inserting a User Name into a Table

     <xsql:dml connection="demo" bind-params="webuser"
               xmlns:xsql="urn:oracle-xsql">
       BEGIN
         INSERT INTO request_log(page,userid)
           VALUES( 'somepage.xsql', ? );
         COMMIT;
       END;
     </xsql:dml>

### 33.5 \<xsql:if-param\>

Element `<xsql:if-param>` is described.

#### Purpose

Enables you to include elements and actions nested inside if a specified condition is true. If the condition is true, then all nested XML content and actions are included in the page. If the condition is false, then none of the nested XML content or actions is included (and thus none of the nested actions is executed).

Specify which parameter value is evaluated by supplying the required `name` attribute. Simple parameter names and array-parameter names are supported.

**Note:**

If the parameter being tested does not exist, the test evaluates to false.

#### Syntax

The syntax for the action is this, where `some_name` is the value of the `name` attribute and `test_condition` is exactly one of the conditions listed in Table 33-5:

    <xsql:if-param name="some_name" test_condition>
       element_or_action
    </xsql:if-param>

Any XML content or XSQL action elements can be nested inside an `<xsql:if-param>`, including other `<xsql:if-param>` elements.

#### Attributes

In addition to the required `name` attribute, you must choose exactly one of the attributes listed in Table 33-5 to indicate how the parameter value (or values, in the array case) is tested. As with other XSQL actions, the attributes of the `<xsql:if-param>` action can contain lexical substitution parameter expressions such as `{@paramName}`.

Table 33-5 Attributes for \<xsql:if-param\>

| Attribute Name                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `exists="yes_or_no"`                            | If set to `exists="yes"`, then this condition tests whether the named parameter exists and has a nonempty value. For an array-valued parameter, it tests whether the array-parameter exists and has at least one nonempty element.<br>If set to `exists="no"`, then this condition evaluates to true if the parameter does not exist, of if it exists but has an empty value. For an array-valued parameter, it evaluates to true if the parameter does not exist, or if all of the array elements are empty.                                                       |
| `equals="stringValue"`                          | This condition tests whether the named parameter equals the string value provided. By default the comparison is an exact string match. For a case-insensitive match, supply the additional `ignore-case="yes"` attribute as well.<br>For an array-valued parameter, the condition tests whether any element in the array has the indicated value.                                                                                                                                                                                                                   |
| `not-equals="stringValue"`                      | This condition tests whether the named parameter does not equal the string value provided. By default the comparison is an exact string match. For an array-valued parameter, the condition evaluates to true if none of the elements in the array has the indicated value.                                                                                                                                                                                                                                                                                         |
| `in-list = "comma-or-space-separated-list"`     | This condition tests whether the named parameter matches any of the strings in the provided list. By default the comparison is an exact string match. For a case-insensitive match, supply the additional `ignore-case="yes"` attribute as well.<br>The value of the `in-list` parameter is tokenized into an array with commas as the delimiter if commas are detected in the string. Otherwise, it uses a space as the delimiter. For an array-valued parameter, the condition tests whether any element in the array matches an element in the list.             |
| `not-in-list = "comma-or-space-separated-list"` | This tests whether the named parameter does not match any of the strings in the provided list. By default the comparison is an exact string match. For a case-insensitive match, supply the additional `ignore-case="yes"` attribute as well.<br>The value of the `not-in-list` parameter is tokenized into an array with commas as the delimiter if commas are in the string. Otherwise, the processor uses a space as the delimiter. For an array-valued parameter, the condition tests whether none of the elements in the array matches an element in the list. |

#### Examples

To test whether two different conditions are true, you can use nested `<xsql:if-param>` elements as shown in the following example.

Testing Conditions

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
    <!--
    | Set page parameter 'some_param' to value "some_value" if parameter 'a'
    | exists, and if parameter 'b' has a value equal to "X"
    +-->
      <xsql:if-param name="a" exists="yes">
        <xsql:if-param name="b" equals="X">
          <xsql:set-page-param name="some_param" value="some_value"/>
        </xsql:if-param>
      </xsql:if-param>
      <!-- ... -->
    </page>

### 33.6 \<xsql:include-owa\>

Element `<xsql:include-owa>` is described.

#### Purpose

Includes XML content generated by a database stored procedure. This action requires a database connection to be provided by supplying a `connection="connname" `attribute on the document element of the XSQL page in which it appears.

The stored procedure uses the standard OWA packages (`HTP` and `HTF`) to "print" the XML tags into the server-side page buffer. Afterwards, the XSQL pages processor fetches, parses, and includes the dynamically-produced XML content in the data page. The stored procedure must generate a well-formed XML page or an appropriate error is displayed.

#### Usage Notes

You can create a wrapper procedure that constructs XML elements with the HTP package. Your XSQL page can invoke the wrapper procedure by using `<xsql:include-owa>`.

#### Syntax

The syntax for the action is as follows, where `PL/SQL_block` is a PL/SQL Block invoking a procedure that uses the HTP or HTF packages:

    <xsql:include-owa>
       PL/SQL_block
    </xsql:include-owa>

#### Attributes

Table 33-6 lists the optional attributes supported by this action.

Table 33-6 Attributes for \<xsql:include-owa\>

| Attribute Name                | Description                                                                                                                                                                                               |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bind-params = "string"`      | Ordered, space-delimited list of one or more XSQL parameter names. The values of these parameters are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement. |
| `error-param = "string"`      | Name of a page-private parameter that must be set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                     |
| `error-statement = "boolean"` | If set to `no`, suppresses the inclusion of the offending SQL statement in any `<xsql-error>` element generated. Valid values are `yes` (default) and `no`.                                               |

#### Examples

Assume that you write a PL/SQL procedure called `UpdateStatus` that updates the status of a project. The procedure uses HTP to print an `<UpdateStatus>` datagram that contains the element `<Success/>` if no errors occur or one or more `<Error>` elements if errors occur.

The following example shows how you can invoke `UpdateStatus` from an XSQL page. The example uses SQL bind variable instead of lexical substitution to prevent the possibility of SQL injection attacks.

Including XML Content Created by a Stored Procedure

    <xsql:include-owa connection="demo"
                      bind-params="project status"
                      xmlns:xsql="urn:oracle-xsql">
      UpdateStatus( ?,? );
    </xsql:include-owa>

Assume that a user enters an invalid status number for a project into a web-based form. The form posts the input parameters to an XSQL page as shown in the following example. The XSQL processor returns this datagram, which an XSLT stylesheet could transform into an HTML error page:

    <UpdateStatus>
      <Error Field="status">Status must be 1, 2, 3, or 4</Error>
    </UpdateStatus>

### 33.7 \<xsql:include-param\>

Element `<xsql:include-param>` is described.

#### Purpose

Includes an XML representation of the name and value of a single parameter. This technique is useful if an associated XSLT stylesheet must refer to parameter values with XPath expressions.

#### Syntax

The syntax of the action is as follows, where `paramname` is the name of a parameter:

    <xsql:include-param name="paramname" />

The required `name` attribute supplies the name of the parameter whose value you want to include.

#### Attributes

The `name` attribute is required; there are no optional attributes.

#### Examples

The following example uses XPATH to get the value of a parameter and represent it in XML.

Including an XML Representation of a Parameter Value

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql"
                            xmlns:p="http://www.companysite.com/products">
      <xsql:set-page-param name="productid"
                           xpath="/p:Products/productid"/>
      <xsql:include-param name="productid"/>
    </page>

The XML fragment included in the datagram is:

    <productid>12345</productid>

You can use an array parameter name to indicate that the value is to be treated as an array, as shown in this example:

    <xsql:include-param name="productid[]"/>

The XML fragment reflects all of the array values, as shown in this example:

    <productid>
      <value>12345<value>
      <value>33455</value>
      <value>88199</value>
    </productid>

In this array-parameter name scenario, if `productid` is a single-valued parameter, then the fragment looks identical to a one-element array, as showd in this example:

    <productid>
      <value>12345<value>
    </productid>

### 33.8 \<xsql:include-posted-include-posted\>

Element `<xsql:dml>` is described.

#### Purpose

Includes the posted XML document in the XSQL page. If the user posts an HTML form instead of an XML document, then the XML included is similar to that included by the `<xsql:include-request-params>` action.

#### Syntax

The syntax of the action is:

    <xsql:include-posted-xml/>

#### Attributes

None.

#### Examples

The following example shows a sample XSQL page that includes a posted XML document.

Including Posted XML

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsql" href="somepage.xsql"?>
    <page connection="demo"
          xmlns:xsql="urn:oracle-xsql">
      <xsql:include-posted-xml/>
    </page>

### 33.9 \<xsql:include-request-params\>

Element `<xsql:include-request-params>` is described.

#### Purpose

Includes an XML representation of all parameters in the request in the datagram. The action element is replaced in the page at page-request time with a tree of XML elements that represents the parameters available to the request.

This technique is useful if an associated XSLT stylesheet must refer to request parameter values with XPath expressions.

#### Usage Notes

When processing pages through the XSQL servlet, the XML included takes the form shown in the following example.

Including Request Parameters

    <request>
      <parameters>
        <paramname>value1</paramname>
        <ParamName2>value2</ParamName2>
         ...
      </parameters>
      <session>
        <sessVarName>value1</sessVarName>
         ...
      </session>
      <cookies>
        <cookieName>value1</cookieName>
         ...
      </cookies>
    </request>

When you use the XSQL command-line utility or the `XSQLRequest` class, the XML takes the form shown in the following example.

Including Request Parameters

    <request>
      <parameters>
        <paramname>value1</paramname>
        <ParamName2>value2</ParamName2>
         ...
      </parameters>
    </request>

The technique enables you to distinguish request parameters from session parameters or cookies because its value is a child element of `<parameters>`, `<session>`, or `<cookies>`.

#### Syntax

The syntax of the action is:

    <xsql:include-request-params/>

#### Attributes

None.

#### Examples

The following example shows a sample XSQL page that includes all request parameters in the data page.

Including Request Parameters

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsql" href="cookie_condition.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
      <xsql:include-request-params/>
    </page>

The `cookie_condition.xsl` stylesheet chooses an output format based on whether the `siteuser` cookie is present. The following example shows a fragment of the stylesheet.

Testing for Conditions in a Stylesheet

    <xsl:choose>
      <xsl:when test="/page/request/cookies/siteuser">
      ...
      </xsl:when>
      <xsl:otherwise>
      ...
      </xsl:otherwise>
    </xsl:choose>

### 33.10 \<xsql:include-xml\>

Element `<xsql:include-xml>` is described.

#### Purpose

Includes the XML contents of a local, remote, or database-driven XML resource in your datagram. You can specify the resource by URL or SQL statement. The server can deliver a resource that is a static XML file or dynamically created XML from a programmatic resource such as a servlet or common gateway interface (CGI) program.

#### Syntax

The syntax for this action is as follows, where `URL` is a relative URL or an absolute, HTTP-based URL to retrieve XML from another web site:

    <xsql:include-xml href="URL"/>

Alternatively, you can use this syntax, where `SQL_statement` is a SQL `SELECT` statement selecting a single row containing a single `CLOB` or `VARCHAR2` column value:

    <xsql:include-xml>
      SQL_statement
    </xsql:include-xml>

The `href` attribute and SQL statement are mutually exclusive. If you provide one, then the other is not allowed.

#### Attributes

Table 33-7 lists the attributes supported by this action. Required attributes are in bold.

Table 33-7 Attributes for \<xsql:include-xml\>

| Attribute Name           | Description                                                                                                                                                                                           |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `href="URL"`             | The absolute, relative, or parameterized URL of the XML resource to be included. The resource can be a static file dynamic source.                                                                    |
| `bind-params = "string"` | Ordered, space-delimited list of one or more XSQL parameter names. The values for these names are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement. |
| `error-param = "string"` | Name of a page-private parameter that must be set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                 |

#### Examples

The following example includes an XML document retrieved by a database query. The XML content is a `CLOB`-valued member field of a user-defined type. The XML included must come from a `VARCHAR2` or `CLOB` column, not an `XMLType`.

Including an XML Document

    <?xml version="1.0"?>
    <xsql:include-xml bind-params="id" connection="demo"
                       xmlns:xsql="urn:oracle-xsql">
      SELECT x.document.contents doc FROM xmldoc x
      WHERE x.docid = ?
    </xsql:include-xml>

### 33.11 \<xsql:include-xsql\>

Element `<xsql:include-xsql>` is described.

#### Purpose

Includes the XML output of one XSQL page in another page. You can create a page that assembles the contents­—optionally transformed—from other XSQL pages.

#### Usage Notes

If the aggregated page contains an `<?xml-stylesheet?>` processing instruction, then this stylesheet is applied before the result is aggregated. Thus, you can use `<xsql:include-xsql>` to chain XSLT stylesheets.

When one XSQL page aggregates another page by using `<xsql:include-xsql>`, all request-level parameters are visible to the nested page. For pages processed by the XSQL Servlet, the visible data includes session-level parameters and cookies. None of the page-private parameters of the aggregating page are visible to the nested page.

#### Syntax

The syntax for this action is as follows, where `XSQL_page` is a relative or absolute URL of an XSQL page to be included:

    <xsql:include-xsql href="XSQL_page"/>

#### Attributes

Table 33-8 lists the attributes supported by this action. Required attributes are in bold; all others are optional.

Table 33-8 Attributes for \<xsql:include-xsql\>

| Attribute Name           | Description                                                                                                                                                                                                                                                                                  |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `href="string"`          | Relative or absolute URL of XSQL page to be included.                                                                                                                                                                                                                                        |
| `error-param = "string"` | Name of a page-private parameter that must be set to the string `Error` if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                                                          |
| `reparse = "boolean"`    | Indicates whether output of the included XSQL page must be reparsed before it is included. Valid values are `no` (default) and `yes`.<br>This attribute is useful if the included XSQL page selects the text of an XML document fragment that the including page wants to treat as elements. |

#### Examples

The following example displays an XSQL page that lists discussion forum categories.

Categories.xsql

    <?xml version="1.0"?>
    <xsql:query connection="demo" xmlns:xsql="urn:oracle-xsql">
      SELECT name
      FROM categories
      ORDER BY name
    </xsql:query>

The following example shows how you can include the results of the page in the previous Categories.xsql example into a page that lists the ten most recent topics in the current forum.

TopTenTopics.xsql

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <top-ten-topics connection="demo" xmlns:xsql="urn:oracle-xsql">
      <topics>
        <xsql:query max-rows="10">
          SELECT subject
          FROM topics
          ORDER BY last_modified DESC
        </xsql:query>
      </topics>
      <categories>
        <xsql:include-xsql href="Categories.xsql"/>
      </categories>
    </top-ten-topics>

You can also use `<xsql:include-xsql>` to apply an XSLT stylesheet to an included page. Assume that you write this XSLT stylesheets:

- `cats-as-html.xsl`, which renders the topics in HTML

- `cats-as-wml.xsl`, which renders the topics in WML

One approach for catering to two different types of devices is to create different XSQL pages for each device. The following example shows an XSQL page that aggregates `Categories.xsql` and applies the `cats-as-html.xsl` stylesheet.

HTMLCategories.xsql

    <?xml version="1.0"?>
    <!-- HTMLCategories.xsql -->
    <?xml-stylesheet type="text/xsl" href="cats-as-html.xsl"?>
    <xsql:include-xsql href="Categories.xsql" xmlns:xsql="urn:oracle-xsql"/>

The following example shows an XSQL page that aggregates `Categories.xsql` and applies the `cats-as-html.xsl` stylesheet for delivering to wireless devices.

WMLCategories.xsql

    <?xml version="1.0"?>
    <!-- WMLCategories.xsql -->
    <?xml-stylesheet type="text/xsl" href="cats-as-wml.xsl"?>
    <xsql:include-xsql href="Categories.xsql" xmlns:xsql="urn:oracle-xsql"/>

### 33.12 \<xsql:insert-param\>

Element `<xsql:insert-param>` is described.

#### Purpose

Inserts the value of a parameter into a table or view. Use this tag when the client is posting a well-formed XML document as text in an HTTP parameter or individual HTML form field.

By combining the [XML SQL Utility (XSU)](glossary.md) with XSLT, you can transform XML into the canonical format expected by a given table. Afterward, you can use XSU to insert the resulting canonical XML. For a specified database table, the canonical XML form is given by one row of XML output from a `SELECT *` query against the table.

#### Syntax

The syntax for this action is as follows, where `table_or_view_name` is a relative or absolute URL of an XSQL page to be included:

    <xsql:insert-param table="table_or_view_name" name="string"/>

#### Attributes

Table 33-9 lists the optional attributes that you can use on the` <xsql:insert-param>` action.

Table 33-9 Attributes for \<xsql:insert-param\>

| Attribute Name                  | Description                                                                                                                                                                                                                                                               |
|:--------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name="string"`                 | Name of the parameter whose value contains XML to be inserted.                                                                                                                                                                                                            |
| `table="string"`                | Name of the table, view, or synonym to use for inserting the XML data.                                                                                                                                                                                                    |
| `transform = "URL"`             | Relative or absolute URL of the XSLT transformation to use to transform the document to be inserted into canonical ROWSET/ROW format.                                                                                                                                     |
| `columns = "string"`            | Space-delimited or comma-delimited list of one or more column names whose values are inserted. If supplied, then only these columns are inserted. If not supplied, all columns are inserted, with NULL values for columns whose values do not appear in the XML document. |
| `commit = "boolean"`            | If set to `yes`, invokes commit on the current connection after a successful execution of the insert. Valid values are `yes` (default) and `no`.                                                                                                                          |
| `commit-batch-size = "integer"` | If a positive, nonzero number `integer` is specified, then after each batch of `integer` inserted records, the XSQL processor issues a `COMMIT`. Default batch size is zero (`0`), which instructs the processor not to commit interim batches.                           |
| `date-format = "string"`        | Date format mask to use for interpreting date field values in XML being inserted. Valid values are those for the `java.text.SimpleDateFormat` class.                                                                                                                      |
| `error-param = "string"`        | Name of a page-private parameter that must be set to `Error` if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                                                  |

#### Examples

The following example parses and transforms the contents of the HTML form parameter `xmlfield` for database insert.

Inserting XML Contained in an HTML Form Parameter

    <?xml version="1.0"?>
    <xsql:insert-param name="xmlfield" table="image_metadata_table"
    transform="field-to-rowset.xsl" connection="demo" xmlns:xsql="urn:oracle-xsql"/>

### 33.13 \<xsql:insert-request\>

Element `<xsql:insert-request>` is described.

#### Purpose

Accepts data posted from an XML document or HTML form and uses the [XML SQL Utility (XSU)](glossary.md) to insert the content of an XML document in canonical form into a target table or view.

If an HTML Form has been posted, then the posted XML document is materialized from HTTP request parameters, cookies, and session variables. The XML document has this form:

    <request>
    <parameters>
      <param1>value1</param1>
        :
      </paramN>valueN</paramN>
    </parameters>
      :
    </request>

By combining XSU with XSLT, you can transform XML into the canonical format expected by a given table. The XSQL engine uses XSU to insert the resulting canonical XML. For a specified database table, the canonical XML form is given by one row of XML output from a `SELECT *` query against the table.

#### Usage Notes

If you target a database view with an `INSERT`, then you can create `INSTEAD OF INSERT` triggers on the view to further automate the handling of the posted data. For example, an `INSTEAD OF INSERT` trigger on a view can use PL/SQL to check for the existence of a record and intelligently choose whether to do an `INSERT` or an `UPDATE` depending on the result.

#### Syntax

The syntax for this action is:

    <xsql:insert-request table="table"/>

#### Attributes

Table 33-10 lists the optional attributes that you can use on the` <xsql:insert-request>` action.

Table 33-10 Attributes for \<xsql:insert-request\>

| Attribute Name                  | Description                                                                                                                                                                                                                                                    |
|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table = "string"`              | Name of the table, view, or synonym to use for inserting the XML data.                                                                                                                                                                                         |
| `transform = "URL"`             | Relative or absolute URL of the XSLT transformation to use to transform the document to be inserted into canonical ROWSET/ROW format.                                                                                                                          |
| `columns = "string"`            | Relative or absolute URL of the XSLT transformation to use to transform the document to be inserted into canonical ROWSET/ROW format.                                                                                                                          |
| `commit = "boolean"`            | If set to `yes` (default), invokes `COMMIT` on the current connection after a successful execution of the insert. Valid values are `yes` and `no`.                                                                                                             |
| `commit-batch-size = "integer"` | If a positive, nonzero number `integer` is specified, then after each batch of integer inserted records, the processor issues a `COMMIT`. The default batch size is zero (0) if not specified, which means that the processor does not commit interim batches. |
| `date-format = "string"`        | Date format mask to use for interpreting date field values in XML being inserted. Valid values are those documented for the `java.text.SimpleDateFormat` class.                                                                                                |
| `error-param = "string"`        | Name of a page-private parameter that must be set to the string `Error` if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                            |

#### Examples

The following example parses and transforms the contents of the posted XML document or HTML Form for insert.

Inserting XML Received in a Parameter

    <?xml version="1.0"?>
    <xsql:insert-request
      table="purchase_order"
      transform="purchseorder-to-rowset.xsl"
      connection="demo"
      xmlns:xsql="urn:oracle-xsql"/>

### 33.14 \<xsql:query\>

Element `<xsql:query>` is described.

#### Purpose

Executes a SQL select statement and includes a canonical XML representation of the query result set in the data page. This action requires a database connection to be provided by supplying a `connection="``connname``"` attribute on the document element of the XSQL page in which it appears.

#### Syntax

The syntax for the action is:

    <xsql:query>
       SELECT_Statement
    </xsql:query>

Any legal SQL select statement is permissible as a substitution for the `SELECT_Statement` placeholder. If the select statement produces no rows, then you can provide a fallback query by including a nested `<xsql:no-rows-query>` element:

    <xsql:query>
      SELECT_Statement
      <xsql:no-rows-query>
        Fallback_SELECT_Statement
      </xsql:no-rows-query>
    </xsql:query>

An `<xsql:no-rows-query>` element can itself contain nested `<xsql:no-rows-query>` elements to any level of nesting. The options available on the `<xsql:no-rows-query>` are identical to those legal on the `<xsql:query>` action element.

#### Attributes

The optional attributes listed in Table 33-11 can be supplied to control various aspects of the data retrieved and the XML produced by the `<xsql:query>` action.

Table 33-11 Attributes for \<xsql:query\>

| Attribute Name                   | Description                                                                                                                                                                                                                                 |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bind-params = "string"`         | Ordered, space-delimited list of one or more XSQL parameter names. The values of these parameters are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement.                                   |
| `date-format = "string"`         | Date format mask to use for formatted date column and attribute values in the XML that is queried. Valid values are the same values legal for the `java.text.SimpleDateFormat `class.                                                       |
| `error-param = "string"`         | Name of a page-private parameter that must be set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                       |
| `error-statement = "boolean"`    | If set to `no`, suppresses the inclusion of the offending SQL statement in any `<xsql-error>` element generated. Valid values are `yes` (default) and `no`.                                                                                 |
| `fetch-size = "integer"`         | Number of records to fetch in each round trip to the database. If not set, the default value is used as specified by the `/XSQLConfig/processor/default-fetch-size` configuration setting in `XSQLConfig.xml`.                              |
| `id-attribute = "string"`        | XML attribute name to use instead of the default `num` for uniquely identifying each row in the result set. If the value is the empty string, then the row id attribute is suppressed.                                                      |
| `id-attribute-column = "string"` | Case-sensitive name of the column in the result set whose value must be used in each row as the value of the row id attribute. The default is to use the row count as the value of the row id attribute.                                    |
| `include-schema = "boolean"`     | If set to `yes`, includes an inline XML schema that describes the structure of the result set. Valid values are `yes` and `no` (default).                                                                                                   |
| `max-rows = "integer"`           | Maximum number of rows to fetch after optionally skipping the number of rows set by the `skip-rows` attribute. If not specified, the default is to fetch all rows.                                                                          |
| `null-indicator = "boolean"`     | Indicates whether to signal that a column's value is NULL by including the `NULL="Y"` attribute on the element for the column. By default, columns with NULL values are omitted from the output. Valid values are `yes` and `no` (default). |
| `row-element = "string"`         | XML element name to use instead of the default `<ROW>` for the `rowset` of query results. Set to the empty string to suppress generating a containing `<ROW>` element for each row in the result set.                                       |
| `rowset-element = "string"`      | XML element name to use instead of the default `<ROWSET>` for the `rowset` of query results. Set to the empty string to suppress generating a containing `<ROWSET>` element.                                                                |
| `skip-rows = "integer"`          | Number of rows to skip before fetching rows from the result set. Can be combined with `max-rows` for stateless paging through query results.                                                                                                |
| `tag-case = "string"`            | Valid values are `lower` and `upper`. If not specified, the default is to use the case of column names as specified in the query as corresponding XML element names.                                                                        |

#### Examples

The following example shows a simple XSQL page.

Hello World

    <?xml version="1.0"?>
    <xsql:query connection="xmlbook" xmlns:xsql="urn:oracle-xsql">
       SELECT 'Hello, World!' AS text     FROM DUAL</xsql:query>

If you save the previous example as `hello.xsql` and execute it in a browser, the XSQL page processor returns this XML:

    <?xml version = '1.0'?>
    <ROWSET>
       <ROW num="1">
          <TEXT>Hello, World!</TEXT>
       </ROW>
    </ROWSET>

By default, the XML produced by a query reflects the column structure of its result set, with element names matching the names of the columns. Columns in the result with this nested structure produce nested elements that reflect this structure:

- Object types

- Collection types

- CURSOR expressions

The result of a typical query containing different types of columns and returning one row might look like the following example.

Nested Structure Example

    <ROWSET>
      <ROW id="1">
        <VARCHARCOL>Value</VARCHARCOL>
        <NUMBERCOL>12345</NUMBERCOL>
        <DATECOL>12/10/2001 10:13:22</DATECOL>
        <OBJECTCOL>
           <ATTR1>Value</ATTR1>
           <ATTR2>Value</ATTR2>
        </OBJECTCOL>
        <COLLECTIONCOL>
           <COLLECTIONCOL_ITEM>
             <ATTR1>Value</ATTR1>
             <ATTR2>Value</ATTR2>
           </COLLECTIONCOL_ITEM>
           <COLLECTIONCOL_ITEM>
             <ATTR1>Value</ATTR1>
             <ATTR2>Value</ATTR2>
           </COLLECTIONCOL_ITEM>
        </COLLECTIONCOL>
        <CURSORCOL>
          <CURSORCOL_ROW>
            <COL1>Value1</COL1>
            <COL2>Value2</COL2>
          </CURSORCOR_ROW>
        </CURSORCOL>
      </ROW>
    </ROWSET>

A `<ROW>` element repeats for each row in the result set. Your query can use standard SQL column aliasing to rename the columns in the result, which effectively renames the XML elements that are produced. Column aliasing is required for columns whose names otherwise are illegal names for an XML element.

For example, an `<xsql:query>` action as shown in the following example produces an error because the default column name for the calculated expression is an illegal XML element name.

Query with Error

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <xsql:query connection="demo" xmlns:xsql="urn:oracle-xsql">
      SELECT TO_CHAR(hire_date,'DD-MON')
      FROM   employees
    </xsql:query>

You can fix the problem by using column aliasing as shown in the following example.

Query with Column Aliasing

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <xsql:query connection="demo" xmlns:xsql="urn:oracle-xsql">
      SELECT TO_CHAR(hire_date,'DD-MON') AS hiredate FROM   employees
    </xsql:query>

### 33.15 \<xsql:ref-cursor-function\>

Element `<xsql:ref-cursor-function>` is described.

#### Purpose

Executes an arbitrary stored function returning a `REF` `CURSOR` and includes the query result set in canonical XML format. This action requires a database connection to be provided by supplying a `connection="``connname``"` attribute on the document element of the XSQL page in which it appears.

Use this tag to invoke a stored procedure that determines what the query is and returns a cursor to the query. Used in this way, this tag also provides a weak level of security because it can hide the query from direct inspection.

#### Syntax

The syntax of the action is as follows, where `SCHEMA_NAME` represents an optional database schema name, `PACKAGE_NAME` represents an optional PL/SQL package name, and `FUNCTION_NAME` (required) specifies the name of a PL/SQL function:

    <xsql:ref-cursor-function>
      [SCHEMA_NAME.][PACKAGE_NAME.]FUNCTION_NAME(args);
    </xsql:ref-cursor-function>

#### Attributes

The optional attributes are the same as for the `<xsql:query>` action listed in Table 33-11 except that `fetch-size` is not available for `<xsql:ref-cursor-function>`.

#### Examples

By exploiting dynamic SQL in PL/SQL, a function can conditionally construct a dynamic query before a cursor handle to its result set is returned to the XSQL page processor. The return value of the function must be of type `REF` `CURSOR`. Consider the PL/SQL package shown in the following example.

DynCursor PL/SQL Package

    CREATE OR REPLACE PACKAGE DynCursor IS
      TYPE ref_cursor IS REF CURSOR;
      FUNCTION DynamicQuery(id NUMBER) RETURN ref_cursor;
    END;
    CREATE OR REPLACE PACKAGE BODY DynCursor IS
      FUNCTION DynamicQuery(id NUMBER) RETURN ref_cursor IS
        the_cursor ref_cursor;
      BEGIN
        IF id = 1 THEN -- Conditionally return a dynamic query as a REF CURSOR
          OPEN the_cursor  -- An employees Query
           FOR 'SELECT employee_id, email FROM employees';
        ELSE
          OPEN the_cursor  -- A departments Query
            FOR 'SELECT department_name, department_id FROM departments';
       END IF;
       RETURN the_cursor;
      END;
    END;

An `<xsql:ref-cursor-function>` can include the dynamic results of the `REF` `CURSOR` returned by this function as shown in the following example.

Executing a REF CURSOR Function

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <xsql:ref-cursor-function connection="demo" xmlns:xsql="urn:oracle-xsql">
      DynCursor.DynamicQuery(1);
    </xsql:ref-cursor-function>

### 33.16 \<xsql:set-cookie\>

Element `<xsql:set-cookie>` is described.

#### Purpose

Sets an HTTP cookie to a value. By default, the value remains for the lifetime of the current browser, but you can change its lifetime by supplying the optional `max-age` attribute. The value to be assigned to the cookie can be supplied by a combination of static text and other parameter values, or from the result of a SQL `SELECT` statement.

Because this feature is specific to the HTTP protocol, this action is effective only if the XSQL page in which it appears is processed by the XSQL servlet. If this action is encountered in an XSQL page processed by the XSQL command-line utility or the `XSQLRequest` programmatic application programming interface (API), then it does nothing.

#### Usage Notes

If you use the SQL statement option, then a single row is fetched from the result set and the parameter is assigned the value of the first column. This use requires a database connection to be provided by supplying a `connection="connname"` attribute on the document element of the XSQL page in which it appears.

If you must set several cookie values based on the results of a single SQL statement, then do not use the `name` attribute. Instead, you can use the `names` attribute and supply a space-or-comma-delimited list of one or more cookie names.

#### Syntax

The syntax for this action is as follows, where `paramname` is the name of a parameter:

    <xsql:set-cookie name="paramname" value="value"/>

Alternatively, you can use this syntax, where `SQL_statement` is a SQL `SELECT` statement and `paramname` is the name of a parameter:

    <xsql:set-cookie name="paramname">
      SQL_statement
    </xsql:set-cookie>

Either the `name` or the `names` attribute is required. The `value` attribute and the contained SQL statement are mutually exclusive. The number of columns in the select list must match the number of cookies being set or an error message results.

#### Attributes

Table 33-12 lists the attributes supported by this action. Attributes in bold are required; all others are optional.

Table 33-12 Attributes for \<xsql:set-cookie\>

| Attribute Name                   | Description                                                                                                                                                                                                                                                          |
|:---------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name = "string"`                | Name of the cookie whose value you want to set. You must use `name` or `names` but not both.                                                                                                                                                                         |
| `names = "string string ..."`    | Space-or-comma-delimited list of the cookie names whose values you want to set. You must use `name` or `names` but not both.                                                                                                                                         |
| `bind-params = "string"`         | Ordered, space-delimited list of one or more XSQL parameter names. Values are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement.                                                                                    |
| `domain = "string"`              | Domain in which cookie value is valid and readable. If `domain` is not set explicitly, it defaults to the fully qualified host name (for example, `server.biz.com`) of the document creating the cookie.                                                             |
| `error-param = "string"`         | Name of a page-private parameter that is set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                                     |
| `ignore-empty-value = "boolean"` | Indicates whether the cookie assignment is ignored if the value to which it is being assigned is an empty string.Valid values are `yes` and `no` (default).                                                                                                          |
| `immediate = "boolean"`          | Indicates whether the cookie assignment is immediately visible to the current page. Typically, cookies set in the current request are not visible until the browser sends them back to the server in a subsequent request.Valid values are `yes` and `no` (default). |
| `max-age = "integer"`            | Sets the maximum age of the cookie in seconds. Default is to set the cookie to expire when users current browser session terminates.                                                                                                                                 |
| `only-if-unset = "boolean"`      | Indicates whether the cookie assignment occurs only when the cookie currently does not exists.Valid values are `yes` and `no` (default).                                                                                                                             |
| `path = "string"`                | Relative URL path within domain in which cookie value is valid and readable. If path is not set explicitly, then it defaults to the URL path of the document creating the cookie.                                                                                    |
| `value = "string"`               | Sets the value to assign to the cookie.                                                                                                                                                                                                                              |

#### Examples

The following example sets the HTTP cookie to the value of the parameter named `choice`.

Setting a Cookie to a Parameter Value

    <?xml version="1.0"?>
    <xsql:set-cookie name="last_selection"
                     value="{@choice}" xmlns:xsql="urn:oracle-xsql"/>

Table 33-5 sets the HTTP cookie to a value selected from the database.

Setting a Cookie to a Database-Generated Value

    <?xml version="1.0"?>
    <xsql:set-cookie name="shopping_cart_id" bind-params="user"
                     connection="demo"       xmlns:xsql="urn:oracle-xsql">
     SELECT cartmgr.new_cart_id(UPPER(?)) FROM DUAL
    </xsql:set-cookie>

Table 33-6 sets three cookies based on the result of a single `SELECT` statement.

Setting Three Cookies

    <?xml version="1.0"?>
    <xsql:set-cookie names="paramname1 paramname2 paramname3"
                     connection="demo" xmlns:xsql="urn:oracle-xsql">
      SELECT expression_or_column1, expression_or_column2, expression_or_column3
      FROM table
      WHERE clause_identifying_a_single_row
    </xsql:set-cookie>

### 33.17 \<xsql:set-page-param\>

Element `<xsql:set-page-param>` is described.

#### Purpose

Sets a page-private parameter to a value. The value can be supplied by a combination of static text and other parameter values, or alternatively from the result of a SQL `SELECT` statement.

#### Usage Notes

If you use the SQL statement option, then the program fetches a single row from the result set and assigns the parameter the value of the first column. This usage requires a database connection to be provided by supplying a `connection="connname"` attribute on the document element of the XSQL page in which it appears.

As an alternative to providing the `value` attribute, or a SQL statement, you can supply the `xpath` attribute to set the page-level parameter to the value of an XPath expression. The XPath expression is evaluated against an XML document or HTML form that has been posted to the XSQL pages processor. The value of the `xpath` attribute can be any valid XPath expression, optionally built using XSQL parameters as part of the attribute value like any other XSQL action element.

After a page-private parameter is set, subsequent action handlers can use this value as a lexical parameter, for example `{@po_id}`. Alternatively, action handlers can use this value as a SQL bind parameter value; they can reference its name in the `bind-params` attribute of any action handler that supports SQL operations.

If you must set multiple session parameter values based on the results of a single SQL statement, instead of using the `name` attribute, then you can use the `names` attribute. You can supply a list, delimited by spaces or commas, of one or more session parameter names.

#### Syntax

The syntax for this action is as follows, where `paramname` is the name of a parameter and `value` is a value:

    <xsql:set-page-param name="paramname" value="value"/>

Alternatively, you can use this syntax, where `SQL_statement` is a SQL `SELECT` statement and `paramname` is the name of a parameter:

    <xsql:set-page-param nname="paramname">
      SQL_statement
    </xsql:set-page-param>

Alternatively, you can use this syntax, where `paramname` is the name of a parameter and where `expression` is an XPath expression:

    <xsql:set-page-param name="paramname" xpath="expression"/>

Either the `name` or the `names` attribute is required. The `value` attribute and the contained SQL statement are mutually exclusive.

#### Attributes

Table 33-13 lists the attributes supported by this action. Attributes in bold are required; all others are optional.

Table 33-13 Attributes for \<xsql:set-page-param\>

| Attribute Name                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name = "string"`                 | Name of the page-private parameter whose value you want to set.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `names = "string string ..."`     | Space-or-comma-delimited list of the page parameter names whose values you want to set. Either use the `name` or the `names` attribute, but not both.                                                                                                                                                                                                                                                                                                                                                  |
| `bind-params = "string"`          | Ordered, space-delimited list of one or more XSQL parameter names. The values of these parameters are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement.                                                                                                                                                                                                                                                                                              |
| `error-param = "string"`          | Name of a page-private parameter that must be set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                                                                                                                                                                                                                                                                  |
| `ignore-empty-value = "boolean"`  | Indicates whether the page-level parameter assignment is ignored if the value to which it is being assigned is an empty string.Valid values are `yes` and `no` (default).                                                                                                                                                                                                                                                                                                                              |
| `quote-array-values = "boolean"`  | If the parameter name is a simple-valued parameter name (for example, `myparam`) and if `treat-list-as-array="yes"` is specified, then specifying `quote-array-values="yes"` surrounds each string token with single quotation marks before separating the values with commas. Valid values are `yes` and `no` (default).                                                                                                                                                                              |
| `treat-list-as-array = "boolean"` | Indicates whether the string-value assigned to the parameter is tokenized into an array of separate values before assignment. If any comma is present in the string, then the comma is used for separating tokens. Otherwise, spaces are used.Valid values are `yes` and `no`. The default value is `yes` if the parameter name being set is an array parameter name (for example, `myparam[]`), and default is `no` if the parameter name being set is a simple-valued parameter name like `myparam`. |
| `value = "string"`                | Sets the value to assign to the parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `xpath = "XPathExpression"`       | Sets the value of the parameter to an XPath expression evaluated against an XML document or HTML form that has been posted to the XSQL pages processor.                                                                                                                                                                                                                                                                                                                                                |

#### Examples

The following example sets multiple parameter values based on the results of a single SQL statement.

Setting Multiple Page Parameters

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <xsql:set-page-param names="paramname1 paramname2 paramname3"
                         connection="demo" xmlns:xsql="urn:oracle-xsql>
      SELECT expression_or_column1, expression_or_column2, expression_or_column3
      FROM table
      WHERE clause_identifying_a_single_row
    </xsql:set-page-param>

The following example sets the page-level parameter to a value selected from database and then uses it as the value of an `xsql:query` attribute.

Setting a Parameter to a Database-Generated Value

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
      <xsql:set-page-param name="max-rows-pref">
         SELECT max_rows
         FROM user_profile
         WHERE userid = {@userid}
      </xsql:set-page-param>
      <xsql:query max-rows="{@max-rows-pref}">
        SELECT title, url
        FROM newsstory
        ORDER BY date_entered DESC
      </xsql:query>
    </page>

### 33.18 \<xsql:set-session-param\>

Element `<xsql:set-session-param>` is described.

#### Purpose

Sets an HTTP session-level parameter to a value. The value of the session-level parameter remains for the lifetime HTTP session of the current browser user. The web server controls the session. The value can be supplied by a combination of static text and other parameter values, or from the result of a SQL `SELECT` statement.

Because this feature is specific to Java servlets, this action is effective only if the XSQL page in which it appears is processed by the XSQL servlet. If this action occurs in an XSQL page processed by the XSQL command-line utility or the `XSQLRequest` programmatic API, it does nothing.

#### Usage Notes

If you use the SQL statement option, the XSQL processor fetches a single row from the result set and assigns the parameter the value of the first column. This use requires a database connection to be provided by supplying a `connection="connname"` attribute on the document element of the XSQL page in which it appears.

To set several session parameter values based on the results of a single SQL statement, do not use the `name` attribute. Instead, use the `names` attribute and supply a space-or-comma-delimited list of one or more session parameter names.

#### Syntax

The syntax for this action is as follows, where `paramname` is the name of a parameter and where `value` is a value:

    <xsql:set-session-param name="paramname" value="value"/>

Alternatively, you can use this syntax, where `SQL_statement` is a SQL `SELECT` statement and `paramname` is the name of a parameter:

    <xsql:set-session-param name="paramname">
      SQL_statement
    </xsql:set-session-param>

Either the `name` or the `names` attribute is required. The `value` attribute and the contained SQL statement are mutually exclusive.

#### Attributes

Table 33-14 lists the optional attributes supported by this action. Attributes in bold are required; all others are optional.

Table 33-14 Attributes for \<xsql:set-session-param\>

| Attribute Name                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name = "string"`                 | Name of the session-level variable whose value you want to set. Either use the `name` or the `names` attribute, but not both.                                                                                                                                                                                                                                                                                                                                                                          |
| `names = "string string ..."`     | Space-or-comma-delimited list of the session parameter names whose values you want to set. Either use the `name` or the `names` attribute, but not both.                                                                                                                                                                                                                                                                                                                                               |
| `bind-params = "string"`          | Ordered, space-delimited list of one or more XSQL parameter names. The parameter values are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement.                                                                                                                                                                                                                                                                                                        |
| `error-param = "string"`          | Name of a page-private parameter that is set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                                                                                                                                                                                                                                                                       |
| `ignore-empty-value = "boolean"`  | Indicates whether the session-level parameter assignment is ignored if the value to which it is being assigned is an empty string. Valid values are `yes` and `no` (default).                                                                                                                                                                                                                                                                                                                          |
| `only-if-unset = "boolean"`       | Indicates whether the session variable assignment occurs only when the session variable currently does not exists.Valid values are `yes` and `no` (default).                                                                                                                                                                                                                                                                                                                                           |
| `quote-array-values = "boolean"`  | If the parameter name is a simple-valued parameter name (for example, `myparam`) and if `treat-list-as-array="yes"` is specified, then specifying `quote-array-values="yes"` surrounds each string token with single quotation marks before separating the values with commas. Valid values are `yes` and `no` (default).                                                                                                                                                                              |
| `treat-list-as-array = "boolean"` | Indicates whether the string-value assigned to the parameter is tokenized into an array of separate values before assignment. If any comma is present in the string, then the comma is used for separating tokens. Otherwise, spaces are used.Valid values are `yes` and `no`. The default value is `yes` if the parameter name being set is an array parameter name (for example, `myparam[]`), and default is `no` if the parameter name being set is a simple-valued parameter name like `myparam`. |
| `value = "string"`                | Sets the value to assign to the parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

#### Examples

The following example sets multiple session parameter values based on the results of a single `SELECT` statement.

Setting Session Parameters

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
      <xsql:set-session-param names="paramname1 paramname2 paramname3">
        SELECT expression_or_column1, expression_or_column2, expression_or_column3
        FROM   table
        WHERE  clause_identifying_a_single_row
      </xsql:set-session-param>
      <!-- ... -->
    </page>

### 33.19 \<xsql:set-stylesheet-param\>

Element `<xsql:set-stylesheet-param>` is described.

#### Purpose

Sets a top-level XSLT stylesheet parameter to a value. The value can be supplied by a combination of static text and other parameter values, or from the result of a SQL `SELECT` statement. The stylesheet parameter is set on any stylesheet used during the processing of the current page.

#### Usage Notes

If you use the SQL statement option, then a single row is fetched from the result set and the parameter is assigned the value of the first column. This use requires a database connection to be provided by supplying a `connection="connname"` attribute on the document element of the XSQL page in which it appears.

To set several stylesheet parameter values based on the results of a single SQL statement, do not use the `name` attribute. You can use the `names` attribute and supply a space-or-comma-delimited list of one or more stylesheet parameter names.

#### Syntax

The syntax for this action is as follows, where `paramname` is the name of a parameter and where `value` is a value:

    <xsql:set-stylesheet-param name="paramname" value="value"/>

Alternatively, you can use this syntax, where `SQL_statement` is a SQL `SELECT` statement and `paramname` is the name of a parameter:

    <xsql:set-stylesheet-param name="paramname">
      SQL_statement
    </xsql:set-stylesheet-param>

Either the `name` or the `names` attribute is required. The `value` attribute and the contained SQL statement are mutually exclusive.

#### Attributes

Table 33-15 lists the optional attributes supported by this action. Attributes in bold are required; all others are optional.

Table 33-15 Attributes for \<xsql:set-stylesheet-param\>

| Attribute Name                   | Description                                                                                                                                                                                 |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name = "string"`                | Name of the top-level stylesheet parameter whose value you want to set.                                                                                                                     |
| `names = "string string ..."`    | Space-or-comma-delimited list of the top-level stylesheet parameter names whose values you want to set. Use the `name` or the `names` attribute, but not both.                              |
| `bind-params = "string"`         | Ordered, space-delimited list of one or more XSQL parameter names. Parameter values are used to bind to the JDBC bind variable in the appropriate sequential position in the SQL statement. |
| `error-param = "string"`         | Name of a page-private parameter that must be set to the string '`Error`' if a nonfatal error occurs while processing this action. Valid value is any parameter name.                       |
| `ignore-empty-value = "boolean"` | Indicates whether the stylesheet parameter assignment is to be ignored if the value to which it is being assigned is an empty string. Valid values are `yes` and `no` (default).            |
| `value = "string"`               | Sets the value to assign to the parameter.                                                                                                                                                  |

#### Examples

The following example associates a stylesheet and uses the `<xsql:set-stylesheet-param>` action element to assign the value of the XSQL page parameter named `p_table` to the XSLT top-level stylesheet parameter named `table`.

Setting a Stylesheet Parameter

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="style.xsl"?>
    <page connname="xmlbook" connection="{@p_connname}">
      <xsql:query null-indicator="yes" xmlns:xsql="urn:oracle-xsql">
      <![CDATA[
        SELECT *
        FROM {@p_table}
        WHERE rownum < 2
      ]>
      </xsql:query>
      <xsql:set-stylesheet-param name="table" value="{@p_table}"
                                 xmlns:xsql="urn:oracle-xsql" />
    </page>

### 33.20 \<xsql:update-request\>

Element `<xsql:update-request>` is described.

#### Purpose

Accepts data posted from an XML document or HTML form and uses the [XML SQL Utility (XSU)](glossary.md) to update the content of an XML document in canonical form from a target table or view.

By combining XSU with XSLT, you can transform XML into the canonical format expected by a given table. Afterward, you can use XSU to update the resulting canonical XML. For a specified database table, the canonical XML form is given by one row of XML output from a `SELECT *` query against the table.

#### Syntax

The syntax for this action is:

    <xsql:update-request table="table_name"/>

#### Attributes

Table 33-3 lists the attributes that you can use on the` <xsql:update-request>` action. Required attributes are in bold.

Table 33-16 Attributes for \<xsql:update-request\>

| Attribute Name                      | Description                                                                                                                                                                                                                                                |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table = "string"`                  | Name of the table, view, or synonym to use for updating the XML data.                                                                                                                                                                                      |
| `key_columns = "string string ..."` | Space-delimited or comma-delimited list of one or more column names. The processor uses the values of these names in the posted XML document to identify the existing rows to update.                                                                      |
| `transform = "URL"`                 | Relative or absolute URL of the XSLT transformation to use to transform the document to be updated into canonical ROWSET/ROW format.                                                                                                                       |
| `columns = "string"`                | Relative or absolute URL of the XSLT transformation to use to transform the document to be updated into canonical ROWSET/ROW format.                                                                                                                       |
| `commit = "boolean"`                | If set to `yes` (default), invokes `COMMIT` on the current connection after a successful execution of the update. Valid values are `yes` and `no`.                                                                                                         |
| `commit-batch-size = "integer"`     | If a positive, nonzero `integer` is specified, then after each batch of `integer` updated records, the processor issues a `COMMIT`. The default batch size is zero (`0`) if not specified, which means that the processor does not commit interim batches. |
| `date-format = "string"`            | Date format mask to use for interpreting date field values in XML being updated. Valid values are those for the `java.text.SimpleDateFormat` class.                                                                                                        |
| `error-param = "string"`            | Name of a page-private parameter that must be set to `Error` if a nonfatal error occurs while processing this action. Valid value is any parameter name.                                                                                                   |

#### Examples

The following example parses and transforms the contents of the posted XML document or HTML Form for update.

Updating XML Received in a Parameter

    <?xml version="1.0"?>
    <xsql:update-request table="purchase_order"   key-columns="department_id"
                         connection="demo"        transform="doc-to-departments.xsl"
     xmlns:xsql="urn:oracle-xsql/>
