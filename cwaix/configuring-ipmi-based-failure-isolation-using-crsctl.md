On Oracle Solaris and AIX platforms, where Oracle does not currently support the native IPMI driver, DHCP addressing is not supported and manual configuration is required for IPMI support.

Oracle Universal Installer (OUI) will not collect the administrator credentials, so failure isolation must be manually configured, the BMC must be configured with a static IP address, and the address must be manually stored in the OLR.

Configure BMC as described in this guide.

1.  If necessary, start Oracle Clusterware using the following command:
        $ crsctl start crs
2.  Use the BMC management utility to obtain the BMC’s IP address and then use the cluster control utility crsctl to store the BMC’s IP address in the Oracle Local Registry (OLR) by issuing the crsctl set css ipmiaddr address command. For example:
        $crsctl set css ipmiaddr 192.168.10.45
3.  Enter the following crsctl command to store the user ID and password for the resident BMC in the OLR, where youradminacct is the IPMI administrator user account, and provide the password when prompted:
        $ crsctl set css ipmiadmin youradminact
        IPMI BMC Password:

    This command attempts to validate the credentials you enter by sending them to another cluster node. The command fails if that cluster node is unable to access the local BMC using the credentials.

    When you store the IPMI credentials in the OLR, you must have the anonymous user specified explicitly, or a parsing error will be reported.

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
