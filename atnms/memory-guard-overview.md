Memory Guard automatically monitors cluster nodes to prevent node stress caused by the lack of memory.

Memory Guard autonomously collects metrics on memory usage for every node in an Oracle Real Application Clusters (Oracle RAC) environment. Memory Guard gets the information from Cluster Health Monitor. If Memory Guard determines that a node has insufficient memory, then Memory Guard performs the following actions:

- Prevents new database sessions from being created on the afflicted node

- Stops all CRS-managed services transactionally on the node, allowing the existing workload on the node to complete and free their memory

When Memory Guard determines that the memory stress has been relieved, it restores connectivity to the node, allowing new sessions to be created on that node.

Running out of memory can result in failed transactions or, in extreme cases, a restart of the node resulting in the loss of availability and resources for your applications.

**Parent topic:** [Resolving Memory Stress](purpose-memory-guard.md)
