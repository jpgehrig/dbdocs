Just as a view is a virtual table, an object view is a virtual object table. Each row in the view is an object: you can call its methods, access its attributes using the dot notation, and create a `REF` that points to it.

You can run object-oriented applications without converting existing tables to a different physical structure. To do this, you can use object views to prototype or transition to object-oriented applications because the data in the view can be taken from relational tables and accessed as if the table were defined as an object table.

Object views can be used like relational views to present only the data that you want users to see. For example, you might create an object view that presents selected data from an employee table but omits sensitive data about salaries.

Using object views can lead to better performance. Relational data that makes up a row of an object view traverses the network as a unit, potentially saving many round trips.

You can fetch relational data into the client-side object cache and map it into C structures or C++ or Java classes,so 3GL applications can manipulate it just like native classes. You can also use object-oriented features like complex object retrieval with relational data.

- You can query the data in new ways by synthesizing objects from relational data. You can view data from multiple tables by using object dereferencing instead of writing complex joins with multiple tables.

- You can pin the object data from object views and use the data in the client side object cache. When you retrieve these synthesized objects in the object cache by means of specialized object-retrieval mechanisms, you reduce network traffic.

- You gain great flexibility when you create an object model within a view, enabling you to continue developing the model. If you need to alter an object type, you can simply replace the invalidated views with a new definition.

- You do not place any restrictions on the characteristics of the underlying storage mechanisms by using objects in views. By the same token, you are not limited by the restrictions of current technology. For example, you can synthesize objects from relational tables which are parallelized and partitioned.

- You can create different complex data models from the same underlying data.

  **See Also:**

  - [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) for a complete description of SQL syntax and usage

  - [Oracle Database PL/SQL Language Reference](../lnpls/overview.md) for a complete discussion of PL/SQL capabilities

  - [Oracle Database Java Developer's Guide](../jjdev/Java-introduction.md) for a complete discussion of Java

  - [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md) for a complete discussion of those facilities
