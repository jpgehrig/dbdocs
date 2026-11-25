If you do not use a Fixup script or CVU to set ephemeral ports, then set TCP/IP ephemeral port range parameters to provide enough ephemeral ports for the anticipated server workload.

Ensure that the lower range is set to at least 9000 or higher, to avoid Well Known ports, and to avoid ports in the Registered Ports range commonly used by Oracle and other server ports. Set the port range high enough to avoid reserved ports for any applications you may intend to use. If the lower value of the range you have is greater than 9000, and the range is large enough for your anticipated workload, then you can ignore Oracle Universal Installer warnings regarding the ephemeral port range.

On Oracle Solaris 11, use the `ipadm` command to check your current range for ephemeral ports:

    # ipadm show-prop -p smallest_anon_port,largest_anon_port tcp

    PROTO PROPERTY           PERM CURRENT PERSISTENT DEFAULT POSSIBLE
    tcp   smallest_anon_port rw   32768       --     32768   1024-65535
    tcp   largest_anon_port  rw   65500       --     65535   32768-65535

In the preceding examples, the ephemeral ports are set to the default range (32768-65535).

If necessary for your anticipated workload or number of servers , update the UDP and TCP ephemeral port range to a broader range. For example:

On Oracle Solaris 11:

    # ipadm set-prop -p smallest_anon_port=9000 tcp
    # ipadm set-prop -p largest_anon_port=65500 tcp
    # ipadm set-prop -p smallest_anon_port=9000 udp
    # ipadm set-prop -p largest_anon_port=65500 udp

Oracle recommends that you make these settings permanent. Refer to your system administration documentation for information about how to automate this ephemeral port range alteration on system restarts.

**Parent topic:** [Configuring Kernel Parameters on Oracle Solaris](configuring-kernel-parameters-on-oracle-solaris.md)
