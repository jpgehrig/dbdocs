This screen shot shows the Database Home page in EM Express.

The Status section at the top left displays how long the database has been up, the database type, version, database name, instance name, platform name, host name, Oracle Home name, thread, and status of the archiver. If the database type is a CDB, the line after the database type shows the number of PDBs in the CDB.

Below the Status section is the Incidents - Last 24 Hours section. The table in this section displays information about database incidents that have occurred in the past 24 hours. It has the Instance, Time, Incident, Problem, and Error columns.

Below the Incidents - Last 24 Hours section is the Running Jobs section. It shows information about database jobs that are currently running. The table in this section has the Instance, Owner, Name, Elapsed, and Started columns.

The Performance section at the top right shows the Activity Class tab, which has a chart that shows the values for Wait, User I/O, and CPU activity. The red line on the chart shows the number of CPU Cores. The Performance section also includes the Services tab, and if the database is a CDB, a Containers tab.

Below the Performance section is the Resources section. Three charts appear in the Resources section in the screen shot:

- Host CPU: Shows the percentage of CPU used on the host by the database instance and by other processes

- Active Sessions: Shows the average number of active sessions broken out by Wait and CPU

- Memory: Shows the average amount of memory used by Other SGA, Shared I/O Pool, Java Pool, Large Pool, Shared Pool, Buffer Cache, and PGA

Below the Resources section is the SQL Monitor - Last Hour (20 max) section. This chart shows the last 20 SQL statements that were monitored during the past hour and also any SQL statements that are currently running. The table includes the Status, Duration, Type, ID, User, Parallel, Database Time, and SQL Text columns.
