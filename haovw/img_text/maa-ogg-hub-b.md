#

The image shows the Oracle MAA GoldenGate Hub architecture in three major parts: an GoldenGate hub (GGHub) in the center, the Source database environment on the left side and the Target database environment on the right.

The source and target database environments consist of an Exadata Database Machine and a network connection to the GGHub.

The source database is labeled as Database 12c Release 2, and the target database is labeled as Database 19c, to show they are different versions of Oracle Database.

The GGHub in the center of the diagram is divided into two major boxes labeled GoldenGate Deployment.

The GoldenGate Deployment on the left side of the GGHub consists of a Service Manager (server icon), Administration Server (server icon), Extract process (cylinder icon), and Performance Metric Server (server icon).

The GoldenGate Deployment on the right side of the GGHub consists of a Service Manager (server icon), Administration Server (server icon), Replicat process (cylinder icon), and Performance Metric Server (server icon).

Between the two GoldenGate Deployment boxes, a Trail Files icon with arrows shows the flow of trail files from the left-side GoldenGate Deployment Extract process to the right-side GoldenGate Deployment Replicat process.
