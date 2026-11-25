If you do not use a Fixup script or CVU to set ephemeral ports, then set TCP/IP ephemeral port range parameters to provide enough ephemeral ports for the anticipated server workload.

Check your current range for ephemeral ports:

    # /usr/bin/ndd /dev/tcp tcp_largest_anon_port

    65535

In the preceding example, tcp_largest_anon_port is set to the default value.

If necessary, edit the file `/etc/rc.config.d/nddconf` and add entries to update the UDP and TCP ephemeral port values. For example:

    TRANSPORT_NAME[0]=tcp
    NDD_NAME[0]=tcp_largest_anon_port
    NDD_VALUE[0]=65500


    TRANSPORT_NAME[1]=udp
    NDD_NAME[1]=udp_largest_anon_port
    NDD_VALUE[1]=65500

Ensure that the entries are numbered in proper order. For example, if there are two entries present for the TCP and UDP ports in nddconf, then they are numbered 0 through 1: TRANSPORT_NAME\[0\]=tcp and TRANSPORT_NAME\[1\]=udp.

**Parent topic:** [Configuring Kernel Parameters on HP-UX Itanium Systems](configuring-kernel-parameters-on-hp-ux-itanium-systems.md)
