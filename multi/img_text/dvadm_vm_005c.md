Graphic dvadm_vm_005c.png shows from top to bottom, left to right, the following components:

- The root administrator for a CDB that contains three PDBs. PDB1 has the HR realm; PDB2 has the FIN realm, and PDB3. PDB3 is not Database Vault-enabled and has a CRM. The root administrator has access to the CRM in PDB3 but not to the realms in the PDB1 and PDB2

- To the left, the local administrator for the two Database Vault-enabled PDBs does not have access to the HR and FIN realms.

- To the right, the local adminstrator for the PDB that is not Database Vault-enabled has access to the Custom App application in PDB3.
