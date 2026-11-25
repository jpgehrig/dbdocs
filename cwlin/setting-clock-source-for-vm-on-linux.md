## Setting Clock Source for VMs on Linux x86-64

Oracle recommends that you set the clock source to `tsc` for better performance in virtual environments (VM) on Linux x86-64.

1.  As the `root` user, check if the `tsc` clock source is available on your system.
        # cat /sys/devices/system/clocksource/clocksource0/available_clocksource
        kvm-clock tsc acpi_pm
2.  If the `tsc` clock source is available, then set `tsc` as the current clock source.
        # echo "tsc">/sys/devices/system/clocksource/clocksource0/current_clocksource
3.  Verify that the current clock source is set to `tsc`.
        # cat /sys/devices/system/clocksource/clocksource0/current_clocksource
        tsc
4.  Using any text editor, append the `clocksource` directive to the `GRUB_CMDLINE_LINUX` line in the `/etc/default/grub` file to retain this clock source setting even after a reboot.
        GRUB_CMDLINE_LINUX="rd.lvm.lv=ol/root rd.lvm.lv=ol/swap rhgb quiet numa=off transparent_hugepage=never clocksource=tsc"
5.  Run the following command to update `GRUB` and ensure that these settings are retained even after a reboot:
        # grub2-mkconfig -o /boot/grub2/grub.cfg

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)
