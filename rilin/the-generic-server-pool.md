## The Generic Server Pool

The Generic server pool stores any Oracle Database that is not policy managed.

Additionally, the Generic server pool contains servers with names you specified in the `SERVER_NAMES` attribute of the server pools that list the Generic server pool as a parent server pool.

The Generic server pool's attributes are restricted, as follows:

- No one can modify configuration attributes of the Generic server pool (all attributes are read-only)

- When DBCA or SRVCTL specifies a server name in the `HOSTING_MEMBERS` resource attribute, Oracle Clusterware only allows it if the server is:

  - Online and exists in the Generic server pool

  - Online and exists in the Free server pool, in which case Oracle Clusterware moves the server into the Generic server pool

  - Online and exists in any other server pool and the user is either a cluster administrator or is allowed to use the server pool's servers, in which case, the server is moved into the Generic server pool

  - Offline and the user is a cluster administrator

**Parent topic:** [About Server Pools](about-server-pools.md)
