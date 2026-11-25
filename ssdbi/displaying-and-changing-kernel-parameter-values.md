Use these procedures to display the current value specified for resource controls and to change them if necessary:

### Displaying Resource Control Values

1.  To display the current values of the resource control:

        $ id -p // to verify the project id
        uid=100(oracle) gid=100(dba) projid=1 (group.dba)
        $ prctl -n project.max-shm-memory -i project group.dba
        $ prctl -n project.max-sem-ids -i project group.dba

2.  To change the current values use the `prctl` command. For example:

    - To modify the value of max-shm-memory to 6 GB:

          # prctl -n project.max-shm-memory -v 6gb -r -i project group.dba

    - To modify the value of max-sem-ids to 256:

          # prctl -n project.max-sem-ids -v 256 -r -i project group.dba

    **Note:**

    When you use the `prctl` command (Resource Control) to change system parameters, you do not have to restart the system for these parameter changes to take effect. However, the changed parameters do not persist after a system restart.

### Modifying Resource Control Values

Use the following procedure to modify the resource control project settings, so that they persist after a system restart:

1.  By default, Oracle instances are run as the `oracle` user of the dba group. A project with the name `group.dba` is created to serve as the default project for the `oracle` user. Run the `id `command to verify the default project for the `oracle` user:

        # su - oracle
        $ id -p
        uid=100(oracle) gid=100(dba) projid=100(group.dba)
        $ exit

2.  To set the maximum shared memory size to 2 GB, run the `projmod` command:

        # projmod -sK "project.max-shm-memory=(privileged,2G,deny)" group.dba

    Alternatively, add the resource control value `project.max-shm-memory=(privileged,2147483648,deny)` to the last field of the project entries for the Oracle project.

3.  Check the values for the `/etc/project` file:

        # cat /etc/project

    The output is similar to the following:

        system:0::::
        user.root:1::::
        noproject:2::::
        default:3::::
        group.staff:10::::
        group.dba:100:Oracle default project ::: project.max-shm-memory=(privileged,2147483648,deny)

4.  To verify that the resource control is active, check process ownership, and run the commands `id` and `prctl`:

        # su - oracle
        $ id -p
        uid=100(oracle) gid=100(dba) projid=100(group.dba)
        $ prctl -n project.max-shm-memory -i process $$
        process: 5754: -bash
        NAME                    PRIVILEGE     VALUE     FLAG     ACTION    RECIPIENT
        project.max-shm-memory  privileged    2.00GB     -       deny

**Note:**

The value for the maximum shared memory depends on the SGA requirements and should be set to a value greater than the SGA size.

**Related Topics**

- [Oracle Solaris Tunable Parameters Reference Manual](http://docs.oracle.com/en/operating-systems/solaris.html)

**Parent topic:** [Configuring Kernel Parameters on Oracle Solaris](configuring-kernel-parameters-on-oracle-solaris.md)
