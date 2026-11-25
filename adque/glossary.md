### ADT

Abstract data type.

### API

See application programming interface.

### application programming interface

The calling conventions by which an application program accesses operating system and other services.

### approximate CSCN

An approximate system change number value, based on the current SCN of the database when a transaction that has enqueued messages into a commit-time queue is committed.

### asynchronous

A process in a multitasking system is asynchronous if its execution can proceed independently in the background. Other processes can be started before the asynchronous process has finished. The opposite of synchronous.

### BFILE

An external binary file that exists outside the database tablespaces residing in the operating system.

### binary large object

A large object datatype whose content consists of binary data. This data is considered raw, because its structure is not recognized by the database.

### BLOB

See binary large object.

### broadcast

A publish/subscribe mode in which the message producer does not know the identity of any message consumer. This mode is similar to a radio or television station.

### buffered queue

Buffered queues support queuing of messages with buffered attributes (buffered messages) and materialize them in memory. If the memory devoted to a buffered message is required for a newer message, or if a buffered message has exceeded a stipulated duration in memory, then that buffered message is swapped to the underlying queue table. The memory for buffered messages comes from a separate pool called the streams pool. Buffered messages cannot be recovered if the database is bounced. Messages that have no buffered attributes set are queued as persistent messages in the underlying persistent queue.

### canonical

The usual or standard state or manner of something.

### character large object

The large object datatype whose value is composed of character data corresponding to the database character set. A character large object can be indexed and searched by the Oracle Text search engine.

### CLOB

See character large object.

### ConnectionFactory

A ConnectionFactory encapsulates a set of connection configuration parameters that has been defined by an administrator. A client uses it to create a connection with a Java Message Service provider.

### commit-time queue

A queue in which messages are ordered by their approximate CSCN values.

### consumer

A user or application that can dequeue messages.

### data manipulation language

Data manipulation language (DML) statements manipulate database data. For example, querying, inserting, updating, and deleting rows of a table are all DML operations; locking a table or view and examining the execution plan of an SQL statement are also DML operations.

### Database Configuration Assistant

An Oracle Database tool for creating and deleting databases and for managing database templates.

### DBCA

See Database Configuration Assistant.

### dequeue

To retrieve a message from a queue

### DML

See data manipulation language.

### enqueue

To place a message in a queue. The JMS equivalent of enqueue is send.

### exception queue

Messages are transferred to an exception queue if they cannot be retrieved and processed for some reason.

### IDAP

See Internet Data Access Presentation.

### index-organized table

Unlike an ordinary table whose data is stored as an unordered collection, data for an index-organized table is stored in a B-tree index structure sorted on a primary key. Besides storing the primary key column values of an index-organized table row, each index entry in the B-tree stores the nonkey column values as well.

### Internet Data Access Presentation

The Simple Object Access Protocol (SOAP) specification for Oracle Database Advanced Queuing operations. IDAP defines the XML message structure for the body of the SOAP request. An IDAP-structured message is transmitted over the Internet using HTTP(S).

### Inter-process Communication

Exchange of data between one process and another, either within the same computer or over a network. It implies a protocol that guarantees a response to a request.

### IOT

See index-organized table.

### IPC

See Inter-process Communication.

### Java Database Connectivity

An industry-standard Java interface for connecting to a relational database from a Java program, defined by Sun Microsystems.

### Java Message Service

A messaging standard defined by Sun Microsystems, Oracle, IBM, and other vendors. JMS is a set of interfaces and associated semantics that define how a JMS client accesses the facilities of an enterprise messaging product.

### Java Naming and Directory Interface

A programming interface from Sun for connecting Java programs to naming and directory services.

### Java Virtual Machine

The Java interpreter that converts the compiled Java bytecode into the machine language of the platform and runs it. JVMs can run on a client, in a browser, in a middle tier, on an intranet, on an application server such as Oracle Application Server 10g, or in a database server such as Oracle Database 10g.

### JDBC

See Java Database Connectivity.

### JDBC driver

The vendor-specific layer of Java Database Connectivity that provides access to a particular database. Oracle Database provides three JDBC drivers--Thin, OCI, and KPRB.

### JMS

See Java Message Service.

### JMS connection

An active connection of a client to its JMS provider, typically an open TCP/IP socket (or a set of open sockets) between a client and a provider's service daemon.

### JMS message

JMS messages consist of a header, one or more optional properties, and a message payload.

### JMS session

A single threaded context for producing and consuming messages.

### JMS topic

Equivalent to a multiconsumer queue in the other Oracle Database Advanced Queuing interfaces.

### JNDI

See Java Naming and Directory Interface.

### Jnnn

Job queue process

### JServer

The Java Virtual Machine that runs within the memory space of Oracle Database.

### JVM

See Java Virtual Machine

### large object

The class of SQL datatype consisting of BFILE, BLOB, CLOB, and NCLOB objects.

### LDAP

See Lightweight Directory Access Protocol

### Lightweight Directory Access Protocol

A standard, extensible directory access protocol. It is a common language that LDAP clients and servers use to communicate. The framework of design conventions supporting industry-standard directory products, such as the Oracle Internet Directory.

### LOB

See large object

### local consumer

A local consumer dequeues the message from the same queue into which the producer enqueued the message.

### logical change record

An object with a specific format that describes a database change, captured from the redo log by a capture process or user application. Capture processes enqueue messages containing logical change records (LCRs) only into `ANYDATA` queues. For improved performance, these LCRs are always stored in a buffered queue.

### message

The smallest unit of information inserted into and retrieved from a queue. A message consists of control information (metadata) and payload (data).

### multicast

A publish/subscribe mode in which the message producer knows the identity of each consumer. This mode is also known as point-to-multipoint.

### national character large object

The large object datatype whose value is composed of character data corresponding to the database national character set.

### NCLOB

See national character large object.

### nonpersistent

Nonpersistent queues store messages in memory. They are generally used to provide an asynchronous mechanism to send notifications to all users that are currently connected. Nonpersistent queues are deprecated in Oracle Database Advanced Queuing 10g Release 2 (10.2). Oracle recommends that you use buffered messaging instead.

### nontransactional

Allowing enqueuing and dequeuing of only one message at a time.

### object type

An object type encapsulates a data structure along with the functions and procedures needed to manipulate the data. When you define an object type using the `CREATE TYPE` statement, you create an abstract template that corresponds to a real-world object.

### OCI

See Oracle Call Interface.

### Oracle JMS

See Oracle Java Message Service.

### OLTP

See Online Transaction Processing.

### Online Transaction Processing

Online transaction processing systems are optimized for fast and reliable transaction handling. Compared to data warehouse systems, most OLTP interactions involve a relatively small number of rows, but a larger group of tables.

### Oracle Call Interface

An application programming interface that enables data and schema manipulation in Oracle Database.

### Oracle Java Message Service

Oracle Java Message Service (Oracle JMS) provides a Java API for Oracle Database Advanced Queuing based on the Java Message Service (JMS) standard. Oracle JMS supports the standard JMS interfaces and has extensions to support the Oracle Database Advanced Queuing administrative operations and other Oracle Database Advanced Queuing features that are not a part of the standard.

### producer

A user or application that can enqueue messages.

### propagation

Copying messages from one queue to another (local or remote) queue.

### publish/subscribe

A type of messaging in which a producer enqueues a message to one or more multiconsumer queues, and then the message is dequeued by several subscribers. The published message can have a wide dissemination mode called broadcast or a more narrowly aimed mode called multicast.

### QMNC

Queue monitor coordinator. It dynamically spawns slaves qXXX depending on the system load. The slaves do various background tasks.

### QMNn

Queue monitor process.

### queue

The abstract storage unit used by a messaging system to store messages.

### queue table

A database table where queues are stored. Each queue table contains a default exception queue.

### recipient

An agent authorized by the enqueuer or queue administrator to retrieve messages. The enqueuer can explicitly specify the consumers who can retrieve the message as recipients of the message. A queue administrator can specify a default list of recipients who can retrieve messages from a queue. A recipient specified in the default list is known as a subscriber. If a message is enqueued without specifying the recipients, then the message is sent to all the subscribers. Specific messages in a queue can be directed toward specific recipients, who may or may not be subscribers to the queue, thereby overriding the subscriber list.

If only the name of the recipient is specified, then the recipient must dequeue the message from the queue in which the message was enqueued. If the name and an address of the recipient are specified with a protocol value of 0, then the address should be the name of another queue in the same database or another installation of Oracle Database. If the recipient's name is `NULL`, then the message is propagated to the specified queue in the address and can be dequeued by any subscriber of the queue specified in the address. If the protocol field is nonzero, then the name and address are not interpreted by the system, and the message can be dequeued by a special consumer.

### remote consumer

A remote consumer dequeues from a queue that is different from the queue where the message was enqueued.

### result cache

A Result Cache can be defined as a cache of results of an evaluation for a set of argument values. In case of rules engine a result cache refers to cache of results pertaining to Rule Set, Rule and Independent Expression evaluations given certain input arguments

### rules

Boolean expressions that define subscriber interest in subscribing to messages. The expressions use syntax similar to the `WHERE` clause of a SQL query and can include conditions on: message properties (currently priority and correlation identifier), user data properties (object payloads only), and functions. If a rule associated with a subscriber evaluates to `TRUE` for a message, then the message is sent to that subscriber even if the message does not have a specified recipient.

### rules engine

Oracle Database software that evaluates rules. Rules are database objects that enable a client to perform an action when an event occurs and a condition is satisfied. Rules are similar to conditions in WHERE clauses of SQL queries. Both user-created applications and Oracle Database features, such as Oracle Database Advanced Queuing, can be clients of the rules engine.

### schema

A collection of database objects, including logical structures such as tables, views, sequences, stored procedures, synonyms, indexes, clusters, and database links. A schema has the name of the user who controls it.

### send

The JMS equivalent of enqueue.

### servlet

A Java program that runs as part of a network service and responds to requests from clients. It is typically an HTTP server.

### SGA

See System Global Area.

### sharded queue

A single logical queue that is divided into multiple, independent, physical queues through system-maintained partitioning.

### Simple Object Access Protocol

A minimal set of conventions for invoking code using XML over HTTP defined by World Wide Web Consortium.

### SOAP

See Simple Object Access Protocol.

### subscriber

An agent authorized by a queue administrator to retrieve messages from a queue.

### System Global Area

A group of shared memory structures that contain data and control information for one Oracle Database instance. The SGA and Oracle Database processes constitute an Oracle Database instance. Oracle Database automatically allocates memory for an SGA whenever you start an instance and the operating system reclaims the memory when you shut down the instance. Each instance has one and only one SGA.

### synchronous

Two or more processes are synchronous if they depend upon the occurrences of specific events such as common timing signals. The opposite of asynchronous.

### transactional

Allowing simultaneous enqueuing or dequeuing of multiple messages as part of a group.

### transformation

A mapping from one Oracle data type to another, represented by a SQL function that takes the source data type as input and returns an object of the target data type. A transformation can be specified during enqueue, to transform the message to the correct type before inserting it into the queue. It can be specified during dequeue to receive the message in the wanted format. If specified with a remote consumer, then the message is transformed before propagating it to the destination queue.

### user queue

A queue for normal message processing.

### VARRAY

An ordered set of data elements. All elements of a given array are of the same datatype. Each element has an index, which is a number corresponding to the element's position in the array. The number of elements in an array is the size of the array. Oracle Database allows arrays to be of variable size.

### wildcard

A special character or character sequence which matches any character in a string comparison.

### workflow

The set of relationships between all the activities in a project or business transaction, from start to finish. Activities are related by different types of trigger relations. Activities can be triggered by external events or by other activities.
