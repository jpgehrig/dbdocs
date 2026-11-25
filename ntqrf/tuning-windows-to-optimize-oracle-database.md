Learn how to tune the Windows Server operating system to ensure that Oracle Database is running in the best possible environment.

**Note:**

For the sake of brevity, this discussion uses the collective term Windows Server when a statement applies to all supported Windows operating systems.

- [Overview of Windows Tuning](overview-of-windows-tuning.md)
  Learn about tuning Windows Server operating system.
- [Overview of Large Page Support](overview-of-large-page-support.md)
  Large page support is a feature of Oracle Database.
- [About Reducing Priority of Foreground Applications on Server Console](about-reducing-priority-of-foreground-applications-on-server-console.md)
  One of the settings provided by default during the installation of a Windows Server gives the interactive foreground applications a priority over every background process.
- [About Configuring Windows Server to Be an Application Server](about-configuring-windows-server-to-be-an-application-server.md)
  Windows memory manager divides up system memory into three different pools, described in Windows Server Memory Shares.
- [About Disabling Unnecessary Services](about-disabling-unnecessary-services.md)
  After you have significantly reduced the file cache, you can retrieve additional physical memory for Oracle Database by disabling services not needed for core operating system functionality.
- [About the Necessity to Remove Unused Network Protocols](about-the-necessity-to-remove-unused-network-protocols.md)
  Remove all unnecessary network protocols on Windows so that the processing time can be concentrated on servicing only critical protocols.
- [About the Necessity to Reset Network Protocol Bind Order](about-the-necessity-to-reset-network-protocol-bind-order.md)
  If multiple protocols must be installed on the server, you can give the protocol most frequently used by Oracle Database the highest priority by resetting the network protocol bind order.
- [Setting the Order of Multiple Network Interface Cards](setting-the-order-of-multiple-network-interface-cards.md)
  If you have public and private network interface cards (NICs) on a single Windows computer and they are not in the correct order, then you might experience problems with any configuration (Oracle Enterprise Manager, for example) that uses `gethostname`.
- [Overview of the Latest Reliable Windows Server Service Pack](overview-of-latest-reliable-windows-server-service-pack.md)
  Microsoft releases operating system patches, called Service Packs, on a quarterly basis. Service Packs are a collection of bug fixes and product enhancements to the basic Windows Server release.
- [Overview of Hardware or Operating System Striping](overview-of-hardware-or-operating-system-striping.md)
  Learn about data striping, which is an effective means of reducing the impact of slow hard drives.
- [About Multiplex Windows Server Virtual Memory Paging File](about-multiplex-windows-server-virtual-memory-paging-file.md)
  Discusses about Multiplexing the Windows Server virtual memory paging file to boost system performance.
- [Closing All Unnecessary Foreground Applications](closing-all-unnecessary-foreground-applications.md)
  Learn about closing all unnecessary foreground applications.
