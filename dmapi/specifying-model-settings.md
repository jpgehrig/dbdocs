Understand how to configure data mining models at build time.

Numerous configuration settings are available for configuring data mining models at build time. To specify settings, create a settings table with the columns shown in the following table and pass the table to `CREATE_MODEL`.

Table 31-4 Settings Table Required Columns

| Column Name     | Data Type        |
|:----------------|:-----------------|
| `setting_name`  | `VARCHAR2(30)`   |
| `setting_value` | `VARCHAR2(4000)` |

Example 31-1 creates a settings table for an Support Vector Machine (SVM) Classification model. Since SVM is not the default classifier, the `ALGO_NAME` setting is used to specify the algorithm. Setting the `SVMS_KERNEL_FUNCTION` to `SVMS_LINEAR` causes the model to be built with a linear kernel. If you do not specify the kernel function, the algorithm chooses the kernel based on the number of attributes in the data.

Some settings apply generally to the model, others are specific to an algorithm. Model settings are referenced in Table 31-5 and Table 31-6.

Table 31-5 General Model Settings

| Settings                     | Description                                                                                                    |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------|
| Mining function settings     | See "[Mining Function Settings](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference   |
| Algorithm names              | See "[Algorithm Names](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference            |
| Global model characteristics | See "[Global Settings](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference            |
| Automatic Data Preparation   | See "[Automatic Data Preparation](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference |

Table 31-6 Algorithm-Specific Model Settings

| Algorithm                         | Description                                                                                                                                                     |
|:----------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CUR Matrix Decomposition          | See "[DBMS_DATA_MINING —Algorithm Settings: CUR Matrix Decomposition](../arpls/DBMS_DATA_MINING.md)"in Oracle Database PL/SQL Packages and Types Reference      |
| Decision Tree                     | See "[DBMS_DATA_MINING —Algorithm Settings: Decision Tree](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference                         |
| Expectation Maximization          | See "[DBMS_DATA_MINING —Algorithm Settings: Expectation Maximization](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference              |
| Explicit Semantic Analysis        | See “[DBMS_DATA_MINING —Algorithm Settings: Explicit Semantic Analysis](../arpls/DBMS_DATA_MINING.md)” in Oracle Database PL/SQL Packages and Types Reference   |
| Exponential Smoothing             | See "[DBMS_DATA_MINING —Algorithm Settings: Exponential Smoothing Models](../arpls/DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference |
| Generalized Linear Models         | See "[DBMS_DATA_MINING —Algorithm Settings: Generalized Linear Models](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference             |
| k-Means                           | See "[DBMS_DATA_MINING —Algorithm Settings: k-Means](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference                               |
| Naive Bayes                       | See "[Algorithm Settings: Naive Bayes](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference                                             |
| Neural Network                    | See "[DBMS_DATA_MINING —Algorithm Settings: Neural Network](../arpls/DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference               |
| Non-Negative Matrix Factorization | See "[DBMS_DATA_MINING —Algorithm Settings: Non-Negative Matrix Factorization](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference     |
| O-Cluster                         | See "[Algorithm Settings: O-Cluster](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference                                               |
| Random Forest                     | See "[DBMS_DATA_MINING — Algorithm Settings: Random Forest](../arpls/DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference               |
| Singular Value Decomposition      | See "[DBMS_DATA_MINING —Algorithm Settings: Singular Value Decomposition](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference          |
| Support Vector Machine            | See "[DBMS_DATA_MINING —Algorithm Settings: Support Vector Machine](DBMS_DATA_MINING.md)" in Oracle Database PL/SQL Packages and Types Reference                |

Example 31-1 Creating a Settings Table for an SVM Classification Model

    CREATE TABLE svmc_sh_sample_settings (
      setting_name VARCHAR2(30),
      setting_value VARCHAR2(4000));

    BEGIN
      INSERT INTO svmc_sh_sample_settings (setting_name, setting_value) VALUES
        (dbms_data_mining.algo_name, dbms_data_mining.algo_support_vector_machines);
      INSERT INTO svmc_sh_sample_settings (setting_name, setting_value) VALUES
        (dbms_data_mining.svms_kernel_function, dbms_data_mining.svms_linear);
      COMMIT;
    END;
    /

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](DBMS_DATA_MINING.md)

### 31.3.1 Specifying Costs

Specify a cost matrix table to build a Decision Tree model.

The `CLAS_COST_TABLE_NAME` setting specifies the name of a cost matrix table to be used in building a Decision Tree model. A cost matrix biases a classification model to minimize costly misclassifications. The cost matrix table must have the columns shown in the following table:

Table 31-7 Cost Matrix Table Required Columns

| Column Name              | Data Type              |
|:-------------------------|:-----------------------|
| `actual_target_value`    | valid target data type |
| `predicted_target_value` | valid target data type |
| `cost`                   | `NUMBER`               |

Decision Tree is the only algorithm that supports a cost matrix at build time. However, you can create a cost matrix and associate it with any classification model for scoring.

If you want to use costs for scoring, create a table with the columns shown in Table 31-7, and use the `DBMS_DATA_MINING.ADD_COST_MATRIX` procedure to add the cost matrix table to the model. You can also specify a cost matrix inline when invoking a `PREDICTION` function. [Table 29-1](about-attributes.md) has details for valid target data types.

**Related Topics**

- [Oracle Data Mining Concepts](classification.md)

### 31.3.2 Specifying Prior Probabilities

Prior probabilities can be used to offset differences in distribution between the build data and the actual population.

The `CLAS_PRIORS_TABLE_NAME` setting specifies the name of a table of prior probabilities to be used in building a Naive Bayes model. The priors table must have the columns shown in the following table.

Table 31-8 Priors Table Required Columns

| Column Name         | Data Type              |
|:--------------------|:-----------------------|
| `target_value`      | valid target data type |
| `prior_probability` | `NUMBER`               |

**Related Topics**

- [Target Attribute](about-attributes.md)
- [Oracle Data Mining Concepts](classification.md)

### 31.3.3 Specifying Class Weights

Specify class weights table settings in Logistic Regression or Support Vector Machine (SVM) Classification to favour higher weighted classes.

The `CLAS_WEIGHTS_TABLE_NAME` setting specifies the name of a table of class weights to be used to bias a logistic regression (Generalized Linear Model Classification) or SVM Classification model to favor higher weighted classes. The weights table must have the columns shown in the following table.

Table 31-9 Class Weights Table Required Columns

| Column Name    | Data Type              |
|:---------------|:-----------------------|
| `target_value` | valid target data type |
| `class_weight` | `NUMBER`               |

**Related Topics**

- [Target Attribute](about-attributes.md)
- [Oracle Data Mining Concepts](classification.md)

### 31.3.4 Model Settings in the Data Dictionary

Explains about `ALL/USER/DBA_MINING_MODEL_SETTINGS` in data dictionary view.

Information about mining model settings can be obtained from the data dictionary view `ALL/USER/DBA_MINING_MODEL_SETTINGS`. When used with the `ALL` prefix, this view returns information about the settings for the models accessible to the current user. When used with the `USER` prefix, it returns information about the settings for the models in the user's schema. The `DBA` prefix is only available for DBAs.

The columns of `ALL_MINING_MODEL_SETTINGS` are described as follows and explained in the following table.

    SQL> describe all_mining_model_settings
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     OWNER                                     NOT NULL VARCHAR2(30)
     MODEL_NAME                                NOT NULL VARCHAR2(30)
     SETTING_NAME                              NOT NULL VARCHAR2(30)
     SETTING_VALUE                                      VARCHAR2(4000)
     SETTING_TYPE                                       VARCHAR2(7)

Table 31-10 ALL_MINING_MODEL_SETTINGS

| Column          | Description                                                                              |
|:----------------|:-----------------------------------------------------------------------------------------|
| `owner`         | Owner of the mining model.                                                               |
| `model_name`    | Name of the mining model.                                                                |
| `setting_name`  | Name of the setting.                                                                     |
| `setting_value` | Value of the setting.                                                                    |
| `setting_type`  | `INPUT` if the value is specified by a user. `DEFAULT` if the value is system-generated. |

The following query lists the settings for the Support Vector Machine (SVM) Classification model `SVMC_SH_CLAS_SAMPLE`. The `ALGO_NAME`, `CLAS_WEIGHTS_TABLE_NAME`, and `SVMS_KERNEL_FUNCTION` settings are user-specified. These settings have been specified in a settings table for the model.

Example 31-2 ALL_MINING_MODEL_SETTINGS

    SQL> COLUMN setting_value FORMAT A35
    SQL> SELECT setting_name, setting_value, setting_type
                FROM all_mining_model_settings
                WHERE model_name in 'SVMC_SH_CLAS_SAMPLE';

    SETTING_NAME                   SETTING_VALUE                       SETTING
    ------------------------------ ----------------------------------- -------
    SVMS_ACTIVE_LEARNING           SVMS_AL_ENABLE                      DEFAULT
    PREP_AUTO                      OFF                                 DEFAULT
    SVMS_COMPLEXITY_FACTOR         0.244212                            DEFAULT
    SVMS_KERNEL_FUNCTION           SVMS_LINEAR                         INPUT
    CLAS_WEIGHTS_TABLE_NAME        svmc_sh_sample_class_wt             INPUT
    SVMS_CONV_TOLERANCE            .001                                DEFAULT
    ALGO_NAME                      ALGO_SUPPORT_VECTOR_MACHINES        INPUT

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](DBMS_DATA_MINING.md)

### 31.3.5 Specifying Mining Model Settings for R Model

The mining model settings for R model determine the characteristics of the model. You can specify the mining model settings in the `mining_model_table`.

You can build R models with the mining model settings by combining together generic settings that do not require an algorithm, such as `ODMS_PARTITION_COLUMNS` and `ODMS_SAMPLING`. The following settings are exclusive to R mining model, and they allow you to specify the R Mining model:

- ALGO_EXTENSIBLE_LANG

- RALG_BUILD_FUNCTION

- RALG_BUILD_PARAMETER

- RALG_DETAILS_FORMAT

- RALG_DETAILS_FUNCTION

- RALG_SCORE_FUNCTION

- RALG_WEIGHT_FUNCTION

**Related Topics**

- Registered R Scripts

#### 31.3.5.1 ALGO_EXTENSIBLE_LANG

Use the `ALGO_EXTENSIBLE_LANG` setting to specify the Oracle Data Mining framework with extensible algorithms.

Currently, `R` is the only valid value for `ALGO_EXTENSIBLE_LANG`. When the value for `ALGO_EXTENSIBLE_LANG` is set to R, the mining models are built using the R language. You can use the following settings in the `model_setting_table` to specify the build, score, and view of the R model.

- RALG_BUILD_FUNCTION

- RALG_BUILD_PARAMETER

- RALG_DETAILS_FUNCTION

- RALG_DETAILS_FORMAT

- RALG_SCORE_FUNCTION

- RALG_WEIGHT_FUNCTION

**Related Topics**

- Registered R Scripts

#### 31.3.5.2 RALG_BUILD_FUNCTION

Use the `RALG_BUILD_FUNCTION` to specify the name of an existing registered R script for R algorithm mining model build.

You must specify both `RALG_BUILD_FUNCTION` and `ALGO_EXTENSIBLE_LANG` in the `model_setting_table`. The R script defines an R function that has the first input argument of `data.frame` for training data, and it returns an R model object. The first data argument is mandatory. The `RALG_BUILD_FUNCTION` can accept additional model build parameters.

**Note:**

The valid inputs for input parameters are numeric and string scalar data types.

Example 31-3 Example of RALG_BUILD_FUNCTION

This example shows how to specify the name of the R script `MY_LM_BUILD_SCRIPT` that is used to build the model in the `model_setting_table.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_build_function,'MY_LM_BUILD_SCRIPT');
    End;
    /

The R script `MY_LM_BUILD_SCRIPT` defines an R function that builds the LM model. You must register the script `MY_LM_BUILD_SCRIPT` in the R script repository which uses the existing ORE security restrictions. You can use Oracle R Enterprise API `sys.rqScriptCreate` to register the script. Oracle R Enterprise requires the `RQADMIN` role to register R scripts.

For example:

    Begin
    sys.rqScriptCreate('MY_LM_BUILD_SCRIPT', 'function(data, formula, model.frame) {lm(formula = formula, data=data, model = as.logical(model.frame)}');
    End;
    /

For Clustering and Feature Extraction mining function model build, the R attributes `dm$nclus` and `dm$nfeat` must be set on the return R model to indicate the number of clusters and features respectively.

The R script `MY_KM_BUILD_SCRIPT` defines an R function that builds the k-Means model for Clustering. R attribute `dm$nclus` is set with the number of clusters for the return Clustering model.

    'function(dat) {dat.scaled <- scale(dat)
         set.seed(6543); mod <- list()
         fit <- kmeans(dat.scaled, centers = 3L)
         mod[[1L]] <- fit
         mod[[2L]] <- attr(dat.scaled, "scaled:center")
         mod[[3L]] <- attr(dat.scaled, "scaled:scale")
         attr(mod, "dm$nclus") <- nrow(fit$centers)
         mod}'

The R script `MY_PCA_BUILD_SCRIPT` defines an R function that builds the PCA model. R attribute `dm$nfeat` is set with the number of features for the return feature extraction model.

    'function(dat) {
         mod <- prcomp(dat, retx = FALSE)
         attr(mod, "dm$nfeat") <- ncol(mod$rotation)
         mod}'

**Related Topics**

- RALG_BUILD_PARAMETER
- Registered R Scripts

##### 31.3.5.2.1 RALG_BUILD_PARAMETER

The `RALG_BUILD_FUNCTION` input parameter specifies a list of numeric and string scalar values in SQL `SELECT` query statement format.

Example 31-4 Example of RALG_BUILD_PARAMETER

The `RALG_BUILD_FUNCTION` input parameters must be a list of numeric and string scalar values. The input parameters are optional.

The syntax of the parameter is:

    'SELECT value parameter name ...FROM dual'

This example shows how to specify a formula for the input argument `'formula'` and a numeric value zero for input argument `'model.frame'` using the `RALG_BUILD_PARAMETER`. These input arguments must match with the function signature of the R script used in `RALG_BUILD_FUNCTION` Parameter.

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_build_parameter, 'select ''AGE ~ .'' as "formula", 0 as "model.frame" from dual');
    End;
    /

**Related Topics**

- RALG_BUILD_FUNCTION

#### 31.3.5.3 RALG_DETAILS_FUNCTION

The `RALG_DETAILS_FUNCTION` specifies the R model metadata that is returned in the `data.frame.`

Use the `RALG_DETAILS_FUNCTION` to specify an existing registered R script that generates model information. The specified R script defines an R function that contains the first input argument for the R model object. The output of the R function must be a `data.frame`. The columns of the `data.frame` are defined by `RALG_DETAILS_FORMAT`, and can contain only numeric or string scalar types.

Example 31-5 Example of RALG_DETAILS_FUNCTION

This example shows how to specify the name of the R script `MY_LM_DETAILS_SCRIPT` in the `model_setting_table`. This script defines the R function that is used to provide the model information.

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_details_function, 'MY_LM_DETAILS_SCRIPT');
    End;
    /

In the R script repository, the script `MY_LM_DETAILS_SCRIPT` is registered as:

     'function(mod) data.frame(name=names(mod$coefficients),
        coef=mod$coefficients)'

**Related Topics**

- Registered R Scripts
- RALG_DETAILS_FORMAT

##### 31.3.5.3.1 RALG_DETAILS_FORMAT

Use the `RALG_DETAILS_FORMAT` parameter to specify the names and column types in the model view. It is a string that contains a `SELECT` query to specify a list of numeric and string scalar data types for the name and type of the model view columns.

When `RALG_DETAILS_FORMAT` and `RALG_DETAILS_FUNCTION` are both specified, a model view by the name `DM$VD` `<model_name>` is created along with an R model in the current schema. The first column of the model view is `PARTITION_NAME`. It has NULL value for non-partitioned models. The other columns of the model view are defined by `RALG_DETATLS_FORMAT.`

Example 31-6 Example of RALG_DETAILS_FORMAT

This example shows how to specify the name and type of the columns for the generated model view. The model view contains `varchar2` column `attr_name` and number column `coef_value` after the first column `partition_name.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_details_format, 'select cast(''a'' as varchar2(20)) as attr_name, 0 as coef_value from dual');
    End;
    /

**Related Topics**

- RALG_DETAILS_FUNCTION

#### 31.3.5.4 RALG_SCORE_FUNCTION

Use the `RALG_SCORE_FUNCTION` to specify an existing registered R script for R algorithm mining model score in the `mining_model_table.`

The specified R script defines an R function. The first input argument defines the model object. The second input argument defines the `data.frame` that is used for scoring data.

Example 31-7 Example of RALG_SCORE_FUNCTION

This example shows how the function takes the R model and scores the data in the `data.frame.` The argument object is the R Linear Model. The argument `newdata` contains scoring data in the `data.frame.`

    function(object, newdata) {res <- predict.lm(object, newdata = newdata, se.fit = TRUE); data.frame(fit=res$fit, se=res$se.fit, df=summary(object)$df[1L])}

In this example,

- `object` indicates the LM model

- `newdata` indicates the scoring data.frame

The output of the specified R function must be a `data.frame`. Each row represents the prediction for the corresponding scoring data from the input `data.frame`. The columns of the `data.frame` are specific to mining functions, such as:

**Regression:** A single numeric column for predicted target value, with two optional columns containing standard error of model fit, and the degrees of freedom number. The optional columns are needed for query function `PREDICTION_BOUNDS` to work.

Example 31-8 Example of RALG_SCORE_FUNCTION for Regression

This example shows how to specify the name of the R script `MY_LM_PREDICT_SCRIPT` that is used to score the model in the `model_setting_table.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_score_function, 'MY_LM_PREDICT_SCRIPT');
    End;
    /

In the R script repository, the script `MY_LM_PREDICT_SCRIPT` is registered as:

    function(object, newdata) {data.frame(pre = predict(object, newdata = newdata))}

**Classification:** Each column represents the predicted probability of one target class. The column name is the target class name.

Example 31-9 Example of RALG_SCORE_FUNCTION for Classification

This example shows how to specify the name of the R script `MY_LOGITGLM_PREDICT_SCRIPT` that is used to score the logit Classification model in the `model_setting_table.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_score_function, 'MY_LOGITGLM_PREDICT_SCRIPT');
    End;
    /

In the R script repository, `MY_LOGITGLM_PREDICT_SCRIPT` is registered as follows. It is a logit Classification with two target class "0" and "1".

    'function(object, newdata) {
       pred <- predict(object, newdata = newdata, type="response");
       res <- data.frame(1-pred, pred);
       names(res) <- c("0", "1");
       res}'

**Clustering:** Each column represents the predicted probability of one cluster. The columns are arranged in order of cluster ID. Each cluster is assigned a cluster ID, and they are consecutive values starting from 1. To support `CLUSTER_DISTANCE` in the R model, the output of R score function returns extra column containing the value of the distance to each cluster in order of cluster ID after the columns for the predicted probability.

Example 31-10 Example of RALG_SCORE_FUNCTION for Clustering

This example shows how to specify the name of the R script `MY_CLUSTER_PREDICT_SCRIPT` that is used to score the model in the `model_setting_table.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_score_function, 'MY_CLUSTER_PREDICT_SCRIPT');
    End;
    /

In the R script repository, the script `MY_CLUSTER_PREDICT_SCRIPT` is registered as:

    'function(object, dat){
         mod <- object[[1L]]; ce <- object[[2L]]; sc <- object[[3L]];
         newdata = scale(dat, center = ce, scale = sc);
         centers <- mod$centers;
         ss <- sapply(as.data.frame(t(centers)),
         function(v) rowSums(scale(newdata, center=v, scale=FALSE)^2));
         if (!is.matrix(ss)) ss <- matrix(ss, ncol=length(ss));
         disp <- -1 / (2* mod$tot.withinss/length(mod$cluster));
         distr <- exp(disp*ss);
         prob <- distr / rowSums(distr);
         as.data.frame(cbind(prob, sqrt(ss)))}'

This function fetches the centers of the clusters from the R model, and computes the probabilities for belonging to each cluster based on the distance of the score data to the corresponding cluster center.

**Feature Extraction:** Each column represents the coefficient value of one feature. The columns are arranged in order of feature ID. Each feature is assigned a feature ID, and they are consecutive values starting from 1.

Example 31-11 Example of RALG_SCORE_FUNCTION for Feature Extraction

This example shows how to specify the name of the R script `MY_FEATURE_EXTRACTION_SCRIPT` that is used to score the model in the `model_setting_table.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_score_function, 'MY_FEATURE_EXTRACTION_SCRIPT');
    End;
    /

In the R script repository, the script `MY_FEATURE_EXTRACTION_SCRIPT` is registered as:

     'function(object, dat) { as.data.frame(predict(object, dat)) }'

The function fetches the centers of the features from the R model, and computes the feature coefficient based on the distance of the score data to the corresponding feature center.

**Related Topics**

- Registered R Scripts

#### 31.3.5.5 RALG_WEIGHT_FUNCTION

Use the `RALG_WEIGHT_FUNCTION` to specify the name of an existing registered R script that computes weight or contribution for each attribute in scoring. The specified R script is used in the query function `PREDICTION_DETAILS` to evaluate attribute contribution.

The specified R script defines an R function containing the first input argument for model object, and the second input argument of `data.frame` for scoring data. When the mining function is Classification, Clustering, or Feature Extraction, the target class name or cluster ID or feature ID is passed by the third input argument to compute the weight for that particular class or cluster or feature. The script returns a `data.frame` containing the contributing weight for each attribute in a row. Each row corresponds to that input scoring `data.frame.`

Example 31-12 Example of RALG_WEIGHT_FUNCTION

This example shows how to specify the name of the R script `MY_PREDICT_WEIGHT_SCRIPT` that computes weight or contribution of R model attributes in the `model_setting_table.`

    Begin
    insert into model_setting_table values
    (dbms_data_mining.ralg_weight_function, 'MY_PREDICT_WEIGHT_SCRIPT');
    End;
    /

In the R script repository, the script `MY_PREDICT_WEIGHT_SCRIPT` for Regression is registered as:

    'function(mod, data) { coef(mod)[-1L]*data }'

In the R script repository, the script `MY_PREDICT_WEIGHT_SCRIPT` for logit Classification is registered as:

    'function(mod, dat, clas) {
       v <- predict(mod, newdata=dat, type = "response");
       v0 <- data.frame(v, 1-v); names(v0) <- c("0", "1");
       res <- data.frame(lapply(seq_along(dat),
       function(x, dat) {
       if(is.numeric(dat[[x]])) dat[,x] <- as.numeric(0)
       else dat[,x] <- as.factor(NA);
       vv <- predict(mod, newdata = dat, type = "response");
       vv = data.frame(vv, 1-vv); names(vv) <- c("0", "1");
       v0[[clas]] / vv[[clas]]}, dat = dat));
       names(res) <- names(dat);
       res}'

**Related Topics**

- Registered R Scripts

#### 31.3.5.6 Registered R Scripts

The `RALG_*_FUNCTION` must specify R scripts that exist in the R script repository. You can register the R scripts using Oracle R Enterprise.

The `RALG_*_FUNCTION` includes the following functions:

- RALG_BUILD_FUNCTION

- RALG_DETAILS_FUNCTION

- RALG_SCORE_FUNCTION

- RALG_WEIGHT_FUNCTION

**Note:**

The R scripts must exist in the R script repository for an R model to function.

You can register the R scripts through Oracle Enterprise R (ORE). To register R scripts, you must have the `RQADMIN` role. After an R model is built, the names of these specified R scripts become model settings. These R scripts must exist in the R script repository for an R model to remain functional.

You can manage the R memory that is used to build, score, and view the R models through Oracle Enterprise R as well.

#### 31.3.5.7 R Model Demonstration Scripts

You can access R model demonstration scripts under `rdbms/demo`

    dmraidemo.sql  dmrglmdemo.sql dmrpcademo.sql
    dmrardemo.sql  dmrkmdemo.sql  dmrrfdemo.sql
    dmrdtdemo.sql  dmrnndemo.sql
