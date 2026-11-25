## 22 SDO_CS Package (Coordinate System Transformation)

The MDSYS.SDO_CS package contains subprograms for working with coordinate systems.

You can perform explicit coordinate transformations on a single geometry or an entire layer of geometries (that is, all geometries in a specified column in a table).

To use the subprograms in this chapter, you must understand the conceptual information about coordinate systems in [Coordinate System](spatial-concepts.md) and [Coordinate Systems (Spatial Reference Systems)](coordinate-systems-concepts.md).

The rest of this chapter provides reference information on the subprograms, listed in alphabetical order.

- SDO_CS.ADD_PREFERENCE_FOR_OP
- SDO_CS.CONVERT_3D_SRID_TO_2D
- SDO_CS.CONVERT_NADCON_TO_XML
- SDO_CS.CONVERT_NTV2_TO_XML
- SDO_CS.CONVERT_XML_TO_NADCON
- SDO_CS.CONVERT_XML_TO_NTV2
- SDO_CS.CREATE_CONCATENATED_OP
- SDO_CS.CREATE_OBVIOUS_EPSG_RULES
- SDO_CS.CREATE_PREF_CONCATENATED_OP
- SDO_CS.DELETE_ALL_EPSG_RULES
- SDO_CS.DELETE_OP
- SDO_CS.DETERMINE_CHAIN
- SDO_CS.DETERMINE_DEFAULT_CHAIN
- SDO_CS.FIND_GEOG_CRS
- SDO_CS.FIND_PROJ_CRS
- SDO_CS.FIND_SRID
- SDO_CS.FROM_GEOHASH
- SDO_CS.FROM_OGC_SIMPLEFEATURE_SRS
- SDO_CS.FROM_USNG
- SDO_CS.GENERATE_SCRIPT_FROM_SRID
- SDO_CS.GET_EPSG_DATA_VERSION
- SDO_CS.GET_GEOHASH_CELL_HEIGHT
- SDO_CS.GET_GEOHASH_CELL_WIDTH
- SDO_CS.LOAD_EPSG_MATRIX
- SDO_CS.MAKE_2D
- SDO_CS.MAKE_3D
- SDO_CS.MAP_EPSG_SRID_TO_ORACLE
- SDO_CS.MAP_ORACLE_SRID_TO_EPSG
- SDO_CS.REVOKE_PREFERENCE_FOR_OP
- SDO_CS.TO_GEOHASH
- SDO_CS.TO_OGC_SIMPLEFEATURE_SRS
- SDO_CS.TO_USNG
- SDO_CS.TRANSFORM
- SDO_CS.TRANSFORM_LAYER
- SDO_CS.UPDATE_WKTS_FOR_ALL_EPSG_CRS
- SDO_CS.UPDATE_WKTS_FOR_EPSG_CRS
- SDO_CS.UPDATE_WKTS_FOR_EPSG_DATUM
- SDO_CS.UPDATE_WKTS_FOR_EPSG_ELLIPS
- SDO_CS.UPDATE_WKTS_FOR_EPSG_OP
- SDO_CS.UPDATE_WKTS_FOR_EPSG_PARAM
- SDO_CS.UPDATE_WKTS_FOR_EPSG_PM
- SDO_CS.VALIDATE_EPSG_MATRIX
- SDO_CS.VALIDATE_WKT

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 22.1 SDO_CS.ADD_PREFERENCE_FOR_OP

#### Format

    SDO_CS.ADD_PREFERENCE_FOR_OP(
         op_id       IN NUMBER,
         source_crs  IN NUMBER DEFAULT NULL,
         target_crs  IN NUMBER DEFAULT NULL,
         use_case    IN VARCHAR2 DEFAULT NULL);

#### Description

Adds a preference for an operation between a source coordinate system and a target coordinate system.

#### Parameters

op_id
ID number of the operation. Must be a value in the COORD_OP_ID column of the SDO_COORD_OPS table (described in [SDO_COORD_OPS Table](coordinate-systems-concepts.md)).

source_crs
The SRID of the source coordinate reference system. Must be null or a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

target_crs
The SRID of the target coordinate reference system. Must be null or a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

use_case
Name of the use case to be associated with this preference. Must be null or a value from the USE_CASE column of the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

#### Usage Notes

If `use_case` is null, the transformation plan associated with the operation is a systemwide preference, and a row is added (or two rows are added if a reverse operation exists) to the SDO_PREFERRED_OPS_SYSTEM table (described in [SDO_PREFERRED_OPS_SYSTEM Table](coordinate-systems-concepts.md)). If `use_case` is not null, the transformation plan associated with the operation is a preference associated with the specified use case, and a row is added (or two rows are added if a reverse operation exists) to the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

To create a concatenated operation and make it preferred either systemwide or for a specified use case, you can use the SDO_CS.CREATE_PREF_CONCATENATED_OP convenience procedure.

To revoke a preference for an operation between a source coordinate system and a target coordinate system, use the SDO_CS.REVOKE_PREFERENCE_FOR_OP procedure.

#### Examples

The following example adds a preference for operation 19977 to be used in transformations from SRID 4301 to SRID 4326 when use case use_case_B is specified for the transformation.

    EXECUTE SDO_CS.ADD_PREFERENCE_FOR_OP(19977, 4301, 4326, 'use_case_B');

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.2 SDO_CS.CONVERT_3D_SRID_TO_2D

#### Format

    SDO_CS.CONVERT_3D_SRID_TO_2D(
         srid3d  IN NUMBER) RETURN NUMBER;

#### Description

Converts a three-dimensional SRID value into a two-dimensional SRID value.

#### Parameters

srid_3d
The SRID of a three-dimensional coordinate reference system. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

**Note:**

SDO_CS.CONVERT_3D_SRID_TO_2D function is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

This function returns the SRID value of a functionally equivalent two-dimensional coordinate reference system that corresponds to the input coordinate reference system.

- If a compound 3D SRID is input, there is only one corresponding two-dimensional SRID, and it is returned.

- If a Geographic 3D SRID is input, there may be multiple possible corresponding two-dimensional SRIDs, and one of them is returned.

- If a two-dimensional SRID is input, it is returned.

For information about three-dimensional coordinate reference system support, see [Three-Dimensional Coordinate Reference System Support](coordinate-systems-concepts.md).

#### Examples

The following example returns an equivalent two-dimensional SRID for each coordinate reference system listed in the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)). For 2D SRID values in that table, the function returns the existing value.

    SELECT
        crs.srid "nD SRID",
        crs.coord_ref_sys_kind "nD Type",
        sdo_cs.convert_3d_srid_to_2d(crs.srid) "2D SRID",
        (SELECT
            coord_ref_sys_kind
          FROM
            sdo_coord_ref_sys crs2
          WHERE
            crs2.srid = sdo_cs.convert_3d_srid_to_2d(crs.srid)
        ) "2D Type"
      FROM sdo_coord_ref_sys crs
      ORDER BY crs.coord_ref_sys_kind,crs.srid;

       nD SRID nD Type                     2D SRID 2D Type
    ---------- ------------------------ ---------- ------------------------
          4097 COMPOUND                       4093 PROJECTED
          4098 COMPOUND                       4094 PROJECTED
          4099 COMPOUND                       4095 PROJECTED
          …    …                              …    …
          7400 COMPOUND                       4807 GEOGRAPHIC2D
          …    …                              …    …
          5800 ENGINEERING                    5800 ENGINEERING
          …    …                              …    …
          4000 GEOCENTRIC
          …    …                              …    …
          4326 GEOGRAPHIC2D                   4326 GEOGRAPHIC2D
          …    …                              …    …
          4327 GEOGRAPHIC3D                   4326 GEOGRAPHIC2D
          …    …                              …    …
         27700 PROJECTED                     27700 PROJECTED
          …    …                              …    …
          3855 VERTICAL                       3855 VERTICAL
          …    …                              …    …

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.3 SDO_CS.CONVERT_NADCON_TO_XML

#### Format

    SDO_CS.CONVERT_NADCON_TO_XML(
         laa_clob  IN CLOB,
         loa_clob  IN CLOB,
         xml_grid  OUT XMLTYPE );

#### Description

Converts a NADCON (North American Datum Conversion) grid in ASCII format to an Oracle Spatial and Graph XML representation.

#### Parameters

laa_clob
Latitude values of the NADCON grid in a CLOB object.

loa_clob
Longitude values of the NADCON grid in a CLOB object.

xml_grid
Output XML document containing the Oracle Spatial and Graph XML representation of the NADCON grid.

#### Usage Notes

To convert an Oracle Spatial and Graph XML representation to a NADCON grid, use the SDO_CS.CONVERT_XML_TO_NADCON procedure.

#### Examples

The following example converts a NADCON grid in ASCII format to an Oracle Spatial and Graph XML representation, converts the resulting XML representation back to a NADCON ASCII representation, and displays the resulting ASCII representation. (Only part of the output is shown.)

    set lines 32000
    set long 2000000000

    DECLARE
      laa       CLOB;
      loa       CLOB;
      xml       XMLTYPE;
      laa_file  BFILE;
      loa_file  BFILE;
    BEGIN
      laa_file := BFILENAME('MY_WORK_DIR', 'samplenadcon.laa');
      loa_file := BFILENAME('MY_WORK_DIR', 'samplenadcon.loa');
      DBMS_LOB.OPEN(laa_file, DBMS_LOB.LOB_READONLY);
      DBMS_LOB.OPEN(loa_file, DBMS_LOB.LOB_READONLY);

      DBMS_LOB.CREATETEMPORARY(laa, TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(loa, TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.OPEN(laa, DBMS_LOB.LOB_READWRITE);
      DBMS_LOB.OPEN(loa, DBMS_LOB.LOB_READWRITE);
      DBMS_LOB.LOADFROMFILE(laa, laa_file, DBMS_LOB.LOBMAXSIZE);
      DBMS_LOB.LOADFROMFILE(loa, loa_file, DBMS_LOB.LOBMAXSIZE);
      DBMS_LOB.CLOSE(laa);
      DBMS_LOB.CLOSE(loa);
      DBMS_LOB.CLOSE(laa_file);
      DBMS_LOB.CLOSE(loa_file);

      SDO_CS.convert_NADCON_to_XML(laa, loa, xml);
      SDO_CS.convert_XML_to_NADCON(xml, laa, loa);
      DBMS_OUTPUT.PUT_LINE(SUBSTR(laa, 1, 32000));
      DBMS_OUTPUT.PUT_LINE(SUBSTR(loa, 1, 32000));
    END;
    /
    NADCON EXTRACTED REGION                                 NADGRD
      33  49   1  -107.00000      .25000    25.00000      .25000      .00000
         .006731     .006444     .006208     .006036     .005935     .005904
         .005932     .006002     .006092     .006174     .006218     .006198
         .006087     .005867     .005522     .005045     .004432     .003688
         .002818     .001836     .000759    -.000385    -.001559    -.002704
    . . .
    NADCON EXTRACTED REGION                                 NADGRD
      33  49   1  -107.00000      .25000    25.00000      .25000      .00000
         .008509     .007147     .005756     .004331     .002879     .001410
        -.000060    -.001507    -.002904    -.004222    -.005431    -.006498
        -.007395    -.008095    -.008579    -.008832    -.008848    -.008632
        -.008200    -.007577    -.006800    -.005911    -.004957    -.003974
    . . .

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.4 SDO_CS.CONVERT_NTV2_TO_XML

#### Format

    SDO_CS.CONVERT_NTV2_TO_XML(
         ntv2_clob IN CLOB,
         xml_grid  OUT XMLTYPE );

#### Description

Converts an NTv2 (National Transformation Version 2) grid in ASCII format to an Oracle Spatial and Graph XML representation.

#### Parameters

ntv2_clob
NTv2 grid values in a CLOB object.

xml_grid
Output XML document containing the Oracle Spatial and Graph XML representation of the NTv2 grid.

#### Usage Notes

To convert an Oracle Spatial and Graph XML representation to an NTv2 grid, use the SDO_CS.CONVERT_XML_TO_NTV2 procedure.

#### Examples

The following example converts an NTv2 grid in ASCII format to an Oracle Spatial and Graph XML representation, converts the resulting XML representation back to an NTv2 ASCII representation, and displays the resulting ASCII representation. (Only part of the output is shown.)

    set lines 32000
    set long 2000000000

    DECLARE
      ntv2      CLOB;
      xml       XMLTYPE;
      ntv2_file BFILE;
    BEGIN
      ntv2_file := BFILENAME('MY_WORK_DIR', 'samplentv2.gsa');
      DBMS_LOB.OPEN(ntv2_file, DBMS_LOB.LOB_READONLY);

      DBMS_LOB.CREATETEMPORARY(ntv2, TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.OPEN(ntv2, DBMS_LOB.LOB_READWRITE);
      DBMS_LOB.LOADFROMFILE(ntv2, ntv2_file, DBMS_LOB.LOBMAXSIZE);
      DBMS_LOB.CLOSE(ntv2);
      DBMS_LOB.CLOSE(ntv2_file);

      SDO_CS.convert_NTv2_to_XML(ntv2, xml);
      SDO_CS.convert_XML_to_NTv2(xml, ntv2);
      DBMS_OUTPUT.PUT_LINE(SUBSTR(ntv2, 1, 32000));
    END;
    /
    NUM_OREC 11
    NUM_SREC 11
    NUM_FILE  2
    GS_TYPE SECONDS
    VERSION NTv2.0
    DATUM_F NAD27
    DATUM_T NAD83
    MAJOR_F  6378206.400
    MINOR_F  6356583.800
    MAJOR_T  6378137.000
    MINOR_T  6356752.314
    SUB_NAMEALbanff
    PARENT  NONE
    CREATED 95-06-29
    UPDATED 95-07-04
    S_LAT     183900.000000
    N_LAT     184500.000000
    E_LONG    415800.000000
    W_LONG    416100.000000
    LAT_INC       30.000000
    LONG_INC      30.000000
    GS_COUNT   231
      0.084020  3.737300  0.005000  0.008000
      0.083029  3.738740  0.017000  0.011000
      0.082038  3.740180  0.029000  0.015000
    . . .

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.5 SDO_CS.CONVERT_XML_TO_NADCON

#### Format

    SDO_CS.CONVERT_XML_TO_NADCON(
         xml_grid  IN XMLTYPE,
         laa_clob  OUT CLOB,
         loa_clob  OUT CLOB);

#### Description

Converts an Oracle Spatial and Graph XML representation of a NADCON (North American Datum Conversion) grid to NADCON ASCII format.

#### Parameters

xml_grid
XML document containing the Oracle Spatial and Graph XML representation of the NADCON grid.

laa_clob
Output CLOB object containing the latitude values of the NADCON grid.

loa_clob
Output CLOB object containing the longitude values of the NADCON grid.

#### Usage Notes

To convert a NADCON grid in ASCII format to an Oracle Spatial and Graph XML representation, use the SDO_CS.CONVERT_NADCON_TO_XML procedure.

#### Examples

The following example converts a NADCON grid in ASCII format to an Oracle Spatial and Graph XML representation, converts the resulting XML representation back to a NADCON ASCII representation, and displays the resulting ASCII representation. (Only part of the output is shown.)

    set lines 32000
    set long 2000000000

    DECLARE
      laa       CLOB;
      loa       CLOB;
      xml       XMLTYPE;
      laa_file  BFILE;
      loa_file  BFILE;
    BEGIN
      laa_file := BFILENAME('MY_WORK_DIR', 'samplenadcon.laa');
      loa_file := BFILENAME('MY_WORK_DIR', 'samplenadcon.loa');
      DBMS_LOB.OPEN(laa_file, DBMS_LOB.LOB_READONLY);
      DBMS_LOB.OPEN(loa_file, DBMS_LOB.LOB_READONLY);

      DBMS_LOB.CREATETEMPORARY(laa, TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(loa, TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.OPEN(laa, DBMS_LOB.LOB_READWRITE);
      DBMS_LOB.OPEN(loa, DBMS_LOB.LOB_READWRITE);
      DBMS_LOB.LOADFROMFILE(laa, laa_file, DBMS_LOB.LOBMAXSIZE);
      DBMS_LOB.LOADFROMFILE(loa, loa_file, DBMS_LOB.LOBMAXSIZE);
      DBMS_LOB.CLOSE(laa);
      DBMS_LOB.CLOSE(loa);
      DBMS_LOB.CLOSE(laa_file);
      DBMS_LOB.CLOSE(loa_file);

      SDO_CS.convert_NADCON_to_XML(laa, loa, xml);
      SDO_CS.convert_XML_to_NADCON(xml, laa, loa);
      DBMS_OUTPUT.PUT_LINE(SUBSTR(laa, 1, 32000));
      DBMS_OUTPUT.PUT_LINE(SUBSTR(loa, 1, 32000));
    END;
    /
    NADCON EXTRACTED REGION                                 NADGRD
      33  49   1  -107.00000      .25000    25.00000      .25000      .00000
         .006731     .006444     .006208     .006036     .005935     .005904
         .005932     .006002     .006092     .006174     .006218     .006198
         .006087     .005867     .005522     .005045     .004432     .003688
         .002818     .001836     .000759    -.000385    -.001559    -.002704
    . . .
    NADCON EXTRACTED REGION                                 NADGRD
      33  49   1  -107.00000      .25000    25.00000      .25000      .00000
         .008509     .007147     .005756     .004331     .002879     .001410
        -.000060    -.001507    -.002904    -.004222    -.005431    -.006498
        -.007395    -.008095    -.008579    -.008832    -.008848    -.008632
        -.008200    -.007577    -.006800    -.005911    -.004957    -.003974
    . . .

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.6 SDO_CS.CONVERT_XML_TO_NTV2

#### Format

    SDO_CS.CONVERT_XML_TO_NTV2(
         xml_grid  IN XMLTYPE,
         ntv2_clob OUT CLOB);

#### Description

Converts an Oracle Spatial and Graph XML representation of an NTv2 (National Transformation Version 2) grid to NTv2 ASCII format.

#### Parameters

xml_grid
XML document containing the Oracle Spatial and Graph XML representation of the NTv2 grid.

ntv2_clob
Output CLOB object containing the values for the NTv2 grid.

#### Usage Notes

To convert an NTv2 grid in ASCII format to an Oracle Spatial and Graph XML representation, use the SDO_CS.CONVERT_NTV2_TO_XML procedure.

#### Examples

The following example converts an NTv2 grid in ASCII format to an Oracle Spatial and Graph XML representation, converts the resulting XML representation back to an NTv2 ASCII representation, and displays the resulting ASCII representation. (Only part of the output is shown.)

    set lines 32000
    set long 2000000000

    DECLARE
      ntv2      CLOB;
      xml       XMLTYPE;
      ntv2_file BFILE;
    BEGIN
      ntv2_file := BFILENAME('MY_WORK_DIR', 'samplentv2.gsa');
      DBMS_LOB.OPEN(ntv2_file, DBMS_LOB.LOB_READONLY);

      DBMS_LOB.CREATETEMPORARY(ntv2, TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.OPEN(ntv2, DBMS_LOB.LOB_READWRITE);
      DBMS_LOB.LOADFROMFILE(ntv2, ntv2_file, DBMS_LOB.LOBMAXSIZE);
      DBMS_LOB.CLOSE(ntv2);
      DBMS_LOB.CLOSE(ntv2_file);

      SDO_CS.convert_NTv2_to_XML(ntv2, xml);
      SDO_CS.convert_XML_to_NTv2(xml, ntv2);
      DBMS_OUTPUT.PUT_LINE(SUBSTR(ntv2, 1, 32000));
    END;
    /
    NUM_OREC 11
    NUM_SREC 11
    NUM_FILE  2
    GS_TYPE SECONDS
    VERSION NTv2.0
    DATUM_F NAD27
    DATUM_T NAD83
    MAJOR_F  6378206.400
    MINOR_F  6356583.800
    MAJOR_T  6378137.000
    MINOR_T  6356752.314
    SUB_NAMEALbanff
    PARENT  NONE
    CREATED 95-06-29
    UPDATED 95-07-04
    S_LAT     183900.000000
    N_LAT     184500.000000
    E_LONG    415800.000000
    W_LONG    416100.000000
    LAT_INC       30.000000
    LONG_INC      30.000000
    GS_COUNT   231
      0.084020  3.737300  0.005000  0.008000
      0.083029  3.738740  0.017000  0.011000
      0.082038  3.740180  0.029000  0.015000
    . . .

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.7 SDO_CS.CREATE_CONCATENATED_OP

#### Format

    SDO_CS.CREATE_CONCATENATED_OP(
         op_id    IN NUMBER,
         op_name  IN VARCHAR2,
         use_plan IN TFM_PLAN);

#### Description

Creates a concatenated operation.

#### Parameters

op_id
ID number of the concatenated operation.

op_name
Name to be associated with the concatenated operation.

use_plan
Transformation plan. The TFM_PLAN object type is explained in [TFM_PLAN Object Type](coordinate-systems-concepts.md).

#### Usage Notes

A concatenated operation is the concatenation (chaining) of two or more atomic operations.

To create a concatenated operation and make it preferred either systemwide or for a specified use case, you can use the SDO_CS.CREATE_PREF_CONCATENATED_OP convenience procedure.

#### Examples

The following example creates a concatenation operation with the operation ID 2999 and the name `CONCATENATED_OPERATION_2999`.

    DECLARE
    BEGIN
    SDO_CS.CREATE_CONCATENATED_OP(
      2999,
      'CONCATENATED_OPERATION_2999',
      TFM_PLAN(SDO_TFM_CHAIN(4242, 19910, 24200, 1000000000, 24200)));
    END;
    /

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.8 SDO_CS.CREATE_OBVIOUS_EPSG_RULES

#### Format

    SDO_CS.CREATE_OBVIOUS_EPSG_RULES(
         use_case  IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a basic set of EPSG rules to be applied in certain transformations.

#### Parameters

use_case
Name of the use case to be associated with the application of the EPSG rules that are created. Must be a value from the USE_CASE column of the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

#### Usage Notes

This procedure creates rules to implement the main EPSG-defined transformations between specific coordinate reference systems. For transformations between some coordinate reference systems, EPSG has specified rules that should be applied. For any given transformation from one coordinate reference system to another, the EPSG rule might be different from the default Oracle Spatial and Graph rule. If you execute this procedure, the EPSG rules are applied in any such cases. If you do not execute this procedure, the default Spatial and Graph rules are used in such cases.

This procedure inserts many rows into the SDO_PREFERRED_OPS_SYSTEM table (see [SDO_PREFERRED_OPS_SYSTEM Table](coordinate-systems-concepts.md)).

To delete the EPSG rules created by this procedure, and thus cause the default Spatial and Graph rules to be used in all cases, use the SDO_CS.DELETE_ALL_EPSG_RULES procedure.

#### Examples

The following example creates a basic set of EPSG rules to be applied in certain transformations.

    EXECUTE SDO_CS.CREATE_OBVIOUS_EPSG_RULES;

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.9 SDO_CS.CREATE_PREF_CONCATENATED_OP

#### Format

    SDO_CS.CREATE_PREF_CONCATENATED_OP(
         op_id    IN NUMBER,
         op_name  IN VARCHAR2,
         use_plan IN TFM_PLAN,
         use_case IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a concatenated operation, associating it with a transformation plan and making it preferred either systemwide or for a specified use case.

#### Parameters

op_id
ID number of the concatenated operation to be created.

op_name
Name to be associated with the concatenated operation.

use_plan
Transformation plan. The TFM_PLAN object type is explained in [TFM_PLAN Object Type](coordinate-systems-concepts.md).

use_case
Use case to which this preferred concatenated operation applies. Must be a null or a value from the USE_CASE column of the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

#### Usage Notes

This convenience procedure combines the operations of the SDO_CS.CREATE_CONCATENATED_OP and SDO_CS.ADD_PREFERENCE_FOR_OP procedures.

A concatenated operation is the concatenation (chaining) of two or more atomic operations.

If `use_case` is null, the transformation plan associated with the operation is a systemwide preference, and a row is added (or two rows are added if a reverse operation exists) to the SDO_PREFERRED_OPS_SYSTEM table (described in [SDO_PREFERRED_OPS_SYSTEM Table](coordinate-systems-concepts.md)). If `use_case` is not null, the transformation plan associated with the operation is a preference associated with the specified use case, and a row is added (or two rows are added if a reverse operation exists) to the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

To create a concatenation without making it preferred either systemwide or for a specified use case, use the SDO_CS.CREATE_CONCATENATED_OP procedure

To delete a concatenated operation, use the SDO_CS.DELETE_OP procedure.

#### Examples

The following example creates a concatenation operation with the operation ID 300 and the name `MY_CONCATENATION_OPERATION`, and causes Spatial and Graph to use the specified transformation plan in all cases (because `use_case` is null) when this operation is used.

    DECLARE
    BEGIN
    SDO_CS.CREATE_PREF_CONCATENATED_OP(
      300,
      'MY_CONCATENATED_OPERATION',
      TFM_PLAN(SDO_TFM_CHAIN(4242, 19910, 24200, 1000000000, 24200)),
      NULL);
    END;
    /

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.10 SDO_CS.DELETE_ALL_EPSG_RULES

#### Format

    SDO_CS.DELETE_ALL_EPSG_RULES(
         use_case  IN VARCHAR2 DEFAULT NULL);

#### Description

Deletes the basic set of EPSG rules to be applied in certain transformations.

#### Parameters

use_case
Name of the use case to be associated with the application of the EPSG rules that are created. Must match the value that was used for the `use_case` parameter value (either null or a specified value) when the SDO_CS.CREATE_OBVIOUS_EPSG_RULES procedure was called.

#### Usage Notes

This procedure deletes the EPSG rules that were previously created by the SDO_CS.CREATE_OBVIOUS_EPSG_RULES procedure, and thus causes the default Spatial and Graph rules to be used in all cases. (See the Usage Notes for the SDO_CS.CREATE_OBVIOUS_EPSG_RULES procedure for more information.)

If `use_case` is null, this procedure deletes all rows from the SDO_PREFERRED_OPS_SYSTEM table (see [SDO_PREFERRED_OPS_SYSTEM Table](coordinate-systems-concepts.md)). If `use_case` is not null, this procedure deletes the rows associated with the specified use case from the SDO_PREFERRED_OPS_USER table (see [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

#### Examples

The following example deletes the basic set of EPSG rules to be applied in certain transformations.

    EXECUTE SDO_CS.DELETE_ALL_EPSG_RULES;

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.11 SDO_CS.DELETE_OP

#### Format

    SDO_CS.DELETE_OP(
         op_id  IN NUMBER);

#### Description

Deletes a concatenated operation.

#### Parameters

op_id
ID number of the operation to be deleted.

#### Usage Notes

To create a concatenated operation and make it preferred systemwide or only for a specified use case, use the SDO_CS.CREATE_CONCATENATED_OP procedure.

#### Examples

The following example deletes the operation with the ID number 300.

    EXECUTE SDO_CS.DELETE_OP(300);

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.12 SDO_CS.DETERMINE_CHAIN

#### Format

    SDO_CS.DETERMINE_CHAIN(
         transient_rule_set IN SDO_TRANSIENT_RULE_SET,
         use_case           IN VARCHAR2,
         source_srid        IN NUMBER,
         target_srid        IN NUMBER) RETURN TFM_PLAN;

#### Description

Returns the query chain, based on the system rule set, to be used in transformations from one coordinate reference system to another coordinate reference system.

#### Parameters

transient_rule_set
Rule set to be used for the transformation. If you specify a null value, the Oracle system rule set is used.

use_case
Use case for which to determine the query chain. Must be a null value or a value from the USE_CASE column of the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

source_srid
The SRID of the source coordinate reference system. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

target_srid
The SRID of the target coordinate reference system. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

This function returns an object of type TFM_PLAN, which is explained in [TFM_PLAN Object Type](coordinate-systems-concepts.md).

The `transient_rule_set` parameter is of type SDO_TRANSIENT_RULE_SET, which has the following definition:

    CREATE TYPE sdo_transient_rule_set AS OBJECT (
      source_srid  NUMBER,
      target_srid  NUMBER,
      tfm          NUMBER);

#### Examples

The following example returns the query chain based on the system rule set.

    SELECT MDSYS.SDO_CS.DETERMINE_CHAIN(NULL, NULL, 4804, 4257) FROM DUAL;

    MDSYS.SDO_CS.DETERMINE_CHAIN(NULL,NULL,4804,4257)(THE_PLAN)
    --------------------------------------------------------------------------------
    TFM_PLAN(SDO_TFM_CHAIN(4804, -2, 4257))

The next example creates a preferred concatenated operation (with operation ID 300) with a specified chain for transformations from SRID 4804 to SRID 4257, and then calls the DETERMINE_CHAIN function, returning a different result. (The operation created in this example is not meaningful or useful, and it was created only for illustration.)

    CALL SDO_CS.CREATE_PREF_CONCATENATED_OP(
        300,
        'CONCATENATED OPERATION',
        TFM_PLAN(
          SDO_TFM_CHAIN(
                        4804,
            1000000001, 4804,
            1000000002, 4804,
            1000000001, 4804,
            1000000001, 4804,
            1000000002, 4804,
            1000000002, 4804,
            1000000001, 4804,
            1000000001, 4804,
            1000000001, 4804,
            1000000002, 4804,
            1000000002, 4804,
            1000000002, 4257)),
        NULL);

    SELECT MDSYS.SDO_CS.DETERMINE_CHAIN(NULL, NULL, 4804, 4257) FROM DUAL;

    MDSYS.SDO_CS.DETERMINE_CHAIN(NULL,NULL,4804,4257)(THE_PLAN)
    --------------------------------------------------------------------------------
    TFM_PLAN(SDO_TFM_CHAIN(4804, 300, 4257))

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.13 SDO_CS.DETERMINE_DEFAULT_CHAIN

#### Format

    SDO_CS.DETERMINE_DEFAULT_CHAIN(
         source_srid  IN NUMBER,
         target_srid  IN NUMBER) RETURN SDO_SRID_CHAIN;

#### Description

Returns the default chain of SRID values in transformations from one coordinate reference system to another coordinate reference system.

#### Parameters

source_srid
The SRID of the source coordinate reference system. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

target_srid
The SRID of the target coordinate reference system. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

This function returns an object of type SDO_SRID_CHAIN, which is defined as `VARRAY(1048576) OF NUMBER`.

#### Examples

The following example returns the default chain of SRID values in transformations from SRID 4804 to SRID 4257.

    SELECT MDSYS.SDO_CS.DETERMINE_DEFAULT_CHAIN(4804, 4257) FROM DUAL;

    MDSYS.SDO_CS.DETERMINE_DEFAULT_CHAIN(4804,4257)
    --------------------------------------------------------------------------------
    SDO_SRID_CHAIN(NULL, 4804, 4257, NULL)

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.14 SDO_CS.FIND_GEOG_CRS

#### Format

    SDO_CS.FIND_GEOG_CRS(
         reference_srid  IN NUMBER,
         is_legacy       IN VARCHAR2,
         max_rel_num_difference IN NUMBER DEFAULT 0.000001) RETURN SDO_SRID_LIST;

#### Description

Returns the SRID values of geodetic (geographic) coordinate reference systems that have the same well-known text (WKT) numeric values as the coordinate reference system with the specified reference SRID value.

#### Parameters

reference_srid
The SRID of the coordinate reference system for which to find all other geodetic coordinate reference systems that have the same WKT numeric values. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

is_legacy
`TRUE` limits the results to geodetic coordinate reference systems for which the IS_LEGACY column value is `TRUE` in the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)); `FALSE` limits the results to geodetic coordinate reference systems for which the IS_LEGACY column value is `FALSE` in the SDO_COORD_REF_SYS table. If you specify a null value for this parameter, the IS_LEGACY column value in the SDO_COORD_REF_SYS table is ignored in determining the results.

max_rel_num_difference
A numeric value indicating how closely WKT values must match in order for a projected coordinate reference system to be considered a match. The default value is 0.000001. The value for each numeric WKT item is compared with its corresponding value in the WKT for the reference SRID or in the specified list of parameters to this function; and if the difference in all cases is less than or equal to the `max_rel_num_difference` value, the SRID for that coordinate reference system is included in the results.

#### Usage Notes

This function returns an object of type SDO_SRID_LIST, which is defined as `VARRAY(1048576) OF NUMBER`.

The well-known text (WKT) format is described in [Well-Known Text (WKT)](coordinate-systems-concepts.md).

#### Examples

The following examples show the effect of the `is_legacy` parameter value on the results. The first example returns the SRID values of all geodetic legacy coordinate reference systems that have the same WKT numeric values as the coordinate reference system with the SRID value of 8307.

    SELECT SDO_CS.FIND_GEOG_CRS(
      8307,
      'TRUE') FROM DUAL;

    SDO_CS.FIND_GEOG_CRS(8307,'TRUE')
    --------------------------------------------------------------------------------
    SDO_SRID_LIST(8192, 8265, 8307, 8311, 8320, 524288, 2000002, 2000006, 2000012, 2
    000015, 2000023, 2000028)

The next example returns the SRID values of all geodetic non-legacy coordinate reference systems that have the same WKT numeric values as the coordinate reference system with the SRID value of 8307.

    SELECT SDO_CS.FIND_GEOG_CRS(
      8307,
      'FALSE') FROM DUAL;

    SDO_CS.FIND_GEOG_CRS(8307,'FALSE')
    --------------------------------------------------------------------------------
    SDO_SRID_LIST(4019, 4030, 4031, 4032, 4033, 4041, 4121, 4122, 4126, 4130, 4133,
    4140, 4141, 4148, 4151, 4152, 4163, 4166, 4167, 4170, 4171, 4172, 4173, 4176, 41
    80, 4189, 4190, 4258, 4269, 4283, 4318, 4319, 4326, 4610, 4612, 4617, 4619, 4624
    , 4627, 4640, 4659, 4661, 4667, 4669, 4670)

The next example returns the SRID values of all geodetic coordinate reference systems (legacy and non-legacy) that have the same WKT numeric values as the coordinate reference system with the SRID value of 8307.

    SELECT SDO_CS.FIND_GEOG_CRS(
      8307,
      NULL) FROM DUAL;

    SDO_CS.FIND_GEOG_CRS(8307,NULL)
    --------------------------------------------------------------------------------
    SDO_SRID_LIST(4019, 4030, 4031, 4032, 4033, 4041, 4121, 4122, 4126, 4130, 4133,
    4140, 4141, 4148, 4151, 4152, 4163, 4166, 4167, 4170, 4171, 4172, 4173, 4176, 41
    80, 4189, 4190, 4258, 4269, 4283, 4318, 4319, 4326, 4610, 4612, 4617, 4619, 4624
    , 4627, 4640, 4659, 4661, 4667, 4669, 4670, 8192, 8265, 8307, 8311, 8320, 524288
    , 2000002, 2000006, 2000012, 2000015, 2000023, 2000028)

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.15 SDO_CS.FIND_PROJ_CRS

#### Format

    SDO_CS.FIND_PROJ_CRS(
         reference_srid          IN NUMBER,
         is_legacy               IN VARCHAR2,
         max_rel_num_difference  IN NUMBER DEFAULT 0.000001) RETURN SDO_SRID_LIST;

#### Description

Returns the SRID values of projected coordinate reference systems that have the same well-known text (WKT) numeric values as the coordinate reference system with the specified reference SRID value.

#### Parameters

reference_srid
The SRID of the coordinate reference system for which to find all other projected coordinate reference systems that have the same WKT numeric values. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

is_legacy
`TRUE` limits the results to projected coordinate reference systems for which the IS_LEGACY column value is `TRUE` in the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)); `FALSE` limits the results to projected coordinate reference systems for which the IS_LEGACY column value is `FALSE` in the SDO_COORD_REF_SYS table. If you specify a null value for this parameter, the IS_LEGACY column value in the SDO_COORD_REF_SYS table is ignored in determining the results.

max_rel_num_difference
A numeric value indicating how closely WKT values must match in order for a coordinate reference system to be considered a match. The default value is 0.000001. The value for each numeric WKT item is compared with its corresponding value in the WKT for the reference SRID or in the specified list of parameters to this function; and if the difference in all cases is less than or equal to the `max_rel_num_difference` value, the SRID for that coordinate reference system is included in the results.

#### Usage Notes

This function returns an object of type SDO_SRID_LIST, which is defined as `VARRAY(1048576) OF NUMBER`.

The well-known text (WKT) format is described in [Well-Known Text (WKT)](coordinate-systems-concepts.md).

#### Examples

The following examples show the effect of the `is_legacy` parameter value on the results. The first example returns the SRID values of all projected legacy coordinate reference systems that have the same WKT numeric values as the coordinate reference system with the SRID value of 2007. The returned result list is empty, because there are no legacy projected legacy coordinate reference systems that meet the search criteria.

    SELECT SDO_CS.FIND_PROJ_CRS(
      2007,
      'TRUE') FROM DUAL;

    SDO_CS.FIND_PROJ_CRS(2007,'TRUE')
    --------------------------------------------------------------------------------
    SDO_SRID_LIST()

The next example returns the SRID values of all projected non-legacy coordinate reference systems that have the same WKT numeric values as the coordinate reference system with the SRID value of 2007.

    SELECT SDO_CS.FIND_PROJ_CRS(
      2007,
      'FALSE') FROM DUAL;

    SDO_CS.FIND_PROJ_CRS(2007,'FALSE')
    --------------------------------------------------------------------------------
    SDO_SRID_LIST(2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007, 21291)

The next example returns the SRID values of all projected coordinate reference systems (legacy and non-legacy) that have the same WKT numeric values as the coordinate reference system with the SRID value of 2007. The returned result list is the same as for the preceding example.

    SELECT SDO_CS.FIND_PROJ_CRS(
      2007,
      NULL) FROM DUAL;

    SDO_CS.FIND_PROJ_CRS(2007,NULL)
    --------------------------------------------------------------------------------
    SDO_SRID_LIST(2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007, 21291)

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.16 SDO_CS.FIND_SRID

#### Format

    SDO_CS.FIND_SRID(
         srid               OUT NUMBER,
         epsg_srid_geog     IN NUMBER DEFAULT NULL,
         epsg_srid_proj     IN NUMBER DEFAULT NULL,
         datum_id           IN NUMBER DEFAULT NULL,
         pm_id              IN NUMBER DEFAULT NULL,
         proj_method_id     IN NUMBER DEFAULT NULL,
         coord_ref_sys_kind IN VARCHAR2 DEFAULT NULL,
         semi_major_axis    IN NUMBER DEFAULT NULL,
         semi_minor_axis    IN NUMBER DEFAULT NULL,
         inv_flattening     IN NUMBER DEFAULT NULL,
         params             IN EPSG_PARAMS DEFAULT NULL);

or

    SDO_CS.FIND_SRID(
         srid               OUT NUMBER,
         epsg_srid_geog     IN NUMBER DEFAULT NULL,
         epsg_srid_proj     IN NUMBER DEFAULT NULL,
         datum_id           IN NUMBER DEFAULT NULL,
         pm_id              IN NUMBER DEFAULT NULL,
         proj_method_id     IN NUMBER DEFAULT NULL,
         proj_op_id         IN NUMBER DEFAULT NULL,
         coord_ref_sys_kind IN VARCHAR2 DEFAULT NULL,
         semi_major_axis    IN NUMBER DEFAULT NULL,
         semi_minor_axis    IN NUMBER DEFAULT NULL,
         inv_flattening     IN NUMBER DEFAULT NULL,
         params             IN EPSG_PARAMS DEFAULT NULL,
         max_rel_num_difference IN NUMBER DEFAULT 0.000001);

#### Description

Finds an SRID value for a coordinate system that matches information that you specify.

#### Parameters

srid
Output parameter; will contain either a numeric SRID value or a null value, as explained in the Usage Notes.

epsg_srid_geog
EPGS SRID value of a geographic coordinate system. Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will either verify the existence of a coordinate system with this geographic SRID value, or will find an SRID value of a projected coordinate system based on a coordinate system with this SRID value.

epsg_srid_proj
EPGS SRID value of a projected coordinate system.

datum_id
Datum ID value. Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will look for the SRID of a geographic or projected coordinate system based on this datum.

ellipsoid_id
Ellipsoid ID value. Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will look for the SRID of a geographic or projected coordinate system based on this ellipsoid.

pm_id
Prime meridian ID value. Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will look for the SRID of a geographic or projected coordinate system based on this prime meridian.

proj_method_id
Projection method ID value. This procedure will look for the SRID of a projected coordinate system based on this projection method.

proj_op_id
Projection operation ID value. This procedure will look for the SRID of a projected coordinate system based on this projection operation. A projection operation is a projection method combined with specific projection parameters.

coord_ref_sys_kind
The kind or category of coordinate system. Must be a string value in the COORD_REF_SYS_KIND column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)). Examples: `GEOGRAPHIC2D` and `PROJECTED`

semi_major_axis
Semi-major axis ID value. Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will loo for the SRID of a geographic or projected coordinate system based on this semi-major axis.

semi_minor_axis
Semi-minor axis ID value. Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will look for the SRID of a geographic or projected coordinate system based on this semi-minor axis.

inv_flattening
Inverse flattening (unit "unity"). Depending on the value of the `coord_ref_sys_kind` parameter, this procedure will look for the SRID of a geographic or projected coordinate system based on this inverse flattening.

params
Projection parameters. The parameters depend on the projection method. The EPSG_PARAMS type is defined as `VARRAY(1048576) OF EPSG_PARAM`, and the EPSG_PARAM type is defined as `(id NUMBER, val NUMBER, uom NUMBER)`. The format includes attributes for the parameter ID, value, and unit of measure ID, as shown in the following example:

    epsg_params(
      epsg_param(8801,      0.0,    9102),
      epsg_param(8802,      9.0,    9102),
      epsg_param(8805,      0.9996, 9201),
      epsg_param(8806, 500000.0,    9001),
      epsg_param(8807,      0.0,    9001));

max_rel_num_difference
A numeric value indicating how closely WKT values must match in order for a coordinate reference system to be considered a match. The default value is 0.000001. The value for each numeric WKT item is compared with its corresponding value in the WKT for the reference SRID or in the specified list of parameters to this procedure; and if the difference in all cases is less than or equal to the `max_rel_num_difference` value, the SRID for that coordinate reference system is included in the results.

#### Usage Notes

This procedure places the result of its operation in the `srid` output parameter. The result is either a numeric SRID value or a null value.

This procedure has the following major uses:

- To check if a coordinate system with a specific SRID value exists. In this case, you specify a value for `epsg_srid_geog` or `epsg_srid_proj` (depending on whether the coordinate system is geographic or projected) and enough parameters for a valid PL/SQL statement. If the resulting `srid` parameter value is the same number as the value that you specified, the coordinate system with that SRID value exists; however, if the resulting `srid` parameter value is null, no coordinate system with that SRID value exists.

- To find the SRID value of a coordinate system based on information that you specify about it.

If multiple coordinate systems match the criteria specified in the input parameters, only one SRID value is returned in the `srid` parameter. This could be any one of the potential matching SRID values, and it is not guaranteed to be the same value in subsequent executions of this procedure with the same input parameters.

#### Examples

The following example finds an SRID value for a projected coordinate system that uses datum ID 6267 in its definition.

    DECLARE
      returned_srid  NUMBER;
    BEGIN
    SDO_CS.FIND_SRID (
       srid               => returned_srid,
       epsg_srid_geog     => null,
       epsg_srid_proj     => null,
       datum_id           => 6267,
       ellips_id          => null,
       pm_id              => null,
       proj_method_id     => null,
       proj_op_id         => null,
       coord_ref_sys_kind => 'PROJECTED');
    DBMS_OUTPUT.PUT_LINE('SRID = ' || returned_srid);
    END;
    /
    SRID = 4267

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.17 SDO_CS.FROM_GEOHASH

#### Format

    SDO_CS.FROM_GEOHASH(
         geohash IN SDO_VARCHAR2,
         srid    IN NUMBER) RETURN SDO_GEOMETRY;

#### Description

Returns a spatial geometry (type SDO_GEOMETRY) representing a specified geohash.

#### Parameters

geohash
Geohash representation of a geometry

srid
Coordinate system (spatial reference system) to be used in constructing the Oracle Spatial geometry..

#### Usage Notes

For information about geohash support in Oracle Spatial, see [Geohash Support](coordinate-systems-concepts.md).

#### Examples

The following example “converts” a specified geohash value to a geometry of SRID 4326.

    SELECT sdo_cs.from_GeoHash('u4pruydqqvj', 4326) FROM DUAL;

    SDO_GEOMETRY(2002, 4326, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 3), SDO_ORDINATE_ARRAY(10.407439, 57.64911, 10.4074404, 57.6491113))

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.18 SDO_CS.FROM_OGC_SIMPLEFEATURE_SRS

#### Format

    SDO_CS.FROM_OGC_SIMPLEFEATURE_SRS(
         wkt  IN VARCHAR2) RETURN VARCHAR2;

#### Description

Converts a well-known text string from the Open Geospatial Consortium simple feature format without the `TOWGS84` keyword to the format that includes the `TOWGS84` keyword.

#### Parameters

wkt
Well-known text string.

#### Usage Notes

To convert a well-known text string from the Open Geospatial Consortium simple feature format that includes the `TOWGS84` keyword to the format without the `TOWGS84` keyword, use the SDO_CS.TO_OGC_SIMPLEFEATURE_SRS function.

#### Examples

The following example converts a well-known text string from the Open Geospatial Consortium simple feature format without the `TOWGS84` keyword to the format that includes the `TOWGS84` keyword.

    SELECT sdo_cs.from_OGC_SimpleFeature_SRS('GEOGCS [ "Longitude / Latitude (DHDN)",
      DATUM ["", SPHEROID ["Bessel 1841", 6377397.155, 299.1528128],
      582.000000, 105.000000, 414.000000, -1.040000, -0.350000, 3.080000, 8.300000 ],
      PRIMEM [ "Greenwich", 0.000000 ], UNIT ["Decimal Degree", 0.01745329251994330]]')
    FROM DUAL;

    MDSYS.SDO_CS.FROM_OGC_SIMPLEFEATURE_SRS('GEOGCS["LONGITUDE/LATITUDE(DHDN)",DATUM
    --------------------------------------------------------------------------------
    GEOGCS [ "Longitude / Latitude (DHDN)", DATUM ["", SPHEROID ["Bessel 1841", 6377
    397.155, 299.1528128], TOWGS84[ 582.000000, 105.000000, 414.000000, -1.040000, -
    0.350000, 3.080000, 8.300000]], PRIMEM [ "Greenwich", 0.000000 ], UNIT ["Decimal
     Degree", 0.01745329251994330]]

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.19 SDO_CS.FROM_USNG

#### Format

    SDO_CS.FROM_USNG(
         usng   IN VARCHAR2,
         srid   IN NUMBER,
         datum  IN VARCHAR2 DEFAULT 'NAD83') RETURN SDO_GEOMETRY;

#### Description

Converts a point represented in U.S. National Grid format to a spatial point geometry object.

#### Parameters

usng
Well-known text string.

srid
The SRID of the coordinate system to be used for the conversion (that is, the SRID to be used in the returned geometry). Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

datum
The name of the datum on which the U.S. National Grid coordinate for the point is based. Must be either a value in the DATUM_NAME column of the SDO_DATUMS table (described in [SDO_DATUMS Table](coordinate-systems-concepts.md)) or null. The default value is `NAD83`.

#### Usage Notes

For information about Oracle Spatial and Graph support for the U.S. National Grid, see [U.S. National Grid Support](coordinate-systems-concepts.md).

To convert a spatial point geometry to a point represented in U.S. National Grid format, use the SDO_CS.TO_USNG function.

#### Examples

The following example converts a point represented in U.S. National Grid format to a spatial geometry point object with longitude/latitude coordinates.

    -- Convert US National Grid point to SDO_GEMETRY point using SRID 4326
    -- (WGS 84, longitude/latitude).
    SELECT SDO_CS.FROM_USNG(
      '18SUJ2348316806479498',
      4326) FROM DUAL;

    WGS84(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2001, 4326, SDO_POINT_TYPE(-77.03524, 38.8894673, NULL), NULL, NULL)

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.20 SDO_CS.GENERATE_SCRIPT_FROM_SRID

#### Format

    GENERATE_SCRIPT_FROM_SRID(
         srid          IN NUMBER,
         offset        IN NUMBER DEFAULT 0,
         include_units IN NUMBER DEFAULT 1) RETURN CLOB;

#### Description

Returns a CLOB object that includes the SQL statements necessary to create the coordinate system with the specified SRID value.

#### Parameters

srid
The SRID of the coordinate reference system. Must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

offset
A number to be added to the SRID value of the coordinate system created by the generated script. For example, specifying `SDO_CS.GENERATE_SCRIPT_FROM_SRID(``27700, 50000``)` would cause the INSERT statements the resulting script to specify the SRID as 77700 (that is, 27700 + 50000). The purpose might be to ensure that a new unique SRID gets generated if you know that you do not have any current SRIDs equal to or greater than 77700.

The default offset value is 0 (zero).

include_units
The numeric value 0 means not to include units of measure in generated statements; the numeric value 1 (the default) means to include units of measure in generated statements.

The default value is recommended in virtually all cases. Exceptions, if any, should be rare, and only if there are “nonstandard” units of measure for attributes.

#### Usage Notes

Before using this function, you must use the SQL\*Plus command SET LONG to increase the maximum width in bytes for column output. For example: `SET LONG 20000`

If you plan to use the output to help you modify a coordinate system definition or to create a new definition -- as opposed to just viewing the information -- you must edit the output as needed to ensure syntactic correctness (such as for the INSERT statements).

The script can be run on a different (target) database or on the same database on which you executed this function. In either case, there might be an existing coordinate system associated with the SRID in question; and in this case you might want to take action to deal with that scenario (such as using the `offeet` parameter).

You are discouraged from making changes to “standard” coordinate system definitions.

#### Examples

The following example returns a CLOB object that includes the statements necessary to define the coordinate system with the SRID value 27700.

    SQL> SET LONG 20000

    SQL> SELECT sdo_cs.GENERATE_SCRIPT_FROM_SRID(27700) FROM DUAL;

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
    insert into mdsys.sdo_units_of_measure (
      UOM_ID,
      UNIT_OF_MEAS_NAME,
      SHORT_NAME,
      LEGACY_UNIT_NAME,
      UNIT_OF_MEAS_TYPE,
      TARGET_UOM_ID,
      FACTOR_B,
      FACTOR_C,
      INFORMATION_SOURCE,
      DATA_SOURCE,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      IS_LEGACY,
      LEGACY_CODE)
    values (
      9001,
      'metre',
      'METRE_9001',
      'Meter',
      'length',
      9001,
      1,
      1,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'ISO 1000.',
      'EPSG',
      'FALSE',
      NULL);

    insert into mdsys.sdo_units_of_measure (
      UOM_ID,
      UNIT_OF_MEAS_NAME,
      SHORT_NAME,
      LEGACY_UNIT_NAME,
      UNIT_OF_MEAS_TYPE,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      TARGET_UOM_ID,
      FACTOR_B,
      FACTOR_C,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE)
    values (
      9102,
      'degree',
      'DEGREE_EPSG_9102',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'Decimal Degree',
      'angle',
      9101,
      3.14159265358979,
      180,
      NULL,
      'EPSG',
      'FALSE',
      NULL);

    insert into mdsys.sdo_units_of_measure (

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      UOM_ID,
      UNIT_OF_MEAS_NAME,
      SHORT_NAME,
      LEGACY_UNIT_NAME,
      UNIT_OF_MEAS_TYPE,
      TARGET_UOM_ID,
      FACTOR_B,
      FACTOR_C,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      LEGACY_CODE)
    values (
      9110,
      'sexagesimal DMS',
      'SEXAGESIMAL_DMS_EPSG_9110',
      NULL,
      'angle',
      9101,
      3.14159265358979,
      180,
      'EPSG',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'EPSG',
      'FALSE',
      NULL);

    insert into mdsys.sdo_units_of_measure (
      UOM_ID,
      UNIT_OF_MEAS_NAME,
      SHORT_NAME,
      LEGACY_UNIT_NAME,
      UNIT_OF_MEAS_TYPE,
      TARGET_UOM_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      FACTOR_B,
      FACTOR_C,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE)
    values (
      9122,
      'degree (supplier to define representation)',
      'DEGREE_SUPPLIER_DEFINED_9122',
      'Decimal Degree',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'angle',
      9101,
      3.14159265358979,
      180,
      'EPSG',
      'EPSG',
      'FALSE',
      NULL);

    insert into mdsys.sdo_units_of_measure (
      UOM_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      UNIT_OF_MEAS_NAME,
      SHORT_NAME,
      LEGACY_UNIT_NAME,
      UNIT_OF_MEAS_TYPE,
      TARGET_UOM_ID,
      FACTOR_B,
      FACTOR_C,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE)

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
    values (
      9201,
      'unity',
      'UNITY_9201',
      NULL,
      'scale',
      9201,
      1,
      1,
      NULL,
      'EPSG',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'FALSE',
      NULL);

    insert into mdsys.sdo_coord_ops (
      COORD_OP_ID,
      COORD_OP_NAME,
      COORD_OP_TYPE,
      SOURCE_SRID,
      TARGET_SRID,
      COORD_TFM_VERSION,
      COORD_OP_VARIANT,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      COORD_OP_METHOD_ID,
      UOM_ID_SOURCE_OFFSETS,
      UOM_ID_TARGET_OFFSETS,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      SHOW_OPERATION,
      IS_LEGACY,
      LEGACY_CODE,
      REVERSE_OP,
      IS_IMPLEMENTED_FORWARD,
      IS_IMPLEMENTED_REVERSE)

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
    values (
      19916,
      'British National Grid (EPSG OP 19916)',
      'CONVERSION',
      NULL,
      NULL,
      NULL,
      NULL,
      9807,
      NULL,
      NULL,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'Ordnance Survey of Great Britain.  http://www.gps.gov.uk/additionalInfo/image
    s/A_guide_to_coord.pdf',
      'EPSG',
      1,
      'FALSE',
      NULL,
      1,
      1,
      1);

    insert into mdsys.sdo_coord_op_param_vals (

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      COORD_OP_ID,
      COORD_OP_METHOD_ID,
      PARAMETER_ID,
      PARAMETER_VALUE,
      PARAM_VALUE_FILE_REF,
      PARAM_VALUE_FILE,
      PARAM_VALUE_XML,
      UOM_ID)
    values (
      19916,
      9807,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      8801,
      49,
      NULL,
      null,
      null,
      9102);

    insert into mdsys.sdo_coord_op_param_vals (
      COORD_OP_ID,
      COORD_OP_METHOD_ID,
      PARAMETER_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      PARAMETER_VALUE,
      PARAM_VALUE_FILE_REF,
      PARAM_VALUE_FILE,
      PARAM_VALUE_XML,
      UOM_ID)
    values (
      19916,
      9807,
      8802,
      -2,
      NULL,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      null,
      null,
      9102);

    insert into mdsys.sdo_coord_op_param_vals (
      COORD_OP_ID,
      COORD_OP_METHOD_ID,
      PARAMETER_ID,
      PARAMETER_VALUE,
      PARAM_VALUE_FILE_REF,
      PARAM_VALUE_FILE,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      PARAM_VALUE_XML,
      UOM_ID)
    values (
      19916,
      9807,
      8805,
      .9996012717,
      NULL,
      null,
      null,
      9201);

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------

    insert into mdsys.sdo_coord_op_param_vals (
      COORD_OP_ID,
      COORD_OP_METHOD_ID,
      PARAMETER_ID,
      PARAMETER_VALUE,
      PARAM_VALUE_FILE_REF,
      PARAM_VALUE_FILE,
      PARAM_VALUE_XML,
      UOM_ID)
    values (

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      19916,
      9807,
      8806,
      400000,
      NULL,
      null,
      null,
      9001);

    insert into mdsys.sdo_coord_op_param_vals (
      COORD_OP_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      COORD_OP_METHOD_ID,
      PARAMETER_ID,
      PARAMETER_VALUE,
      PARAM_VALUE_FILE_REF,
      PARAM_VALUE_FILE,
      PARAM_VALUE_XML,
      UOM_ID)
    values (
      19916,
      9807,
      8807,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      -100000,
      NULL,
      null,
      null,
      9001);

    insert into mdsys.sdo_ellipsoids (
      ELLIPSOID_ID,
      ELLIPSOID_NAME,
      SEMI_MAJOR_AXIS,
      UOM_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      INV_FLATTENING,
      SEMI_MINOR_AXIS,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE)
    values (
      7001,
      'Airy 1830',
      6377563.396,
      9001,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      299.3249646,
      6356256.90923728512018673099343615524143,
      'Ordnance Survey of Great Britain.',
      'EPSG',
      'FALSE',
      8001);

    insert into mdsys.sdo_prime_meridians (
      PRIME_MERIDIAN_ID,
      PRIME_MERIDIAN_NAME,
      GREENWICH_LONGITUDE,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      UOM_ID,
      INFORMATION_SOURCE,
      DATA_SOURCE)
    values (
      8901,
      'Greenwich 8901',
      0,
      9110,
      NULL,
      'EPSG');

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
    insert into mdsys.sdo_datums (
      DATUM_ID,
      DATUM_NAME,
      DATUM_TYPE,
      ELLIPSOID_ID,
      PRIME_MERIDIAN_ID,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      SHIFT_X,
      SHIFT_Y,
      SHIFT_Z,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      ROTATE_X,
      ROTATE_Y,
      ROTATE_Z,
      SCALE_ADJUST,
      IS_LEGACY,
      LEGACY_CODE)
    values (
      6277,
      'OSGB 1936',
      'GEODETIC',
      7001,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      8901,
      'Ordnance Survey of Great Britain',
      'EPSG',
      446.448,
      -125.157,
      542.06,
      .15,
      .247,
      .842,
      -20.489,
      'FALSE',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      NULL);

    insert into mdsys.sdo_coord_sys (
      COORD_SYS_ID,
      COORD_SYS_NAME,
      COORD_SYS_TYPE,
      DIMENSION,
      INFORMATION_SOURCE,
      DATA_SOURCE)
    values (
      6422,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'Ellipsoidal 2D CS. Axes: latitude, longitude. Orientations: north, east.  UoM
    : deg 6422',
      'ellipsoidal',
      2,
      'EPSG',
      'EPSG');

    insert into mdsys.sdo_coord_axes (
      COORD_SYS_ID,
      COORD_AXIS_NAME_ID,
      COORD_AXIS_ORIENTATION,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      COORD_AXIS_ABBREVIATION,
      UOM_ID,
      "ORDER")
    values (
      6422,
      9901,
      'north',
      'Lat',
      9122,
      1);

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
    insert into mdsys.sdo_coord_axes (
      COORD_SYS_ID,
      COORD_AXIS_NAME_ID,
      COORD_AXIS_ORIENTATION,
      COORD_AXIS_ABBREVIATION,
      UOM_ID,
      "ORDER")
    values (
      6422,
      9902,
      'east',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'Long',
      9122,
      2);

    insert into mdsys.sdo_coord_ref_system (
      SRID,
      COORD_REF_SYS_NAME,
      COORD_REF_SYS_KIND,
      COORD_SYS_ID,
      DATUM_ID,
      GEOG_CRS_DATUM_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      SOURCE_GEOG_SRID,
      PROJECTION_CONV_ID,
      CMPD_HORIZ_SRID,
      CMPD_VERT_SRID,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE,
      LEGACY_WKTEXT,
      LEGACY_CS_BOUNDS,
      IS_VALID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      SUPPORTS_SDO_GEOMETRY)
    values (
      4277,
      'OSGB 1936',
      'GEOGRAPHIC2D',
      6422,
      6277,
      6277,
      NULL,
      NULL,
      NULL,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      NULL,
      NULL,
      'EPSG',
      'FALSE',
      NULL,
      NULL,
      null,
      'TRUE',
      'TRUE');

    insert into mdsys.sdo_coord_sys (

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      COORD_SYS_ID,
      COORD_SYS_NAME,
      COORD_SYS_TYPE,
      DIMENSION,
      INFORMATION_SOURCE,
      DATA_SOURCE)
    values (
      4400,
      'Cartesian 2D CS.  Axes: easting, northing (E,N). Orientations: east, north.
    UoM: m. 4400',
      'Cartesian',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      2,
      'EPSG',
      'EPSG');

    insert into mdsys.sdo_coord_axes (
      COORD_SYS_ID,
      COORD_AXIS_NAME_ID,
      COORD_AXIS_ORIENTATION,
      COORD_AXIS_ABBREVIATION,
      UOM_ID,
      "ORDER")

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
    values (
      4400,
      9906,
      'east',
      'E',
      9001,
      1);

    insert into mdsys.sdo_coord_axes (
      COORD_SYS_ID,
      COORD_AXIS_NAME_ID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      COORD_AXIS_ORIENTATION,
      COORD_AXIS_ABBREVIATION,
      UOM_ID,
      "ORDER")
    values (
      4400,
      9907,
      'north',
      'N',
      9001,
      2);

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------

    insert into mdsys.sdo_coord_ref_system (
      SRID,
      COORD_REF_SYS_NAME,
      COORD_REF_SYS_KIND,
      COORD_SYS_ID,
      DATUM_ID,
      GEOG_CRS_DATUM_ID,
      SOURCE_GEOG_SRID,
      PROJECTION_CONV_ID,
      CMPD_HORIZ_SRID,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      CMPD_VERT_SRID,
      INFORMATION_SOURCE,
      DATA_SOURCE,
      IS_LEGACY,
      LEGACY_CODE,
      LEGACY_WKTEXT,
      LEGACY_CS_BOUNDS,
      IS_VALID,
      SUPPORTS_SDO_GEOMETRY)
    values (
      27700,

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'OSGB 1936 / British National Grid',
      'PROJECTED',
      4400,
      NULL,
      6277,
      4277,
      19916,
      NULL,
      NULL,
      NULL,
      'EPSG',

    SDO_CS.GENERATE_SCRIPT_FROM_SRID(27700)
    --------------------------------------------------------------------------------
      'FALSE',
      NULL,
      NULL,
      null,
      'TRUE',
      'TRUE');

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.21 SDO_CS.GET_EPSG_DATA_VERSION

#### Format

    SDO_CS.GET_EPSG_DATA_VERSION() RETURN VARCHAR2;

#### Description

Gets the version number of the EPSG dataset used by Spatial and Graph.

#### Parameters

None.

#### Usage Notes

The EPSG dataset is available from the European Petroleum Survey Group, and is distributed in a Microsoft Access 97 database and as SQL scripts.

#### Examples

The following example gets the version number of the EPSG dataset used by Spatial and Graph.

    SELECT SDO_CS.GET_EPSG_DATA_VERSION FROM DUAL;

    GET_EPSG_DATA_VERSION
    -------------------------------------------------------------------------------
    7.5

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.22 SDO_CS.GET_GEOHASH_CELL_HEIGHT

#### Format

    SDO_CS.GET_GEOHASH_CELL_HEIGHT(
         geohash_length  IN NUMBER) RETURN SDO_NUMBER;

#### Description

Returns the cell height of a specified geohash.

#### Parameters

geohash_length
Length of the geohash.

#### Usage Notes

Depending on its length, a geohash can vary in its accuracy. A longer geohash defines a smaller (more accurate) coordinate cell. You can return the cell width and height in meters (assuming WGS84).

For information about geohash support in Oracle Spatial, see [Geohash Support](coordinate-systems-concepts.md).

#### Examples

The following example returns the cell height in meters if the geohash length is 11..

    SELECT sdo_cs.get_GeoHash_cell_height(11) FROM DUAL;

                            .149

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.23 SDO_CS.GET_GEOHASH_CELL_WIDTH

#### Format

    SDO_CS.GET_GEOHASH_CELL_WIDTH(
         geohash_length  IN NUMBER) RETURN SDO_NUMBER;

#### Description

Returns the cell width of a specified geohash.

#### Parameters

geohash_length
Length of the geohash.

#### Usage Notes

Depending on its length, a geohash can vary in its accuracy. A longer geohash defines a smaller (more accurate) coordinate cell. You can return the cell width and height in meters (assuming WGS84).

For information about geohash support in Oracle Spatial, see [Geohash Support](coordinate-systems-concepts.md).

#### Examples

The following example returns the cell width in meters if the geohash length is 11..

    SELECT sdo_cs.get_GeoHash_cell_width(11) FROM DUAL;

                            .149

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.24 SDO_CS.LOAD_EPSG_MATRIX

#### Format

    SDO_CS.LOAD_EPSG_MATRIX(
         op_id        IN NUMBER,
         parameter_id IN NUMBER,
         directory    IN VARCHAR2,
         file_name    IN VARCHAR2);

#### Description

Loads an EPSG matrix of NADCON, NTv2, or VERTCON format.

#### Parameters

op_id
EPSG operation ID to which the matrix belongs.

parameter_id
EPSG parameter id identifying the matrix, if an operation has more than one matrix, such as NADCON.

directory
Name of the matrix file directory.

file_name
Matrix file name.

#### Usage Notes

To validate an EPSG matrix, use the SDO_CS.VALIDATE_EPSG_MATRIX function.

#### Examples

The following example loads an NTv2 matrix for operation 1703 ("NAD27 to WGS 84 (32)"). For an NTv2 operation, a single matrix is sufficient, assigned to parameter ID 8656.

    CREATE OR REPLACE DIRECTORY work_dir AS '…';

    EXECUTE sdo_cs.load_epsg_matrix(
        1703,
        8656,
        'WORK_DIR',
        'ntv2file.asc');

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.25 SDO_CS.MAKE_2D

#### Format

    SDO_CS.MAKE_2D(
         geom3d      IN SDO_GEOMETRY,
         target_srid IN NUMBER DEFAULT NULL) RETURN SDO_GEOMETRY;

#### Description

Converts a three-dimensional (or more dimensions) geometry into a two-dimensional geometry.

#### Parameters

geom3d
Geometry object with more then two dimensions.

target_srid
The SRID of the target coordinate reference system. Must be null or a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)). If this parameter is null, a default SRID is used based on the SRID of the input geometry.

#### Usage Notes

This function returns a two-dimensional geometry object that removes the third (height) dimension value (and other dimension values if the input geometry has more than three dimensions) from each vertex in the input geometry.

For information about three-dimensional coordinate reference system support, see [Three-Dimensional Coordinate Reference System Support](coordinate-systems-concepts.md).

#### Examples

The following example converts a three-dimensional geometry to a two-dimensional geometry by removing all the third (height) dimension values. (It uses as its input geometry the output geometry from the example for the SDO_CS.MAKE_3D function.)

    SELECT SDO_CS.MAKE_2D(SDO_GEOMETRY(3003, 8307, NULL,
     SDO_ELEM_INFO_ARRAY(1, 1003, 1),
       SDO_ORDINATE_ARRAY(1, 1, 10, 5, 1, 10, 5, 7, 10, 1, 7, 10, 1, 1, 10)))
    FROM DUAL;

    SDO_CS.MAKE_2D(SDO_GEOMETRY(3003,8307,NULL,SDO_ELEM_INFO_ARRAY(1,1003,1),SDO_ORD
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(1, 1, 5, 1, 5, 7, 1, 7, 1, 1))

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.26 SDO_CS.MAKE_3D

#### Format

    SDO_CS.MAKE_3D(
         geom2d      IN SDO_GEOMETRY,
         height      IN NUMBER DEFAULT 0,
         target_srid IN NUMBER DEFAULT NULL) RETURN SDO_GEOMETRY;

#### Description

Converts a two-dimensional geometry into a three-dimensional geometry.

#### Parameters

geom2d
Two-dimensional geometry object.

height
Height value to be used in the third dimension for all vertices in the returned geometry. If this parameter is null or not specified, a height of 0 (zero) is used for all vertices.

target_srid
The SRID of the target coordinate reference system. Must be null or a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

**Note:**

SDO_CS.MAKE_3D function is supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

For information about using this function to simulate a cross-dimensionality transformation, see [Cross-Dimensionality Transformations](coordinate-systems-concepts.md).

For information about three-dimensional coordinate reference system support, see [Three-Dimensional Coordinate Reference System Support](coordinate-systems-concepts.md).

#### Examples

The following example converts the `cola_a` two-dimensional geometry to a three-dimensional geometry. (This example uses the definitions from the example in [Example of Coordinate System Transformation](coordinate-systems-concepts.md).).

    SELECT SDO_CS.MAKE_3D(c.shape, 10, 8307) FROM cola_markets_cs c
      WHERE c.name = 'cola_a';

    SDO_CS.MAKE_3D(C.SHAPE,10,8307)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELE
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(3003, 8307, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(1, 1, 10, 5, 1, 10, 5, 7, 10, 1, 7, 10, 1, 1, 10))

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.27 SDO_CS.MAP_EPSG_SRID_TO_ORACLE

#### Format

    SDO_CS.MAP_EPSG_SRID_TO_ORACLE(
         epsg_srid  IN NUMBER) RETURN NUMBER;

#### Description

Returns the Oracle Spatial and Graph SRID value corresponding to the specified EPSG SRID value.

#### Parameters

epsg_srid
The SRID of the EPSG coordinate reference system, as indicated in the COORD_REF_SYS_CODE field in the EPSG Coordinate Reference System table.

#### Usage Notes

This function returns a value that matches a value in the SRID column of the SDO_COORD_REF_SYS table (see [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

To return the EPSG SRID value corresponding to the specified Oracle Spatial and Graph SRID value, use the SDO_CS.MAP_ORACLE_SRID_TO_EPSG function.

#### Examples

The following example returns the Oracle Spatial and Graph SRID value corresponding to EPSG SRID 23038.

    SELECT SDO_CS.MAP_EPSG_SRID_TO_ORACLE(23038) FROM DUAL;

    SDO_CS.MAP_EPSG_SRID_TO_ORACLE(23038)
    -------------------------------------
                                    82361

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.28 SDO_CS.MAP_ORACLE_SRID_TO_EPSG

#### Format

    SDO_CS.MAP_ORACLE_SRID_TO_EPSG(
         legacy_srid  IN NUMBER) RETURN NUMBER;

#### Description

Returns the EPSG SRID value corresponding to the specified Oracle Spatial and Graph SRID value.

#### Parameters

legacy_srid
Oracle Spatial and Graph SRID value. Must match a value in the LEGACY_CODE column of the SDO_COORD_REF_SYS table (see [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

This function returns the SRID of an EPSG coordinate reference system. The EPSG SRID value for a coordinate reference system is indicated in the COORD_REF_SYS_CODE field in the EPSG Coordinate Reference System table.

To return the Oracle Spatial and Graph SRID value corresponding to a specified EPSG SRID value, use the SDO_CS.MAP_EPSG_SRID_TO_ORACLE function.

#### Examples

The following example returns the EPSG SRID value corresponding to Oracle Spatial and Graph SRID 82361.

    SELECT SDO_CS.MAP_ORACLE_SRID_TO_EPSG(82361) FROM DUAL;

    SDO_CS.MAP_ORACLE_SRID_TO_EPSG(82361)
    -------------------------------------
                                    23038

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.29 SDO_CS.REVOKE_PREFERENCE_FOR_OP

#### Format

    SDO_CS.REVOKE_PREFERENCE_FOR_OP(
         op_id      IN NUMBER,
         source_crs IN NUMBER DEFAULT NULL,
         target_crs IN NUMBER DEFAULT NULL,
         use_case   IN VARCHAR2 DEFAULT NULL);

#### Description

Revokes a preference for an operation between a source coordinate system and a target coordinate system.

#### Parameters

op_id
ID number of the operation. Must match an `op_id` value that was specified in a call to the SDO_CS.ADD_PREFERENCE_FOR_OP procedure.

source_crs
The SRID of the source coordinate reference system. Must match the `source_crs` value in a `source_crs`, `target_crs`, and `use_case` combination that was specified in a call to the SDO_CS.ADD_PREFERENCE_FOR_OP procedure.

target_crs
The SRID of the target coordinate reference system. Must match the `target_crs` value in a `source_crs`, `target_crs`, and `use_case` combination that was specified in a call to the SDO_CS.ADD_PREFERENCE_FOR_OP procedure.

use_case
Name of the use case associated with the preference. Must match the `use_case` value in a `source_crs`, `target_crs`, and `use_case` combination that was specified in a call to the SDO_CS.ADD_PREFERENCE_FOR_OP procedure.

#### Usage Notes

This procedure reverses the effect of the SDO_CS.ADD_PREFERENCE_FOR_OP procedure.

If `use_case` is null, this procedure deletes one or more rows from the SDO_PREFERRED_OPS_SYSTEM table (described in [SDO_PREFERRED_OPS_SYSTEM Table](coordinate-systems-concepts.md)). If `use_case` is not null, this procedure deletes one or more rows from the SDO_PREFERRED_OPS_USER table (described in [SDO_PREFERRED_OPS_USER Table](coordinate-systems-concepts.md)).

#### Examples

The following example revokes a preference for operation ID 19777 to be used in transformations from SRID 4301 to SRID 4326 when use case `use_case_B` is specified for the transformation.

    EXECUTE SDO_CS.REVOKE_PREFERENCE_FOR_OP(19977, 4301, 4326, 'use_case_B');

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.30 SDO_CS.TO_GEOHASH

#### Format

    SDO_CS.TO_GEOHASH(
         geom           IN SDO_GEOMETRY,
         geohash_length IN NUMBER) RETURN VARCHAR2;

#### Description

Returns the geohash representation of a spatial geometry (type SDO_GEOMETRY).

#### Parameters

geom
Oracle Spatial geometry

geohash_length
Length of the geohash result.

#### Usage Notes

For information about geohash support in Oracle Spatial, see [Geohash Support](coordinate-systems-concepts.md).

#### Examples

The following examples show the effect of the `is_legacy` parameter value on the results. The first example returns the SRID values of all geodetic legacy coordinate reference systems that have the same WKT numeric values as the coordinate reference system with the SRID value of 8307.

    SELECT sdo_cs.to_GeoHash(sdo_geometry(2001, 4326, sdo_point_type(10.40744, 57.64911, null), null, null), 11)
       FROM DUAL;from dual;

    u4pruydqqvj

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.31 SDO_CS.TO_OGC_SIMPLEFEATURE_SRS

#### Format

    SDO_CS.TO_OGC_SIMPLEFEATURE_SRS(
         wkt  IN VARCHAR2) RETURN VARCHAR2;

#### Description

Converts a well-known text string from the Open Geospatial Consortium simple feature format that includes the `TOWGS84` keyword to the format without the `TOWGS84` keyword.

#### Parameters

wkt
Well-known text string.

#### Usage Notes

To convert a well-known text string from the Open Geospatial Consortium simple feature format without the `TOWGS84` keyword to the format that includes the `TOWGS84` keyword, use the SDO_CS.FROM_OGC_SIMPLEFEATURE_SRS procedure.

#### Examples

The following example converts a well-known text string from the Open Geospatial Consortium simple feature format that includes the `TOWGS84` keyword to the format without the `TOWGS84` keyword.

    SELECT sdo_cs.to_OGC_SimpleFeature_SRS('GEOGCS [ "Longitude / Latitude (DHDN)",
      DATUM ["", SPHEROID ["Bessel 1841", 6377397.155, 299.1528128],
      TOWGS84 [582.000000, 105.000000, 414.000000, -1.040000, -0.350000, 3.080000,
        8.300000] ],
      PRIMEM [ "Greenwich", 0.000000 ], UNIT ["Decimal Degree", 0.01745329251994330]]')
    FROM DUAL;

    MDSYS.SDO_CS.TO_OGC_SIMPLEFEATURE_SRS('GEOGCS["LONGITUDE/LATITUDE(DHDN)",DATUM["
    --------------------------------------------------------------------------------
    GEOGCS [ "Longitude / Latitude (DHDN)", DATUM ["", SPHEROID ["Bessel 1841", 6377
    397.155, 299.1528128], 582.000000, 105.000000, 414.000000, -1.040000, -0.350000,
    3.080000, 8.300000 ], PRIMEM [ "Greenwich", 0.000000 ], UNIT ["Decimal Degree",
    0.01745329251994330]]

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.32 SDO_CS.TO_USNG

#### Format

    SDO_CS.TO_USNG(
         geom               IN SDO_GEOMETRY,
         accuracy_in_meters IN NUMBER,
         datum              IN VARCHAR2 DEFAULT 'NAD83') RETURN VARCHAR2;

#### Description

Converts a spatial point geometry object to a point represented in U.S. National Grid format.

#### Parameters

geom
Point geometry whose representation is to be converted to a point represented in U.S. National Grid format. The input geometry must have a valid non-null SRID, that is, a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

accuracy_in_meters
Accuracy of the point location in meters. Should be 1 raised to a negative or positive power of 10 (for example, 0.001, 0.01, 0.1, 1, 10, 100, or 1000). Any other specified values are adjusted internally by Spatial and Graph, and the result might not be what you expect.

datum
The name of the datum on which the U.S. National Grid coordinate for the point is to be based. Must be either `NAD83` or `NAD27`. The default value is `NAD83`.

#### Usage Notes

For information about Oracle Spatial and Graph support for the U.S. National Grid, see [U.S. National Grid Support](coordinate-systems-concepts.md).

The `accuracy_in_meters` value affects the number of digits used to represent the accuracy in the returned U.S. National Grid string. For example, if you specify 0.000001, the string will contain many digits; however, depending on the source of the data, the digits might not accurately reflect geographical reality. Consider the following scenarios. If you create a U.S. National Grid string from a UTM geometry, you can get perfect accuracy, because no inherently inaccurate transformation is involved. However, transforming from a Lambert projection to the U.S. National Grid format involves an inverse Lambert projection and a forward UTM projection, each of which has some inherent inaccuracy. If you request the resulting U.S. National Grid string with 1 millimeter (0.001) accuracy, the string will contain all the digits, but the millimeter-level digit will probably be geographically inaccurate.

To convert a point represented in U.S. National Grid format to a spatial point geometry, use the SDO_CS.FROM_USNG function.

#### Examples

The following example converts a spatial geometry point object with longitude/latitude coordinates to a point represented in U.S. National Grid format using an accuracy of 0.001 meter (1 millimeter).

    -- Convert longitude/latitude (WGS 84) point to US National Grid.
    SELECT SDO_CS.TO_USNG(
      SDO_GEOMETRY(2001, 4326,
        SDO_POINT_TYPE(-77.0352402158258, 38.8894673086544, NULL),
        NULL, NULL),
      0.001) FROM DUAL;

    SDO_CS.TO_USNG(SDO_GEOMETRY(2001,4326,SDO_POINT_TYPE(-77.0352402158258,38.889467
    --------------------------------------------------------------------------------
    18SUJ2348316806479498

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.33 SDO_CS.TRANSFORM

#### Format

    SDO_CS.TRANSFORM(
         geom    IN SDO_GEOMETRY,
         to_srid IN NUMBER
         ) RETURN SDO_GEOMETRY;

or

    SDO_CS.TRANSFORM(
         geom      IN SDO_GEOMETRY,
         to_srname IN VARCHAR2
         ) RETURN SDO_GEOMETRY;

or

    SDO_CS.TRANSFORM(
         geom      IN SDO_GEOMETRY,
         use_case  IN VARCHAR2,
         to_srid   IN NUMBER
         ) RETURN SDO_GEOMETRY;

or

    SDO_CS.TRANSFORM(
         geom      IN SDO_GEOMETRY,
         use_plan  IN TFM_PLAN
         ) RETURN SDO_GEOMETRY;

#### Description

Transforms a geometry representation using a coordinate system (specified by SRID or name).

You can also associate a use case or a transformation plan with the transformation.

#### Parameters

geom
Geometry whose representation is to be transformed using another coordinate system. The input geometry must have a valid non-null SRID, that is, a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

to_srid
The SRID of the coordinate system to be used for the transformation. It must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

to_srname
The name of the coordinate system to be used for the transformation. It must be a value (specified exactly) in the COORD_REF_SYS_NAME column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

use_case
The name of the use case to be associated with the transformation. If you specify the string `USE_SPHERICAL`, the transformation uses spherical math instead of ellipsoidal math, thereby accommodating Google Maps and some other third-party tools that use projections based on spherical math. Use cases are explained in [EPSG Model and Spatial and Graph](coordinate-systems-concepts.md). For considerations related to Google Maps, see [Google Maps Considerations](coordinate-systems-concepts.md).

use_plan
Transformation plan. The TFM_PLAN object type is explained in [TFM_PLAN Object Type](coordinate-systems-concepts.md).

#### Usage Notes

Transformation can be done only between two different georeferenced coordinate systems or between two different local coordinate systems.

Transformation of circles and arcs is not supported, regardless of the type of coordinate systems involved.

An exception is raised if `geom`, `to_srid`, or `to_srname` is invalid. For `geom` to be valid for this function, its definition must include an SRID value matching a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Examples

The following example transforms the `cola_c` geometry to a representation that uses SRID value 8199. (This example uses the definitions from the example in [Example of Coordinate System Transformation](coordinate-systems-concepts.md).)

    -- Return the transformation of cola_c using to_srid 8199
    -- ('Longitude / Latitude (Arc 1950)')
    SELECT c.name, SDO_CS.TRANSFORM(c.shape, 8199)
      FROM cola_markets_cs c WHERE c.name = 'cola_c';

    NAME
    --------------------------------
    SDO_CS.TRANSFORM(C.SHAPE,8199)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM
    --------------------------------------------------------------------------------
    cola_c
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3.00074114, 3.00291482, 6.00067068, 3.00291287, 6.0006723, 5.00307625, 4.0007
    1961, 5.00307838, 3.00074114, 3.00291482))

    -- Same as preceding, but using to_srname parameter.
    SELECT c.name, SDO_CS.TRANSFORM(c.shape, 'Longitude / Latitude (Arc 1950)')
      FROM cola_markets_cs c  WHERE c.name = 'cola_c';

    NAME
    --------------------------------
    SDO_CS.TRANSFORM(C.SHAPE,'LONGITUDE/LATITUDE(ARC1950)')(SDO_GTYPE, SDO_SRID, SDO
    --------------------------------------------------------------------------------
    cola_c
    SDO_GEOMETRY(2003, 8199, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARR
    AY(3.00074114, 3.00291482, 6.00067068, 3.00291287, 6.0006723, 5.00307625, 4.0007
    1961, 5.00307838, 3.00074114, 3.00291482))

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.34 SDO_CS.TRANSFORM_LAYER

#### Format

    SDO_CS.TRANSFORM_LAYER(
         table_in  IN VARCHAR2,
        column_in IN VARCHAR2,
        table_out IN VARCHAR2,
        to_srid   IN NUMBER);

or

    SDO_CS.TRANSFORM_LAYER(
         table_in  IN VARCHAR2,
        column_in IN VARCHAR2,
        table_out IN VARCHAR2,
        use_plan  IN TFM_PLAN);

or

    SDO_CS.TRANSFORM_LAYER(
         table_in  IN VARCHAR2,
        column_in IN VARCHAR2,
        table_out  IN VARCHAR2,
        use_case  IN VARCHAR2,
        to_srid   IN NUMBER);

#### Description

Transforms an entire layer of geometries (that is, all geometries in a specified column in a table).

#### Parameters

table_in
Table containing the layer (`column_in`) whose geometries are to be transformed.

column_in
Column in `table_in` that contains the geometries to be transformed.

table_out
Table that will be created and that will contain the results of the transformation. See the Usage Notes for information about the format of this table.

to_srid
The SRID of the coordinate system to be used for the transformation. `to_srid` must be a value in the SRID column of the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

use_plan
Transformation plan. The TFM_PLAN object type is explained in [TFM_PLAN Object Type](coordinate-systems-concepts.md).

use_case
Name of the use case whose transformation rules are to be applied in performing the transformation. Use cases are explained in [EPSG Model and Spatial and Graph](coordinate-systems-concepts.md).

#### Usage Notes

Transformation can be done only between two different georeferenced coordinate systems or between two different local coordinate systems.

An exception is raised if any of the following occurs:

- `table_in` does not exist, or `column_in` does not exist in the table.

- The geometries in `column_in` have a null or invalid SDO_SRID value.

- `table_out` already exists.

- `to_srid` is invalid.

The `table_out` table is created by the procedure and is filled with one row for each transformed geometry. This table has the columns shown in Table 22-1.

Table 22-1 Table to Hold Transformed Layer

| Column Name | Data Type    | Description                                                                                                                                                  |
|:------------|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SDO_ROWID   | ROWID        | Oracle ROWID (row address identifier). For more information about the ROWID data type, see [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md). |
| GEOMETRY    | SDO_GEOMETRY | Geometry object with coordinate values in the specified (`to_srid` parameter) coordinate system.                                                             |

#### Examples

The following example transforms the geometries in the `shape` column in the COLA_MARKETS_CS table to a representation that uses SRID value 8199. The transformed geometries are stored in the newly created table named COLA_MARKETS_CS_8199. (This example uses the definitions from the example in [Example of Coordinate System Transformation](coordinate-systems-concepts.md).)

    -- Transform the entire SHAPE layer and put results in the table
    -- named cola_markets_cs_8199, which the procedure will create.
    CALL SDO_CS.TRANSFORM_LAYER('COLA_MARKETS_CS','SHAPE','COLA_MARKETS_CS_8199',8199);

[Example of Coordinate System Transformation](coordinate-systems-concepts.md) includes a display of the geometry object coordinates in both tables (COLA_MARKETS_CS and COLA_MARKETS_CS_8199).

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.35 SDO_CS.UPDATE_WKTS_FOR_ALL_EPSG_CRS

#### Format

    SDO_CS.UPDATE_WKTS_FOR_ALL_EPSG_CRS();

#### Description

Updates the well-known text (WKT) description for all EPSG coordinate reference systems.

#### Parameters

None.

#### Usage Notes

For information about using procedures to update well-known text (WKT) description, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for all EPSG coordinate reference systems.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_ALL_EPSG_CRS;
    Updating SRID 4001...
    Updating SRID 4002...
    Updating SRID 4003...
    . . .
    Updating SRID 69036405...
    Updating SRID 69046405...

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.36 SDO_CS.UPDATE_WKTS_FOR_EPSG_CRS

#### Format

    SDO_CS.UPDATE_WKTS_FOR_EPSG_CRS(
         srid IN NUMBER);

#### Description

Updates the well-known text (WKT) description for the EPSG coordinate reference system associated with a specified SRID.

#### Parameters

srid
The SRID of the coordinate system whose well-known text (WKT) description is to be updated. An entry for the specified value must exist in the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

This procedure updates the WKT descriptions for the specified SRID and all dependent SRIDs. For example, for SRID 4326 (WGS84 geodetic system), all EPSG coordinate systems that use this geodetic system will also be updated.

For information about using procedures to update well-known text (WKT) descriptions, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for the EPSG coordinate reference system associated with SRID 4326.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_EPSG_CRS(4326);

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.37 SDO_CS.UPDATE_WKTS_FOR_EPSG_DATUM

#### Format

    SDO_CS.UPDATE_WKTS_FOR_EPSG_DATUM(
         datum_id  IN NUMBER);

#### Description

Updates the well-known text (WKT) description for all EPSG coordinate reference systems associated with a specified datum.

#### Parameters

datum_id
The ID of the datum. Must match a value in the DATUM_ID column of the SDO_DATUMS table (described in [SDO_DATUMS Table](coordinate-systems-concepts.md)).

#### Usage Notes

For information about using procedures to update well-known text (WKT) description, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for all EPSG coordinate reference systems associated with datum 5100.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_EPSG_DATUM(5100);
    Updating SRID 5714...
    Updating SRID 5715...

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.38 SDO_CS.UPDATE_WKTS_FOR_EPSG_ELLIPS

#### Format

    SDO_CS.UPDATE_WKTS_FOR_EPSG_ELLIPS(
         ellipsoid_id  IN NUMBER);

#### Description

Updates the well-known text (WKT) description for all EPSG coordinate reference systems associated with a specified ellipsoid.

#### Parameters

ellipsoid_id
The ID of the ellipsoid. Must match a value in the ELLIPSOID_ID column of the SDO_ELLIPSOIDS table (described in [SDO_ELLIPSOIDS Table](coordinate-systems-concepts.md)).

#### Usage Notes

For information about using procedures to update well-known text (WKT) description, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for all EPSG coordinate reference systems associated with ellipsoid 7100.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_EPSG_ELLIPS(7001);
    Updating SRID 4001...
    Updating SRID 4188...
    Updating SRID 29901...
    Updating SRID 61886405...
    Updating SRID 4277...
    Updating SRID 27700...
    Updating SRID 62776405...
    Updating SRID 4278...
    Updating SRID 62786405...
    Updating SRID 4279...
    Updating SRID 62796405...

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.39 SDO_CS.UPDATE_WKTS_FOR_EPSG_OP

#### Format

    SDO_CS.UPDATE_WKTS_FOR_EPSG_OP(
         coord_op_id  IN NUMBER);

#### Description

Updates the well-known text (WKT) description for all EPSG coordinate reference systems associated with a specified coordinate transformation operation.

#### Parameters

coord_op_id
The ID of the SRID of the coordinate transformation operation. Must match a value in the COORD_OP_ID column of the SDO_COORD_OP_PARAM_VALS table (described in [SDO_COORD_OP_PARAM_VALS Table](coordinate-systems-concepts.md)).

#### Usage Notes

For information about using procedures to update well-known text (WKT) description, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for all EPSG coordinate reference systems associated with coordinate transformation operation 2000067.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_EPSG_OP(2000067);
    Updating SRID 20000671...

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.40 SDO_CS.UPDATE_WKTS_FOR_EPSG_PARAM

#### Format

    SDO_CS.UPDATE_WKTS_FOR_EPSG_PARAM(
         coord_op_id  IN NUMBER,
         parameter_id IN NUMBER);

#### Description

Updates the well-known text (WKT) description for all EPSG coordinate reference systems associated with a specified coordinate transformation operation and parameter for transformation operations.

#### Parameters

coord_op_id
The ID of the SRID of the coordinate transformation operation. Must match a value in the COORD_OP_ID column of the SDO_COORD_OP_PARAM_VALS table (described in [SDO_COORD_OP_PARAM_VALS Table](coordinate-systems-concepts.md)).

parameter_id
The ID of the SRID of the parameter for transformation operations. Must match a value in the PARAMETER_ID column of the SDO_COORD_OP_PARAM_VALS table (described in [SDO_COORD_OP_PARAM_VALS Table](coordinate-systems-concepts.md)) where the COORD_OP_ID column value is equal to the `coord_op_id` parameter value.

#### Usage Notes

For information about using procedures to update well-known text (WKT) description, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for all EPSG coordinate reference systems associated with coordinate transformation operation 9601 and parameter 8602.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_EPSG_PARAM(9601, 8602);

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.41 SDO_CS.UPDATE_WKTS_FOR_EPSG_PM

#### Format

    SDO_CS.UPDATE_WKTS_FOR_EPSG_PM(
         prime_meridian_id IN NUMBER);

#### Description

Updates the well-known text (WKT) description for all EPSG coordinate reference systems associated with a specified prime meridian.

#### Parameters

prime_meridian_id
The ID of the prime meridian. Must match a value in the PRIME_MERIDIAN_ID column in the SDO_PRIME_MERIDIANS table (described in [SDO_PRIME_MERIDIANS Table](coordinate-systems-concepts.md)).

#### Usage Notes

For information about using procedures to update well-known text (WKT) description, see [Procedures for Updating the Well-Known Text](coordinate-systems-concepts.md).

#### Examples

The following example updates the WKT description for all EPSG coordinate reference systems associated with prime meridian 8902.

    EXECUTE SDO_CS.UPDATE_WKTS_FOR_EPSG_PM(8902);
    Updating SRID 4803...
    Updating SRID 20790...
    Updating SRID 20791...
    Updating SRID 68036405...
    Updating SRID 4904...
    Updating SRID 2963...
    Updating SRID 69046405...

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.42 SDO_CS.VALIDATE_EPSG_MATRIX

#### Format

    SDO_CS.VALIDATE_EPSG_MATRIX(
         method_id    IN NUMBER,
         parameter_id IN NUMBER,
         matrix       IN CLOB
         ) RETURN VARCHAR2;

#### Description

Validates an EPSG matrix of NADCON, NTv2, or VERTCON format.

#### Parameters

method_id
EPSG method ID to which the matrix refers.

parameter_id
EPSG parameter id identifying the matrix, if an operation has more than one matrix, such as NADCON.

matrix
Matrix CLOB (loaded, using SDO_CS.LOAD_EPSG_MATRIX or manually).

#### Usage Notes

You can load an EPSG matrix using the SDO_CS.LOAD_EPSG_MATRIX procedure.

#### Examples

The following example loads an NTv2 matrix for operation 1703 ("NAD27 to WGS 84 (32)"). For an NTv2 operation, a single matrix is sufficient, assigned to parameter ID 8656.

    SQL> select
      m.coord_op_method_name "Method",
      vals.parameter_id "Parameter",
      sdo_cs.validate_epsg_matrix(m.coord_op_method_id, vals.parameter_id, vals.param_value_file) "Valid",
      count(*) "#"
    from
      sdo_coord_op_param_vals vals,
      sdo_coord_op_methods m
    where
      m.coord_op_method_id = vals.coord_op_method_id and
      not(vals.param_value_file is null)
    group by
      m.coord_op_method_name,
      vals.parameter_id,
      sdo_cs.validate_epsg_matrix(m.coord_op_method_id, vals.parameter_id, vals.param_value_file)
    order by
      m.coord_op_method_name,
      vals.parameter_id,
      sdo_cs.validate_epsg_matrix(m.coord_op_method_id, vals.parameter_id, vals.param_value_file);

    Method                                              Parameter Valid          #
    -------------------------------------------------- ---------- ----- ----------
    Geographic3D to Geographic2D+GravityRelatedHeight        8666 TRUE           2
    Geographic3D to GravityRelatedHeight (OSGM02)            8666 TRUE          14
    NADCON                                                   8657 TRUE         104
    NADCON                                                   8658 TRUE         104
    NTv2                                                     8656 TRUE           4
    Ordnance Survey National Transformation                  8664 TRUE           3

    6 rows selected.

**Parent topic:** SDO_CS Package (Coordinate System Transformation)

### 22.43 SDO_CS.VALIDATE_WKT

#### Format

    SDO_CS.VALIDATE_WKT(
         srid IN NUMBER
         ) RETURN VARCHAR2;

#### Description

Validates the well-known text (WKT) description associated with a specified SRID.

#### Parameters

srid
The SRID of the coordinate system whose well-known text (WKT) description is to be validated. An entry for the specified value must exist in the SDO_COORD_REF_SYS table (described in [SDO_COORD_REF_SYS Table](coordinate-systems-concepts.md)).

#### Usage Notes

This function returns the string 'TRUE' if the WKT description is valid. If the WKT description is invalid, this function returns a string in the format 'FALSE (\<position-number\>)', where \<position-number\> is the number of the character position in the WKT description where the first error occurs.

The WKT description is checked to see if it satisfies the requirements described in [Well-Known Text (WKT)](coordinate-systems-concepts.md).

#### Examples

The following example validates the WKT description of the coordinate system associated with SRID 81989000. The results show that the cause of the invalidity (or the first cause of the invalidity) starts at character position 181 in the WKT description. (SRID 81989000 is not associated with any established coordinate system. Rather, it is for a deliberately invalid coordinate system that was inserted into a test version of the MDSYS.CS_SRS table, and it is not included in the MDSYS.CS_SRS table that is shipped with Oracle Spatial and Graph.)

    SELECT SDO_CS.VALIDATE_WKT(81989000) FROM DUAL;

    SDO_CS.VALIDATE_WKT(81989000)
    --------------------------------------------------------------------------------
    FALSE (181)

**Parent topic:** SDO_CS Package (Coordinate System Transformation)
