## Database Services for an Oracle RAC Database

Each database is represented by one or more services. A service is identified by a service name, such as `sales.example.com`. A client uses a service name to identify the database it must access.

During installation, Oracle RAC databases are configured with a default database service that has the same name as the database. This service can be used for performing database management tasks. Create additional services for client and application connections to the database.

A service name can be associated with multiple database instances, and an instance can be associated with multiple services. The listener acts as a mediator between the client and database instances and routes the connection request to the appropriate instance. Clients connecting to a service do not have to specify which instance they want to connect to.

**Parent topic:** [Oracle Net Services Configuration for Oracle RAC Databases](oracle-net-services-configuration-for-oracle-rac-databases.md)
