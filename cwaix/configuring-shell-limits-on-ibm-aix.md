For IBM AIX on POWER Systems (64-bit), it is the ulimit settings that determine process memory related resource limits. Use these instructions to display and change the shell limit values if they are different from the recommended value.

Set shell limits for the Oracle Grid Infrastructure installation owner and for `root`. Verify that unlimited is set for both accounts either by using the `smit` utility or by editing the `/etc/security/limits` file. The root user requires these settings because the crs daemon (`crsd`) runs as `root`.

Verify that the shell limits displayed in the following table are set to the values shown:

Table A-2 Recommended Shell Limit Values

| Shell Limit (As Shown in smit) | Recommended Value                                    |
|:-------------------------------|:-----------------------------------------------------|
| Soft File Descriptors          | at least 1024                                        |
| Hard File Descriptors          | at least 65536                                       |
| Number of processes (Soft)     | at least 2047                                        |
| Number of processes (Hard)     | at least 16384                                       |
| Soft STACK size                | at least 10240 KB                                    |
| Hard STACK size                | at least 10240 KB; at most 32768 KB                  |
| Soft FILE size                 | unlimited                                            |
| Soft CPU time                  | unlimited<br>**Note:**<br>This is the default value. |
| Soft DATA segment              | unlimited                                            |
| Soft Real Memory size          | unlimited                                            |

To display the current value specified for these shell limits, and to change them if necessary

1.  Enter the following command:
        # smit chuser
2.  In the User NAME field, enter the user name of the Oracle software owner, for example `oracle`.
3.  Scroll down the list and verify the values shown for the limits listed in the previous table.
    If necessary, edit the existing value. To edit the values, you can use the `smit` utility. However, to set the value of Soft Real Memory size, you must edit the file `/etc/security/limits`. If you have permissions to run the `smit` utility, then you automatically have the permissions to edit the limits file.
4.  When you have finished making changes, press F10 to exit.

**Parent topic:** [Configuring Shell Limits and System Configuration Parameters for IBM AIX](configuring-shell-limits-and-system-configuration.md)
