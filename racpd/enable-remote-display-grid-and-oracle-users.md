## Enable Remote Display

To ensure that your client can display the installation windows, you must enable remote display control of your Oracle Real Application Clusters (Oracle RAC) on the container environment.

In this example, we enable remote display from the client to the container host, and log in as the Grid user.

1.  From the client machine, start `xhost` (in our case `user-client-1`):

        # hostname
        # xhost + 10.0.20.150

    **Note:**

    `10.0.20.150` is the IP address of the first Oracle RAC container (`racnode1`). This IP address is reachable from our client machine.

2.  From the client, use SSH to log in to the Oracle RAC Container (`racnode1`) as the `grid` user:

        # ssh -X grid@10.0.20.150

3.  When prompted for a password, provide the `grid` user password, and then export the display inside the `racnode1` container to the client, where `display_computer` is the client system, and `port` is the port for the display:

        $ export DISPLAY=display_computer:port

    **Note:**

    You can only use the private IP address of the client as the export target for `DISPLAY`.

**Parent topic:** [Configure Remote Display for Installation](configure-remote-display-installation.md)
