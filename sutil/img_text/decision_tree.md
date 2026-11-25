# Description of the illustration decision_tree.eps

This image shows a flow chart that is designed to help you decide on the type of LogMiner dictionary to use. The flow chart indicates that if your answer to each of the following questions is yes, then you should use the LogMiner dictionary in the online catalog:

- Will LogMiner have access to the source database?

- Will column definitions will be unchanged?

- Will the database be open?

If your answer to the first or second of the preceding questions is no, then the flow chart poses these questions:

- Will the database be open for write access?

- Might column definitions change?

If your answer to both of these question is yes, then the flow chart indicates that you should use the dictionary in the redo log files. If the answer to either of these questions is no, or if the answer to the question "Will the database be open" is no, then the flow chart poses this question:

Will the instance be started?

If the answer to this question is yes, then you should use the dictionary extracted to a flat file.

If the answer to this question is no, then you cannot use LogMiner.
