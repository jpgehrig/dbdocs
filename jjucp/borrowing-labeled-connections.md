A pool-enabled data source provides two `getConnection` methods that are used to borrow a labeled connection from the pool. The methods are shown below:

    public Connection getConnection(java.util.Properties labels )
       throws SQLException;

    public Connection getConnection( String user, String password,
                                     java.util.Properties labels )
       throws SQLException;

The methods require that the label be passed to the `getConnection` method as a `Properties` object. The following example demonstrates getting a connection with the label `property1, value`.

    String pname = "property1";
    String pvalue = "value";
    Properties label = new Properties();
    label.setProperty(pname, pvalue);

    Connection conn = pds.getConnection(label);
