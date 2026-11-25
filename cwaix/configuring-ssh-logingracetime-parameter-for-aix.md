On AIX systems, configure the OpenSSH parameter to avoid timeout errors.

On AIX systems, the OpenSSH parameter LoginGraceTime by default is commented out, and the default behavior of OpenSSH on AIX can sometimes result in timeout errors. To avoid these errors, complete the following procedure:

1.  Log in as `root`.
2.  Using a text editor, open the OpenSSH configuration file `/etc/ssh/sshd_config`.
3.  Locate the comment line `#LoginGraceTime 2m`.
4.  Uncomment the line, and change the value to `0 (unlimited)`.
    For example:

         LoginGraceTime 0
5.  Save `/etc/ssh/sshd_config`.
6.  Restart SSH.

**Parent topic:** [Tuning AIX System Environment](tuning-aix-system-environment.md)
