You need to take various issues into onsideration when working with `REF`s.

Topics:

- Storage Size of REFs

- Integrity Constraints for REF Columns

- Performance and Storage Considerations for Scoped REFs

- Performance Improvement for Object Access Using the WITH ROWID Option

### 9.3.1 Storage Size of REFs

A `REF` contains the following three logical components:

- OID of the object referenced. A system-generated OID is 16 bytes long. The size of a primary-key based OID depends on the size of the primary key column(s).

- OID of the table or view containing the object referenced, which is 16 bytes long.

- Rowid hint, which is 10 bytes long.

### 9.3.2 Integrity Constraints for REF Columns

Referential integrity constraints on `REF` columns ensure that there is a row object for the `REF`.

Referential integrity constraints on `REF`s create the same relationship as specifying a primary key/foreign key relationship on relational data. In general, you should use referential integrity constraints wherever possible because they are the only way to ensure that the row object for the `REF` exists. However, you cannot specify referential integrity constraints on `REF`s that are in nested tables.

### 9.3.3 Performance and Storage Considerations for Scoped REFs

A scoped `REF` is constrained to contain only references to a specified object table. You can specify a scoped `REF` when you declare a column type, collection element, or object type attribute to be a `REF`.

In general, you should use scoped `REF`s instead of unscoped `REF`s because scoped `REF`s are stored more efficiently. Whereas an unscoped `REF` takes at least 36 bytes to store (more if it uses rowids), a scoped `REF` is stored as just the OID of its target object and can take less than 16 bytes, depending on whether the referenced OID is system-generated or primary-key based. A system-generated OID requires 16 bytes; a primary key based (PK-based) OID requires enough space to store the primary key value, which may be less than 16 bytes. However, a `REF` to a PK-based OID, which must be dynamically constructed upon selection, may take more space in memory than a `REF` to a system-generated OID.

Besides requiring less storage space, scoped `REF`s often enable the optimizer to optimize queries that dereference a scoped `REF` into more efficient joins. This optimization is not possible for unscoped `REF`s because the optimizer cannot determine the containing table(s) for unscoped `REF`s at query-optimization time.

Unlike referential integrity constraints, scoped `REF`s do not ensure that the referenced row object exists; they only ensure that the referenced object table exists. Therefore, if you specify a scoped `REF` to a row object and then delete the row object, the scoped `REF` becomes a dangling `REF` because the referenced object no longer exists.

**Note:**

Referential integrity constraints are scoped implicitly.

Unscoped `REF`s are useful if the application design requires that the objects referenced be scattered in multiple tables. Because rowid hints are ignored for scoped `REF`s, you should use unscoped `REF`s if the performance gain of the rowid hint, as explained in the "Performance Improvement for Object Access Using the WITH ROWID Option", outweighs the benefits of the storage saving and query optimization of using scoped `REF`s.

#### 9.3.3.1 Indexing for Scoped REFs

You can build indexes on scoped `REF` columns using the `CREATE` `INDEX` command. This allows you to use the index to efficiently evaluate queries that dereference the scoped `REF`s. Such queries are turned into joins implicitly. For certain types of queries, Oracle can use an index on the scoped `REF` column to evaluate the join efficiently.

For example, suppose the object type `address_objtyp` is used to create an object table named `address_objtab`:

    CREATE TABLE address_objtab OF address_objtyp ;

A `people_reltab2` table can be created that has the same definition as the `people_reltab` table shown in [Example 9-2](general-storage-considerations-for-objects.md), except that a `REF` is used for the address. Next, an index can be created on the `address_ref` column.

Example 9-3 Creating an Index on Scoped REF Columns

    CREATE TABLE people_reltab2 (
      id            NUMBER(4)   CONSTRAINT pk_people_reltab2 PRIMARY KEY,
      name_obj      name_objtyp,
      address_ref   REF address_objtyp SCOPE IS address_objtab,
      phones_ntab   phone_ntabtyp)
      NESTED TABLE  phones_ntab STORE AS phone_store_ntab2 ;

    CREATE INDEX address_ref_idx ON people_reltab2 (address_ref) ;

The following query dereferences the `address_ref`:

    SELECT id FROM people_reltab2 p
       WHERE p.address_ref.state = 'CA' ;

When this query is executed, the `address_ref_idx` index is used to efficiently evaluate it. Here, `address_ref` is a scoped `REF` column that stores references to addresses stored in the `address_objtab` object table. Oracle implicitly transforms the preceding query into a query with a join:

    SELECT p.id FROM people_reltab2 p, address_objtab a
       WHERE p.address_ref = REF(a) AND a.state = 'CA' ;

The Oracle query optimizer might create a plan to perform a nested-loops join with `address_objtab` as the outer table and look up matching addresses using the index on the `address_ref` scoped `REF` column.

### 9.3.4 Performance Improvement for Object Access Using the WITH ROWID Option

If the `WITH` `ROWID` option is specified for a `REF` column, Oracle maintains the rowid of the object referenced in the `REF`. Then, Oracle can find the object referenced directly using the rowid contained in the `REF`, without the need to fetch the rowid from the OID index. Therefore, you use the `WITH` `ROWID` option to specify a rowid hint. Maintaining the rowid requires more storage space because the rowid adds 10 bytes to the storage requirements of the `REF`.

Bypassing the OID index search improves the performance of `REF` traversal (navigational access) in applications. The actual performance gain may vary from application to application depending on the following factors:

- How large the OID indexes are.

- Whether the OID indexes are cached in the buffer cache.

- How many `REF` traversals an application does.

The `WITH` `ROWID` option is only a hint because, when you use this option, Oracle checks the OID of the row object with the OID in the `REF`. If the two OIDs do not match, Oracle uses the OID index instead. The rowid hint is not supported for scoped `REF`s, for `REF`s with referential integrity constraints. .
