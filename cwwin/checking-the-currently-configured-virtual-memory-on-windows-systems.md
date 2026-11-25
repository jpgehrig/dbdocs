## Checking the Currently Configured Virtual Memory on Windows Systems

Virtual memory (also known as a paging file) stores information that cannot fit in RAM, the main memory for the computer. All processes share the paging files, and a lack of space in the paging files can prevent processes from allocating memory.

Oracle recommends that you set the paging file size to match the amount of RAM available on the server, up to a maximum of 16 GB. If possible, split the paging file into multiple files on multiple physical devices. This configuration encourages parallel access to virtual memory, and improves the software performance.

1.  From the Control panel, select System.
2.  In the System Properties window, select the Advanced tab.
3.  Under Performance, click Performance Options, or Settings.
4.  In the Performance Options window, click the Advanced tab.

The virtual memory configuration is displayed at the bottom of the window.

If necessary, refer to your operating system documentation for information about how to configure additional virtual memory.

**Parent topic:** [Checking Server Hardware and Memory Configuration](checking-server-hardware-and-memory-configuration.md)
