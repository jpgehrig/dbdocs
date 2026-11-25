Use the `oclumon dumpnodeview` command to view log information from the system monitor service in the form of a node view.

### Usage Notes

A node view is a collection of all metrics collected by Cluster Health Monitor for a node at a point in time. Cluster Health Monitor attempts to collect metrics every five seconds on every node. Some metrics are static while other metrics are dynamic.

A node view consists of eight views when you display verbose output:

- SYSTEM: Lists system metrics such as CPU COUNT, CPU USAGE, and MEM USAGE

- TOP CONSUMERS: Lists the top consuming processes in the following format:

      metric_name: 'process_name(process_identifier) utilization'

- CPUS: Lists statistics for each CPU

- PROCESSES: Lists process metrics such as PID, name, number of threads, memory usage, and number of file descriptors

- DEVICES: Lists device metrics such as disk read and write rates, queue length, and wait time per I/O

- NICS: Lists network interface card metrics such as network receive and send rates, effective bandwidth, and error rates

- FILESYSTEMS: Lists file system metrics, such as total, used, and available space

- PROTOCOL ERRORS: Lists any protocol errors

Generate a summary report that only contains the SYSTEM and TOP CONSUMERS views.

### Syntax

    oclumon dumpnodeview [-allnodes | -n node1 ...] [-last duration | -s timestamp -e timestamp] [-i interval] [-v | [-system][-process][-procag][-device][-filesystem][-nic][-protoerr][-cpu][-topconsumer]] [-format format type] [-dir directory [-append]]

### Parameters

Table B-2 oclumon dumpnodeview Command Parameters

| Parameter                                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-allnodes`                                                                    | Use this option to dump the node views of all the nodes in the cluster.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-n node1 node2`                                                               | Specify one node or several nodes in a space-delimited list for which you want to dump the node view.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-last "duration"`                                                             | Use this option to specify a time, given in `HH24:MM:SS` format surrounded by double quotation marks (`""`), to retrieve the last metrics.<br>For example:<br>`"23:05:00"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-s "time_stamp" -e "time_stamp"`                                              | Use the `-s` option to specify a time stamp from which to start a range of queries and use the `-e` option to specify a time stamp to end the range of queries.<br>Specify time in `YYYY-MM-DD HH24:MM:SS` format surrounded by double quotation marks (`""`).<br>For example:<br>`"2011-05-10 23:05:00"`<br>Note: Specify these two options together to obtain a range.                                                                                                                                                                                                                                                                                 |
| `-i interval`                                                                  | Specify a collection interval, in five-second increments.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-v`                                                                           | Displays verbose node view output.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-system, -process, -device, -filesystem, -nic, -protoerr, -cpu, -topconsumer` | Dumps each specified node view parts.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-format "format type"`                                                        | Specify the output format.<br>"format type" can be `legacy`, `tabular`, or `csv`.<br>The default format is mostly tabular with legacy for node view parts with only one row.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-dir directory`                                                               | Dumps the node view to the files in the directory that you specify.<br>Specify the `-append` option to append the files of the current to the existing files. If you do not specify `–append`, then the command overwrites the existing files, if present.<br>For example, the command `oclumon dumpnodeview -dir ``dir_name` dumps the data in the specified directory.<br>If this command is run twice, it overwrites the data dumped by the previous run.<br>Running the command with `-append`, for example, `oclumon dumpnodeview -dir ``dir_name`` -append`, appends the data of the current run with the previous one in the specified directory. |
| `-procag`                                                                      | Outputs the process of the node view, aggregated by category:<br>• DBBG (DB backgrounds)<br>• DBFG (DB foregrounds)<br>• CLUST (Cluster)<br>• OTHER (other processes)<br>Note: `-procag` is currently available only on Linux, Solaris, and AIX. It is not supported on Microsoft Windows systems.                                                                                                                                                                                                                                                                                                                                                       |
| `-h`                                                                           | Displays online help for the `oclumon dumpnodeview` command.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

### Usage Notes

- In certain circumstances, data can be delayed for some time before the command replays the data.

  For example, the `crsctl stop cluster -all` command can cause data delay. After running `crsctl start cluster -all`, it may take several minutes before `oclumon dumpnodeview` shows any data collected during the interval.

- The default is to continuously dump node views. To stop continuous display, use Ctrl+C on Linux and Microsoft Windows.

- Both the local system monitor service (`osysmond`) and the cluster logger service (`ologgerd`) must be running to obtain node view dumps.

- The `oclumon dumpnodeview` command displays only 127 CPUs of the CPU core, omitting a CPU at random from the list.

### Metric Descriptions

This section includes descriptions of the metrics in each of the seven views that comprise a node view listed in the following tables.

Table B-3 oclumon dumpnodeview SYSTEM View Metric Descriptions

| Metric                                                                                     | Description                                                                                                                                                                                                                                                           |
|:-------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `#pcpus`                                                                                   | Number of physical CPUs.                                                                                                                                                                                                                                              |
| `#cores`                                                                                   | Number of CPU cores in the system.                                                                                                                                                                                                                                    |
| `#vcpus`                                                                                   | Number of logical compute units.                                                                                                                                                                                                                                      |
| `cpuht`                                                                                    | CPU hyperthreading enabled (Y) or disabled (N).                                                                                                                                                                                                                       |
| `chipname`                                                                                 | Name of the CPU vendor.                                                                                                                                                                                                                                               |
| `cpu`                                                                                      | Average CPU utilization per processing unit within the current sample interval (%).                                                                                                                                                                                   |
| Percentage of over all CPU cores. 100% indicates that all cores are spent for that metric. |                                                                                                                                                                                                                                                                       |
| `cpuusage`                                                                                 | Total CPU usage = `cpusystem` + `cpuuser` + `cpunice`                                                                                                                                                                                                                 |
| `cpusystem`                                                                                | CPU used by processes in kernel mode.                                                                                                                                                                                                                                 |
| `cpuuser`                                                                                  | CPU used by normal processes in user mode.                                                                                                                                                                                                                            |
| `cpunice`                                                                                  | CPU used by "niced" processes (low priority).                                                                                                                                                                                                                         |
| `cpuiowait`                                                                                | CPU waiting for I/O.                                                                                                                                                                                                                                                  |
| `cpusteal`                                                                                 | Virtual CPU waiting for physical CPU to be freed by other VM.                                                                                                                                                                                                         |
| `cpuq`                                                                                     | Number of processes waiting in the run queue within the current sample interval.                                                                                                                                                                                      |
| `physmemfree`                                                                              | Amount of free RAM (KB).                                                                                                                                                                                                                                              |
| `physmemtotal`                                                                             | Amount of total usable RAM (KB).                                                                                                                                                                                                                                      |
| `shmem`                                                                                    | Shared memory.                                                                                                                                                                                                                                                        |
| `mcache`                                                                                   | Amount of physical RAM used for file buffers plus the amount of physical RAM used as cache memory (KB).<br>On Microsoft Windows systems, this is the number of bytes currently being used by the file system cache.<br>Note: This metric is not available on Solaris. |
| `swapfree`                                                                                 | Amount of swap memory free (KB)                                                                                                                                                                                                                                       |
| `swaptotal`                                                                                | Total amount of physical swap memory (KB)                                                                                                                                                                                                                             |
| `hugepagetotal`                                                                            | Total size of huge in KB<br>Note: This metric is not available on Solaris or Microsoft Windows systems.                                                                                                                                                               |
| `hugepagefree`                                                                             | Free size of huge page in KB<br>Note: This metric is not available on Solaris or Microsoft Windows systems.                                                                                                                                                           |
| `hugepagesize`                                                                             | Smallest unit size of huge page<br>Note: This metric is not available on Solaris or Microsoft Windows systems.                                                                                                                                                        |
| `ior`                                                                                      | Average total disk read rate within the current sample interval (KB per second).                                                                                                                                                                                      |
| `iow`                                                                                      | Average total disk write rate within the current sample interval (KB per second).                                                                                                                                                                                     |
| `ios`                                                                                      | Average disk I/O operation rate within the current sample interval (I/O operations per second).                                                                                                                                                                       |
| `swpin`                                                                                    | Average swap in rate within the current sample interval (KB per second).<br>Note: This metric is not available on Microsoft Windows systems.                                                                                                                          |
| `swpout`                                                                                   | Average swap out rate within the current sample interval (KB per second).<br>Note: This metric is not available on Microsoft Windows systems.                                                                                                                         |
| `pgin`                                                                                     | Average page in rate within the current sample interval (pages per second).                                                                                                                                                                                           |
| `pgout`                                                                                    | Average page out rate within the current sample interval (pages per second).                                                                                                                                                                                          |
| `netr`                                                                                     | Average total network receive rate within the current sample interval (KB per second).                                                                                                                                                                                |
| `netw`                                                                                     | Average total network send rate within the current sample interval (KB per second).                                                                                                                                                                                   |
| `procs`                                                                                    | Number of processes.                                                                                                                                                                                                                                                  |
| `procsoncpu`                                                                               | The current number of processes running on the CPU.                                                                                                                                                                                                                   |
| `#procs_blocked`                                                                           | Number of processes currently blocked waiting for I/O.                                                                                                                                                                                                                |
| `rtprocs`                                                                                  | Number of real-time processes.                                                                                                                                                                                                                                        |
| `rtprocsoncpu`                                                                             | The current number of real-time processes running on the CPU.                                                                                                                                                                                                         |
| `#fds`                                                                                     | Number of open file descriptors.<br>or<br>Number of open handles on Microsoft Windows.                                                                                                                                                                                |
| `#sysfdlimit`                                                                              | System limit on the number of file descriptors.<br>Note: This metric is not available on either Solaris or Microsoft Windows systems.                                                                                                                                 |
| `#disks`                                                                                   | Number of disks.                                                                                                                                                                                                                                                      |
| `#nics`                                                                                    | Number of network interface cards.                                                                                                                                                                                                                                    |
| `nicErrors`                                                                                | Average total network error rate within the current sample interval (errors per second).                                                                                                                                                                              |
| `#nfs`                                                                                     | Number of network file system.                                                                                                                                                                                                                                        |
| `loadavg1`<br>`loadavg5`<br>`loadavg15`                                                    | Load average (average number of jobs in the run queue or waiting for disk I/O) of the last 1, 5, 15 minutes.                                                                                                                                                          |

Table B-4 oclumon dumpnodeview PROCESSES View Metric Descriptions

| Metric                      | Description                                                                                                                                                              |
|:----------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`                      | The name of the process executable.                                                                                                                                      |
| `pid`                       | The process identifier assigned by the operating system.                                                                                                                 |
| `ppid`                      | PID of the parent process.<br>For example, if process 1 spawns process 2, then ppid of process 2 is pid of process 1.                                                    |
| `cumulative_cpu`            | The total amount of CPU time this process is scheduled to run since it started. The total amount of CPU time spent for this process so far is measured in micro seconds. |
| `#procfdlimit`              | Limit on number of file descriptors for this process.<br>Note: This metric is not available on Microsoft Windows, AIX, and HP-UX systems.                                |
| `cpuusage`                  | Process CPU utilization (%).<br>Note: The utilization value can be up to 100 times the number of processing units.                                                       |
| `vmem`                      | Process virtual memory usage (KB).                                                                                                                                       |
| `privmem`                   | Process private memory usage (KB).                                                                                                                                       |
| `shmem, shm, and sharedmem` | Process shared memory usage (KB).<br>Note: This metric is not available on Microsoft Windows, Solaris, and AIX systems. It is supported only on Linux systems.           |
| `workingset`                | Working set of a program (KB)<br>Note: This metric is only available on Microsoft Windows.                                                                               |
| `#fd`                       | Number of file descriptors open by this process.<br>or<br>Number of open handles by this process on Microsoft Windows.                                                   |
| `#threads`                  | Number of threads created by this process.                                                                                                                               |
| `priority`                  | The process priority.                                                                                                                                                    |
| `nice`                      | The nice value of the process.<br>Note: This metric is not applicable to Microsoft Windows systems.                                                                      |
| `state`                     | The state of the process.<br>Note: This metric is not applicable to Microsoft Windows systems.                                                                           |

Table B-5 oclumon dumpnodeview DEVICES View Metric Descriptions

| Metric | Description                                                                                                                            |
|:-------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `ior`  | Average disk read rate within the current sample interval (KB per second).                                                             |
| `iow`  | Average disk write rate within the current sample interval (KB per second).                                                            |
| `ios`  | Average disk I/O operation rate within the current sample interval (I/O operations per second)                                         |
| `qlen` | Number of I/O requests in `WAIT` state within the current sample interval.                                                             |
| `wait` | Average wait time per I/O within the current sample interval (msec).                                                                   |
| `type` | If applicable, identifies what the device is used for. Possible values are:<br>• `SWAP`<br>• `SYS`<br>• `OCR`<br>• `ASM`<br>• `VOTING` |

Table B-6 oclumon dumpnodeview NICS View Metric Descriptions

| Metric         | Description                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------|
| `netrr`        | Average network receive rate within the current sample interval (KB per second).                 |
| `netwr`        | Average network sent rate within the current sample interval (KB per second).                    |
| `neteff`       | Average effective bandwidth within the current sample interval (KB per second)                   |
| `nicerrors`    | Average error rate within the current sample interval (errors per second).                       |
| `pktsin`       | Average incoming packet rate within the current sample interval (packets per second).            |
| `pktsout`      | Average outgoing packet rate within the current sample interval (packets per second).            |
| `errsin`       | Average error rate for incoming packets within the current sample interval (errors per second).  |
| `errsout`      | Average error rate for outgoing packets within the current sample interval (errors per second).  |
| `indiscarded`  | Average drop rate for incoming packets within the current sample interval (packets per second).  |
| `outdiscarded` | Average drop rate for outgoing packets within the current sample interval (packets per second).  |
| `inunicast`    | Average packet receive rate for unicast within the current sample interval (packets per second). |
| `type`         | Whether PUBLIC or PRIVATE.                                                                       |
| `innonunicast` | Average packet receive rate for multi-cast (packets per second).                                 |
| `latency`      | Estimated latency for this network interface card (msec).                                        |

Table B-7 oclumon dumpnodeview FILESYSTEMS View Metric Descriptions

| Metric      | Description                                                                                            |
|:------------|:-------------------------------------------------------------------------------------------------------|
| `total`     | Total amount of space (KB).                                                                            |
| `mount`     | Mount point.                                                                                           |
| `type`      | File system type, whether local file system, NFS, or other.                                            |
| `used`      | Amount of used space (KB).                                                                             |
| `available` | Amount of available space (KB).                                                                        |
| `used%`     | Percentage of used space (%)                                                                           |
| `ifree%`    | Percentage of free file nodes (%).<br>Note: This metric is not available on Microsoft Windows systems. |

Table B-8 oclumon dumpnodeview PROTOCOL ERRORS View Metric Descriptions

| Metric          | Description                                                                                                                                                                                                                                                                     |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IPHdrErr`      | Number of input datagrams discarded due to errors in the IPv4 headers of the datagrams.                                                                                                                                                                                         |
| `IPAddrErr`     | Number of input datagrams discarded because the IPv4 address in their IPv4 header's destination field was not a valid address to be received at this entity.                                                                                                                    |
| `IPUnkProto`    | Number of locally addressed datagrams received successfully but discarded because of an unknown or unsupported protocol.                                                                                                                                                        |
| `IPReasFail`    | Number of failures detected by the IPv4 reassembly algorithm.                                                                                                                                                                                                                   |
| `IPFragFail`    | Number of IPv4 discarded datagrams due to fragmentation failures.                                                                                                                                                                                                               |
| `TCPFailedConn` | Number of times that TCP connections have made a direct transition to the `CLOSED` state from either the `SYN-SENT` state or the `SYN-RCVD` state, plus the number of times that TCP connections have made a direct transition to the `LISTEN` state from the `SYN-RCVD` state. |
| `TCPEstRst`     | Number of times that TCP connections have made a direct transition to the `CLOSED` state from either the `ESTABLISHED` state or the `CLOSE-WAIT` state.                                                                                                                         |
| `TCPRetraSeg`   | Total number of TCP segments retransmitted.                                                                                                                                                                                                                                     |
| `UDPUnkPort`    | Total number of received UDP datagrams for which there was no application at the destination port.                                                                                                                                                                              |
| `UDPRcvErr`     | Number of received UDP datagrams that could not be delivered for reasons other than the lack of an application at the destination port.                                                                                                                                         |

Table B-9 oclumon dumpnodeview CPUS View Metric Descriptions

| Metric       | Description                       |
|:-------------|:----------------------------------|
| `cpu``id`    | Virtual CPU.                      |
| `sys-usage`  | CPU usage in system space.        |
| `user-usage` | CPU usage in user space.          |
| `nice`       | Value of NIC for a specific CPU.  |
| `usage`      | CPU usage for a specific CPU.     |
| `iowait`     | CPU wait time for I/O operations. |

Example B-2 dumpnodeview -n

The following example dumps node views from `node1`, `node2`, and `node3` collected over the last 12 hours:

    $ oclumon dumpnodeview -n node1 node2 node3 -last "12:00:00"

The following example displays node views from all nodes collected over the last 15 minutes at a 30-second interval:

    $ oclumon dumpnodeview -allnodes -last "00:15:00" -i 30

Example B-3 dumpnodeview –format csv

The following example shows how to use the option `-format csv` to output content in comma-separated values file format:

    # oclumon dumpnodeview –format csv

    dumpnodeview: Node name not given. Querying for the local host

    ----------------------------------------
    Node: node1 Clock: '2016-09-02 11.18.00-0700' SerialNo:310668
    ----------------------------------------

    SYSTEM:
    "#pcpus","#cores","#vcpus","cpuht","chipname","cpuusage[%]","cpusys[%]","cpuuser[%]",
    "cpunice[%]","cpuiowait[%]","cpusteal[%]","cpuq","physmemfree[KB]","physmemtotal[KB]",
    "mcache[KB]","swapfree[KB]","swaptotal[KB]","hugepagetotal","hugepagefree","hugepagesize",
    "ior[KB/S]","iow[KB/S]","ios[#/S]","swpin[KB/S]","swpout[KB/S]","pgin[#/S]","pgout[#/S]",
    "netr[KB/S]","netw[KB/S]","#procs","#procsoncpu","#procs_blocked","#rtprocs","#rtprocsoncpu",
    "#fds","#sysfdlimit","#disks","#nics","loadavg1","loadavg5","loadavg15","#nicErrors"
    2,12,24,Y,"Intel(R) Xeon(R) CPU X5670 @ 2.93GHz",68.66,5.40,63.26,0.00,0.00,0.00,0,820240,
    73959636,61520568,4191424,4194300,0,0,
    2048,143,525,64,0,0,0,279,600.888,437.070,951,24,0,58,N/A,33120,6815744,13,5,19.25,17.67,16.09,0

    TOPCONSUMERS:
    "topcpu","topprivmem","topshm","topfd","topthread"
    "java(25047) 225.44","java(24667) 1008360","ora_lms1_prod_1(28913) 4985464","polkit-gnome-au(20730) 1038","java(2734) 209"

Example B-4 dumpnodeview –procag

The following example shows how to output node views, aggregated by category: DBBG (DB backgrounds), DBFG (DB foregrounds), CLUST (Cluster), and OTHER (other processes).

    # oclumon dumpnodeview –procag

    ----------------------------------------
    Node: node1 Clock: '2016-09-02 11.14.15-0700' SerialNo:310623
    ----------------------------------------
    PROCESS AGGREGATE:
    cpuusage[%]   privatemem[KB]    maxshmem[KB]   #threads     #fd   #processes   category       sid
           0.62         45791348         4985200        187   10250          183       DBBG    prod_1
           0.52         29544192         3322648        191   10463          187       DBBG    webdb_1
          17.81          8451288          967924         22     511           22       DBFG    webdb_1
          75.94         34930368         1644492         64    1067           64       DBFG    prod_1
           3.42          3139208          120256        480    3556           25       CLUST
           1.66          1989424           16568       1110    4040          471       OTHER

Example B-5 Node View Output

    ----------------------------------------
    Node: rwsak10 Clock: '2016-05-08 02.11.25-0800' SerialNo:155631
    ----------------------------------------

    SYSTEM:
    #pcpus: 2 #vcpus: 24 cpuht: Y chipname: Intel(R) cpu: 1.23 cpuq: 0
    physmemfree: 8889492 physmemtotal: 74369536 mcache: 55081824 swapfree: 18480404
    swaptotal: 18480408 hugepagetotal: 0 hugepagefree: 0 hugepagesize: 2048 ior: 132
    iow: 236 ios: 23 swpin: 0 swpout: 0 pgin: 131 pgout: 235 netr: 72.404
    netw: 97.511 procs: 969 procsoncpu: 6 rtprocs: 62 rtprocsoncpu N/A #fds: 32640
    #sysfdlimit: 6815744 #disks: 9 #nics: 5 nicErrors: 0

    TOP CONSUMERS:
    topcpu: 'osysmond.bin(30981) 2.40' topprivmem: 'oraagent.bin(14599) 682496'
    topshm: 'ora_dbw2_oss_3(7049) 2156136' topfd: 'ocssd.bin(29986) 274'
    topthread: 'java(32255) 53'

    CPUS:

    cpu18: sys-2.93 user-2.15 nice-0.0 usage-5.8 iowait-0.0 steal-0.0
    .
    .
    .

    PROCESSES:

    name: 'osysmond.bin' pid: 30891 #procfdlimit: 65536 cpuusage: 2.40 privmem: 35808
    shm: 81964 #fd: 119 #threads: 13 priority: -100 nice: 0 state: S
    .
    .
    .

    DEVICES:

    sdi ior: 0.000 iow: 0.000 ios: 0 qlen: 0 wait: 0 type: SYS
    sda1 ior: 0.000 iow: 61.495 ios: 629 qlen: 0 wait: 0 type: SYS
    .
    .
    .

    NICS:

    lo netrr: 39.935  netwr: 39.935  neteff: 79.869  nicerrors: 0 pktsin: 25
    pktsout: 25  errsin: 0  errsout: 0  indiscarded: 0  outdiscarded: 0
    inunicast: 25 innonunicast: 0  type: PUBLIC
    eth0 netrr: 1.412  netwr: 0.527  neteff: 1.939  nicerrors: 0 pktsin: 15
    pktsout: 4  errsin: 0  errsout: 0  indiscarded: 0  outdiscarded: 0
    inunicast: 15  innonunicast: 0  type: PUBLIC  latency: <1

    FILESYSTEMS:

    mount: / type: rootfs total: 563657948 used: 78592012 available: 455971824
    used%: 14 ifree%: 99 GRID_HOME
    .
    .
    .

    PROTOCOL ERRORS:

    IPHdrErr: 0 IPAddrErr: 0 IPUnkProto: 0 IPReasFail: 0 IPFragFail: 0
    TCPFailedConn: 5197 TCPEstRst: 717163 TCPRetraSeg: 592 UDPUnkPort: 103306
    UDPRcvErr: 70

**Parent topic:** [OCLUMON Command Reference](oclumon-command-reference.md)
