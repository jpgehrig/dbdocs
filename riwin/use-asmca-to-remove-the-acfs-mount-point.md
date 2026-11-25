## Using Oracle ASMCA to Remove the ACFS Mount Point

Now you have configured the mount point using Direct NFS, you can remove the Oracle Automatic Storage Management Cluster File System (Oracle ACFS) mount point using Oracle Automatic Storage Management Configuration Assistant (ASMCA).

When creating Oracle ACFS file systems on Windows, run ASMCA as a Windows domain user who is also an administrator of the computer.

1.  From the `Grid_home``/bin` directory, run `asmca.exe` to start the ASMCA.
2.  Select the ASM Cluster File System tab.
3.  Select the mount point created earlier (`C:\oradatamnt`), then click Dismount All.
4.  Select the Volumes tab.
5.  Right-click the mount point and then select Delete.

**Parent topic:** [Creating an Oracle RAC Database on Direct NFS](creating-an-oracle-rac-database-on-direct-nfs.md)
