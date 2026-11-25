#

The image shows the Oracle MAA Platinum reference architecture deployed with the MAA Oracle GoldenGate hub architecture.

The diagram consists of two main horizontal sections: a Primary Region on top and a Remote Region on the bottom.

The Primary and Remote Region sections each contain 3 major components: Availability Domain 1 on the left, Application Tier in the center, and Availability Domain 2 on the right.

Each Availability Domain consists of an Exadata Database system and an Oracle GoldenGate Hub (GGHub). Each Availability Domain 1 system is labeled Production, and each Availability Domain 2 system is labeled Standby.

The Application Tier in each Region has two arrows each pointing at one of the Exadata systems within its region. The arrow pointing at Exadata in Availability Domain 1 is labeled Read/Write, and the arrow to Exadata in Availability Domain 2 is labeled Read.

There is a dotted line arrow from Exadata in Availability Domain 1 to the Exadata in Availability Domain 2 labeled Sync Transport with Zero Data Loss. According to the legend below the diagram, the dotted line indicates Active Data Guard Fast-Start Failover.

There is a dot and dash line between the Availability Domain 1 Exadata systems in each region, which indicates Oracle GoldenGate Replication.
