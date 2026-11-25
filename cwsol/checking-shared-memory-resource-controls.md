Use the `prctl` command to make runtime interrogations of and modifications to the resource controls associated with an active process, task, or project on the system.

To view the current value of project.max-shm-memory set for a project and system-wide:

    # prctl -n project.max-shm-memory -i project default

default is the project ID obtained by running the `id -p` command.

For example, to change the setting for project.max-shm-memory to 6 GB for the project default without a reboot:

    prctl -n project.max-shm-memory -v 6gb -r -i project default

**Related Topics**

- [Administering Oracle Solaris 11](http://docs.oracle.com/cd/E23824_01/index.html)

**Parent topic:** [Configuring Kernel Parameters on Oracle Solaris](configuring-kernel-parameters-on-oracle-solaris.md)
