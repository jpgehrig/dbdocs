Oracle Cluster Health Advisor provides system and database administrators with early warning of pending performance issues, and root causes and corrective actions for Oracle RAC databases and cluster nodes.

Use Oracle Cluster Health Advisor to increase availability and performance management.

Oracle Cluster Health Advisor estimates an expected value of an observed input based on the default model, which is a trained calibrated model based on a normal operational period of the target system. Oracle Cluster Health Advisor then performs anomaly detection for each input based on the difference between observed and expected values. If sufficient inputs associated with a specific problem are abnormal, then Oracle Cluster Health Advisor raises a warning and generates an immediate targeted diagnosis and corrective action.

Oracle Cluster Health Advisor stores the analysis results, along with diagnosis information, corrective action, and metric evidence for later triage, in the Grid Infrastructure Management Repository (GIMR). Oracle Cluster Health Advisor also sends warning messages to Enterprise Manager Cloud Control using the Oracle Clusterware event notification protocol.

- [Oracle Cluster Health Advisor Architecture](cluster-health-advisor-architecture.md)
  Oracle Cluster Health Advisor runs as a highly available cluster resource, `ochad`, on each node in the cluster.
- [Monitoring the Oracle Real Application Clusters (Oracle RAC) Environment with Oracle Cluster Health Advisor](monitoring-rac-cha.md)
  Oracle Cluster Health Advisor is automatically provisioned on each node by default when Oracle Grid Infrastructure is installed for Oracle Real Application Clusters (Oracle RAC) or Oracle RAC One Node database.
- [Using Cluster Health Advisor for Health Diagnosis](using-cha-health-diagnosis.md)
  Oracle Cluster Health Advisor raises and clears problems autonomously and stores the history in the Grid Infrastructure Management Repository (GIMR).
- [Calibrating an Oracle Cluster Health Advisor Model for a Cluster Deployment](calibrating-cha-model-cluster-deployment.md)
  As shipped with default node and database models, Oracle Cluster Health Advisor is designed not to generate false warning notifications.
- [Viewing the Details for an Oracle Cluster Health Advisor Model](viewing-cha-model-details.md)
  Use the `chactl query model` command to view the model details.
- [Managing the Oracle Cluster Health Advisor Repository](managing-cha-repository.md)
  Oracle Cluster Health Advisor repository stores the historical records of cluster host problems, database problems, and associated metric evidence, along with models.
- [Viewing the Status of Cluster Health Advisor](using-srvctl.md)
  SRVCTL commands are the tools that offer total control on managing the life cycle of Oracle Cluster Health Advisor as a highly available service.

**Related Topics**

- [Introduction to Oracle Cluster Health Advisor](cluster-health-advisor.md)

**Parent topic:** [Analyzing the Cluster Configuration](analyzing-risks-and-complying-best-practices.md)
