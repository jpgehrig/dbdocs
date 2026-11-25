A Heterogeneous Services agent is the process through which Oracle Database connects to a non-Oracle system.

The agent process that accesses a non-Oracle system is called a gateway. Access to all gateways goes through the Heterogeneous Services component in Oracle Database and all gateways contain the same agent-generic code. Each gateway has a different driver linked in that maps the Heterogeneous Services to the client application programming interface (API) of the non-Oracle system.

The agent process consists of two components. These are agent generic code and a non-Oracle system-specific driver. An agent exists primarily to isolate Oracle Database from third-party code. For a process to access the non-Oracle system, the non-Oracle system client libraries must be linked into it. In the absence of the agent process, these libraries would have to be directly linked into the Oracle Database software and problems in this code could cause Oracle Database to fail. An agent process isolates Oracle Database from any problems in third-party code. Even if a fatal error occurs in the third-party code, only the agent process will end.

An agent can exist in the following places:

- On the same computer as the non-Oracle system

- On the same computer as Oracle Database

- On a computer different from either of these two

Agent processes are started when a user session accesses a non-Oracle system through a database link. These connections are made using Oracle's remote data access software, Oracle Net Services, which enables both client/server and server/server communication. The agent process continues to run until the user session is disconnected or the database link is explicitly closed.

Multithreaded agents act differently. They must be explicitly started and shut down by a database administrator, instead of automatically being spawned by Oracle Net Services

**Parent topic:** [The Role of the Heterogeneous Services Component](heterogeneous-services-role.md)
