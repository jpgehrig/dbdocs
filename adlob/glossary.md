## Glossary

### BFILE

A Large Object datatype that is a binary file residing in the file system, outside of the database data files and tablespace. Note that the `BFILE` datatype is also referred to as an external LOB in some documentation.

**Parent topic:** Glossary

### Binary Large Object (BLOB)

A Large Object datatype that has content consisting of binary data and is typically used to hold unstructured data. The `BLOB` datatype is included in the category Persistent LOBs because it resides in the database.

**Parent topic:** Glossary

### BLOB

See Binary Large Object (BLOB) .

**Parent topic:** Glossary

### Character Large Object (CLOB)

The LOB data type that has content consisting of character data in the database character set. A CLOB can be indexed and searched by the Oracle Text search engine.

**Parent topic:** Glossary

### CLOB

See Character Large Object (CLOB).

**Parent topic:** Glossary

### data interface

Data interface is a generic term referring to whichever interface is in use, to query the database or to update the database.

**Parent topic:** Glossary

### deduplication

Deduplication enables Oracle Database to automatically detect duplicate LOB data and conserve space by only storing one copy (if storage parameter is `SECUREFILE`).

**Parent topic:** Glossary

### DBFS

The Database Filesystem, which is visible to end-users as the client-side API (`dbms_dbfs_content`).

**Parent topic:** Glossary

### DBFS Link

Database File System Links (DBFS Links) are references from SecureFiles LOBs to data stored outside the segment where the SecureFiles LOB resides.

**Parent topic:** Glossary

### external LOB

A Large Object datatype that is stored outside of the database tablespace. The `BFILE` datatype is the only external LOB datatype. See also `BFILE`.

**Parent topic:** Glossary

### internal persistent LOB

A large object (LOB) that is stored in the database in a `BLOB`/`CLOB`/`NCLOB` column.

**Parent topic:** Glossary

### introspect

To examine attributes or value of an object.

**Parent topic:** Glossary

### Large Objects (LOBs)

Large Objects include the following SQL datatypes: `BLOB`, `CLOB`, `NCLOB`, and `BFILE`. These datatypes are designed for storing data that is large in size. See also `BFILE`, Binary Large Object, Character Large Object, and National Character Large Object.

**Parent topic:** Glossary

### LOB

See Large Objects (LOBs)

**Parent topic:** Glossary

### LOB attribute

A large object datatype that is a field of an object datatype. For example a `CLOB` field of an object type.

**Parent topic:** Glossary

### LOB value

The actual data stored by the Large Object. For example, if a `BLOB` stores a picture, then the value of the `BLOB` is the data that makes up the image.

**Parent topic:** Glossary

### mount point

The path where the Database File System is mounted. Note that all file systems owned by the database user are seen at the mount point.

**Parent topic:** Glossary

### National Character Large Object

The LOB data type that has content consisting of Unicode character data in the database national character set. An `NCLOB` can be indexed and searched by the Oracle Text search engine.

**Parent topic:** Glossary

### NCLOB

See National Character Large Object.

**Parent topic:** Glossary

### persistent LOB

A `BLOB`, `CLOB`, or `NCLOB` that is stored in the database. A persistent LOB instance can be selected out of a table and used within the scope of your application. The ACID (atomic, consistent, isolated, durable) properties of the instance are maintained just as for any other column type. Persistent LOBs are sometimes also referred to as internal persistent LOBs or just, internal LOBs.

A persistent LOB can exist as a field of an object data type and an instance in a LOB-type column. For example a `CLOB` attribute of an instance of type `object`.

See also temporary LOB and external LOB.

**Parent topic:** Glossary

### SECUREFILE

LOB storage parameter that allows deduplication, encryption, and compression. The opposite parameter, that does not allow these features, is `BASICFILE`.

**Parent topic:** Glossary

### SPI

The DBFS Store Provider Interface, visible to end-users as the server-side SPI (`dbms_dbfs_content_spi`).

**Parent topic:** Glossary

### Store

A unified content repository, visible to the DBFS, and managed by a single store provider. The store itself may be a single relational table, a collection of tables, or even a collection of relational and non-relational entities (e.g., hierarchical stores like tapes and the cloud, elements inside an XML file, components of HDF-style documents, and so on.

**Parent topic:** Glossary

### Store Provider

An entity, embodied as a P L/SQL package, that implements the DBFS SPI.

**Parent topic:** Glossary

### tablespace

A database storage unit that groups related logical structures together.

**Parent topic:** Glossary

### temporary LOB

A `BLOB`, `CLOB`, or `NCLOB` that is accessible and persists only within the application scope in which it is declared. A temporary LOB does not exist in database tables.

**Parent topic:** Glossary
