Third-party products, such as middleware platforms or frameworks, can use UCP to provide connection pooling functionality for their applications and services. UCP integration includes the same connection pool features that are available to stand-alone applications and offers the same tight integration with the Oracle Database.

Two data source classes are available as integration points with UCP: `PoolDataSourceImpl` for non-XA connection pools and `PoolXADataSourceImpl` for XA connection pools. Both classes are located in the `oracle.ucp.jdbc` package. These classes are implementations of the `PoolDataSource` and `PoolXADataSource` interfaces, respectively, and contain default constructors.

**See Also:**

[Oracle Universal Connection Pool Java API Reference](../jjuar/index.md) for more information on the implementation classes.

These implementations explicitly create connection pool instances and can return connections. For example:

    PoolXADataSource pds = new PoolXADataSourceImpl();

    pds.setConnectionFactoryClassName("oracle.jdbc.xa.client.OracleXADataSource");
    pds.setURL("jdbc:oracle:thin:@//localhost:1521/XE");
    pds.setUser("user");
    pds.setPassword("password");

    XAConnection conn = pds.getXAConnection();

Third-party products can instantiate these data source implementation classes. In addition, the methods of these interfaces follow the JavaBean design pattern and can be used to set connection pool properties on the class using reflection. For example, a UCP data source that uses an Oracle JDBC connection factory and database might be defined as follows and loaded into a JNDI registry:

    <data-sources>
       <data-source
          name="UCPDataSource"
          jndi-name="jdbc/UCP_DS"
          data-source-class="oracle.ucp.jdbc.PoolDataSourceImpl">
          <property name="ConnectionFactoryClassName"
                    value="oracle.jdbc.pool.OracleDataSource"/>
          <property name="URL" value="jdbc:oracle:thin:@//localhost:1521:oracle"/>
          <property name="User" value"user"/>
          <property name="Password" value="password"/>
          <property name="ConnectionPoolName" value="MyPool"/>
          <property name="MinPoolSize" value="5"/>
          <property name="MaxPoolSize" value="50"/>
       </data-source>
    </data-sources>

When using reflection, the name attribute matches (case sensitive) the name of the setter method used to set the property. An application could then use the data source as follows:

    Connection connection = null;
    try {
       InitialContext context = new InitialContext();
       DataSource ds = (DataSource) context.lookup( "jdbc/UCP_DS" );
       connection = ds.getConnection();
       ...
