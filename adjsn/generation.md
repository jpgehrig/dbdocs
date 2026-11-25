SQL/JSON functions `json_object`, `json_array`, `json_objectagg`, and `json_arrayagg` are presented.

- Overview of SQL/JSON Generation Functions
  You can use SQL/JSON functions `json_object`, `json_array`, `json_objectagg`, and `json_arrayagg` to construct JSON data from non-JSON data in the database. The JSON data is returned as a SQL value.
- Handling of Input Values For SQL/JSON Generation Functions
  The SQL/JSON generation functions take SQL values as input and render them as JSON values inside the SQL value that is returned. How the input values are rendered as JSON depends on their SQL data type.
- SQL/JSON Function JSON_OBJECT
  SQL/JSON function `json_object` constructs JSON objects from the results of evaluating its argument SQL expressions.
- SQL/JSON Function JSON_ARRAY
  SQL/JSON function `json_array` constructs a JSON array from the results of evaluating its argument SQL expressions.
- SQL/JSON Function JSON_OBJECTAGG
  SQL/JSON function `json_objectagg` constructs a JSON object by aggregating information from multiple rows of a grouped SQL query as the object members.
- SQL/JSON Function JSON_ARRAYAGG
  SQL/JSON function `json_arrayagg` constructs a JSON array by aggregating information from multiple rows of a grouped SQL query as the array elements. The order of array elements reflects the query result order, by default, but you can use the `ORDER BY` clause to impose array element order.

**Parent topic:** [Generation of JSON Data](generation-of-json-data.md)

### 23.1 Overview of SQL/JSON Generation Functions

You can use SQL/JSON functions `json_object`, `json_array`, `json_objectagg`, and `json_arrayagg` to construct JSON data from non-JSON data in the database. The JSON data is returned as a SQL value.

These generation functions make it easy to construct JSON data directly from a SQL query. They allow non-JSON data to be represented as JSON objects and JSON arrays. You can generate complex, hierarchical JSON documents by nesting calls to these functions. Nested subqueries can generate JSON collections that represent one-to-many relationships.<sup>Foot 1</sup>

#### The Best Way to Construct JSON Data from Non-JSON Data

Alternatives to using the SQL/JSON generation functions are generally error prone or inefficient.

- Using string concatenation to generate JSON documents is error prone. In particular, there are a number of complex rules that must be respected concerning when and how to escape special characters, such as double quotation marks (`"`). It is easy to overlook or misunderstand these rules, which can result in generating incorrect JSON data.

- Reading non-JSON result sets from the database and using client-side application code to generate JSON data is typically quite inefficient, particularly due to network overhead. When representing one-to-many relationships as JSON data, multiple `SELECT` operations are often required, to collect all of the non-JSON data needed. If the documents to be generated represent multiple levels of one-to-many relationships then this technique can be quite costly.

The SQL/JSON generation functions do not suffer from such problems; they are designed for the job of constructing JSON data from non-JSON database data.

- They always construct well-formed JSON documents.

- By using SQL subqueries with these functions, you can generate an entire set of JSON documents using a single SQL statement, which allows the generation operation to be optimized.

- Because only the generated documents are returned to a client, network overhead is minimized: there is at most one round trip per document generated.

#### The SQL/JSON Generation Functions

- Functions `json_object` and `json_array` construct a JSON object or array, respectively. In the simplest case, `json_object` takes SQL name–value pairs as arguments, and `json_array` takes SQL values as arguments.

- Functions `json_objectagg`, and `json_arrayagg` are aggregate SQL functions. They transform information that is contained in the rows of a grouped SQL query into JSON objects and arrays, respectively. Evaluation of the arguments determines the number of object members and array elements, respectively; that is, the size of the result reflects the current queried data.

  For `json_objectagg` and `json_arrayagg`, the order of object members and array elements, respectively, is unspecified. For `json_arrayagg`, you can use an `ORDER BY` clause within the `json_arrayagg` invocation to control the array element order.

#### Result Returned by SQL/JSON Generation Functions

By default, the generated JSON data is returned from a generation function as a SQL `VARCHAR2` value. You can use the optional `RETURNING` clause to specify a `VARCHAR2` size or to specify a `CLOB` or `BLOB` return value instead. When `BLOB` is the return type, the character set is AL32UTF8.

#### Handling of Input Values For SQL/JSON Generation Functions

The SQL/JSON generation functions take SQL values as input and render them as JSON values inside the SQL value that is returned. How the input values are rendered as JSON depends on their SQL data type.

#### Optional Behavior For SQL/JSON Generation Functions

You can optionally specify a SQL `NULL`-handling clause, a `RETURNING` clause, and keyword `STRICT`.

- `NULL`-handling clause — Determines how a SQL `NULL` value resulting from input evaluation is handled.

  - `NULL ON NULL` — An input SQL `NULL` value is converted to JSON `null` for output. This is the default behavior for `json_object` and `json_objectagg`.

  - `ABSENT ON NULL` — An input SQL `NULL` value results in no corresponding output. This is the default behavior for `json_array` and `json_arrayagg`.

- `RETURNING` clause — The SQL data type used for the function return value. The default is `VARCHAR2(4000)`.

- `STRICT` keyword — If present, the returned JSON data is checked, to be sure it is well-formed. If `STRICT` is present and the returned data is not well-formed then an error is raised.

**Related Topics**

- Handling of Input Values For SQL/JSON Generation Functions
- [ISO 8601 Date and Time Support](json-path-expressions.md)

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/JSON_ARRAY.md) for information about SQL/JSON function `json_array`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_ARRAYAGG.md) for information about SQL/JSON function `json_arrayagg`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_OBJECT.md) for information about SQL/JSON function `json_object`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_OBJECTAGG.md) for information about SQL/JSON function `json_objectagg`

**Parent topic:** Generation of JSON Data with SQL/JSON Functions

### 23.2 Handling of Input Values For SQL/JSON Generation Functions

The SQL/JSON generation functions take SQL values as input and render them as JSON values inside the SQL value that is returned. How the input values are rendered as JSON depends on their SQL data type.

By default, a SQL `NUMBER` value is rendered in the output as a JSON number, a SQL `VARCHAR2` value is rendered as a JSON string, and so on. For example, by default the `VARCHAR2` value `'{}'` is rendered as the JSON string `"{}"`.

In some cases you know or expect that an input value in fact already represents JSON data, and you want to communicate this to the generation function so that the value is kept as is. For example, if the input is `'{}'` then you might want it interpreted (rendered) as an empty JSON object, `{}`, not as a JSON string, `"{}"`.

You can do this by adding keywords `FORMAT JSON` after an input expression to declare that the value that results from it is to be considered as already representing JSON data. Equivalently, you can apply SQL function `treat` with keywords `AS JSON` to a generation-function input value — the effect is the same as using `FORMAT JSON`.

In many cases Oracle can determine automatically that an input value is in fact JSON data, in which case the input is treated as if it were followed by an explicit `FORMAT JSON` declaration. This is the case, for instance, if the value expression is itself an invocation of a SQL/JSON generation function or function `json_query`.

If you do not specify `FORMAT JSON` for a given input value, and if Oracle cannot determine that the value is JSON data, then it is assumed to be ordinary (non-JSON) SQL data. In that case it is serialized as follows (any other SQL value raises an error):

- An instance of a user-defined SQL object type is rendered as a JSON object whose field names are taken from the object attribute names and whose field values are taken from the object attribute values (to which JSON generation is applied recursively).

- An instance of a SQL collection type is rendered as a JSON array whose element values are taken from the collection element values (to which JSON generation is applied recursively).

- A `VARCHAR2`, `CLOB`, or `NVARCHAR` value is wrapped in double quotation marks (`"`), and characters are escaped when necessary to conform to the JSON standard.

- A numeric value (`NUMBER`, `BINARY_DOUBLE`, or `BINARY_FLOAT`) is rendered as a JSON number. (It is not quoted.)

  The numeric values of positive and negative infinity, and values that are the undefined result of a numeric operation ("not a number" or `NaN`), cannot be expressed as JSON numbers. They are instead rendered as JSON strings: `"Inf"`, `"-Inf"`, and `"Nan"`, respectively.

- A `RAW` or `BLOB` value is rendered as a hexadecimal JSON string (with double quotation marks, `"`).

- A time-related value (`DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, `TIMESTAMP WITH LOCAL TIME ZONE`, `INTERVAL YEAR TO MONTH`, or `INTERVAL DAY TO SECOND`) is rendered in a supported ISO 8601 format, and the result is enclosed in double quotation marks (`"`).

- A `BOOLEAN` PL/SQL value is rendered as JSON `true` or `false`. (It is not quoted.)

- A `NULL` value is rendered as JSON `null`, regardless of the `NULL` data type. (It is not quoted.)

**Note:**

For data types `CLOB` and `BLOB`, an empty instance is distinguished from `NULL` and is rendered as an empty JSON string (`""`). But for data types `VARCHAR2`, `NVARCHAR2`, and `RAW`, Oracle SQL treats an empty (zero-length) value as `NULL`, so do not expect such a value to be rendered as a JSON string.

The format of an input argument can affect the format of the data that is returned by the function. In particular, if an input is declared or automatically determined to be of format JSON then it is treated as JSON data when computing the return value. Example 23-1 illustrates this — it explicitly uses `FORMAT JSON` to interpret the SQL string `"true"` as the JSON Boolean value `true`.

Example 23-1 Declaring an Input Value To Be JSON

This example specifies `FORMAT JSON` for SQL string values `'true'` and `'false'`, in order that the JSON Boolean values `true` and `false` are used. Without specifying `FORMAT JSON`, the values of field `hasCommission` would be the JSON string values `"true"` and `"false"`, not the JSON Boolean values `true` and `false`.

    SELECT json_object('name'          VALUE first_name || ' ' || last_name,
                       'hasCommission' VALUE
                         CASE WHEN commission_pct IS NULL THEN 'false' ELSE 'true'
                         END FORMAT JSON)
      FROM employees WHERE first_name LIKE 'W%';

    JSON_OBJECT('NAME'ISFIRST_NAME||''||LAST_NAME,'
    -----------------------------------------------
    {"name":"William Gietz","hasCommission":false}
    {"name":"William Smith","hasCommission":true}
    {"name":"Winston Taylor","hasCommission":false}

**Related Topics**

- Overview of SQL/JSON Generation Functions
- SQL/JSON Function JSON_OBJECT
- SQL/JSON Function JSON_ARRAY

**See Also:**

[https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=SQLRF-GUID-7B72E154-677A-4342-A1EA-C74C1EA928E6#GUID-7B72E154-677A-4342-A1EA-C74C1EA928E6](../sqlrf/Data-Types.md)

**Parent topic:** Generation of JSON Data with SQL/JSON Functions

### 23.3 SQL/JSON Function JSON_OBJECT

SQL/JSON function `json_object` constructs JSON objects from the results of evaluating its argument SQL expressions.

It can accept any number of arguments, each of which is one of the following:

- An explicit field name–value pair. Example: `answer : 42`.

  A name–value pair argument specifies an object member for the generated JSON object (except when the value expression evaluates to SQL `NULL` and the `ABSENT ON NULL` clause applies). The name and value are SQL expressions. The name expression must evaluate to a SQL string. The value expression must evaluate to a SQL value that can be rendered as a JSON value. The name and value expressions are separated by keyword `VALUE` or a colon (`:`).

  **Note:**

  Some client drivers might try to scan query text and identify bind variables before sending the query to the database. In some such cases a colon as name–value separator in `json_object` might be misinterpreted as introducing a bind variable. You can use keyword `VALUE` as the separator to avoid this problem (`'Name' VALUE Diderot`), or you can simply enclose the value part of the pair in parentheses: `'Name':(Diderot)`.

- A relational column name, possibly preceded by a table name or alias, or a view name followed by a dot (`.`). Example: `t1.address`.

  In this case, for a given row of data, the JSON-object member specified by the column-name argument has the column name as its field name and the column value as the field value.

  Regardless of whether it is quoted, the column name you provide is interpreted case-sensitively. For example, if you use `Email` as a column-name argument then the data in column `EMAIL` is used to produce object members with field name `Email` (not `EMAIL`).

- A table name or alias, or a view name, followed by a dot and an asterisk wildcard (`.*`). Example: `t1.*`. (The name or alias can also be prefixed by a database schema name, as in `myschema.t1.*`.)

  In this case, all columns of the table or view are used as input. Each is handled as if it were named explicitly. In particular, the column names are interpreted case-sensitively.

Alternatively, `json_object` accepts a single argument that is one of the following:

- An instance of a user-defined SQL object-type. Example: `json_object(my_sql_object_42)`.

  In this case, the resulting JSON-object field names are taken from the SQL object attribute names, and their values are taken from the SQL object attribute values (to which JSON generation is applied recursively).

- An asterisk wildcard (`*`). Example: `json_object(*)`.

  The wildcard acts as a shortcut to explicitly specifying all of the columns of a table or view, to produce the object members. The resulting JSON-object field names are the uppercase column names. You can use a wildcard with a table, a view, or a table alias, which is understood from the `FROM` list. The columns can be of any SQL data type.

  Note the difference between this case (`json_object(*)`) and the case described above, where the asterisk is preceded by an explicit table or view name (or table alias), followed by a dot: `json_object(``t.``*)`. In the `json_object(*)` case, the column names are not interpreted case-sensitively.

Another way of describing the use of asterisk wildcards with `json_object` is to say that it follows what is allowed for wildcards in a SQL `SELECT` list.

Just as for SQL/JSON condition `is json`, you can use keywords `STRICT` and `WITH UNIQUE KEYS` with functions `json_object` and `json_objectagg`. The behavior for each is the same as for `is json`.

Example 23-2 Using Name–Value Pairs with JSON_OBJECT

This example constructs a JSON object for each employee of table `hr.employees` (from standard database schema `HR`) whose salary is greater than 15000.

It passes explicit name–value pairs to specify the members of the JSON object. The object includes, as the value of its field `contactInfo`, an object with fields `mail` and `phone`.

    SELECT json_object('id'          : employee_id,
                       'name'        : first_name || ' ' || last_name,

                       'contactInfo' : json_object('mail'  : email,
                                                   'phone' : phone_number),
                       'hireDate'    : hire_date,
                       'pay'         : salary)
      FROM hr.employees
      WHERE salary > 15000;

    -- The query returns rows such as this (pretty-printed here for clarity):

    {"id"          : 101,
     "name"        : "Neena Kochhar",
     "contactInfo" : {"mail"  : "NKOCHHAR",
                      "phone" : "515.123.4568"},
     "hireDate"    : "21-SEP-05",
     "pay"         : 17000}

**Note:**

Because function `json_object` always returns JSON data, there is no need to specify `FORMAT JSON` for the value of input field `contactInfo`. But if the value of that field had been given as, for example, `'{"mail":' || email ', "phone":' || phone_number || '}'` then you would need to follow it with `FORMAT JSON` to have that string value interpreted as JSON data:

    "contactInfo" : '{"mail":' || email ', "phone":' || phone_number || '}'
    FORMAT JSON,

Example 23-3 Using Column Names with JSON_OBJECT

This example constructs a JSON object for the employee whose `employee_id` is `101`. The fields produced are named after the columns, but case-sensitively.

    SELECT json_object(last_name,
                       'contactInfo' : json_object(email, phone_number),
                       hire_date,
                       salary)
      FROM hr.employees
      WHERE employee_id = 101;

    -- The query returns rows such as this (pretty-printed here for clarity):

    {"last_name"   : "Kochhar",
     "contactInfo" : {"email"        : "NKOCHHAR",
                      "phone_number" : "515.123.4568"},
     "hire-date"   : "21-SEP-05",
     "salary"      : 17000}

Example 23-4 Using a Wildcard (\*) with JSON_OBJECT

This example constructs a JSON object for each employee whose salary is greater than 15000. Each column of table employees is used to construct one object member, whose field name is the (uppercase) column name. Note that a SQL `NULL` value results in a JSON field value of `null`.

    SELECT json_object(*)
      FROM hr.employees
      WHERE salary > 15000;

    -- The query returns rows such as this (pretty-printed here for clarity):

    JSON_OBJECT(*)
    --------------
    {"EMPLOYEE_ID":100,
     "FIRST_NAME":"Steven",
     "LAST_NAME":"King",
     "EMAIL":"SKING",
     "PHONE_NUMBER":"515.123.4567",
     "HIRE_DATE":"2003-06-17T00:00:00",
     "JOB_ID":"AD_PRES",
     "SALARY":24000,
     "COMMISSION_PCT":null,
     "MANAGER_ID":null,
     "DEPARTMENT_ID":90}

    {"EMPLOYEE_ID":101,
     "FIRST_NAME":"Neena",
     "LAST_NAME":"Kochhar",
     "EMAIL":"NKOCHHAR",
     "PHONE_NUMBER":"515.123.4568",
     "HIRE_DATE":"2005-09-21T00:00:00",
     "JOB_ID":"AD_VP",
     "SALARY":17000,
     "COMMISSION_PCT":null,
     "MANAGER_ID":100,
     "DEPARTMENT_ID":90}

    {"EMPLOYEE_ID":102,
     "FIRST_NAME":"Lex",
     "LAST_NAME":"De Haan",
     "EMAIL":"LDEHAAN",
     "PHONE_NUMBER":"515.123.4569",
     "HIRE_DATE":"2001-01-13T00:00:00",
     "JOB_ID":"AD_VP",
     "SALARY":17000,
     "COMMISSION_PCT":null,
     "MANAGER_ID":100,
     "DEPARTMENT_ID":90}

Example 23-5 Using JSON_OBJECT With ABSENT ON NULL

This example queries table `hr.locations` from standard database schema `HR` to create JSON objects with fields `city` and `province`.

The default `NULL`-handling behavior for `json_object` is `NULL ON NULL`.

In order to prevent the creation of a field with a `null` JSON value, this example uses `ABSENT ON NULL`. The `NULL` SQL value for column `state_province` when column `city` has value `'Singapore'` means that no `province` field is created for that location.

    SELECT JSON_OBJECT('city'     VALUE city,
                       'province' : state_province ABSENT ON NULL)
      FROM hr.locations
      WHERE city LIKE 'S%';

    JSON_OBJECT('CITY'ISCITY,'PROVINCE'ISSTATE_PROVINCEABSENTONNULL)
    ----------------------------------------------------------------
    {"city":"Southlake","province":"Texas"}
    {"city":"South San Francisco","province":"California"}
    {"city":"South Brunswick","province":"New Jersey"}
    {"city":"Seattle","province":"Washington"}
    {"city":"Sydney","province":"New South Wales"}
    {"city":"Singapore"}
    {"city":"Stretford","province":"Manchester"}
    {"city":"Sao Paulo","province":"Sao Paulo"}

Example 23-6 Using a User-Defined Object-Type Instance with JSON_OBJECT

This example creates table `po_ship` with column `shipping` of object type `shipping_t`. (It uses SQL/JSON function `json_value` to construct the `shipping_t` instances from JSON data — see [Example 18-3](function-JSON_VALUE.md).)

It then uses `json_object` to generate JSON objects from the SQL object-type instances in column `po_ship.shipping`.

(The query output is shown pretty-printed here, for clarity.)

    CREATE TABLE po_ship
      AS SELECT json_value(po_document, '$.ShippingInstructions'
                           RETURNING shipping_t)
      shipping
      FROM j_purchaseorder;

    DESCRIBE po_ship;

    Name      Null?   Type
    --------- ------- ----------
    SHIPPING          SHIPPING_T

    SELECT json_object(shipping) from po_ship;

    JSON_OBJECT(SHIPPING)
    ---------------------
    {"NAME":"Alexis Bull",
     "ADDRESS":{"STREET":"200 Sporting Green",
                "CITY":"South San Francisco"}}
    {"NAME":"Sarah Bell",
     "ADDRESS":{"STREET":"200 Sporting Green",
                "CITY":"South San Francisco"}}

**Related Topics**

- Overview of SQL/JSON Generation Functions
- Handling of Input Values For SQL/JSON Generation Functions

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/SELECT.md) for information about the `select_list` syntax

- [Oracle Database SQL Language Reference](../sqlrf/JSON_OBJECT.md) for information about SQL/JSON function `json_object`

- [Oracle Database SQL Language Reference](../sqlrf/Database-Object-Names-and-Qualifiers.md) for SQL identifier syntax

**Parent topic:** Generation of JSON Data with SQL/JSON Functions

### 23.4 SQL/JSON Function JSON_ARRAY

SQL/JSON function `json_array` constructs a JSON array from the results of evaluating its argument SQL expressions.

In the simplest case, the evaluated arguments you provide to `json_array` are SQL values that are converted to JSON values as the JSON array elements. The resulting array has an element for each argument you provide (except when an argument expression evaluates to SQL `NULL` and the `ABSENT ON NULL` clause applies). Array element order is the same as the argument order.

There are several kinds of SQL values that you can use as an argument to `json_array`, including scalar, collection instance, and user-defined object-type instance.

Example 23-7 Using JSON_ARRAY to Construct a JSON Array

This example constructs a JSON object for each employee job in database table `hr.jobs` (from standard database schema `HR`). The fields of the objects are the job title and salary range. The salary range (field `salaryRange`) is an array of two numeric values, the minimum and maximum salaries for the job. These values are taken from SQL columns `min_salary` and `max_salary`.

    SELECT json_object('title'       VALUE job_title,
                       'salaryRange' VALUE json_array(min_salary, max_salary))
      FROM jobs;

    JSON_OBJECT('TITLE'ISJOB_TITLE,'SALARYRANGE'ISJSON_ARRAY(MIN_SALARY,MAX_SALARY))
    --------------------------------------------------------------------------------
    {"title":"President","salaryRange":[20080,40000]}
    {"title":"Administration Vice President","salaryRange":[15000,30000]}
    {"title":"Administration Assistant","salaryRange":[3000,6000]}
    {"title":"Finance Manager","salaryRange":[8200,16000]}
    {"title":"Accountant","salaryRange":[4200,9000]}
    {"title":"Accounting Manager","salaryRange":[8200,16000]}
    {"title":"Public Accountant","salaryRange":[4200,9000]}
    {"title":"Sales Manager","salaryRange":[10000,20080]}
    {"title":"Sales Representative","salaryRange":[6000,12008]}
    {"title":"Purchasing Manager","salaryRange":[8000,15000]}
    {"title":"Purchasing Clerk","salaryRange":[2500,5500]}
    {"title":"Stock Manager","salaryRange":[5500,8500]}
    {"title":"Stock Clerk","salaryRange":[2008,5000]}
    {"title":"Shipping Clerk","salaryRange":[2500,5500]}
    {"title":"Programmer","salaryRange":[4000,10000]}
    {"title":"Marketing Manager","salaryRange":[9000,15000]}
    {"title":"Marketing Representative","salaryRange":[4000,9000]}
    {"title":"Human Resources Representative","salaryRange":[4000,9000]}
    {"title":"Public Relations Representative","salaryRange":[4500,10500]}

**Related Topics**

- Overview of SQL/JSON Generation Functions
- Handling of Input Values For SQL/JSON Generation Functions
- SQL/JSON Function JSON_OBJECT

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_ARRAY.md) for information about SQL/JSON function `json_array`

**Parent topic:** Generation of JSON Data with SQL/JSON Functions

### 23.5 SQL/JSON Function JSON_OBJECTAGG

SQL/JSON function `json_objectagg` constructs a JSON object by aggregating information from multiple rows of a grouped SQL query as the object members.

Unlike the case for SQL/JSON function `json_object`, where the number of members in the resulting object directly reflects the number of arguments, for `json_objectagg` the size of the resulting object reflects the current queried data. It can thus vary, depending on the data that is queried.

Example 23-8 Using JSON_OBJECTAGG to Construct a JSON Object

This example constructs a single JSON object from table `hr.departments` (from standard database schema `HR`) using field names taken from column `department_name` and field values taken from column `department_id`.

    SELECT json_objectagg(department_name VALUE department_id) FROM departments;

    -- The returned object is pretty-printed here for clarity.
    -- The order of the object members is arbitrary.

    JSON_OBJECTAGG(DEPARTMENT_NAMEISDEPARTMENT_ID)
    ----------------------------------------------
    {"Administration":        10,
     "Marketing":             20,
     "Purchasing":            30,
     "Human Resources":       40,
     "Shipping":              50,
     "IT":                    60,
     "Public Relations":      70,
     "Sales":                 80,
     "Executive":             90,
     "Finance":              100,
     "Accounting":           110,
     "Treasury":             120,
     "Corporate Tax":        130,
     "Control And Credit":   140,
     "Shareholder Services": 150,
     "Benefits":             160,
     "Manufacturing":        170,
     "Construction":         180,
     "Contracting":          190,
     "Operations":           200,
     "IT Support":           210,
     "NOC":                  220,
     "IT Helpdesk":          230,
     "Government Sales":     240,
     "Retail Sales":         250,
     "Recruiting":           260,
     "Payroll":              270}

**Related Topics**

- Overview of SQL/JSON Generation Functions

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_OBJECTAGG.md) for information about SQL/JSON function `json_objectagg`

**Parent topic:** Generation of JSON Data with SQL/JSON Functions

### 23.6 SQL/JSON Function JSON_ARRAYAGG

SQL/JSON function `json_arrayagg` constructs a JSON array by aggregating information from multiple rows of a grouped SQL query as the array elements. The order of array elements reflects the query result order, by default, but you can use the `ORDER BY` clause to impose array element order.

Unlike the case for SQL/JSON function `json_array`, where the number of elements in the resulting array directly reflects the number of arguments, for `json_arrayagg` the size of the resulting array reflects the current queried data. It can thus vary, depending on the data that is queried.

Example 23-9 Using JSON_ARRAYAGG to Construct a JSON Array

This example constructs a JSON object for each employee of table `hr.employees` (from standard database schema `HR`) who is a manager in charge of at least six employees. The objects have fields for the manager id number, manager name, number of employees reporting to the manager, and id numbers of those employees.

The order of the employee id numbers in the array is determined by the `ORDER BY` clause for `json_arrayagg`. The default direction for `ORDER BY` is `ASC` (ascending). The array elements, which are numeric, are in ascending numerical order.

    SELECT json_object('id'         VALUE mgr.employee_id,
                       'manager'    VALUE (mgr.first_name || ' '|| mgr.last_name),
                       'numReports' VALUE count(rpt.employee_id),
                       'reports'    VALUE json_arrayagg(rpt.employee_id
                                                        ORDER BY rpt.employee_id))
      FROM  employees mgr, employees rpt
      WHERE mgr.employee_id = rpt.manager_id
      GROUP BY mgr.employee_id, mgr.last_name, mgr.first_name
      HAVING count(rpt.employee_id) > 6;

    -- The returned object is pretty-printed here for clarity.

    JSON_OBJECT('ID'ISMGR.EMPLOYEE_ID,'MANAGER'VALUE(MGR.FIRST_NAME||''||MGR.LAST_NAME)
    -----------------------------------------------------------------------------------
    {"id":         100,
     "manager":    "Steven King",
     "numReports": 14,
     "reports":    [101,102,114,120,121,122,123,124,145,146,147,148,149,201]}

    {"id":         120,
     "manager":    "Matthew Weiss",
     "numReports": 8,
     "reports":    [125,126,127,128,180,181,182,183]}

    {"id":         121,
     "manager":    "Adam Fripp",
     "numReports": 8,
     "reports":    [129,130,131,132,184,185,186,187]}

    {"id":         122,
     "manager":    "Payam Kaufling",
     "numReports": 8,
     "reports":    [133,134,135,136,188,189,190,191]}

    {"id":         123,
     "manager":    "Shanta Vollman",
     "numReports": 8,
     "reports":    [137,138,139,140,192,193,194,195]}

    {"id":         124,
     "manager":    "Kevin Mourgos",
     "numReports": 8,
     "reports":    [141,142,143,144,196,197,198,199]}

Example 23-10 Generating JSON Objects with Nested Arrays Using a SQL Subquery

This example shows a SQL left outer join between two tables: `countries` and `regions`. Table `countries` has a foreign key, `region_id`, which joins with the primary key of table `regions`, also named `region_id`.

The query returns a JSON object for each row in table `regions`. Each of these region objects has a `countries` field whose value is an array of country objects — the countries in that region.

    SELECT json_object(
             'region'    : region_name,
             'countries' :
             (SELECT json_arrayagg(json_object('id'   : country_id,
                                               'name' : country_name))
                FROM countries c
                WHERE c.region_id = r.region_id))
      FROM regions r;

The query results in objects such as the following:

    {"region"    : "Europe",
     "countries" : [{"id"   : "BE",
                     "name" : "Belgium"},
                    {"id"   : "CH",
                     "name" : "Switzerland"},
                    {"id"   : "DE",
                     "name" : "Germany"},
                    {"id"   : "DK",
                     "name" : "Denmark"},
                    {"id"   : "FR",
                     "name" : "France"},
                    {"id"   : "IT",
                     "name" : "Italy"},
                    {"id"   : "NL",
                     "name" : "Netherlands"},
                    {"id"   : "UK",
                     "name" : "United Kingdom"}]}

**Related Topics**

- Overview of SQL/JSON Generation Functions

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_ARRAYAGG.md) for information about SQL/JSON function `json_arrayagg`

**Parent topic:** Generation of JSON Data with SQL/JSON Functions

------------------------------------------------------------------------



Footnote Legend

Footnote 1: The behavior of the SQL/JSON generation functions for JSON data is similar to that of the SQL/XML generation functions for XML data.
