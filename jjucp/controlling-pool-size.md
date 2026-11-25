UCP JDBC connection pools include a set of properties that are used to control the size of the pool. The properties allow the number of connections in the pool to increase and decrease as demand increases and decreases. This dynamic behavior helps conserve system resources that are otherwise lost on maintaining unnecessary connections.

This section describes the following topics:

- Setting the Initial Pool Size

- Setting the Minimum Pool Size

- Setting the Maximum Pool Size

### 4.2.1 Setting the Initial Pool Size

The initial pool size property specifies the number of available connections that are created when the connection pool is initially created or re-initialized. This property is typically used to reduce the ramp-up time incurred by priming the pool to its optimal size.

A value of `0` indicates that no connections are pre-created. The default value is `0`. The following example demonstrates configuring an initial pool size:

    pds.setInitialPoolSize(5);

If the initial pool size property is greater than the maximum pool size property, then only the maximum number of connections are initialized.

If the initial pool size property is less than the minimum pool size property, then only the initial number of connections are initialized and maintained until enough connections are created to meet the minimum pool size value.

### 4.2.2 Setting the Minimum Pool Size

The minimum pool size property specifies the minimum amount of available connections and borrowed connections that a pool maintains. A connection pool always tries to return to the minimum pool size specified unless the minimum amount is yet to be reached. For example, if the minimum limit is set to `10` and only 2 connections are ever created and borrowed, then the number of connections maintained by the pool remains at `2` because this number is less than the minimum pool size.

This property allows the number of connections in the pool to decrease as demand decreases. At the same time, the property ensures that system resources are not wasted on maintaining connections that are unnecessary.

The default value is `0`. The following example demonstrates configuring a minimum pool size:

    pds.setMinPoolSize(2);

### 4.2.3 Setting the Maximum Pool Size

The maximum pool size property specifies the maximum number of available and borrowed (in use) connections that a pool maintains. If the maximum number of connections are borrowed, no connections will be available until a connection is returned to the pool.

This property allows the number of connections in the pool to increase as demand increases. At the same time, the property ensures that the pool does not grow to the point of exhausting the resources of a system, which ultimately affects the performance and availability of an application.

A value of `0` indicates that no connections are maintained by the pool. An attempt to get a connection results in an exception. The default value is to allow the pool to continue to create connections up to `Integer.MAX_VALUE` (2147483647 by default). The following example demonstrates configuring a maximum pool size:

    pds.setMaxPoolSize(100);
