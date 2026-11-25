Check your software to see if they meet the minimum version, compiler, and patch requirements for installation.

1.  To determine the distribution and version of HP-UX installed:
        # uname -a

        HP-UX hostname B.11.31 U ia64 4156074294 unlimited-user license

    In this example, the version of HP-UX is 11.31 and the processor is Itanium.
2.   To determine the compiler installed:
        # /usr/sbin/swlist -l product | grep -i compiler
3.  To determine if a patch is installed:
        # /usr/sbin/swlist -l patch | grep PHSS_42686

    Alternatively, to list all installed patches:

        # /usr/sbin/swlist -l patch | more

    If a required patch is not installed, then download it from the HP Support Center website and install it:
    <https://www.support.hp.com/>

    If the website has a recent version of the patch, then download and install that version.
4.  To verify if the system meets the minimum patch bundle requirements:
        # /usr/sbin/swlist -l bundle |grep QPK

    The QPK (Quality Pack) bundles have version numbers of the form `B.11.31.0809.326a` (for the September 2008 release), `B.11.31.0903.334a` (for the March 2009 release), and so on.

    If a required bundle, product, or fileset is not installed, then install it. See your operating system or software documentation for information about installing products.

    **Note:**

    There may be more recent versions of the patches listed in the preceding paragraph that are installed on the system. If a listed patch is not installed, then determine if a more recent version is installed before installing the version listed.
5.  If you require a CSD for WebSphere MQ, then refer to the following website for download and installation information:
    <https://www.ibm.com/support/>

**Parent topic:** [Configuring Operating Systems for Oracle Database on HP-UX Itanium](configuring-operating-systems-for-oracle-database-on-hp-ux-itanium.md)
