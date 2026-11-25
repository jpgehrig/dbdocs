The model details view for text features is `DM$VX`model_name.

The text feature view `DM$VX``model_name` describes the extracted text features if there are text attributes present. The view has the following schema:

    Name                                Type
     --------------            ---------------------
     PARTITION_NAME                     VARCHAR2(128)
     COLUMN_NAME                        VARCHAR2(128)
     TOKEN                              VARCHAR2(4000)
     DOCUMENT_FREQUENCY                 NUMBER

Table 33-1 Text Feature View for Extracted Text Features

| Column Name          | Description                                             |
|:---------------------|:--------------------------------------------------------|
| `PARTITION_NAME`     | A partition in a partitioned model to retrieve details  |
| `COLUMN_NAME`        | Name of the identifier column                           |
| `TOKEN`              | Text token which is usually a word or stemmed word      |
| `DOCUMENT_FREQUENCY` | A measure of token frequency in the entire training set |
