Prediction details are XML strings that provide information about the score. Details are available for all types of scoring: clustering, feature extraction, classification, regression, and anomaly detection. Details are available whether scoring is dynamic or the result of model apply.

The details functions, `CLUSTER_DETAILS`, `FEATURE_DETAILS`, and `PREDICTION_DETAILS` return the actual value of attributes used for scoring and the relative importance of the attributes in determining the score. By default, the functions return the five most important attributes in descending order of importance.

### 32.3.1 Cluster Details

For the most likely cluster assignments of customer 100955 (probability of assignment \> 20%), the query in the following example produces the five attributes that have the most impact for each of the likely clusters. The clustering functions apply an Expectation Maximization model named `em_sh_clus_sample` to the data selected from `mining_data_apply_v`. The "5" specified in `CLUSTER_DETAILS` is not required, because five attributes are returned by default.

Example 32-6 Cluster Details

    SELECT S.cluster_id, probability prob,
               CLUSTER_DETAILS(em_sh_clus_sample, S.cluster_id, 5 USING T.*) det
        FROM
          (SELECT v.*, CLUSTER_SET(em_sh_clus_sample, NULL, 0.2 USING *) pset
            FROM mining_data_apply_v v
           WHERE cust_id = 100955) T,
          TABLE(T.pset) S
        ORDER BY 2 DESC;

    CLUSTER_ID  PROB DET
    ---------- ----- ----------------------------------------------------------------------------
            14 .6761 <Details algorithm="Expectation Maximization" cluster="14">
                     <Attribute name="AGE" actualValue="51" weight=".676" rank="1"/>
                     <Attribute name="HOME_THEATER_PACKAGE" actualValue="1" weight=".557" rank="2"/>
                     <Attribute name="FLAT_PANEL_MONITOR" actualValue="0" weight=".412" rank="3"/>
                     <Attribute name="Y_BOX_GAMES" actualValue="0" weight=".171" rank="4"/>
                     <Attribute name="BOOKKEEPING_APPLICATION"actualValue="1" weight="-.003"
                      rank="5"/>
                     </Details>

             3 .3227 <Details algorithm="Expectation Maximization" cluster="3">
                     <Attribute name="YRS_RESIDENCE" actualValue="3" weight=".323" rank="1"/>
                     <Attribute name="BULK_PACK_DISKETTES" actualValue="1" weight=".265" rank="2"/>
                     <Attribute name="EDUCATION" actualValue="HS-grad" weight=".172" rank="3"/>
                     <Attribute name="AFFINITY_CARD" actualValue="0" weight=".125" rank="4"/>
                     <Attribute name="OCCUPATION" actualValue="Crafts" weight=".055" rank="5"/>
                     </Details>

### 32.3.2 Feature Details

The query in the following example returns the three attributes that have the greatest impact on the top Principal Components Analysis (PCA) projection for customer 101501. The `FEATURE_DETAILS` function applies a Singular Value Decomposition model named `svd_sh_sample` to the data selected from `svd_sh_sample_build_num`.

Example 32-7 Feature Details

    SELECT FEATURE_DETAILS(svd_sh_sample, 1, 3 USING *) proj1det
      FROM svd_sh_sample_build_num
      WHERE CUST_ID = 101501;

    PROJ1DET
    --------------------------------------------------------------------------------
    <Details algorithm="Singular Value Decomposition" feature="1">
    <Attribute name="HOME_THEATER_PACKAGE" actualValue="1" weight=".352" rank="1"/>
    <Attribute name="Y_BOX_GAMES" actualValue="0" weight=".249" rank="2"/>
    <Attribute name="AGE" actualValue="41" weight=".063" rank="3"/>
    </Details>

### 32.3.3 Prediction Details

The query in the following example returns the attributes that are most important in predicting the age of customer 100010. The prediction functions apply a Generalized Linear Model Regression model named `GLMR_SH_Regr_sample` to the data selected from `mining_data_apply_v`.

Example 32-8 Prediction Details for Regression

    SELECT cust_id,
          PREDICTION(GLMR_SH_Regr_sample USING *) pr,
          PREDICTION_DETAILS(GLMR_SH_Regr_sample USING *) pd
      FROM mining_data_apply_v
      WHERE CUST_ID = 100010;

    CUST_ID    PR PD
    ------- ----- -----------
     100010 25.45 <Details algorithm="Generalized Linear Model">
                  <Attribute name="FLAT_PANEL_MONITOR" actualValue="1" weight=".025" rank="1"/>
                  <Attribute name="OCCUPATION" actualValue="Crafts" weight=".019" rank="2"/>
                  <Attribute name="AFFINITY_CARD" actualValue="0" weight=".01" rank="3"/>
                  <Attribute name="OS_DOC_SET_KANJI" actualValue="0" weight="0" rank="4"/>
                  <Attribute name="BOOKKEEPING_APPLICATION" actualValue="1" weight="-.004" rank="5"/>
                  </Details>

The query in the following example returns the customers who work in Tech Support and are likely to use an affinity card (with more than 85% probability). The prediction functions apply an Support Vector Machine (SVM) Classification model named `svmc_sh_clas_sample`. to the data selected from `mining_data_apply_v`. The query includes the prediction details, which show that education is the most important predictor.

Example 32-9 Prediction Details for Classification

    SELECT cust_id, PREDICTION_DETAILS(svmc_sh_clas_sample, 1 USING *) PD
          FROM mining_data_apply_v
      WHERE PREDICTION_PROBABILITY(svmc_sh_clas_sample, 1 USING *) > 0.85
      AND occupation = 'TechSup'
      ORDER BY cust_id;

    CUST_ID PD
    ------- ---------------------------------------------------------------------------------------
     100029 <Details algorithm="Support Vector Machines" class="1">
            <Attribute name="EDUCATION" actualValue="Assoc-A" weight=".199" rank="1"/>
            <Attribute name="CUST_INCOME_LEVEL" actualValue="I: 170\,000 - 189\,999" weight=".044"
             rank="2"/>
            <Attribute name="HOME_THEATER_PACKAGE" actualValue="1" weight=".028" rank="3"/>
            <Attribute name="BULK_PACK_DISKETTES" actualValue="1" weight=".024" rank="4"/>
            <Attribute name="BOOKKEEPING_APPLICATION" actualValue="1" weight=".022" rank="5"/>
            </Details>

     100378 <Details algorithm="Support Vector Machines" class="1">
            <Attribute name="EDUCATION" actualValue="Assoc-A" weight=".21" rank="1"/>
            <Attribute name="CUST_INCOME_LEVEL" actualValue="B: 30\,000 - 49\,999" weight=".047"
             rank="2"/>
            <Attribute name="FLAT_PANEL_MONITOR" actualValue="0" weight=".043" rank="3"/>
            <Attribute name="HOME_THEATER_PACKAGE" actualValue="1" weight=".03" rank="4"/>
            <Attribute name="BOOKKEEPING_APPLICATION" actualValue="1" weight=".023" rank="5"/>
            </Details>

     100508 <Details algorithm="Support Vector Machines" class="1">
            <Attribute name="EDUCATION" actualValue="Bach." weight=".19" rank="1"/>
            <Attribute name="CUST_INCOME_LEVEL" actualValue="L: 300\,000 and above" weight=".046"
             rank="2"/>
            <Attribute name="HOME_THEATER_PACKAGE" actualValue="1" weight=".031" rank="3"/>
            <Attribute name="BULK_PACK_DISKETTES" actualValue="1" weight=".026" rank="4"/>
            <Attribute name="BOOKKEEPING_APPLICATION" actualValue="1" weight=".024" rank="5"/>
            </Details>

     100980 <Details algorithm="Support Vector Machines" class="1">
            <Attribute name="EDUCATION" actualValue="Assoc-A" weight=".19" rank="1"/>
            <Attribute name="FLAT_PANEL_MONITOR" actualValue="0" weight=".038" rank="2"/>
            <Attribute name="HOME_THEATER_PACKAGE" actualValue="1" weight=".026" rank="3"/>
            <Attribute name="BULK_PACK_DISKETTES" actualValue="1" weight=".022" rank="4"/>
            <Attribute name="BOOKKEEPING_APPLICATION" actualValue="1" weight=".02" rank="5"/>
            </Details>

The query in the following example returns the two customers that differ the most from the rest of the customers. The prediction functions apply an anomaly detection model named `SVMO_SH_Clas_sample` to the data selected from `mining_data_apply_v`. Anomaly Detection uses a one-class SVM classifier.

Example 32-10 Prediction Details for Anomaly Detection

    SELECT cust_id, pd FROM
      (SELECT cust_id,
             PREDICTION_DETAILS(SVMO_SH_Clas_sample, 0 USING *) pd,
             RANK() OVER (ORDER BY prediction_probability(
                   SVMO_SH_Clas_sample, 0 USING *) DESC, cust_id) rnk
      FROM mining_data_one_class_v)
      WHERE rnk <= 2
      ORDER BY rnk;

      CUST_ID PD
    ---------- -----------------------------------------------------------------------------------
        102366 <Details algorithm="Support Vector Machines" class="0">
               <Attribute name="COUNTRY_NAME" actualValue="United Kingdom" weight=".078" rank="1"/>
               <Attribute name="CUST_MARITAL_STATUS" actualValue="Divorc." weight=".027" rank="2"/>
               <Attribute name="CUST_GENDER" actualValue="F" weight=".01" rank="3"/>
               <Attribute name="HOUSEHOLD_SIZE" actualValue="9+" weight=".009" rank="4"/>
               <Attribute name="AGE" actualValue="28" weight=".006" rank="5"/>
               </Details>

        101790 <Details algorithm="Support Vector Machines" class="0">
               <Attribute name="COUNTRY_NAME" actualValue="Canada" weight=".068" rank="1"/>
               <Attribute name="HOUSEHOLD_SIZE" actualValue="4-5" weight=".018" rank="2"/>
               <Attribute name="EDUCATION" actualValue="7th-8th" weight=".015" rank="3"/>
               <Attribute name="CUST_GENDER" actualValue="F" weight=".013" rank="4"/>
               <Attribute name="AGE" actualValue="38" weight=".001" rank="5"/>
               </Details>

### 32.3.4 GROUPING Hint

Data mining functions consist of SQL functions such as `PREDICTION*`, `CLUSTER*`, `FEATURE*`, and `ORA_DM_*`. The `GROUPING` hint is an optional hint which applies to data mining scoring functions when scoring partitioned models.

#### Enhanced PREDICTION Function Command Format

This hint results in partitioning the input data set into distinct data slices so that each partition is scored in its entirety before advancing to the next partition. However, parallelism by partition is still available. Data slices are determined by the partitioning key columns used when the model was built. This method can be used with any data mining function against a partitioned model. The hint may yield a query performance gain when scoring large data that is associated with many partitions but may negatively impact performance when scoring large data with few partitions on large systems. Typically, there is no performance gain if you use the hint for single row queries.

    <prediction function> ::=
        PREDICTION <left paren> /*+ GROUPING */ <prediction model>
            [ <comma> <class value> [ <comma> <top N> ] ]
            USING <mining attribute list> <right paren>

The syntax for only the `PREDICTION` function is given but it is applicable to any Data mining function where `PREDICTION`, `CLUSTERING`, and `FEATURE_EXTRACTION` scoring functions occur.

Example 32-11 Example

    SELECT PREDICTION(/*+ GROUPING */my_model USING *) pred FROM <input table>;

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/PREDICTION.md)
