## Checking Resource Limits for Oracle Software Installation Users

For each installation software owner user account, check the resource limits for installation.

On Oracle Linux systems, Oracle recommends that you install Oracle Database Preinstallation RPMs to meet preinstallation requirements like configuring your operating system to set the resource limits in the `limits.conf` file.

Use the following ranges as guidelines for resource allocation to Oracle software installation owners for standard installations and to Oracle Grid Infrastructure software installation owners for job role separation:

Table 6-1 Oracle Software Installation Owner and Oracle Grid Infrastructure Software Installation Owner Resource Limit Recommended Ranges

| Resource Shell Limit                           | Resource | Soft Limit                                                                                                                                                                         | Hard Limit                                                                                                                                                                        |
|:-----------------------------------------------|:---------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Open file descriptors                          | nofile   | at least 1024                                                                                                                                                                      | at least 65536                                                                                                                                                                    |
| Number of processes available to a single user | nproc    | at least 2047                                                                                                                                                                      | at least 16384                                                                                                                                                                    |
| Size of the stack segment of the process       | stack    | at least 10240 KB                                                                                                                                                                  | at least 10240 KB, and at most 32768 KB                                                                                                                                           |
| Maximum locked memory limit                    | memlock  | at least 90 percent of the current RAM when HugePages memory is enabled and at least 3145728 KB (3 GB) when HugePages memory is disabled.<br>Note: `unlimited` on Exadata systems. | at least 90 percent of the current RAM when HugePages memory is enabled and at least 3145728 KB (3 GB) when HugePages memory is disabled<br>Note: `unlimited` on Exadata systems. |

To check resource limits:

1.  Log in as an installation owner.
2.  Check the soft and hard limits for the file descriptor setting. Ensure that the result is in the recommended range. For example:
        $ ulimit -Sn
        1024
        $ ulimit -Hn
        65536
3.  Check the soft and hard limits for the number of processes available to a user. Ensure that the result is in the recommended range. For example:
        $ ulimit -Su
        2047
        $ ulimit -Hu
        16384
4.  Check the soft limit for the stack setting. Ensure that the result is in the recommended range. For example:
        $ ulimit -Ss
        10240
        $ ulimit -Hs
        32768
5.  Repeat this procedure for each Oracle software installation owner.

If necessary, update the resource limits in the `/etc/security/limits.conf` configuration file for the installation owner. However, the configuration file may be distribution specific. Contact your system administrator for distribution specific configuration file information.

**Note:**

If you make changes to an Oracle installation user account and that user account is logged in, then changes to the `limits.conf` file do not take effect until you log these users out and log them back in. You must do this before you use these accounts for installation.

**Parent topic:** [Configuring Grid Infrastructure Software Owner User Environments](configuring-software-users-environments.md)
