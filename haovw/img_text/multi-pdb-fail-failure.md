#

The image shows the topology when PDB002 fails.

In the upper left is the source primary CDB (CDB100) containing 3 PDBs (PDB001, PDB002, PDB003).

PDB002 has an X over it indicating that this primary instance failed.

The lower left shows the standby CDB for CDB100 (CDB100_STBY) containing 3 PDBs (PDB001, PDB002, PDB003).

An arrow from source primary CDB CDB100 pointing to its standby CDB100_STBY is labeled "Data Guard Redo Ship/Apply".

The lower right of the image shows the empty destination CDB (CDB200) containing no PDBs.

Between the source standby CDB (CDB100_STBY) and the destination CDB (CDB200) is shown an ASM disk group with solid lines to each CDB.
