#

The image shows two Azure regions on the left and two OCI regions on the right with the OCI Managed Network between them.

Inside the primary Azure region is the availability zone containing the ExaDB-D primary database, and inside the Standby Azure Region is the availability zone containing the ExaDB-D standby database. Each database is configured with its own VNet network, called VNet DB Primary and VNet DB Standby. An arrow depicts Data Guard redo transport going from the primary database to the standby database through the OCI Managed Network. There are several other components that are not pertinent to this document.

Inside the OCI regions are the OCI Managed Services: 2 instances of Object Storage, and OCI Vault. Each database in the Azure regions has an arrow going from it, through the OCI Managed Network, to one of the Object Storage icons, indicating that automatic backups are sent to separate Object Storage repositories. Each database also has an arrow going from the database to the Vault through the OCI Managed Network.
