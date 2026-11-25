You can construct pointers (`REF`s) to the row objects in an object view. Because the view data is not stored persistently, you must specify a set of distinct values to be used as object identifiers. Object identifiers allow you to reference the objects in object views and pin them in the object cache.

If the view is based on an object table or an object view, then there is already an object identifier associated with each row and you can reuse them. To do this, either omit the `WITH` `OBJECT` `IDENTIFIER` clause or specify `WITH` `OBJECT` `IDENTIFIER` `DEFAULT`.

However, if the row object is synthesized from relational data, you must choose some other set of values.

You can specify object identifiers based on the primary key. This turns the set of unique keys that identify the row object into an identifier for the object. These values must be unique within the rows selected out of the view, because duplicates would lead to problems during navigation through object references.

- Object views created with the `WITH` `OBJECT` `IDENTIFIER` Clause

  An object view created with the `WITH` `OBJECT` `IDENTIFIER` clause has an object identifier derived from the primary key.

  For example, note the definition of the object type `dept_t` and the object view `dept_view` described in "[Single-Level Collections in Object Views](nested-tables-and-varrays-used-in-object-views.md)".

  Because the underlying relational table has `deptno` as the primary key, each department row has a unique department number. In the view, the `deptno` column becomes the `deptno` attribute of the object type. Once you know that `deptno` is unique within the view objects, you can specify it as the object identifier.

- Object views created with the `WITH` `OBJECT` `IDENTIFIER` `DEFAULT` Clause

  If the `WITH` `OBJECT` `IDENTIFIER` `DEFAULT` clause is specified, the object identifier is either system-generated or primary-key based, depending on the underlying table or view definition.

**See Also:**

- "[Object Identifiers Used to Identify Row Objects](key-features-object-relational-model.md)" for a description of primary-key based and system-generated object identifiers

- See "[Storage Considerations for Object Identifiers (OIDs)](general-storage-considerations-for-objects.md)".
