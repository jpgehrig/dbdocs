A list of error messages is provided to aid you in troubleshooting problems.

- Oracle JMS Error Messages

- Oracle AQ XML Servlet Error Messages

### Oracle JMS Error Messages

JMS-101 Invalid delivery mode (string)
Cause: The delivery mode is not supported

Action: The valid delivery mode is AQjmsConstants.PERSISTENT

JMS-102 Feature not supported (string)
Cause: This feature is not supported in the current release

Action: Self-explanatory

JMS-104 Message Payload must be specified
Cause: The message payload was null

Action: Specify a non-null payload for the message

JMS-105 Agent must be specified
Cause: AQjmsAgent object was null

Action: Specify a valid AQjmsAgent representing the remote subscriber

JMS-106 Cannot have more than one open Session on a JMSConnection
Cause: There is already one open JMS session on the connection. Cannot have more than one open session on a connection

Action: Close the open session and then open a new one

JMS-107 Operation not allowed on (string)
Cause: The specified operation is not allowed on this object

Action: Self-explanatory

JMS-108 Messages of type (string) not allowed with Destinations containing payload of type (string)
Cause: There was a mismatch between the message type being used and the payload type specified for the destination

Action: Use the message type that maps to the payload specified for the queue table that contains this destination

JMS-109 Class not found: (string)
Cause: The specified class was not found

Action: Make sure your `CLASSPATH` contains the class

JMS-110 Property (string) not writeable
Cause: An attempt was made to update a read-only message header field or property

Action: Self-explanatory

JMS-111 Connection must be specified
Cause: The connection object was null

Action: Specify a non-null JDBC connection

JMS-112 Connection is invalid
Cause: The JDBC connection is invalid

Action: Specify a non-null oracle JDBC connection

JMS-113 Connection is in stopped state
Cause: An attempt was made to receive messages on a connection that is in stopped state

Action: Start the connection

JMS-114 Connection is closed
Cause: An attempt was made to use a Connection that has been closed

Action: Create a new connection

JMS-115 Consumer is closed
Cause: An attempt was mode to use a Consumer that has been closed

Action: Create a new Message Consumer

JMS-116 Subscriber name must be specified
Cause: Subscriber name was null

Action: Specify a non-null subscription name

JMS-117 Conversion failed - invalid property type
Cause: An error occurred while converting the property to the requested type

Action: Use the method corresponding to the property data type to retrieve it

JMS-119 Invalid Property value
Cause: The property value specified is invalid

Action: Use the appropriate type of value for the property being set

JMS-120 Dequeue failed
Cause: An error occurred while receiving the message

Action: See message inside the JMSException and linked SQLException for more information

JMS-121 DestinationProperty must be specified
Cause: A null AQjmsDestinationProperty was specified while creating a queue/topic

Action: Specify a non-null AQjmsDestinationProperty for the destination

JMS-122 Internal error (string)
Cause: Internal error occurred

Action: Call Support

JMS-123 Interval must be at least (integer) seconds
Cause: An invalid interval was specified

Action: The interval must be greater than 30 seconds

JMS-124 Invalid Dequeue mode
Cause: Invalid dequeue mode was specified

Action: Valid Dequeue modes are AQConstants.DEQUEUE_BROWSE, AQConstants.DEQUEUE_REMOVE, AQConstants.DEQUEUE_LOCKED, AQConstants.DEQUEUE_REMOVE_NODATA

JMS-125 Invalid Queue specified
Cause: An invalid Queue object was specified

Action: Specify a valid Queue handle

JMS-126 Invalid Topic specified
Cause: An invalid Topic object was specified

Action: Specify a valid Topic handle

JMS-127 Invalid Destination
Cause: An invalid destination object was specified

Action: Specify a valid destination (Queue/Topic) object

JMS-128 Invalid Navigation mode
Cause: An invalid navigation mode was specified

Action: The valid navigation modes are AQjmsConstants.NAVIGATION_FIRST_MESSAGE, AQjmsConstants.NAVIGATION_NEXT_MESSAGE, AQjmsConstants.NAVIGATION_NEXT_TRANSACTION

JMS-129 Invalid Payload type
Cause: There was a mismatch between the message type being used and the payload type specified for the destination

Action: Use the message type that maps to the payload specified for the queue table that contains this destination. For ADT messages, use the appropriate CustomDatum factory to create the message consumer

JMS-130 JMS queue cannot be multi-consumer enabled
Cause: An attempt was made to get a AQ multi-consumer queue as a JMS queue

Action: JMS queues cannot be multi-consumer enabled

JMS-131 Session is closed
Cause: An attempt was made to use a session that has been closed

Action: Open a new session

JMS-132 Maximum number of properties (integer) exceeded
Cause: Maximum number of user defined properties for the message has been exceeded

Action: Self-explanatory

JMS-133 Message must be specified
Cause: Message specified was null

Action: Specify a non-null message

JMS-134 Name must be specified
Cause: Queue or Queue table Name specified was null

Action: Specify a non-null name

JMS-135 Driver (string) not supported
Cause: The specified driver is not supported

Action: Valid drivers are oci8 and thin. To use the kprb driver get the kprb connection using getDefaultConnection() and use the static createTopicConnection and createQueueConnection methods

JMS-136 Payload factory can only be specified for destinations with ADT payloads
Cause: A CustomDatumFactory was specified for consumers on destinations not containing ADT payloads

Action: This field must be set to null for destinations containing payloads of type SYS.AQ\$\_JMS_TEXT_MESSAGE, SYS.AQ\$\_JMS_BYTES_MESSAGE, SYS.AQ\$\_JMS_MAP_MESSAGE, SYS.AQ\$\_JMS_OBJECT_MESSAGE, SYS.AQ\$\_JMS_STREAM_MESSAGE

JMS-137 Payload factory must be specified for destinations with ADT payloads
Cause: CustomDatumFactory was not specified for destinations containing ADT payloads

Action: For destinations containing ADT messages, a CustomDatumFactory for a java class that maps to the SQL ADT type of the destination must be specified

JMS-138 Producer is closed
Cause: An attempt was made to use a producer that has been closed

Action: Create a new Message Producer

JMS-139 Property name must be specified
Cause: Property name was null

Action: Specify a non-null property name

JMS-140 Invalid System property
Cause: Invalid system property name specified.

Action: Specify one of the valid JMS system properties

JMS-142 JMS topic must be created in multi-consumer enabled queue tables
Cause: An attempt was made to create a JMS topic in a single-consumer queue table

Action: JMS topics can only be created in queue tables that are multi-consumer enabled

JMS-143 Queue must be specified
Cause: Null queue was specified

Action: Specify a non-null queue

JMS-144 JMS queue cannot be created in multiconsumer enabled queue tables
Cause: An attempt was made to create a JMS queue in a multi-consumer queue table

Action: JMS queues can only be created in queue tables that are not multi-consumer enabled

JMS-145 Invalid recipient list
Cause: The recipient list specified was empty

Action: Specify a recipient list with at least one recipient

JMS-146 Registration failed
Cause: An error occurred while registering the type in the type map

Action: Self-explanatory

JMS-147 Invalid ReplyTo destination type
Cause: The ReplyTo destination object type is invalid

Action: The ReplyTo destination must be of type AQjmsAgent

JMS-148 Property name size exceeded
Cause: The property name is greater than the maximum size

Action: Specify a property name that is less than 100 characters

JMS-149 Subscriber must be specified
Cause: Subscriber specified was null

Action: Specify a non-null subscriber

JMS-150 Property not supported
Cause: An attempt was made to use a property that is not supported

Action: Self-explanatory

JMS-151 Topics cannot be of type EXCEPTION
Cause: Topics cannot be of type AQjmsConstants.EXCEPTION

Action: Specify topics to be of type AQjmsConstants.NORMAL

JMS-153 Invalid System property type
Cause: The type of the value specified does not match the type defined for the system property being set

Action: Use the correct type for the setting the system property

JMS-154 Invalid value for sequence deviation
Cause: The sequence deviation is invalid

Action: Valid values are AQEnqueueOption.DEVIATION_BEFORE, AQEnqueueOption.DEVIATION_TOP

JMS-155 AQ Exception (string)
Cause: An error occurred in the AQ java layer

Action: See the message inside the JMSException and the linked exception for more information

JMS-156 Invalid Class (string)
Cause: Class specified is invalid

Action: Make sure your `CLASSPATH` has the specified class

JMS-157 IO Exception (string)
Cause: IO exception

Action: See message is JMSException for details

JMS-158 SQL Exception (string)
Cause: SQL Exception

Action: See message inside linked SQLException for details

JMS-159 Invalid selector (string)
Cause: The selector specified is either invalid or too long

Action: Check the syntax of the selector

JMS-160 EOF Exception (string)
Cause: EOF exception occurred while reading the byte stream

Action: Self-explanatory

JMS-161 MessageFormat Exception: (string)
Cause: An error occurred while converting the stream data to specified type

Action: Check the type of data expected on the stream and use the appropriate read method

JMS-162 Message not Readable
Cause: Message is in write-only mode

Action: Call the reset method to make the message readable

JMS-163 Message not Writeable
Cause: Message is in read-only mode

Action: Use the clearBody method to make the message writeable

JMS-164 No such element
Cause: Element with specified name was not found in the map message

Action: Self-explanatory

JMS-165 Maximum size of property value exceeded
Cause: The property value exceeded the maximum length allowed

Action: Values for JMS defined properties can be a maximum of length of 100, Values for User defined properties can have a maximum length of 2000

JMS-166 Topic must be specified
Cause: Topic specified was null

Action: Specify a non-null topic

JMS-167 Payload factory or Sql_data_class must be specified
Cause: Payload factory or Sql_data_class not specified for queues containing object payloads

Action: Specify a CustomDatumFactory or the SQLData class of the java object that maps to the ADT type defined for the queue.

JMS-168 Cannot specify both payload factory and sql_data_class
Cause: Both CustomDatumFactory and SQLData class were specified during dequeue

Action: Specify either the CustomDatumFactory or the SQLData class of the java object that maps to the ADT type defined for the queue.

JMS-169 Sql_data_class cannot be null
Cause: SQLData class specified is null

Action: Specify the SQLData class that maps to the ADT type defined for the queue

JMS-171 Message is not defined to contain (string)
Cause: Invalid payload type in message

Action: Check if the queue is defined to contain RAW or OBJECT payloads and use the appropriate payload type in the message

JMS-172 More than one queue table matches query (string)
Cause: More than one queue table matches the query

Action: Specify both owner and queue table name

JMS-173 Queue Table (string) not found
Cause: The specified queue table was not found

Action: Specify a valid queue table

JMS-174 Class must be specified for queues with object payloads\n. Use dequeue(deq_option,payload_fact) or dequeue(deq_option, sql_data_cl)
Cause: This dequeue method cannot be used to dequeue from queues with OBJECT payloads

Action: Use the either dequeue(deq_option, payload_fact) or dequeue(deq_option, sql_data_cl)

JMS-175 DequeueOption must be specified
Cause: DequeueOption specified is null

Action: Specify a non-null dequeue option

JMS-176 EnqueueOption must be specified
Cause: EnqueueOption specified is null

Action: Specify a non-null enqueue option

JMS-177 Invalid payload type: Use dequeue(deq_option) for raw payload queues
Cause: This method cannot be used to dequeue from queues with RAW payload

Action: Use the dequeue(deq_option) method

JMS-178 Invalid Queue name - (string)
Cause: The queue name specified is null or invalid

Action: Specify a queue name that is not null. The queue name must not be qualified with the schema name. The schema name must be specified as the value of the owner parameter

JMS-179 Invalid Queue Table name - (string)
Cause: The queue table name specified is null or invalid

Action: Specify a queue table name that is not null. The queue table name must not be qualified with the schema name. The schema name must be specified as the value of the owner parameter

JMS-180 Invalid Queue Type
Cause: Queue type is invalid

Action: Valid types are AQConstants.NORMAL or AQConstants.EXCEPTION

JMS-181 Invalid value for wait_time
Cause: Invalid value for wait type

Action: Wait time can be AQDequeueOption.WAIT_FOREVER, AQDequeueOption.WAIT_NONE or any value greater than 0

JMS-182 More than one queue matches query
Cause: More than one queue matches query

Action: Specify both the owner and name of the queue

JMS-183 No AQ driver registered
Cause: No AQDriver registered

Action: Make sure that the AQ java driver is registered. Use Class.forName("oracle.AQ.AQOracleDriver")

JMS-184 Queue object is invalid
Cause: The queue object is invalid

Action: The underlying JDBC connection may have been closed. Get the queue handle again

JMS-185 QueueProperty must be specified
Cause: AQQueueProperty specified is null

Action: Specify a non-null AQQueueProperty

JMS-186 QueueTableProperty must be specified
Cause: QueueTableProperty specified is null

Action: Specify a non-null AQQueueTableProperty

JMS-187 Queue Table must be specified
Cause: Queue Table specified is null

Action: Specify a non-null queue table

JMS-188 QueueTable object is invalid
Cause: The queue table object is invalid

Action: The underlying JDBC connection may have been closed. Get the queue table handle again

JMS-189 Byte array too small
Cause: The byte array given is too small to hold the data requested

Action: Specify a byte array that is large enough to hold the data requested or reduce the length requested

JMS-190 Queue (string) not found
Cause: The specified queue was not found

Action: Specify a valid queue

JMS-191 sql_data_cl must be a class that implements SQLData interface
Cause: The class specified does not support the java.sql.SQLData interface

Action: Self-explanatory

JMS-192 Invalid Visibility value
Cause: Visibility value specified is invalid

Action: Valid values areAQConstants.VISIBILITY_ONCOMMIT, AQConstants.VISIBILITY_IMMEDIATE

JMS-193 JMS queues cannot contain payload of type RAW
Cause: An attempt was made to create a JMS queue with RAW payload

Action: JMS queues/topics cannot contain RAW payload

JMS-194 Session object is invalid
Cause: Session object is invalid

Action: The underlying JDBC connection may have been closed. Create a new session

JMS-195 Invalid object type: object must implement CustomDatum or SQLData interface
Cause: Invalid object type specified

Action: Object must implement CustomDatum or SQLData interface

JMS-196 Cannot have more than one open QueueBrowser for the same destination on a JMS Session
Cause: There is already an open QueueBrowser for this queue on this session

Action: There cannot be more than one queue browser for the same queue in a particular session. Close the existing QueueBrowser and then open a new one

JMS-197 Agent address must be specified for remote subscriber
Cause: Address field is null for remote subscriber

Action: The address field must contain the fully qualified name of the remote topic

JMS-198 Invalid operation: Privileged message listener set for the Session
Cause: The client tried to use a message consumer to receive messages when the session message listener was set.

Action: Use the session's message listener to consume messages. The consumer's methods for receiving messages must not be used.

JMS-199 Registration for notification failed
Cause: Listener Registration failed

Action: See error message in linked Exception for details

JMS-200 Destination must be specified
Cause: Destination is null

Action: Specify a non-null destination

JMS-201 All Recipients in recipient_list must be specified
Cause: One or more elements in the recipient list are null

Action: All AQjmsAgents in the recipient list must be specified

JMS-202 Unregister for asynchronous receipt of messages failed
Cause: An error occurred while removing the registration of the consumer with the database for asynchronous receipt

Action: Check error message in linked exception for details

JMS-203 Payload Factory must be specified
Cause: Null Payload Factory was specified

Action: Specify a non null payload factory

JMS-204 An error occurred in the AQ JNI layer
Cause: JNI Error

Action: Check error message in linked exception for details

JMS-205 Naming Exception
Cause: Naming exception

Action: Check error message in linked exception for details

JMS-207 JMS Exception (string)
Cause: An error occurred in the JMS layer

Action: See the message inside the linked JMSException for more information

JMS-208 XML SQL Exception
Cause: An error occurred in the XML SQL layer

Action: See the message inside the linked AQxmlException for more information

JMS-209 XML SAX Exception
Cause: An error occurred in the XML SAX layer

Action: See the message inside the linked AQxmlException for more information

JMS-210 XML Parse Exception
Cause: An error occurred in the XML Parser layer

Action: See the message inside the linked AQxmlException for more information

JMS-220 Connection no longer available
Cause: Connection to the database no longer available.

Action: Comment: This may happen if the database/network/machine is not accessible. This may be a transient failure.

JMS-221 Free physical database connection unavailable in connection pool
Cause: A free physical database connection was not available in the OCI connection pool in order to perform the specified operation.

Action: Try performing the operation later

JMS-222: Invalid Payload factory type
Cause: Payload factory should be of CustomDatumFactory or ORADataFactory type.

Action: Use one of CustomDatumFactory/ORADataFactory types.

JMS-223: Payload factory must be null for destinations with Sys.AnyData payload - use typemap instead
Cause: A CustomDatumFactory/ORADataFactory was specifed for consumers on destinations containing SYS.ANYDATA payloads

Action: This field must be set to null for destinations containing payloads of type SYS.AnyData. The ORADataFactory(s) must be registered in the session's typemap

JMS-224: Typemap is invalid - must be populated with SQLType/OraDataFactory mappings to receive messages from Sys.AnyData destinations
Cause: The typemap of the session is null or empty. For destinations of tpye Sys.AnyData, the typemap must contain OraDataFactory objects for all possible types that may be stored in the queue/topic

Action: Use the AQjmsSession.getTypeMap() method get the typemap. Then use the put() method to register SQLType names and their corresponding OraDataFactory objects

JMS-225: Invalid JDBC driver - OCI driver must be used for this operation
Cause: Operations on Sys.AnyData queues/topics are not supported using this JDBC driver

Action: Use the JDBC OCI driver to receive messages from Sys.AnyData queues/topics

JMS-226: Header-only Message does not have a body
Cause: Header-only message does not have a body; the body cannot be cleared, changed, or queried.

Action: Do not access or modify the body of a read-only message.

JMS-227: Illegal attempt to commit on a non transacted JMS Session
Cause: Illegal attempt to invoke the commit method on a non transacted JMS Session

Action: Remove invocation of the commit method on the current JMS Session

JMS-228: Illegal attempt to rollback on a non transacted JMS Session
Cause: Illegal attempt to invoke the rollback method on a non transacted JMS Session

Action: Remove invocation of the rollback method on the current JMS Session

JMS-229: (string) must be specified
Cause: The specified parameter was null

Action: Specify a non-null value for the parameter

JMS-230: Illegal operation on durable subscription with active TopicSubscriber
Cause: Try to unsubscribe, change or create durable subscription while it has an active TopicSubscriber.

Action: Close the active TopicSubscriber and try again.

JMS-231: Consumers on temporary destination must belong to the same
Cause: The specified parameter was null

Action: Specify a non-null value for the parameter

JMS-232: An invalid user/password was specified for the JMS connection
Cause: Invalid user/password specified for connection

Action: Specify valid user/password for connection

JMS-233: The required subscriber information is not available
Cause: Try to retrieve subscriber information from a subscriber which was obtained with getDurableSubscriber method and had no corresponding information in the in-memory map.

Action: Do not retrieve subscriber information from such a subscriber

JMS-234: This operation is not allowed in the current messaging domain
Cause: Perform an operation that is not allowed in the current messaging domain

Action: Do not perform the operation in the current messaging domain

JMS-235: Can not link the durable subscriber name with a topic in unsubscribe method.
Cause: OJMS is unable to link the supplied durable subscriber name with a topic. This causes unsubscribe method to fail.

Action: Use other unsubscribe methods which the user can provide topic name.

JMS-236: OJMS encountered invalid OCI handles.
Cause: OJMS encountered invalid OCI handles when using JDBC OCI driver .

Action: Make sure the underlying JDBC connection is not closed while OJMS is still operating.

JMS-237: Can not start thread for message listener.
Cause: OJMS is unable to start a new thread for message listener.

Action: Check the thread proxy code if the thread was started by a user provided thread proxy.

JMS-238: Illegal attempt to recover on a transacted JMS Session
Cause: Illegal attempt to invoke the recover method on a transacted JMS Session

Action: Use rollback method instead of recover method on transacted JMS session.

JMS-239: Illegal attempt to call (string) method on a XASession.
Cause: Illegal attempt to invoke the commit or rollback method on a XASession

Action: Use JTA to commit or rollback a distributed transaction

JMS-240: Illegal attempt to call setClientID after other actions.
Cause: Illegal attempt to call Connection.setClientID method after other actions has been taken on this Connection

Action: set client ID before any other action on the Connection

JMS-241: Illegal attempt to delete temporary destination when there are consumers using it.
Cause: Illegal attempt to delete temporary destination while there are existing consumers still using it.

Action: close the consumers before deleting the temporary destination

JMS-242: Illegal attempt to enqueue message with both immediate visibility and three phase enqueue process.
Cause: Illegal attempt to enqueue message with both immediate visibility and three phase enqueue process.

Action: turn on the system property oracle.jms.useTemplobsForEnqueue

JMS-243: Topic (string) not found}
Cause: The specified topic was not found

Action: Specify a valid topic

### Oracle AQ XML Servlet Error Messages

JMS-400 Destination name must be specified
Cause: A null Destination name was specified

Action: Specify a non-null destination name

JMS-402 Class not found: {0}
Cause: The specified class was not found

Action: Make sure your `CLASSPATH` contains the class specified in the error message

JMS-403 IO Exception {0}
Cause: IO exception

Action: See the message inside the linked AQxmlException for more information

JMS-404 XML Parse Exception
Cause: An error occurred in the XML Parser layer

Action: See the message inside the linked AQxmlException for more information

JMS-405 XML SAX Exception
Cause: An error occurred in the XML SAX layer

Action: See the message inside the linked AQxmlException for more information

JMS-406 JMS Exception {0}
Cause: An error occurred in the JMS layer

Action: See the message inside the linked JMSException for more information

JMS-407 Operation not allowed on {0}
Cause: The specified operation is not allowed on this object

Action: Check that the user performing the operation has the required privileges

JMS-408 Conversion failed - invalid property type
Cause: An error occurred while converting the property to the requested type

Action: Use the method corresponding to the property data type to retrieve it

JMS-409 No such element
Cause: Element with specified name was not found in the map message

Action: Specify a valid element name

JMS-410 XML SQL Exception
Cause: An error occurred in the JDBC SQL layer

Action: See the message inside the linked SQLException for more information

JMS-411 Payload body cannot be null
Cause: An invalid body string or document was specified

Action: Specify a non-null body string or document for the payload

JMS-412 Byte conversion failed
Cause: An invalid username/password was specified

Action: Specify a non-null username and password

JMS-413 Autocommit not allowed for operation
Cause: The autocommit flag cannot be set for this operation

Action: Do not set the autocommit flag

JMS-414 Destination owner must be specified
Cause: A null Destination owner was specified

Action: Specify a non-null destination name

JMS-415 Invalid Visibility value
Cause: Visibility value specified is invalid

Action: Valid values are AQxmlConstants.VISIBILITY_ONCOMMIT, AQxmlConstants.VISIBILITY_IMMEDIATE

JMS-416 Invalid Dequeue mode
Cause: Invalid dequeue mode was specified

Action: Valid Dequeue modes are AQxmlConstants.DEQUEUE_BROWSE, AQxmlConstants.DEQUEUE_REMOVE, AQxmlConstants.DEQUEUE_LOCKED, AQxmlConstants.DEQUEUE_REMOVE_NODATA

JMS-417 Invalid Navigation mode
Cause: An invalid navigation mode was specified

Action: The valid navigation modes are:

- AQxmlConstants.NAVIGATION_FIRST_MESSAGE

- AQxmlConstants.NAVIGATION_NEXT_MESSAGE

- AQxmlConstants.NAVIGATION_NEXT_TRANSACTION

JMS-418 Invalid value for wait_time
Cause: Invalid value for wait type

Action: Wait time can be AQDequeueOption.WAIT_FOREVER, AQDequeueOption.WAIT_NONE, or any value greater than 0

JMS-419 Invalid ConnectionPoolDataSource
Cause: A null or invalid ConnectionPoolDataSource was specified

Action: Specify a valid OracleConnectionPoolDataSource object with the correct URL and user/password

JMS-420 Invalid value for cache_size
Cause: An invalid cache_size was specified

Action: Cache size must be greater than 0

JMS-421 Invalid value for cache_scheme
Cause: An invalid cache scheme was specified

Action: The valid cache schemes are:

- OracleConnectionCacheImpl.DYNAMIC_SCHEME

- OracleConnectionCacheImpl.FIXED_WAIT_SCHEME

JMS-422 Invalid tag - {0}
Cause: An invalid tag was encountered in the XML document

Action: Verify that the XML document conforms to the AQ schema

JMS-423 Invalid value
Cause: An invalid value was specified

Action: Verify that the value specified in the XML document conforms to those specified in the AQ schema

JMS-424 Invalid message header
Cause: The message header specified is null or invalid

Action: Specify a valid message header

JMS-425 Property name must be specified
Cause: Property name was null

Action: Specify a non-null property name

JMS-426 Property does not exist
Cause: Invalid property name specified. The property does not exist

Action: The property does not exist

JMS-427 Subscriber name must be specified
Cause: Subscriber name was null

Action: Specify a non-null subscription name

JMS-428 Valid message must be specified
Cause: Message was null

Action: Specify a non-null message

JMS-429 Register Option must be specified
Cause: Register option is null

Action: Specify a non-null Register Option

JMS-430 Database Link must be specified
Cause: DB Link is null

Action: Specify a non-null Register Option

JMS-431 Sequence Number must be specified
Cause: Register option is null

Action: Specify a non-null Register Option

JMS-432 Status must be specified
Cause: Status option is null

Action: Specify a non-null Register Option

JMS-433 User not authenticated
Cause: User is not authenticated

Action: Check that the user was authenticated by the webserver before connecting to the Servlet

JMS-434 Invalid data source
Cause: Data source is null or invalid

Action: Specify a valid data source for connecting to the database

JMS-435 Invalid schema location
Cause: Schema location is null or invalid

Action: Specify a valid URL for the schema

JMS-436 AQ Exception
Cause: An error occurred in the AQ java layer

Action: See the message inside the AQxmlException and the linked exception for more information

JMS-437 Invalid Destination
Cause: An invalid destination object was specified

Action: Specify a valid destination (Queue/Topic) object

JMS-438 AQ agent {0} not mapped to a valid database user
Cause: The AQ agent specified does not map to a database user which has privileges to perform the requested operation

Action: Use dbms_aqadm.enable_db_access to map the agent to a database user with the required queue privileges

JMS-439 Invalid schema document
Cause: The schema document specified is not valid

Action: Specify a valid URL for the schema document

JMS-440 Invalid operations - agent {0} maps to more than one database user
Cause: The AQ agent mapped to more than one database user in the same session

Action: Map the AQ agent to only one database user. Check the `aq$internet_users` view for database users that map to this agent.

JMS-441: {0} cannot be null
Cause: The specified parameter was null

Action: Specify a non-null value

JMS-442: Name and Address for Agent cannot be null
Cause: Both the name and address parameters were specified as null

Action: Specify a non-null value for the name or address

JMS-443: IMMEDIATE visibility mode not supported for this queue/topic
Cause: IMMEDIATE visibility mode not supported for JMS type queue/topic

Action: Use ON_COMMIT or the default visibility mode for JMS type queue/topic

JMS-444: This feature is not supported yet
Cause: The requested feature is not yet supported

Action: wait for future releases that support the feature.

JMS-445: Destination alias must be specified
Cause: A null Destination alias was specified

Action: Specify a non-null destination alias

JMS-446: Agent alias must be specified
Cause: A null Agent alias was specified

Action: Specify a non-null agent alias

JMS-447: error in accessing LDAP server
Cause: error in accessing the LDAP server

Action: check the LDAP server is up and the environment parameters provided to the servlet are correct

JMS-448: Invalid Content-Type
Cause: Invalid Content-Type

Action: Content-Type must be "text/xml" or "application/x-www-form-urlencoded" with parameter name "aqxmldoc"
