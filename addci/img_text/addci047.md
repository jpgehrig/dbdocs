The server tables are:

- Base Table T1, with 3 partitions:

  - Partition Name (PartName) P1 has Partition Number (PartNum) equal to 1

  - Partition Name (PartName) P2 has Partition Number (PartNum) equal to 2

  - Partition Name (PartName) P3 has Partition Number (PartNum) equal to 3

- Local Index IT1, with three partitions:

  - Partition Name (PartName) IP1 has Partition Number (PartNum) equal to 1

  - Partition Name (PartName) IP2 has Partition Number (PartNum) equal to 2

  - Partition Name (PartName) IP3 has Partition Number (PartNum) equal to 3

The index tables are:

- Metadata Table MT1, with 3 rows:

  - The row of Partition Name (PartName) IP1 has Partition ID (PartId) equal to 101 and Metadata equal to Params1

  - The row of Partition Name (PartName) IP2 has Partition ID (PartId) equal to 102 and Metadata equal to Params2

  - The row of Partition Name (PartName) IP3 has Partition ID (PartId) equal to 103 and Metadata equal to Params3

- System Partitioned Table SPT1, with 3 rows:

  - The row of Partition Name (PartName) IP1 has Partition Number (PartNum) equal to 1

  - The row of Partition Name (PartName) IP2 has Partition Number (PartNum) equal to 2

  - The row of Partition Name (PartName) IP3 has Partition Number (PartNum) equal to 3
