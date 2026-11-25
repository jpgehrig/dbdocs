An agent process is started for each session to access a system at the same time leading to several thousand agent processes concurrently.

The agent processes operation regardless of whether each individual agent process is currently active. Agent processes and open connections can consume a disproportionate amount of system resources. This problem is addressed by using multithreaded agent architecture.

The multithreaded agent architecture uses a pool of shared agent threads. The tasks requested by the user sessions are put in a queue and are picked up by the first available multithreaded agent thread. Because only a small percentage of user connections are active at a given moment, using a multithreaded architecture allows for more efficient use of system resources.

**See Also:**

- [Oracle Database Development Guide](../adfns/external-procedures.md)

- [Oracle Database Heterogeneous Connectivity User's Guide](../heter/heterogeneous-services-agents.md)

**Parent topic:** [Developing Applications for Windows](developing-applications-for-windows.md)
