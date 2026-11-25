## 2.3.2 Deploying RDF Graph Server and Query UI from Oracle Cloud Marketplace

You can set up RDF Graph Server and Query UI in your Autonomous Database instance using the Oracle Cloud Marketplace image.

As a prerequisite, you must have the following already created:

- Oracle Autonomous Database (shared or dedicated infrastructure) created using your Oracle Cloud account
- Virtual Cloud Network (VCN) in your tenancy
- OCI compartment to create the stack instance
- SSH Key pair for `ssh` access to the instance

The Oracle Cloud Infrastructure (OCI) Marketplace displays two listings for Oracle RDF Graph Server and Query UI. However, the deployment varies depending on the pricing model as shown:

- Free: Apache Tomcat Server deployment
- BYOL: Oracle WebLogic Server deployment

The following steps apply to both Autonomous Data Warehouse or Autonomous Transaction Processing workload types as applicable to your Autonomous Database.

1.  Sign in to the OCI console and navigate to Marketplace.
2.  Search RDF on the Cloud Marketplace page and click the RDF Graph Server and Query UI listing that applies to you.
3.  Review, accept the Oracle Standard Terms and Restrictions and click Launch Stack.
    The Stack setup wizard gets triggered.
4.  Enter the appropriate metadata, selecting the required options to create the Compute Instance and configure the Instance Network variables.
5.  Enter the ADMIN user credentials for your application server under Advanced Configuration.
6.  Review the information and click Create.
    The stack deployment gets invoked and you can monitor the job progress on the Job Details page.
    Once the job completes and the stack is created successfully, the status shows as SUCCEEDED on the Job Details page.

    The RDF Graph Server and Query UI instance is now provisioned.
7.  Scroll down to the bottom of the logs section and note the public URL to launch RDF Graph Server and Query UI.
    The URL follows the format as shown:
    - Apache Tomcat Deployment: `https://<public_IP>:4040/orardf`
    - WebLogic Server Deployment: `https://<public_IP>:8001/orardf`
8.  Launch the RDF Graph Server and Query UI application in your browser.
    The RDF Graph login screen appears. See [RDF Graph Server and Query UI](rdf-graph-server-and-query-ui.md) for more details.

**Parent topic:** [Quick Start for Using RDF Semantic Data in Oracle Autonomous Database](quick-start-using-rdf-data-oracle-autonomous-database.md)
