Learn how to use Generalized Linear Models (GLM) statistical technique for Linear modeling.

Oracle Data Mining supports GLM for Regression and Binary Classification.

- About Generalized Linear Models

- GLM in Oracle Data Mining

- Scalable Feature Selection

- Tuning and Diagnostics for GLM

- GLM Solvers

- Data Preparation for GLM

- Linear Regression

- Logistic Regression

**Related Topics**

- [Regression](regression.md)
- [Classification](classification.md)

### 16.1 About Generalized Linear Models

Introduces Generalized Linear Models (GLM).

GLM include and extend the class of linear models.

Linear models make a set of restrictive assumptions, most importantly, that the target (dependent variable y) is normally distributed conditioned on the value of predictors with a constant variance regardless of the predicted response value. The advantage of linear models and their restrictions include computational simplicity, an interpretable model form, and the ability to compute certain diagnostic information about the quality of the fit.

Generalized linear models relax these restrictions, which are often violated in practice. For example, binary (yes/no or 0/1) responses do not have same variance across classes. Furthermore, the sum of terms in a linear model typically can have very large ranges encompassing very negative and very positive values. For the binary response example, we would like the response to be a probability in the range \[0,1\].

Generalized linear models accommodate responses that violate the linear model assumptions through two mechanisms: a link function and a variance function. The link function transforms the target range to potentially -infinity to +infinity so that the simple form of linear models can be maintained. The variance function expresses the variance as a function of the predicted response, thereby accommodating responses with non-constant variances (such as the binary responses).

Oracle Data Mining includes two of the most popular members of the GLM family of models with their most popular link and variance functions:

- **Linear regression** with the identity link and variance function equal to the constant 1 (constant variance over the range of response values).

- **Logistic regression** with the logit link and binomial variance functions.

**Related Topics**

- [Linear Regression](regression.md)
- Linear Regression
- Logistic Regression

### 16.2 GLM in Oracle Data Mining

Generalized Linear Models (GLM) is a parametric modeling technique. Parametric models make assumptions about the distribution of the data. When the assumptions are met, parametric models can be more efficient than non-parametric models.

The challenge in developing models of this type involves assessing the extent to which the assumptions are met. For this reason, quality diagnostics are key to developing quality parametric models.

#### 16.2.1 Interpretability and Transparency

Learn how to interpret, and understand data transparency through model details and global details.

Oracle Data Mining Generalized Linear Models (GLM) are easy to interpret. Each model build generates many statistics and diagnostics. Transparency is also a key feature: model details describe key characteristics of the coefficients, and global details provide high-level statistics.

**Related Topics**

- Tuning and Diagnostics for GLM

#### 16.2.2 Wide Data

Oracle Data Mining Generalized Linear Model (GLM) is uniquely suited for handling wide data. The algorithm can build and score quality models that use a virtually limitless number of predictors (attributes). The only constraints are those imposed by system resources.

#### 16.2.3 Confidence Bounds

Predict confidence bounds through Generalized Linear Models (GLM).

GLM have the ability to predict confidence bounds. In addition to predicting a best estimate and a probability (Classification only) for each row, GLM identifies an interval wherein the prediction (Regression) or probability (Classification) lies. The width of the interval depends upon the precision of the model and a user-specified confidence level.

The confidence level is a measure of how sure the model is that the true value lies within a confidence interval computed by the model. A popular choice for confidence level is 95%. For example, a model might predict that an employee's income is \$125K, and that you can be 95% sure that it lies between \$90K and \$160K. Oracle Data Mining supports 95% confidence by default, but that value can be configured.

**Note:**

Confidence bounds are returned with the coefficient statistics. You can also use the `PREDICTION_BOUNDS` SQL function to obtain the confidence bounds of a model prediction.

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/PREDICTION_BOUNDS.md)

#### 16.2.4 Ridge Regression

Understand the use of Ridge regression for singularity (exact multicollinearity) in data.

The best regression models are those in which the predictors correlate highly with the target, but there is very little correlation between the predictors themselves. **Multicollinearity** is the term used to describe multivariate regression with correlated predictors.

**Ridge regression** is a technique that compensates for multicollinearity. Oracle Data Mining supports ridge regression for both Regression and Classification mining functions. The algorithm automatically uses ridge if it detects singularity (exact multicollinearity) in the data.

Information about singularity is returned in the global model details.

**Related Topics**

- Global Model Statistics for Linear Regression
- Global Model Statistics for Logistic Regression

##### 16.2.4.1 Configuring Ridge Regression

Configure Ridge Regression through build settings.

You can choose to explicitly enable ridge regression by specifying a build setting for the model. If you explicitly enable ridge, you can use the system-generated ridge parameter or you can supply your own. If ridge is used automatically, the ridge parameter is also calculated automatically.

The configuration choices are summarized as follows:

- Whether or not to override the automatic choice made by the algorithm regarding ridge regression

- The value of the ridge parameter, used only if you specifically enable ridge regression.

**Related Topics**

- [Oracle Database SQL Language Reference](../arpls/DBMS_DATA_MINING.md)

##### 16.2.4.2 Ridge and Confidence Bounds

Models built with Ridge Regression do not support confidence bounds.

**Related Topics**

- Confidence Bounds

##### 16.2.4.3 Ridge and Data Preparation

Learn about preparing data for Ridge Regression.

When Ridge Regression is enabled, different data preparation is likely to produce different results in terms of model coefficients and diagnostics. Oracle recommends that you enable Automatic Data Preparation for Generalized Linear Models, especially when Ridge Regression is used.

**Related Topics**

- Data Preparation for GLM

### 16.3 Scalable Feature Selection

Oracle Data Mining supports a highly scalable and automated version of feature selection and generation for Generalized Linear Models. This capability can enhance the performance of the algorithm and improve accuracy and interpretability. Feature selection and generation are available for both Linear Regression and binary Logistic Regression.

#### 16.3.1 Feature Selection

Feature selection is the process of choosing the terms to be included in the model. The fewer terms in the model, the easier it is for human beings to interpret its meaning. In addition, some columns may not be relevant to the value that the model is trying to predict. Removing such columns can enhance model accuracy.

##### 16.3.1.1 Configuring Feature Selection

Feature selection is a build setting for Generalized Linear Models. It is not enabled by default. When configured for feature selection, the algorithm automatically determines appropriate default behavior, but the following configuration options are available:

- The feature selection criteria can be AIC, SBIC, RIC, or α-investing. When the feature selection criteria is α-investing, feature acceptance can be either strict or relaxed.

- The maximum number of features can be specified.

- Features can be pruned in the final model. Pruning is based on t-statistics for linear regression or wald statistics for logistic regression.

##### 16.3.1.2 Feature Selection and Ridge Regression

Feature selection and ridge regression are mutually exclusive. When feature selection is enabled, the algorithm can not use ridge.

**Note:**

If you configure the model to use both feature selection and ridge regression, then you get an error.

#### 16.3.2 Feature Generation

Feature generation is the process of adding transformations of terms into the model. Feature generation enhances the power of models to fit more complex relationships between target and predictors.

##### 16.3.2.1 Configuring Feature Generation

Learn about configuring Feature Generation.

Feature generation is only possible when feature selection is enabled. Feature generation is a build setting. By default, feature generation is not enabled.

The feature generation method can be either quadratic or cubic. By default, the algorithm chooses the appropriate method. You can also explicitly specify the feature generation method.

The following options for feature selection also affect feature generation:

- Maximum number of features

- Model pruning

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

### 16.4 Tuning and Diagnostics for GLM

The process of developing a Generalized Linear Model typically involves a number of model builds. Each build generates many statistics that you can evaluate to determine the quality of your model. Depending on these diagnostics, you may want to try changing the model settings or making other modifications.

#### 16.4.1 Build Settings

Specify the build settings for Generalized Linear Model (GLM).

You can use specify build settings.

Additional build settings are available to:

- Control the use of ridge regression.

- Specify the handling of missing values in the training data.

- Specify the target value to be used as a reference in a logistic regression model.

**Related Topics**

- Ridge Regression
- Data Preparation for GLM
- Logistic Regression
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)

#### 16.4.2 Diagnostics

Generalized Linear Models generate many metrics to help you evaluate the quality of the model.

##### 16.4.2.1 Coefficient Statistics

Learn about coeffficient statistics for Linear and Logistic Regression.

The same set of statistics is returned for both linear and logistic regression, but statistics that do not apply to the mining function are returned as NULL.

Coefficient statistics are returned by the Model Detail Views for Generalized Linear Model.

**Related Topics**

- Coefficient Statistics for Linear Regression
- Coefficient Statistics for Logistic Regression
- [Oracle Data Mining User’s Guide](../dmprg/model-detail-views.md)

##### 16.4.2.2 Global Model Statistics

Learn about high-level statistics describing the model.

Separate high-level statistics describing the model as a whole, are returned for linear and logistic regression. When ridge regression is enabled, fewer global details are returned.

Global statistics are returned by the Model Detail Views for Generalized Linear Model.

**Related Topics**

- Global Model Statistics for Linear Regression
- Global Model Statistics for Logistic Regression
- Ridge Regression
- [Oracle Data Mining User’s Guide](../dmprg/model-detail-views.md)

##### 16.4.2.3 Row Diagnostics

Generate row-statistics by configuring Generalized Linear Models (GLM).

GLM to generate per-row statistics by specifying the name of a diagnostics table in the build setting `GLMS_DIAGNOSTICS_TABLE_NAME`.

GLM requires a case ID to generate row diagnostics. If you provide the name of a diagnostic table but the data does not include a case ID column, an exception is raised.

**Related Topics**

- Row Diagnostics for Linear Regression
- Row Diagnostics for Logistic Regression

### 16.5 GLM Solvers

Learn about the different solvers for Generalized Liner Models (GLM).

The GLM algorithm supports four different solvers: Cholesky, QR, Stochastic Gradient Descent (SGD),and Alternating Direction Method of Multipliers (ADMM) (on top of L-BFGS). The Cholesky and QR solvers employ classical decomposition approaches. The Cholesky solver is faster compared to the QR solver but less stable numerically. The QR solver handles better rank deficient problems without the help of regularization.

The SGD and ADMM (on top of L-BFGS) solvers are best suited for large scale data. The SGD solver employs the stochastic gradient descent optimization algorithm while ADMM (on top of L-BFGS) uses the Broyden-Fletcher-Goldfarb-Shanno optimization algorithm within an Alternating Direction Method of Multipliers framework. The SGD solver is fast but is sensitive to parameters and requires suitable scaled data to achieve good convergence. The L-BFGS algorithm solves unconstrained optimization problems and is more stable and robust than SGD. Also, L-BFGS uses ADMM in conjunction, which, results in an efficient distributed optimization approach with low communication cost.

**Related Topics**

- [DBMS_DATA_MINING - Algorithm Settings: Neural Network](../arpls/DBMS_DATA_MINING.md)
- [DBMS_DATA_MINING — Algorithm Settings: Generalized Linear Models](../arpls/DBMS_DATA_MINING.md)
- [DBMS_DATA_MINING — Algorithm Settings: ADMM](../arpls/DBMS_DATA_MINING.md)
- [DBMS_DATA_MINING — Algorithm Settings: LBFGS](../arpls/DBMS_DATA_MINING.md)

### 16.6 Data Preparation for GLM

Learn about preparing data for Generalized Linear Models (GLM).

Automatic Data Preparation (ADP) implements suitable data transformations for both linear and logistic regression.

**Note:**

Oracle recommends that you use Automatic Data Preparation with GLM.

**Related Topics**

- [Oracle Data Mining User’s Guide](automatic-data-preparation.md)

#### 16.6.1 Data Preparation for Linear Regression

Learn about Automatic Data Preparation (ADP) for Generalized Linear Model (GLM).

When Automatic Data Preparation (ADP) is enabled, the algorithm chooses a transformation based on input data properties and other settings. The transformation can include one or more of the following for numerical data: subtracting the mean, scaling by the standard deviation, or performing a correlation transformation (Neter, et. al, 1990). If the correlation transformation is applied to numeric data, it is also applied to categorical attributes.

Prior to standardization, categorical attributes are exploded into N-1 columns where N is the attribute cardinality. The most frequent value (mode) is omitted during the explosion transformation. In the case of highest frequency ties, the attribute values are sorted alpha-numerically in ascending order, and the first value on the list is omitted during the explosion. This explosion transformation occurs whether or not ADP is enabled.

In the case of high cardinality categorical attributes, the described transformations (explosion followed by standardization) can increase the build data size because the resulting data representation is dense. To reduce memory, disk space, and processing requirements, use an alternative approach. Under these circumstances, the VIF statistic must be used with caution.

**Related Topics**

- Ridge and Data Preparation
- [Oracle Data Mining User’s Guide](../dmprg/transforming-data.md)

**See Also:**

- Neter, J., Wasserman, W., and Kutner, M.H., "Applied Statistical Models", Richard D. Irwin, Inc., Burr Ridge, IL, 1990.

#### 16.6.2 Data Preparation for Logistic Regression

Categorical attributes are exploded into N-1 columns where N is the attribute cardinality. The most frequent value (mode) is omitted during the explosion transformation. In the case of highest frequency ties, the attribute values are sorted alpha-numerically in ascending order and the first value on the list is omitted during the explosion. This explosion transformation occurs whether or not Automatic Data Preparation (ADP) is enabled.

When ADP is enabled, numerical attributes are scaled by the standard deviation. This measure of variability is computed as the standard deviation per attribute with respect to the origin (not the mean) (Marquardt, 1980).

**See Also:**

Marquardt, D.W., "A Critique of Some Ridge Regression Methods: Comment", Journal of the American Statistical Association, Vol. 75, No. 369 , 1980, pp. 87-91.

#### 16.6.3 Missing Values

When building or applying a model, Oracle Data Mining automatically replaces missing values of numerical attributes with the mean and missing values of categorical attributes with the mode.

You can configure a Generalized Linear Models to override the default treatment of missing values. With the `ODMS_MISSING_VALUE_TREATMENT` setting, you can cause the algorithm to delete rows in the training data that have missing values instead of replacing them with the mean or the mode. However, when the model is applied, Oracle Data Mining performs the usual mean/mode missing value replacement. As a result, it is possible that the statistics generated from scoring does not match the statistics generated from building the model.

If you want to delete rows with missing values in the scoring the model, you must perform the transformation explicitly. To make build and apply statistics match, you must remove the rows with NULLs from the scoring data before performing the apply operation. You can do this by creating a view.

    CREATE VIEW viewname AS SELECT * from tablename
         WHERE column_name1 is NOT NULL
         AND   column_name2 is NOT NULL
         AND   column_name3 is NOT NULL .....

**Note:**

In Oracle Data Mining, missing values in nested data indicate sparsity, not values missing at random.

The value `ODMS_MISSING_VALUE_DELETE_ROW` is only valid for tables without nested columns. If this value is used with nested data, an exception is raised.

### 16.7 Linear Regression

Linear regression is the Generalized Linear Models’ Regression algorithm supported by Oracle Data Mining. The algorithm assumes no target transformation and constant variance over the range of target values.

#### 16.7.1 Coefficient Statistics for Linear Regression

Generalized Linear Model Regression models generate the following coefficient statistics:

- Linear coefficient estimate

- Standard error of the coefficient estimate

- t-value of the coefficient estimate

- Probability of the t-value

- Variance Inflation Factor (VIF)

- Standardized estimate of the coefficient

- Lower and upper confidence bounds of the coefficient

#### 16.7.2 Global Model Statistics for Linear Regression

Generalized Linear Model Regression models generate the following statistics that describe the model as a whole:

- Model degrees of freedom

- Model sum of squares

- Model mean square

- Model F statistic

- Model F value probability

- Error degrees of freedom

- Error sum of squares

- Error mean square

- Corrected total degrees of freedom

- Corrected total sum of squares

- Root mean square error

- Dependent mean

- Coefficient of variation

- R-Square

- Adjusted R-Square

- Akaike's information criterion

- Schwarz's Baysian information criterion

- Estimated mean square error of the prediction

- Hocking Sp statistic

- JP statistic (the final prediction error)

- Number of parameters (the number of coefficients, including the intercept)

- Number of rows

- Whether or not the model converged

- Whether or not a covariance matrix was computed

#### 16.7.3 Row Diagnostics for Linear Regression

For Linear Regression, the diagnostics table has the columns described in the following table. All the columns are `NUMBER`, except the `CASE_ID` column, which preserves the type from the training data.

Table 16-1 Diagnostics Table for GLM Regression Models

| Column                 | Description                                     |
|:-----------------------|:------------------------------------------------|
| `CASE_ID`              | Value of the case ID column                     |
| `TARGET_VALUE`         | Value of the target column                      |
| `PREDICTED_VALUE`      | Value predicted by the model for the target     |
| `HAT`                  | Value of the diagonal element of the hat matrix |
| `RESIDUAL`             | Measure of error                                |
| `STD_ERR_RESIDUAL`     | Standard error of the residual                  |
| `STUDENTIZED_RESIDUAL` | Studentized residual                            |
| `PRED_RES`             | Predicted residual                              |
| `COOKS_D`              | Cook's D influence statistic                    |

### 16.8 Logistic Regression

Binary Logistic Regression is the Generalized Linear Model Classification algorithm supported by Oracle Data Mining. The algorithm uses the logit link function and the binomial variance function.

#### 16.8.1 Reference Class

You can use the build setting `GLMS_REFERENCE_CLASS_NAME` to specify the target value to be used as a reference in a binary logistic regression model. Probabilities are produced for the other (non-reference) class. By default, the algorithm chooses the value with the highest prevalence. If there are ties, the attributes are sorted alpha-numerically in an ascending order.

#### 16.8.2 Class Weights

You can use the build setting `CLAS_WEIGHTS_TABLE_NAME` to specify the name of a class weights table. Class weights influence the weighting of target classes during the model build.

#### 16.8.3 Coefficient Statistics for Logistic Regression

Generalized Linear Model Classification models generate the following coefficient statistics:

- Name of the predictor

- Coefficient estimate

- Standard error of the coefficient estimate

- Wald chi-square value of the coefficient estimate

- Probability of the Wald chi-square value

- Standardized estimate of the coefficient

- Lower and upper confidence bounds of the coefficient

- Exponentiated coefficient

- Exponentiated coefficient for the upper and lower confidence bounds of the coefficient

#### 16.8.4 Global Model Statistics for Logistic Regression

Generalized Linear Model Classification models generate the following statistics that describe the model as a whole:

- Akaike's criterion for the fit of the intercept only model

- Akaike's criterion for the fit of the intercept and the covariates (predictors) model

- Schwarz's criterion for the fit of the intercept only model

- Schwarz's criterion for the fit of the intercept and the covariates (predictors) model

- -2 log likelihood of the intercept only model

- -2 log likelihood of the model

- Likelihood ratio degrees of freedom

- Likelihood ratio chi-square probability value

- Pseudo R-square Cox an Snell

- Pseudo R-square Nagelkerke

- Dependent mean

- Percent of correct predictions

- Percent of incorrect predictions

- Percent of ties (probability for two cases is the same)

- Number of parameters (the number of coefficients, including the intercept)

- Number of rows

- Whether or not the model converged

- Whether or not a covariance matrix was computed.

#### 16.8.5 Row Diagnostics for Logistic Regression

For Logistic Regression, the diagnostics table has the columns described in the following table. All the columns are `NUMBER`, except the `CASE_ID` and `TARGET_VALUE` columns, which preserve the type from the training data.

Table 16-2 Row Diagnostics Table for Logistic Regression

| Column              | Description                                                               |
|:--------------------|:--------------------------------------------------------------------------|
| `CASE_ID`           | Value of the case ID column                                               |
| `TARGET_VALUE`      | Value of the target value                                                 |
| `TARGET_VALUE_PROB` | Probability associated with the target value                              |
| `HAT`               | Value of the diagonal element of the hat matrix                           |
| `WORKING_RESIDUAL`  | Residual with respect to the adjusted dependent variable                  |
| `PEARSON_RESIDUAL`  | The raw residual scaled by the estimated standard deviation of the target |
| `DEVIANCE_RESIDUAL` | Contribution to the overall goodness of fit of the model                  |
| `C`                 | Confidence interval displacement diagnostic                               |
| `CBAR`              | Confidence interval displacement diagnostic                               |
| `DIFDEV`            | Change in the deviance due to deleting an individual observation          |
| `DIFCHISQ`          | Change in the Pearson chi-square                                          |
