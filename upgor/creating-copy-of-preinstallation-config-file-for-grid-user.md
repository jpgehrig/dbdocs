Create a copy of the preinstallation configuration file for the `grid` user to set hard and soft limits for the operating system parameters.

1.  As the `root` user, go to the `/etc/security/limits.d` directory.
        # cd /etc/security/limits.d
2.  Create a copy of the preinstallation configuration file for the `grid` user by replacing the `oracle` user with the `grid` user.
        # cat oracle-database-preinstall-19c.conf | sed 's/oracle /grid /g' > oracle-grid-user-preinstall-19c.conf
3.  Delete the preinstallation configuration files for the earlier release.
        # rm -r -f oracle-database-preinstall-18c.conf oracle-grid-user-preinstall-18c.conf

**Parent topic:** [Preparing to Upgrade Oracle Restart](preparing-to-upgrade-oracle-restart.md)
