# Description of the illustration odmr.png

This image, odmr.png, shows a sample workflow in Oracle Data Miner. At a very high level, there are two data Source node of sample data: CUST_INSU_LTV and NEW_CUST_INSUR_LTV.

1.  The CUST_INSU_LTV data is ‘explored’ or a data profiling is done using the Explore Data node.

2.  A filter is applied using Filter Column node and a Response Model scores a Classification model.

3.  The workflow for CUST_INSU_LTV data builds a Cluster model and a Classification model predicting the customer segments and the likelihood of the customers to buy the insurance respectively.

4.  The workflow for NEW_CUST_INSUR_LTV data builds a Classification model predicting the likelihood of the customers to buy the insurance.
