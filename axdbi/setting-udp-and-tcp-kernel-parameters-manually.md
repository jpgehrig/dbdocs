If you do not use a Fixup script or CVU to set ephemeral ports, then use NDD to ensure that the kernel TCP/IP ephemeral port range is broad enough to provide enough ephemeral ports for the anticipated server workload.

Ensure that the lower range is set to at least 9000 or higher, to avoid Well Known ports, and to avoid ports in the Registered Ports range commonly used by Oracle and other server ports. Set the port range high enough to avoid reserved ports for any applications you may intend to use. If the lower value of the range you have is greater than 9000, and the range is large enough for your anticipated workload, then you can ignore OUI warnings regarding the ephemeral port range.

1.  Use the following commands to check your current range for ephemeral ports:
        # /usr/sbin/no -a | fgrep ephemeral
             tcp_ephemeral_low = 32768
             tcp_ephemeral_high = 65500
             udp_ephemeral_low = 32768
             udp_ephemeral_high = 65500

    In the preceding example, the TCP and UDP ephemeral ports are set to the default range (32768-65536).
2.  If you expect your workload to require a high number of ephemeral ports, such as high node counts or heavy use of Parallel Query, then update the UDP and TCP ephemeral port range to a broader range. For example:
        # /usr/sbin/no -p -o tcp_ephemeral_low=9000 -o tcp_ephemeral_high=65500
        # /usr/sbin/no -p -o udp_ephemeral_low=9000 -o udp_ephemeral_high=65500

**Parent topic:** [Completing Preinstallation Tasks Manually](completing-preinstallation-tasks-manually.md)
