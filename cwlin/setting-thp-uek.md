## Setting and Disabling Transparent HugePages on UEK Kernels

Learn when to set Transparent HugePages and when to disable Transparent HugePages depending on your UEK kernel version.

- Setting Transparent HugePages to madvise
  Transparent HugePages memory is enabled by default with Oracle Linux. However, for optimal performance, Oracle recommends that you set Transparent HugePages to `madvise` on all Oracle Database servers running UEK7 and later kernels before you start the installation.
- Disabling Transparent HugePages
  On Oracle Database servers running UEK release earlier than UEK7, Oracle recommends that you disable Transparent HugePages before you start installation.

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)

### Setting Transparent HugePages to madvise

Transparent HugePages memory is enabled by default with Oracle Linux. However, for optimal performance, Oracle recommends that you set Transparent HugePages to `madvise` on all Oracle Database servers running UEK7 and later kernels before you start the installation.

On Oracle Database servers running UEK release earlier than UEK7, Oracle recommends that you disable Transparent HugePages before you start the installation. See Disabling Transparent HugePages. Later on, if the UEK version is upgraded to UEK7 or later, apply the steps in this topic.

If you install Oracle Database Preinstallation RPM, then it sets Transparent HugePages to `madvise` on all Oracle Database servers running UEK7 and later kernels.

To set `madvise` on Transparent HugePages:

1.  For Oracle Linux and Red Hat Enterprise Linux, add or modify the transparent_hugepage=madvise parameter in the `/etc/default/grub` file. For example:
        GRUB_TIMEOUT=5
        GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
        GRUB_DEFAULT=saved
        GRUB_DISABLE_SUBMENU=true
        GRUB_TERMINAL_OUTPUT="console"
        GRUB_CMDLINE_LINUX="crashkernel=auto rhgb quiet transparent_hugepage=madvise"
        GRUB_DISABLE_RECOVERY="true"

    **Note:**

    The file name may vary depending on your operating system and hardware. For example, on Oracle Cloud Infrastructure (OCI) the `grub.cfg` file is located at `/boot/efi/EFI/redhat/`. Check your operating system documentation for the exact file name.
2.  Run the `grub2–mkconfig` command to regenerate the `grub.cfg` file.
    On Oracle Linux 8

        # grub2-mkconfig -o /boot/grub2/grub.cfg

    On Oracle Linux 9

        grub2-mkconfig -o /boot/grub2/grub.cfg --update-bls-cmdline
3.  Restart the system to make the changes permanent. If you do not want to restart your system, then enter the following command:
        # echo madvise >
              /sys/kernel/mm/transparent_hugepage/enabled
4.  To check if Transparent HugePages is enabled and configured with `madvise`, run one of the following commands as the `root` user:
    Oracle Linux kernels:

        # cat /sys/kernel/mm/transparent_hugepage/enabled

    Red Hat Enterprise Linux kernels:

        # cat /sys/kernel/mm/redhat_transparent_hugepage/enabled

    The following is a sample output that shows Transparent HugePages is being used and set to `madvise`.

        always [madvise] never

**Parent topic:** Setting and Disabling Transparent HugePages on UEK Kernels

### Disabling Transparent HugePages

On Oracle Database servers running UEK release earlier than UEK7, Oracle recommends that you disable Transparent HugePages before you start installation.

Transparent HugePages memory differs from standard HugePages memory because the kernel `khugepaged` thread allocates memory dynamically during runtime. Standard HugePages memory is pre-allocated at startup, and does not change during runtime.

**Note:**

Although Transparent HugePages is disabled on UEK2 and later UEK kernels, Transparent HugePages may be enabled by default on your Linux system.

Transparent HugePages memory is enabled by default with Oracle Linux 6 and later, Red Hat Enterprise Linux 6 and later, SUSE 11 and later, kernels.

Transparent HugePages can cause memory allocation delays during runtime. To avoid performance issues, Oracle recommends that you disable Transparent HugePages on all Oracle Database servers. Oracle recommends that you instead use standard HugePages for enhanced performance.

To check if Transparent HugePages is enabled, run one of the following commands as the `root` user:

Red Hat Enterprise Linux kernels:

    # cat /sys/kernel/mm/redhat_transparent_hugepage/enabled

Other kernels:

    # cat /sys/kernel/mm/transparent_hugepage/enabled

The following is a sample output that shows Transparent HugePages are being used as the \[always\] flag is enabled.

    [always] never

**Note:**

If Transparent HugePages is removed from the kernel, then neither `/sys/kernel/mm/transparent_hugepage` nor `/sys/kernel/mm/redhat_transparent_hugepage files` exist.

To disable Transparent HugePages:

1.  For Oracle Linux 7, Oracle Linux 8, Red Hat Enterprise Linux 7, and Red Hat Enterprise Linux 8, add or modify the transparent_hugepage=never parameter in the `/etc/default/grub` file:

        transparent_hugepage=never

    For example:
        GRUB_TIMEOUT=5
        GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
        GRUB_DEFAULT=saved
        GRUB_DISABLE_SUBMENU=true
        GRUB_TERMINAL_OUTPUT="console"
        GRUB_CMDLINE_LINUX="crashkernel=auto rhgb quiet transparent_hugepage=never"
        GRUB_DISABLE_RECOVERY="true"

    **Note:**

    The file name may vary for your operating systems. Check your operating system documentation for the exact file name and the steps to disable Transparent HugePages.

2.  Run the `grub2–mkconfig `command to regenerate the `grub.cfg` file.

        # grub2-mkconfig -o /boot/grub2/grub.cfg

3.  Restart the system to make the changes permanent.

**Parent topic:** Setting and Disabling Transparent HugePages on UEK Kernels
