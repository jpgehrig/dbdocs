The Row Source Execution table function:

- "ODCITableStart" begins the process

- "ODCITableFetch" is called; result is examined:

  - If the result is null, call "ODCITableClose"

  - If the result is not null, process the result and call "ODCITableFetch" again
