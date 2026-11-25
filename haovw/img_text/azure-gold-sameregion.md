#

The image shows The Azure region on the left and the OCI region on the right with the OCI Managed Network between them.

Inside the Azure region are the ExaDB-D primary database in Availability Zone 1, and the ExaDB-D standby database in Availability Zone 2. Each database is configured with its own VNet network, called VNet DB Primary and VNet DB Standby. An arrow depicts Data Guard redo transport going from the primary database to the standby database through the OCI Managed Network. There are several other components that are not pertinent to this document.

Inside the OCI region are the OCI Managed Services: 2 instances of Object Storage, and OCI Vault. Each database in the Azure region has an arrow going from it, through the OCI Managed Network, to one of the Object Storage icons, indicating that automatic backups are sent to separate Object Storage repositories. Each database also has an arrow going from the database to the Vault through the OCI Managed Network.
