Review the metrics collected by CHM.

### Overview of Metrics

CHM groups the operating system data collected into a Nodeview. A Nodeview is a grouping of metric sets where each metric set contains detailed metrics of a unique system resource.

Brief description of metric sets are as follows:

- CPU metric set: Metrics for top 127 CPUs sorted by usage percentage
- Device metric set: Metrics for 127 devices that include ASM/VD/OCR along with those having a high average wait time
- Process metric set: Metrics for 127 processes
  - Top 25 CPU consumers (idle processes not reported)
  - Top 25 Memory consumers (RSS \< 1% of total RAM not reported)
  - Top 25 I/O consumers
  - Top 25 File Descriptors consumers (helps to identify top inode consumers)
  - Process Aggregation: Metrics summarized by foreground and background processes for all Oracle Database and Oracle ASM instances
- Network metric set: Metrics for 16 NICS that include public and private interconnects
- NFS metric set: Metrics for 32 NFS ordered by round trip time
- Protocol metric set: Metrics for protocol groups TCP, UDP, and IP
- Filesystem metric set: Metrics for filesystem utilization
- Critical resources metric set: Metrics for critical system resource utilization
  - CPU Metrics: system-wide CPU utilization statistics
  - Memory Metrics: system-wide memory statistics
  - Device Metrics: system-wide device statistics distinct from individual device metric set
  - NFS Metrics: Total NFS devices collected every 30 seconds
  - Process Metrics: system-wide unique process metrics

### CPU Metric Set

Contains metrics from all CPU cores ordered by usage percentage.

Table 4-1 CPU Metric Set

| Metric Name (units) | Description                                                                                                                   |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------|
| system \[%\]        | Percentage of CPU utilization occurred while executing at the system level (kernel).                                          |
| user \[%\]          | Percentage of CPU utilization occurred while executing at the user level (application).                                       |
| usage \[%\]         | Total utilization (system\[%\] + user\[%\]).                                                                                  |
| nice \[%\]          | Percentage of CPU utilization occurred while executing at the user level with nice priority.                                  |
| ioWait \[%\]        | Percentage of time that the CPU was idle during which the system had an outstanding disk I/O request.                         |
| steal \[%\]         | Percentage of time spent in involuntary wait by the virtual CPU while the hypervisor was servicing another virtual processor. |

### Device Metric Set

Contains metrics from all disk devices/partitions ordered by their service time in milliseconds.

Table 4-2 Device Metric Set

| Metric Name (units) | Description                                                                                                                                    |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| ioR \[KB/s\]        | Amount of data read from the device.                                                                                                           |
| ioW \[KB/s\]        | Amount of data written to the device.                                                                                                          |
| numIOs \[#/s\]      | Average disk I/O operations.                                                                                                                   |
| qLen \[#\]          | Number of I/O queued requests, that is, in a wait state.                                                                                       |
| aWait \[msec\]      | Average wait time per I/O.                                                                                                                     |
| svcTm \[msec\]      | Average service time per I/O request.                                                                                                          |
| util \[%\]          | Percent utilization of the device (same as `'%util` metric from the `iostat -x` command. Represents the percentage of time device was active). |

### Process Metric Set

Contains multiple categories of summarized metric data computed across all system processes.

Table 4-3 Process Metric Set

| Metric Name (units)  | Description                                                                                                                 |
|:---------------------|:----------------------------------------------------------------------------------------------------------------------------|
| pid                  | Process ID.                                                                                                                 |
| pri                  | Process priority (raw value from the operating system).                                                                     |
| psr                  | The processor that process is currently assigned to or running on.                                                          |
| pPid                 | Parent process ID.                                                                                                          |
| nice                 | Nice value of the process.                                                                                                  |
| state                | State of the process. For example, `R->Running`, `S->Interruptible sleep`, and so on.                                       |
| class                | Scheduling class of the process. For example, `RR->RobinRound`, `FF->First in First out`, `B->Batch scheduling`, and so on. |
| fd \[#\]             | Number of file descriptors opened by this process, which is updated every 30 seconds.                                       |
| name                 | Name of the process.                                                                                                        |
| cpu \[%\]            | Process CPU utilization across cores. For example, 50% =\> 50% of single core, 400% =\> 100% usage of 4 cores.              |
| thrds \[#\]          | Number of threads created by this process.                                                                                  |
| vmem \[KB\]          | Process virtual memory usage (KB).                                                                                          |
| shMem \[KB\]         | Process shared memory usage (KB).                                                                                           |
| rss \[KB\]           | Process memory-resident set size (KB).                                                                                      |
| ioR \[KB/s\]         | I/O read in kilobytes per second.                                                                                           |
| ioW \[KB/s\]         | I/O write in kilobytes per second.                                                                                          |
| ioT \[KB/s\]         | I/O total in kilobytes per second.                                                                                          |
| cswch \[#/s\]        | Context switch per second. Collected only for a few critical Oracle Database processes.                                     |
| nvcswch \[#/s\]      | Non-voluntary context switch per second. Collected only for a few critical Oracle Database processes.                       |
| cumulativeCpu \[ms\] | Amount of CPU used so far by the process in microseconds.                                                                   |

### NIC Metric Set

Contains metrics from all network interfaces ordered by their total rate in kilobytes per second.

Table 4-4 NIC Metric Set

| Metric Name (units)  | Description                                                                 |
|:---------------------|:----------------------------------------------------------------------------|
| name                 | Name of the interface.                                                      |
| tag                  | Tag for the interface, for example, public, private, and so on.             |
| mtu \[B\]            | Size of the maximum transmission unit in bytes supported for the interface. |
| rx \[Kbps\]          | Average network receive rate.                                               |
| tx \[Kbps\]          | Average network send rate.                                                  |
| total \[Kbps\]       | Average network transmission rate (rx\[Kb/s\] + tx\[Kb/s\]).                |
| rxPkt \[#/s\]        | Average incoming packet rate.                                               |
| txPkt \[#/s\]        | Average outgoing packet rate.                                               |
| pkt \[#/s\]          | Average rate of packet transmission (rxPkt\[#/s\] + txPkt\[#/s\]).          |
| rxDscrd \[#/s\]      | Average rate of dropped/discarded incoming packets.                         |
| txDscrd \[#/s\]      | Average rate of dropped/discarded outgoing packets.                         |
| rxUnicast \[#/s\]    | Average rate of unicast packets received.                                   |
| rxNonUnicast \[#/s\] | Average rate of multicast packets received.                                 |
| dscrd \[#/s\]        | Average rate of total discarded packets (rxDscrd + txDscrd).                |
| rxErr \[#/s\]        | Average error rate for incoming packets.                                    |
| txErr \[#/s\]        | Average error rate for outgoing packets.                                    |
| Err \[#/s\]          | Average error rate of total transmission (rxErr\[#/s\] + txErr\[#/s\]).     |

### NFS Metric Set

Contains top 32 NFS ordered by round trip time. This metric set is collected once every 30 seconds.

Table 4-5 NFS Metric Set

| Metric Name (units) | Description                                                                                                                                        |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| op \[#/s\]          | Number of read/write operations issued to a filesystem per second.                                                                                 |
| bytes \[#/sec\]     | Number of bytes read/write per second from a filesystem.                                                                                           |
| rtt \[s\]           | This is the duration from the time that the client's kernel sends the RPC request until the time it receives the reply.                            |
| exe \[s\]           | This is the duration from that NFS client does the RPC request to its kernel until the RPC request is completed, this includes the RTT time above. |
| retrains \[%\]      | This is the retransmission's frequency in percentage.                                                                                              |

### Protocol Metric Set

Contains specific metrics for protocol groups TCP, UDP, and IP. Metric values are cumulative since the system starts.

Table 4-6 TCP Metric Set

| Metric Name (units) | Description                                                                                                                                                                                                                                                           |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| failedConnErr \[#\] | Number of times that TCP connections have made a direct transition to the CLOSED state from either the SYN-SENT state or the SYN-RCVD state, plus the number of times that TCP connections have made a direct transition to the LISTEN state from the SYN-RCVD state. |
| estResetErr \[#\]   | Number of times that TCP connections have made a direct transition to the CLOSED state from either the ESTABLISHED state or the CLOSE-WAIT state.                                                                                                                     |
| segRetransErr \[#\] | Total number of TCP segments retransmitted.                                                                                                                                                                                                                           |
| rxSeg \[#\]         | Total number of TCP segments received on TCP layer.                                                                                                                                                                                                                   |
| txSeg \[#\]         | Total number of TCP segments sent from TCP layer.                                                                                                                                                                                                                     |

Table 4-7 UDP Metric Set

| Metric Name (units) | Description                                                                                                                         |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| unkPortErr \[#\]    | Total number of received datagrams for which there was no application at the destination port.                                      |
| rxErr \[#\]         | Number of received datagrams that could not be delivered for reasons other than the lack of an application at the destination port. |
| rxPkt \[#\]         | Total number of packets received.                                                                                                   |
| txPkt \[#\]         | Total number of packets sent.                                                                                                       |

Table 4-8 IP Metric Set

| Metric Name (units) | Description                                                                                                                                                  |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ipHdrErr \[#\]      | Number of input datagrams discarded due to errors in their IPv4 headers.                                                                                     |
| addrErr \[#\]       | Number of input datagrams discarded because the IPv4 address in their IPv4 header's destination field was not a valid address to be received at this entity. |
| unkProtoErr \[#\]   | Number of locally-addressed datagrams received successfully but discarded because of an unknown or unsupported protocol.                                     |
| reasFailErr \[#\]   | Number of failures detected by the IPv4 reassembly algorithm.                                                                                                |
| fragFailErr \[#\]   | Number of IPv4 discarded datagrams due to fragmentation failures.                                                                                            |
| rxPkt \[#\]         | Total number of packets received on IP layer.                                                                                                                |
| txPkt \[#\]         | Total number of packets sent from IP layer.                                                                                                                  |

### Filesystem Metric Set

Contains metrics for filesystem utilization. Collected only for GRID_HOME filesystem.

Table 4-9 Filesystem Metric Set

| Metric Name (units) | Description                            |
|:--------------------|:---------------------------------------|
| mount               | Mount point.                           |
| type                | Filesystem type, for example, etx4.    |
| tag                 | Filsystem tag, for example, GRID_HOME. |
| total \[KB\]        | Total amount of space (KB).            |
| used \[KB\]         | Amount of used space (KB).             |
| avbl \[KB\]         | Amount of available space (KB).        |
| used \[%\]          | Percentage of used space.              |
| ifree \[%\]         | Percentage of free file nodes.         |

### System Metric Set

Contains a summarized metric set of critical system resource utilization.

Table 4-10 CPU Metrics

| Metric Name (units) | Description                                                                                                                                               |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| pCpus \[#\]         | Number of physical processing units in the system.                                                                                                        |
| Cores \[#\]         | Number of cores for all CPUs in the system.                                                                                                               |
| vCpus \[#\]         | Number of logical processing units in the system.                                                                                                         |
| cpuHt               | CPU Hyperthreading enabled (Y) or disabled (N).                                                                                                           |
| osName              | Name of the operating system.                                                                                                                             |
| chipName            | Name of the chip of the processing unit.                                                                                                                  |
| system \[%\]        | Percentage of CPUs utilization that occurred while executing at the system level (kernel).                                                                |
| user \[%\]          | Percentage of CPUs utilization that occurred while executing at the user level (application).                                                             |
| usage \[%\]         | Total CPU utilization (system\[%\] + user\[%\]).                                                                                                          |
| nice \[%\]          | Percentage of CPUs utilization occurred while executing at the user level with NICE priority.                                                             |
| ioWait \[%\]        | Percentage of time that the CPUs were idle during which the system had an outstanding disk I/O request.                                                   |
| Steal \[%\]         | Percentage of time spent in involuntary wait by the virtual CPUs while the hypervisor was servicing another virtual processor.                            |
| cpuQ \[#\]          | Number of processes waiting in the run queue within the current sample interval.                                                                          |
| loadAvg1            | Average system load calculated over time of one minute.                                                                                                   |
| loadAvg5            | Average system load calculated over of time of five minutes.                                                                                              |
| loadAvg15           | Average system load calculated over of time of 15 minutes. High load averages imply that a system is overloaded; many processes are waiting for CPU time. |
| Intr \[#/s\]        | Number of interrupts occurred per second in the system.                                                                                                   |
| ctxSwitch \[#/s\]   | Number of context switches that occurred per second in the system.                                                                                        |

Table 4-11 Memory Metrics

| Metric Name (units)   | Description                                                                                                                     |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| totalMem \[KB\]       | Amount of total usable RAM (KB).                                                                                                |
| freeMem \[KB\]        | Amount of free RAM (KB).                                                                                                        |
| avblMem \[KB\]        | Amount of memory available to start a new process without swapping.                                                             |
| shMem \[KB\]          | Memory used (mostly) by tmpfs.                                                                                                  |
| swapTotal \[KB\]      | Total amount of physical swap memory (KB).                                                                                      |
| swapFree \[KB\]       | Amount of swap memory free (KB).                                                                                                |
| swpIn \[KB/s\]        | Average swap in rate within the current sample interval (KB/sec).                                                               |
| swpOut \[KB/s\]       | Average swap-out rate within the current sample interval (KB/sec).                                                              |
| pgIn \[#/s\]          | Average page in rate within the current sample interval (pages/sec).                                                            |
| pgOut \[#/s\]         | Average page out rate within the current sample interval (pages/sec).                                                           |
| slabReclaim \[KB\]    | The part of the slab that might be reclaimed such as caches.                                                                    |
| buffer \[KB\]         | Memory used by kernel buffers.                                                                                                  |
| Cache \[KB\]          | Memory used by the page cache and slabs.                                                                                        |
| bufferAndCache \[KB\] | Total size of buffer and cache (buffer\[KB\] + Cache\[KB\]).                                                                    |
| hugePageTotal \[#\]   | Total number of huge pages present in the system for the current sample interval.                                               |
| hugePageFree \[KB\]   | Total number of free huge pages in the system for the current sample interval.                                                  |
| hugePageSize \[KB\]   | Size of one huge page in KB, depends on the operating system version. Typically the same for all samples for a particular host. |

Table 4-12 Device Metrics

| Metric Name (units) | Description                                      |
|:--------------------|:-------------------------------------------------|
| disks \[#\]         | Number of disks configured in the system.        |
| ioR \[KB/s\]        | Aggregate read rate across all devices.          |
| ioW \[KB/s\]        | Aggregate write rate across all devices.         |
| numIOs \[#/s\]      | Aggregate I/O operation rate across all devices. |

Table 4-13 NFS Metrics

| Metric Name (units) | Description        |
|:--------------------|:-------------------|
| nfs \[#\]           | Total NFS devices. |

Table 4-14 Process Metrics

| Metric Name (units) | Description                                                                                                            |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------|
| fds \[#\]           | Number of open file structs in system.                                                                                 |
| procs \[#\]         | Number of processes.                                                                                                   |
| rtProcs \[#\]       | Number of real-time processes.                                                                                         |
| procsInDState       | Number of processes in uninterruptible sleep.                                                                          |
| sysFdLimit \[#\]    | System limit on a number of file structs.                                                                              |
| procsOnCpu \[#\]    | Number of processes currently running on CPU.                                                                          |
| procsBlocked \[#\]  | Number of processes waiting for some event/resource becomes available, such as for the completion of an I/O operation. |

### Process Aggregates Metric Set

Contains aggregated metrics for all processes by process groups.

Table 4-15 Process Aggregates Metric Set

| Metric Name (units) | Description                                    |
|:--------------------|:-----------------------------------------------|
| DBBG                | User Oracle Database background process group. |
| DBFG                | User Oracle Database foreground process group. |
| MDBBG               | MGMTDB background processes group.             |
| MDBFG               | MGMTDB foreground processes group.             |
| ASMBG               | ASM background processes group.                |
| ASMFG               | ASM foreground processes group.                |
| IOXBG               | IOS background processes group.                |
| IOXFG               | IOS foreground processes group.                |
| APXBG               | APX background processes group.                |
| APXFG               | APX foreground processes group.                |
| CLUST               | Clusterware processes group.                   |
| OTHER               | Default group.                                 |

For each group, the below metrics are aggregated to report a group summary.

| Metric Name (units) | Description                                                          |
|:--------------------|:---------------------------------------------------------------------|
| processes \[#\]     | Total number of processes in the group.                              |
| cpu \[%\]           | Aggregated CPU utilization.                                          |
| rss \[KB\]          | Aggregated resident set size.                                        |
| shMem \[KB\]        | Aggregated shared memory usage.                                      |
| thrds \[#\]         | Aggregated thread count.                                             |
| fds \[#\]           | Aggregated open file-descriptor.                                     |
| cpuWeight \[%\]     | Contribution of the group in overall CPU utilization of the machine. |

**Parent topic:** [Collecting Operating System Resources Metrics](purpose-cluster-health-monitor.md)
