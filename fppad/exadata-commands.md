## exadata Commands

Use commands with the `exadata` keyword to patch an Oracle Exadata system.

- rhpctl update exadata
  Patches an Oracle Exadata system.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl update exadata

Patches an Oracle Exadata system.

#### Syntax

    rhpctl update exadata {-dbnodes comma_separates_list_of_nodes [-patchmgrloc patch_mgr_loc] [-iso_repo iso_repo_name]
    [-backup] [-batches list_of_batches | -continue | -abort] | -cells [-list_of_cell_nodes] | -ibswitches [-list_of_ibswitch_nodes]
    [-downgrade]} [-image exadata_image_name] [-fromnode node_name] [-patchmgargs "-patch_mgr_args"] [-client client_name]
    [-rollback] [-smtpfrom "email_address"] [-smtpto "email_address"] [-schedule {timer_value | NOW }] [-eval]

#### Parameters

Table A-20 rhpctl update exadata Command Parameters

| Parameter                        | Description                                                                                                                                                                                                                                                      |
|:---------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-dbnodes`                       | Specifies to patch Exadata database nodes.                                                                                                                                                                                                                       |
| `-patchmgrloc ``patch_mgr_loc`   | Specifies the patch manager location.                                                                                                                                                                                                                            |
| `-iso_repo ``iso_image_name`     | Specifies the ISO image name.                                                                                                                                                                                                                                    |
| `-backup`                        | Performs backup of the Exadata database server.                                                                                                                                                                                                                  |
| `-batches ``list_of_batches`     | Optionally, you can specify a comma-delimited list of batches of nodes where each batch is a comma-delimited list of node names enclosed in parentheses and node names are enclosed in double quotation marks (`""`) in the format: `"(nA,nB,...),(...,nY,nZ)"`. |
| `-continue`                      | Update Oracle Exadata on the next batch of nodes.                                                                                                                                                                                                                |
| `-abort`                         | Stop the ongoing update operation.                                                                                                                                                                                                                               |
| `-cells`                         | Comma separated list of storage server nodes.                                                                                                                                                                                                                    |
| `-ibswitches`                    | Specifies to patch the InfiniBand Network Fabric switches.                                                                                                                                                                                                       |
| `-ibnodes `                      | List of IB switch nodes in the format `Ba,...,Bz`                                                                                                                                                                                                                |
| `-downgrade`                     | Specify this option to downgrade the InfiniBand Network Fabric switches.                                                                                                                                                                                         |
| `-image`                         | Specify the name of an Oracle Exadata image.<br>This image should have already been deployed to all the database nodes of the target machine.                                                                                                                    |
| `-fromnode`                      | Specify the name of the source node.                                                                                                                                                                                                                             |
| `-patchmgargs`                   | Optionally specify the patch manager arguments in double quoted string.                                                                                                                                                                                          |
| `-client ``client_name`          | Specify the name of the cluster in which you want to update database nodes.                                                                                                                                                                                      |
| `-rollback`                      | Specify this option to roll back the patch.                                                                                                                                                                                                                      |
| `-smtpfrom`                      | The email address from which you want to send patch manager notifications.                                                                                                                                                                                       |
| `-smtpto`                        | The email address to which you want to send patch manager notifications.                                                                                                                                                                                         |
| `-schedule {timer_value | NOW }` | Optionally, you can use this parameter to schedule a time to run this operation, in ISO-8601 format, as in the following example:<br>`2020-07-25T19:13:17+05`<br>If `NOW` is specified or the option is omitted, then the job is scheduled immediately           |
| `-eval`                          | Evaluate the command without actually running the command.                                                                                                                                                                                                       |

#### Usage Notes

Use the `rhpctl update exadata` command to perform only database node patching.

#### Example

The following example performs database node patching on a client cluster.

    $ rhpctl update exadata image -image EXADATAIMAGEV1
         -iso_repo p28802055_192000_Linux-x86-64.zip -patchmgrloc /patchMgr/dbserver_patch_19.190306
         -patchmgrargs "-ignore_alerts" -client CLIENT1 -batches "(rac07box1)"

**See Also:**

[Combined Oracle Exadata Database Server and Grid Infrastructure Update](combined-exadata-database-node-and-grid-patching.md) for information about Oracle Exadata database node patching

**Parent topic:** exadata Commands
