Learn how to manipulate family settings to initializing parameters.

To use ORADIM to add family support to the initialization parameters, enter:

    oradim     -FAMILY -set|-delete value [-SID sid | -ASMSID sid |  -MGMTDBSID sid | -IOSSID sid | -APXSID sid ]

For this command, note the following:

- `-FAMILY`: Indicates that you are manipulating family settings. This is a mandatory parameter.

- `-set | -delete value`: Should be used to set/delete value `<HKLM>/Software/Oracle/<Current_ORACLE_HOME>/ORACLE_FAMILY`. Set creates the above registry key and sets its value with the one specified. If the key exists already, then its value is updated. Delete removes the entry.

- `[-SID ``sid`` | -ASMSID ``sid`` | -MGMTDBSID ``sid ``| -IOSSID ``sid`` | -APXSID ``sid`` ]`: If one of these is specified, then the registry entry set/delete is `<HKLM>/Software/Oracle/<Current_ORACLE_HOME>/ORACLE_<sid>_FAMILY`. This is optional.

To make `inst1 `as part of the family `prod` for example, enter:

`c:\>oradim -FAMILY -set prod -SID inst1`

This creates the registry entry `<HKLM>/Software/Oracle/<Current_ORACLE_HOME>/ORACLE_inst1_FAMILY = prod`.

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
