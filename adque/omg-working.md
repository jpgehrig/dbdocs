After Oracle Messaging Gateway (MGW) is loaded and set up, it is ready to be configured and run. You can use `DBMS_MGWADM`.`ALTER_AGENT` to set the user name, password, database specifier, and connection type the Messaging Gateway agent will use for creating database connections.

Topics:

- Configuring the Oracle Messaging Gateway Agent

- Starting and Shutting Down the Oracle Messaging Gateway Agent

- Configuring Messaging System Links

- Configuring Non-Oracle Messaging System Queues

- Configuring Oracle Messaging Gateway Propagation Jobs

- Propagation Jobs\_ Subscribers\_ and Schedules

- Configuration Properties

**Note:**

All commands in the examples must be run as a user granted `MGW_ADMINISTRATOR_ROLE`.

**See Also:**

"DBMS_MGWADM" and "DBMS_MGWMSG" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWADM.md)

### Configuring the Oracle Messaging Gateway Agent

Messages are propagated between Oracle Database Advanced Queuing and non-Oracle messaging systems by the Messaging Gateway agent. The Messaging Gateway agent runs as an external process of the Oracle Database server.

Messaging Gateway supports multiple agents for a given database. A default agent is automatically created that has the name of `DEFAULT_AGENT`. Additional named agents can be created to provide propagation job isolation and grouping, and scaling in an Oracle RAC environment. The default agent is usually sufficient for single instance, non-Oracle RAC, environments.

This section contains these topics:

- Creating a Messaging Gateway Agent

- Removing a Messaging Gateway Agent

- Setting Database Connection

- Setting the Resource Limits

#### Creating a Messaging Gateway Agent

You can use `DBMS_MGWADM`.`CREATE_AGENT` to create additional Messaging Gateway agents. The Messaging Gateway default agent, `DEFAULT_AGENT`, is automatically created when Messaging Gateway is installed and will always exist.

Agents can be configured with an agent user, connection information, database service, and resource limits when the agent is created, or at a later time using `DBMS_MGWADM`.`ALTER_AGENT`. A Messaging Gateway agent must be configured with a database user that has been granted the role `MGW_AGENT_ROLE` before the agent can be started.

Example 19-1 creates the agent named `myagent` and specifies the database connection information for the agent user. Default values are used for all other parameters.

Example 19-1 Creating a Messaging Gateway Agent

    SQL> exec DBMS_MGWADM.CREATE_AGENT(
                             agent_name  => 'myagent',
                             username    => 'mgwagent',
                             password    => 'mgwagent_password',
                             database    => 'mydatabase');

#### Removing a Messaging Gateway Agent

A Messaging Gateway agent can be removed by calling `DBMS_MGWADM`.`REMOVE_AGENT`. Before an agent can be removed, all Messaging Gateway links associated with the agent must be removed and the agent shut down. The default agent, `DEFAULT_AGENT`, cannot be removed. Example 19-2 removes the agent named `myagent`.

Example 19-2 Removing a Messaging Gateway Agent

    SQL> exec DBMS_MGWADM.REMOVE_AGENT(agent_name   => 'myagent');

#### Setting Database Connection

The Messaging Gateway agent runs as a process external to the database. To access Oracle Database Advanced Queuing and the Messaging Gateway packages, the Messaging Gateway agent needs to establish connections to the database. You can use `DBMS_MGWADM`.`ALTER_AGENT` to set the user name, password and the database connect string that the Messaging Gateway agent will use for creating database connections. The user must be granted the role `MGW_AGENT_ROLE` before the Messaging Gateway agent can be started.

Example 19-3 shows the Messaging Gateway default agent being configured for user `mgwagent` with password `mgwagent_password` using net service name `mydatabase`.

Example 19-3 Setting Database Connection Information

    SQL> exec DBMS_MGWADM.ALTER_AGENT (
                                 agent_name => 'default_agent',
                                 username   => 'mgwagent',
                                 password   => 'mgwagent_password',
                                 database   => 'mydatabase');

#### Setting the Resource Limits

You can use `DBMS_MGWADM`.`ALTER_AGENT` to set resource limits for the Messaging Gateway agent. For example, you can set the heap size of the Messaging Gateway agent process and the number of propagation threads used by the agent process. The default values are 64 MB of memory heap and one propagation thread. For named agents, these values can also be specified when the agent is created by `DBMS_MGWADM`.`CREATE_AGENT`.

Example 19-4 sets the heap size to 96 MB and two propagation threads for the agent myagent.

The memory heap size and the number of propagation threads cannot be altered when the Messaging Gateway agent is running.

Example 19-4 Setting the Resource Limits

    SQL> exec DBMS_MGWADM.ALTER_AGENT(
                            agent_name  => 'myagent',
                            max_memory  => 96,
                            max_threads => 2);

### Starting and Shutting Down the Oracle Messaging Gateway Agent

This section contains these topics:

- Starting the Oracle Messaging Gateway Agent

- Shutting Down the Oracle Messaging Gateway Agent

- Oracle Messaging Gateway Agent Scheduler Job

- Running the Oracle Messaging Gateway Agent on Oracle RAC

#### Starting the Oracle Messaging Gateway Agent

After the Messaging Gateway agent is configured, you can start the agent with `DBMS_MGWADM.STARTUP`. Example 19-5 shows how to start the default agent and agent `myagent`.

You can use the `MGW_GATEWAY` view to check the status of the Messaging Gateway agent, as described in [Monitoring Oracle Messaging Gateway](omg-monitoring.md).

Example 19-5 Starting the Messaging Gateway Agent

    SQL> exec DBMS_MGWADM.STARTUP;
    SQL> exec DBMS_MGWADM.STARTUP ('myagent');

#### Shutting Down the Oracle Messaging Gateway Agent

You can use `DBMS_MGWADM`.`SHUTDOWN` to shut down the Messaging Gateway agent. Example 19-6 shows how to shut down the Messaging Gateway default agent and agent `myagent`.

You can use the `MGW_GATEWAY` view to check if the Messaging Gateway agent has shut down successfully, as described in [Monitoring Oracle Messaging Gateway](omg-monitoring.md).

Example 19-6 Shutting Down the Messaging Gateway Agent

    SQL> exec DBMS_MGWADM.SHUTDOWN;
    SQL> exec DBMS_MGWADM.SHUTDOWN ('myagent');

#### Oracle Messaging Gateway Agent Scheduler Job

Messaging Gateway uses a Scheduler job to start the Messaging Gateway agent. This job is created when procedure `DBMS_MGWADM.STARTUP` is called. When the job is run, it calls an external procedure that creates the Messaging Gateway agent in an external process. The job is removed after:

- The agent shuts down because `DBMS_MGWADM.SHUTDOWN` was called

- The agent terminates because a non-restartable error occurs

Messaging Gateway uses `DBMS_SCHEDULER` to create a repeatable Scheduler job with a repeat interval of one minute. The job is owned by `SYS`. A repeatable job enables the Messaging Gateway agent to restart automatically when a given job instance ends because of a database shutdown, database malfunction, or a restartable error. Only one instance of a Messaging Gateway agent job runs at a given time.

Each agent uses a Scheduler job class to specify the service affinity for the agent's Scheduler job. The job class will be configured with the database service specified by `DBMS_MGWADM`.`CREATE_AGENT` or `DBMS_MGWADM`.`ALTER_AGENT`. A database administrator is responsible for setting up the database service. If no database service is specified, the default database service that maps to every instance is used.

The name of the Scheduler job class used by the Messaging Gateway default agent is `SYS`.`MGW_JOBCLS_DEFAULT_AGENT`. The Scheduler job used by the default agent is `SYS`.`MGW_JOB_DEFAULT_AGENT`.

The name of the Scheduler job class used by a Messaging Gateway named agent is `SYS`.`MGW_JOBCLS_`\<`agent_name`\>. The Scheduler job used by a named agent is `SYS`.`MGW_JOB_`\<`agent_name`\>.

If the agent job encounters an error, then the error is classified as either a restartable error or non-restartable error. A restartable error indicates a problem that might go away if the agent job were to be restarted. A non-restartable error indicates a problem that is likely to persist and be encountered again if the agent job restarts. ORA-01089 (immediate shutdown in progress) and ORA-28576 (lost RPC connection to external procedure) are examples of restartable errors. ORA-06520 (error loading external library) is an example of a non-restartable error.

Messaging Gateway uses a database shutdown trigger. If the Messaging Gateway agent is running on the instance being shut down, then the trigger notifies the agent of the shutdown, and upon receipt of the notification, the agent will terminate the current run. The job scheduler will automatically schedule the job to run again at a future time.

If a Messaging Gateway agent job instance ends because of a database malfunction or a restartable error detected by the agent job, then the job will not be removed and the job scheduler will automatically schedule the job to run again at a future time.

The `MGW_GATEWAY` view shows the agent status, database service, and the database instance on which the Messaging Gateway agent is current running. The Oracle Scheduler views provide information about Scheduler jobs, job classes, and job run details.

**See Also:**

- "DBMS_SCHEDULER" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SCHEDULER.md)

- [Monitoring Oracle Messaging Gateway](omg-monitoring.md)

#### Running the Oracle Messaging Gateway Agent on Oracle RAC

While the Messaging Gateway job startup and shutdown principles are the same for Oracle Real Application Clusters (Oracle RAC) and non-Oracle RAC environments, there are some things to keep in mind for an Oracle RAC environment.

A single process of each configured Messaging Gateway agent can be running, even in an Oracle RAC environment. For example, if the default agent and two named agents have been configured with an agent user, then one instance of all three agents could be running at the same time. The database service associated with each agent determines the service affinity of the agent's Scheduler job, and thus, the database instance on which the agent process can run.

When a database instance is shut down in an Oracle RAC environment, the Messaging Gateway shutdown trigger will notify the agent to shut down only if the Messaging Gateway agent is running on the instance being shut down. The job scheduler will automatically schedule the job to be run again at a future time, either on another instance, or if the job can only run on the instance being shut down, when that instance is restarted.

Oracle recommends that all database connections made by the Messaging Gateway agent be made to the instance on which the Messaging Gateway agent process is running. This ensures correct failover behavior in an Oracle RAC environment.

If a Messaging Gateway agent has been associated with a database service, the agent's Scheduler job will not run unless that service is current enabled on a running instance. When you shut down a database Oracle stops all services to that database and you may need to manually restart the services when you start the database.

**See Also:**

- "[Configuring Oracle Messaging Gateway in an Oracle RAC Environment](omg-getting-started.md)"

- "`DBMS_MGWADM`" and "`DBMS_SCHEDULER`" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SCHEDULER.md)

### Configuring Messaging System Links

Running as a client of non-Oracle messaging systems, the Messaging Gateway agent communicates with non-Oracle messaging systems through messaging system links. A messaging system link is a set of connections between the Messaging Gateway agent and a non-Oracle messaging system.

To configure a messaging system link of a non-Oracle messaging system, users must provide information for the agent to make connections to the non-Oracle messaging system. Users can specify the maximum number of messaging connections.

An agent name will be associated with each messaging system link. This is done when the link is created and cannot be changed. The agent associated with the link is then responsible for processing all propagation jobs that use a registered queue associated with that link. The Messaging Gateway default agent will be used if an agent name is not specified when the messaging system link is created.

When configuring a messaging system link for a non-Oracle messaging system that supports transactions and persistent messages, the native name of log queues for inbound and outbound propagation must be specified in order to guarantee exactly-once [message](glossary.md) delivery. The log queues should be used only by the Messaging Gateway agent. No other programs should [enqueue](glossary.md) or [dequeue](glossary.md) messages of the log queues. The inbound log queue and outbound log queue can refer to the same physical queue, but better performance can be achieved if they refer to different physical queues.

One and only one Messaging Gateway agent should access a propagation log queue. This insures that a given log queue contains log records for only those propagation jobs processed by that agent and that the agent is free to discard any other log records it might encounter.

When configuring a messaging system link, users can also specify an `options` argument. An `options` argument is a set of {name, value} pairs of type `SYS.MGW_PROPERTY`.

This section contains these topics:

- Creating a WebSphere MQ Base Java Link

- Creating a WebSphere MQ JMS Link

- Creating a WebSphere MQ Link to Use SSL

- Creating a TIB/Rendezvous Link

- Altering a Messaging System Link

- Removing a Messaging System Link

- Views for Messaging System Links

#### Creating a WebSphere MQ Base Java Link

A WebSphere MQ Base Java link is created by calling `DBMS_MGWADM.CREATE_MSGSYSTEM_LINK` with the following information provided:

- Interface type: `DBMS_MGWADM.MQSERIES_BASE_JAVA_INTERFACE`

- WebSphere MQ connection information:

  - Host name and port number of the WebSphere MQ server

  - Queue manager name

  - Channel name

  - User name and password

- Maximum number of messaging connections allowed

- Log queue names for inbound and outbound propagation

- Optional information such as:

  - Send, receive, and security exits

  - Character sets

Example 19-7 configures a WebSphere MQ Base Java link `mqlink`. The link is configured to use the WebSphere MQ queue manager `my.queue.manager` on host `myhost.mydomain` and port 1414, using WebSphere MQ channel `mychannel`.

This example also sets the option to register a WebSphere MQ `SendExit` class. The class `mySendExit` must be in the `CLASSPATH` set in `mgw.ora`. The Messaging Gateway default agent (`DEFAULT_AGENT`) is responsible for the link and all propagation jobs using the link.

**See Also:**

- "[Understanding the mgw.ora Initialization File](omg-getting-started.md)" for information on setting the CLASSPATH of the Messaging Gateway agent

- "WebSphere MQ System Properties"

Example 19-7 Configuring a WebSphere MQ Base Java Link

    DECLARE
      v_options sys.mgw_properties;
      v_prop sys.mgw_mqseries_properties;
    BEGIN
      v_prop := sys.mgw_mqseries_properties.construct();

      v_prop.interface_type := dbms_mgwadm.MQSERIES_BASE_JAVA_INTERFACE;
      v_prop.max_connections := 1;
      v_prop.username := 'mqm';
      v_prop.password := 'mqm';
      v_prop.hostname := 'myhost.mydomain';
      v_prop.port     := 1414;
      v_prop.channel  := 'mychannel';
      v_prop.queue_manager := 'my.queue.manager';
      v_prop.outbound_log_queue := 'mylogq';

      -- Specify a WebSphere MQ send exit class 'mySendExit' to be associated with
      -- the queue.
      -- Note that this is used as an example of how to use the options parameter,
      -- but is not an option that is usually set.
      v_options := sys.mgw_properties(sys.mgw_property('MQ_SendExit',
                                                       'mySendExit'));
      dbms_mgwadm.create_msgsystem_link(
          linkname => 'mqlink', agent_name=>'default_agent', properties => v_prop,
          options => v_options );
    END;

#### Creating a WebSphere MQ JMS Link

A WebSphere MQ JMS link is created by calling `DBMS_MGWADM.CREATE_MSGSYSTEM_LINK` with the following information provided:

- Interface type

  [Java Message Service](glossary.md) (JMS) distinguishes between queue and topic connections. The Sun Microsystem JMS 1.1 standard supports domain unification that allows both JMS queues and topics to be accessed by a single JMS connection:

  - A WebSphere MQ JMS link created with interface type `DBMS_MGWADM.JMS_CONNECTION` can be used to access both JMS queues and topics. This is the recommended interface for a WebSphere MQ JMS link.

  - A WebSphere MQ JMS link created with interface type `DBMS_MGWADM.JMS_QUEUE_CONNECTION` can be used to access only JMS queues.

  - A WebSphere MQ JMS link created with interface type `DBMS_MGWADM.JMS_TOPIC_CONNECTION` can be used to access only JMS topics.

- WebSphere MQ connection information:

  - Host name and port number of the WebSphere MQ server

  - Queue manager name

  - Channel name

  - User name and password

- Maximum number of messaging connections allowed

  A messaging connection is mapped to a [JMS session](glossary.md).

- Log destination (JMS queue or [JMS topic](glossary.md)) for inbound and outbound propagation

  The log destination type must be valid for the link type. JMS unified links and JMS queue links must use JMS queues for log destinations, and JMS topic links must use topics:

  - For a WebSphere MQ JMS unified or queue link, the log queue name must be the name of a physical WebSphere MQ JMS queue created using WebSphere MQ administration tools.

  - For a WebSphere MQ JMS topic link, the log topic name must be the name of a WebSphere MQ JMS topic. The physical WebSphere MQ queue used by that topic must be created using WebSphere MQ administration tools. By default, the physical queue used is `SYSTEM.JMS.D.SUBSCRIBER.QUEUE`. A link option can be used to specify a different physical queue.

- Optional information such as:

  - Send, receive, and security exits

  - Character sets

  - WebSphere MQ [publish/subscribe](glossary.md) configuration used for JMS topics

Example 19-8 configures a Messaging Gateway link to a WebSphere MQ queue manager using a JMS topic interface. The link is named `mqjmslink` and is configured to use the WebSphere MQ queue manager `my.queue.manager` on host `myhost.mydomain` and port 1414, using WebSphere MQ channel `mychannel`.

This example also uses the `options` parameter to specify a nondefault durable subscriber queue to be used with the log topic. The Messaging Gateway agent `myagent` is responsible for the link and all propagation jobs using the link.

**See Also:**

- "Registering a WebSphere MQ JMS Queue or Topic" for more information on JMS queues and topics

- "WebSphere MQ System Properties"

Example 19-8 Configuring a WebSphere MQ JMS Link

    DECLARE
      v_options sys.mgw_properties;
      v_prop sys.mgw_mqseries_properties;
    BEGIN
      v_prop := sys.mgw_mqseries_properties.construct();
      v_prop.max_connections := 1;

      v_prop.interface_type := DBMS_MGWADM.JMS_TOPIC_CONNECTION;
      v_prop.username := 'mqm';
      v_prop.password := 'mqm';
      v_prop.hostname := 'myhost.mydomain';
      v_prop.port     := 1414;
      v_prop.channel  := 'mychannel';
      v_prop.queue_manager := 'my.queue.manager';

      v_prop.outbound_log_queue := 'mylogtopic'

      -- Specify a WebSphere MQ durable subscriber queue to be used with the
      -- log topic.
      v_options := sys.mgw_properties(
      sys.mgw_property('MQ_JMSDurSubQueue', 'myDSQueue'));

      DBMS_MGWADM.CREATE_MSGSYSTEM_LINK(
          linkname     =>  'mqjmslink',
          agent_name   =>  'myagent',
          properties   =>   v_prop,
          options      =>   v_options );
    END;

#### Creating a WebSphere MQ Link to Use SSL

Messaging Gateway allows SSL support for IBM WebSphere MQ and WebSphere MQ JMS connections. This section describes how to configure Messaging Gateway to use SSL for a WebSphere MQ Base Java link and the same information applies to a WebSphere MQ JMS link. There are no differences in terms of the Messaging Gateway configuration.

The following are needed in order to use SSL for WebSphere MQ connections:

- A WebSphere MQ channel configured to use SSL.

- A truststore and optionally a keystore file that are in a location accessible to the Messaging Gateway agent process. In an Oracle RAC environment, these files must be accessible to all instances on which the Messaging Gateway agent process might run, using the same path specification.

- Use `DBMS_MGWADM`.`CREATE_MSGSYSTEM_LINK` to create a WebSphere MQ link with the desired SSL related link options. At minimum, the `MQ_SSLCIPHERSUITE` property should be set to specify the SSL ciphersuite used by the channel.

- Use `DBMS_MGWADM`.`SET_OPTION` to set certain JSSE Java properties for the Messaging Gateway agent assigned to the link.

JSEE related properties:

- j`ava.net.ssl.keyStore`

  This property is used to specify the location of the keystore. A keystore is a database of key material used for various purposes, including authentication and data integrity.

- `java.net.ssl.keyStorePassword`

  This property is used to specify the password of the keystore. This password is used to check the integrity of the data in the keystore before accessing it.

- j`ava.net.ssl.trustStore`

  This property is used to specify the location of the truststore. A truststore is a keystore that is used when making decisions about which clients and servers are trusted.

- `java.net.ssl.trustStorePassword`

  This property is used to specify the password of the truststore. This password is used to check the integrity of the data in the truststore before accessing it.

The `java`.`net`.`ssl`.`keyStore` and `java`.`net`.`ssl`.`keyStorePassword` properties are only needed if the WebSphere MQ channel is configured to use SSL client authentication.

Example 19-9 configures a WebSphere MQ Base Java link mqssllink to use SSL connections using the `SSL_RSA_WITH_RC4_128_MD5` ciphersuite. It assumes the channel has been configured for SSL client authentication so the Messaging Gateway agent associated with the link, `DEFAULT_AGENT`, is configured with Java properties for both a keystore and a truststore.

This configuration should be done when the Messaging Gateway agent is shut down since the Java properties set by `DBMS_MGWADM`.`SET_OPTION` are set only when the agent first starts. If the agent is running when the configuration is done it will need to be shutdown and restarted before the SSL connections will be used.

**Note:**

"WebSphere MQ System Properties"

Example 19-9 Configuring a WebSphere MQ Base Java Link for SSL

    DECLARE
      v_options sys.mgw_properties;
      v_prop sys.mgw_mqseries_properties;
      v_agent varchar2(30) := 'default_agent';
    BEGIN
         v_prop := sys.mgw_mqseries_properties.construct();
         v_prop.interface_type := DBMS_MGWADM.MQSERIES_BASE_JAVA_INTERFACE;
         v_prop.max_connections := 1;
         v_prop.username := 'mqm';
         v_prop.password := 'mqm';
         v_prop.hostname := 'myhost.mydomain';
         v_prop.port := 1414;
         v_prop.channel := 'mysslchannel';
         v_prop.queue_manager := 'my.queue.manager';
         v_prop.outbound_log_queue := 'mylogq';

       -- specify the SSL ciphersuite
         v_options := sys.mgw_properties(
            sys.mgw_property('MQ_SSLCIPHERSUITE','SSL_RSA_WITH_RC4_128_MD5') );

         -- create the MQSeries link
        DBMS_MGWADM.CREATE_MSGSYSTEM_LINK(linkname => 'mqssllink',
                                        agent_name => v_agent,
                                        properties => v_prop,
                                        options => v_options);

       -- set Java properties for the agent that specify the JSSE security
       -- properties for the keystore and truststore; the paths will be
       -- saved as cleartext and the passwords encrypted

       DBMS_MGWADM.SET_OPTION(target_type  => DBMS_MGWADM.AGENT_JAVA_PROP,
                           target_name  => v_agent,
                           option_name  => 'javax.net.ssl.keyStore',
                           option_value => '/tmp/mq_ssl/key.jks',
                           encrypted    => false);

       DBMS_MGWADM.SET_OPTION(target_type  => DBMS_MGWADM.AGENT_JAVA_PROP,
                           target_name  => v_agent,
                           option_name  => 'javax.net.ssl.keyStorePassword',
                           option_value => 'welcome',
                           encrypted    => true);

       DBMS_MGWADM.SET_OPTION(target_type  => DBMS_MGWADM.AGENT_JAVA_PROP,
                           target_name  => v_agent,
                           option_name  => 'javax.net.ssl.trustStore',
                           option_value => '/tmp/mq_ssl/trust.jks',
                           encrypted    => false);

       DBMS_MGWADM.SET_OPTION(target_type  => DBMS_MGWADM.AGENT_JAVA_PROP,
                           target_name  => v_agent,
                           option_name  => 'javax.net.ssl.trustStorePassword',
                           option_value => 'welcome',
                           encrypted    => true);
    END;

#### Creating a TIB/Rendezvous Link

A TIB/Rendezvous link is created by calling `DBMS_MGWADM.CREATE_MSGSYSTEM_LINK` with three parameters (`service`, `network` and `daemon`) for the agent to create a corresponding transport of `TibrvRvdTransport` type.

A TIB/Rendezvous message system link does not need propagation log queues. Logging information is stored in memory. Therefore, Messaging Gateway can only guarantee at-most-once message delivery.

Example 19-10 configures a TIB/Rendezvous link named `rvlink` that connects to the `rvd` daemon on the local computer. An agent name is not specified for the link so the Messaging Gateway default agent (`DEFAULT_AGENT`) is responsible for the link and all propagation jobs using the link.

**See Also:**

"TIB/Rendezvous System Properties"

Example 19-10 Configuring a TIB/Rendezvous Link

    DECLARE
      v_options sys.mgw_properties;
      v_prop     sys.mgw_tibrv_properties;
    BEGIN
      v_prop := sys.mgw_tibrv_properties.construct();

      DBMS_MGWADM.CREATE_MSGSYSTEM_LINK(linkname => 'rvlink', properties => v_prop);
    END;

#### Altering a Messaging System Link

Using `DBMS_MGWADM.ALTER_MSGSYSTEM_LINK`, you can alter some link information after the link is created. You can alter link information with the Messaging Gateway agent running or shut down. Example 19-11 alters the link `mqlink` to change the `max_connections` property.

**See Also:**

"Configuration Properties" for restrictions on changes when the Messaging Gateway agent is running

Example 19-11 Altering a WebSphere MQ Link

    DECLARE
      v_options sys.mgw_properties;
      v_prop sys.mgw_mqseries_properties;
    BEGIN
      -- use alter_construct() for initialization
      v_prop := sys.mgw_mqseries_properties.alter_construct();
      v_prop.max_connections := 2;

      DBMS_MGWADM.ALTER_MSGSYSTEM_LINK(
        linkname => 'mqlink', properties => v_prop);
    END;

#### Removing a Messaging System Link

You can remove a Messaging Gateway link to a non-Oracle messaging system with `DBMS_MGWADM.REMOVE_MSGSYSTEM_LINK`, but only if all registered queues associated with this link have already been unregistered. The link can be removed with the Messaging Gateway agent running or shut down. Example 19-12 removes the link `mqlink`.

Example 19-12 Removing a Messaging Gateway Link

    BEGIN
      dbms_mgwadm.remove_msgsystem_link(linkname =>'mqlink');
    END;

#### Views for Messaging System Links

You can use the `MGW_LINKS` view to check links that have been created. It lists the name and link type, as shown in Example 19-13.

You can use the `MGW_MQSERIES_LINKS` and `MGW_TIBRV_LINKS` views to check messaging system type-specific configuration information, as shown in Example 19-14.

Example 19-13 Listing All Messaging Gateway Links

    SQL> select link_name, link_type from MGW_LINKS;

    LINK_NAME     LINK_TYPE
    ------------------------
    MQLINK        MQSERIES
    RVLINK        TIBRV

Example 19-14 Checking Messaging System Link Configuration Information

    SQL> select link_name, queue_manager, channel, hostname from mgw_mqseries_links;

    LINK_NAME   QUEUE_MANAGER      CHANNEL     HOSTNAME
    ----------------------------------------------------------
    MQLINK      my.queue.manager  mychannel  myhost.mydomain

    SQL> select link_name, service, network, daemon from mgw_tibrv_links;

    LINK_NAME   SERVICE      NETWORK     DAEMON
    -----------------------------------------------------
    RVLINK

### Configuring Non-Oracle Messaging System Queues

All non-Oracle messaging system queues involved in propagation as a source queue, destination queue, or [exception queue](glossary.md) must be registered through the Messaging Gateway administration interface. You do not need to register Oracle Database Advanced Queuing queues involved in propagation.

This section contains these topics:

- Registering a Non-Oracle Queue

- Unregistering a Non-Oracle Queue

- View for Registered Non-Oracle Queues

#### Registering a Non-Oracle Queue

You can register a non-Oracle queue using `DBMS_MGWADM.REGISTER_FOREIGN_QUEUE`. Registering a non-Oracle queue provides information for the Messaging Gateway agent to access the queue. However, it does not create the physical queue in the non-Oracle messaging system. The physical queue must be created using the non-Oracle messaging system administration interfaces before the Messaging Gateway agent accesses the queue.

The following information is used to register a non-Oracle queue:

- Name of the messaging system link used to access the queue

- Native name of the queue (its name in the non-Oracle messaging system)

- Domain of the queue

  - `DBMS_MGWADM.DOMAIN_QUEUE` for a point-to-point queue

  - `DBMS_MGWADM.DOMAIN_TOPIC` for a publish/subscribe queue

- Options specific to the non-Oracle messaging system

  These options are a set of {name, value} pairs, both of which are strings.

**See Also:**

"Optional Foreign Queue Configuration Properties"

Example 19-15 shows how to register the WebSphere MQ Base Java queue `my_mq_queue` as a Messaging Gateway queue `destq`.

Example 19-15 Registering a WebSphere MQ Base Java Queue

    BEGIN
      DBMS_MGWADM.REGISTER_FOREIGN_QUEUE(
        name            => 'destq',
        linkname        => 'mqlink',
        provider_queue  => 'my_mq_queue',
        domain          => dbms_mgwadm.DOMAIN_QUEUE);
    END;

##### Registering a WebSphere MQ Base Java Queue

The domain must be `DBMS_MGWADM.DOMAIN_QUEUE` or NULL, because only point-to-point queues are supported for WebSphere MQ.

##### Registering a WebSphere MQ JMS Queue or Topic

When registering a WebSphere MQ JMS queue, the domain must be `DBMS_MGWADM.DOMAIN_QUEUE`, and the `linkname` parameter must refer to a WebSphere MQ JMS unified link or queue link.

When registering a WebSphere MQ JMS topic, the domain must be `DBMS_MGWADM.DOMAIN_TOPIC`, and the `linkname` parameter must refer to a WebSphere MQ JMS unified link or topic link. The `provider_queue` for a WebSphere MQ JMS topic used as a propagation source may include wildcards. See WebSphere MQ documentation for [wildcard](glossary.md) syntax.

##### Registering a TIB/Rendezvous Subject

When registering a TIB/Rendezvous subject with Messaging Gateway, the `provider_queue` parameter specifies a TIB/Rendezvous subject name. The domain of a registered TIB/Rendezvous queue must be `DBMS_MGWADM.DOMAIN_TOPIC` or NULL.

A registered TIB/Rendezvous queue with `provider_queue` set to a wildcard subject name can be used as a propagation source queue for inbound propagation. It is not recommended to use queues with wildcard subject names as propagation destination queues or exception queues. As documented in TIB/Rendezvous, sending messages to wildcard subjects can trigger unexpected behavior. However, neither Messaging Gateway nor TIB/Rendezvous prevents you from doing so.

#### Unregistering a Non-Oracle Queue

A non-Oracle queue can be unregistered with `DBMS_MGWADM.UNREGISTER_FOREIGN_QUEUE`, but only if there are no propagation jobs referencing it.

Example 19-16 unregisters the queue `destq` of the link `mqlink`.

Example 19-16 Unregistering a Non-Oracle Queue

    BEGIN
      DBMS_MGWADM.UNREGISTER_FOREIGN_QUEUE(name =>'destq', linkname=>'mqlink');
    END;

#### View for Registered Non-Oracle Queues

You can use the `MGW_FOREIGN_QUEUES` view to check which non-Oracle queues are registered and what link each uses, as shown in Example 19-17.

Example 19-17 Checking Which Queues Are Registered

    SELECT name, link_name, provider_queue FROM MGW_FOREIGN_QUEUES;

    NAME   LINK_NAME   PROVIDER_QUEUE
    ------------------------------------
    DESTQ  MQLINK      my_mq_queue

### Configuring Oracle Messaging Gateway Propagation Jobs

Propagating messages between an Oracle Database AQ queue and a non-Oracle messaging system queue requires a propagation job. Each propagation job will have a unique propagation type, source, and destination triplet.

You can create a propagation job to propagate messages between JMS destinations. You can also create a propagation job to propagate messages between non-JMS queues. Messaging Gateway does not support message propagation between a JMS destination and a non-JMS queue.

This section contains these topics:

- Propagation Job Overview

- Creating an Oracle Messaging Gateway Propagation Job

- Enabling and Disabling a Propagation Job

- Resetting a Propagation Job

- Altering a Propagation Job

- Removing a Propagation Job

#### Propagation Job Overview

A propagation job specifies what messages are propagated and how the messages are propagated.

Messaging Gateway allows bidirectional message propagation. An outbound propagation moves messages from Oracle Database Advanced Queuing to non-Oracle messaging systems. An inbound propagation moves messages from non-Oracle messaging systems to Oracle Database Advanced Queuing.

If the propagation source is a queue (point-to-point), then the Messaging Gateway agent moves all messages from the source queue to the destination queue. If the propagation source is a topic (publish/subscribe), then the Messaging Gateway agent creates a subscriber of the propagation source queue in the messaging system. The agent only moves messages that are published to the source queue after the subscriber is created.

When propagating a message, the Messaging Gateway agent converts the message from the format in the source messaging system to the format in the destination messaging system. Users can customize the message conversion by providing a message [transformation](glossary.md). If message conversion fails, then the message will be moved to an exception queue, if one has been provided, so that the agent can continue to propagate messages for the subscriber.

A Messaging Gateway exception queue is different from an Oracle Database Advanced Queuing exception queue. Messaging Gateway moves a message to a Messaging Gateway exception queue when message conversion fails. Oracle Database Advanced Queuing moves a message to an Oracle Database Advanced Queuing exception queue after `MAX_RETRIES` dequeue attempts on the message.

Messages moved to an Oracle Database Advanced Queuing exception queue may result in irrecoverable failures on the associated Messaging Gateway propagation job. To avoid the problem, the `MAX_RETRIES` parameter of any Oracle Database Advanced Queuing queue that is used as the propagation source of a Messaging Gateway propagation job should be set to a value much larger than 16.

If the messaging system of the propagation source queue supports message selection, then a message selection rule can be specified for a propagation subscriber. Only messages that satisfy the message selector will be propagated.

Users can also specify propagation job options to control how messages are propagated, such as options for [JMS message](glossary.md) delivery mode and TIB/Rendezvous queue policies.

The `MGW_JOBS` view can be used to check the configuration and status of Messaging Gateway propagation jobs.

**See Also:**

[Monitoring Oracle Messaging Gateway](omg-monitoring.md)

#### Creating an Oracle Messaging Gateway Propagation Job

Messaging Gateway propagation jobs are created by `DBMS_MGWADM`.`CREATE_JOB`.

If the propagation source for non-JMS propagation is an Oracle Database AQ queue, then the queue can be either a single consumer queue or multiple consumer queue. If it is a multiple consumer queue, Messaging Gateway creates a corresponding Oracle Database AQ subscriber `MGW_job_name` for the propagation job `job_name` when `DBMS_MGWADM`.`CREATE_JOB` is called.

If the propagation source is a JMS topic, such as an [Oracle Java Message Service](glossary.md) (Oracle JMS) topic or a WebSphere MQ JMS topic, then a JMS subscriber `MGW_job_name` is created on the topic in the source messaging system by the Messaging Gateway agent. If the agent is not running, then the subscriber will not be created until the agent is restarted.

If the propagation source is a queue, then only one propagation job can be created using that queue as the propagation source. If the propagation source is a topic, then multiple propagation jobs can be set up using that topic as the propagation source with each propagation job having its own corresponding subscriber on the topic in the messaging system.

Example 19-18 creates Messaging Gateway propagation job `job_aq2mq`.

**Note:**

If a WebSphere MQ JMS topic is involved in a propagation job and the interface type of the link is `DBMS_MGWADM.JMS_TOPIC_CONNECTION`, then a durable subscriber `MGL_``subscriber_id` is created on the log topic. The durable subscriber is removed when the Messaging Gateway propagation job is successfully removed.

Example 19-18 Creating a Messaging Gateway Propagation Job

    BEGIN
       DBMS_MGWADM.CREATE_JOB(
         job_name            =>  'job_aq2mq',
         propagation_type    =>   DBMS_MGWADM.OUTBOUND_PROPAGATION,
         source              =>  'mquser.srcq',
         destination         =>  'deqq@mqlink');
    END;

#### Enabling and Disabling a Propagation Job

A propagation job can be initially enabled or disabled when it is created by `DBMS_MGWADM`.`CREATE_JOB`. By default, a job is enabled when it is created. You can use `DBMS_MGWADM`.`ENABLE_JOB` to enable a propagation job and `DBMS_MGWADM`.`DISABLE_JOB` to disable a job. No propagation processing will occur when the job is disabled.

Example 19-19 enables the propagation for propagation job `job_aq2mq`.

Example 19-20 disables the propagation for propagation job `job_aq2mq`.

Example 19-19 Enabling a Messaging Gateway Propagation Job

    BEGIN
      DBMS_MGWADM.ENABLE_JOB(job_name => 'job_aq2mq');
    END;

Example 19-20 Disabling a Messaging Gateway Propagation Job

    BEGIN
      DBMS_MGWADM.DISABLE_JOB(job_name => 'job_aq2mq');
    END;

#### Resetting a Propagation Job

When a problem occurs with a propagation job, the Messaging Gateway agent retries the failed operation up to 16 times in an exponential backoff scheme before the propagation job stops. You can use `DBMS_MGWADM.RESET_JOB` to reset the failure count to zero to allow the agent to retry the failed operation immediately.

Example 19-21 resets the failure count for propagation job `job_aq2mq`.

Example 19-21 Resetting a Propagation Job

    BEGIN
      DBMS_MGWADM.RESET_JOB (job_name => 'job_aq2mq');
    END;

#### Altering a Propagation Job

After a propagation job is created you can alter the selection rule, transformation, exception queue, job options, and poll interval of the job using `DBMS_MGWADM`.`ALTER_JOB`. The job can be altered with the Messaging Gateway running or shut down.

Example 19-22 adds an exception queue for a propagation job.

Example 19-23 changes the polling interval for a propagation job. The polling interval determines how soon the agent can discover the available messages in the propagation source queue. The default polling interval is 5 seconds or the value set for `oracle`.`mgw`.`polling_interval` in the Messaging Gateway initialization file.

Example 19-22 Altering Propagation Job by Adding an Exception Queue

    BEGIN
        DBMS_MGWADM.ALTER_JOB(
           job_name         =>  'job_aq2mq',        exception_queue  =>  'mgwuser.my_ex_queue');
    END;

Example 19-23 Altering Propagation Job by Changing the Polling Interval

    BEGIN
        DBMS_MGWADM.ALTER_JOB(
            job_name       =>  'job_aq2mq',         poll_interval  =>  2);
    END;

#### Removing a Propagation Job

You can remove a Messaging Gateway propagation job by calling `DBMS_MGWADM`.`REMOVE_JOB`.

Before removing the propagation job from the Messaging Gateway configuration, Messaging Gateway does the following cleanup:

- Removes from the messaging system the associated subscriber that may have been created by Messaging Gateway

- Removes propagation log records from log queues for the job being removed

Messaging Gateway may fail to do the cleanup because:

- The Messaging Gateway agent is not running

- Non-Oracle messaging system is not running

- The Messaging Gateway agent cannot interact with the source or destination messaging system

If the Messaging Gateway cleanup fails for any reason, then the propagation job being removed is placed in a `DELETE_PENDING` state. The Messaging Gateway agent tries to clean up propagation jobs in a `DELETE_PENDING` state when:

- `DBMS_MGWADM`.`REMOVE_JOB` is called and the Messaging Gateway agent is running.

- The Messaging Gateway agent is starting and finds a propagation job in a `DELETE_PENDING` state.

`DBMS_MGWADM`.`REMOVE_JOB` has a force parameter that allows you to force the propagation job to be removed from the Messaging Gateway configuration without placing it in `DELETE_PENDING` state. This is useful in case of cleanup failures or if you want to remove a propagation job when the Messaging Gateway agent is not running.

Forcing a propagation job to be removed may result in obsolete log records being left in the log queues, and subscriptions in the messaging systems that may cause unnecessary message accumulation. Oracle recommends that the force option not be used for `DBMS_MGWADM`.`REMOVE_JOB` if possible.

Example 19-24 removes a propagation job in a non-forced manner.

Example 19-24 Removing a Propagation Job

    BEGIN
        DBMS_MGWADM.REMOVE_JOB (job_name  =>  'job_aq2mq');
    END;

### Propagation Jobs, Subscribers, and Schedules

Subprograms are provided as part of the `DBMS_MGWADM` package that simplify the creation and management of propagation jobs. Those subprograms allow a user to configure a propagation job rather than a disjoint subscriber and schedule as was done in prior releases. Oracle recommends that you use the propagation job procedures but still supports the subscriber and schedule procedures for backward compatibility.

Table 19-1 lists the Messaging Gateway propagation job procedures and shows which subscriber and/or schedule procedures it replaces. All procedures are from the `DBMS_MGWADM` package.

Table 19-1 Messaging Gateway Propagation Job Subprograms

| Job Procedure | Replaces Subscriber, Schedule Procedure          |
|:--------------|:-------------------------------------------------|
| `CREATE_JOB`  | `ADD_SUBSCRIBER`, `SCHEDULE_PROPAGATION`         |
| `ALTER_JOB`   | `ALTER_SUBSCRIBER`, `ALTER_PROPAGATION_SCHEDULE` |
| `REMOVE_JOB`  | `REMOVE_SUBSCRIBER`, `UNSCHEDULE_PROPAGATION`    |
| `ENABLE_JOB`  | `ENABLE_PROPAGATION_SCHEDULE`                    |
| `DISABLE_JOB` | `DISABLE_PROPAGATION_SCHEDULE`                   |
| `RESET_JOB`   | `RESET_SUBSCRIBER`                               |

This section contains the following topics:

- Propagation Job\_ Subscriber\_ Schedule Interface Interoperability

- Propagation Job\_ Subscriber\_ Schedule Views

- Single Consumer Queue as Propagation Source

#### Propagation Job, Subscriber, Schedule Interface Interoperability

The user can create two types of propagation jobs, a new style job or an old style job. A new style job is created by `DBMS_MGWADM`.`CREATE_JOB`. An old style job is created by calling `DBMS_MGWADM`.`ADD_SUBSCRIBER` and `DBMS_MGWADM`.`SCHEDULE_PROPAGATION` using the same {`propagation_type`, `source`, `destination`} triplet. A subscriber that does not have a matching schedule, or a schedule that does not have a matching subscriber, is not considered to be a propagation job.

For new style job, the job name will serve as both the subscriber ID and the schedule ID. For an old style job, the subscriber ID is used as the job name.

Both the propagation job subprograms and the subscriber/schedule subprograms can be used for old style propagation jobs. Oracle recommends that you use the job subprograms to create and manage propagation jobs. The job subprograms cannot be used for an unmatched subscriber or schedule since those do not constitute a propagation job.

Only the new job subprograms can be used for new style propagation jobs. An error will occur if a user tries to call a subscriber or scheduler procedure on a new style job.

Other than `DBMS_MGWADM`.`REMOVE_JOB`, calling the job subprograms for an old style job is straightforward and the results are effectively the same as calling the corresponding subscriber/schedule subprograms. There may be certain restrictions in the future but there are none at this time.

The `DBMS_MGWADM`.`REMOVE_JOB` procedure can be used to remove both new style and old style jobs. A forced and non-forced remove is supported. If the Messaging Gateway agent is not running when a non-forced remove is done, the job will be flagged as delete pending and neither the underlying subscriber nor schedule will be removed at that time. The job (subscriber /schedule pair) will be removed once the agent is restarted and performs its cleanup work or a forced `DBMS_MGWADM`.`REMOVE_JOB` is performed. In order to insure that the subscriber/schedule pair is removed at the same time, an error will occur if you first call `DBMS_MGWADM`.`REMOVE_JOB` and subsequently attempt to call `DBMS_MGWADM`.`REMOVE_SUBSCRIBER` or `DBMS_MGWADM`.`UNSCHEDULE_PROPAGATION` for an old style job.

Once `DBMS_MGWADM`.`REMOVE_JOB` as been called for a job and it has been flagged as delete pending, all job procedures, other than `DBMS_MGWADM`.`REMOVE_JOB`, will fail for both new style and old style jobs. In addition, all subscriber and schedule subprograms will fail if the propagation job happens to be an old style job.`DBMS_MGWADM`.`REMOVE_SUBSCRIBER` and `DBMS_MGWADM`.`UNSCHEDULE_PROPAGATION` can be used for an old style job as long as `DBMS_MGWADM`.`REMOVE_JOB` has not been called for that job. If `DBMS_MGWADM`.`UNSCHEDULE_PROPAGATION` is called for an old style job, the schedule is immediately removed and it ceases to be a propagation job and `DBMS_MGWADM`.`REMOVE_SUSCRIBER` must be used to remove the subscriber. If `DBMS_MGWADM`.`REMOVE_SUBSCRIBER` is called for an old style job, the user can subsequently call `DBMS_MGWADM`.`REMOVE_JOB` as long as the subscriber exists.

#### Propagation Job, Subscriber, Schedule Views

The `MGW_JOBS` view shows information for the current propagation jobs, both new style jobs and old style jobs, and includes all the pertinent information shown by the `MGW_SUBSCRIBERS` and `MGW_SCHEDULES` views. The `MGW_SUBSCRIBERS` and `MGW_SCHEDULES` views are still useful for finding an unmatched subscriber or schedule since they don't constitute a propagation job and will not show up in the `MGW_JOBS` view.

#### Single Consumer Queue as Propagation Source

Messaging Gateway allows an Oracle Database AQ multiple consumer queue or a single consumer queue to be a propagation source for an outbound new style job created by `DBMS_MGWADM`.`CREATE_JOB`. A multiple consumer queue must be used for the propagation source for an outbound old style job. An error will occur if an administrator attempts to call `DBMS_MGWADM`.`ADD_SUBSCRIBER` and the source is a single consumer queue.

An Oracle Database AQ dequeue condition is not supported for native (non-JMS) outbound propagation when the propagation source is a single consumer queue.

### Configuration Properties

This section summarizes basic and optional properties related to Messaging Gateway links, foreign queues, and propagation jobs.

This section contains these topics:

- WebSphere MQ System Properties

- TIB/Rendezvous System Properties

- Optional Link Configuration Properties

- Optional Foreign Queue Configuration Properties

- Optional Job Configuration Properties

#### WebSphere MQ System Properties

Table 19-2 summarizes the basic configuration properties for a WebSphere MQ messaging link. The table indicates which properties of `SYS.MGW_MQSERIES_PROPERTIES` are optional (`NULL` allowed), which can be altered, and if alterable, which values can be dynamically changed.

**See Also:**

"SYS.MGW_MQSERIES_PROPERTIES Type" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWMSG.md)

Table 19-2 WebSphere MQ Link Properties

| Attribute            | NULL Allowed? | Alter Value? | Dynamic? |
|:---------------------|:--------------|:-------------|:---------|
| `queue_manager`      | no            | no           | no       |
| `hostname`           | yes (1)       | no           | no       |
| `port`               | yes (1)       | no           | no       |
| `channel`            | yes (1), (6)  | yes          | no       |
| `interface_type`     | yes (2)       | no           | no       |
| `max_connections`    | yes (3)       | yes          | yes      |
| `username`           | yes           | yes          | yes      |
| `password`           | yes           | yes          | yes      |
| `inbound_log_queue`  | yes (4)       | yes(4)       | yes      |
| `outbound_log_queue` | yes (5)       | yes(5)       | yes      |

##### Notes on Table 19-2

- If `hostname` is `NULL`, then the port and channel must be `NULL`. If the hostname is not `NULL`, then the port must be not `NULL`. If the hostname is `NULL`, then a WebSphere MQ bindings connection is used; otherwise a client connection is used.

- If `interface_type` is `NULL`, then a default value of `DBMS_MGWADM.MQSERIES_BASE_JAVA_INTERFACE` is used.

- If `max_connections` is `NULL`, then a default value of `1` is used.

- Attribute `inbound_log_queue` can be `NULL` if the link is not used for inbound propagation. The log queue can be altered only when no inbound propagation job references the link.

- Attribute `outbound_log_queue` can be `NULL` if the link is not used for outbound propagation. The log queue can be altered only when no outbound propagation job references the link.

- The channel attribute must be `NULL` if a client channel definition table (CCDT) is used. The `MQ_ccdtURL` link option can be used to specify a CCDT.

Table 19-3 summarizes the optional configuration properties supported when a WebSphere MQ Base Java interface is used to access the WebSphere MQ messaging system. Table 19-4 summarizes the optional configuration properties supported when a WebSphere MQ JMS interface is used. Each table lists the property name, where that property applies, whether the property can be altered, and if alterable, whether the value can be dynamically changed. Only the properties listed in the tables are supported, and any extra properties are ignored.

Table 19-3 Optional Configuration Properties for WebSphere MQ Base Java

| Property Name        | Used For      | Alter Value? | Dynamic? |
|:---------------------|:--------------|:-------------|:---------|
| "MQ_ccdtUrl"         | link          | yes          | no       |
| "MQ_ccsid"           | link          | yes          | no       |
| "MQ_ReceiveExit"     | link          | yes          | no       |
| "MQ_SecurityExit"    | link          | yes          | no       |
| "MQ_SendExit"        | link          | yes          | no       |
| "MQ_SSLCipherSuite"  | link          | yes          | no       |
| "MQ_SSLFipsRequired" | link          | yes          | no       |
| "MQ_SSLPeerName"     | link          | yes          | no       |
| "MQ_SSLResetCount"   | link          | yes          | no       |
| "MQ_openOptions"     | foreign queue | no           | no       |
| "MsgBatchSize"       | job           | yes          | yes      |
| "PreserveMessageID"  | job           | yes          | yes      |

Table 19-4 Optional Configuration Properties for WebSphere MQ JMS

| Property Name           | Used For      | Alter Value? | Dynamic? |
|:------------------------|:--------------|:-------------|:---------|
| "MQ_BrokerControlQueue" | link          | yes          | no       |
| "MQ_BrokerPubQueue"     | link          | yes          | no       |
| "MQ_BrokerQueueManager" | link          | yes          | no       |
| "MQ_BrokerVersion"      | link          | yes          | no       |
| "MQ_ccdtUrl"            | link          | yes          | no       |
| "MQ_ccsid"              | link          | yes          | no       |
| "MQ_JmsDurSubQueue"     | link          | no           | no       |
| "MQ_PubAckInterval"     | link          | yes          | no       |
| "MQ_ReceiveExit"        | link          | yes          | no       |
| "MQ_ReceiveExitInit"    | link          | yes          | no       |
| "MQ_SecurityExit"       | link          | yes          | no       |
| "MQ_SecurityExitInit"   | link          | yes          | no       |
| "MQ_SendExit"           | link          | yes          | no       |
| "MQ_SendExitInit"       | link          | yes          | no       |
| "MQ_SSLCipherSuite"     | link          | yes          | no       |
| "MQ_SSLCrl"             | link          | yes          | no       |
| "MQ_SSLFipsRequired"    | link          | yes          | no       |
| "MQ_SSLPeerName"        | link          | yes          | no       |
| "MQ_SSLResetCount"      | link          | yes          | no       |
| "MQ_CharacterSet"       | foreign queue | no           | no       |
| "MQ_JmsDurSubQueue"     | foreign queue | no           | no       |
| "MQ_JmsTargetClient"    | foreign queue | no           | no       |
| "JMS_DeliveryMode"      | job           | yes          | yes      |
| "JMS_NoLocal"           | job           | no           | no       |
| "MsgBatchSize"          | job           | yes          | yes      |
| "PreserveMessageID"     | job           | yes          | yes      |

#### TIB/Rendezvous System Properties

Table 19-5 summarizes the basic configuration properties for a TIB/Rendezvous messaging link. It indicates which properties of `SYS.MGW_TIBRV_PROPERTIES` are optional (`NULL` allowed), which can be altered, and if alterable, which values can be dynamically changed.

**See Also:**

"SYS.MGW_TIBRV_PROPERTIES Type" in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MGWMSG.md)

Table 19-5 TIB/Rendezvous Link Properties

| Attribute   | NULL allowed? | Alter value? | Dynamic? |
|:------------|:--------------|:-------------|:---------|
| `service`   | yes(1)        | no           | no       |
| `daemon`    | yes(1)        | no           | no       |
| `network`   | yes(1)        | no           | no       |
| `cm_name`   | yes(2)        | no           | no       |
| `cm_ledger` | yes(2)        | no           | no       |

##### Notes on Table 19-5:

- System default values will be used if `service`, `daemon`, or `network` are `NULL`.

- The `cm_name` and `cm_ledger` attributes are reserved for future use when TIB/Rendezvous certified messages are supported. At present, a `NULL` must be specified for these parameters when a TIB/Rendezvous link is configured.

Table 19-6 summarizes the optional configuration properties supported when a TIB/Rendezvous messaging system is used. The table lists the property name, where that property applies, whether the property can be altered, and if alterable, whether the value can be dynamically changed. Only the properties listed in the table are supported, and any extra properties will be ignored.

Table 19-6 Optional Properties for TIB/Rendezvous

| Property Name       | Used For | Alter Value? | Dynamic? |
|:--------------------|:---------|:-------------|:---------|
| "AQ_MsgProperties"  | job      | yes          | yes      |
| "MsgBatchSize"      | job      | yes          | yes      |
| "PreserveMessageID" | job      | yes          | yes      |
| "RV_discardAmount"  | job      | yes          | no       |
| "RV_limitPolicy"    | job      | yes          | no       |
| "RV_maxEvents"      | job      | yes          | no       |

#### Optional Link Configuration Properties

This section describes optional link properties you can specify using the `options` parameter of `DBMS_MGWADM.CREATE_MSGSYSTEM_LINK` and `DBMS_MGWADM.ALTER_MSGSYSTEM_LINK`. Each listing also indicates which messaging system might use that property.

MQ_BrokerControlQueue
This property is used by WebSphere MQ JMS. It specifies the name of the broker control queue and corresponds to WebSphere MQ JMS administration tool property `BROKERCONQ`. The WebSphere MQ default is `SYSTEM.BROKER.CONTROL.QUEUE`.

MQ_BrokerPubQueue
This property is used by WebSphere MQ JMS. It specifies the name of the broker publish queue and corresponds to WebSphere MQ JMS administration tool property `BROKERPUBQ`. The WebSphere MQ default is `SYSTEM.BROKER.DEFAULT.STREAM`.

MQ_BrokerQueueManager
This property is used by WebSphere MQ JMS. It specifies the name of the broker queue manager and corresponds to WebSphere MQ administration tool property `BROKERQMGR`. If it is not set, then no default is used.

MQ_BrokerVersion
This property is used by WebSphere MQ JMS. It specifies the broker version number and corresponds to WebSphere MQ JMS administration tool property `BROKERVER`. The WebSphere MQ default is `0`.

MQ_ccdtUrl
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the URL string of a client channel definition table (CCDT) to be used. If not set, a CCDT is not used. If a CCDT is used, then the `SYS`.`MGW_MQSERIES_PROPERTIES`.`channel` link property must be `NULL`.

MQ_ccsid
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the character set identifier to be used to translate information in the WebSphere MQ message header. This should be the integer value of the character set (for example, `819`) rather than a descriptive string. If it is not set, then the WebSphere MQ default character set `819` is used.

MQ_JmsDurSubQueue
This property is used by WebSphere MQ JMS. It applies to WebSphere MQ JMS topic links only. The `SYS.MGW_MQSERIES_PROPERITES` attributes, `inbound_log_queue` and `outbound_log_queue`, specify the names of WebSphere MQ JMS topics used for propagation logging. This property specifies the name of the WebSphere MQ queue from which durable subscription messages are retrieved by the log topic subscribers. The WebSphere MQ default queue is `SYSTEM.JMS.D.SUBSCRIBER.QUEUE`.

MQ_PubAckInterval
This property is used by WebSphere MQ JMS. It specifies the interval, in number of messages, between publish requests that require acknowledgment from the broker and corresponds to WebSphere MQ JMS administration tool property `PUBACKINT`. The WebSphere MQ default is `25`.

MQ_ReceiveExit
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the fully qualified Java classname of a class implementing the `MQReceiveExit` interface. This class must be in the `CLASSPATH` of the Messaging Gateway agent. There is no default.

MQ_ReceiveExitInit
This initialization string is used by WebSphere MQ JMS. It is passed by WebSphere MQ JMS to the constructor of the class specified by `MQ_ReceiveExit` and corresponds to WebSphere MQ JMS administration tool property `RECEXITINIT`. There is no default.

MQ_SecurityExit
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the fully qualified Java classname of a class implementing the `MQSecurityExit` interface. This class must be in the `CLASSPATH` of the Messaging Gateway agent. There is no default.

MQ_SecurityExitInit
This initialization string is used by WebSphere MQ JMS. It is passed by WebSphere MQ JMS to the constructor of the class specified by `MQ_SecurityExit` and corresponds to WebSphere MQ JMS administration tool property `SECEXITINIT`. There is no default.

MQ_SendExit
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the fully qualified Java classname of a class implementing the `MQSendExit` interface. This class must be in the `CLASSPATH` of the Messaging Gateway agent. There is no default.

MQ_SendExitInit
This initialization string is used by WebSphere MQ JMS. It is passed by WebSphere MQ JMS to the constructor of the class specified by `MQ_SendExit`. It corresponds to WebSphere MQ JMS administration tool property `SENDEXITINIT`. There is no default.

MQ_SSLCipherSuite
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the CipherSuite to be used; for example, `SSL_RSA_WITH_RC4_128_MD5`. This corresponds to the WebSphere MQ `SSLCIPHERSUITE` administration property.

MQ_SSLCrl
This property is used by WebSphere MQ JMS. It specifies a space-delimited list of LDAP servers that can be used for certificate revocation list (CRL) checking. If not set, no CRL checking is done. This corresponds to the WebSphere MQ `SSLCRL` administration property. This option is not supported for WebSphere MQ Base Java, and instead, a client channel definition table (CCDT) must be used if CRL checking is needed.

MQ_SSLFipsRequired
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It indicates whether the CipherSuite being used is supported by the IBM Java JSSE FIPS provider (IBMSJSSEFIPS). The value should be `TRUE` or `FALSE`. The default value is `FALSE`. This corresponds to the WebSphere MQ `SSLFIPSREQUIRED` administration property.

MQ_SSLPeerName
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies a distinguished name (DN) pattern that the queue manager certificate must match in order for a connection to be established. If not set, no DN check is performed. This corresponds to the WebSphere MQ `SSLPEERNAME` administration property.

MQ_SSLResetCount
This property is used by WebSphere MQ Base Java and WebSphere MQ JMS. It specifies the total number of bytes sent and received before the secret key is renegotiated. If not set, the key is not renegotiated. This corresponds to the WebSphere MQ `SSLRESETCOUNT` administration property.

#### Optional Foreign Queue Configuration Properties

This section describes optional foreign queue properties that you can specify using the `options` parameter of `DBMS_MGWADM`.`REGISTER_FOREIGN_QUEUE`. Each listing also indicates which messaging system might use that property.

MQ_CharacterSet
This property is used by WebSphere MQ JMS. It is used only for outbound propagation to a JMS queue or topic. It specifies the character set to be used to encode text strings sent to the destination. It should be the integer value of the character set (for example, `1208`) rather than a descriptive string. The default value used by Messaging Gateway is `1208` (UTF8).

MQ_JmsDurSubQueue
This property is used by WebSphere MQ JMS. It is a string representing the name of the WebSphere MQ queue from which durable subscription messages are retrieved by subscribers on this topic. It applies only to WebSphere MQ JMS topics. The WebSphere MQ default queue is `SYSTEM.JMS.D.SUBSCRIBER.QUEUE`.

MQ_JmsTargetClient
This property is used by WebSphere MQ JMS. It is used only for outbound propagation to a JMS queue or topic. Supported values are `TRUE` and `FALSE`. `TRUE` indicates that WebSphere MQ should store the message as a JMS message. `FALSE` indicates that WebSphere MQ should store the message in non-JMS format so that non-JMS applications can access it. Default is `TRUE`.

MQ_openOptions
This property is used by WebSphere MQ Base Java. It specifies the value used for the `openOptions` argument of the WebSphere MQ Base Java `MQQueueManager.accessQueue` method. No value is required. But if one is given, then the Messaging Gateway agent adds `MQOO_OUTPUT` to the specified value for an enqueue (`put`) operation. `MQOO_INPUT_SHARED` is added for a dequeue (`get`) operation. The default is `MQOO_OUTPUT` for an enqueue/put operation; `MQOO_INPUT_SHARED` for a dequeue/get operation.

#### Optional Job Configuration Properties

This section describes optional propagation job properties that you can specify using the options parameter of `DBMS_MGWADM`.`CREATE_JOB` and `DBMS_MGWADM`.`ALTER_JOB`.

AQ_MsgProperties
This property is used by TIB/Rendezvous. It specifies how Oracle Database AQ message properties will be used during message propagation. Supported values are `TRUE` and `FALSE`. The default value is `FALSE`.

For an outbound propagation job, if the value is `TRUE` (case insensitive), then the Messaging Gateway agent will add a field for most Oracle Database AQ message properties to the message propagated to the TIB/Rendezvous subject.

For an inbound propagation job, if the value is `TRUE` (case insensitive), then the Messaging Gateway agent will search the source message for a field with a reserved name, and if it exists, use its value to set the corresponding Oracle Database AQ message property. A default value will be used if the field does not exist or does not have an expected datatype.

JMS_DeliveryMode
This property is used by WebSphere MQ JMS and Oracle JMS. You can use this property when the propagation destination is a JMS messaging system. It sets the delivery mode of messages enqueued to the propagation destination queue by a JMS `MessageProducer`. The default is `PRESERVE_MSG`. Supported values and their associated delivery modes are:

- `PERSISTENT` (`DeliveryMode.PERSISTENT`)

- `NON_PERSISTENT` (`DeliveryMode.NON_PERSISTENT`)

- `PRESERVE_MSG` (delivery mode of the source JMS message is used)

JMS_NoLocal
This property is used by WebSphere MQ JMS and Oracle JMS. You can use it when the propagation source is a JMS messaging system. It sets the `noLocal` parameter of a JMS `TopicSubscriber`. `TRUE` indicates that messages that have been published to this topic through the same Messaging Gateway link will not be propagated. The default value `FALSE` indicates that such messages will be propagated from the topic.

MsgBatchSize
This property can be used by any supported messaging system. It specifies the maximum number of messages, if available, to be propagated in one transaction. The default is 30.

PreserveMessageID
This property is used by WebSphere MQ Base Java, WebSphere MQ JMS, TIB/Rendezvous, and Oracle JMS. It specifies whether Messaging Gateway should preserve the original message identifier when the message is propagated to the destination messaging system. The exact details depend on the capabilities of the messaging systems involved. Supported values are `TRUE` and `FALSE`. The default value is `FALSE`.

RV_discardAmount
This property is used by TIB/Rendezvous. It specifies the discard amount of a queue. It is meaningful only for an inbound propagation job. The default is 0.

RV_limitPolicy
This property is used by TIB/Rendezvous. It specifies the limit policy for resolving overflow of a queue limit. It is meaningful only for an inbound propagation job. The default is `DISCARD_NONE`. Supported values and their associated limit policies are: `DISCARD_NONE`, `DISCARD_FIRST`, `DISCARD_LAST` and `DISCARD_NEW`.

- `DISCARD_NONE` (`TibrvQueue.DISCARD_NONE`)

- `DISCARD_FIRST` (`TibrvQueue.DISCARD_FIRST`)

- `DISCARD_LAST` (`TibrvQueue.DISCARD_LAST`)

- `DISCARD_NEW` (`TibrvQueue.DISCARD_NEW`)

RV_maxEvents
This property is used by TIB/Rendezvous. It specifies the maximum event limit of a queue. It is meaningful only for an inbound propagation job. The default is 0.
