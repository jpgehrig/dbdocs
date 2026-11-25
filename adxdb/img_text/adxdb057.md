This figure shows a data or document-type gradient, from highly structured data at the left to highly unstructured data at the right. This gradient is indicated by a color gradient from deep yellow at the left to pale yellow at the right. Superimposed on the color gradient are three document icons. From left to right, the content in those document icons looks less and less structured.

Below this data-structure gradient is a table that describes the three main use cases along this gradient. The table background color follows the gradient above the table: deep yellow at the left and pale yellow at the right, indicating that document structure decreases toward the right. The table has two column headings, Data-Centric on the left and Document-Centric on the right. Each column heading spans two columns. The table has four row headings, Use Case, Typical Data, Storage Model, and Indexing.

Row Use Case has these entries, from left to right:

- XML schema-based data, with little variation and little structural change over time

- Variable, free-form data, with some fixed embedded structures

- Variable, free-form data

Row Typical Data has these entries, from left to right:

- Employee record

- Technical article, with author, date, and title fields

- Web document or book chapter

Row Storage Model has the following entries. The first is under the column heading Data-Centric, and the second is under the column heading Document-Centric. The second entry thus covers the complete spectrum of document-centric data.

- Object-Relational

- Binary XML

Row Indexing has these entries, from left to right:

- B-tree index

- - `XMLIndex` index with structured and unstructured components

  - XML search index

- - `XMLIndex` index with unstructured component

  - XML search index
