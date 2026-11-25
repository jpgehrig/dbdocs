An explanation is given of how to use advanced features of the XSQL pages publishing framework.

**Related Topics**

- [Using the XSQL Pages Publishing Framework](using-XSQL-pages-publishing-framework.md)

**See Also:**

[Using the XSQL Pages Publishing Framework](using-XSQL-pages-publishing-framework.md) for information about basic features

### 25.1 Customizing the XSQL Configuration File Name

By default, the XSQL pages framework expects the configuration file to be named `XSQLConfig.xml`. When moving between development, test, and production environments, you can switch among different versions of a configuration file. To override the name of the configuration file read by the XSQL page processor, set system property `xsql.config`.

The simplest technique is to specify a Java Virtual Machine (JVM) command-line flag such as `-Dxsql.config=``MyConfigFile.xml `by defining a servlet initialization parameter named `xsql.config`. Add an `<init-param>` element to your `web.xml` file as part of the `<servlet>` tag that defines the XSQL Servlet:

    <servlet>
      <servlet-name>XSQL</servlet-name>
      <servlet-class>oracle.xml.xsql.XSQLServlet</servlet-class>
      <init-param>
        <param-name>xsql.config</param-name>
        <param-value>MyConfigFile.xml</param-value>
        <description>
           Please Use MyConfigFile.xml instead of XSQLConfig.xml
        </description>
      </init-param>
    </servlet>

The servlet initialization parameter is applicable only to the servlet-based use of the XSQL engine. When using the `XSQLCommandLine` or `XSQLRequest` programmatic interfaces, use the `System` parameter instead.

**Note:**

The configuration file is always read from the `CLASSPATH`. For example, if you specify a custom configuration parameter file named `MyConfigFile.xml`, then the XSQL processor attempts to read the XML file as a resource from the `CLASSPATH`. In a servlet environment like Java Platform, Enterprise Edition (Java EE), you must place your `MyConfigFile.xml` in the `.\WEB-INF\classes` directory (or another top-level directory on the `CLASSPATH`). If both the servlet initialization parameter and the `System` parameter are provided, then the servlet initialization parameter value is used.

### 25.2 Controlling How Stylesheets Are Processed

Topics here include an overview of client stylesheets, controlling content type, assigning stylesheets dynamically, processing stylesheets in a client, and providing multiple stylesheets.

#### 25.2.1 Overriding Client Stylesheets

If the current XSQL page being requested allows it, you can supply an Extensible Stylesheet Language Transformation (XSLT) stylesheet URL in the request. This technique lets you override the default stylesheet or apply a stylesheet where none is applied by default.

The client-initiated stylesheet URL is provided by supplying the `xml-stylesheet` parameter as part of the request. The valid values for this parameter are:

- Any relative URL interpreted relative to the XSQL page being processed.

- Any absolute URL that uses the HTTP protocol scheme, provided it references a trusted host as defined in the XSQL configuration file.

- The literal value `none`. Setting `xml-stylesheet=none` is useful during development to temporarily "short-circuit" the XSLT stylesheet processing to determine what XML datagram your stylesheet is seeing. Use this technique to determine why a stylesheet is not producing expected results.

You can allow client override of stylesheets for an XSQL page in these ways:

- Setting the `allow-client-style` configuration parameter to `no` in the XSQL configuration file

- Explicitly including an `allow-client-style="no"` attribute on the document element of any XSQL page

If client-override of stylesheets has been globally disabled by default in the XSQL configuration file, any page can still enable client-override explicitly by including an `allow-client-style="yes"` attribute on the document element of that page.

#### 25.2.2 Controlling the Content Type of the Returned Document

Setting the content type of the data you serve lets a requesting client correctly interpret the data you return. If your stylesheet uses an `<xsl:output>` element then the XSQL processor infers the media type and the encoding of the returned document from the `media-type` and `encoding` attributes of `<xsl:output>`.

The stylesheet in Example 25-1 uses the `media-type="application/vnd.ms-excel"` attribute on `<xsl:output>`. This instruction transforms the results of an XSQL page containing a standard query of the `hr.employees` table into Microsoft Excel format.

The following XSQL page uses the stylesheet in Example 25-1:

    <?xml version="1.0"?>
    <?xml-stylesheet href="empToExcel.xsl" type="text/xsl"?>
    <xsql:query connection="hr" xmlns:xsql="urn:oracle-xsql">
      SELECT   employee_id, email, salary
      FROM     employees
      ORDER BY salary DESC
    </xsql:query>

Example 25-1 empToExcel.xsl

    <?xml version="1.0"?>
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
      <xsl:output method="html" media-type="application/vnd.ms-excel"/>
      <xsl:template match="/">
       <html>
         <table>
           <tr><th>Id</th><th>Email</th><th>Salary</th></tr>
           <xsl:for-each select="ROWSET/ROW">
             <tr>
               <td><xsl:value-of select="EMPLOYEE_ID"/></td>
               <td><xsl:value-of select="EMAIL"/></td>
               <td><xsl:value-of select="SALARY"/></td>
             </tr>
           </xsl:for-each>
         </table>
       </html>
      </xsl:template>
    </xsl:stylesheet>

#### 25.2.3 Assigning the Stylesheet Dynamically

If you include an `<?xml-stylesheet?>` instruction at the top of your `.xsql` file, then the XSQL page processor considers it for use in transforming the resulting XML datagram.

Consider the `emp_test.xsql` page shown in Example 25-2.

The page in Example 25-2 uses the `emp.xsl` stylesheet to transform the results of the `employees` query in the server tier before returning the response to the requester. The processor accesses the stylesheet by the URL provided in the `href` pseudo-attribute on the `<?xml-stylesheet?>` processing instruction.

For example, to change XSLT stylesheets dynamically based on arguments passed to the XSQL servlet, you can use a lexical parameter in the `href` attribute of your `xml-stylesheet` processing instruction, as shown in this sample instruction:

    <?xml-stylesheet type="text/xsl" href="{@filename}.xsl"?>

You can then pass the value of the `filename` parameter as part of the URL request to XSQL servlet.

You can also use the [\<xsql:set-page-param\>](XSQL-pages-reference.md) element in an XSQL page to set the value of the parameter based on a SQL query. For example, the XSQL page in Example 25-3 selects the name of the stylesheet to use from a table by assigning the value of a page-private parameter.

Example 25-2 emp_test.xsql

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="emp.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
      <xsql:query>
        SELECT   *
        FROM     employees
        ORDER BY salary DESC
      </xsql:query>
    </page>

Example 25-3 emp_test_dynamic.xsql

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" href="{@sheet}.xsl"?>
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
      <xsql:set-page-param bind-params="UserCookie" name="sheet">
        SELECT stylesheet_name
        FROM   user_prefs
        WHERE  username = ?
      </xsql:set-page-param>
      <xsql:query>
        SELECT   *
        FROM     employees
        ORDER BY salary DESC
      </xsql:query>
    </page>

#### 25.2.4 Processing XSLT Stylesheets in the Client

How to process XSLT stylesheets in the client is described.

Some browsers support processing XSLT stylesheets in the client. These browsers recognize the stylesheet to be processed for an XML document by using an `<?xml-stylesheet?>` processing instruction. The use of `<?xml-stylesheet?>` for this purpose is part of the W3C Recommendation from June 29, 1999 entitled "Associating Stylesheets with XML Documents, Version 1.0".

By default, the XSQL pages processor performs XSLT transformations in the server. By adding `client="yes"` to your `<?xml-stylesheet?>` processing instruction in your XSQL page, however, you can defer XSLT processing to the client. The processor serves the XML datagram "raw" with the current `<?xml-stylesheet?>` element at the top of the document.

#### 25.2.5 Providing Multiple Stylesheets

You can include multiple `<?xml-stylesheet?>` processing instructions at the top of an XSQL page.

The instructions can contain an optional `media` pseudo-attribute. If specified, the processor case-insensitively compares the value of the `media` pseudo-attribute with the value of the User-Agent string in the HTTP header. If the value of the `media` pseudo-attribute matches part of the User-Agent string, then the processor selects the current `<?xml-stylesheet?>` instruction for use. Otherwise, the processor ignores the instruction and continues looking. The processor uses the first matching processing instruction in document order. An instruction without a `media` pseudo-attribute matches all user agents.

Example 25-4 shows multiple processing instructions at the top of an XSQL file. The processor uses `doyouxml-lynx.xsl` for Lynx browsers, `doyouxml-ie.xsl` for Internet Explorer 5.0 or 5.5 browsers, and `doyouxml.xsl` for all others.

Table 25-1 summarizes the supported pseudo-attributes allowed on the `<?xml-stylesheet?>` processing instruction.

Table 25-1 Pseudo-Attributes for \<?xml-stylesheet ?\>

| Attribute Name          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type = "string"`       | Indicates the Multipurpose Internet Mail Extensions (MIME) type of the associated stylesheet. For XSLT stylesheets, this attribute must be set to the string `text/xsl`.<br>This attribute may be present or absent when using the `serializer` attribute, depending on whether an XSLT stylesheet must execute before invoking the serializer, or not.                                                                                                                                                                                                                                                                                                                                                                    |
| `href = "URL"`          | Indicates the relative or absolute URL to the XSLT stylesheet to be used. If an absolute URL is supplied that uses the `http` protocol scheme, the IP address of the resource must be a trusted host listed in the XSQL configuration file (by default, named `XSQLConfig.xml`).                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `media = "string"`      | Performs a case-insensitive match on the `User-Agent` string from the HTTP header sent by the requesting device. This attribute is optional. The current `<?xml-stylesheet?>` processing instruction is used only if the `User-Agent` string contains the value of the `media` attribute; otherwise it is ignored.                                                                                                                                                                                                                                                                                                                                                                                                         |
| `client = "boolean"`    | Defers the processing of the associated XSLT stylesheet to the client if set to `yes`. The raw XML datagram is sent to the client with the current `<?xml-stylesheet?>` instruction at the top of the document. The default if not specified is to perform the transformation in the server.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `serializer = "string"` | By default, the XSQL page processor uses:<br>• XML Document Object Model (DOM) serializer if no XSLT stylesheet is used<br>• XSLT processor serializer if an XSLT stylesheet is used<br>Specifying this pseudo-attribute indicates that a custom serializer implementation must be used instead.<br>Valid values are either the name of a custom serializer defined in the `<serializerdefs>` section of the XSQL configuration file or the string `java:fully.qualified.Classname`. If both an XSLT stylesheet and the serializer attribute are present, then the processor performs the XSLT transformation first, then invokes the custom serializer to render the final result to the `OutputStream` or `PrintWriter`. |

Example 25-4 Multiple \<?xml-stylesheet ?\> Processing Instructions

    <?xml version="1.0"?>
    <?xml-stylesheet type="text/xsl" media="lynx" href="doyouxml-lynx.xsl" ?>
    <?xml-stylesheet type="text/xsl" media="msie 5" href="doyouxml-ie.xsl" ?>
    <?xml-stylesheet type="text/xsl" href="doyouxml.xsl" ?>
    <page xmlns:xsql="urn:oracle-xsql" connection="demo">

### 25.3 Working with Array-Valued Parameters

Topics here include using array values for parameters, including page or session parameters and parameters in SQL or PL/SQL code

#### 25.3.1 Supplying Values for Array-Valued Parameters

Request parameters, session parameters, and page-private parameters can have arrays of strings as values. To treat to the value of a parameter as an array, add two empty square brackets to the end of its name.

For example, if an HTML form is posted with four occurrences of a input control named `productid`, then use the notation `productid[]` to refer to the array-valued `productid` parameter. If you refer to an array-valued parameter without using the array-brackets notation, then the XSQL processor uses the value of the first array entry.

**Note:**

The XSQL processor does not support use of numbers inside the array brackets. That is, you can refer to `productid` or `productid[]`, but not `productid[2]`.

Suppose that you refer to an array-valued parameter as a lexical substitution parameter inside an action handler attribute value or inside the content of an action handler element. The XSQL page processor converts its value to a comma-delimited list of non-null and nonempty strings in the order that they exist in the array. Example 25-5 shows an XSQL page with an array-valued parameter.

You can invoke the XSQL command-line utility to supply multiple values for the `productid` parameter in `Page.xsql`:

    xsql Page.xsql productid=111 productid=222 productid=333 productid=444

The preceding command sets the `productid[]` array-valued parameter to the value {"`111`","`222`","`333`","`444`"}. The XSQL page processor replaces the `{@productid[]}` expression in the query with the string "111,222,333,444".

You can also pass multivalued parameters programmatically through the `XSQLRequest` application programming interface (API), which accepts a `java.util.Dictionary` of named parameters. You can use a `Hashtable` and invoke its `put(name,value)` method to add `String`-valued parameters to the request. To add multivalued parameters, put a value of type `String[]` instead of type `String`.

**Note:**

Only request parameters, page-private parameters, and session parameters can use string arrays. The [\<xsql:set-stylesheet-param\>](XSQL-pages-reference.md) and [\<xsql:set-cookie\>](XSQL-pages-reference.md) actions support only working with parameters as simple string values. To refer to a multivalued parameter in your XSLT stylesheet, use [\<xsql:include-param\>](XSQL-pages-reference.md) to include the multivalued parameter into your XSQL datapage, then use an XPath expression in the stylesheet to refer to the values from the datapage.

Example 25-5 Using an Array-Valued Parameter in an XSQL Page

    <page xmlns:xsql="urn:oracle-xsql">
      <xsql:query>
        SELECT description
        FROM product
        WHERE productid in ( {@productid[]} )  /* Using lexical parameter */
      </xsql:query>
    </page>

#### 25.3.2 Setting Array-Valued Page or Session Parameters from Strings

You can set the value of a page-private parameter or a session parameter from strings.

You can set the value of a page-private parameter to a string-array value by using array brackets notation on the name:

    <!-- param name contains array brackets -->
    <xsql:set-page-param name="names[]" value="Tom Jane Joe"/>

You set the value similarly for session parameters, as shown in this example:

    <xsql:set-session-param name="dates[]" value="12-APR-1962 15-JUL-1968"/>

By default, when the name of the parameter uses array brackets, the XSQL processor treats the value as a space-or-comma-delimited list and tokenizes it.

The resulting string array value contains these separate tokens. In the preceding examples, parameter `names[]` is the string array {"`Tom`", "`Jane`", "`Joe`"} and parameter `dates[]` is the string array {"`12-APR-1962`", "`15-JUL-1968`"}.

To handle strings that contain spaces, the tokenization algorithm first checks the string for the presence of commas. If at least one comma is found in the string, then commas are used as the token delimiter. For example, this action sets the value of the `names[]` parameter to the string array {"`Tom Jones`", "`Jane York`"}:

    <!-- param name contains array brackets -->
    <xsql:set-page-param name="names[]" value="Tom Jones,Jane York"/>

By default, when you set a parameter whose name does not end with the array-brackets, then the string-tokenization does not occur. Thus, this action sets the parameter `names` to the literal string "`Tom Jones,Jane York`":

    <!-- param name does NOT contain array brackets -->
    <xsql:set-page-param name="names" value="Tom Jones,Jane York"/>

You can force the string to be tokenized by including the `treat-list-as-array="yes"` attribute on the [\<xsql:set-page-param\>](XSQL-pages-reference.md) or [\<xsql:set-session-param\>](XSQL-pages-reference.md) actions. When this attribute is set, the XSQL processor assigns a comma-delimited string of the tokenized values to the parameter. For example, this action sets the `names` parameter to the literal string "`Tom,Jane,Joe`":

    <!-- param name does NOT contain array brackets -->
    <xsql:set-page-param name="names" value="Tom Jane Joe"
                         treat-list-as-array="yes"/>

When you are setting the value of a simple string-valued parameter and you are tokenizing the value with `treat-list-as-array="yes"`, you can include the `quote-array-values="yes"` attribute to surround the comma-delimited values with single quotation marks. Thus, this action assigns the literal string value "`'Tom Jones','Jane York','Jimmy'`" to the `names` parameter:

    <!--  param name does NOT contain array brackets -->
    <xsql:set-page-param name="names" value="Tom Jones,Jane York,Jimmy"
                         treat-list-as-array="yes"
                         quote-array-values="yes"/>

#### 25.3.3 Binding Array-Valued Parameters in SQL and PL/SQL Statements

Where string-valued scalar bind variables are supported in an XSQL page, you can also bind array-valued parameters. Use the array parameter name, for example, `myparam[]`, in the list of parameter names that you supply for attribute `bind-params`. This technique lets you process array-valued parameters in SQL statements and PL/SQL procedures.

The XSQL processor binds array-valued parameters as a nested table object type named `XSQL_TABLE_OF_VARCHAR`. You must create this type in your current schema with this DDL statement:

    CREATE TYPE xsql_table_of_varchar AS TABLE OF VARCHAR2(2000);

Although the type must have the name `xsql_table_of_varchar`, you can change the dimension of the `VARCHAR2` string, if necessary. You must make the dimension long enough for any string value you expect to handle in your array-valued string parameters.

Consider the PL/SQL function shown in Example 25-6.

The XSQL page in Example 25-7 shows how to bind two array-valued parameters in a SQL statement that uses `testTableFunction`.

Executing the XSQL page in Example 25-7 generates this datagram:

    <page someNames="aa,bb,cc" someValues="11,22,33">
      <ROWSET>
        <ROW num="1">
          <EXAMPLE>aa=11:bb=22:cc=33</EXAMPLE>
        </ROW>
      </ROWSET>
    </page>

This technique shows that the XSQL processor bound the array-valued `someNames[]` and `someValues[]` parameters as table collection types. It iterated over the values and concatenated them to produce the "`aa=11:bb=22:cc=33`" string value as the return value of the PL/SQL function.

You can mix any number of regular parameters and array-valued parameters in your bind-params string. Use the array-bracket notation for the parameters to be bound as arrays.

**Note:**

If you run the page in Example 25-7 but you have not created the `XSQL_TABLE_OF_VARCHAR` type as showd earlier, then you receive an error such as:

    <page someNames="aa,bb,cc" someValues="11,22,33">
      <xsql-error code="17074" action="xsql:query">
        <statement>
         select testTableFunction(?,?) as example from dual
        </statement>
        <message>
          invalid name pattern: SCOTT.XSQL_TABLE_OF_VARCHAR
        </message>
      </xsql-error>
    </page>

Because the XSQL processor binds array parameters as nested table collection types, you can use the `TABLE()` operator with the `CAST()` operator in SQL to treat the nested table bind variable value as a table of values. You can then query this table. This technique is especially useful in subqueries. The page in Example 25-8 uses an array-valued parameter containing employee IDs to restrict the rows queried from `hr.employees`.

The XSQL page in Example 25-8 generates a datagram such as:

    <page>
      <ROWSET>
        <ROW num="1">
          <NAME>Alana Walsh</NAME>
          <SALARY>3100</SALARY>
        </ROW>
        <ROW num="2">
          <NAME>Kevin Feeny</NAME>
          <SALARY>3000</SALARY>
        </ROW>
      </ROWSET>
    </page>

Example 25-7 and Example 25-8 show how to use `bind-params` with [\<xsql:query\>](XSQL-pages-reference.md), but these techniques work for [\<xsql:dml\>](XSQL-pages-reference.md), [\<xsql:include-owa\>](XSQL-pages-reference.md), [\<xsql:ref-cursor-function\>](XSQL-pages-reference.md), and other actions that accept SQL or PL/SQL statements.

PL/SQL index-by tables work with the OCI JDBC driver but not the JDBC thin driver. By using the nested table collection type `XSQL_TABLE_OF_VARCHAR`, you can use array-valued parameters with either driver. In this way you avoid losing the programming flexibility of working with array values in PL/SQL.

Example 25-6 testTableFunction

    FUNCTION testTableFunction(p_name  XSQL_TABLE_OF_VARCHAR,
                               p_value XSQL_TABLE_OF_VARCHAR)
    RETURN VARCHAR2 IS
      lv_ret     VARCHAR2(4000);
      lv_numElts INTEGER;
    BEGIN
      IF p_name IS NOT NULL THEN
        lv_numElts := p_name.COUNT;
        FOR j IN 1..lv_numElts LOOP
          IF (j > 1) THEN
            lv_ret := lv_ret||':';
          END IF;
          lv_ret := lv_ret||p_name(j)||'='||p_value(j);
        END LOOP;
      END IF;
      RETURN lv_ret;
    END;

Example 25-7 XSQL Page with Array-Valued Parameters

    <page xmlns:xsql="urn:oracle-xsql" connection="demo"
          someNames="aa,bb,cc" someValues="11,22,33">
      <xsql:query bind-params="someNames[] someValues[]">
        SELECT testTableFunction(?,?) AS example
        FROM dual
      </xsql:query>
    </page>

Example 25-8 Using an Array-Valued Parameter to Restrict Rows

    <page xmlns:xsql="urn:oracle-xsql" connection="hr">
      <xsql:set-page-param name="someEmployees[]" value="196,197"/>
      <xsql:query bind-params="someEmployees[]">
        SELECT first_name||' '||last_name AS name, salary
        FROM employees
        WHERE employee_id IN (
            SELECT * FROM TABLE(CAST( ? AS xsql_table_of_varchar))
         )
       </xsql:query>
    </page>

### 25.4 Setting Error Parameters on Built-In Actions

You can set a page-private parameter on a built-in XSQL action when the action reports a nonfatal error.

The XSQL page processor determines whether an action encountered a nonfatal error during its execution. For example, an attempt to insert a row or invoke a stored procedure can fail with a database exception that gets included in your XSQL data page as an` <xsql-error>` element.

Use attribute `error-param` on the action to set a page-private parameter on a built-in XSQL action when the action reports a nonfatal error. For example, to set parameter `dml-error` when the statement inside action [\<xsql:dml\>](XSQL-pages-reference.md) encounters a database error, you can use the technique shown in Example 25-9.

If the execution of action `<xsql:dml>` encounters an error then the XSQL processor sets the page-private parameter `dml-error` to the string `"Error"`. If the execution is successful then the XSQL processor does not assign a value to the error parameter. In Example 25-9, if the page-private parameter `dml-error` already exists then it retains its current value. If it does not exist then it continues not to exist.

Example 25-9 Setting an Error Parameter

    <xsql:dml error-param="dml-error" bind-params="val">
      INSERT INTO yourtable(somecol)
        VALUES(?)
    </xsql:dml>

#### 25.4.1 Using Conditional Logic with Error Parameters

How to get conditional behavior in your XSQL page template is described.

By using the error parameter in combination with [\<xsql:if-param\>](XSQL-pages-reference.md), you can achieve conditional behavior in your XSQL page template. For example, assume that your connection definition sets the `AUTOCOMMIT` flag to `false` on the connection named `demo` in the XSQL configuration file. The XSQL page shown in Example 25-10 shows how you might roll back the changes made by a previous action if a subsequent action encounters an error.

If you have written custom action handlers, and if your custom actions invoke `reportMissingAttribute()`, `reportError()`, or `reportErrorIncludingStatement()` to report nonfatal action errors, then they automatically pick up this feature as well.

Example 25-10 Achieving Conditional Behavior with an Error Parameter

    <!-- NOTE: Connection "demo" must not set to autocommit! -->
    <page connection="demo" xmlns:xsql="urn:oracle-xsql">
      <xsql:dml error-param="dml-error" bind-params="val">
        INSERT INTO yourtable(somecol)
          VALUES(?)
      </xsql:dml>
      <!-- This second statement will commit if it succeeds -->
      <xsql:dml commit="yes" error-param="dml-error" bind-params="val2">
        INSERT INTO anothertable(anothercol)
          VALUES(?)
      </xsql:dml>
      <xsql:if-param name="dml-error" exists="yes">
        <xsql:dml>
          ROLLBACK
        </xsql:dml>
      </xsql:if-param>
    </page>

#### 25.4.2 Formatting XSQL Action Handler Errors

Errors raised by the processing of XSQL action elements are reported as XML elements in a uniform way. This fact enables XSLT stylesheets to detect their presence and optionally format them for presentation.

The action element in error is replaced in the page by this element:

    <xsql-error action="xxx">

Depending on the error the `<xsql-error>` element contains:

- A nested `<message>` element

- A `<statement>` element with the offending SQL statement

Example 25-11 shows an XSLT stylesheet that uses this information to display error information on the screen.

Example 25-11 XSLT Stylesheet

    <xsl:if test="//xsql-error">
         <table style="background:yellow">
            <xsl:for-each select="//xsql-error">
               <tr>
                <td><b>Action</b></td>
                <td><xsl:value-of select="@action"/></td>
                </tr>
                <tr valign="top">
                <td><b>Message</b></td>
                <td><xsl:value-of select="message"/></td>
               </tr>
              </xsl:for-each>
         </table>
    </xsl:if>

### 25.5 Including XMLType Query Results in XSQL Pages

Oracle Database supports `XMLType` for storing and querying XML-based database content.

You can exploit database XML features to produce XML data for inclusion in your XSQL pages by using one of these techniques:

- [\<xsql:query\>](XSQL-pages-reference.md) handles any query including columns of type `XMLType`, but it handles XML markup in `CLOB` and `VARCHAR2` columns as literal text.

- [\<xsql:include-xml\>](XSQL-pages-reference.md) parses and includes a single `CLOB` or string-based XML document retrieved from a query.

One difference between the preceding approaches is that `<xsql:include-xml>` parses the literal XML appearing in a CLOB or string value as needed to turn it into a tree of elements and attributes. In contrast, `<xsql:query>` leaves XML markup in `CLOB` or string-valued columns as literal text.

Another difference is that while `<xsql:query>` can handle query results of any number of columns and rows, `<xsql:include-xml>` works on a single column of a single row. Accordingly, when using `<xsql:include-xml>`, the `SELECT` statement inside it returns a single row containing a single column. The column can either be a `CLOB` or a `VARCHAR2` value containing a well-formed XML document. The XSQL engine parses the XML document and includes it in your XSQL page.

Example 25-12 uses nested `XmlAgg()` functions to aggregate the results of a dynamically-constructed XML document containing departments and nested employees. The functions aggregate the document into a single "result" document wrapped in a `<DepartmentList>` element.

In another example, suppose you have many `<Movie>` XML documents stored in a table of `XMLType` called `movies.` Each document might look like the one shown in Example 25-13.

You can use the built-in XPath query features to extract an aggregate list of all cast members who have received Oscar awards from any movie in the database. Example 25-14 shows a sample query.

To include this query result of `XMLType` in your XSQL page, paste the query inside an `<xsql:query>` element. Make sure you include an alias for the query expression, as shown in Example 25-15.

You can use the combination of `XmlElement()` and `XmlAgg()` to make the database aggregate all of the XML fragments identified by the query into single, well-formed XML document. The functions work to produce a well-formed result like this:

    <AwardedActors>
      <Actor>...</Actor>
      <Actress>...</Actress>
    </AwardedActors>

You can use the standard XSQL bind variable capabilities in the middle of an XPath expression if you concatenate the bind variable into the expression. For example, to parameterize the value `Oscar` into a parameter named `award-from`, you can use an XSQL page like the one shown in Example 25-16.

Example 25-12 Aggregating a Dynamically-Constructed XML Document

    <xsql:query connection="hr" xmlns:xsql="urn:oracle-xsql">
      SELECT XmlElement("DepartmentList",
               XmlAgg(
                 XmlElement("Department",
                   XmlAttributes(department_id AS "Id"),
                   XmlForest(department_name AS "Name"),
                   (SELECT XmlElement("Employees",
                             XmlAgg(
                               XmlElement("Employee",
                                 XmlAttributes(employee_id AS "Id"),
                                 XmlForest(first_name||' '||last_name AS "Name",
                                           salary   AS "Salary",
                                           job_id   AS "Job")
                               )
                             )
                           )
                    FROM employees e
                    WHERE e.department_id = d.department_id
                   )
                 )
               )
             ) AS result
      FROM departments d
      ORDER BY department_name
    </xsql:query>

Example 25-13 Movie XML Document

    <Movie Title="The Talented Mr.Ripley" RunningTime="139" Rating="R">
      <Director>
        <First>Anthony</First>
        <Last>Minghella</Last>
      </Director>
      <Cast>
        <Actor Role="Tom Ripley">
          <First>Matt</First>
          <Last>Damon</Last>
        </Actor>
        <Actress Role="Marge Sherwood">
          <First>Gwyneth</First>
          <Last>Paltrow</Last>
        </Actress>
        <Actor Role="Dickie Greenleaf">
          <First>Jude</First>
          <Last>Law</Last>
          <Award From="BAFTA" Category="Best Supporting Actor"/>
        </Actor>
      </Cast>
    </Movie>

Example 25-14 Using XPath to Extract an Aggregate List

    SELECT XMLELEMENT("AwardedActors",
               XMLAGG(EXTRACT(VALUE(m),
                      '/Movie/Cast/*[Award[@From="Oscar"]]')))
    FROM movies m

Example 25-15 Including an XMLType Query Result

    <xsql:query connection="demo" xmlns:xsql="urn:oracle-xsql">
      SELECT XMLELEMENT("AwardedActors",
               XMLAGG(EXTRACT(VALUE(m),
                      '/Movie/Cast/*[Award[@From="Oscar"]]'))) AS result
      FROM movies m
    </xsql:query>

Example 25-16 Using XSQL Bind Variables in an XPath Expression

    <xsql:query connection="orcl92" xmlns:xsql="urn:oracle-xsql"
                award-from="Oscar"  bind-params="award-from">
      /* Using a bind variable in an XPath expression */
      SELECT XMLELEMENT("AwardedActors",
               XMLAGG(EXTRACT(VALUE(m),
                      '/Movie/Cast/*[Award[@From="'|| ? ||'"]]'))) AS result
      FROM movies m
    </xsql:query>

### 25.6 Handling Posted XML Content

In addition to simplifying the assembly and transformation of XML content, the XSQL pages framework helps you handle posted XML content.

Built-in actions provide these advantages:

- Simplify the handling of posted data from both XML document and HTML forms

- Enable data to be posted directly into a database table by using XSU

XSU can perform database inserts, updates, and deletes based on the content of an XML document in canonical form for a target table or view. For a specified table, the canonical XML form of its data is given by one row of XML output from a `SELECT *` query. When given an XML document in this form, XSU can automate the DML operation.

By combining XSU with XSLT, you can transform XML in any format into the canonical format expected by a given table. XSU can then perform DML on the resulting canonical XML.

The following built-in XSQL actions make it possible for you to exploit this capability from within your XSQL pages:

- [\<xsql:insert-request\>](XSQL-pages-reference.md)

  Insert the optionally transformed XML document that was posted in the request into a table.

- [\<xsql:update-request\>](XSQL-pages-reference.md)

  Update the optionally transformed XML document that was posted in the request into a table or view.

- [\<xsql:delete-request\>](XSQL-pages-reference.md)

  Delete the optionally transformed XML document that was posted in the request from a table or view.

- [\<xsql:insert-param\>](XSQL-pages-reference.md)

  Insert the optionally transformed XML document that was posted as the value of a request parameter into a table or view.

If you target a database view with your insert, then you can create `INSTEAD OF INSERT` triggers on the view to further automate the handling of the posted information. For example, an `INSTEAD OF INSERT` trigger on a view can use PL/SQL to check for the existence of a record and intelligently choose whether to do an `INSERT` or an `UPDATE` depending on the result of this check.

#### 25.6.1 Understanding XML Posting Options

An overview is provided of XML posting options.

The XSQL pages framework can handle posted data in these scenarios:

- A client program sends an HTTP `POST` message that targets an XSQL page. The request body contains an XML document; the HTTP header reports a `ContentType` of "`text/xml`".

  In this case, `<xsql:insert-request>`, `<xsql:update-request>`, or `<xsql:delete-request>` can insert, update, or delete the content of the posted XML in the target table. If you transform the posted XML with XSLT, then the posted document is the source for the transformation.

- A client program sends an HTTP `GET` request for an XSQL page, one of whose parameters contains an XML document.

  In this case, you can use the `<xsql:insert-param>` action to insert the content of the posted XML parameter value in the target table. If you transform the posted XML document with XSLT, then the XML document in the parameter value is the source document for this transformation.

- A browser submits an HTML form with `method`=`"POST"` whose action targets an XSQL page. The request body of the HTTP `POST` message contains an encoded version of the form fields and values with a `ContentType` of "`application/x-www-form-urlencoded`".

  In this case, the request does not contain an XML document, but an encoded version of the form parameters. To make all three of these cases uniform, however, the XSQL page processor materializes on demand an XML document from the form parameters, session variables, and cookies contained in the request. The XSLT processor transforms this dynamically-materialized XML document into canonical form for DML by using `<xsql:insert>`, `<xsql:update-request>`, or `<xsql:delete-request>`.

When working with posted HTML forms, the dynamically materialized XML document has the form shown in Example 25-17.

If multiple parameters are posted with the same name, then the XSQL processor automatically creates multiple `<row>` elements to make subsequent processing easier. Assume that a request posts or includes these parameters and values:

- `id` = `101`

- `name` = `Steve`

- `id` = `102`

- `name` = `Sita`

- `operation` = `update`

The XSQL page processor creates a set of parameters as follows:

    <request>
      <parameters>
        <row>
          <id>101</id>
          <name>Steve</name>
        </row>
        <row>
          <id>102</id>
          <name>Sita</name>
        </row>
        <operation>update</operation>
      </parameters>
      ...
    </request>

You must provide an XSLT stylesheet that transforms this materialized XML document containing the request parameters into canonical format for your target table. Thus, you can build an XSQL page:

    <!--
     | ShowRequestDocument.xsql
     | Show Materialized XML Document for an HTML Form
     +-->
    <xsql:include-request-params xmlns:xsql="urn:oracle-xsql"/>

With this page in place, you can temporarily modify your HTML form to post to the `ShowRequestDocument.xsql` page. In the browser you see the "raw" XML for the materialized XML request document, which you can save and use to develop the XSL transformation.

Example 25-17 XML Document Generated from HTML Form

    <request>
      <parameters>
        <firstparamname>firstparamvalue</firstparamname>
         ...
        <lastparamname>lastparamvalue</lastparamname>
      </parameters>
      <session>
        <firstparamname>firstsessionparamvalue</firstparamname>
          ...
        <lastparamname>lastsessionparamvalue</lastparamname>
      </session>
      <cookies>
        <firstcookie>firstcookievalue</firstcookiename>
           ...
        <lastcookie>firstcookievalue</lastcookiename>
      </cookies>
    </request>

### 25.7 Producing PDF Output with the FOP Serializer

Using the XSQL pages framework support for custom serializers, the `oracle.xml.xsql.serializers.XSQLFOPSerializer` class provides integration with the Apache Formatting Objects Processor (FOP). The FOP processor renders a PDF document from an XML document containing XSL Formatting Objects.

As described in [Table 24-1](using-XSQL-pages-publishing-framework.md), the demo directory includes the `emptablefo.xsl` stylesheet and `emptable.xsql` page as illustrations. If you get an error trying to use the FOP serializer, then probably you do not have all of the required JAR files in the `CLASSPATH`. The `XSQLFOPSerializer` class resides in the separate `xml.jar` file, which must be included in the `CLASSPATH` to use the FOP integration. You must also add these additional Java archives to your `CLASSPATH`:

- `fop.jar`—from Apache, version 0.20.3 or later

- `batik.jar`—from the FOP distribution

- `avalon-framework-4.0.jar`—from FOP distribution

- l`ogkit-1.0.jar`—from FOP distribution

In case you want to customize the implementation, the source code for the FOP serializer provided in this release is shown in Example 25-18.

**See Also:**

[Apache FOP](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=apache_org_fop)

Example 25-18 Source Code for FOP Serializer

    package oracle.xml.xsql.serializers;
    import org.w3c.dom.Document;
    import org.apache.log.Logger;
    import org.apache.log.Hierarchy;
    import org.apache.fop.messaging.MessageHandler;
    import org.apache.log.LogTarget;
    import oracle.xml.xsql.XSQLPageRequest;
    import oracle.xml.xsql.XSQLDocumentSerializer;
    import org.apache.fop.apps.Driver;
    import org.apache.log.output.NullOutputLogTarget;
    /**
     * Tested with the FOP 0.20.3RC release from 19-Jan-2002
     */
    public class XSQLFOPSerializer implements XSQLDocumentSerializer {
      private static final String PDFMIME = "application/pdf";
      public void serialize(Document doc, XSQLPageRequest env) throws Throwable {
        try {
          // First make sure we can load the driver
          Driver FOPDriver = new Driver();
          // Tell FOP not to spit out any messages by default.
          // You can modify this code to create your own FOP Serializer
          // that logs the output to one of many different logger targets
          // using the Apache LogKit API
          Logger logger=Hierarchy.getDefaultHierarchy().getLoggerFor("XSQLServlet");
          logger.setLogTargets(new LogTarget[]{new NullOutputLogTarget()});
          FOPDriver.setLogger(logger);
          // Some of FOP's messages appear to still use MessageHandler.
          MessageHandler.setOutputMethod(MessageHandler.NONE);
          // Then set the content type before getting the reader
          env.setContentType(PDFMIME);
          FOPDriver.setOutputStream(env.getOutputStream());
          FOPDriver.setRenderer(FOPDriver.RENDER_PDF); FOPDriver.render(doc);
        }
        catch (Exception e) {
          // Cannot write PDF output for the error anyway.
          // So maybe this stack trace will be useful info
          e.printStackTrace(System.err);
        }
      }
    }

### 25.8 Performing XSQL Customizations

XSQL customization topics are presented.

#### 25.8.1 Writing Custom XSQL Action Handlers

The XSQL pages engine processes an XSQL page by looking for action elements from the `xsql` namespace and invoking an appropriate action element handler class to process each action. The processor supports any action that implements the `XSQLActionHandler` interface. All of the built-in actions implement this interface.

When a task requires custom processing, and none of the built-in actions listed in [Table 33-2](XSQL-pages-reference.md) does exactly what you need, you can write your own actions.

The XSQL engine processes the actions in a page in the following way. For each action in the page, the engine performs these steps:

1.  Constructs an instance of the action handler class using the default constructor
2.  Initializes the handler instance with the action element object and the page processor context by invoking the method `init(Element actionElt,XSQLPageRequest context`)
3.  Invokes the method that allows the handler to handle the action `handleAction` (`Node` result)

For built-in actions, the engine can map the XSQL action element name to the Java class that implements the handler of the action. [Table 33-2](XSQL-pages-reference.md) lists the built-in actions and their corresponding classes.

For user-defined actions, use this built-in action, replacing `fully.qualified.Classname` with the name of your class:

    <xsql:action handler="fully.qualified.Classname" ... />

The `handler` attribute provides the fully qualified name of the Java class that implements the custom action handler.

##### 25.8.1.1 Implementing the XSQLActionHandler Interface

To create a custom action handler, provide a class that implements To create a custom action handler, provide a class that implements `oracle.xml.xsql.XSQLActionHandler` interface `oracle.xml.xsql.XSQLActionHandler`. Most custom action handlers extend `oracle.xml.xsql.XSQLActionHandlerImpl`, which provides a default implementation of the `init()` method and offers useful helper methods.

When an action handler's `handleAction()` method is invoked by the XSQL pages processor, a DOM fragment is passed to the action implementation. The action handler appends any dynamically created XML content returned to the page to the root node.

The XSQL processor conceptually replaces the action element in the XSQL page with the content of this document fragment. It is legal for an action handler to append nothing to this fragment if it has no XML content to add to the page.

While writing your custom action handlers, some methods on the `XSQLActionHandlerImpl` class are helpful. Table 25-2 lists these methods.

Table 25-2 Helpful Methods in the XSQLActionHandlerImpl Class

| Method Name                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `getActionElement`              | Returns the current action element being handled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `getActionElementContent`       | Returns the text content of the current action element, with all lexical parameters substituted appropriately.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `getPageRequest`                | Returns the current XSQL pages processor context. Using this object you do this:<br>• `setPageParam()`<br>• Set a page parameter value.<br>• `getPostedDocument()/setPostedDocument()`<br>• Get or set the posted XML document.<br>• `translateURL()`<br>• Translate a relative URL to an absolute URL.<br>• `getRequestObject()/setRequestObject()`<br>• Get or set objects in the page request context that can be shared across actions in a single page.<br>• `getJDBCConnection()`<br>• Gets the JDBC connection in use by this page (possible null if no connection in use).<br>• `getRequestType()`<br>• Detect whether you are running in the Servlet, Command Line, or Programmatic context. For example, if the request type is Servlet then you can cast the `XSQLPageRequest` object to the more specific `XSQLServletPageRequest` to access servlet-specific methods such as `getHttpServletRequest`, `getHttpServletResponse`, and `getServletContext`. |
| `getAttributeAllowingParam`     | Retrieves the attribute value from an element, resolving any XSQL lexical parameter references that might appear in value of the attribute. Typically this method is applied to the action element itself, but it is also useful for accessing attributes of subelements. To access an attribute value without allowing lexical parameters, use the standard `getAttribute()` method on the DOM `Element` interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `appendSecondaryDocument`       | Appends the contents of an external XML document to the root of the action handler result content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `addResultElement`              | Simplifies appending a single element with text content to the root of the action handler result content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `firstColumnOfFirstRow`         | Returns the first column value of the first row of a SQL statement. Requires the current page to have a connection attribute on its document element, or an error is returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `getBindVariableCount`          | Returns the number of tokens in the space-delimited list of `bind-params`. This number indicates how many bind variables are expected to be bound to parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `handleBindVariables`           | Manages the binding of JDBC bind variables that appear in a prepared statement with the parameter values specified in the `bind-params` attribute on the current action element. If the statement is already using several bind variables before invoking this method, you can pass the number of existing bind variable slots in use as well.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `reportErrorIncludingStatement` | Reports an error. The error includes the offending (SQL) statement that caused the problem and optionally includes a numeric error code.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `reportFatalError`              | Reports a fatal error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `reportMissingAttribute`        | Reports an error that a required action handler attribute is missing by using the `<xsql-error>` element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `reportStatus`                  | Reports action handler status by using the `<xsql-status>` element.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `requiredConnectionProvided`    | Checks whether a connection is available for this request and outputs an errorgram into the page if no connection is available.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `variableValue`                 | Returns the value of a lexical parameter, taking into account all scoping rules that might determine its default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

Example 25-19 shows a custom action handler named `MyIncludeXSQLHandler` that leverages a built-in action handler. It uses arbitrary Java code to modify the XML fragment returned by this handler before appending its result to the XSQL page.

You might have to write custom action handlers that work differently based on whether the page is requested through the XSQL servlet, the XSQL command-line utility, or programmatically through the `XSQLRequest` class.You can invoke `getPageRequest()` in your action handler implementation to get a reference to the `XSQLPageRequest` interface for the current page request. By invoking `getRequestType()` on the `XSQLPageRequest` object, you can determine whether the request is coming from the Servlet, Command Line, or Programmatic routes. If the return value is `Servlet`, then you can access the HTTP servlet request, response, and servlet context objects as shown in Example 25-20.

Example 25-19 MyIncludeXSQLHandler.java

    import oracle.xml.xsql.*;
    import oracle.xml.xsql.actions.XSQLIncludeXSQLHandler;
    import org.w3c.dom.*;
    import java.sql.SQLException;
    public class MyIncludeXSQLHandler extends XSQLActionHandlerImpl {
      XSQLActionHandler nestedHandler = null;
      public void init(XSQLPageRequest req, Element action) {
        super.init(req, action);
        // Create an instance of an XSQLIncludeXSQLHandler and init() the handler by
        // passing the current request/action. This assumes the XSQLIncludeXSQLHandler
        // will pick up its href="xxx.xsql" attribute from the current action element.
        nestedHandler = new XSQLIncludeXSQLHandler();
        nestedHandler.init(req,action);
      }
      public void handleAction(Node result) throws SQLException {
        DocumentFragment df=result.getOwnerDocument().createDocumentFragment();
        nestedHandler.handleAction(df);
        // Custom Java code here can work on the returned document fragment
        // before appending the final, modified document to the result node.
        // For example, add an attribute to the first child.
        Element e = (Element)df.getFirstChild();
        if (e != null) {
          e.setAttribute("ExtraAttribute","SomeValue");
        }
        result.appendChild(df);
      }
    }

Example 25-20 Testing for the Servlet Request

    XSQLServletPageRequest xspr = (XSQLServletPageRequest)getPageRequest();
    if (xspr.getRequestType().equals("Servlet")) {
      HttpServletRequest     req  = xspr.getHttpServletRequest();
      HttpServletResponse   resp  = xspr.getHttpServletResponse();
      ServletContext        cont  = xspr.getServletContext();
      // Do something here with req, resp, or cont. Note that writing to the response
      // directly from a handler produces unexpected results. All the servlet or your
      // custom Serializer to write to the servlet response output stream at the right
      // moment later when all action elements have been processed.
    }

##### 25.8.1.2 Using Multivalued Parameters in Custom XSQL Actions

`XSQLActionHandlerImpl` is the base class for custom XSQL actions.

It supports:

- Array-named lexical parameter substitution

- Array-named bind variables

- Simple-valued parameters

If your custom actions use methods such as `getAttributeAllowingParam()`, `getActionElementContent()`, or `handleBindVariables()` from this base class, you pick up multivalued parameter functionality for free in your custom actions.

Use the `getParameterValues()` method on the `XSQLPageRequest` interface to explicitly get a parameter value as a `String[]`. The helper method `variableValues()` in `XSQLActionHandlerImpl` enables you to use this functionality from within a custom action handler if you must do so programmatically.

#### 25.8.2 Implementing Custom XSQL Serializers

You can implement a user-defined serializer class to control how the final XSQL datapage is serialized to a text or binary stream. A user-defined serializer must implement interface `oracle.xml.xsql.XSQLDocumentSerializer`.

Interface `oracle.xml.xsql.XSQLDocumentSerializer` contains this single method:

    void serialize(org.w3c.dom.Document doc, XSQLPageRequest env) throws Throwable;

Only DOM-based serializers are supported. A custom serializer class is expected to perform these steps:

1.  Set the content type of the serialized stream before writing any content to the output `PrintWriter` (or `OutputStream`).

    Set the type by invoking `setContentType()` on the `XSQLPageRequest` passed to your serializer. When setting the content type, you can set a MIME type:

        env.setContentType("text/html");

    Alternatively, you can set a MIME type with an explicit output encoding character set:

        env.setContentType("text/html;charset=Shift_JIS");

2.  Invoke either `getWriter()` or `getOutputStream()` (but not both) on the `XSQLPageRequest` to get the appropriate `PrintWriter` or `OutputStream` for serializing the content.

The custom serializer in Example 25-21 shows a simple implementation that serializes an HTML document containing the name of the document element of the current XSQL data page.

Example 25-21 Custom Serializer

    package oracle.xml.xsql.serializers;
    import org.w3c.dom.Document;
    import java.io.PrintWriter;
    import oracle.xml.xsql.*;

    public class XSQLSampleSerializer implements XSQLDocumentSerializer {
      public void serialize(Document doc, XSQLPageRequest env) throws Throwable {
        String encoding = env.getPageEncoding();  // Use same encoding as XSQL page
                                                  // template. Set to specific
                                                  // encoding if necessary
        String mimeType = "text/html"; // Set this to the appropriate content type
        // (1) Set content type using the setContentType on the XSQLPageRequest
        if (encoding != null && !encoding.equals("")) {
          env.setContentType(mimeType+";charset="+encoding);
        }
        else {
          env.setContentType(mimeType);
        }
        // (2) Get the output writer from the XSQLPageRequest
        PrintWriter e = env.getWriter();
        // (3) Serialize the document to the writer
        e.println("<html>Document element is <b>"+
                  doc.getDocumentElement().getNodeName()+"</b></html>");
      }
    }

##### 25.8.2.1 Techniques for Using a Custom Serializer

There are two ways to use a custom serializer, depending on whether you must first perform an XSLT transformation before serializing.

To perform an XSLT transformation before using a custom serializer, add the `serializer="java:fully.qualified.ClassName"` in the `<?xml-stylesheet?>` processing instruction at the top of your page. The following examples shows this technique:

    <?xml version="1.0?>
    <?xml-stylesheet type="text/xsl" href="mystyle.xsl"
                     serializer="java:my.pkg.MySerializer"?>

If you need only the custom serializer, omit the `type` and `href` attributes. The following example shows this technique:

    <?xml version="1.0?>
    <?xml-stylesheet serializer="java:my.pkg.MySerializer"?>

##### 25.8.2.2 Assigning a Short Name to a Custom Serializer

You can assign a short name to your custom serializers in the `<serializerdefs>` section of the XSQL configuration file. You can then use the short name in the serializer attribute, to save typing. The short name is case-sensitive.

Assume that you have the information shown in Example 25-22 in your XSQL configuration file. You can use the short names "Sample" or "FOP" in a stylesheet instruction:

    <?xml-stylesheet type="text/xsl" href="emp-to-xslfo.xsl" serializer="FOP"?>
    <?xml-stylesheet serializer="Sample"?>

The `XSQLPageRequest` interface supports both a `getWriter()` and a `getOutputStream()` method. Custom serializers can invoke `getOutputStream()` to return an `OutputStream` instance into which binary data can be serialized. When you use the XSQL servlet, writing to this output stream writes binary information to the servlet output stream.

The serializer shown in Example 25-23 shows an example of writing a dynamic GIF image. In this example the GIF image is a static "ok" icon, but it shows the basic technique that a more sophisticated image serializer must use.

Using the XSQL command-line utility, the binary information is written to the target output file. Using the `XSQLRequest` API, two constructors exist that allow the caller to supply the target `OutputStream` to use for the results of page processing.

Your serializer must either invoke `getWriter()` for textual output or `getOutputStream()` for binary output but not both. Invoking both in the same request raises an error.

Example 25-22 Assigning Short Names to Custom Serializers

    <XSQLConfig>
      <!--and so on. -->
      <serializerdefs>
        <serializer>
          <name>Sample</name>
          <class>oracle.xml.xsql.serializers.XSQLSampleSerializer</class>
        </serializer>
        <serializer>
          <name>FOP</name>
          <class>oracle.xml.xsql.serializers.XSQLFOPSerializer</class>
        </serializer>
      </serializerdefs>
    </XSQLConfig>

Example 25-23 Writing a Dynamic GIF Image

    package oracle.xml.xsql.serializers;
    import org.w3c.dom.Document;
    import java.io.*;
    import oracle.xml.xsql.*;

    public class XSQLSampleImageSerializer implements XSQLDocumentSerializer {
       // Byte array representing a small "ok" GIF image
       private static byte[] okGif =
         {(byte)0x47,(byte)0x49,(byte)0x46,(byte)0x38,
          (byte)0x39,(byte)0x61,(byte)0xB,(byte)0x0,
          (byte)0x9,(byte)0x0,(byte)0xFFFFFF80,(byte)0x0,
          (byte)0x0,(byte)0x0,(byte)0x0,(byte)0x0,
          (byte)0xFFFFFFFF,(byte)0xFFFFFFFF,(byte)0xFFFFFFFF,(byte)0x2C,
          (byte)0x0,(byte)0x0,(byte)0x0,(byte)0x0,
          (byte)0xB,(byte)0x0,(byte)0x9,(byte)0x0,
          (byte)0x0,(byte)0x2,(byte)0x14,(byte)0xFFFFFF8C,
          (byte)0xF,(byte)0xFFFFFFA7,(byte)0xFFFFFFB8,(byte)0xFFFFFF9B,
          (byte)0xA,(byte)0xFFFFFFA2,(byte)0x79,(byte)0xFFFFFFE9,
          (byte)0xFFFFFF85,(byte)0x7A,(byte)0x27,(byte)0xFFFFFF93,
          (byte)0x5A,(byte)0xFFFFFFE3,(byte)0xFFFFFFEC,(byte)0x75,
          (byte)0x11,(byte)0xFFFFFF85,(byte)0x14,(byte)0x0,
          (byte)0x3B};

      public void serialize(Document doc, XSQLPageRequest env) throws Throwable {
        env.setContentType("image/gif");
        OutputStream os = env.getOutputStream();
        os.write(okGif,0,okGif.length);
        os.flush();
      }
    }

#### 25.8.3 Using a Custom XSQL Connection Manager for JDBC Data Sources

As an alternative to defining your named connections in the XSQL configuration file, you can use one of two `XSQLConnectionManager` implementations provided. These let you use your servlet container's JDBC data source implementation and related connection pooling features.

This XSQL pages framework provides this alternative connection manager implementations:

- `oracle.xml.xsql.XSQLDatasourceConnectionManager `

  Consider using this connection manager if your servlet container's data source implementation does not use the Oracle JDBC driver. Features of the XSQL pages system such as `<xsql:ref-cursor-function>` and `<xsql:include-owa>` are not available when you do not use an Oracle JDBC driver.

- `oracle.xml.xsql.XSQLOracleDatasourceConnectionManager `

  Consider using this connection manager when your data source implementation returns JDBC `PreparedStatement` and `CallableStatement` objects that implement the `oracle.jdbc.PreparedStatement` and `oracle.jdbc.CallableStatement` interfaces. The Oracle WebLogic Server has a data source implementation that performs this task.

When using either of the preceding alternative connection manager implementations, the value of the connection attribute in your XSQL page template is the Java Naming and Directory Interface (JNDI) name used to look up your desired data source. For example, the value of the connection attribute might look like:

- `jdbc/scottDS`

- `java:comp/env/jdbc/MyDatasource`

If you are not using the default XSQL pages connection manager, then needed connection pooling functionality must be provided by the alternative connection manager implementation. In the case of the preceding two options based on JDBC data sources, you must properly configure your servlet container to supply the connection pooling. See your servlet container documentation for instructions on how to properly configure the data sources to offer pooled connections.

#### 25.8.4 Writing Custom XSQL Connection Managers

You can provide a custom connection manager to replace the built-in connection management mechanism.

To provide a custom connection manager implementation, you must perform these steps:

1.  Write a connection manager factory class that implements the `oracle.xml.xsql.XSQLConnectionManagerFactory` interface.

2.  Write a connection manager class that implements the `oracle.xml.xsql.XSQLConnectionManager` interface.

3.  Change the name of the `XSQLConnectionManagerFactory` class in your XSQL configuration file.

The XSQL servlet uses your connection management scheme instead of the XSQL pages default scheme.

You can set your custom connection manager factory as the default connection manager factory by providing the class name in the XSQL configuration file. Set the factory in this section:

    <!--
     | Set the name of the XSQL Connection Manager Factory
     | implementation. The class must implement the
     | oracle.xml.xsql.XSQLConnectionManagerFactory interface.
     | If unset, the default is to use the built-in connection
     | manager implementation in
     | oracle.xml.xsql.XSQLConnectionManagerFactoryImpl
    +-->
      <connection-manager>
          <factory>oracle.xml.xsql.XSQLConnectionManagerFactoryImpl</factory>
      </connection-manager>

In addition to specifying the default connection manager factory, you can associate a custom connection factory with a `XSQLRequest` object by using APIs provided.

The responsibility of the `XSQLConnectionManagerFactory` is to return an instance of an `XSQLConnectionManager` for use by the current request. In a multithreaded environment such as a servlet engine, the `XSQLConnectionManager` object must ensure that a single `XSQLConnection` instance is not used by two different threads. This aim is realized by marking the connection as in use for the time between the `getConnection()` and `releaseConnection()` method invocations. The default XSQL connection manager implementation automatically pools named connections and adheres to this thread-safe policy.

If your custom implementation of `XSQLConnectionManager` implements the optional `oracle.xml.xsql.XSQLConnectionManagerCleanup` interface, then your connection manager can clean up any resources it has allocated. For example, if your servlet container invokes the `destroy()` method on the `XSQLServlet` servlet, which can occur during online administration of the servlet for example, the connection manager has a chance to clean up resources as part of the servlet destruction process.

##### 25.8.4.1 Accessing Authentication Information in a Custom Connection Manager

To use the HTTP authentication mechanism to get the user name and password to connect to the database, write a customized connection manager. You can then invoke a `getConnection()` method to get the needed information.

You can write a Java program that follows these steps:

1.  Pass an instance of the `oracle.xml.xsql.XSQLPageRequest` interface to the `getConnection()` method.
2.  Invoke `getRequestType()` to ensure that the request type is `Servlet`.
3.  Cast the `XSQLPageRequest` object to an `XSQLServletPageRequest`.
4.  Invoke `getHttpServletRequest()` on the result of the preceding step.
5.  Get the authentication information from the `javax.servlet.http.HttpServletResponse` object returned by the previous invocation.

#### 25.8.5 Implementing a Custom XSQLErrorHandler

You can control how serious page processor errors such as an unavailable connection are reported to users by implementing interface `oracle.xml.xsql.XSQLErrorHandler`.

The interface contains this single method signature:

    public interface XSQLErrorHandler {
      public void handleError( XSQLError err, XSQLPageRequest env);
    }

You can provide a class that implements the `XSQLErrorHandler` interface to customize how the XSQL pages processor writes error messages. The new `XSQLError` object encapsulates the error information and provides access to the error code, formatted error message, and so on.

Example 25-24 shows a sample implementation of `XSQLErrorHandler`.

You can control which custom `XSQLErrorHandler` implementation is used in these distinct ways:

- Define the name of a custom `XSQLErrorHandler` implementation class in the XSQL configuration file. You must provide the fully qualified class name of your error handler class as the value of the `/XSQLConfig/processor/error-handler/class` entry.

  If the XSQL processor can load this class, and if it correctly implements the `XSQLErrorHandler` interface, then it uses this class as a singleton and replaces the default implementation globally wherever page processor errors are reported.

- Override the error writer on a per page basis by using the `errorHandler` (or `xsql:errorHandler`) attribute on the document element of the page. The attribute value is the fully qualified class name of a class that implements the `XSQLErrorHandler` interface. This class reports the errors only for this page. The class is instantiated on each page request by the page engine.

You can use a combination of the preceding approaches if needed.

Example 25-24 myErrorHandler class

    package example;
    import oracle.xml.xsql.*;
    import java.io.*;
    public class myErrorHandler implements XSQLErrorHandler {
      public void logError( XSQLError err, XSQLPageRequest env) {
        // Must set the content type before writing anything out
        env.setContentType("text/html");
        PrintWriter pw = env.getErrorWriter();
        pw.println("<H1>ERROR</H1><hr>"+err.getMessage());
      }
    }

#### 25.8.6 Providing a Custom XSQL Logger Implementation

You can optionally register custom code to handle the logging of the start and end of each XSQL page request. Your custom logger code must provide an implementation of interfaces `oracle.xml.xsql.XSQLLoggerFactory` and `oracle.xml.xsql.XSQLLogger`.

The `XSQLLoggerFactory` interface contains this single method:

    public interface XSQLLoggerFactory {
      public XSQLLogger create( XSQLPageRequest env);
    }

You can provide a class that implements the `XSQLLoggerFactory` interface to decide how `XSQLLogger` objects are created (or reused) for logging. The XSQL processor holds a reference to the `XSQLLogger` object returned by the factory for the duration of a page request. The processor uses it to log the start and end of each page request by invoking the `logRequestStart()` and `logRequestEnd()` methods.

The `XSQLLogger` interface is:

    public interface XSQLLogger {
       public void logRequestStart(XSQLPageRequest env) ;
       public void logRequestEnd(XSQLPageRequest env);
    }

The classes in Example 25-25 and Example 25-26 show a trivial implementation of a custom logger. The `XSQLLogger` implementation in Example 25-25 notes the time the page request started. It then logs the page request end by printing the name of the page request and the elapsed time to `System.out`.

The factory implementation is shown in Example 25-26.

To register a custom logger factory, edit the `XSQLConfig.xml` file and provide the name of your custom logger factory class as the content to the `/XSQLConfig/processor/logger/factory` element. Example 25-27 shows this technique.

By default, `<logger>` section is commented out. There is no default logger.

Example 25-25 SampleCustomLogger Class

    package example;
    import oracle.xml.xsql.*;
    public class SampleCustomLogger implements XSQLLogger  {
      long start = 0;
      public void logRequestStart(XSQLPageRequest env) {
        start = System.currentTimeMillis();
      }
      public void logRequestEnd(XSQLPageRequest env) {
        long secs = System.currentTimeMillis() - start;
        System.out.println("Request for " + env.getSourceDocumentURI()
                            + " took "+ secs + "ms");
      }
    }

Example 25-26 SampleCustomLoggerFactory Class

    package example;
    import oracle.xml.xsql.*;
    public class SampleCustomLoggerFactory implements XSQLLoggerFactory {
      public XSQLLogger create(XSQLPageRequest env) {
        return new SampleCustomLogger();
      }
    }

Example 25-27 Registering a Custom Logger Factory

    <XSQLConfig>
        :
      <processor>
             :
          <logger>
             <factory>example.SampleCustomLoggerFactory</factory>
          </logger>
             :
       </processor>
    </XSQLConfig>
