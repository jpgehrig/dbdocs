## Load SSH Keys Into Memory Before Starting DBCA

In an Oracle RAC environment, you must load SSH keys into memory for the terminal session where you start DBCA. If you do not do this, then you receive user equivalency errors when you attempt to start DBCA.

If you use a pass phrase on your system for SSH, then you must provide the pass phrase to load the SSH keys.

Use the following commands to load SSH keys:

    $ exec /usr/bin/ssh-agent $SHELL
    $ /usr/bin/ssh-add

If needed, provide the pass phrase when prompted. You can then start DBCA.

**Parent topic:** [Tasks to Complete Before Using DBCA to Create any Oracle RAC Database](tasks-to-complete-before-using-dbca-to-create-any-oracle-rac-database.md)
