## Naming Methods and Connect Descriptors

Each net service name is associated with a connect descriptor. A connect descriptor provides the location of the database and the name of the database service.

A connect descriptor is comprised of one or more protocol addresses of the listener and the connect information for the destination service.The information needed to use a service name to create a database connection can be stored in a repository, which is represented by one or more naming methods. A naming method is a resolution method used by a client application to resolve a service name to a connect descriptor. Oracle Net Services offers several types of naming methods that support localized configuration on each client, or centralized configuration that can be accessed by all clients in the network.

**Parent topic:** [Oracle Net Services Configuration for Oracle RAC Databases](oracle-net-services-configuration-for-oracle-rac-databases.md)
