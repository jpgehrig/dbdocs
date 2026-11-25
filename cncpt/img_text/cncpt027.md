# Description of the illustration cncpt027.eps

This graphic depicts the relationship between a Tablespace, Segment, Datafiles, Extents, and Data Blocks.

The tablespace holds one Segment of 96 Kb. The segment is divided into one extent of 24 Kb and another of 72 Kb, each of which is in a separate datafile. The 72 Kb extent maps to 12 rows of 2 Kb blocks, with 3 2 Kb blocks in each row. The 24 Kb extent maps to 12 2 Kb blocks.
