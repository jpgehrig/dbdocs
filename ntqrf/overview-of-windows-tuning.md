Learn about tuning Windows Server operating system.

Windows Server operating systems offer considerably fewer tuning adjustments than UNIX systems. This difference constrains system administrators when they try to optimize Windows Server performance, but it also makes Windows Server easier to use.

You can make Windows Server a better application server environment for Oracle Database. Most of the operating system specific procedures described in this chapter enable Oracle Database to reserve more system resources, such as CPU, memory, and disk I/O.

In addition, because Oracle Database is a high-performance database management system that effectively uses resources of your Windows computer, it must not also serve as any of the following:

- Primary or backup domain controller

- File or print server

- Remote access server

- Router

These configurations consume network, memory, and CPU resources. In addition, the Windows computer that is running Oracle Database should not be locally accessed with a high frequency or intensively used for local user processing, unless it has enough resources to accommodate all this activity.

**Parent topic:** [Tuning Windows to Optimize Oracle Database](tuning-windows-to-optimize-oracle-database.md)
