Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SegY2SqlLdr.md)
- [Next Class](ShapefileReaderJGeom.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.util

## Class ShapefileFeatureJGeom

- java.lang.Object

- - oracle.spatial.util.ShapefileFeatureJGeom

<!-- -->

-

  ------------------------------------------------------------------------



      public class ShapefileFeatureJGeom
      extends java.lang.Object

  This class helps to create features from a shapefile.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `ShapefileFeatureJGeom``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type            | Method and Description                                                                                                                                                                                                                                                                                              |
    |------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.util.Hashtable` | `fromRecordToFeature``(`[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbf, `[`ShapefileReaderJGeom`](ShapefileReaderJGeom.md)` sfr, byte[] fieldTypes, int numFields, int row, int srid)`<br>Convert .dbf columns and .shp bytes into Feature instance.                                                                    |
    | `static java.util.Hashtable` | `fromRecordToFeature``(`[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbf, `[`ShapefileReaderJGeom`](ShapefileReaderJGeom.md)` sfr, java.lang.String[] fieldNames, int[] fieldIndexes, byte[] fieldTypes, int row, int srid)`<br>Convert .dbf columns and .shp bytes into Feature instance.                                |
    | `static java.lang.String`    | `getDimArray``(int shpDims, java.lang.String m_tolerance, java.lang.String min_x, java.lang.String max_x, java.lang.String min_y, java.lang.String max_y, double min_z, double max_z, double min_m, double max_m)`                                                                                                  |
    | `static java.lang.String[]`  | `getOraFieldNames``(`[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbf, byte[] fieldTypes, int numFields)`                                                                                                                                                                                                                 |
    | `static java.lang.String[]`  | `getOraFieldNames``(`[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbf, byte[] fieldTypes, int[] fieldIndexes)`                                                                                                                                                                                                            |
    | `static java.lang.String`    | `getRelSchema``(`[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbf)`                                                                                                                                                                                                                                                       |
    | `static java.lang.String`    | `getRelSchema``(`[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbf, java.lang.String gidName)`                                                                                                                                                                                                                             |
    | `static void`                | `insertFeatures``(OracleConnection conn, `[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbfr, `[`ShapefileReaderJGeom`](ShapefileReaderJGeom.md)` sfh, java.lang.String m_tableName, int m_commit_interval, int m_srid, java.lang.String dimArrayMig)`                                                                     |
    | `static void`                | `insertFeatures``(OracleConnection conn, `[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbfr, `[`ShapefileReaderJGeom`](ShapefileReaderJGeom.md)` sfh, java.lang.String m_tableName, java.lang.String m_idName, int m_start_id, int m_commit_interval, int m_println_interval, int m_srid, java.lang.String dimArrayMig)`  |
    | `static boolean`             | `isGeodetic``(OracleConnection conn, int m_srid)`                                                                                                                                                                                                                                                                   |
    | `static boolean`             | `isReservedWord``(OracleConnection conn, java.lang.String word, java.lang.String m_keyword_table)`                                                                                                                                                                                                                  |
    | `static boolean`             | `isReservedWord``(java.lang.String word)`<br>From jpaiva MapBuilder Returns if input word is an Oracle SQL reserved word or an ANSI reserved word.                                                                                                                                                                  |
    | `static void`                | `prepareTableForData``(OracleConnection conn, `[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbfr, java.lang.String m_tableName, java.lang.String m_idName, java.lang.String m_geom, int m_srid, java.lang.String dimArray)`                                                                                               |
    | `static void`                | `prepareTableForData``(OracleConnection conn, `[`DBFReaderJGeom`](DBFReaderJGeom.md)` dbfr, java.lang.String m_tableName, java.lang.String m_idName, java.lang.String m_geom, int m_srid, java.lang.String dimArray, java.lang.String m_keyword_table)`                                                             |
    | `static boolean`             | `validateMvalue``(`[`ShapefileReaderJGeom`](ShapefileReaderJGeom.md)` sfr, int srid)`                                                                                                                                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ShapefileFeatureJGeom

          public ShapefileFeatureJGeom()

  <!-- -->

  - ### Method Detail

    - #### isReservedWord

          public static boolean isReservedWord(java.lang.String word)

      From jpaiva MapBuilder Returns if input word is an Oracle SQL reserved word or an ANSI reserved word.
      Parameters:
      `word` -

      Returns:
      boolean

    <!-- -->

    - #### isReservedWord

          public static boolean isReservedWord(OracleConnection conn,
                                               java.lang.String word,
                                               java.lang.String m_keyword_table)

    <!-- -->

    - #### validateMvalue

          public static boolean validateMvalue(ShapefileReaderJGeom sfr,
                                               int srid)
                                        throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRelSchema

          public static java.lang.String getRelSchema(DBFReaderJGeom dbf)

    <!-- -->

    - #### getRelSchema

          public static java.lang.String getRelSchema(DBFReaderJGeom dbf,
                                                      java.lang.String gidName)

    <!-- -->

    - #### getOraFieldNames

          public static java.lang.String[] getOraFieldNames(DBFReaderJGeom dbf,
                                                            byte[] fieldTypes,
                                                            int numFields)
                                                     throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### getOraFieldNames

          public static java.lang.String[] getOraFieldNames(DBFReaderJGeom dbf,
                                                            byte[] fieldTypes,
                                                            int[] fieldIndexes)
                                                     throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### fromRecordToFeature

          public static java.util.Hashtable fromRecordToFeature(DBFReaderJGeom dbf,
                                                                ShapefileReaderJGeom sfr,
                                                                byte[] fieldTypes,
                                                                int numFields,
                                                                int row,
                                                                int srid)
                                                         throws java.io.IOException

      Convert .dbf columns and .shp bytes into Feature instance.
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### fromRecordToFeature

          public static java.util.Hashtable fromRecordToFeature(DBFReaderJGeom dbf,
                                                                ShapefileReaderJGeom sfr,
                                                                java.lang.String[] fieldNames,
                                                                int[] fieldIndexes,
                                                                byte[] fieldTypes,
                                                                int row,
                                                                int srid)
                                                         throws java.io.IOException

      Convert .dbf columns and .shp bytes into Feature instance.
      Parameters:
      `dbf` -

      `sfr` -

      `fieldNames` - attribute names to be processed (not necessarily all)

      `fieldIndexes` - attribute index position on original attribute list

      `fieldTypes` - attribute types

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### isGeodetic

          public static boolean isGeodetic(OracleConnection conn,
                                           int m_srid)
                                    throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDimArray

          public static java.lang.String getDimArray(int shpDims,
                                                     java.lang.String m_tolerance,
                                                     java.lang.String min_x,
                                                     java.lang.String max_x,
                                                     java.lang.String min_y,
                                                     java.lang.String max_y,
                                                     double min_z,
                                                     double max_z,
                                                     double min_m,
                                                     double max_m)

    <!-- -->

    - #### prepareTableForData

          public static void prepareTableForData(OracleConnection conn,
                                                 DBFReaderJGeom dbfr,
                                                 java.lang.String m_tableName,
                                                 java.lang.String m_idName,
                                                 java.lang.String m_geom,
                                                 int m_srid,
                                                 java.lang.String dimArray)
                                          throws java.io.IOException,
                                                 java.sql.SQLException

      Throws:
      `java.io.IOException`

      `java.sql.SQLException`

    <!-- -->

    - #### prepareTableForData

          public static void prepareTableForData(OracleConnection conn,
                                                 DBFReaderJGeom dbfr,
                                                 java.lang.String m_tableName,
                                                 java.lang.String m_idName,
                                                 java.lang.String m_geom,
                                                 int m_srid,
                                                 java.lang.String dimArray,
                                                 java.lang.String m_keyword_table)
                                          throws java.io.IOException,
                                                 java.sql.SQLException

      Throws:
      `java.io.IOException`

      `java.sql.SQLException`

    <!-- -->

    - #### insertFeatures

          public static void insertFeatures(OracleConnection conn,
                                            DBFReaderJGeom dbfr,
                                            ShapefileReaderJGeom sfh,
                                            java.lang.String m_tableName,
                                            java.lang.String m_idName,
                                            int m_start_id,
                                            int m_commit_interval,
                                            int m_println_interval,
                                            int m_srid,
                                            java.lang.String dimArrayMig)
                                     throws java.sql.SQLException,
                                            java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### insertFeatures

          public static void insertFeatures(OracleConnection conn,
                                            DBFReaderJGeom dbfr,
                                            ShapefileReaderJGeom sfh,
                                            java.lang.String m_tableName,
                                            int m_commit_interval,
                                            int m_srid,
                                            java.lang.String dimArrayMig)
                                     throws java.sql.SQLException,
                                            java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SegY2SqlLdr.md)
- [Next Class](ShapefileReaderJGeom.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
