Review the requirements for performance classes and workload classifiers.

Currently, the only workloads that Oracle Database QoS Management manages are OLTP database workloads. To manage the workload for a database, the incoming work requests must be assigned to a Performance Class. Workload is mapped to a Performance Class using classifiers.

In multi-tier environments, a request from a client is routed to different database sessions by the middle tier or through load balancing, making the tracking of a client across database sessions difficult. Classifiers use session attributes to identify work requests. The attributes used are service name, user name, module, action, and program.

Each classifier must specify one or more service names. If a classifier specifies multiple service names, then when matching the connection data to a Performance Class, the service names are evaluated using an `OR` operation. If any one of the service names specified in the classifier matches the service name in the work request, then the comparison evaluates to `TRUE`.

To set the `MODULE` and `ACTION` attributes, use the `OCIAttrSet()` call. Use the default namespace, `USERENV`, for the application context.

You can also optionally include the **UserName** and **program name** in the classifier. The user name is the name of the database user to which the session connects. The program attribute is the name of the client program used to log in to the server.

If the classifier for a Performance Class specifies multiple attributes, then the session attributes are combined using an `AND` operation. If all of the attribute values specified in the classifier match the session attribute values in the work request, then the comparison evaluates to `TRUE`. If you have more than one classifier that uses similar attribute values, then place the classifier with the most fine-grained conditions first.

For example, consider the following classifiers:

- `create_invoice_taxes_pc` that specifies the `sales_cart` service, the `ORDER` module, and the `CALCULATE TAX` action

- `create_invoice_pc`, which specifies the `sales_cart` service and the `ORDER` module

The `create_invoice_taxes_pc` classifier should be evaluated before the `create_invoice_pc` classifier. If a work request uses the `sales_cart` service, and is performing the `CALCULATE TAX` action in the `ORDER` module, then the work request is assigned to the `create_invoice_taxes_pc`. If the work request does not have the matching values for all the attributes, then the work request is compared to the next classifier, for `create_invoice_pc`. If you evaluate the `create_invoice_pc` classifier first, then any work request that uses the `sales_cart` service and the `ORDER` module will be assigned to the `create_invoice_pc` Performance Class, regardless of what action the work request performs.

You can create up to 47 Performance Classes for a cluster. If you have more than 47 services for your cluster, then use more than one service name within classifiers. Once a match is found for a classifier, Oracle Database QoS Management assigns a tag to the matching work request. The tag is based on the classifier that evaluates to `TRUE`.

**Related Topics**

- [Using Additional Filters for Classifying Work Requests](overview-oracle-database-qos-management.md)
- [Applying Classifiers to Work Requests](overview-oracle-database-qos-management.md)
- [Performance Class Tags](overview-oracle-database-qos-management.md)

**Parent topic:** [Supported Workloads and Strategies](supported-workloads-and-strategies.md)
