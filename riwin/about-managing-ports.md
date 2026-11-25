## About Managing Ports

During installation, Oracle Universal Installer (OUI) assigns port numbers to components from a set of default port numbers. Many Oracle Real Application Clusters (Oracle RAC) components and services use ports.

As an administrator, it is important to know the port numbers used by these services, and to ensure that the same port number is not used by two services on your system.

Most port numbers are assigned during installation. Every component and service has an allotted port range, which is the set of port numbers Oracle RAC attempts to use when assigning a port. Oracle RAC starts with the lowest number in the range and performs the following checks:

- Is the port used by another Oracle Database installation on the system?

  The installation can be either active or inactive at the time; Oracle Database can still detect if the port is used.

- Is the port used by a process that is currently running?

  This could be any process on the host, including processes other than Oracle Database processes.

If the answer to any of the preceding questions is yes, then Oracle RAC moves to the next highest port in the allotted port range and continues checking until it finds a free port.

**Parent topic:** [Managing Oracle Database Port Numbers](managing-oracle-database-port-numbers.md)
