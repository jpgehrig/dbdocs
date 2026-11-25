Oracle Autonomous Health Framework assists with monitoring, diagnosing, and preventing availability and performance issues.

System administrators can use most of the components in Oracle Autonomous Health Framework interactively during installation, patching, and upgrading. Database administrators can use Oracle Autonomous Health Framework to diagnose operational runtime issues and mitigate the impact of these issues.

- Availability Issues
  Availability issues are runtime issues that threaten the availability of software stack.
- Performance Issues
  Performance issues are runtime issues that threaten the performance of the system.

**Parent topic:** [Introduction to Oracle Autonomous Health Framework](autonomous-health-framework.md)

### 1.1.1 Availability Issues

Availability issues are runtime issues that threaten the availability of software stack.

Availability issues can result from either software issues (Oracle Database, Oracle Grid Infrastructure, operating system) or the underlying hardware resources (CPU, Memory, Network, Storage).

The components within Oracle Autonomous Health Framework address the following availability issues:

#### Examples of Server Availability Issues

Server availability issues can cause a server to be evicted from the cluster and shut down all the database instances that are running on the server.

Examples of such issues are:

- Issue: Memory stress caused by a server running out of free physical memory, results in the operating system `Swapper` process to run for extended periods of time moving memory to disk. Swapping prevents time-critical cluster processes from running and eventually causing the node to be evicted.

  Solution: Memory Guard detects the memory stress in advance and causes work to be drained to free up memory.

- Issue: Network congestion on the private interconnect can cause time-critical internode or storage I/O to have excessive latency or dropped packets. This type of failure typically builds up and can be detected early, and corrected or relieved.

  Solution: If a change in the server configuration causes this issue, then Cluster Verification Utility (CVU) detects it if the issue persists for more than an hour. However, Oracle Cluster Health Advisor detects the issue within minutes and presents corrective actions.

- Issue: Network failures on the private interconnect caused by a pulled cable or failed network interface card (NIC) can immediately result in evicted nodes.

  Solution: Although these types of network failures cannot be detected early, the cause can be narrowed down by using Cluster Health Monitor and Oracle Trace File Analyzer to pinpoint the time of the failure and the network interfaces involved.

#### Examples of Database Availability Issues

Database availability issues can cause an Oracle database or one of the instances of the database to become unresponsive and thus unavailable to users.

Examples of such issues are:

- Issue: Runaway queries or hangs can deny critical database resources such as locks, latches, or CPU to other sessions. Denial of critical database resources results in database or an instance of a database being non-responsive to applications.

  Solution: Hang Manager detects and automatically resolves these types of hangs. Also, Oracle Cluster Health Advisor detects, identifies, and notifies the database administrator of such hangs and provides an appropriate corrective action.

- Issue: Denial-of-service (DoS) attacks, vulnerabilities, or simply software bugs can cause a database or a database instance to be unresponsive.

  Solution: Proactive recommendations of known issues and their resolutions provided by Oracle ORAchk can prevent such occurrences. If these issues are not prevented, then automatic collection of logs by Oracle Trace File Analyzer, in addition to data collected by Cluster Health Monitor, can speed up the correction of these issues.

- Issue: Configuration changes can cause database outages that are difficult to troubleshoot. For example, incorrect permissions on the `oracle.bin` file can prevent session processes from being created.

  Solution: Use Cluster Verification Utility and Oracle ORAchk to speed up identification and correction of these types of issues. You can generate a diff report using Oracle ORAchk to see a baseline comparison of two reports and a list of differences. You can also view configuration reports created by Cluster Verification Utility to verify whether your system meets the criteria for an Oracle installation.

**Parent topic:** Oracle Autonomous Health Framework Problem and Solution Space

### 1.1.2 Performance Issues

Performance issues are runtime issues that threaten the performance of the system.

Performance issues can result from either software issues (bugs, configuration problems, data contention, and so on) or client issues (demand, query types, connection management, and so on).

Server and database performance issues are intertwined and difficult to separate. It is easier to categorize them by their origin: database server or client.

#### Examples of Database Server Performance Issues

- Issue: Deviations from best practices in configuration can cause database server performance issues.

  Solution: Oracle ORAchk detects configuration issues when Oracle ORAchk runs periodically and notifies the database administrator of the appropriate corrective settings.

- Issue: Bottlenecked resources or poorly constructed SQL statements can cause database server performance issues.

  Solution: Oracle Database Quality of Service (QoS) Management flags these issues and generates notifications when the issues put Service Level Agreements (SLAs) at risk. Oracle Cluster Health Advisor detects when the issues exceed normal operating conditions and notifies the database administrator with corrective actions.

- Issue: A session can cause other sessions to slow down waiting for the blocking session to release its resource or complete its work.

  Solution: Hang Manager detects these chains of sessions and automatically kills the root holder session to relieve the bottleneck.

- Issue: Unresolved known issues or unpatched bugs can cause database server performance issues.

  Solution: These issues can be detected through the automatic Oracle ORAchk reports and flagged with associated patches or workarounds. Oracle ORAchk is regularly enhanced to include new critical issues, either in existing products or in new product areas.

#### Examples of Performance Issues Caused by Database Client

- Issue: When a server is hosting more database instances than its resources and client load can manage, performance suffers because of waits for CPU, I/O, or memory.

  Solution: Oracle ORAchk and Oracle Database QoS Management detect when these issues are the result of misconfiguration such as oversubscribing of CPUs, memory, or background processes. Oracle ORAchk and Oracle Database QoS Management notify you with corrective actions.

- Issue: Misconfigured parameters such as SGA and PGA allocation, number of sessions or processes, CPU counts, and so on, can cause database performance degradation.

  Solution: Oracle ORAchk and Oracle Cluster Health Advisor detect the settings and consequences respectively and notify you automatically with recommended corrective actions.

- Issue: A surge in client connections can exceed the server or database capacity, causing timeout errors and other performance problems.

  Solution: Oracle Database QoS Management and Oracle Cluster Health Advisor automatically detect the performance degradation. Also, Oracle Database QoS Management and Oracle Cluster Health Advisor notify you with corrective actions to relieve the bottleneck and restore performance.

**Parent topic:** Oracle Autonomous Health Framework Problem and Solution Space
