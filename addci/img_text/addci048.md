The server tables are:

- Base Table T1, with 4 partitions:

  - Partition Name (PartName) P1 has Partition Number (PartNum) equal to 1

  - Partition Name (PartName) P21 has Partition Number (PartNum) equal to 2

  - Partition Name (PartName) P22 has Partition Number (PartNum) equal to 3

  - Partition Name (PartName) P3 has Partition Number (PartNum) equal to 4

- Local Index IT1, with 4 partitions:

  - Partition Name (PartName) IP1 has Partition Number (PartNum) equal to 1

  - Partition Name (PartName) IP21 has Partition Number (PartNum) equal to 2

  - Partition Name (PartName) IP22 has Partition Number (PartNum) equal to 3

  - Partition Name (PartName) IP3 has Partition Number (PartNum) equal to 4

The index tables are:

- Metadata Table MT1, with 4 rows:

  - The row of Partition Name (PartName) IP1 has Partition ID (PartId) equal to 101 and Metadata equal to Params1

  - The row of Partition Name (PartName) IP21 has Partition ID (PartId) equal to 1021 and Metadata equal to Params2

  - The row of Partition Name (PartName) IP22 has Partition ID (PartId) equal to 1022 and Metadata equal to Param2

  - The row of Partition Name (PartName) IP3 has Partition ID (PartId) equal to 103 and Metadata equal to Params3

- System Partitioned Table SPT1, with 4 rows:

  - Partition Name (PartName) IP1 has Partition Number (PartNum) equal to 1

  - Partition Name (PartName) IP21 has Partition Number (PartNum) equal to 2

  - Partition Name (PartName) IP22 has Partition Number (PartNum) equal to 3

  - Partition Name (PartName) IP3 has Partition Number (PartNum) equal to 4
