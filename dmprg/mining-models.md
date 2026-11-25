Data mining models are database schema objects that perform data mining techniques.

As with all schema objects, access to data mining models is controlled by database privileges. Models can be exported and imported. They support comments and they can be tracked in the Oracle Database auditing system.

Data mining models are created by the `CREATE_MODEL` procedure in the `DBMS_DATA_MINING` PL/SQL package. Models are created for a specific data mining technique, and they use a specific algorithm to perform that function. **Machine learning function** is a term that refers to a class of data mining problems to be solved. Examples of data mining techniques are: regression, classification, attribute importance, clustering, anomaly detection, and feature selection. Oracle Data Mining supports one or more algorithms for each data mining technique.

Along with the data mining technique, in the `CREATE_MODEL` procedure you can specify a settings table to specify an algorithm and other characteristics of a model. Some settings are general, some are specific to a data mining technique, and some are specific to an algorithm.

**Note:**

Most types of data mining models can be used to score data. However, it is possible to score data without applying a model. Dynamic scoring and predictive analytics return scoring results without a user-supplied model. They create and apply transient models that are not visible to you.

**Related Topics**

- [Dynamic Scoring](dynamic-scoring.md)
- [DBMS_PREDICTIVE_ANALYTICS](data-mining-PL-SQL-packages.md)
- [Creating a Model](model-creation.md)
- [Administrative Tasks for Oracle Data Mining](administrative-tasks.md)
