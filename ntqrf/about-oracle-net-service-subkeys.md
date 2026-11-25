`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services` contains subkeys that correspond to services.

Depending on what is installed, your Oracle Net Services consist of all or a subset of the following:

- `Oracle``HOMENAME``ClientCache`` `

- `Oracle``HOMENAME``CMAdmin`` `

- `Oracle``HOMENAME``CMan`` `

- `Oracle``HOMENAME``TNSListener`` `

Each service subkey contains the parameters shown in Service Subkey Parameters.

Table B-1 Service Subkey Parameters

| Parameter     | Description                                                                                                                               |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| `DisplayName` | Specifies service name.                                                                                                                   |
| `ImagePath`   | Specifies fully qualified path name of the executable started by service and any command line arguments passed to executable at run time. |
| `ObjectName`  | Specifies logon user account and computer to which service must log on.                                                                   |

**Parent topic:** [About Modifying Oracle Net Services Registry Parameters and Subkeys](about-modifying-oracle-net-services-registry-parameters-and-subkeys.md)
