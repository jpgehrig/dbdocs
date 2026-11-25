You can learn a great deal about the Oracle Data Mining application programming interface (API) from the data mining sample programs. The programs illustrate typical approaches to data preparation, algorithm selection, algorithm tuning, testing, and scoring.

The programs are easy to use. They include extensive inline comments to help you understand the code. They delete all temporary objects on exit; you can run the programs repeatedly without setup or cleanup.

The data mining sample programs are installed with Oracle Database Examples in the demo directory under Oracle Home. The demo directory contains sample programs that illustrate many features of Oracle Database. You can locate the data mining files by doing a directory listing of `dm*.sql`. The following example shows this directory listing on a Linux system.

Note that the directory listing in the following example includes one file, `dmhpdemo.sql`, that is not a data mining program.

Example 35-1 Directory Listing of the Data Mining Sample Programs

    > cd $ORACLE_HOME/rdbms/demo
    > ls dm*.sql
    dmaidemo.sql      dmkmdemo.sql    dmsvddemo.sql
    dmardemo.sql      dmnbdemo.sql    dmsvodem.sql
    dmdtdemo.sql      dmnmdemo.sql    dmsvrdem.sql
    dmdtxvlddemo.sql  dmocdemo.sql    dmtxtnmf.sql
    dmemdemo.sql      dmsh.sql        dmtxtsvm.sql
    dmglcdem.sql      dmshgrants.sql
    dmglrdem.sql      dmstardemo.sql
    dmhpdemo.sql      dmsvcdem.sql

The data mining sample programs create a set of mining models in the user's schema. After executing the programs, you can list the models with a query like the one in the following example.

Example 35-2 Models Created by the Sample Programs

    SELECT mining_function, algorithm, model_name FROM user_mining_models
        ORDER BY mining_function;

    MINING_FUNCTION                ALGORITHM                      MODEL_NAME
    ------------------------------ ------------------------------ -------------------
    ASSOCIATION_RULES              APRIORI_ASSOCIATION_RULES      AR_SH_SAMPLE
    CLASSIFICATION                 GENERALIZED_LINEAR_MODEL       GLMC_SH_CLAS_SAMPLE
    CLASSIFICATION                 SUPPORT_VECTOR_MACHINES        T_SVM_CLAS_SAMPLE
    CLASSIFICATION                 SUPPORT_VECTOR_MACHINES        SVMC_SH_CLAS_SAMPLE
    CLASSIFICATION                 SUPPORT_VECTOR_MACHINES        SVMO_SH_CLAS_SAMPLE
    CLASSIFICATION                 NAIVE_BAYES                    NB_SH_CLAS_SAMPLE
    CLASSIFICATION                 DECISION_TREE                  DT_SH_CLAS_SAMPLE
    CLUSTERING                     EXPECTATION_MAXIMIZATION       EM_SH_CLUS_SAMPLE
    CLUSTERING                     O_CLUSTER                      OC_SH_CLUS_SAMPLE
    CLUSTERING                     KMEANS                         KM_SH_CLUS_SAMPLE
    CLUSTERING                     KMEANS                         DM_STAR_CLUSTER
    FEATURE_EXTRACTION             SINGULAR_VALUE_DECOMP          SVD_SH_SAMPLE
    FEATURE_EXTRACTION             NONNEGATIVE_MATRIX_FACTOR      NMF_SH_SAMPLE
    FEATURE_EXTRACTION             NONNEGATIVE_MATRIX_FACTOR      T_NMF_SAMPLE
    REGRESSION                     SUPPORT_VECTOR_MACHINES        SVMR_SH_REGR_SAMPLE
    REGRESSION                     GENERALIZED_LINEAR_MODEL       GLMR_SH_REGR_SAMPLE
