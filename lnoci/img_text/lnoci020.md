# Description of the illustration lnoci020.eps

This illustration depicts the steps involved in processing SQL statements. This illustration shows six boxes stacked one above the other with downward connecting arrows from the box above to the box below. In addition an arrow from the bottom box returns to the third box and the same arrow returns to the top box The top box is labelled “prepare statements”, the second box is labelled “bind placeholders”, the third box is labelled “execute statement”, the fourth box is labelled “describe select-list items”, the fifth box is labelled “define output variables”, and the sixth and bottom box is labelled “fetch and process data”. Each box represents a processing step for processing SQL statements. Boxes representing Steps 2, 4, 5, and 6 are performed if necessary.

To the right of each box are the calls that can be used for each step. These include:

- For preparing a statement, you can call OCIStmtPrepare() or OCIStmtPrepare2().

- For binding placeholders, you can call OCIBindByName() or OCIBindByName2(), OCIBindByPos() or OCIBindByPos(), OCIBindObject(), OCIBindArrayOfStruct(), or OCIBindDynamic().

- For executing the statement, you can call OCIStmtExecute() or OCIStmtExecute2().

- For describing select-list items, you can call OCIParamGet() or OCIAttrGet().

- For defining output variables, you can call OCIDefineByPos() or OCIDefineByPos2(), OCIDefineObject(), OCIDefineArraytOfStruct(), or OCIDefineDynamic().

- For fetching and processing data, you can call OCIStmtFetch() or OCIStmtFetch2().
