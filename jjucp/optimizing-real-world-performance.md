Most on-line transaction processing (OLTP) performance problems that the Real-World Performance group investigates relate to the connection strategy used by the application. For this reason, designing a sound connection strategy is crucial for system performance, especially in enterprise environments that must scale to meet increasing demand.

###

Most applications use a dynamic pool of connections to the database, configured with a minimum number of connections to keep open on the database and a maximum number of connections that can be made to the database. When an application needs a connection to the database, then it requests one from the pool. If there are no connections available, then the application creates a new connection, if it has not reached the maximum number of connections already. If a connection has not been used for a specified duration of time, then the application closes the connection, if there are more than the minimum number of connections available.

This configuration conserves system resources by only maintaining the number of connections actively needed by the application. In the real world, this configuration enables connection storms and database system CPU oversubscription, quickly destabilizing a system. A connection storm can occur when there are lots of activities on the application server requiring database connections. If there are not enough connections to the database to serve all of the requests, then the application server opens new connections. Creating a new connection to the database is a resource intensive activity, and when lots of connections are made in a short period of time, it can overwhelm the CPU resources on the database system.

So, for creating a static connection pool, the number of connections to the database system must be based on the CPU cores available on the system. Oracle recommends 1-10 connections per CPU core. The ideal number varies depending on the application and the system hardware. However, the value is somewhere within that range. the Real-World Performance group recommends creating a static pool of connections to the database by setting the minimum and maximum number of connections to the same value. This prevents connection storms by keeping the number of database connections constant to a predefined value.

For example, if a database server has 2 CPUs, 12 cores per CPU, and 2 threads per core, then there are 24 cores available and the number of connections to the database should be between 12 and 120. The number of threads is not taken into consideration as only the CPU cores are able to execute instructions. This number is cumulative for all applications connecting to the system and for all databases, if there is more than one database on the system. If there are two application servers, then the maximum number of connections (for example, 120 in this case) should be divided between them. If there are two databases running on the system, then the maximum number of connections that is, 120 connections needs to be divided between them.

**See Also:**

- <https://www.youtube.com/watch?v=Oo-tBpVewP4>

- <https://www.youtube.com/watch?v=XzN8Rp6glEo>
