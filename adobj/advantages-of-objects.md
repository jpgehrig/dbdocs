The object-type model, in general, is similar to the class mechanism found in C++ and Java.

Like classes, the reusability of objects makes it possible to develop database applications faster and more efficiently. By natively supporting object types in the database, Oracle Database enables application developers to directly access the data structures used by their applications.

Objects offer other advantages over a purely relational approach, such as:

- Objects Can Encapsulate Operations Along with Data

- Objects Are Efficient

- Objects Can Represent Part-Whole Relationships

### Objects Can Encapsulate Operations Along with Data

Database tables contain only data. Objects can include the ability to perform operations that are likely to be performed on that data.

Thus, an object such as a purchase order might include a method to calculate the cost of all the items purchased. Or a customer object might have methods to return the customer's buying history and payment pattern. An application can simply call the methods to retrieve the information.

### Objects Are Efficient

Using object types allows for greater efficiency:

- Object types and their methods are stored with the data in the database, so they are available for any application to use. Developers do not need to re-create similar structures and methods in every application. This also ensures that developers are using consistent standards.

- You can fetch and manipulate a set of related objects as a single unit. A single request to fetch an object from the server can retrieve other objects that are connected to it. When you reference a column of a SQL object type, you retrieve the whole object.

### Objects Can Represent Part-Whole Relationships

Object types allow you to represent part-whole relationships.

In a relational table for stock items, for example, a piston and an engine may have the same status. Using objects can reduce the need to represent pistons as parts of engines with complicated schemas of multiple tables with primary key-foreign key relationships. An object can have other objects as attributes, and the attribute objects can have their own object attributes too. An entire parts-list hierarchy can be built up in this way from interlocking object types.
