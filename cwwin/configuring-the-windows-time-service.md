## Configuring the Windows Time Service

The Windows Time service (W32Time) provides network clock synchronization on computers running Microsoft Windows.

If you are using Windows Time service, and you prefer to continue using it instead of Cluster Time Synchronization Service, then you must modify the Windows Time service time jump settings, to allow the time to gradually match with the reference time. Restart the Windows Time service after you complete this task.

1.  To configure Windows Time service, use the following command on each node:
        C:\> W32tm /register
2.  To modify the Windows Time service to work in an Oracle RAC environment, perform the following steps:
    1.  Open the Registry Editor (regedit)
    2.  Locate the `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time\Config` key.
    3.  Set the following Windows Time service parameters to these decimal values:
        - `MaxPosPhaseCorrection` to 600

        - `MaxNegPhaseCorrection` to 600

        - `MaxAllowedPhaseOffset` to 600

        These parameter settings specify that small time adjustments are allowed when the time difference between the reference and cluster nodes is under 10 minutes.

    **Note:**

    You should configure the Windows Time service to meet the requirements of your environment, with assistance from Microsoft, if necessary. The recommended settings provided for the three parameters are the settings that Oracle recommends to allow time adjustments to happen through slewing (gradually adjusting the clock using small changes) rather than in large steps (setting the clock to a new time). Large time adjustments in a single step are not supported.
3.  To put the changes into effect, use the following command:
        C:\> W32tm /config /update

**See Also:**

For more information about using and configuring the Windows Time Service, see:

- Microsoft® Support article ID 816042: "How to configure an authoritative time server in Windows Server"

- Microsoft® Support article ID 939322: "Support boundary to configure the Windows Time service for high accuracy environments"

- [NTP FAQ and HOW TO](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwwin&id=ntp_faq)

**Parent topic:** [Configuring Time Synchronization for the Cluster](configuring-time-synchronization-for-the-cluster.md)
