## Fleet Patching and Provisioning Architecture

The Fleet Patching and Provisioning architecture consists of a Fleet Patching and Provisioning Server and any number of Fleet Patching and Provisioning Clients and targets.

Oracle recommends deploying the Fleet Patching and Provisioning Server in a multi-node cluster so that it is highly available. Oracle FPP Server supports single-node deployment, but it is not recommended.

**Note:**

You can not configure Oracle FPP Server on an Oracle Restart server.

The Fleet Patching and Provisioning Server cluster is a repository for all data, of which there are primarily three types:

- Gold images
- Working copies and clients
- Metadata related to users, roles, permissions, and identities

The Fleet Patching and Provisioning Server acts as a central server for provisioning Oracle Database homes, Oracle Grid Infrastructure homes, and other application software homes, making them available to the cluster hosting the Fleet Patching and Provisioning Server and to the Fleet Patching and Provisioning Client clusters, their targets, and non-client targets.

Users operate on the Fleet Patching and Provisioning Server or Fleet Patching and Provisioning Client to request deployment of Oracle homes or to query gold images. When a user makes a request for an Oracle home, specifying a gold image, the Fleet Patching and Provisioning Client communicates with the Fleet Patching and Provisioning Server to pass on the request. The Fleet Patching and Provisioning Server processes the request by taking appropriate action to instantiate a copy of the gold image, and to make it available to the Fleet Patching and Provisioning Client cluster using available technologies such as Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and local file systems.

- [Oracle Fleet Patching and Provisioning Server](oracle-fpp-server.md)
  The Oracle Fleet Patching and Provisioning Server (FPPS) is a highly available software provisioning system that uses Oracle Automatic Storage Management (Oracle ASM), Oracle Automatic Storage Management Cluster File System (Oracle ACFS), Grid Naming Service (GNS), and other components.
- [Targets of Oracle Fleet Patching and Provisioning](oracle-fpp-targets.md)
  Computers of which Oracle Fleet Patching and Provisioning (Oracle FPP) is aware are known as `rhpclient`-less targets, which do not have the `rhpclient` component enabled.
- [Oracle Fleet Patching and Provisioning Clients and Targets](oracle-fpp-client.md)
  The Oracle Fleet Patching and Provisioning (Oracle FPP) Client is part of Oracle Clusterware. Users operate on an Oracle FPP Client to perform tasks such as requesting deployment of Oracle homes and listing available gold images.
- [Images of Oracle Fleet Patching and Provisioning](oracle-fpp-images.md)
  You can easily copy an image of an Oracle home to a new host on a new file system to serve as an active usable Oracle home.
- [Working Copies of Oracle Fleet Patching and Provisioning](oracle-fpp-working-copies.md)
  Working copy is a copy of the gold image that you use to provision the software on an Oracle Fleet Patching and Provisioning (Oracle FPP) Client or an `rhpclient`-less target.

**Parent topic:** [Oracle Fleet Patching and Provisioning Overview](fleet-patching-provisioning.md)
