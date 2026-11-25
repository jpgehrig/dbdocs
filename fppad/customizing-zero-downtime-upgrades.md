## Customizing Zero-Downtime Upgrades

You can customize zero-downtime upgrades using the user-action framework of Fleet Patching and Provisioning.

To use the user-action framework, you can provide a separate script for any or all of the points listed in the overall process.

Table 5-1 Zero-Downtime Upgrade Plugins

| Plugin Type                      | Pre or Post                                                                                                   | Plugin runs...                                                       |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------|
| `ZDTUPGRADE_DATABASE`            | Pre                                                                                                           | Before Fleet Patching and Provisioning starts zero-downtime upgrade. |
| Post                             | After Fleet Patching and Provisioning completes zero-downtime upgrade.                                        |                                                                      |
| `ZDTUPGRADE_DATABASE_SNAPDB`     | Pre                                                                                                           | Before creating the snapshot or full-clone database.                 |
| Post                             | After starting the snapshot or full-clone database (but before switching over).                               |                                                                      |
| `ZDTUPGRADE_DATABASE_DBUA`       | Pre                                                                                                           | Before running DBUA (after switching over).                          |
| Post                             | After DBUA completes.                                                                                         |                                                                      |
| `ZDTUPGRADE_DATABASE_SWITCHBACK` | Pre                                                                                                           | Before switching back users to the upgraded source database.         |
| Post                             | After switching back users to the upgraded source database (before deleting snapshot or full-clone database). |                                                                      |

- To register a plugin to be run during a zero-downtime upgrade, run the following command:
      $ rhpctl add useraction -useraction user_action_name -actionscript script_name
        {-pre | -post} -optype {ZDTUPGRADE_DATABASE | ZDTUPGRADE_DATABASE_SNAPDB |
         ZDTUPGRADE_DATABASE_DBUA | ZDTUPGRADE_DATABASE_SWITCHBACK}

  You can specify run-time input to the plugins using the `-useractiondata` option of the `rhpctl zdtupgrade database` command.

**Parent topic:** [Zero-Downtime Upgrade](zero-downtime-upgrade.md)
