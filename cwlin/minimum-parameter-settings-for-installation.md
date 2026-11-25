## Minimum Parameter Settings for Installation

Use this table to set parameters manually if you cannot use the fixup scripts.

**Note:**

- Unless otherwise specified, the kernel parameter and shell limit values shown in the following table are minimum values only. For production database systems, Oracle recommends that you tune these values to optimize the performance of the system. See the operating system documentation for more information about tuning kernel parameters.

- If the current value for any parameter is greater than the value listed in this table, then the Fixup scripts do not change the value of that parameter.

Table B-1 Minimum Operating System Resource Parameter Settings

| Parameter                            | Value                                                                                                                                 | File                                     |
|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------|
| semmsl<br>semmns<br>semopm<br>semmni | 250<br>32000<br>100<br>128                                                                                                            | `/proc/sys/kernel/sem`                   |
| shmall                               | Greater than or equal to the value of shmmax, in pages.                                                                               | `/proc/sys/kernel/shmall`                |
| shmmax                               | Half the size of physical memory in bytes<br>See My Oracle Support Note 567506.1 for additional information about configuring shmmax. | `/proc/sys/kernel/shmmax`                |
| shmmni                               | 4096                                                                                                                                  | `/proc/sys/kernel/shmmni`                |
| panic_on_oops                        | 1                                                                                                                                     | `/proc/sys/kernel/panic_on_oops`         |
| file-max                             | 6815744                                                                                                                               | `/proc/sys/fs/file-max`                  |
| aio-max-nr                           | 1048576<br>Note: This value limits concurrent outstanding requests and should be set to avoid I/O subsystem failures.                 | `/proc/sys/fs/aio-max-nr`                |
| ip_local_port_range                  | Minimum: 9000<br>Maximum: 65500                                                                                                       | `/proc/sys/net/ipv4/ip_local_port_range` |
| rmem_default                         | 262144                                                                                                                                | `/proc/sys/net/core/rmem_default`        |
| rmem_max                             | 4194304                                                                                                                               | `/proc/sys/net/core/rmem_max`            |
| wmem_default                         | 262144                                                                                                                                | `/proc/sys/net/core/wmem_default`        |
| wmem_max                             | 1048576                                                                                                                               | `/proc/sys/net/core/wmem_max`            |

**Parent topic:** [Configuring Kernel Parameters for Linux](configuring-kernel-parameters-for-linux.md)
