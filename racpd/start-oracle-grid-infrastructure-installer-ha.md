## Start the Oracle Grid Infrastructure Installer

Use this procedure to start up the Oracle Grid Infrastructure installer, and provide information for the configuration.

**Note:**

The instructions in the "Oracle Database Patch 34130714 - GI Release Update 19.16.0.0.220719" patch notes tell you to use `opatchauto` to install the patch. However, this patch should be applied by the Oracle Grid Infrastructure installer using the `-applyRU` argument

1.  From your client connection to the Podman container as the Grid user on `racnode1`, start the installer, using the following command:

        /u01/app/19c/grid/gridSetup.sh -applyRU /software/stage/34130714 \
        -applyOneOffs /software/stage/34339952,/software/stage/32869666

2.  Choose the option Configure Grid Infrastructure for a New Cluster, and click Next.

    The Select Cluster Configuration window appears.

3.  Choose the option Configure an Oracle Standalone Cluster, and click Next.

4.  In the Cluster Name and SCAN Name fields, enter the names for your cluster, and for the cluster Single Client Access Names (SCANs) that are unique throughout your entire enterprise network. For this example, we used these names:

    - Cluster Name: `raccluster01`
    - SCAN Name: `racnode-scan`
    - SCAN Port : `1521`

5.  If you have configured your domain name server (DNS) to send to the GNS virtual IP address name resolution, then you can select Configure GNS requests for the subdomain GNS servers. Click Next.

6.  In the Public Hostname column of the table of cluster nodes, check to see that you have the following values set

    - Public Hostname:
      - `racnode1.example.info`
      - `racnode2.example.info`
    - Virtual Hostname:
      - `racnode1-vip.example.info`
      - `racnode2-vip.example.info`

7.  Click SSH connectivity, and set up SSH between `racnode1` and `racnode2`.

    When SSH is configured, click Next.

8.  On the Network Interface Usage window, select the following:

    - `eth0 10.0.20.0` for the Public network
    - `eth1 192.168.17.0` for the first Oracle ASM and Private network
    - `eth2 192.168.18.0` for the second Oracle ASM and Private network

    After you make those selections, click Next.

9.  On the Storage Option window, select Use Oracle Flex ASM for Storage and click Next.

10. On the GIMR Option window, select default, and click Next.

11. On the Create ASM Disk Group window, click Change Discovery Path, and set the value for Disk Discovery Path to `/dev/asm*`, and click OK. Provide the following values:

    - Disk group name: `DATA`
    - Redundancy: `External`
    - Select the default, Allocation Unit Size
    - Select Disks, and provide the following values:
      - `/dev/asm-disk1`
      - `/dev/asm-disk2`

    When you have entered these values, click. Next.

12. On the ASM Password window, provide the passwords for the `SYS` and `ASMSNMP` users, and click Next.

13. On the Failure Isolation window, Select the default, and click Next.

14. On the Management Options window, select the default, and click Next.

15. On the Operating System Group window, select the default, and click Next.

16. On the Installation Location window, for Oracle base, enter the path `/u01/app/grid`, and click Next.

17. On the Oracle Inventory window, for Inventory Directory, enter `/u01/app/oraInventory`, and click Next.

18. On the Root Script Execution window, select the default, and click Next.

19. On the Prerequisite Checks window, under Verification Results, you may see a `Systemd` status warning. You can ignore this warning, and proceed.

    If you encounter an unexpected warning, then please refer to Known Issues in My Oracle Support ID 2885873.1.

20. On the Prerequisite Checks window, it is possible that you can see a warning indicating that `cvuqdisk-1.0.10-1` is missing, and see the failure message "Device Checks for ASM" failed. If this warning appears, then you must install the package `cvuqdisk-1.0.10-1` on both the containers. In this case:
    - The Fix & Check Again button is disabled, and you need to install the package manually. Complete the following steps:

      1.  Open a terminal, and log in as `root` to `racnode1 /bin/bash`.

      2.  Run the following command to install the `cvuqdisk` RPM package:

              rpm -ivh /tmp/GridSetupActions*/CVU_*/cvuqdisk-1.0.10-1.rpm

      3.  Click Check Again.

      4.  Repeat steps a and b to install the RPM on `racnode2`.

      You should not see any further warnings or failure messages. The installer should automatically proceed to the next window.

21. Click Install.

22. When prompted, run `orainstRoot.sh` and `root.sh` on `racnode1` and `racnode2`.

23. After installation is complete, confirm that the CRS stack is up:

        $ORACLE_HOME/bin/crsctl stat res -t

**Parent topic:** [Run the Oracle Grid Infrastructure Installer](run-oracle-grid-infrastructure-installer.md)
