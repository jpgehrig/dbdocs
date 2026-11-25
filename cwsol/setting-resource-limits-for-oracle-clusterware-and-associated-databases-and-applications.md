After you have completed Oracle Grid Infrastructure installation, you can set resource limits in the `Grid_home``/crs/install/s_crsconfig_``nodename``_env.txt` file.

The resource limits apply to all Oracle Clusterware processes and Oracle databases managed by Oracle Clusterware. For example, to set a higher number of processes limit, edit the file and set the `CRS_LIMIT_NPROC` parameter to a high value.

    ---
    #Do not modify this file except as documented above or under the
    #direction of Oracle Support Services.
    #########################################################################
    TZ=PST8PDT
    NLS_LANG=AMERICAN_AMERICA.WE8ISO8859P1
    CRS_LIMIT_STACK=2048
    CRS_LIMIT_OPENFILE=65536
    CRS_LIMIT_NPROC=65536
    TNS_ADMIN=

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
