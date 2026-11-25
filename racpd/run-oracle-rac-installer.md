## Run the Oracle RAC Installer

To proceed through the Oracle Real Application Clusters (Oracle RAC) installer screen workflow, run the installer, and answer questions as prompted.

1.  Run the installer with the following command:
        $ /u01/app/oracle/product/19c/dbhome_1/runInstaller -applyRU /software/stage/34130714
2.  Select Set Up Software only, and click Next.
3.  Choose Oracle Real Application Clusters database installation, and click Next.
4.  Ensure that both the `racnode1` and `racnode2` nodes are selected, and click SSH connectivity.
5.  In SSH connectivity, provide the SSH password, and click set up. Click OK after completing the SSH setup, and then click Next.
6.  Choose Enterprise Edition,and click Next.
7.  Set the Oracle base path to `/u01/app/oracle`, and click Next.
8.  On Operating System Groups, choose the default, and click Next.
9.  On Root Script execution, choose the default, and click Next.
10. Click Install.
11. When prompted, run `root.sh` on both of the nodes.
12. After the installation completes, click Close to exit the installer.

**Parent topic:** [Run the Oracle RAC Database Installer](run-oracle-rac-database-installer.md)
