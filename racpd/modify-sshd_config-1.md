## Modify sshd_config

To run the installation of Oracle Real Application Clusters (Oracle RAC), you must modify the configuration file, `sshd_config` so that X11 forwarding is enabled.

Run the following on `racnode1` only.

Edit the `sshd` configuration file `/etc/ssh/sshd_config` and set the following parameters:

    X11Forwarding yes
    X11UseLocalhost no
    X11DisplayOffset 10

Restart `sshd`:

    # systemctl daemon-reload
    # systemctl restart sshd

You do not need to repeat these steps on `racnode2`, because Oracle RAC installations are run from a single node.

**Parent topic:** [Configure Remote Display for Installation](configure-remote-display-installation.md)
