Memory Guard is an Oracle Real Application Clusters (Oracle RAC) environment feature to monitor the cluster nodes to prevent node stress caused by the lack of memory.

Enabled by default, Memory Guard:

- Analyzes over-committed memory conditions once in every minute

- Issues alert if any server is at risk

- Protects applications by automatically closing the server to new connections

- Stops all CRS-managed services transactionally on the server

- Re-opens server to connections once the memory pressure has subsided

Enterprise database servers can use all available memory due to too many open sessions or runaway workloads. Running out of memory can result in failed transactions or, in extreme cases, a restart of the node and the loss of availability of resources for your applications.

Memory Guard autonomously collects metrics on memory of every node from Cluster Health Monitor to determine if the nodes have insufficient memory. If the memory is insufficient, then Memory Guard prevents new database sessions from being created allowing the existing workload to complete and free their memory. New sessions are started automatically when the memory stress is relieved.

**Related Topics**

- [Resolving Memory Stress](purpose-memory-guard.md)

**Parent topic:** [Components of Autonomous Health Framework](components-ahf.md)
