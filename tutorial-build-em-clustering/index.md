## Before You Begin

This 15-minute tutorial shows you how to build an expectation maximization (EM) clustering model using a text-based data source.

### Background

In addition to the existing k-Means and O-Cluster algorithms, Oracle Data Mining now supports Expectation Maximization, a clustering algorithm that creates a density model of the data. The density model allows for an improved approach to combining data originating in different domains. For example, EM enables combination of structured data (such as sales transactions and customer demographics) with unstructured data, such as text data.

### What Do You Need?

- Oracle Database 19c Enterprise Edition
- [Oracle SQL Developer version 19.x](https://www.oracle.com/tools/downloads/sqldev-downloads.html)
- Oracle Data Miner User Account
- Data Miner Workflow for Text Mining

------------------------------------------------------------------------

## Build the Model and View the Results

1.  Right-click the Clust Build node and select **Run** from the pop-up menu.

    <figure>
    <img src="img/build-model.jpg" alt="Description of build-model.jpg follows" />
    <figcaption>Description of the illustration build-model.jpg</figcaption>
    </figure>

    When the build is complete, all nodes contain a green check mark in the node border

2.  Right-click the clustering build node again, and select **View Models \> CLUS_EM_1_3** (Note: The automatically generated name of your Clustering model may be different than shown here.)

    The Edit Classification Build Node window automatically appears.

3.  Select **Cluster 2**, which represents the slightly larger cluster after the split.

    <figure>
    <img src="img/cluster3-tree.png" alt="Description of cluster3-tree.png follows" />
    <figcaption>Description of the illustration cluster3-tree.png</figcaption>
    </figure>

    The bottom pane contains three tabs: Centroid, Rule, and Components. The Centroid tab displays a list of the attribute values that best define the selected cluster, ranked by importance.

4.  Select the **Component** tab.

    <figure>
    <img src="img/component-tab.png" alt="Description of component-tab.png follows" />
    <figcaption>Description of the illustration component-tab.png</figcaption>
    </figure>

    The Component tab includes distribution plots of the ranked text mining results. In this tab, the bottom pane provides two tabs: (A) The Chart tab provides a larger view of the selected attribute’s distribution chart. (B) The Projections tab (shown in the example) provides a list of the Attribute Sub Name values that best describe the selected attribute. Here, we sorted the list in descending order by Coefficient value.

5.  Select the **Cluster** tab.

    <figure>
    <img src="img/cluster-tab.png" alt="Description of cluster-tab.png follows" />
    <figcaption>Description of the illustration cluster-tab.png</figcaption>
    </figure>

    In this example, Cluster 3 is selected. This is the same cluster that we selected in the Tree viewer. The Cluster tab shows a list of contributing attributes, ranked by Confidence %. A histogram of the selected attribute is shown in the bottom pane.

6.  Select the **Compare** tab.

    <figure>
    <img src="img/compare-tab.png" alt="Description of compare-tab.png follows" />
    <figcaption>Description of the illustration compare-tab.png</figcaption>
    </figure>

    The Compare tab shows a list of contributing attributes for the selected clusters, sorted by Rank of importance. In this example, Clusters 2 and 3 are compared. A distribution histogram of the selected attribute is shown in the bottom pane

7.  Dismiss the model viewer window.

------------------------------------------------------------------------

## Apply the Model to Make Predictions

1.  Add a new Data Source node in the workflow:
    - From the Data group in the Components tab, drag and drop a **Data Source** node to the workflow pane, as shown below. The Define Data Source wizard opens automatically.
    - Select the **MINING_DATA_TEXT_APPLY_V** view in Step 1 of the wizard.
    - Click **Finish** to save the data source definition.

2.  Expand the Model Operations category in the Components tab and drag an **Apply** node to the workflow canvas.

3.  Connect the Clust Build node to the Apply node, and then connect the MINING_DATA_TEXT_APPLY_V node to the Apply node.

4.  Add the customer id to the output:
    - Right-click the Apply Model node and select **Edit**.
    - In the Predictions tab of the Edit Apply Node window, select **CUST_ID** as the Case ID.

5.  Click **OK** in the Edit Apply Node window to save your changes.

6.  Right-click the Apply Model node and select **Run** from the menu.

    <figure>
    <img src="img/run-em-model.jpg" alt="Description of run-em-model.jpg follows" />
    <figcaption>Description of the illustration run-em-model.jpg</figcaption>
    </figure>

    When the process is complete, green check mark icons are displayed in the border of all workflow nodes to indicate that the server process completed successfully.

------------------------------------------------------------------------

## View the Results

1.  Right-click the Apply Model node and select **View Data** from the Menu.
2.  Click the **Sort** button, and specify a sort using the prediction probability, in descending order.
3.  Click **Apply Sort** to view the results.
    <figure>
    <img src="img/apply-model-results.png" alt="Description of apply-model-results.png follows" />
    <figcaption>Description of the illustration apply-model-results.png</figcaption>
    </figure>
4.  You can enter a Where clause in the Filter box to narrow the output results.
    - Enter the following Where clause:

           CLUS_EM_1_2_CLID = 3 and CLUS_EM_1_2_PROB > .997

    - Press **Enter**.

      <figure>
      <img src="img/apply-model-filter.png" alt="Description of apply-model-filter.png follows" />
      <figcaption>Description of the illustration apply-model-filter.png</figcaption>
      </figure>

      The results should show records for those customers who are predicted to be in Cluster 3, with a probability greater than 99.7%.

      Each time you run an Apply node, Oracle Data Miner may take a different sample of the data to display. With each Apply, both the data and the order in which it is displayed may change. Therefore, the sample in your table may be different from the sample shown here. This is particularly evident when only a small pool of data is available, which is the case in the schema for this lesson.
5.  When you are done viewing the results, dismiss the Apply Model window, and click **Save All**.

------------------------------------------------------------------------

## Want to Learn More?

- [Oracle Data Miner User's Guide](https://docs.oracle.com/en/database/oracle/sql-developer/19.4/dmrug/oracle-data-miner.html)
- [Oracle Data Miner product page](https://www.oracle.com/database/technologies/advanced-analytics/odm.html)

------------------------------------------------------------------------
