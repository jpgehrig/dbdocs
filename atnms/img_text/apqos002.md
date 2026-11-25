The illustration shows in a flow chart how performance metrics are collected and used by the Oracle Database QoS Management server. On the left side of the illustration is a group titled Data Sources. In this group are three entities: Oracle RAC 12c, Oracle Clusterware 12c, and Operating System. Each entity communicates with the Data Connectors component of the Oracle Database QoS Management server. The communication is indicated by double-sided arrows, each of a different color. Oracle RAC 12c communicates with the Data Connector using JDBC. Oracle Clusterware 12c communicates with the Data Connector using the Server Manager (SRVM) component of Oracle Clusterware. The operating system communicates with the Data Connector using Clusterware Healthcheck Monitor (CHM).

In the middle of the illustration is a group titled QoS Management Server. On the left side of this group are three boxes, all labeled Data Connector. These boxes are connected to entities in the Data Sources group, as described earlier. On the right side of the QoS Management Server group are two boxes. The top one is labeled JMX Client Interfaces and the bottom one is labeled Policy and Performance Management Engine. The JMX Client Interfaces box is connected to the last group in the illustration, Oracle Enterprise Manager, using double-sided arrows, with the label XML.

On the right side of the illustration is a group titled Oracle Enterprise Manager. This group contains a single entity (or box). Inside the box is a list of ways in which Oracle Enterprise Manager displays the information. These are:

- Management Dashboard

- Policy Set Wizard

- Performance History

- Alerts and Actions

End of description.
