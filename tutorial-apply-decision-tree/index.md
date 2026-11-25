## Before You Begin

This 15-minute tutorial shows you how to apply a decision tree model and create a table to display the results by using the Data Miner graphical user interface.

### Background

The Workflow creation process of Oracle Data Miner automates many of the difficult tasks during the building and testing of models. It’s difficult to know in advance which algorithms will best solve the business problem, so normally several models are created and tested. No model is perfect, and the search for the best predictive model is not necessarily a question of determining the model with the highest accuracy, but rather a question of determining the types of errors that are tolerable in view of the business goals.

### What Do You Need?

- Oracle Database 19c Enterprise Edition
- [Oracle SQL Developer version 19.x](https://www.oracle.com/tools/downloads/sqldev-downloads.html)
- Oracle Data Miner User Account
- Oracle Data Miner Project and Workflow
- A Data Miner Decision Tree Classification Model Built from the INSUR_CUST_LTV_SAMPLE data

------------------------------------------------------------------------

## Choose A Model

1.  In the workflow, select the Class Build node. Then, using the Models section of the Properties tab, deselect all of the models except for the DT model.

    To deselect a model, click the large green arrow in the model's Output column. This action adds a small red "x" to the column, indicating that the model will not be used in the next build.

2.  Add a new Data Source node in the workflow.

    Note: Even though we are using the same table as the "Apply" data source, you must still add a second data source node to the workflow.

3.  In the Define Data Source wizard, select the **INSUR_CUST_LTV_SAMPLE** table, and then click **FINISH**.

4.  Click on the the new data source node name in the workflow. Then, change the node name to **INSUR_CUST_LTV_APPLY**.

5.  Expand the **Model Operations** category in the Components tab.

6.  Rename the Apply node to **Apply Model**.

7.  Connect the Class Build node to the Apply Model node.

    <figure>
    <img src="img/apply-model-setup.png" alt="Description of apply-model-setup.png follows" />
    <figcaption>Description of the illustration apply-model-setup.png</figcaption>
    </figure>

    The yellow exclamation mark disappears from the Apply node border once the second link is completed. This indicates that the node is ready to be run.

------------------------------------------------------------------------

## Specify the Output and Run the Model

Before you run the apply model node, consider the resulting output. By default, an apply node creates two columns of information for each customer: the prediction (Yes or No); and the probability of the prediction.

However, you really want to know this information for each customer, so that you can readily associate the predictive information with a given customer.To get this information, you need to add a third column to the apply output: CUSTOMER_ID.

1.  Right-click the Apply Model node and select **Edit**.

2.  In the Predictions tab of the Edit Apply Node window, select **CUSTOMER_ID** as the Case ID.

3.  Click **OK**.

4.  Right-click the Apply Model node and select **Run** from the menu.

    When the process is complete, green check mark icons are displayed in the border of all workflow nodes to indicate that the server process completed successfully.

------------------------------------------------------------------------

## Create a Database Table to Store the Results

1.  Using the Data category in the Components pane, drag the **Create Table or View** node to the workflow window.

2.  Connect the Apply Model node to the OUTPUT node.

3.  specify a name for the table that will be created:

4.  - Right-click the OUTPUT node and select **Edit** from the menu.
    - In the Edit Create Table or View Node window, change the default table name to **DT_PREDICTIONS**.
    - Click **OK**.

5.  Right-click the DT_PREDICTIONS node and select **Run** from the menu.

    <figure>
    <img src="img/create-table.png" alt="Description of create-table.png follows" />
    <figcaption>Description of the illustration create-table.png</figcaption>
    </figure>

    After you run the OUTPUT node (DT_PREDICTIONS), the table is created in your schema.

------------------------------------------------------------------------

## View the Results

1.  Right-click the DT_PREDICTIONS Table node and select **View Data** from the Menu.

2.  Sort the table results on any of the columns using the Sort button:

3.  - The Predicted outcome (CLAS_DT_1_1_PRED), in **Descending** order (meaning that the prediction of "Yes" for buying insurance is first.
    - Prediction Probability (CLAS_DT_1_1_PROB), in **Descending** order (meaning that the highest prediction probabilities are at the top of the table display.

4.  Click **Apply Sort** to view the results.

5.  When you are done viewing the results, dismiss the tab for the DT_PREDICTIONS table, and click **Save All**.

------------------------------------------------------------------------

## Want to Learn More?

- [Oracle Data Miner User's Guide](https://docs.oracle.com/en/database/oracle/sql-developer/19.4/dmrug/oracle-data-miner.html)
- [Oracle Data Miner product page](https://www.oracle.com/database/technologies/advanced-analytics/odm.html)

------------------------------------------------------------------------
