Hang Manager is an Oracle Real Application Clusters (Oracle RAC) environment feature that autonomously resolves hangs and keeps the resources available.

Enabled by default, Hang Manager:

- Reliably detects database hangs and deadlocks

- Autonomously resolves database hangs and deadlocks

- Supports Oracle Database QoS Performance Classes, Ranks, and Policies to maintain SLAs

- Logs all detections and resolutions

- Provides SQL interface to configure sensitivity (Normal/High) and trace file sizes

A database hangs when a session blocks a chain of one or more sessions. The blocking session holds a resource such as a lock or latch that prevents the blocked sessions from progressing. The chain of sessions has a root or a final blocker session, which blocks all the other sessions in the chain. Hang Manager resolves these issues autonomously by detecting and resolving the hangs.

**Related Topics**

- [Resolving Database and Database Instance Hangs](purpose-hang-manager.md)

**Parent topic:** [Components of Autonomous Health Framework](components-ahf.md)
