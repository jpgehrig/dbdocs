#

The image shows the Oracle MAA Platinum reference architecture at a high level.

The diagram consists of two main horizontal sections: a Primary Region on top and a Remote Region on the bottom.

Primary Region

- The Primary Region section contains 3 major components: on the far left, a Zero Data Loss Recovery Appliance (Recovery Appliance), and then two Availability Domains labeled AD2 (left) and AD1 (right).

- AD2 and AD1 each consist of a 2-node Oracle RAC on Exadata and between the ADs is a line labeled Data Guard FSFO (Fast-start failover).

- Connected to AD2 is a Standby Database icon indicating that this is a Standby Database on the 2-node RAC Exadata system. AD2 is also linked to the Recovery Appliance icon indicating that the Standby Database system is backed up locally on the appliance.

- Connected to AD1 is a Primary Database icon indicating that this is a Primary Database on the 2-node RAC Exadata system.

Remote Region

- The Remote Region section also contains the same 3 major components as the Primary Region: on the far left, a Zero Data Loss Recovery Appliance (Recovery Appliance), and then two Availability Domains labeled AD1 (left) and AD2 (right). Note that the order of AD1 and AD2 are the opposite of those ADs in the Primary Region.

- AD1 and AD2 each consist of a 2-node Oracle RAC on Exadata, and between the ADs is a line labeled Data Guard FSFO (Fast-start failover).

- Connected to AD1 is a Standby Database icon indicating that this is a Standby Database on the 2-node RAC Exadata system. AD1 is also linked to the Recovery Appliance icon indicating that the Standby Database system is backed up locally on the appliance.

- Connected to AD2 is a Primary Database icon indicating that this is a Primary Database on the 2-node RAC Exadata system.

Finally, between the AD1 in the Primary Region and AD2 in the Remote Region there is a bidirectional arrow labeled Oracle GoldenGate Replication, indicating that bi-directional GoldenGate replication is taking place between the Primary Database of each region.
