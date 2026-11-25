Borrowed connections that are no longer being used should be returned to the pool so that they can be available for the next connection request. The `close` method closes connections and automatically returns them to the pool. The `close` method does not physically remove the connection from the pool.

Borrowed connections that are not closed will remain borrowed; subsequent requests for a connection result in a new connection being created if no connections are available. This behavior can cause many connections to be created and can affect system performance.

The following example demonstrates closing a connection and returning it to the pool:

    Connection conn = pds.getConnection();

    //do some work with the connection.

    conn.close();
    conn=null;
