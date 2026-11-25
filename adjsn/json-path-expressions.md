Oracle Database provides SQL access to JSON data using SQL/JSON path expressions.

- Overview of SQL/JSON Path Expressions
  Oracle Database provides SQL access to JSON data using SQL/JSON path expressions.
- SQL/JSON Path Expression Syntax
  SQL/JSON path expressions are matched by SQL/JSON functions and conditions against JSON data, to select portions of it. Path expressions can use wildcards and array ranges. Matching is case-sensitive.
- SQL/JSON Path Expression Item Methods
  The Oracle item methods available for a SQL/JSON path expression are described.
- ISO 8601 Date and Time Support
  International Standards Organization (ISO) standard 8601 describes an internationally accepted way to represent dates and times. Oracle Database supports many of the ISO 8601 date and time formats.
- Types in Comparisons
  Comparisons in SQL/JSON path-expression filter conditions are statically typed at compile time. If the effective types of the operands of a comparison are not known to be the same then an attempt is sometimes made to reconcile them by type-casting.

**Parent topic:** [Query JSON Data](query-json-data.md)

### 15.1 Overview of SQL/JSON Path Expressions

Oracle Database provides SQL access to JSON data using SQL/JSON path expressions.

JSON is a notation for JavaScript values. When JSON data is stored in the database you can query it using path expressions that are somewhat analogous to XQuery or XPath expressions for XML data. Similar to the way that SQL/XML allows SQL access to XML data using XQuery expressions, Oracle Database provides SQL access to JSON data using SQL/JSON path expressions.

SQL/JSON path expressions have a simple syntax. A path expression selects zero or more JSON values that match, or satisfy, it.

SQL/JSON condition `json_exists` returns true if at least one value matches, and false if no value matches. If a single value matches, then SQL/JSON function `json_value` returns that value if it is scalar and raises an error if it is non-scalar. If no value matches the path expression then `json_value` returns SQL `NULL`.

SQL/JSON function `json_query` returns all of the matching values, that is, it can return multiple values. You can think of this behavior as returning a sequence of values, as in XQuery, or you can think of it as returning multiple values. (No user-visible sequence is manifested.)

In all cases, path-expression matching attempts to match each step of the path expression, in turn. If matching any step fails then no attempt is made to match the subsequent steps, and matching of the path expression fails. If matching each step succeeds then matching of the path expression succeeds.

**Related Topics**

- SQL/JSON Path Expression Syntax

**Parent topic:** SQL/JSON Path Expressions

### 15.2 SQL/JSON Path Expression Syntax

SQL/JSON path expressions are matched by SQL/JSON functions and conditions against JSON data, to select portions of it. Path expressions can use wildcards and array ranges. Matching is case-sensitive.

You pass a SQL/JSON path expression and some JSON data to a SQL/JSON function or condition. The path expression is matched against the data, and the matching data is processed by the particular SQL/JSON function or condition. You can think of this matching process in terms of the path expression returning the matched data to the function or condition.

- Basic SQL/JSON Path Expression Syntax
  The basic syntax of a SQL/JSON path expression is presented. It is composed of a context-item symbol (`$`) followed by zero or more object, array, and descendant steps, each of which can be followed by a filter expression, followed optionally by a function step. Examples are provided.
- SQL/JSON Path Expression Syntax Relaxation
  The basic SQL/JSON path-expression syntax is relaxed to allow implicit array wrapping and unwrapping. This means that you need not change a path expression in your code if your data evolves to replace a JSON value with an array of such values, or vice versa. Examples are provided.

**Related Topics**

- [About Strict and Lax JSON Syntax](conditions-is-json-and-is-not-json.md)
- [Diagrams for Basic SQL/JSON Path Expression Syntax](diagrams-basic-sql-json-path-expression-syntax.md)

**Parent topic:** SQL/JSON Path Expressions

#### 15.2.1 Basic SQL/JSON Path Expression Syntax

The basic syntax of a SQL/JSON path expression is presented. It is composed of a context-item symbol (`$`) followed by zero or more object, array, and descendant steps, each of which can be followed by a filter expression, followed optionally by a function step. Examples are provided.

However, this basic syntax is extended by relaxing the matching of arrays and non-arrays against non-array and array patterns, respectively — see SQL/JSON Path Expression Syntax Relaxation.

Matching of data against SQL/JSON path expressions is case-sensitive.

- A SQL/JSON **basic path expression** (also called just a path expression here) is an absolute path expression or a relative path expression.

- An **absolute path expression** begins with a dollar sign (`$`), which represents the path-expression **context item**, that is, the JSON data to be matched. That data is the result of evaluating a SQL expression that is passed as argument to the SQL/JSON function. The dollar sign is followed by zero or more nonfunction steps, followed by an optional function step.

- A **relative path expression** is an at sign (`@`) followed by zero or more nonfunction steps, followed by an optional function step. It has the same syntax as an absolute path expression, except that it uses an at sign instead of a dollar sign (`$`).

  A relative path expression is used inside a filter expression (filter, for short). The at sign represents the path-expression **current filter item**, that is, the JSON data that matches the part of the (surrounding) path expression that precedes the filter containing the relative path expression. A relative path expression is matched against the current filter item in the same way that an absolute path expression is matched against the context item.

- A **nonfunction step** is an object step, an array step, or a descendant step, followed by an optional filter expression.

- A single **function step** is optional in a basic path expression (absolute or a relative). If present, it is the last step of the path expression. It is a period (`.`), sometimes read as "dot", followed by a SQL/JSON **item method**, followed by a left parenthesis (`(`) and then a right parenthesis (`)`). The parentheses can have whitespace between them (such whitespace is insignificant).

  The item method is applied to the data that is targeted by the rest of the same path expression, which precedes the function step. The item method is used to transform that data. The SQL function or condition that is passed the path expression as argument uses the transformed data in place of the targeted data.

- An **object step** is a period (`.`), followed by an object field name or an asterisk (`*`) wildcard, which stands for (the values of) all fields. A field name can be empty, in which case it must be written as `""` (no intervening whitespace). A nonempty field name must start with an uppercase or lowercase letter A to Z and contain only such letters or decimal digits (0-9), or else it must be enclosed in double quotation marks (`"`).

  An object step returns the value of the field that is specified. If a wildcard is used for the field then the step returns the values of all fields, in no special order.

- An **array step** is a left bracket (`[`) followed by either an asterisk (`*`) wildcard, which stands for all array elements, or one or more specific array indexes or range specifications separated by commas (`,`), followed by a right bracket (`]`). An error is raised if you use both an asterisk and either an array index or a range specification.

  In a path expression, **array indexing** is zero-based (0, 1, 2,...), as in the JavaScript convention for arrays. A **range specification** has the form `N` to `M`, where `N` and `M` are array indexes and `N` is strictly less than `M`.<sup>Foot 1</sup> An error is raised at query compilation time if `N` is not less than `M`.

  When indexes or range specifications are used, the array elements they collectively specify must be specified in ascending order, without repetitions, or else a compile-time error is raised. For example, an error is raised for each of `[3, 1 to 4]`, `[4, 2]`, `[2, 3 to 3]`, and `[2, 3, 3]`. Errors are raised on the first two because the order is not ascending, Errors are raised on the last two because of the repetition of array index `3` (which indexes the fourth array element, because of zero-based indexing).

  Similarly, the elements in the array value that results from matching are in ascending order, with no repetitions. If an asterisk is used in the path expression then all of the array elements are returned, in array order.

- A **descendant** step is two consecutive periods (`..`), sometimes read as "dot dot", followed by a field name (which has the same syntax as for an object step).

  It descends recursively into the objects or arrays that match the step immediately preceding it (or into the context item if there is no preceding step).

  At each descendant level, for each object and for each array element that is an object, it gathers the values of all fields that have the specified name. It returns all of the gathered field values.

  For example, consider this query and data:

      json_query(some_json_column, '$.a..z' WITH ARRAY WRAPPER)

      { "a" : { "b" : { "z" : 1 },
                "c" : [ 5, { "z" : 2 } ],
                "z" : 3 },
        "z" : 4 }

  The query returns an array, such as `[1,2,3]`, whose elements are `1`, `2`, and `3`. It gathers the value of each field `z` within the step that immediately precedes the dot dot (`..`), which is field `a`. The topmost field `z`, with value 4, is not matched because it is not within the value of field `a`.

  The value of field `a` is an object, which is descended into.

  - It has a field `z`, whose value (`3`) is gathered. It also has a field `b` whose value is an object, which is descended into to gather the value of its field `z`, which is `1`.

  - It also has a field `c` whose value is an array, which has an element that is an object with a field `z`, whose value (`2`) is gathered.

  The JSON values gathered are thus `3`, `1`, and `2`. They are wrapped in an array, in an undefined order. One of the possible return values is `[1,2,3]`.

- A **filter expression** (**filter**, for short) is a question mark (`?`) followed by a filter condition enclosed in parentheses (`()`). A filter is satisfied if its condition is satisfied, that is, returns true.

- A **filter condition** applies a predicate (Boolean function) to its arguments and is one of the following, where each of `cond`, `cond1`, and `cond2` stands for a filter condition.

  - `(`` ``cond`` ``)`: Parentheses are used for grouping, separating filter condition `cond` as a unit from other filter conditions that may precede or follow it.

  - `cond1`` ``&&`` ``cond2`: The conjunction (and) of `cond1` and `cond2`, requiring that both be satisfied.

  - `cond1`` ``||`` ``cond2`: The inclusive disjunction (or) of `cond1` and `cond2`, requiring that `cond1`, `cond2`, or both, be satisfied.

  - `! (`` ``cond`` ``)`: The negation of `cond`, meaning that `cond` must not be satisfied.

  - `exists (`, followed by a relative path expression, followed by `)`: The condition that the targeted data exists (is present).

  - A **comparison**, which is one of the following:

    - A relative path expression, followed by a comparison predicate, followed by either a JSON scalar value or a SQL/JSON variable.

    - Either a JSON scalar value or a SQL/JSON variable, followed by a comparison predicate, followed by a relative path expression.

    - A JSON scalar value, followed by a comparison predicate, followed by another JSON scalar value.

    - A relative path expression, followed by `has substring`, `starts with`, `like`, `like_regex`, or `eq_regex`, followed by either a JSON string or a SQL/JSON variable that is bound to a SQL string (which is automatically converted from the database character set to UTF8).

      - `has substring` means that the matching data value has the specified string as a substring.

      - `starts with` means that the matching data value has the specified string as a prefix.

      - `like` means that the JSON string data value matches the specified string, which is interpreted as a SQL `LIKE` pattern that uses SQL `LIKE4` character-set semantics. A percent sign (`%`) in the pattern matches zero or more characters. An underscore (`_`) matches a single character.

        **Note:**

        Unlike the case for SQL `LIKE`, there is no escape character for path-expression predicate `like`. Also, Oracle recommends that you avoid using character `` ` ``, GRAVE ACCENT (U+0060), in your `like` patterns — that character, also known sometimes as backquote or backtick, is reserved for future use.

      - `like_regex` means that the JSON string data value matches the specified string, which is interpreted as a SQL `REGEXP LIKE` regular expression pattern that uses SQL `LIKE4` character-set semantics.

        `like_regex` is exceptional among the pattern-matching comparisons, in that its pattern matches the empty JSON string (`""`).

      - `eq_regex` is just like `like_regex`, except for these two differences:

        - `eq_regex` matches its regular expression pattern against the entire JSON string data value — the full string must match the pattern for the comparison to be satisfied. `like_regex` is satisfied if any portion of the JSON string matches the pattern.

        - The `eq_regex` pattern does not match the empty JSON string (`""`).

      For all of these predicates, a pattern that is the empty string (`""`) matches data that is the empty string. And for all except `like_regex`, a pattern that is a nonempty string does not match data that is the empty string. For `like_regex` a nonempty pattern does match empty-string data.

    - A relative path expression, followed by `in`, followed by a value list, meaning that the value is one of those in the value list.

    A **comparison predicate** is `==`, `<>`, `!=`<sup>Foot 2</sup>, `<`, `<=`, `>=`, or `>`, meaning equals, does not equal, is less than, is less than or equal to, is greater than or equal to, and is greater than, respectively.

    A **SQL/JSON variable** is a dollar sign (`$`) followed by the name of a SQL identifier that is bound in a `PASSING` clause for `json_exists`.

  - A **value list** is `(`, followed by a list of one or more scalar values and SQL/JSON variables separated by commas (`,`), followed by `)`.

  The predicates that you can use in filter conditions are thus `&&`, `||`, `!`, `exists`, `==`, `<>`, `!=`, `<`, `<=`,` >=`, `>`, and `in`.

  As an example, the filter condition `(a || b) && (!(c) || d < 42)` is satisfied if both of the following criteria are met:

  - At least one of the filter conditions `a` and `b` is satisfied: `(a || b)`.

  - Filter condition `c` is not satisfied or the number `d` is less than or equal to 42, or both are true: `(!(c) || d < 42)`.

  Comparison predicate `!` has precedence over `&&`, which has precedence over `||`. You can always use parentheses to control grouping.

  Without parentheses for grouping, the preceding example would be `a || b && !(c) || d < 42`, which would be satisfied if at least one of the following criteria is met:

  - Condition `b && !(c)` is satisfied, which means that each of the conditions `b` and `!(c)` is satisfied (which in turn means that condition `c` is not satisfied).

  - Condition `a` is satisfied.

  - Condition `d < 42` is satisfied.

At least one side of a comparison must not be a SQL/JSON variable. The default type for a comparison is defined at compile time, based on the type(s) for the non-variable side(s). You can use a type-specifying item method to override this default with a different type. The type of your matching data is automatically converted, for the comparison, to fit the determined type (default or specified by item method). For example, `$.a > 5` imposes numerical comparison because `5` is a number, `$.a > "5"` imposes string comparison because `"5"` is a string.

**Tip:**

For queries that you use often, use a `PASSING` clause to define SQL bind variables, which you use as SQL/JSON variables in path expressions. This can improve performance by avoiding query recompilation when the (variable) values change.

For example, this query passes the value of bind variable `V1` as SQL/JSON variable `$V1`:

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$.LineItems.Part?(@.UPCCode == $V1)'
                        PASSING '85391628927' AS "V1");

**Note:**

For powerful full-text search, use Oracle SQL function `json_textcontains`, which requires that you create a JSON search index. As a less-powerful alternative, if you do not create a JSON search index, and you just want simple string pattern-matching in a filter condition, you can use any of the pattern-matching comparisons: `has substring`, `starts with`, `like`, `like_regex`, or `eq_regex`.

Here are some examples of path expressions, with their meanings spelled out in detail.

- `$` – The context item.

- `$``.friends` – The value of field `friends` of a context-item object. The dot (`.`) immediately after the dollar sign (`$`) indicates that the context item is a JSON object.

- `$.friends``[0]` – An object that is the first element of an array that is the value of field `friends` of a context-item object. The bracket notation indicates that the value of field `friends` is an array.

- `$.friends[0]``.name` – Value of field `name` of an object that is the first element of an array that is the value of field `friends` of a context-item object. The second dot (`.`) indicates that the first element of array `friends` is an object (with a `name` field).

- `$.friends``[*]``.name` – Value of field `name` of each object in an array that is the value of field `friends` of a context-item object.

- `$``.*[*]``.name` – Field `name` values for each object in an array value of a field of a context-item object.

- `$.friends[``3``, ``8 to 10``, ``12``]` – The fourth, ninth through eleventh, and thirteenth elements of an array `friends` (field of a context-item object). The elements must be specified in ascending order, and they are returned in that order: fourth, ninth, tenth, eleventh, thirteenth.

- `$.friends[3].cars` – The value of field `cars` of an object that is the fourth element of an array `friends`. The dot (`.`) indicates that the fourth element is an object (with a `cars` field).

- `$.friends[3]``.*` – The values of all of the fields of an object that is the fourth element of an array `friends`.

- `$.friends[3].cars[0].year` – The value of field `year` of an object that is the first element of an array that is the value of field `cars` of an object that is the fourth element of an array `friends`.

- `$.friends[3].cars[0]``?(@.year > 2016)` – The first object of an array `cars` (field of an object that is the fourth element of an array `friends`), provided that the value of its field `year` is, or can be converted to, a number greater than 2016. A `year` value such as `"2017"` is converted to the number `2017`, which satisfies the test. A `year` value such as `"recent"` fails the test — no match.

- `$.friends[3].cars[0]?(@.year``.number()`` > 2016)` – Same as the previous. Item method `number()` allows only a number or a string value that can be converted to a number, and that behavior is already provided by numeric comparison predicate `>`.

- `$.friends[3].cars[0]?(@.year``.numberOnly()`` > 2016)` – Same as the previous, but only if the `year` value is a number. Item method `numberOnly()` excludes a car with a `year` value that is a string numeral, such as `"2017"`.

- `$.friends[3]``?(@.addresses.city == "San Francisco")` – An object that is the fourth element of an array `friends`, provided that it has an `addresses` field whose value is an object with a field `city` whose value is the string `"San Francisco"`.

- `$.friends``[*]``.addresses``?(@city starts with "San ").zip` – Zip codes of all `addresses` of `friends`, where the name of the address `city` starts with "San ". (In this case the filter is not the last path step.)

- `$``..``zip` – All values of a `zip` field, anywhere, at any level.

- `$.friends[3]``?(@.addresses.city == "San Francisco" && @.addresses.state == "Nevada")` – Objects that are the fourth element of an array `friends`, provided that there is a match for an address with a `city` of `"San Francisco"` and there is a match for an address with a `state` of `"Nevada"`.

  Note: The filter conditions in the conjunction do not necessarily apply to the same object — the filter tests for the existence of an object with city San Francisco and for the existence of an object with state Nevada. It does not test for the existence of an object with both city San Francisco and state Nevada. See [Using Filters with JSON_EXISTS](condition-JSON_EXISTS.md).

- `$.friends[3]``.addresses``?(``@``.city == "San Francisco" && ``@``.state == "Nevada")` – An object that is the fourth element of array `friends`, provided that object has a match for `city` of `"San Francisco"` and a match for `state` of `"Nevada"`.

  Unlike the preceding example, in this case the filter conditions in the conjunction, for fields `city` and `state`, apply to the same `addresses` object. The filter applies to a given `addresses` object, which is outside it.

- `$.friends[3].addresses?(@.city == ``$CITY`` && @.state == ``$STATE``)` — Same as the previous, except the values used in the comparisons are SQL/JSON variables, `$CITY` and `$STATE`. The variable values would be provided by SQL bind variables `CITY` and `STATE`, in a `PASSING` clause. Use of variables in comparisons can improve performance by avoiding query recompilation.

**Related Topics**

- [Using Filters with JSON_EXISTS](condition-JSON_EXISTS.md)
- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- SQL/JSON Path Expression Item Methods
- SQL/JSON Path Expression Syntax Relaxation
- [Diagrams for Basic SQL/JSON Path Expression Syntax](diagrams-basic-sql-json-path-expression-syntax.md)
- [Wrapper Clause for SQL/JSON Query Functions JSON_QUERY and JSON_TABLE](clauses-used-in-functions-and-conditions-for-json.md)
- ISO 8601 Date and Time Support

**See Also:**

- [ISO 8601](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=wikipedia_iso8601) for information about the ISO date formats

- [Oracle Database SQL Language Reference](../sqlrf/Pattern-matching-Conditions.md) for information about SQL condition `REGEXP LIKE`

- [Oracle Database SQL Language Reference](../sqlrf/Pattern-matching-Conditions.md) for information about SQL condition `LIKE` and `LIKE4` character-set semantics

**Parent topic:** SQL/JSON Path Expression Syntax

#### 15.2.2 SQL/JSON Path Expression Syntax Relaxation

The basic SQL/JSON path-expression syntax is relaxed to allow implicit array wrapping and unwrapping. This means that you need not change a path expression in your code if your data evolves to replace a JSON value with an array of such values, or vice versa. Examples are provided.

Basic SQL/JSON Path Expression Syntax defines the basic SQL/JSON path-expression syntax. The actual path expression syntax supported relaxes that definition as follows:

- If a path-expression step targets (expects) an array but the actual data presents no array then the data is implicitly wrapped in an array.

- If a path-expression step targets (expects) a non-array but the actual data presents an array then the array is implicitly unwrapped.

This relaxation allows for the following abbreviation: `[*]` can be elided whenever it precedes the object accessor, `.`, followed by an object field name, with no change in effect. The reverse is also true: `[*]` can always be inserted in front of the object accessor,` .`, with no change in effect.

This means that the object step `[*].``prop`, which stands for the value of field `prop` of each element of a given array of objects, can be abbreviated as `.prop`, and the object step `.prop`, which looks as though it stands for the `prop` value of a single object, stands also for the `prop` value of each element of an array to which the object accessor is applied.

This is an important feature, because it means that you need not change a path expression in your code if your data evolves to replace a given JSON value with an array of such values, or vice versa.

For example, if your data originally contains objects that have field `Phone` whose value is a single object with fields `type` and `number`, the path expression `$.Phone.number`, which matches a single phone number, can still be used if the data evolves to represent an array of phones. Path expression `$.Phone.number` matches either a single phone object, selecting its number, or an array of phone objects, selecting the number of each.

Similarly, if your data mixes both kinds of representation — there are some data entries that use a single phone object and some that use an array of phone objects, or even some entries that use both — you can use the same path expression to access the phone information from these different kinds of entry.

Here are some example path expressions from section Basic SQL/JSON Path Expression Syntax, together with an explanation of equivalences.

- `$.friends` – The value of field `friends` of either:

  - The (single) context-item object.

  - (equivalent to `$[*].friends`) Each object in the context-item array.

- `$.friends[0].name` – Value of field `name` for any of these objects:

  - The first element of the array that is the value of field `friends` of the context-item object.

  - (equivalent to `$.friends.name`) The value of field `friends` of the context-item object.

  - (equivalent to `$[*].friends.name`) The value of field `friends` of each object in the context-item array.

  - (equivalent to `$[*].friends[0].name`) The first element of each array that is the value of field `friends` of each object in the context-item array.

  The context item can be an object or an array of objects. In the latter case, each object in the array is matched for a field `friends`.

  The value of field `friends` can be an object or an array of objects. In the latter case, the first object in the array is used.

- `$.*[*].name` – Value of field `name` for any of these objects:

  - An element of an array value of a field of the context-item object.

  - (equivalent to `$.*.name`) The value of a field of the context-item object.

  - (equivalent to `$[*].*.name`) The value of a field of an object in the context-item array.

  - (equivalent to `$[*].*[*].name`) Each object in an array value of a field of an object in the context-item array.

**Related Topics**

- Basic SQL/JSON Path Expression Syntax

**Parent topic:** SQL/JSON Path Expression Syntax

### 15.3 SQL/JSON Path Expression Item Methods

The Oracle item methods available for a SQL/JSON path expression are described.

An item method is applied to the JSON data that is targeted by (the rest of) the path expression terminated by that method. The method is used to transform that data. The SQL function or condition that is passed the path expression uses the transformed data in place of the targeted data. In some cases the application of an item method acts as a filter, removing the targeted data from the result set.

If an item-method conversion fails for any reason, such as its argument being of the wrong type, then the path cannot be matched (it refers to no data), and no error is raised. In particular, this means that such an error is not handled by an error clause in the SQL/JSON function or condition to which the path expression is passed.

#### Application of an Item Method to an Array

With the exception of item methods `size()` and `type()`, if an array is targeted by an item method then the method is applied to each of the array elements, not to the array itself. For example, `$.a.``method``()` applies item-method `method()` to each element of array `a`, to convert it and use it in place of the array. (This is similar, in effect, to the implied unwrapping of an array when a non-array is expected for an object step.) The resulting set of matches includes the converted array elements, not the targeted array.

For `json_query` or a `json_table` column expression with `json_query` semantics you can use a wrapper clause to capture all of the converted array-element values as an array. For example, this query:

    SELECT json_query('["alpha", 42, "10.4"]', '$[*].stringOnly()' WITH ARRAY WRAPPER) FROM dual;

returns this array (as a `VARCHAR2` value): `["alpha", "10.4"]`.

Item methods `size()` and `type()` are exceptional in this regard. When applied to an array they treat it as such, instead of acting on its elements. For example:

    SELECT json_value('[19, "Oracle", {"a":1},[1,2,3]]', '$.type()') FROM dual;

returns the single `VARCHAR2` value `'array'`.

#### Item-Method Descriptions

In the item-method descriptions here, in some cases a targeted JSON value is said to be interpreted as a value of a given SQL data type. This means that it is handled as if it were controlled by a `json_value` `RETURNING` clause with that SQL data type.

For example, item-method `string()` interprets its target as would `json_value` with clause `RETURNING VARCHAR2(4000)`. A Boolean value is thus treated by `string()` as `"true"` or `"false"`; a `null` value is treated as `"null"`; and a number is represented in a canonical string form.

Because some item methods interpret the targeted JSON data as if it were of a SQL data type, they can be used with `json_value` in place of a `RETURNING` clause, and they can be used with `json_table` in place of a column type specification. That is, the item methods can be used to specify the SQL data type for the extracted JSON data.

You can also use such item methods together with a `json_value` `RETURNING` clause or a `json_table` column type specification. What happens if the SQL data type to use for extracted JSON data is controlled by both an item method and either a `json_value` `RETURNING` clause or a `json_table` column type?

- If the two data types are compatible then the data type for the `RETURNING` clause or the column is used. For these purposes, `VARCHAR2` is compatible with both `VARCHAR2` and `CLOB`.

- If the data types are incompatible then a static, compile-time error is raised.

Table 15-1 Compatibility of Type-Conversion Item Methods and RETURNING Types

| Item Method                    | Compatible RETURNING Clause Data Types                                                  |
|:-------------------------------|:----------------------------------------------------------------------------------------|
| `string()` or `stringOnly()`   | `VARCHAR2` or `CLOB`, except that `string()` returns SQL `NULL` for a JSON `null` value |
| `number()` or `numberOnly()`   | `NUMBER`                                                                                |
| `date()`                       | `DATE`                                                                                  |
| `timestamp()`                  | `TIMESTAMP`                                                                             |
| `boolean()` or `booleanOnly()` | `VARCHAR2`                                                                              |

Using a `RETURNING` clause or a column specification, you can specify a length for character data and a precision and scale for numerical data. This lets you assign a more precise SQL data type for extraction than what is provided by an item method for target-data comparison purposes.

For example, if you use item method `string()` and `RETURNING VARCHAR2(150)` then the data type of the returned data is `VARCHAR2(150)`, not `VARCHAR2(4000)`.

The data-type conversion methods with “only” in their name are the same as the corresponding methods with names without “only”, except that the former convert only JSON values that are of the given type (e.g., `number`) to the related SQL data type (e.g. `NUMBER`). The methods without “only” in the name allow conversion, when possible, of any JSON value to the given SQL data type. (When an “only” method targets an array, the conversion applies to each array element, as usual.)

- `abs()`: The absolute value of the targeted JSON number. Corresponds to the use of SQL function `ABS`.

- `boolean()`: A SQL `VARCHAR2(20)` interpretation of the targeted JSON value.

- `booleanOnly()`: A SQL `VARCHAR2(20)` interpretation of the targeted JSON data, but only if it is a JSON Boolean value; otherwise, there is no match. Acts as a filter, allowing matches only for JSON Boolean values.

- `ceiling()`: The targeted JSON number, rounded up to the nearest integer. Corresponds to the use of SQL function `CEIL`.

- `date()`: A SQL date interpretation of the targeted JSON string. The targeted string data must be in one of the supported ISO 8601 formats; otherwise, there is no match.

- `double()`: A SQL `BINARY_DOUBLE` interpretation of the targeted JSON string or number.

- `floor()`: The targeted JSON number, rounded down to the nearest integer. Corresponds to the use of SQL function `FLOOR`.

- `length()`: The number of characters in the targeted JSON string, interpreted as a SQL `NUMBER`.

- `lower()`: The lowercase string that corresponds to the characters in the targeted JSON string.

- `number()`: A SQL `NUMBER` interpretation of the targeted JSON string or number.

- `numberOnly()`: A SQL `NUMBER` interpretation of the targeted JSON data, but only if it is a JSON number; otherwise, there is no match. Acts as a filter, allowing matches only for JSON numbers.

- `size()`: The number of elements in an array, or 1 for a scalar or an object. This item method can be used with `json_query`, in addition to `json_value` and `json_table`. If applied to data that is an array, no implicit iteration over the array elements occurs: the resulting value is just the number of array elements. (This is an exception to the rule of implicit iteration.)

- `string()`: A SQL `VARCHAR2(4000)` interpretation of the targeted scalar JSON value.

- `stringOnly()`: A SQL `VARCHAR2(4000)` interpretation of the targeted scalar JSON value, but only if it is a JSON string; otherwise, there is no match. Acts as a filter, allowing matches only for JSON strings.

- `timestamp()`: A SQL `TIMESTAMP` interpretation of the targeted JSON string. The targeted string data must be in one of the supported ISO 8601 formats; otherwise, there is no match. <sup>Foot 3</sup>

- `type()`: The name of the JSON data type of the targeted data, interpreted as a SQL `VARCHAR2(20)` value. This item method can be used with `json_query`, in addition to `json_value` and `json_table`. If applied to data that is an array, no implicit iteration over the array elements occurs: the resulting value is `"array"`. (This is an exception to the rule of implicit iteration.)

  - `"null"` for a value of `null`.

  - `"boolean"` for a value of `true` or `false`.

  - `"number"` for a number.

  - `"string"` for a string.

  - `"array"` for an array.

  - `"object"` for an object.

- `upper()`: The uppercase string that corresponds to the characters in the targeted JSON string.

Item methods `boolean()`, `booleanOnly()`, `date()`, `length()`, `lower()`, `number()`, `numberOnly()`, `string()`, `stringOnly()`, `timestamp()`, and `upper()` are Oracle extensions to the SQL/JSON standard. The other item methods, `abs()`, `ceiling()`, `double()`, `floor()`, `size()`, and `type()` are part of the standard.

**Related Topics**

- Basic SQL/JSON Path Expression Syntax
- ISO 8601 Date and Time Support
- Types in Comparisons
- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [SQL/JSON Function JSON_VALUE](function-JSON_VALUE.md)
- [SQL/JSON Function JSON_TABLE](function-JSON_TABLE.md)
- [Wrapper Clause for SQL/JSON Query Functions JSON_QUERY and JSON_TABLE](clauses-used-in-functions-and-conditions-for-json.md)

**Parent topic:** SQL/JSON Path Expressions

### 15.4 ISO 8601 Date and Time Support

International Standards Organization (ISO) standard 8601 describes an internationally accepted way to represent dates and times. Oracle Database supports many of the ISO 8601 date and time formats.

International Standards Organization (ISO) standard 8601 describes an internationally accepted way to represent dates and times. You can manipulate strings that are in the most common ISO 8601 date and time formats as proper Oracle Database date and time values. The ISO 8601 formats that are supported are essentially those that are numeric-only, language-neutral, and unambiguous.

This is the allowed syntax for dates and times:

- Date (only): `YYYY``-``MM``-``DD`

- Date with time: `YYYY``-``MM``-``DD``T``hh``:``mm``:``ss``[``.``s``[``s``[``s``[``s``[``s``[``s``]]]]][``Z``|(``+``|``-``)``hh``:``mm``]`

where:

- `YYYY` specifies the year, as four decimal digits.

- `MM` specifies the month, as two decimal digits, `00` to `12`.

- `DD` specifies the day, as two decimal digits, `00` to `31`.

- `hh` specifies the hour, as two decimal digits, `00` to `23`.

- `mm` specifies the minutes, as two decimal digits, `00` to `59`.

- `ss``[``.``s``[``s``[``s``[``s``[``s``]]]]]` specifies the seconds, as two decimal digits, `00` to `59`, optionally followed by a decimal point and 1 to 6 decimal digits (representing the fractional part of a second).

- `Z` specifies UTC time (time zone 0). (It can also be specified by `+00:00`, but not by `–00:00`.)

- `(``+``|``-``)hh``:``mm` specifies the time-zone as difference from UTC. (One of `+` or `–` is required.)

For a time value, the time-zone part is optional. If it is absent then UTC time is assumed.

No other ISO 8601 date-time syntax is supported. In particular:

- Negative dates (dates prior to year 1 BCE), which begin with a hyphen (e.g. `–``2018–10–26T21:32:52`), are not supported.

- Hyphen and colon separators are required: so-called “basic” format, `YYYYMMDDThhmmss`, is not supported.

- Ordinal dates (year plus day of year, calendar week plus day number) are not supported.

- Using more than four digits for the year is not supported.

Supported dates and times include the following:

- `2018–10–26T21:32:52`

- `2018-10-26T21:32:52+02:00`

- `2018-10-26T19:32:52Z`

- `2018-10-26T19:32:52+00:00`

- `2018-10-26T21:32:52.12679`

Unsupported dates and times include the following:

- `2018-10-26T21:32` (if a time is specified then all of its parts must be present)

- `2018-10-26T``25``:32:52+02:00` (the hours part, 25, is out of range)

- `18-10-26T21:32` (the year is not specified fully)

**See Also:**

- [ISO 8601 standard](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=iso-8601)

- [ISO 8601 at Wikipedia](https://en.wikipedia.org/wiki/ISO_8601)

**Parent topic:** SQL/JSON Path Expressions

### 15.5 Types in Comparisons

Comparisons in SQL/JSON path-expression filter conditions are statically typed at compile time. If the effective types of the operands of a comparison are not known to be the same then an attempt is sometimes made to reconcile them by type-casting.

A SQL/JSON path expression targets JSON data, so the operands of a comparison are JSON values. Type comparison of JSON values is straightforward: JSON data types string, number, null, object, and array are mutually exclusive and incomparable.

But comparison operands are sometimes interpreted (essentially cast) as values of SQL data types. This is the case, for example, when some item methods, such as `number()`, are used. This section addresses the type-checking of such effective values.

You can prevent such type-casting by explicitly using one of the “only” item methods. For example, applying method `numberOnly()` prevents implicit type-casting to a number.

SQL is a statically typed language; types are determined at compile time. The same applies to SQL/JSON path expressions, and in particular to comparisons in filter conditions. This means that you get the same result for a query regardless of how it is evaluated — whether functionally or using features such as indexes, materialized views, and In-Memory scans.

To realize this:

- If the types of both operands are known and they are the same then type-checking is satisfied.

- If the types of both operands are unknown then a compile-time error is raised.

- If the type of one operand is known and the other is unknown then the latter operand is cast to the type of the former.

  For example, in `$.a?(@.b.c == 3)` the type of `$a.b.c` is unknown at compile time. The path expression is compiled as `$.a?(@.b.c.``number()`` == 3)`. At runtime an attempt is thus made to cast the data that matches `$a.b.c` to a number. A string value `"3"` would be cast to the number `3`, satisfying the comparison.<sup>Foot 4</sup>

- If the types of both operands are known and they are not the same then an attempt is made to cast the type of one to the type of the other. Details are presented below.

Comparison operands used in the following combinations are not reconciled; a compile-time error is raised.

- Number compared with any non-number type other than double.

- Double compared with any non-double type other than number.

- String compared with double.

- Boolean compared with any non-Boolean type, except for comparison with a string value of `'true'` or `'false'` (or any letter-case variants, such as `'tRUe'`).

- Date or timestamp compared with string, unless the string has a supported ISO 8601 format.

- Date compared with any non-date type other than string.

- Timestamp (with or without time zone) compared with any non-timestamp type other than string.

- JSON `null` compared with any type other than JSON `null`.

An attempt is made to reconcile comparison operands used in the following combinations, by type-casting. You can think of a type-casting item method being implicitly applied to one of the operands in order to make it type-compatible with the other operand.

- Number compared with double — `double()` is implicitly applied to the number to make it a double value.

- String value of `'true'` or `'false'` (or any letter-case variants, such as `'tRUe'`) compared with Boolean — `boolean()` is implicitly applied to the string to make it a Boolean value.

- String in a supported ISO 8601 format compared with date — `date()` is implicitly applied to the string to make it a date value. (Any time-zone component present is removed.)

- String in a supported ISO 8601 format compared with timestamp (with or without) time zone — `timestamp()` is implicitly applied to the string to make it a timestamp value. For this, the UTC time zone (Coordinated Universal Time, zero offset) is used as the default, taking into account any time zone specified in the string.

**Related Topics**

- SQL/JSON Path Expression Item Methods
- ISO 8601 Date and Time Support

**Parent topic:** SQL/JSON Path Expressions

------------------------------------------------------------------------



Footnote Legend

Footnote 1: The `to` in a range specification is sometimes informally called the array slice operator.
Footnote 2: `!=` is an Oracle alias for the SQL/JSON standard comparison predicate `<>`.
Footnote 3: Applying item method `timestamp()` to a supported ISO 8601 string `<ISO-STRING>` has the effect of SQL `sys_extract_utc(to_utc_timestamp_tz(``<ISO-STRING>``)`.
Footnote 4: To prevent such casting here, you can explicitly apply item method `numberOnly()`: `$.a?(@.b.c.``numberOnly()`` == 3)`. Data with a string value `"3"` would simply not match; it would be filtered out.
