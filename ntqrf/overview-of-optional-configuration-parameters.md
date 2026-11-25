You can use the Windows parameters listed here with Oracle Net Services.

Oracle Net Service first checks for the parameters as environment variables, and uses the values defined. If environment variables are not defined, then Oracle Net Services searches for these parameters in the registry.

- [About LOCAL Parameter](about-local-parameter.md)
  You can use the parameter `LOCAL` to connect to Oracle Database without specifying a connect identifier in the connect string.
- [About TNS_ADMIN Parameter](about-tns-admin-parameter.md)
  You can add the parameter `TNS_ADMIN` to change the directory path of Oracle Net Services configuration files from the default location of `ORACLE_HOME``\network\admin`.
- [About USE_SHARED_SOCKET Parameter](about-use-shared-socket-parameter.md)
  You can set the parameter `USE_SHARED_SOCKET` to `true` to enable the use of shared sockets.

**Parent topic:** [Oracle Net Services Configuration on Windows](net-services-configuration-on-windows.md)
