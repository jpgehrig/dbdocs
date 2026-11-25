UCP uses Database Resident Connection Pooling (DRCP) tagging infrastructure to support labeling in UCP, whether you work with single labels or multiple labels. However, the behavior with multiple labels can be a little different when you use the UCP and DRCP combination instead of only UCP.

This section discusses the following topics:

- When to Use a Labeling Callback in UCP

- Creating a Labeling Callback in UCP

- Registering a Labeling Callback in UCP

- Removing a Labeling Callback in UCP

**See Also:**

"[Integration of UCP with DRCP](ucp-drcp-integration.md)"

### 5.2.1 When to Use a Labeling Callback in UCP

A labeling callback is used to define how the connection pool selects labeled connections and allows the selected connection to be configured before returning it to an application. Applications that use the connection labeling feature must provide a callback implementation.

A labeling callback is used when a labeled connection is requested but there are no connections in the pool that match the requested labels. The callback determines which connection requires the least amount of work in order to be re-configured to match the requested label and then enables the connection labels to be updated before returning the connection to the application. This section describes the following topics:

### 5.2.2 Creating a Labeling Callback in UCP

To create a labeling callback, an application implements the `oracle.ucp.ConnectionLabelingCallback` interface. One callback is created per connection pool. The interface provides the following two methods:

- The cost Method

- The configure Method

#### The cost Method

This method projects the cost of configuring connections considering label-matching differences. Upon a connection request, the connection pool uses this method to select a connection with the least configuration cost.

    public int cost(Properties requestedLabels, Properties currentLabels);

#### The configure Method

This method is called by the connection pool on the selected connection before returning it to the application. The method is used to set the state of the connection and apply or remove any labels to/from the connection.

    public boolean configure(Properties requestedLabels, Connection conn);

The connection pool iterates over each connection available in the pool. For each connection, it calls the `cost` method. The result of the `cost` method is an `integer` which represents an estimate of the cost required to reconfigure the connection to the required state. The larger the value, the costlier it is to reconfigure the connection. The connection pool always returns connections with the lowest cost value. The algorithm is as follows:

- If the `cost` method returns `0` for a connection, then the connection is a match. The connection pool does not call the `configure` method on the connection found and returns the connection as it is.

- If the `cost` method returns a value greater than `0`, then the connection pool iterates until it finds a connection with a cost value of `0` or runs out of available connections.

- If the pool has iterated through all available connections and the lowest cost of a connection is `Integer.MAX_VALUE` (2147483647 by default), then no connection in the pool is able to satisfy the connection request. The pool creates and returns a new connection. If the pool has reached the maximum pool size (it cannot create a new connection), then the pool either throws an SQL exception or waits if the connection wait timeout attribute is specified.

- If the pool has iterated through all available connections and the lowest cost of a connection is less than `Integer.MAX_VALUE`, then the `configure` method is called on the connection and the connection is returned. If multiple connections are less than `Integer.MAX_VALUE`, the connection with the lowest cost is returned.

**Note:**

A cost of `0` does not imply that `requestedLabels` equals `currentLabels`.

#### 5.2.2.1 Example of Labeling Callback in UCP

The following example demonstrates a simple labeling callback implementation that implements both the `cost` and `configure` methods. The callback is used to find a labeled connection that is initialized with a specific transaction isolation level.

    class MyConnectionLabelingCallback
      implements ConnectionLabelingCallback {

      public MyConnectionLabelingCallback()
      {
      }

      public int cost(Properties reqLabels, Properties currentLabels)
      {
        // Case 1: exact match
        if (reqLabels.equals(currentLabels))
        {
          System.out.println("## Exact match found!! ##");
          return 0;
        }

        // Case 2: some labels match with no unmatched labels
        String iso1 = (String) reqLabels.get("TRANSACTION_ISOLATION");
        String iso2 = (String) currentLabels.get("TRANSACTION_ISOLATION");
        boolean match =
          (iso1 != null && iso2 != null && iso1.equalsIgnoreCase(iso2));
        Set rKeys = reqLabels.keySet();
        Set cKeys = currentLabels.keySet();
        if (match && rKeys.containsAll(cKeys))
        {
          System.out.println("## Partial match found!! ##");
          return 10;
        }

        // No label matches to application's preference.
        // Do not choose this connection.
        System.out.println("## No match found!! ##");
        return Integer.MAX_VALUE;
      }

      public boolean configure(Properties reqLabels, Object conn)
      {
        try
        {
          String isoStr = (String) reqLabels.get("TRANSACTION_ISOLATION");
          ((Connection)conn).setTransactionIsolation(Integer.valueOf(isoStr));
          LabelableConnection lconn = (LabelableConnection) conn;

          // Find the unmatched labels on this connection
          Properties unmatchedLabels =
           lconn.getUnmatchedConnectionLabels(reqLabels);

          // Apply each label <key,value> in unmatchedLabels to conn
          for (Map.Entry<Object, Object> label : unmatchedLabels.entrySet())
          {
            String key = (String) label.getKey();
            String value = (String) label.getValue();
            lconn.applyConnectionLabel(key, value);
          }
        }
        catch (Exception exc)
        {
          return false;
        }
        return true;
      }
    }

### 5.2.3 Registering a Labeling Callback in UCP

A pool-enabled data source provides the `registerConnectionLabelingCallback(ConnectionLabelingCallback callback)` method for registering labeling callbacks. Only one callback may be registered on a connection pool. The following example demonstrates registering a labeling callback that is implemented in the `MyConnectionLabelingCallback` class:

    MyConnectionLabelingCallback callback = new MyConnectionLabelingCallback();
    pds.registerConnectionLabelingCallback( callback );

### 5.2.4 Removing a Labeling Callback in UCP

A pool-enabled data source provides the `removeConnectionLabelingCallback()` method for removing a labeling callback. The following example demonstrates removing a labeling callback.

    pds.removeConnectionLabelingCallback( callback );
