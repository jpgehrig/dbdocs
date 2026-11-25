Use this table to set parameters manually if you cannot use the fixup scripts.

Table B-1 Minimum Oracle Solaris Resource Control Parameter Settings

| Resource Control       | Minimum Value                                                                                                              |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------|
| project.max-sem-ids    | 100                                                                                                                        |
| process.max-sem-nsems  | 256                                                                                                                        |
| project.max-shm-memory | This value varies according to the RAM size.<br>See section “Requirements for Shared Memory Resources” for minimum values. |
| project.max-shm-ids    | 100<br>See section “Configuring Additional Shared Memory Identifiers Limit”.                                               |
| tcp_smallest_anon_port | 9000                                                                                                                       |
| tcp_largest_anon_port  | 65500                                                                                                                      |
| udp_smallest_anon_port | 9000                                                                                                                       |
| udp_largest_anon_port  | 65500                                                                                                                      |

### Guidelines for Setting Resource Control Parameters

- Unless otherwise specified, the kernel parameter and shell limit values in the preceding table are minimum values only. Verify that the kernel parameters shown in the preceding table are set to values greater than or equal to the minimum value shown. For production database systems, Oracle recommends that you tune these values to optimize the performance of the system. See your operating system documentation for more information about kernel resource management.

- If the current value for any parameter is greater than the value listed in the preceding table, then the Fixup scripts do not change the value of that parameter.

- The project.max-shm-memory resource control value assumes that no other application is using the shared memory segment from this project other than the Oracle instances. If applications, other than the Oracle instances are using the shared memory segment, then you must add that shared memory usage to the project.max-shm-memory resource control value.

- project.max-shm-memory resource control = the cumulative sum of all shared memory allocated on each Oracle database instance started under the corresponding project.

- Ensure that memory_target or max_sga_size does not exceed process.max-address-space and project.max-shm-memory. For more information, see My Oracle Support Note [1370537.1](https://support.oracle.com/rs?type=doc&id=1370537.1).

### Requirements for Shared Memory Resources project.max-shm-memory

Table B-2 Requirement for Resource Control project.max-shm-memory

| RAM                | project.max-shm-memory setting   |
|:-------------------|:---------------------------------|
| 1 GB to 16 GB      | Half the size of physical memory |
| Greater than 16 GB | At least 8 GB                    |

**Parent topic:** [Configuring Kernel Parameters on Oracle Solaris](configuring-kernel-parameters-on-oracle-solaris.md)
