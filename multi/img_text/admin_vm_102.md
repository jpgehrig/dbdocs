This illustration shows a CDB resource plan in root and a PDB resource plan in the servicespdb PDB.

The CDB resource plan includes three directives, and each directive specifies a share, a utilization_limit, and a parallel_server_limit for a PDB. One directive specifies the following for the salespdb PDB:

- share = 3

- utilization_limit = 100

- parallel_server_limit = 100

- memory_limit = 100

A second directive specifies the following for the servicespdb PDB:

- share = 3

- utilization_limit = 100

- parallel_server_limit = 100

- memory_limit = 100

A third directive specifies the following for the hrpdb PDB:

- share = 1

- utilization_limit = 70

- parallel_server_limit = 70

- memory_limit = 70

The illustration shows the salespdb PDB, the servicespdb PDB, and the hrpdb PDB. It shows the PDB resource plan for the servicespdb PDB. This PDB resource plan includes three directives, and each directive specifies a CPU percentage for a consumer group. One directive specifies 75% of CPU for the "OLTP" consumer group, a second directive specifies 15% of CPU for the "REPORTING" consumer group, and a third directive specifies 10% of CPU for the "OTHER_GROUPS" consumer group.
