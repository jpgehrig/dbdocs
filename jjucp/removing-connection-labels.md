The `removeConnectionLabel` method is used to remove a label from a connection. This method is used after a labeled connection is borrowed from the connection pool. The following example demonstrates removing a connection label.

    String pname = "property1";
    String pvalue = "value";
    Properties label = new Properties();
    label.setProperty(pname, pvalue);
    Connection conn = pds.getConnection(label);
    ((LabelableConnection) conn).removeConnectionLabel(pname);
