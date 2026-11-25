# Description of the illustration netag142.eps

This illustration shows and end-to-end architecture that includes Web browser clients, a middle-tier with application Web servers and Oracle Connection Manager, and a database server configured with shared server.

Six Web browsers connect to two sets of application Web servers. Each set is comprised of three application Web servers and one Oracle Connection Manager. The Oracle Connection Manager connects to the dispatchers on the database server. The dispatchers sent requests to a virtual circuit which forwards the requests to the shard server processes.
