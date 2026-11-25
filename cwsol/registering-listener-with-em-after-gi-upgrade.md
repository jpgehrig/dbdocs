After upgrading Oracle Grid Infrastructure, add the new resource targets to Oracle Enterprise Manager Cloud Control.

Discover and add new resource targets in Oracle Enterprise Manager after Oracle Grid Infrastructure upgrade. The following procedure provides an example of discovering an Oracle ASM listener target after upgrading Oracle Grid Infrastructure:

1.  Log in to Oracle Enterprise Manager Cloud Control.
2.  From the Setup menu, select Add Target, and then select Add Targets Manually.
    The Add Targets Manually page is displayed.
3.  In the Add Targets page, select the Add Using Guided Process option and Target Type as `Oracle Database, Listener and Automatic Storage Management`.
    For any other resource to be added, select the appropriate Target Type in Oracle Enterprise Manager discovery wizard.
4.  Click Add Using Guided Process.
    The Target Discover wizard is displayed.
5.  For the Specify Host or Cluster field, click on the Search icon and search for Target Types of `Hosts`, and select the corresponding Host.
6.  Click Next.
7.  In the Target Discovery: Results page, select the discovered Oracle ASM Listener target, and click Configure.
8.  In the Configure Listener dialog box, specify the listener properties and click OK.
9.  Click Next and complete the discovery process.
    The listener target is discovered in Oracle Enterprise Manager with the status as Down.
10. From the Targets menu, select the type of target.
11. Click the target name to navigate to the target home page.
12. From the host, database, middleware target, or application menu displayed on the target home page, select Target Setup, then select Monitoring Configuration.
13. In the Monitoring Configuration page for the listener, specify the host name in the Machine Name field and the password for the `ASMSNMP` user in the Password field.
14. Click OK.

Oracle ASM listener target is displayed with the correct status.

Similarly, you can add other clusterware resources to Oracle Enterprise Manager after an Oracle Grid Infrastructure upgrade.

**Parent topic:** [Updating Oracle Enterprise Manager Cloud Control Target Parameters](updating-oracle-enterprise-manager-cloud-control-target-parameters.md)
