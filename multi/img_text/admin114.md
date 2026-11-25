This illustration shows a CDB with the following components:

- The CDB has a `CDB$ROOT` container.

- A `PDB$SEED` container is plugged into the root container.

- Several PDBs are plugged into the root container.

- An application container is plugged into the root container.

- The application container has an application root container.

- The application container has an application seed plugged into it.

- The application container has two application PDBs plugged into its application root container.

The illustration shows the application seed files associated with the application seed container. The illustration shows the application seed's files copied to a new location. The copied files are the files of the new application PDB. The illustration shows the copied files associated with the new application PDB. A `CREATE` `PLUGGABLE` `DATABASE` statement uses these copied files to create the new application PDB.
