PL/SQL object types allow fine-grained programmatic construction and manipulation of In-Memory JSON data. You can introspect it, modify it, and serialize it back to textual JSON data.

The principal PL/SQL JSON object types are `JSON_ELEMENT_T`, `JSON_OBJECT_T`, `JSON_ARRAY_T`, and `JSON_SCALAR_T`. Another, less used object type is `JSON_KEY_LIST`, which is a varray of `VARCHAR2(4000)`. Object types are also called abstract data types (ADTs).

These JSON object types provide an In-Memory, hierarchical (tree-like), programmatic representation of JSON data that is stored in the database.<sup>Foot 1</sup>

You can use the object types to programmatically manipulate JSON data in memory, to do things such as the following:

- Check the structure, types, or values of existing JSON data. For example, check whether the value of a given object field satisfies certain conditions.

- Transform existing JSON data. For example, convert address or phone-number formats to follow a particular convention.

- Create JSON data using programming rules that match the characteristics of whatever the data represents. For example, if a product to be represented as a JSON object is flammable then include fields that represent safety information.

PL/SQL object-type instances are transient. To store the information they contain persistently, you must serialize them to `VARCHAR2` or LOB data, which you can then store in a database table or marshal to a database client such as Java Database Connectivity (JDBC).

You construct an object-type instance in memory either all at once, by parsing JSON text, or piecemeal, starting with an empty object or array instance and adding object members or array elements to it.

An unused object-type instance is automatically garbage-collected; you cannot, and need not, free up the memory used by an instance that you no longer need.

Typically, after you have constructed a PL/SQL object-type instance and perhaps made use of it programmatically in various ways, you serialize it to an instance of data type `VARCHAR2`, `CLOB`, or `BLOB`. That is, you convert the transient representation of JSON data in memory to a persistent representation in the database. (Alternatively, you might serialize it only as text to be printed out.)

### Relations Among the JSON Object Types

Type `JSON_ELEMENT_T` is the supertype of the other JSON object types: each of them extends it as a subtype. Subtypes `JSON_OBJECT_T` and `JSON_ARRAY_T` are used for JSON objects and arrays, respectively. Subtype `JSON_SCALAR_T` is used for scalar JSON values: strings, numbers, the Boolean values `true` and `false`, and the value `null`.

You can construct an instance of type `JSON_ELEMENT_T` only by parsing JSON text. Parsing creates a `JSON_ELEMENT_T` instance, which is an In-Memory representation of the JSON data. You cannot construct an empty instance of type `JSON_ELEMENT_T` or type `JSON_SCALAR_T`.

Types `JSON_OBJECT_T` and `JSON_ARRAY_T` each have a constructor function of the same name as the type, which you can use to construct an instance of the type: an empty (In-Memory) representation of a JSON object or array, respectively. You can then fill this object or array as needed, adding object members or array elements, represented by PL/SQL object-type instances.

You can cast an instance of `JSON_ELEMENT_T` to a subtype instance, using PL/SQL function `treat`. For example, `treat(elt AS JSON_OBJECT_T)` casts instance `elt` as a JSON object (instance of `JSON_OBJECT_T`).

### Parsing Function

Static function `parse` accepts an instance of type `VARCHAR2`, `CLOB`, or `BLOB` as argument, which it parses as JSON text to return an instance of type `JSON_ELEMENT_T`, `JSON_OBJECT_T`, or `JSON_ARRAY_T`.

### Serialization Methods

Parsing accepts input JSON data as text and returns an instance of a PL/SQL JSON object type. Serialization does essentially the opposite: you apply it to a PL/SQL object representation of JSON data and it returns a textual representation of that object. The serialization methods have names that start with prefix `to_`. For example, method `to_string()` returns a string (`VARCHAR2`) representation of the JSON object-type instance you apply it to.

Most serialization methods are member functions. For serialization as a `CLOB` or `BLOB` instance, however, there are two forms of the methods: a member function and a member procedure. The member function accepts no arguments. It creates a temporary LOB as the serialization destination. The member procedure accepts a LOB `IN OUT` argument (`CLOB` instance for method `to_clob`, `BLOB` for method `to_blob`). You can thus pass it the LOB (possibly empty) that you want to use for the serialized representation.

### Getter and Setter Methods

Types `JSON_OBJECT_T` and `JSON_ARRAY_T` have getter and setter methods, which obtain and update, respectively, the values of a given object field or a given array element position.

There are two kinds of getter method:

- Method `get()` returns a reference to the original object to which you apply it, as an instance of type `JSON_ELEMENT_T`. That is, the object to which you apply it is passed by reference: If you then modify the returned `JSON_ELEMENT_T` instance, your modifications apply to the original object to which you applied `get()`.

- Getter methods whose names have the prefix `get_` return a copy of any data that is targeted within the object or array to which they are applied. That data is passed by value, not reference.

  For example, if you apply method `get_string()` to a `JSON_OBJECT_T` instance, passing a given field as argument, it returns a copy of the string that is the value of that field. If you apply `get_string()` to a `JSON_ARRAY_T` instance, passing a given element position as argument, it returns a copy of the string at that position in the array.

Like the serialization methods, most getter methods are member functions. But methods `get_clob()` and `get_blob()`, which return the value of a given object field or the element at a given array position as a `CLOB` or `BLOB` instance, have two forms (like the serialization methods `to_clob()` and `to_blob()`): a member function and a member procedure. The member function accepts no argument other than the targeted object field or array position. It creates and returns a temporary LOB instance. The member procedure accepts also a LOB `IN OUT` argument (`CLOB` for `get_clob`, `BLOB` for `get_blob`). You can thus pass it the (possibly empty) LOB instance to use.

The setter methods are `put()`, `put_null()`, and (for `JSON_ARRAY_T` only) `append()`. These update the object or array instance to which they are applied, setting the value of the targeted object field or array element. Note: The setter methods modify the existing instance, instead of returning a modified copy of it.

Method `append()`adds a new element at the end of the array instance. Method `put_null()` sets an object field or array element value to JSON `null`.

Method `put()` requires a second argument (besides the object field name or array element position), which is the new value to set. For an array, `put()` also accepts an optional third argument, `OVERWRITE`. This is a `BOOLEAN` value (default `FALSE`) that says whether to replace an existing value at the given position.

- If the object already has a field of the same name then `put()` replaces that value with the new value.

- If the array already has an element at the given position then, by default, `put()` shifts that element and any successive elements forward (incrementing their positions by one) to make room for the new element, which is placed at the given position. But if optional argument `OVERWRITE` is present and is `TRUE`, then the existing element at the given position is simply replaced by the new element.

### Introspection Methods

Type `JSON_ELEMENT_T` has introspection methods that you can use to determine whether an instance is a JSON object, array, scalar, string, number, or Boolean, or whether it is the JSON value `true`, `false`, or `null`. The names of these methods begin with prefix `is_`. They are predicates, returning a `BOOLEAN` value.

It also has introspection method `get_size()`, which returns the number of members of a `JSON_OBJECT_T` instance and the number of elements of a `JSON_ARRAY_T` instance (it returns 1 for a `JSON_SCALAR_T` instance).

Type `JSON_ELEMENT_T` also has introspection methods `is_date()` and `is_timestamp()`, which test whether an instance represents a date or timestamp. JSON has no native types for dates or timestamps; these are typically representing using JSON strings. But if a `JSON_ELEMENT_T` instance is constructed using SQL data of SQL data type `DATE` or `TIMESTAMP` then this type information is kept for the PL/SQL object representation.

Date and timestamp data is represented using PL/SQL object type `JSON_SCALAR_T`, whose instances you cannot construct directly. You can, however, add such a value to an object (as a field value) or an array (as an element) using method `put()`. Retrieving it using method `get()` returns a `JSON_SCALAR_T` instance.

Types `JSON_OBJECT_T` and `JSON_ARRAY_T` have introspection method `get_type()`, which returns the JSON type of the targeted object field or array element (as a `VARCHAR2` instance). Type `JSON_OBJECT_T` also has introspection methods `has()`, which returns `TRUE` if the object has a field of the given name, and `get_keys()`, which returns an instance of PL/SQL object type `JSON_KEY_LIST`, which is a varray of type `VARCHAR2(4000)`. The varray contains the names of the fields<sup>Foot 2</sup> <sup>Foot 2</sup> present in the given `JSON_OBJECT_T` instance. 

### Other Methods

Types `JSON_OBJECT_T` and `JSON_ARRAY_T` have the following methods:

- `remove()` — Remove the object member with the given field or the array element at the given position.

- `clone()` — Create and return a (deep) copy of the object or array to which the method is applied. Modifying any part of this copy has no effect on the original object or array.

Type `JSON_OBJECT_T` has method `rename_key()`, which renames a given object field.<sup>Foot 2</sup> If the new name provided already names an existing field then an error is raised.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_ARRAY_T`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_ELEMENT_T`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_OBJECT_T` and `JSON_KEY_LIST`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_SCALAR_T`

**Related Topics**

- [Using PL/SQL Object Types for JSON](using-PLSQL-object-types-for-JSON.md)

**Parent topic:** [PL/SQL Object Types for JSON](pl-sql-object-types-for-json.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1: This is similar to what is available for XML data using the Document Object Model (DOM), a language-neutral and platform-neutral object model and API for accessing the structure of XML documents that is recommended by the World Wide Web Consortium (W3C).
Footnote 2: An object field is sometimes called an object “key”.
