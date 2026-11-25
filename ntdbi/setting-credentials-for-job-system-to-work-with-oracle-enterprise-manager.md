## Setting Credentials for the Job System to Work with Oracle Enterprise Manager

Windows systems require that you set the correct credentials for the Jobs system to work properly in Oracle Enterprise Manager.

By default, the Management Agent service is installed as a `LocalSystem` user. When submitting jobs, such as stopping or starting the database, the operating system user submitting the job must have the Log on as a batch job privilege enabled.

Perform the following steps to establish that privilege for any operating system user who must submit an Oracle Enterprise Manager job.

1.  Under the Security Settings list, expand the list to Local Policies.

2.  Under Local Policies, double-click User Rights Assignment.

3.  Under Policy, search for the Log on as a batch job policy.

    If the Management Agent service is installed as any other user (that is, not `LocalSystem`), then, in addition to granting the Log on as a batch job privilege, you must grant the Windows service user the following three privileges:

    - Act as part of the operating system

    - Adjust memory quotas for a process

    - Replace a process level token

      The service under the "Windows service" user runs at the operating system level.

4.  With each policy, perform the following steps:

    1.  Double-click the policy name.

    2.  In the Properties dialog box, click Add User or Group.

    3.  In the Select Users or Groups dialog box, enter the name of the user (for example, `jsmith`, `administrator`, and so on.)

        **Note:**

        On Windows Server 2008, the name of the dialog box is Select Users, Computers, or Groups.

    4.  Click Check Names to check that you have entered the name correctly.

    5.  Click OK.

5.  Click OK to exit the Properties dialog box, then exit Local Security Settings and Administrative Tools.

6.  Restart your computer.

If a user exists locally and at the domain level, Windows gives the local user precedence. To use the domain user, qualify the user name with the domain name. For example, to use the user `joe` in the `ACCOUNTS` domain specify the user name as `ACCOUNTS\joe`.

**Parent topic:** [Configuring Oracle Components](configuring-oracle-components.md)
