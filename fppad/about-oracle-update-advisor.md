## About Oracle Update Advisor

Oracle Update Advisor simplifies the patch management process for Oracle Grid Infrastructure and Oracle Database.

Oracle Update Advisor automates the patch management process and simplifies administration. This feature evaluates the deployed working copies or the specified Oracle home and recommends the best patching strategy. It recommends patches to maintain optimal security, stability, and performance for your Oracle deployments.

You can use the Oracle Update Advisor for both Oracle FPP Local Mode and Oracle FPP Central Server Mode. On Oracle FPP Server, you can directly import the gold image into the Oracle FPP image repository, thus making it ready for deploying a new working copy. On Oracle FPP Local Mode, you can download the gold image as a zip file that you can deploy later.

The workflow for using Oracle Update Advisor with Oracle FPP is as follows:

1.  Register a user for the Oracle Update Advisor using Oracle Single sign-on (SSO) and Customer Support Identifier (CSI).
2.  Get the health status and patch recommendation for the specified Oracle home or gold image.
3.  The image can be either already available or needs to be build per the system environment and health. Based on that, you can receive either of the following responses:
    1.  Sync: Displays the software health details, for already available images, including software health status and recommended patch level.
    2.  Async: Displays estimated time and request ID, for custom build images, which you can use to check the request status.
4.  Download the patched image. This step is different for Oracle FPP Local Mode and Oracle FPP Server Mode. In Oracle FPP Local Mode, you have to evaluate the Oracle home first and then download the image using the request ID that you received in the previous step. In Oracle FPP Server Mode, you can evaluate and download the image at the same time and even import the image to an existing gold image.

**Related Topics**

- [Using Oracle Update Advisor in Oracle FPP Server Mode](using-oracle-update-advisor-in-oracle-fpp-server-mode.md)

**Parent topic:** [Oracle Fleet Patching and Provisioning Overview](fleet-patching-provisioning.md)
