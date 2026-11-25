View the current value specified for network tuning parameters, and change them if necessary.

1.  To check the current values of the network tuning parameters, enter commands similar to the following:
        # no -a | more
2.  If you must change the value of any parameter, then enter the following command to determine whether the system is running in compatibility mode:
        # lsattr -E -l sys0 -a pre520tune

    If the system is running in compatibility mode, then the output is similar to the following, showing that the value of the pre520tune attribute is enabled:

        pre520tune enable Pre-520 tuning compatibility mode True
3.  If the system is running in compatibility mode, then follow these steps to change the parameter values:
    1.  Enter commands similar to the following to change the value of each parameter:
            # no -o parameter_name=value

        For example:

            # no -o udp_recvspace=655360
    2.  Add entries similar to the following to the `/etc/rc.net` file for each parameter that you changed in the previous step:
            if [ -f /usr/sbin/no ] ; then
               /usr/sbin/no -o udp_sendspace=65536
               /usr/sbin/no -o udp_recvspace=655360
               /usr/sbin/no -o tcp_sendspace=65536
               /usr/sbin/no -o tcp_recvspace=65536
               /usr/sbin/no -o rfc1323=1
               /usr/sbin/no -o sb_max=4194304
               /usr/sbin/no -o ipqmaxlen=512
            fi

        By adding these lines to the `/etc/rc.net` file, the values persist when the system restarts.
    3.  You can also use the `chdev` command to change the characteristics of a device or interface. For example, set the RFC1323 value for the network interface `en5` without restarting the system as follows:
            chdev -l en5 -a rfc1323=1
4.  If the system is not running in compatibility mode, then enter commands similar to the following to change the parameter values:
    `ipqmaxlen` parameter:

        /usr/sbin/no -r -o ipqmaxlen=512

    Other parameter:

        /usr/sbin/no -p -o parameter=value

    If you modify the `ipqmaxlen` parameter, then you must restart the system. These commands modify the `/etc/tunables/nextboot` file, causing the attribute values to persist when the system restarts.
5.  If you need to change parameters, and you do not restart your system, then use the `ifconfig` command to check each network parameter after you change the no global setting.
    For example:

        # ifconfig en0
        en0:
        flags=1e080863,2c0<UP,BROADCAST,NOTRAILERS,RUNNING,SIMPLEX,MULTICAST,GROUPRT,6
        4BIT,CHECKSUM_OFFLOAD(ACTIVE),LARGESEND,CHAIN,MONITOR>
        inet 192.0.2.1 netmask 0xfffff800 broadcast 192.0.2.0
                inet 192.0.2.2 netmask 0xfffff800 broadcast 192.0.2.0
                inet 192.0.2.3 netmask 0xfffff800 broadcast 192.0.2.0
                inet 192.0.2.4 netmask 0xfffff800 broadcast 192.0.2.0
                 tcp_sendspace 131072 tcp_recvspace 65536 rfc1323 0

    For the ISNO parameter `tcp_sendspace`, use the following command to set it:

        # ifconfig en0 tcp_sendspace 65536

**Related Topics**

- [Recommended Values for Network Tuning Parameters](recommended-values-for-network-tuning-parameters.md)

**Parent topic:** [Tuning AIX System Environment](tuning-aix-system-environment.md)
