# Description of the illustration cwadd006b.eps

This figure depicts the startup process for Oracle Clusterware. The INIT process starts `ohasd`, which, in turn, starts the `oraagent`, `orarootagent`, and `cssdagent`. These processes then carry out the following steps:

- The `oraagent` starts `mdnsd`, `evmd`, Oracle ASM, `gpnpd`, and `gipcd` (Grid IPC daemon).

- The `orarootagent` starts `OSYSMOND` (which, on some nodes, starts `OLOGGERD`, not shown in the graphic), `ctssd`, the CSSD Monitor, `diskmon` (Disk Monitor daemon), and `crsd`. The `crsd`, in turn, starts another `oraagent` and another `orarootagent`.

  The `oraagent` starts Oracle Notification Service (ONS and eONS), an Oracle ASM instance (which communicates with Oracle ASM started by the `oraagent` that `ohasd` started), the database instance, the listeners, and the SCAN listeners

  The `orarootagent` starts `gnsd`, the VIPs, the SCAN VIP, and the network resources. Additionally, the `orarootagent` starts the Oracle ADVM volume, Oracle ACFS, the NFS service, the high-availability NFS service, and the high-availability VIP.

- The `cssdagent` starts Cluster Synchronization Service (`ocssd`).
