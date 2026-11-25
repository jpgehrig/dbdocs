The bare metal server production deployment consists of two separate Docker hosts, each mounted on independent bare metal servers.

The first is of a single Docker host, Docker Host 1, that contains two containers, container 2 and container 1. Container 2 connects to an Oracle Database called HRPROD. It contains an ASM instance, ASM1, database instance 1, and an Oracle Clusterware instance. Container 1 connects to an Oracle Database called ERPPROD. It contains an ASM instance, ASM1, database instance 1, and an Oracle Clusterware instance. Docker host 1 is on a separate Oracle Linux 7 bare metal server.

The second is of a single Docker host, Docker Host 2, that contains two containers, container 2 and container 1. Container 2 connects to HRPROD. It contains an ASM instance, ASM2, database instance 2 and an Oracle Clusterware instance. Container 1 connects to ERPPROD. It contains an ASM instance, ASM2, database instance 2, and an Oracle Clusterware instance. Docker host 2 is on a separate Oracle Linux 7 bare metal server.

As a result of this configuration, the two instances of HRPROD are on physically separate bare metal servers, and the two instances of ERPPROD are on separate physical servers. If either server goes down, then instances are available on the other server to maintain service to clients.
