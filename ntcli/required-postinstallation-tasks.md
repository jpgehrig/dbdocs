## Required Postinstallation Tasks

Download and apply required patches for your software release after completing your initial installation.

- [Downloading and Installing Release Update Patches](downloading-and-installing-patch-updates.md)
  Download and install Release Updates (RU) and Release Update Revisions (RUR) patches for your Oracle software after you complete installation.
- [Windows Authentication No Longer Uses NTLM by Default](windows-authentication-ntlm.md)
  For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.
- [Updating Instant Client](updating-instant-client.md)
  Review this procedure to update Instant Client.
- [Configuring Oracle Net Services](required-product-specific-postinstallation-task.md)
  You can configure Oracle Database Client to communicate with Oracle Net Services by adding the appropriate entries to the tnsnames.ora and listener.ora files.

**Parent topic:** [Oracle Database Client Postinstallation Tasks](oracle-database-client-postinstallation-tasks.md)
