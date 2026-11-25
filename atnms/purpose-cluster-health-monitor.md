CHM is a high-performance, lightweight daemon that collects, analyzes, aggregates, and stores a large set of operating system metrics to help you diagnose and troubleshoot system issues.

You can now configure Oracle Cluster Health Monitor to operate in local mode to report the operating system metrics using the `oclumon dumpnodeview local` command even if you have not deployed GIMR.

In local mode, you can get only the local node data. In earlier releases, Oracle Cluster Health Monitor required GIMR to report the operating system metrics using the `oclumon dumpnodeview` command.

### Supported Platforms

Linux, Microsoft Windows, Solaris, AIX, IBM Z Series, and ARM

### Why CHM is unique

| CHM                                                                                                                                                                                                                | Typical OS Collector                                                                                                                                                                                   |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Last man standing - daemon runs memory locked, RT scheduling class ensuring consistent data collection under system load.                                                                                          | Inconsistent data dropouts due to scheduling delays under system load.                                                                                                                                 |
| High fidelity data sampling rate, 5 seconds. Very low resource usage profile at 5-second sampling rates.                                                                                                           | Executing multiple utilities creates additional overhead on the system being monitored, and worsens with higher sampling rates.                                                                        |
| High Availability daemon, collated data collections across multiple resource categories. Highly optimized collector (data read directly from the operating system, same source as utilities).                      | Set of scripts/command-line utilities, for example, `top`, `ps`, `vmstat`, `iostat`, and so on re-directing their output to one or more files for every collection sample.                             |
| Collected data is collated into a system snapshot overview (**Nodeview**) on every sample, Nodeview also contains additional summarization and analysis of the collected data across multiple resource categories. | System snapshot overviews across different resource categories are very tedious to collate.                                                                                                            |
| Significant inline analysis and summarization during data collection and collation into the Nodeview greatly reduces tedious, manual, time-consuming analysis to drive meaningful insights.                        | The analysis is time-consuming and processing-intensive as the output of various utilities across multiple files needs to be collated, parsed, interpreted, and then analyzed for meaningful insights. |
| Performs Clusterware-aware specific metrics collection (Process Aggregates, ASM/OCR/VD disk tagging, Private/Public NIC tagging). Also provides an extensive toolset for in-depth data analysis and visualization. | None                                                                                                                                                                                                   |

- [Understanding Cluster Health Monitor Services](understanding-cluster-health-monitor-services.md)
  Cluster Health Monitor uses system monitor (`osysmond`) and cluster logger (`ologgerd`) services to collect diagnostic data.
- [Collecting Cluster Health Monitor Data](collecting-cluster-health-monitor-data.md)
  Collect Cluster Health Monitor data from any node in the cluster.
- [Operating System Metrics Collected by Cluster Health Monitor](os-metrics-collected-by-chm.md)
  Review the metrics collected by CHM.
- [Using Cluster Health Monitor from Enterprise Manager Cloud Control](chm-emcc-integration.md)
  Histograms presented in real-time and historical modes enable you to understand precisely what was happening at the time of degradation or failure.

**Related Topics**

- [Introduction to Cluster Health Monitor](introduction-cluster-health-monitor.md)

**Parent topic:** [Automatically Monitoring the Cluster](automatically-monitoring-cluster.md)
