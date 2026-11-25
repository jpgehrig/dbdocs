Oracle object types are user-defined types that make it possible to model real-world entities, such as customers and purchase orders, as objects in the database.

New object types can be created from any built-in database types and any previously created object types, object references, and collection types. Object types can work with complex data, such as images, audio, and video. Oracle Database stores metadata for user-defined types in a schema that is available to SQL, PL/SQL, Java, and other languages.

Object types and related object-oriented features, such as varrays and nested tables, provide higher-level ways to organize and access data in the database. Underneath the object layer, data is still stored in columns and tables, but you can work with the data in terms of the real-world entities that make the data meaningful. Instead of thinking in terms of columns and tables when you query the database, you can simply select entities that you have created, such as customers and purchase orders.

You can begin to use object-oriented features while continuing to work with most of your data relationally, or you use to an object-oriented approach entirely.

Object types are also known as user-defined types or ADTs. [Oracle Database PL/SQL Language Reference](../lnpls/main-features-pl-sql.md) generally refers to them as ADTs.
