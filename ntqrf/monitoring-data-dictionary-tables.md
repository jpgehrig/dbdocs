If you use Advanced Replication and intend to set up a large number of replicated objects, then you are required to monitor the following data dictionary tables with the `SQL SELECT` argument:

- `ARGUMENT$`

- `IDL_CHAR$`

- `IDL_UB1$`

- `IDL_UB2$`

- `IDL_SB4$`

- `I_ARGUMENT1`

- `I_SOURCE1I$`

- `SOURCE$`

- `TRIGGER`

If necessary, increase the storage parameters to accommodate storage requirements of large numbers of replicated objects.

**Parent topic:** [About Advanced Replication on Windows](about-advanced-replication-on-windows.md)
