## Using Oracle RPM Checker on IBM: Linux on System z

Use the Oracle RPM Checker utility to verify that you have the required Red Hat Enterprise Linux or SUSE packages installed on the operating system before you start the Oracle Database or Oracle Grid Infrastructure installation.

1.  Download the Oracle RPM Checker utility for your IBM: Linux on System z distribution from the link in [My Oracle Support Note 2553465.1](https://support.oracle.com/rs?type=doc&id=2553465.1).
2.  Unzip the RPM, and install the RPM as `root`.
3.  Run the utility as `root` to check your operating system packages. For example:
    Download the Oracle RPM Checker utility for your IBM: Linux on System z distribution. Then,

    On Red Hat Enterprise Linux 9:

        # rpm -ivh ora-val-rpm-RH9-DB-19c-19.0.1-1.s390x.rpm

    On Red Hat Enterprise Linux 8:

        # rpm -ivh ora-val-rpm-RH8-DB-19c.s390x.rpm

    On Red Hat Enterprise Linux 7:

        # rpm -ivh ora-val-rpm-RH7-DB-19c.s390x.rpm

    On SUSE Linux Enterprise Server 12:

        # rpm -ivh ora-val-rpm-S12-DB-19c.s390x.rpm

    On SUSE Linux Enterprise Server 15:

        # rpm -ivh ora-val-rpm-S15-DB-19c.s390x.rpm

    On Red Hat Enterprise Linux, the utility checks and also installs all required RPMs. For example:

    On Red Hat Enterprise Linux 9:

        # yum install ora-val-rpm-RH9-DB-19c-19.0.1-1.s390x.rpm

    On Red Hat Enterprise Linux 8:

        # yum install ora-val-rpm-RH8-DB-19c.s390x.rpm

    On Red Hat Enterprise Linux 7:

        # yum install ora-val-rpm-RH7-DB-19c.s390x.rpm

To remove the Oracle RPM Checker utility:

On Red Hat Enterprise Linux 9:

    # rpm -e ora-val-rpm-RH9-DB-19c-19.0.1-1.s390x

On Red Hat Enterprise Linux 8:

    # rpm -e ora-val-rpm-RH8-DB-19c.s390x

On Red Hat Enterprise Linux 7:

    # rpm -e ora-val-rpm-RH7-DB-19c.s390x

On SUSE Linux Enterprise Server 12:

    # rpm -e ora-val-rpm-S12-DB-19c.s390x

On SUSE Linux Enterprise Server 15:

    # rpm -e ora-val-rpm-S15-DB-19c.s390x

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on Linux](configuring-operating-systems-for-oracle-grid-infrastructure-on-linux.md)
