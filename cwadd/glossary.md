### action script

A script that defines the start, stop and check actions for a resource. The start action is invoked while starting the resource, the stop action for stopping the resource, and the check action while checking the running status of a resource.

### administrator managed

Database administrators define on which servers a database resource should run, and place resources manually as needed. This is the management strategy used in previous releases.

### agent

A program that contains the agent framework and user code to manage resources.

### agent framework

A C library that enables users to plug in application-specific code to manage customized applications.

### availability directive

Instructions to Oracle Clusterware to reconfigure the system when a server leaves or joins a cluster.

### cardinality

The number of servers on which a resource can run, simultaneously.

### client cluster

In a multicluster environment, a client cluster advertises its names with the server cluster.

### cluster

Multiple interconnected computers or servers that appear as if they are one server to end users and applications.

### cluster-aware

Any application designed to be deployed using clusterware.

### cluster administrator

An administrator who can manage a certain part of a cluster based on set policies and privileges.

### cluster configuration policy

A document for policy-managed clusters, which contains exactly one definition for each server pool defined in the system.

### cluster configuration policy set

A document that defines the names of all server pools configured in the cluster, which contains one or more configuration policies. Only one policy can be in effect at any one time, but administrators can set different policies to be in effect at different dates or times of the day in accordance with business needs and system demands.

### Cluster Health Monitor

Detects and analyzes operating system and cluster resource-related degradation and failures.

### cluster resource

A resource that is aware of the cluster environment and subject to cross-node switchover and failover.

### Cluster Time Synchronization Service

A time synchronization mechanism that ensures that all internal clocks of all nodes in a cluster are synchronized.

### Cluster Verification Utility (CVU)

A tool that verifies a wide range of Oracle RAC components such as shared storage devices, networking configurations, system requirements, Oracle Clusterware, groups, and users.

### database cloud

A set of databases integrated by the global service and load management framework into a single virtual server that offers one or more global services, while ensuring high performance, availability, and optimal utilization of resources.

### dependency

The relationship between two or more resources. and the interaction expressed between them.

### disk group

An Oracle ASM disk group is a collection of disks that Oracle ASM manages as a unit. Within a disk group, Oracle ASM exposes a file system interface for Oracle Database files. The content of files that is stored in a disk group is evenly distributed, or striped, to eliminate hot spots and to provide uniform performance across the disks. Oracle ASM files may also be optionally mirrored within a disk group. The performance of disks in a disk group is comparable to the performance of raw devices.

### Dynamic Host Configuration Protocol (DHCP)

A network application protocol used by devices (DHCP clients) to obtain configuration information for operation in an Internet Protocol network. This protocol reduces system administration workload, allowing devices to be added to the network with little or no manual intervention.

### fixup script

Oracle Universal Installer detects when minimum requirements for installation are not completed, and creates shell script programs, called fixup scripts, to resolve many incomplete system configuration requirements. If Oracle Universal Installer detects an incomplete task, it prompts you to create a fixup script and then to run the fixup script in a separate terminal session. You can also generate fixup scripts with certain CVU commands by using the `-fixup` flag.

### gold image

A copy of a software only, installed Oracle home, where the home-specific details are unavailable. This enables you to easily copy an image of an Oracle home to a new host on a new file system to serve as an active usable Oracle home.

A gold image can correspond, generally, to any application but in the context of this document, gold images correspond to Oracle Databases. Also, a gold image is not a ship home, which means that you do not have to run Oracle Universal Installer when deploying a gold image.

### Grid Home client

The Grid Home client is a remote Oracle Grid Infrastructure cluster that subscribes to the Fleet Patching and Provisioning Server for provisioning of gold images.

### Oracle Grid Infrastructure

The software that provides the infrastructure for an enterprise grid architecture. In a cluster this software includes Oracle Clusterware and Oracle ASM. For a standalone server, this software includes Oracle Restart and Oracle ASM. Oracle Database 12c combines these infrastructure products into one software installation called the Oracle Grid Infrastructure home (`Grid_home`).

### Grid Naming Service (GNS)

A generic service which resolves the names of hosts in a delegated normal DNS zone by mapping them to IP addresses within the zone. GNS enables the use of Dynamic Host Configuration Protocol (DHCP) address for Oracle RAC database nodes, simplifying deployment. GNS also resolves host names passed back from a SCAN listener.

### Hub anchor

A Hub Node in an Oracle Flex Cluster that acts as the connection point for purposes of cluster membership for one or more other supported nodes. Those nodes exchange heartbeats with a single Hub anchor.

### Hub Node

A node in an Oracle Flex Cluster that is tightly connected with other servers and has direct access to shared storage.

### image

Master copy of Oracle database home software which resides on the Fleet Patching and Provisioning Server.

### IPv4

Internet Protocol Version 4. IPv4 is the current standard for the IP protocol. IPv4 uses 32-bit (four-byte) addresses, which are typically represented in dotted-decimal notation. The decimal value of each octet is separated by a period, as in 192.168.2.22.

### IPv6

Internet Protocol Version 6. The protocol designed to replace IPv4. In IPv6, an IP address is typically represented in eight fields of hexadecimal values separated by colons, as in 2001:0DB8:0000:0000:0000:0000:1428:57AB. In some cases, fields with 0 values can be compressed, as in 2001:DB8::1428:57AB.

### local resource

A resource that runs on the nodes of a cluster but is unaware of anything outside of the scope of the node.

### OCR writer

Each CRSD process also acts as an OCR server. One of the CRSD processes in the cluster is the OCR server that performs I/O to the disk group or file, or block or raw device.

### Oracle Automatic Storage Management (Oracle ASM)

Oracle ASM manages the storage disks used by Oracle Clusterware and Oracle RAC in disk groups. By default, Oracle Clusterware uses Oracle ASM to store OCR and voting files.

### Oracle Cluster Registry (OCR)

The Oracle RAC configuration information repository that manages information about the cluster node list and instance-to-node mapping information. OCR also manages information about Oracle Clusterware resource profiles for customized applications.

### Oracle Clusterware

Software that allows groups (clusters) of connected servers to operate or be controlled as a unit.

### Oracle Clusterware stack

The Oracle Clusterware stack includes Oracle Cluster Ready Services, Event Manager, Cluster Synchronization Services, and Oracle ASM (if used).

### Oracle Flex Cluster

Large clusters that are made of up of Hub Nodes and other supported nodes, where the Hub Nodes form a cluster using current membership algorithms and the other nodes connect for membership to a single Hub Node.

### policy managed

Database administrators specify the server pool (excluding Generic or Free) in which the database resource runs. Oracle Clusterware places the database resource on a server.

### reader node

A reader node is a nodes on which an Oracle RAC database instance runs.

### resource

A database, application, or process managed by Oracle Clusterware.

### resource group

A container for an application that is comprised of various logically related resources that Oracle Clusterware manages and monitors as a single entity.

### resource state

The state of a particular resource at any given time that determines its availability to the cluster.

### resource type

Defines whether a resource is either a cluster resource or a local resource.

### server categorization

A method of identifying servers in the cluster into different categories by using a set of server attributes. Administrators can configure server pools to restrict which categories they accept. Server categories are created by providing attributes for the SERVER_CATEGORY parameter.

### server cluster

In a multicluster environment, a server cluster is a cluster in which the Grid Naming Service (GNS) process runs.

### server pool

A logical division of servers in a cluster into a group that hosts applications, databases, or both.

### Single Client Access Name (SCAN)

A single name that resolves to three IP addresses in the public network.

### start effort evaluation

The process that Oracle Clusterware goes through when it starts a resource. During this process, Oracle Clusterware considers resource dependencies contained in the profile of the resource.

### state

A set of values that describes what the condition of a particular resource.

### working copy

An Oracle ACFS snapshot of a gold image that can either be a software-only installed Oracle home or an instantiated, configured Oracle home.

### zone data

The GNS daemon records saved in the Oracle Cluster Registry.
