#

The image shows the topology of the use case described above.

In the upper left is the source primary CDB (CDB100) containing 3 PDBs (PDB001, PDB002, PDB003).

The lower left shows the standby CDB for CDB100 (CDB100_STBY) containing 3 PDBs (PDB001, PDB002, PDB003).

An arrow from source primary CDB CDB100 pointing to its standby CDB100_STBY is labeled "Data Guard Redo Ship/Apply".

The upper right of the image shows the empty destination primary CDB (CDB200) containing no PDBs.

The lower right shows the empty standby CDB for CDB200 (CDB200_STBY) containing no PDBs.

An arrow from the destination primary CDB CDB200 pointing to its standby CDB200_STBY is labeled "Data Guard Redo Ship/Apply".

Between the source primary CDB (CDB100) and the destination primary CDB (CDB200) is shown an ASM disk group with solid lines to each primary CDB.

Between the source standby CDB (CDB100_STBY) and the destination standby CDB (CDB200_STBY) is shown an ASM disk group with solid lines to each standby CDB.
