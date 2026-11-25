## About Oracle Fleet Patching and Provisioning Local Mode

Oracle Fleet Patching and Provisioning Server is configured in the local mode by default when you install Oracle Grid Infrastructure.

The local-mode operation enables you to perform Oracle Grid Infrastructure and Oracle Database patching operations on the local cluster. Deploy either the Oracle Grid Infrastructure or the Oracle Database patched home and run the patch operation using either the `rhpctl move gihome` or `rhpctl move database` command, specifying the source and destination paths instead of working copy names.

The Oracle FPP Local Mode supports Oracle Database 11g (11.2.0.4), 12c (12.1.0.2), 12c (12.2.0.1), or later in a clustered environment. In a standalone (non-clustered) environment, you can patch only the database home and the database home must be Oracle Database 18c or later.

The Oracle FPP Local Mode runs locally on the deployment and does not require an Oracle Fleet Patching and Provisioning Server in the architecture. (If there is an Oracle Fleet Patching and Provisioning Server in the architecture, then the Oracle FPP Local Mode does not communicate with it, and the Fleet Patching and Provisioning Server cannot interact with Oracle FPP Local Mode.)

**Parent topic:** [Oracle Fleet Patching and Provisioning Local Mode](oracle-fpp-local-mode.md)
