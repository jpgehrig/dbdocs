## Setting UDP and TCP Dynamic Port Range for Oracle RAC Installations

For certain configurations of Oracle RAC in high load environments it is possible for the system to exhaust the available number of sockets. To avoid this problem, expand the dynamic port range for both UDP and TCP.

1.  Open a command line window as an Administrator user.
2.  Run the following commands to set the dynamic port range:
        netsh int ipv4 set dynamicport udp start=9000 num=56000
        netsh int ipv4 set dynamicport tcp start=9000 num=56000
3.  Run the following commands to verify that the dynamic port range was set:
        netsh int ipv4 show dynamicport udp
        netsh int ipv4 show dynamicport tcp

    For IPv6 network, replace IPv4 with IPv6 in the above examples.

**Parent topic:** [Managing Oracle Database Port Numbers](managing-oracle-database-port-numbers.md)
