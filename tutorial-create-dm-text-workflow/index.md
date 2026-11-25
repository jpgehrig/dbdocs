## Before You Begin

This 15-minute tutorial shows you how to create a new workflow that performs text mining activities.

### Background

In addition to the existing k-Means and O-Cluster algorithms, Oracle Data Mining now supports Expectation Maximization, a clustering algorithm that creates a density model of the data. The density model allows for an improved approach to combining data originating in different domains. For example, EM enables combination of structured data (such as sales transactions and customer demographics) with unstructured data, such as text data.

### What Do You Need?

- Oracle Database 19c Enterprise Edition
- [Oracle SQL Developer version 19.x](https://www.oracle.com/tools/downloads/sqldev-downloads.html)
- Oracle Data Miner User Account
- ABC Insurance Project

------------------------------------------------------------------------

## Create a Workflow and Add a Data Source

1.  Right-click your project (ABC Insurance) and select **New Workflow** from the menu.

2.  In the Create Workflow window, enter **EM Clustering** as the name and click **OK**.

3.  In the Components tab, drill on the **Data** category, drag and drop a Data Source node on the workflow, and select **MINING_DATA_TEXT_BUILD_V** from the Available Tables/Views list in the wizard.

4.  Click **Finish** to complete the data source node definition and close the wizard.

5.  Right-click the data source node and select **View Data** from the menu.

    A tabbed window for the data source appears then enables you to browse the data.

    - Select the first record in the COMMENTS column.

      The View Value window appears (as well as the sunglasses icon).

    - Click the Wrap option to display the entire comment.

      <figure>
      <img src="img/display-comment.jpg" alt="Description of display-comment.jpg follows" />
      <figcaption>Description of the illustration display-comment.jpg</figcaption>
      </figure>

      This column contains customer feedback that we want to use in our text mining exercise.

6.  Close the View Value window.

7.  Dismiss the MINING_DATA_TEXT_BUILD_V window.

8.  Save the workflow.

------------------------------------------------------------------------

## Create the EM Clustering Model

Clustering models may be used to predict the groups (clusters) that categorize specified input attributes. In this scenario, you want to predict the cluster that a customer is most likely to belong to based on customer feedback.

By default, Oracle Data Miner selects all of the supported algorithms for a selected model. Here, you modify a Clustering node to use only the Expectation Maximization algorithm for the model. Then, you will enable text mining within the model.

1.  Expand the Models category in the Components tab.
2.  Drag and drop the Clustering node from the Components tab to the Workflow pane.
3.  Right-click the data source node, select **Connect** from the pop-up menu, drag the pointer to the Clust Build node, and release.
4.  Double-click the clustering build node to display the Edit Clustering Build Node window.
5.  In the Build tab, choose a Case ID value and remove the K-Means and O-Cluster algorithms, by doing the following:
    - Select **CUST_ID** as the Case ID value.
    - Select both the K-Means and O-Cluster algorithms as shown below.
    - Click the **Delete** tool (red "x"), and then click **Yes** in the warning dialog to remove the two algorithms from the Model Settings list.
6.  Select the **Input** tab.
7.  Deselect the **Determine inputs automatically** option.
8.  Modify settings for two of the input attributes: COMMENTS and PRINTER_SUPPLIES:
    - Select the **COMMENTS** attribute, and click the Categorical icon in the Mining Type column. Then use the pop-up menu to change the Mining Type from Categorical to **Text**.
    - Select the **PRINTER_SUPPLIES** attribute and click the Input icon (green arrow). Use the pop-up menu to select **Ignore**.
9.  Click **OK** in the Edit Clustering Build Node window to save your changes

------------------------------------------------------------------------

## Next Tutorial

In the next tutorial, you'll build the EM clustering model against the source data. Once the model is built, you view and evaluate the results.

------------------------------------------------------------------------
