## Updating the Enterprise Manager Agent Base Directory After Upgrades

After upgrading Oracle Grid Infrastructure, update the Enterprise Manager Agent Base Directory on each cluster member node running an agent.

The Agent Base Directory is a directory where the Management Agent home is created. The Management Agent home is in the path Agent_Base_directory\core\\EMAgent_Version. For example, if the Agent Base Directory is `C:\app\emagent`, then Oracle creates the Management Agent home as `C:\app\emagent\core\13.1.1.0`.

1.  Navigate to the `bin` directory in the Management Agent home.
2.  In the `C:\app\emagent\core\13.1.1.0\bin` directory, open the file `emctl` with a text editor.
3.  Locate the parameter `CRS_HOME`, and update the parameter to the new Grid home path.
4.  Repeat steps 1-3 on each node of the cluster with an Enterprise Manager agent.

**Parent topic:** [Updating Oracle Enterprise Manager Cloud Control Target Parameters](updating-oracle-enterprise-manager-cloud-control-target-parameters.md)
