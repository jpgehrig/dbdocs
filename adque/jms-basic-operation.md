The following topics describe the basic operational [Java Message Service](glossary.md) (JMS) administrative interface to Oracle Database Advanced Queuing (AQ).

- EXECUTE Privilege on DBMS_AQIN

- Registering a ConnectionFactory

- Unregistering a Queue/Topic ConnectionFactory

- Getting a QueueConnectionFactory or TopicConnectionFactory

- Getting a Queue or Topic in LDAP

- Creating a Non-Sharded Queue Table

- Creating a Queue

- Getting a Non-Sharded Queue Table

- Granting and Revoking Privileges

- Managing Destinations

- Propagation Schedules

### EXECUTE Privilege on DBMS_AQIN

Users should never directly call methods in the `DBMS_AQIN` package, but they do need the `EXECUTE` privilege on `DBMS_AQIN`. Use the following syntax to accomplish this:

    GRANT EXECUTE ON DBMS_AQIN to user;

### Registering a ConnectionFactory

You can register a [ConnectionFactory](glossary.md) four ways:

- Registering Through the Database Using JDBC Connection Parameters

- Registering Through the Database Using a JDBC URL

- Registering Through LDAP Using JDBC Connection Parameters

- Registering Through LDAP Using a JDBC URL

#### Registering Through the Database Using JDBC Connection Parameters

    public static int registerConnectionFactory(java.sql.Connection connection,
                                                java.lang.String conn_name,
                                                java.lang.String hostname,
                                                java.lang.String oracle_sid,
                                                int portno,
                                                java.lang.String driver,
                                                java.lang.String type)
                                         throws JMSException

This method registers a `QueueConnectionFactory` or TopicConnectionFactory through the database to a [Lightweight Directory Access Protocol](glossary.md) (LDAP) server with JDBC connection parameters. This method is static and has the following parameters:

| Parameter    | Description                                               |
|:-------------|:----------------------------------------------------------|
| `connection` | JDBC connection used in registration                      |
| `conn_name`  | Name of the connection to be registered                   |
| `hostname`   | Name of the host running Oracle Database Advanced Queuing |
| `oracle_sid` | Oracle system identifier                                  |
| `portno`     | Port number                                               |
| `driver`     | JDBC driver type                                          |
| `type`       | Connection factory type (`QUEUE` or `TOPIC`)              |

The database connection passed to `registerConnectionFactory` must be granted `AQ_ADMINISTRATOR_ROLE`. After registration, you can look up the connection factory using [Java Naming and Directory Interface](glossary.md) (JNDI).

Example 12-1 Registering Through the Database Using JDBC Connection Parameters

    String               url;
    java.sql.connection  db_conn;

    url = "jdbc:oracle:thin:@sun-123:1521:db1";
    db_conn = DriverManager.getConnection(url, "scott", "tiger");
    AQjmsFactory.registerConnectionFactory(
       db_conn, "queue_conn1", "sun-123", "db1", 1521, "thin", "queue");

#### Registering Through the Database Using a JDBC URL

    public static int registerConnectionFactory(java.sql.Connection connection,
                                                java.lang.String conn_name,
                                                java.lang.String jdbc_url,
                                                java.util.Properties info,
                                                java.lang.String type)
                                         throws JMSException

This method registers a `QueueConnectionFactory` or TopicConnectionFactory through the database with a JDBC URL to LDAP. It is static and has the following parameters:

| Parameter    | Description                                  |
|:-------------|:---------------------------------------------|
| `connection` | JDBC connection used in registration         |
| `conn_name`  | Name of the connection to be registered      |
| `jdbc_url`   | URL to connect to                            |
| `info`       | Properties information                       |
| `portno`     | Port number                                  |
| `type`       | Connection factory type (`QUEUE` or `TOPIC`) |

The database connection passed to `registerConnectionFactory` must be granted `AQ_ADMINISTRATOR_ROLE`. After registration, you can look up the connection factory using JNDI.

Example 12-2 Registering Through the Database Using a JDBC URL

    String                        url;
    java.sql.connection           db_conn;

    url = "jdbc:oracle:thin:@sun-123:1521:db1";
    db_conn = DriverManager.getConnection(url, "scott", "tiger");
    AQjmsFactory.registerConnectionFactory(
       db_conn, "topic_conn1", url, null, "topic");

#### Registering Through LDAP Using JDBC Connection Parameters

    public static int registerConnectionFactory(java.util.Hashtable env,
                                                java.lang.String conn_name,
                                                java.lang.String hostname,
                                                java.lang.String oracle_sid,
                                                int portno,
                                                java.lang.String driver,
                                                java.lang.String type)
                                         throws JMSException

This method registers a `QueueConnectionFactory` or TopicConnectionFactory through LDAP with JDBC connection parameters to LDAP. It is static and has the following parameters:

| Parameter    | Description                                               |
|:-------------|:----------------------------------------------------------|
| `env`        | Environment of LDAP connection                            |
| `conn_name`  | Name of the connection to be registered                   |
| `hostname`   | Name of the host running Oracle Database Advanced Queuing |
| `oracle_sid` | Oracle system identifier                                  |
| `portno`     | Port number                                               |
| `driver`     | JDBC driver type                                          |
| `type`       | Connection factory type (`QUEUE` or `TOPIC`)              |

The hash table passed to `registerConnectionFactory()` must contain all the information to establish a valid connection to the LDAP server. Furthermore, the connection must have write access to the connection factory entries in the LDAP server (which requires the LDAP user to be either the database itself or be granted `GLOBAL_AQ_USER_ROLE`). After registration, look up the connection factory using JNDI.

Example 12-3 Registering Through LDAP Using JDBC Connection Parameters

    Hashtable            env = new Hashtable(5, 0.75f);
    /* the following statements set in hashtable env:
       * service provider package
       * the URL of the ldap server
       * the distinguished name of the database server
       * the authentication method (simple)
       * the LDAP username
       * the LDAP user password
    */
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
    env.put(Context.PROVIDER_URL, "ldap://sun-456:389");
    env.put("searchbase", "cn=db1,cn=Oraclecontext,cn=acme,cn=com");
    env.put(Context.SECURITY_AUTHENTICATION, "simple");
    env.put(Context.SECURITY_PRINCIPAL, "cn=db1aqadmin,cn=acme,cn=com");
    env.put(Context.SECURITY_CREDENTIALS, "welcome");

    AQjmsFactory.registerConnectionFactory(env,
                                           "queue_conn1",
                                           "sun-123",
                                           "db1",
                                           1521,
                                           "thin",
                                           "queue");

#### Registering Through LDAP Using a JDBC URL

    public static int registerConnectionFactory(java.util.Hashtable env,
                                                java.lang.String conn_name,
                                                java.lang.String jdbc_url,
                                                java.util.Properties info,
                                                java.lang.String type)
                                         throws JMSException

This method registers a `QueueConnectionFactory` or TopicConnectionFactory through LDAP with JDBC connection parameters to LDAP. It is static and has the following parameters:

| Parameter   | Description                                  |
|:------------|:---------------------------------------------|
| `env`       | Environment of LDAP connection               |
| `conn_name` | Name of the connection to be registered      |
| `jdbc_url`  | URL to connect to                            |
| info        | Properties information                       |
| `type`      | Connection factory type (`QUEUE` or `TOPIC`) |

The hash table passed to `registerConnectionFactory()` must contain all the information to establish a valid connection to the LDAP server. Furthermore, the connection must have write access to the connection factory entries in the LDAP server (which requires the LDAP user to be either the database itself or be granted `GLOBAL_AQ_USER_ROLE)`. After registration, look up the connection factory using JNDI.

Example 12-4 Registering Through LDAP Using a JDBC URL

    String               url;
    Hashtable            env = new Hashtable(5, 0.75f);

    /* the following statements set in hashtable env:
       * service provider package
       * the URL of the ldap server
       * the distinguished name of the database server
       * the authentication method (simple)
       * the LDAP username
       * the LDAP user password
    */
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
    env.put(Context.PROVIDER_URL, "ldap://sun-456:389");
    env.put("searchbase", "cn=db1,cn=Oraclecontext,cn=acme,cn=com");
    env.put(Context.SECURITY_AUTHENTICATION, "simple");
    env.put(Context.SECURITY_PRINCIPAL, "cn=db1aqadmin,cn=acme,cn=com");
    env.put(Context.SECURITY_CREDENTIALS, "welcome");
    url = "jdbc:oracle:thin:@sun-123:1521:db1";
    AQjmsFactory.registerConnectionFactory(env, "topic_conn1", url, null, "topic");

### Unregistering a Queue/Topic ConnectionFactory

You can unregister a queue/topic `ConnectionFactory` in LDAP two ways:

- Unregistering Through the Database

- Unregistering Through LDAP

#### Unregistering Through the Database

    public static int unregisterConnectionFactory(java.sql.Connection connection,
                                                  java.lang.String conn_name)
                                           throws JMSException

This method unregisters a `QueueConnectionFactory` or `TopicConnectionFactory` in LDAP. It is static and has the following parameters:

| Parameter    | Description                             |
|:-------------|:----------------------------------------|
| `connection` | JDBC connection used in registration    |
| `conn_name`  | Name of the connection to be registered |

The database connection passed to `unregisterConnectionFactory()` must be granted `AQ_ADMINISTRATOR_ROLE`.

Example 12-5 Unregistering Through the Database

    String               url;
    java.sql.connection  db_conn;

    url = "jdbc:oracle:thin:@sun-123:1521:db1";
    db_conn = DriverManager.getConnection(url, "scott", "tiger");
    AQjmsFactory.unregisterConnectionFactory(db_conn, "topic_conn1");

#### Unregistering Through LDAP

    public static int unregisterConnectionFactory(java.util.Hashtable env,
                                                  java.lang.String conn_name)
                                           throws JMSException

This method unregisters a `QueueConnectionFactory` or TopicConnectionFactory in LDAP. It is static and has the following parameters:

| Parameter   | Description                             |
|:------------|:----------------------------------------|
| `env`       | Environment of LDAP connection          |
| `conn_name` | Name of the connection to be registered |

The hash table passed to `unregisterConnectionFactory()` must contain all the information to establish a valid connection to the LDAP server. Furthermore, the connection must have write access to the connection factory entries in the LDAP server (which requires the LDAP user to be either the database itself or be granted `GLOBAL_AQ_USER_ROLE`).

Example 12-6 Unregistering Through LDAP

    Hashtable            env = new Hashtable(5, 0.75f);

    /* the following statements set in hashtable env:
       * service provider package
       * the distinguished name of the database server
       * the authentication method (simple)
       * the LDAP username
       * the LDAP user password
    */
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
    env.put(Context.PROVIDER_URL, "ldap://sun-456:389");
    env.put("searchbase", "cn=db1,cn=Oraclecontext,cn=acme,cn=com");
    env.put(Context.SECURITY_AUTHENTICATION, "simple");
    env.put(Context.SECURITY_PRINCIPAL, "cn=db1aqadmin,cn=acme,cn=com");
    env.put(Context.SECURITY_CREDENTIALS, "welcome");
    url = "jdbc:oracle:thin:@sun-123:1521:db1";
    AQjmsFactory.unregisterConnectionFactory(env, "queue_conn1");

### Getting a QueueConnectionFactory or TopicConnectionFactory

This section contains these topics:

- Getting a QueueConnectionFactory with JDBC URL

- Getting a QueueConnectionFactory with JDBC Connection Parameters

- Getting a TopicConnectionFactory with JDBC URL

- Getting a TopicConnectionFactory with JDBC Connection Parameters

- Getting a QueueConnectionFactory or TopicConnectionFactory in LDAP

#### Getting a QueueConnectionFactory with JDBC URL

    public static javax.jms.QueueConnectionFactory getQueueConnectionFactory(
                  java.lang.String jdbc_url,
                  java.util.Properties info)
           throws JMSException

This method gets a `QueueConnectionFactory` with JDBC URL. It is static and has the following parameters:

| Parameter  | Description            |
|:-----------|:-----------------------|
| `jdbc_url` | URL to connect to      |
| info       | Properties information |

Example 12-7 Getting a QueueConnectionFactory with JDBC URL

     String      url          = "jdbc:oracle:oci10:internal/oracle"
     Properties  info         = new Properties();
     QueueConnectionFactory   qc_fact;

     info.put("internal_logon", "sysdba");
     qc_fact = AQjmsFactory.getQueueConnectionFactory(url, info);

#### Getting a QueueConnectionFactory with JDBC Connection Parameters

    public static javax.jms.QueueConnectionFactory getQueueConnectionFactory(
                  java.lang.String hostname,
                  java.lang.String oracle_sid,
                  int portno,
                  java.lang.String driver)
           throws JMSException

This method gets a `QueueConnectionFactory` with JDBC connection parameters. It is static and has the following parameters:

| Parameter    | Description                                               |
|:-------------|:----------------------------------------------------------|
| `hostname`   | Name of the host running Oracle Database Advanced Queuing |
| `oracle_sid` | Oracle system identifier                                  |
| `portno`     | Port number                                               |
| `driver`     | JDBC driver type                                          |

Example 12-8 Getting a QueueConnectionFactory with JDBC Connection Parameters

     String      host         = "dlsun";
     String      ora_sid      = "rdbms10i"
     String      driver       = "thin";
     int         port         = 5521;
     QueueConnectionFactory   qc_fact;

     qc_fact = AQjmsFactory.getQueueConnectionFactory(host, ora_sid, port, driver);

#### Getting a TopicConnectionFactory with JDBC URL

    public static javax.jms.QueueConnectionFactory getQueueConnectionFactory(
                  java.lang.String jdbc_url,
                  java.util.Properties info)
           throws JMSException

This method gets a `TopicConnectionFactory` with a JDBC URL. It is static and has the following parameters:

| Parameter  | Description            |
|:-----------|:-----------------------|
| `jdbc_url` | URL to connect to      |
| info       | Properties information |

Example 12-9 Getting a TopicConnectionFactory with JDBC URL

     String      url          = "jdbc:oracle:oci10:internal/oracle"
     Properties  info         = new Properties();
     TopicConnectionFactory   tc_fact;

     info.put("internal_logon", "sysdba");
     tc_fact = AQjmsFactory.getTopicConnectionFactory(url, info);

#### Getting a TopicConnectionFactory with JDBC Connection Parameters

    public static javax.jms.TopicConnectionFactory getTopicConnectionFactory(
                  java.lang.String hostname,
                  java.lang.String oracle_sid,
                  int portno,
                  java.lang.String driver)
           throws JMSException

This method gets a `TopicConnectionFactory` with JDBC connection parameters. It is static and has the following parameters:

| Parameter    | Description                                               |
|:-------------|:----------------------------------------------------------|
| `hostname`   | Name of the host running Oracle Database Advanced Queuing |
| `oracle_sid` | Oracle system identifier                                  |
| `portno`     | Port number                                               |
| `driver`     | JDBC driver type                                          |

Example 12-10 Getting a TopicConnectionFactory with JDBC Connection Parameters

    String      host         = "dlsun";
    String      ora_sid      = "rdbms10i"
    String      driver       = "thin";
    int         port         = 5521;
    TopicConnectionFactory   tc_fact;

    tc_fact = AQjmsFactory.getTopicConnectionFactory(host, ora_sid, port, driver);

#### Getting a QueueConnectionFactory or TopicConnectionFactory in LDAP

This method gets a `QueueConnectionFactory` or `TopicConnectionFactory` from LDAP.

Example 12-11 Getting a QueueConnectionFactory or TopicConnectionFactory in LDAP

    Hashtable              env = new Hashtable(5, 0.75f);
    DirContext             ctx;
    queueConnectionFactory qc_fact;

    /* the following statements set in hashtable env:
       * service provider package
       * the URL of the ldap server
       * the distinguished name of the database server
       * the authentication method (simple)
       * the LDAP username
       * the LDAP user password
    */
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
    env.put(Context.PROVIDER_URL, "ldap://sun-456:389");
    env.put(Context.SECURITY_AUTHENTICATION, "simple");
    env.put(Context.SECURITY_PRINCIPAL, "cn=db1aquser1,cn=acme,cn=com");
    env.put(Context.SECURITY_CREDENTIALS, "welcome");

    ctx = new InitialDirContext(env);
    ctx = (DirContext)ctx.lookup("cn=OracleDBConnections,cn=db1,cn=Oraclecontext,cn=acme,cn=com");
    qc_fact = (queueConnectionFactory)ctx.lookup("cn=queue_conn1");

### Getting a Queue or Topic in LDAP

This method gets a queue or topic from LDAP.

Example 12-12 Getting a Queue or Topic in LDAP

    Hashtable              env = new Hashtable(5, 0.75f);
    DirContext             ctx;
    topic                  topic_1;

    /* the following statements set in hashtable env:
       * service provider package
       * the URL of the ldap server
       * the distinguished name of the database server
       * the authentication method (simple)
       * the LDAP username
       * the LDAP user password
    */
    env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
    env.put(Context.PROVIDER_URL, "ldap://sun-456:389");
    env.put(Context.SECURITY_AUTHENTICATION, "simple");
    env.put(Context.SECURITY_PRINCIPAL, "cn=db1aquser1,cn=acme,cn=com");
    env.put(Context.SECURITY_CREDENTIALS, "welcome");

    ctx = new InitialDirContext(env);
    ctx = (DirContext)ctx.lookup("cn=OracleDBQueues,cn=db1,cn=Oraclecontext,cn=acme,cn=com");
    topic_1 = (topic)ctx.lookup("cn=topic_1");

### Creating a Non-Sharded Queue Table

    public oracle.AQ.AQQueueTable createQueueTable(
                     java.lang.String owner,
                     java.lang.String name,
                     oracle.AQ.AQQueueTableProperty property)
              throws JMSException

This method creates a [queue table](glossary.md). It has the following parameters:

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `owner`   | Queue table owner ([schema](glossary.md)) |
| name      | Queue table name                          |
| property  | Queue table properties                    |

If the queue table is used to hold queues, then the queue table must not be multiconsumer enabled (default). If the queue table is used to hold topics, then the queue table must be multiconsumer enabled.

[CLOB](glossary.md), [BLOB](glossary.md), and [BFILE](glossary.md) objects are valid attributes for an Oracle Database Advanced Queuing [object type](glossary.md) load. However, only CLOB and BLOB can be propagated using Oracle Database Advanced Queuing [propagation](glossary.md) in Oracle8i and after.

**Note:**

Currently JMS Sharded Queues can be created and dropped only through the `DBMS_AQADM` PL/SQL APIs.

Example 12-13 Creating a Queue Table

    QueueSession              q_sess    = null;
    AQQueueTable              q_table   = null;
    AQQueueTableProperty      qt_prop   = null;

    qt_prop = new AQQueueTableProperty("SYS.AQ$_JMS_BYTES_MESSAGE");
    q_table = ((AQjmsSession)q_sess).createQueueTable(
        "boluser", "bol_ship_queue_table", qt_prop);

### Creating a Queue

This section contains these topics:

- Creating a Point-to-Point Queue

- Creating a Publish/Subscribe Topic

- Creating a Sharded Queue for Point-to-Point Queue and Publish/Subscribe Topic

#### Creating a Point-to-Point Queue

    public javax.jms.Queue createQueue(
                 oracle.AQ.AQQueueTable q_table,
                 java.lang.String queue_name,
                 oracle.jms.AQjmsDestinationProperty dest_property)
          throws JMSException

This method creates a queue in a specified queue table. It has the following parameters:

| Parameter       | Description                                                                               |
|:----------------|:------------------------------------------------------------------------------------------|
| `q_table`       | Queue table in which the queue is to be created. The queue table must be single-consumer. |
| `queue_name`    | Name of the queue to be created                                                           |
| `dest_property` | Queue properties                                                                          |

This method is specific to Oracle JMS. You cannot use standard Java `javax.jms.Session` objects with it. Instead, you must cast the standard type to the Oracle JMS concrete class `oracle.jms.AQjmsSession`.

Example 12-14 Creating a Point-to-Point Queue

    QueueSession             q_sess;
    AQQueueTable             q_table;
    AqjmsDestinationProperty dest_prop;
    Queue                    queue;

    queue = ((AQjmsSession)q_sess).createQueue(q_table, "jms_q1", dest_prop);

#### Creating a Publish/Subscribe Topic

    public javax.jms.Topic createTopic(
                 oracle.AQ.AQQueueTable q_table,
                 java.lang.String topic_name,
                 oracle.jms.AQjmsDestinationProperty dest_property)
          throws JMSException

This method creates a topic in the [publish/subscribe](glossary.md) model. It has the following parameters:

| Parameter       | Description                                                                             |
|:----------------|:----------------------------------------------------------------------------------------|
| `q_table`       | Queue table in which the queue is to be created. The queue table must be multiconsumer. |
| `queue_name`    | Name of the queue to be created                                                         |
| `dest_property` | Queue properties                                                                        |

This method is specific to Oracle JMS. You cannot use standard Java `javax.jms.Session` objects with it. Instead, you must cast the standard type to the Oracle JMS concrete class `oracle.jms.AQjmsSession`.

In Example 12-16, if an order cannot be filled because of insufficient inventory, then the transaction processing the order is terminated. The `bookedorders` topic is set up with `max_retries` = 4 and `retry_delay` = 12 hours.Thus, if an order is not filled up in two days, then it is moved to an exception queue.

Example 12-15 Creating a Publish/Subscribe Topic

    TopicSession             t_sess;
    AQQueueTable             q_table;
    AqjmsDestinationProperty dest_prop;
    Topic                    topic;

    topic = ((AQjmsSessa)t_sess).createTopic(q_table, "jms_t1", dest_prop);

Example 12-16 Specifying Max Retries and Max Delays in Messages

    public BolOrder process_booked_order(TopicSession jms_session)
      {
        Topic            topic;
        TopicSubscriber  tsubs;
        ObjectMessage    obj_message;
        BolCustomer      customer;
        BolOrder         booked_order = null;
        String           country;
        int              i = 0;

        try
        {
          /* get a handle to the OE_bookedorders_topic */
          topic = ((AQjmsSession)jms_session).getTopic("WS",
                                                       "WS_bookedorders_topic");

          /* Create local subscriber - to track messages for Western Region  */
          tsubs = jms_session.createDurableSubscriber(topic, "SUBS1",
                                           "Region = 'Western' ",
                                                       false);

           /* wait for a message to show up in the topic */
           obj_message = (ObjectMessage)tsubs.receive(10);

           booked_order = (BolOrder)obj_message.getObject();

           customer = booked_order.getCustomer();
           country    = customer.getCountry();

           if (country == "US")
           {
              jms_session.commit();
           }
           else
           {
              jms_session.rollback();
              booked_order = null;
           }
        }catch (JMSException ex)
        { System.out.println("Exception " + ex) ;}

         return booked_order;
       }

#### Creating a Sharded Queue for Point-to-Point Queue and Publish/Subscribe Topic

AQ JMS has defined a new APIs to create and drop sharded queues. There is no alter queue API in JMS. The signatures are as follows:

        /**
         * Create a JMS sharded queue. It also internally creates the related queue
         * objects (table, indexes) based on this name.
         *
         * @param queueName name of the queue to be created, format is schema.queueName
         *        (where the schema. is optional
         * @param isMultipleConsumer flag to indicate whether the queue is a
         *        multi-consumer or single-consumer queue
         * @return javax.jms.Destination
         * @throws JMSException if the queue could not be created
         */
        public synchronized javax.jms.Destination createJMSShardedQueue(String queueName,
                boolean isMultipleConsumer) throws JMSException {
            return createJMSShardedQueue(queueName, isMultipleConsumer, null, 0, null);
        }

        /**
         * Create a JMS sharded queue. It also internally creates the related queue
         * objects (table, indexes) based on this name.
         *
         * @param queueName name of the queue to be created, format is schema.queueName
         *        (where the schema. is optional
         * @param isMultipleConsumer flag to indicate whether the queue is a
         *        multi-consumer or single-consumer queue
         * @param storageClause additional storage clause
         * @param maxRetries retry count before skip the message while dequeue
         * @param comment comment for the queue
         * @return javax.jms.Destination
         * @throws JMSException if the queue could not be created
    */
    public Destination createJMSShardedQueue(java.lang.String queueName,
                                             boolean isMultipleConsumer,
                                             java.lang.String storageClause,
                                             int maxRetries,
                                             java.lang.String comment)
                                      throws JMSException

### Getting a Non-Sharded Queue Table

    public oracle.AQ.AQQueueTable getQueueTable(java.lang.String owner,
                                                java.lang.String name)
                                         throws JMSException

This method gets a queue table for a non-sharded queue. It has the following parameters:

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `owner`   | Queue table owner ([schema](glossary.md)) |
| name      | Queue table name                          |

If the caller that opened the connection is not the owner of the queue table, then the caller must have Oracle Database Advanced Queuing [enqueue](glossary.md)/[dequeue](glossary.md) privileges on queues/topics in the queue table. Otherwise the queue table is not returned.

Example 12-17 Getting a Queue Table

    QueueSession              q_sess;
    AQQueueTable              q_table;

    q_table = ((AQjmsSession)q_sess).getQueueTable(
       "boluser", "bol_ship_queue_table");

### Granting and Revoking Privileges

This section contains these topics:

- Granting Oracle Database Advanced Queuing System Privileges

- Revoking Oracle Database Advanced Queuing System Privileges

- Granting Publish/Subscribe Topic Privileges

- Revoking Publish/Subscribe Topic Privileges

- Granting Point-to-Point Queue Privileges

- Revoking Point-to-Point Queue Privileges

#### Granting Oracle Database Advanced Queuing System Privileges

    public void grantSystemPrivilege(java.lang.String privilege,
                                     java.lang.String grantee,
                                     boolean admin_option)
                              throws JMSException

This method grants Oracle Database Advanced Queuing system privileges to a user or role.

| Parameter      | Description                                                                                                                     |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `privilege`    | `ENQUEUE_ANY`, `DEQUEUE_ANY` or `MANAGE_ANY`                                                                                    |
| `grantee`      | Grantee (user, role, or `PUBLIC`)                                                                                               |
| `admin_option` | If this is set to true, then the grantee is allowed to use this procedure to grant the system privilege to other users or roles |

Initially only `SYS` and `SYSTEM` can use this procedure successfully. Users granted the `ENQUEUE_ANY` privilege are allowed to enqueue messages to any queues in the database. Users granted the `DEQUEUE_ANY` privilege are allowed to dequeue messages from any queues in the database. Users granted the `MANAGE_ANY` privilege are allowed to run `DBMS_AQADM` calls on any schemas in the database.

Example 12-18 Granting Oracle Database Advanced Queuing System Privileges

    TopicSession             t_sess;

    ((AQjmsSession)t_sess).grantSystemPrivilege("ENQUEUE_ANY", "scott", false);

#### Revoking Oracle Database Advanced Queuing System Privileges

    public void revokeSystemPrivilege(java.lang.String privilege,
                                      java.lang.String grantee)
                               throws JMSException

This method revokes Oracle Database Advanced Queuing system privileges from a user or role. It has the following parameters:

| Parameter   | Description                                  |
|:------------|:---------------------------------------------|
| `privilege` | `ENQUEUE_ANY`, `DEQUEUE_ANY` or `MANAGE_ANY` |
| `grantee`   | Grantee (user, role, or `PUBLIC`)            |

Users granted the `ENQUEUE_ANY` privilege are allowed to enqueue messages to any queues in the database. Users granted the `DEQUEUE_ANY` privilege are allowed to dequeue messages from any queues in the database. Users granted the `MANAGE_ANY` privilege are allowed to run `DBMS_AQADM` calls on any schemas in the database.

Example 12-19 Revoking Oracle Database Advanced Queuing System Privileges

    TopicSession             t_sess;

    ((AQjmsSession)t_sess).revokeSystemPrivilege("ENQUEUE_ANY", "scott");

#### Granting Publish/Subscribe Topic Privileges

    public void grantTopicPrivilege(javax.jms.Session session,
                                    java.lang.String privilege,
                                    java.lang.String grantee,
                                    boolean grant_option)
                             throws JMSException

This method grants a topic privilege in the publish/subscribe model. Initially only the queue table owner can use this procedure to grant privileges on the topic. It has the following parameters:

| Parameter      | Description                                                                                                                     |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `session`      | [JMS session](glossary.md)                                                                                                      |
| `privilege`    | `ENQUEUE`, `DEQUEUE,` or `ALL` (`ALL` means both.)                                                                              |
| `grantee`      | Grantee (user, role, or `PUBLIC`)                                                                                               |
| `grant_option` | If this is set to true, then the grantee is allowed to use this procedure to grant the system privilege to other users or roles |

Example 12-20 Granting Publish/Subscribe Topic Privileges

    TopicSession             t_sess;
    Topic                    topic;

    ((AQjmsDestination)topic).grantTopicPrivilege(
       t_sess, "ENQUEUE", "scott", false);

#### Revoking Publish/Subscribe Topic Privileges

    public void revokeTopicPrivilege(javax.jms.Session session,
                                     java.lang.String privilege,
                                     java.lang.String grantee)
                              throws JMSException

This method revokes a topic privilege in the publish/subscribe model. It has the following parameters:

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `session`   | JMS session                                        |
| `privilege` | `ENQUEUE`, `DEQUEUE,` or `ALL` (`ALL` means both.) |
| `grantee`   | Revoked grantee (user, role, or `PUBLIC`)          |

Example 12-21 Revoking Publish/Subscribe Topic Privileges

    TopicSession             t_sess;
    Topic                    topic;

    ((AQjmsDestination)topic).revokeTopicPrivilege(t_sess, "ENQUEUE", "scott");

#### Granting Point-to-Point Queue Privileges

    public void grantQueuePrivilege(javax.jms.Session session,
                                    java.lang.String privilege,
                                    java.lang.String grantee,
                                    boolean grant_option)
                             throws JMSException

This method grants a queue privilege in the point-to-point model. Initially only the queue table owner can use this procedure to grant privileges on the queue. It has the following parameters:

| Parameter      | Description                                                                                                                     |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `session`      | JMS session                                                                                                                     |
| `privilege`    | `ENQUEUE`, `DEQUEUE,` or `ALL` (`ALL` means both.)                                                                              |
| `grantee`      | Grantee (user, role, or `PUBLIC`)                                                                                               |
| `grant_option` | If this is set to true, then the grantee is allowed to use this procedure to grant the system privilege to other users or roles |

Example 12-22 Granting Point-to-Point Queue Privileges

    QueueSession             q_sess;
    Queue                    queue;

    ((AQjmsDestination)queue).grantQueuePrivilege(
       q_sess, "ENQUEUE", "scott", false);

#### Revoking Point-to-Point Queue Privileges

    public void revokeQueuePrivilege(javax.jms.Session session,
                                     java.lang.String privilege,
                                     java.lang.String grantee)
                              throws JMSException

This method revokes queue privileges in the point-to-point model. Initially only the queue table owner can use this procedure to grant privileges on the queue. It has the following parameters:

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `session`   | JMS session                                        |
| `privilege` | `ENQUEUE`, `DEQUEUE,` or `ALL` (`ALL` means both.) |
| `grantee`   | Revoked grantee (user, role, or `PUBLIC`)          |

To revoke a privilege, the revoker must be the original grantor of the privilege. Privileges propagated through the `GRANT` option are revoked if the grantor privilege is also revoked.

Example 12-23 Revoking Point-to-Point Queue Privileges

    QueueSession             q_sess;
    Queue                    queue;

    ((AQjmsDestination)queue).revokeQueuePrivilege(q_sess, "ENQUEUE", "scott");

### Managing Destinations

This section contains these topics:

- Starting a Destination

- Stopping a Destination

- Altering a Destination

- Dropping a Destination

**Note:**

Currently JMS Sharded Queues can be managed only through the `DBMS_AQADM` PL/SQL APIs.

#### Starting a Destination

    public void start(javax.jms.Session session,
                      boolean enqueue,
                      boolean dequeue)
               throws JMSException

This method starts a destination. It has the following parameters:

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `session` | JMS session                               |
| `enqueue` | If set to `TRUE`, then enqueue is enabled |
| dequeue   | If set to `TRUE`, then dequeue is enabled |

Example 12-24 Starting a Destination

    TopicSession t_sess;
    QueueSession q_sess;
    Topic        topic;
    Queue        queue;

    (AQjmsDestination)topic.start(t_sess, true, true);
    (AQjmsDestination)queue.start(q_sess, true, true);

#### Stopping a Destination

    public void stop(javax.jms.Session session,
                     boolean enqueue,
                     boolean dequeue,
                     boolean wait)
              throws JMSException

This method stops a destination. It has the following parameters:

| Parameter | Description                                                                                                            |
|:----------|:-----------------------------------------------------------------------------------------------------------------------|
| `session` | JMS session                                                                                                            |
| `enqueue` | If set to `TRUE`, then enqueue is disabled                                                                             |
| dequeue   | If set to `TRUE`, then dequeue is disabled                                                                             |
| `wait`    | If set to true, then pending transactions on the queue/topic are allowed to complete before the destination is stopped |

Example 12-25 Stopping a Destination

    TopicSession t_sess;
    Topic        topic;

    ((AQjmsDestination)topic).stop(t_sess, true, false);

#### Altering a Destination

    public void alter(javax.jms.Session session,
                      oracle.jms.AQjmsDestinationProperty dest_property)
               throws JMSException

This method alters a destination. It has the following properties:

| Parameter     | Description                          |
|:--------------|:-------------------------------------|
| `session`     | JMS session                          |
| dest_property | New properties of the queue or topic |

Example 12-26 Altering a Destination

    QueueSession q_sess;
    Queue        queue;
    TopicSession t_sess;
    Topic        topic;
    AQjmsDestionationProperty dest_prop1, dest_prop2;

    ((AQjmsDestination)queue).alter(dest_prop1);
    ((AQjmsDestination)topic).alter(dest_prop2);

#### Dropping a Destination

    public void drop(javax.jms.Session session)
              throws JMSException

This method drops a destination. It has the following parameter:

| Parameter | Description |
|:----------|:------------|
| `session` | JMS session |

Example 12-27 Dropping a Destination

    QueueSession q_sess;
    Queue        queue;
    TopicSession t_sess;
    Topic        topic;

    ((AQjmsDestionation)queue).drop(q_sess);
    ((AQjmsDestionation)topic).drop(t_sess);

### Propagation Schedules

This section contains these topics:

- Scheduling a Propagation

- Enabling a Propagation Schedule

- Altering a Propagation Schedule

- Disabling a Propagation Schedule

- Unscheduling a Propagation

**Note:**

JMS Sharded Queues are currently managed only through the `DBMS_AQADM` PL/SQL APIs and do not support propagation.

#### Scheduling a Propagation

    public void schedulePropagation(javax.jms.Session session,
                                    java.lang.String destination,
                                    java.util.Date start_time,
                                    java.lang.Double duration,
                                    java.lang.String next_time,
                                    java.lang.Double latency)
                             throws JMSException

This method schedules a propagation. It has the following parameters:

| Parameter     | Description                                                                                                                                                                        |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `session`     | JMS session                                                                                                                                                                        |
| `destination` | Database link of the remote database for which propagation is being scheduled. A null string means that propagation is scheduled for all subscribers in the database of the topic. |
| `start_time`  | Time propagation starts                                                                                                                                                            |
| `duration`    | Duration of propagation                                                                                                                                                            |
| `next_time`   | Next time propagation starts                                                                                                                                                       |
| `latency`     | Latency in seconds that can be tolerated. Latency is the difference between the time a message was enqueued and the time it was propagated.                                        |

If a [message](glossary.md) has multiple recipients at the same destination in either the same or different queues, then it is propagated to all of them at the same time.

Example 12-28 Scheduling a Propagation

    TopicSession t_sess;
    Topic        topic;

    ((AQjmsDestination)topic).schedulePropagation(
       t_sess, null, null, null, null, new Double(0));

#### Enabling a Propagation Schedule

    public void enablePropagationSchedule(javax.jms.Session session,
                                          java.lang.String destination)
                                   throws JMSException

This method enables a propagation schedule. It has the following parameters:

| Parameter     | Description                                                                                               |
|:--------------|:----------------------------------------------------------------------------------------------------------|
| `session`     | JMS session                                                                                               |
| `destination` | Database link of the destination database. A null string means that propagation is to the local database. |

Example 12-29 Enabling a Propagation Schedule

    TopicSession             t_sess;
    Topic                    topic;

    ((AQjmsDestination)topic).enablePropagationSchedule(t_sess, "dbs1");

#### Altering a Propagation Schedule

    public void alterPropagationSchedule(javax.jms.Session session,
                                         java.lang.String destination,
                                         java.lang.Double duration,
                                         java.lang.String next_time,
                                         java.lang.Double latency)
                                  throws JMSException

This method alters a propagation schedule. It has the following parameters:

| Parameter     | Description                                                                                                                                                                        |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `session`     | JMS session                                                                                                                                                                        |
| `destination` | Database link of the remote database for which propagation is being scheduled. A null string means that propagation is scheduled for all subscribers in the database of the topic. |
| `duration`    | Duration of propagation                                                                                                                                                            |
| `next_time`   | Next time propagation starts                                                                                                                                                       |
| `latency`     | Latency in seconds that can be tolerated. Latency is the difference between the time a message was enqueued and the time it was propagated.                                        |

Example 12-30 Altering a Propagation Schedule

    TopicSession             t_sess;
    Topic                    topic;

    ((AQjmsDestination)topic).alterPropagationSchedule(
       t_sess, null, 30, null, new Double(30));

#### Disabling a Propagation Schedule

    public void disablePropagationSchedule(javax.jms.Session session,
                                           java.lang.String destination)
                                    throws JMSException

This method disables a propagation schedule. It has the following parameters:

| Parameter     | Description                                                                                               |
|:--------------|:----------------------------------------------------------------------------------------------------------|
| `session`     | JMS session                                                                                               |
| `destination` | Database link of the destination database. A null string means that propagation is to the local database. |

Example 12-31 Disabling a Propagation Schedule

    TopicSession             t_sess;
    Topic                    topic;

    ((AQjmsDestination)topic).disablePropagationSchedule(t_sess, "dbs1");

#### Unscheduling a Propagation

    public void unschedulePropagation(javax.jms.Session session,
                                      java.lang.String destination)
                               throws JMSException

This method unschedules a previously scheduled propagation. It has the following parameters:

| Parameter     | Description                                                                                               |
|:--------------|:----------------------------------------------------------------------------------------------------------|
| `session`     | JMS session                                                                                               |
| `destination` | Database link of the destination database. A null string means that propagation is to the local database. |

Example 12-32 Unscheduling a Propagation

    TopicSession   t_sess;
    Topic          topic;

    ((AQjmsDestination)topic).unschedulePropagation(t_sess, "dbs1");
