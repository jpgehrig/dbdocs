Set control and limit resources for users on the system to prevent denial of service attacks.

On AIX platforms, the `/etc/security/login.cfg` file controls and limits resources for users on the system. On login, set control and limit resources for users on the system so that authentication is carried out through the `pam.conf` file. By default, resource limits are set to `std_auth` for AIX operating systems.

1.  Edit the file `/etc/security/login.cfg` file to change `auth_type` under the `usw` stanza from `std_auth` to `pam_auth`.
2.  To ensure that these resource limits are honored, confirm that the line login session required `/usr/lib/security/pam_aix` is set in `/etc/pam.conf`.
    For example:

        dtsession auth  required        /usr/lib/security/pam_aix
        dtlogin session required        /usr/lib/security/pam_aix
        ftp     session required        /usr/lib/security/pam_aix
        imap    session required        /usr/lib/security/pam_aix
        login   session required        /usr/lib/security/pam_aix
        rexec   session required        /usr/lib/security/pam_aix
        rlogin  session required        /usr/lib/security/pam_aix
        rsh     session required        /usr/lib/security/pam_aix
        snapp   session required        /usr/lib/security/pam_aix
        su      session required        /usr/lib/security/pam_aix
        swrole  session required        /usr/lib/security/pam_aix
        telnet  session required        /usr/lib/security/pam_aix
        xdm     session required        /usr/lib/security/pam_aix
        OTHER   session required        /usr/lib/security/pam_prohibit
        websm_rlogin    session    required     /usr/lib/security/pam_aix
        websm_su        session    required     /usr/lib/security/pam_aix
        wbem       session       required    /usr/lib/security/pam_aix

**Parent topic:** [Configuring Operating Systems for Oracle Grid Infrastructure on IBM AIX on POWER Systems (64–Bit)](configuring-operating-systems-for-oracle-grid-infrastructure-on-ibm-aix-on-power-systems.md)
