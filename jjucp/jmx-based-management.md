JMX (Java Management Extensions) is a Java technology that supplies tools for managing and monitoring applications, system objects, devices, service-oriented networks, and JVM (Java Virtual Machine). In JMX, a given resource is instrumented by one or more Java objects known as MBeans (Managed Beans). An MBean is composed of an MBean interface and a class. The MBean interface lists the methods for all exposed attributes and operations. The class implements this interface and provides the functionality of the instrumented resource.

The MBeans are registered in a core managed object server, known as an MBean server, which acts as a management agent and can run on most devices enabled for the Java programming language. A JMX agent consists of an MBean server, in which MBeans are registered, and a set of services for handling MBeans.

**See Also:**

- <https://docs.oracle.com/javase/tutorial/jmx/mbeans/standard.html>

- [Oracle Universal Connection Pool Java API Reference](../jjuar/index.md)

UCP provides the following two MBeans for pool management support:

- UniversalConnectionPoolManagerMBean

- UniversalConnectionPoolMBean

**Note:**

All MBean attributes and operations are available only when the `UniversalConnectionPoolManager.isJmxEnabled `method returns `true`. The default value of this flag is `true`. This default value can be altered by calling the `UniversalConnectionPoolManager.setJmxEnabled` method. When an MBeanServer is not available, the `jmxFlag` is automatically set to `false`.

### 7.2.1 UniversalConnectionPoolManagerMBean

The `UniversalConnectionPoolManagerMBean` is a manager MBean that includes all the functionalities of a conventional connection pool manager. The `UniversalConnectionPoolManagerMBean` provides the following functionalities:

- Registering and unregistering pool MBeans

- Pool management operations like starting the pool, stopping the pool, refreshing the pool, and so on

- Starting and stopping DMS statistics

- Logging

### 7.2.2 UniversalConnectionPoolMBean

The `UniversalConnectionPoolMBean` is a pool MBean that covers dynamic configuration of pool properties and pool statistics. The `UniversalConnectionPoolMBean` provides the following functionalities:

- Configuring pool property attributes like size, timeouts, and so on

- Pool management operations like refreshing the pool, recycling the pool, and so on

- Monitoring pool statistics and life cycle states
