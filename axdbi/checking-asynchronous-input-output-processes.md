On IBM AIX 6 and IBM AIX 7, the Asynchronous Input Output (AIO) device drivers are enabled by default. For both IBM AIX 6 and IBM AIX 7, increase the number of aioserver processes from the default value. The recommended value for aio_maxreqs is 64k (65536). Confirm this value for both IBM AIX 6 and IBM AIX 7.

Confirm the aio_maxreqs value using the following procedure:

    # ioo –o aio_maxreqs
    aio_maxreqs = 65536

When performing an asynchronous I/O to a file system, each asynchronous I/O operation is tied to an asynchronous I/O server. Thus, the number of asynchronous I/O servers limits the number of concurrent asynchronous I/O operations in the system.

The initial number of servers that are started during a system restart is determined by the aio_minservers parameter. As concurrent asynchronous I/O operations occur, additional asynchronous I/O servers are started, up to a maximum of the value set in the aio_maxservers parameter.

In general, to set the number of asynchronous I/O servers, complete the following procedure:

1.  Adjust the initial value of aio_maxservers to 10 times the number of logical disks divided by the number of CPUs that are to be used concurrently but no more than 80.
2.  Monitor the performance effects on the system during periods of high I/O activity. If all AIO server processes are started, then increase the aio_maxservers value. Also, continue to monitor the system performance during peak I/O activity to determine if there was a benefit from the additional AIO servers. Too many asynchronous I/O servers increase memory and processor overload of additional processes, but this disadvantage is small.
    See your operating system vendor documentation for information about tuning AIO parameters.

To monitor the number of AIO server processes that have started, enter the following:

    # ps -ek|grep -v grep|grep –v posix_aioserver|grep -c aioserver

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
