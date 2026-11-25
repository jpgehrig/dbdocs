`HKEY_LOCAL_MACHINE\SYSTEM\CURRENTCONTROLSET\SERVICES` subkey contains additional subkeys that correspond to each Oracle Database service.

Each service subkey contains the following parameters:

- `DisplayName` specifies the service name of the instance whose `SID` is `SID`. The default value is the name of the service. For example, `OracleServiceORCL1`, where `ORCL1` is the `SID`.

- `ImagePath` specifies the fully qualified path name of the executable started by the service and any command-line arguments passed into the executable at run time. The default value is the path to the executable file of the product.

- `ObjectName` specifies the logon user account and computer to which the service must log on. The default value is `LocalSystem`.

**Parent topic:** [About HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services](about-hkey-local-machine-system-currentcontrolset.services.md)
