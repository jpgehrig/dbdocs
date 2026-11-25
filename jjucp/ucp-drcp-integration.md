Natively, DRCP supports connection tagging, which is a single label without weights. So, labeling with a single label works transparently if you use UCP with DRCP.

**Note:**

Oracle recommends that the maximum pool size of UCP should not be bigger than the size of DRCP. If the UCP pool size is bigger than the DRCP size, then you must set the `setValidateConnectionOnBorrow` property to `off`. Otherwise, UCP keeps invalidating and closing the connections that are not associated with DRCP at that moment, and keeps creating fresh connections.

**See Also:**

[Overview of Validating Connections in UCP](validating-ucp-connections.md)

Multiple label UCP connections work, but they have the following behavior changes:

- The `cost` method in the `ConnectionLabelingCallback` API is not invoked if you use UCP with DRCP using connection labeling

- UCP can invoke the `configure` method in the `ConnectionLabelingCallback` API more with DRCP configuration than without DRCP configuration.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/database-resident-connection-pooling.md) for more information about DRCP
