Use the `oclumon debug` command to set the log level for the Cluster Health Monitor services.

### Syntax

    oclumon debug [log daemon module:log_level] [version]

### Parameters

Table B-1 oclumon debug Command Parameters

| Parameter                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:----------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `log ``daemon`` ``module``:``log_level` | Use this option change the log level of daemons and daemon modules.<br>Supported daemons are:<br>• `osysmond`<br>• `ologgerd`<br>• `client`<br>• `all`<br>Supported daemon modules are:<br>• `osysmond`: `CRFMOND`, `CRFM`, and `allcomp`<br>• `ologgerd`: `CRFLOGD`, `CRFLDREP`, `CRFM`, and `allcomp`<br>• `client`: `OCLUMON`, `CRFM`, and `allcomp`<br>• `all`: `allcomp`<br>Supported `log_level` values are `0`, `1`, `2`, and `3`. |
| `version`                               | Use this option to display the versions of the daemons.                                                                                                                                                                                                                                                                                                                                                                                   |

Example B-1 oclumon debug

The following example sets the log level of the system monitor service (`osysmond`):

    $ oclumon debug log osysmond CRFMOND:3

The following example displays the versions of the daemons:

    $ oclumon debug version

    OCLUMON  version :0.02
    OSYSMOND  version :12.01
    OLOGGERD  version :2.01
    NODEVIEW version :12.01
    Clusterware version - label date:
            12.2.0.1.0 - 160825

**Parent topic:** [OCLUMON Command Reference](oclumon-command-reference.md)
