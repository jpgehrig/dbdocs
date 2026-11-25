This illustration shows a CDB resource plan in root. The plan includes three directives and one default directive, and each directive specifies a share, a utilization_limit, and a parallel_server_limit for a PDB. One directive specifies the following for the salespdb PDB:

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

The default directive specifies the following for any PDB with no directive:

- share = 1

- utilization_limit = 50

- parallel_server_limit = 50

- memory_limit = 50

The illustration shows the default directive applied to two PDBs with no directive, `marketingpdb` and `testingpdb`, and three dots indicate that the default directive applies to any number of PDBs with no directive.
