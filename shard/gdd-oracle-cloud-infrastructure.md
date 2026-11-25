## 5 Using Oracle Database Sharding in Oracle Cloud Infrastructure

Oracle Sharding provides a native Oracle Cloud Infrastructure (OCI) service for managed deployments, and supplies tooling to automate and further simplify the sharded database deployment operations.

### Oracle Cloud Infrastructure Services

Oracle's Globally Distributed Autonomous Database is a fully managed Oracle Cloud Infrastructure service that provides a single user interface to deploy and manage a data set across many database instances (shards) in a globally distributed, linearly scalable, multimodel database.

Oracle Globally Distributed Autonomous Database brings the power of distributed (sharded) databases to Oracle Autonomous Database on Dedicated Exadata Infrastructure. The service is built on top of Oracle's autonomous technology, which means that it is self-driving, self-securing, and self-healing. This allows automation of many of the routine tasks associated with managing a database, such as patching, tuning, and backup and recovery, which can help reduce the risk of human error and improve system uptime. See <https://docs.oracle.com/en/cloud/paas/globally-distributed-autonomous-database/>

### Deploy a Sharded Database on Kubernetes

Automate the provisioning of sharded databases on Oracle Kubernetes Engine (OKE) using Oracle Cloud Infrastructure Ansible Modules and Helm/Chart.

To deploy Oracle Sharding on OKE, Oracle Cloud Infrastructure Ansible Modules create compute resources, configure the network, and create block storage volumes by using yaml files passed to Ansible playbooks.

Find the instructions and downloads for sharded database deployment on Kubernetes at <https://github.com/oracle/db-sharding/tree/master/oke-based-sharding-deployment>.

### Deploy a Sharded Database With Terraform

Tooling for Oracle Sharding includes Terraform modules and scripts to automate your sharded database deployment on both Oracle Cloud Infrastructure and on-premises systems.

The Terraform modules and scripts create and configure a complete sharded database infrastructure, including shard directors, shard catalogs, and shards. The scripts also provide the option to deploy standby shards and shard catalogs using Oracle Data Guard for replication to provide high availability and disaster recovery of the sharded data.

As part of the set-up process, you install the Terraform binary, download the Oracle Sharding shard director installation package, and for on-premises deployments, you download the Oracle Database installation files.

Find the instructions and downloads for Terraform-based sharded database deployment for your target systems at the following locations.

- Oracle Cloud Infrastructure <https://github.com/oracle/db-sharding/tree/master/deployment-with-terraform/sdb-terraform-oci>.
- On-Premises <https://github.com/oracle/db-sharding/tree/master/deployment-with-terraform/sdb-terraform-onprem>

### Deploy a Sharded Database with Docker

Oracle Sharding provides sample Docker build files to facilitate sharded database installation, configuration, and environment setup for DevOps users.

In this process you install and configure the Docker engine, create global service manager (shard director) and Oracle Database images, create a network bridge, create containers for the Oracle Sharding objects and shard director, and deploy the containers.

Find the instructions and downloads for sharded database deployment with Docker at <https://github.com/oracle/db-sharding/tree/master/docker-based-sharding-deployment>.
