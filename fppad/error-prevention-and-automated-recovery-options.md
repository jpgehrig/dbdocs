## Error Prevention and Automated Recovery Options

Fleet Patching and Provisioning has error prevention and automated recovery options to assist you during maintenance operations.

During maintenance operations, errors must be avoided whenever possible and, when they occur, you must have automated recovery paths to avoid service disruption.

### Error Prevention

Many RHPCTL commands include the `-eval` parameter, which you can use to run the command and evaluate the current configuration without making any changes to determine if the command can be successfully run and how running the command will impact the configuration. Commands that you run using the `-eval` parameter run as many prerequisite checks as possible without changing the configuration. If errors are encountered, then RHPCTL reports them in the command output. After you correct any errors, you can run the command again using `-eval` to validate the corrections. Running the command successfully using `–eval` provides a high degree of confidence that running the actual command will succeed.

You can test commands with the `-eval` parameter outside of any maintenance window, so the full window is available for the maintenance procedure, itself.

### Automated Recovery Options

During maintenance operations, errors can occur either in-flight (for example, partway through either an `rhpctl move database` or `rhpctl move gihome` command) or after a successful operation (for example, after an `rhpctl move database` command, you encounter performance or behavior issues).

In-Flight Errors

Should in-flight errors occur during move operations:

- Correct any errors that RHPCTL reports and rerun the command, which will resume running at the point of failure.

  If rerunning the command succeeds and the move operation has a post-operation user action associated with it, then the user action is run. If there is a pre-operation user action, however, then RHPCTL does not rerun the command.

- Run a new move command, specifying only the destination from the failed move (working copy or unmanaged home), an authentication option, if required, and use the `-revert` parameter. This will restore the configuration to its initial state.

  No user actions associated with the operation are run.

- Run a new move command, specifying only the destination from the failed move (working copy or unmanaged home), an authentication option if required, and the `-abort` parameter. This leaves the configuration in its current state. Manual intervention is required at this point to place the configuration in a final state.

  No user actions associated with the operation are run.

Post-Update Issues

Even after a successful move operation to a new database or Oracle Grid Infrastructure home, you still may need to undo the change and roll back to the prior home. You can do this by rerunning the command with the source and destination homes reversed. This is, effectively, a fresh move operation performed without reference to the previous move operation.

**Note:**

For the independent automatons, the source and destination homes are always unmanaged homes (those homes not provisioned by Fleet Patching and Provisioning). When the move operation is run on a Fleet Patching and Provisioning Server or Fleet Patching and Provisioning Client, the destination home must be a managed home that was provisioned by Fleet Patching and Provisioning.

**Parent topic:** [Fleet Patching and Provisioning Postinstallation Tasks](oracle-fpp-postinstallation-tasks.md)
