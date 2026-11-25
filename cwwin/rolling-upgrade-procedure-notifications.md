## Rolling Upgrade Procedure Notifications

Be aware of this information regarding rolling upgrades.

- During rolling upgrades of the operating system, Oracle supports using different operating system binaries when both versions of the operating system are certified with the Oracle Database release you are using.

- Using mixed operating system versions is supported during upgrade only.

  Be aware that mixed operating systems are supported only for the duration of an upgrade, over the period of a few hours.

- Oracle Clusterware does not support nodes that have processors with different instruction set architectures (ISAs) in the same cluster. Each node must be binary compatible with the other nodes in the cluster.

  For example, you cannot have one node using an Intel 64 processor and another node using an IA-64 (Itanium) processor in the same cluster. You could have one node using an Intel 64 processor and another node using an AMD64 processor in the same cluster because the processors use the same x86-64 ISA and run the same binary release of Oracle software.

**Note:**

Your cluster can have nodes with processors of different manufacturers, speeds, or sizes, but this is not recommended.

**Parent topic:** [Reviewing Operating System and Software Upgrade Best Practices](reviewing-operating-system-and-software-upgrade-best-practices.md)
