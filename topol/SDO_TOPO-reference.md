## 3  SDO_TOPO Package Subprograms

The MDSYS.SDO_TOPO package contains subprograms (functions and procedures) that constitute part of the PL/SQL application programming interface (API) for the Spatial and Graph Topology Data Model feature. This package mainly contains subprograms for creating and managing topologies.

To use the subprograms in this chapter, you must understand the conceptual information about topology in [Topology Data Model Overview](topology-data-model-overview.md).

**Note:**

SDO_TOPO subprograms are supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](http://www.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

Another package, SDO_TOPO_MAP, mainly contains subprograms related to editing topologies. Reference information for the SDO_TOPO_MAP package is in [SDO_TOPO_MAP Package Subprograms](SDO_TOPO_MAP-reference.md).

The rest of this chapter provides reference information about the SDO_TOPO subprograms, listed in alphabetical order.

- SDO_TOPO.ADD_TOPO_GEOMETRY_LAYER
- SDO_TOPO.CREATE_TOPOLOGY
- SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER
- SDO_TOPO.DROP_TOPOLOGY
- SDO_TOPO.GET_FACE_BOUNDARY
- SDO_TOPO.GET_TOPO_OBJECTS
- SDO_TOPO.INITIALIZE_AFTER_IMPORT
- SDO_TOPO.INITIALIZE_METADATA
- SDO_TOPO.PREPARE_FOR_EXPORT
- SDO_TOPO.RELATE

**Parent topic:** [Topology Data Model](topology-data-model.md)

### 3.1 SDO_TOPO.ADD_TOPO_GEOMETRY_LAYER

#### Format

    SDO_TOPO.ADD_TOPO_GEOMETRY_LAYER(     
      topology                 IN VARCHAR2,      
      table_name               IN VARCHAR2,      
      column_name              IN VARCHAR2,      
      topo_geometry_layer_type IN VARCHAR2,      
      relation_table_storage   IN VARCHAR2 DEFAULT NULL,      
      child_layer_id           IN NUMBER DEFAULT NULL);

#### Description

Adds a topology geometry layer to a topology.

#### Parameters

topology
Topology to which to add the topology geometry layer containing the topology geometries in the specified column. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure.

table_name
Name of the topology geometry layer table containing the column specified in `column_name`.

column_name
Name of the column (of type SDO_TOPO_GEOMETRY) containing the topology geometries in the topology geometry layer to be added to the topology.

topo_geometry_layer_type
Type of topology geometry layer: POINT, LINE, CURVE, POLYGON, or COLLECTION.

relation_table_storage
Physical storage parameters used internally to create the \<topology-name\>\_RELATION\$ table (described in [Relationship Information Table](topology-data-model-overview.md)). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

child_layer_id
Layer ID number of the child topology geometry layer for this layer, if the topology has a topology geometry layer hierarchy. (Topology geometry layer hierarchy is explained in [Topology Geometry Layer Hierarchy](topology-data-model-overview.md).) If you do not specify this parameter and if the topology has a topology geometry layer hierarchy, the topology geometry layer is added to the lowest level (level 0) of the hierarchy.

If the topology does not have a topology geometry layer hierarchy, do not specify this parameter when adding any of the topology geometry layers.

#### Usage Notes

The first call to this procedure for a given topology creates the \<topology-name\>\_RELATION\$ table, which is described in [Relationship Information Table](topology-data-model-overview.md).

This procedure automatically performs a commit operation, and therefore it cannot be rolled back. To delete the topology that you just created, call the SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER procedure.

The procedure creates a spatial index on the spatial features in the topology geometries, and a B-tree index on the combination of `tg_type` and `tg_id` in the topology geometries.

Users granted CONNECT and RESOURCE roles must also be granted the CREATE VIEW privilege to call the procedure. This is necessary because effective with Oracle Database 10g Release 2, the CONNECT role privilege reduction feature removed the following privileges from the CONNECT role: CREATE CLUSTER, CREATE DATABASE LINK, CREATE SEQUENCE, ALTER SESSION, CREATE SYNONYM, CREATE TABLE, and CREATE VIEW.

The topology geometry layer table (`table_name` parameter) cannot be an object table.

An exception is raised if `topology`, `table_name`, or `column_name` does not exist, or if `topo_geometry_layer_type` is not one of the supported values.

#### Examples

The following example adds a topology geometry layer to the `CITY_DATA` topology. The topology geometry layer consists of polygon geometries in the FEATURE column of the LAND_PARCELS table. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.ADD_TOPO_GEOMETRY_LAYER('CITY_DATA', 'LAND_PARCELS', 'FEATURE', 'POLYGON');

**Parent topic:** SDO_TOPO Package Subprograms

### 3.2 SDO_TOPO.CREATE_TOPOLOGY

#### Format

    SDO_TOPO.CREATE_TOPOLOGY(     
      topology                 IN VARCHAR2,      
      tolerance                IN NUMBER,      
      srid                     IN NUMBER DEFAULT NULL,      
      node_table_storage       IN VARCHAR2 DEFAULT NULL,      
      edge_table_storage       IN VARCHAR2 DEFAULT NULL,      
      face_table_storage       IN VARCHAR2 DEFAULT NULL,      
      history_table_storage    IN VARCHAR2 DEFAULT NULL.      
      digits_right_of_decimal  IN VARCHAR2 DEFAULT 16);

#### Description

Creates a topology.

#### Parameters

topology
Name of the topology to be created. Must not exceed 20 characters.

tolerance
Tolerance value associated with topology geometries in the topology. (Tolerance is explained in [Tolerance in the Topology Data Model](topology-data-model-overview.md).)

srid
Coordinate system (spatial reference system) associated with all topology geometry layers in the topology. The default is null: no coordinate system is associated; otherwise, it must be a value from the SRID column of the SDO_COORD_REF_SYS table (described in [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md)).

node_table_storage
Physical storage parameters used internally to create the \<topology-name\>\_NODE\$ table (described in [Node Information Table](topology-data-model-overview.md)). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

edge_table_storage
Physical storage parameters used internally to create the \<topology-name\>\_EDGE\$ table (described in [Edge Information Table](topology-data-model-overview.md)). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

face_table_storage
Physical storage parameters used internally to create the \<topology-name\>\_FACE\$ table (described in [Face Information Table](topology-data-model-overview.md)). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

history_table_storage
Physical storage parameters used internally to create the \<topology-name\>\_HISTORY\$ table (described in [History Information Table](topology-data-model-overview.md). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

digits_right_of_decimal
The number of digits permitted to the right of the decimal point in the expression of any coordinate position when features are added to an existing topology. All incoming features (those passed as arguments to the `addLinearGeometry`, `addPolygonGeometry`, or `addPointGeometry` method in the Java API or the equivalent PL/SQL subprograms) will be automatically snapped (truncated) to the number of digits right of the decimal that is specified in this parameter. The default is 16.

This value should be set to match the last digit right of the decimal point that is considered valid based on the accuracy of the incoming data. This mechanism is provided to improve the stability of the computational geometry during the feature insertion process, and to minimize the creation of sliver polygons and other undesired results.

#### Usage Notes

This procedure creates the \<topology-name\>\_EDGE\$, \<topology-name\>\_NODE\$, \<topology-name\>\_FACE\$, and \<topology-name\>\_HISTORY\$ tables, which are described in [Topology Data Model Tables](topology-data-model-overview.md), and it creates B-tree indexes on the primary keys of these tables. This procedure also creates the metadata for the topology.

In the `srid` parameter, you can specify a geodetic coordinate system; however, all Spatial and Graph internal operations on the topology will use Cartesian (not geodetic) arithmetic operations. (Geodetic and non-geodetic coordinate systems are discussed in [Oracle Spatial and Graph Developer's Guide](../spatl/coordinate-systems-concepts.md).)

Node, edge, face, and history tables are created without partitions; however, you can alter any of these tables to make it partitioned. You can also create a partitioned spatial index on a partitioned table, as explained in [Oracle Spatial and Graph Developer's Guide](../spatl/indexing-querying-spatial-data.md).

This procedure automatically performs a commit operation, and therefore it cannot be rolled back. To delete the topology that you just created, call the SDO_TOPO.DROP_TOPOLOGY procedure.

An exception is raised if the topology already exists.

#### Examples

The following example creates a topology named `CITY_DATA`. The spatial geometries in this topology have a tolerance value of 0.5 and use the `WGS 84` coordinate system (longitude and latitude, SRID value 8307). (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.CREATE_TOPOLOGY('CITY_DATA', 0.5, 8307);

**Parent topic:** SDO_TOPO Package Subprograms

### 3.3 SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER

#### Format

    SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER(     
      topology    IN VARCHAR2,      
      table_name  IN VARCHAR2,      
      column_name IN VARCHAR2);

#### Description

Deletes a topology geometry layer from a topology.

#### Parameters

topology
Topology from which to delete the topology geometry layer containing the topology geometries in the specified column. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure.

table_name
Name of the table containing the column specified in `column_name`.

column_name
Name of the column containing the topology geometries in the topology geometry layer to be deleted from the topology.

#### Usage Notes

This procedure deletes data associated with the specified topology geometry layer from the \<topology-name\>\_RELATION\$ table (described in [Relationship Information Table](topology-data-model-overview.md)). If this procedure is deleting the only remaining topology geometry layer from the topology, it also deletes the \<topology-name\>\_RELATION\$ table.

This procedure automatically performs a commit operation, and therefore it cannot be rolled back.

#### Examples

The following example deletes the topology geometry layer that is based on the geometries in the FEATURE column of the LAND_PARCELS table from the topology named `CITY_DATA`. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER('CITY_DATA', 'LAND_PARCELS', 'FEATURE');

**Parent topic:** SDO_TOPO Package Subprograms

### 3.4 SDO_TOPO.DROP_TOPOLOGY

#### Format

    SDO_TOPO.DROP_TOPOLOGY(     
      topology  IN VARCHAR2);

#### Description

Deletes a topology.

#### Parameters

topology
Name of the topology to be deleted. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure.

#### Usage Notes

This procedure deletes the \<topology-name\>\_EDGE\$, \<topology-name\>\_NODE\$, \<topology-name\>\_FACE\$, \<topology-name\>\_NODE\$, \<topology-name\>\_RELATION\$, and \<topology-name\>\_HISTORY\$ tables (described in [Topology Data Model Tables](topology-data-model-overview.md)).

If there are no topology layers associated with the topology, the topology is removed from the Spatial and Graph metadata.

This procedure automatically performs a commit operation, and therefore it cannot be rolled back.

A database user that owns a topology cannot be deleted. Therefore, before you can use the DROP USER ... CASCADE statement on a database user that owns a topology, you must connect as that user and execute the SDO_TOPO.DROP_TOPOLOGY procedure.

An exception is raised if the topology contains any topology geometries from any topology geometry layers. If you encounter this exception, delete all topology geometry layers in the topology using the SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER procedure for each topology geometry layer, and then drop the topology.

#### Examples

The following example drops the topology named `CITY_DATA`. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.DROP_TOPOLOGY('CITY_DATA');

**Parent topic:** SDO_TOPO Package Subprograms

### 3.5 SDO_TOPO.GET_FACE_BOUNDARY

#### Format

    SDO_TOPO.GET_FACE_BOUNDARY(     
      topology   IN VARCHAR2,      
      face_id    IN NUMBER,      
      all_edges  IN VARCHAR2 DEFAULT 'FALSE'      
    ) RETURN SDO_LIST_TYPE;

#### Description

Returns a list of the signed ID numbers of the edges for the specified face.

#### Parameters

topology
Name of the topology that contains the face. Must not exceed 20 characters.

face_id
Face ID value of the face.

all_edges
`TRUE` includes all edges that bound the face (that is, that have the face on one or both sides); `FALSE` (the default) includes only edges that constitute the external boundary of the face. (See the examples for this function.)

#### Usage Notes

None.

#### Examples

The following examples return the ID numbers of the edges for the face whose face ID value is 1. The first example accepts the default value of '`FALSE'` for the `all_edges` parameter. The second example specifies `'TRUE'` for `all_edges`, and the list includes the ID numbers of the boundary edge and the two isolated edges on the face. (The examples refer to definitions and data from [Topology Examples (PL/SQL)](topology-data-model-overview.md).)

    -- Get the boundary of face with face_id 1.
    SELECT SDO_TOPO.GET_FACE_BOUNDARY('CITY_DATA', 1) FROM DUAL;

    SDO_TOPO.GET_FACE_BOUNDARY('CITY_DATA',1)
    --------------------------------------------------------------------------------
    SDO_LIST_TYPE(1)

    -- Specify 'TRUE' for the all_edges parameter.
    SELECT SDO_TOPO.GET_FACE_BOUNDARY('CITY_DATA', 1, 'TRUE') FROM DUAL;

    SDO_TOPO.GET_FACE_BOUNDARY('CITY_DATA',1,'TRUE')
    --------------------------------------------------------------------------------
    SDO_LIST_TYPE(1, -26, 25)

**Parent topic:** SDO_TOPO Package Subprograms

### 3.6 SDO_TOPO.GET_TOPO_OBJECTS

#### Format

    SDO_TOPO.GET_TOPO_OBJECTS(     
      topology  IN VARCHAR2,      
      geometry  IN SDO_GEOMETRY      
    ) RETURN SDO_TOPO_OBJECT_ARRAY;

or

    SDO_TOPO.GET_TOPO_OBJECTS(     
      topology               IN VARCHAR2,      
      topo_geometry_layer_id IN NUMBER,      
      topo_geometry_id       IN NUMBER      
    ) RETURN SDO_TOPO_OBJECT_ARRAY;

#### Description

Returns an array of SDO_TOPO_OBJECT objects that interact with a specified geometry object or topology geometry object.

#### Parameters

topology
Name of the topology. Must not exceed 20 characters.

geometry
Geometry object to be checked.

topo_geometry_layer_id
ID number of the topology geometry layer that contains the topology geometry object to be checked.

topo_geometry_id
ID number of the topology geometry object to be checked.

#### Usage Notes

The SDO_TOPO_OBJECT_ARRAY data type is described in [Constructors for Insert Operations: Specifying Topological Elements](topology-data-model-overview.md).

For a topology that has a topology geometry layer hierarchy, this function works for all levels of the hierarchy, and it always returns the leaf-level (lowest-level) objects. (Topology geometry layer hierarchy is explained in [Topology Geometry Layer Hierarchy](topology-data-model-overview.md).)

#### Examples

The following example returns the topology geometry objects that interact with land parcel P2 in the `CITY_DATA` topology. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    -- CITY_DATA layer, land parcels (topo_geometry_ layer_id = 1),
    -- parcel P2 (topo_geometry_id = 2)
    SELECT SDO_TOPO.GET_TOPO_OBJECTS('CITY_DATA', 1, 2) FROM DUAL;

    SDO_TOPO.GET_TOPO_OBJECTS('CITY_DATA',1,2)(TOPO_ID, TOPO_TYPE)
    --------------------------------------------------------------------------------
    SDO_TOPO_OBJECT_ARRAY(SDO_TOPO_OBJECT(9, 1), SDO_TOPO_OBJECT(10, 1), SDO_TOPO_OB
    JECT(13, 1), SDO_TOPO_OBJECT(14, 1), SDO_TOPO_OBJECT(17, 1), SDO_TOPO_OBJECT(18,
     1), SDO_TOPO_OBJECT(6, 2), SDO_TOPO_OBJECT(7, 2), SDO_TOPO_OBJECT(8, 2), SDO_TO
    PO_OBJECT(9, 2), SDO_TOPO_OBJECT(10, 2), SDO_TOPO_OBJECT(11, 2), SDO_TOPO_OBJECT
    (12, 2), SDO_TOPO_OBJECT(13, 2), SDO_TOPO_OBJECT(14, 2), SDO_TOPO_OBJECT(17, 2),
     SDO_TOPO_OBJECT(18, 2), SDO_TOPO_OBJECT(19, 2), SDO_TOPO_OBJECT(20, 2), SDO_TOP
    O_OBJECT(-6, 2), SDO_TOPO_OBJECT(-7, 2), SDO_TOPO_OBJECT(-8, 2), SDO_TOPO_OBJECT
    (-9, 2), SDO_TOPO_OBJECT(-10, 2), SDO_TOPO_OBJECT(-11, 2), SDO_TOPO_OBJECT(-12,
    2), SDO_TOPO_OBJECT(-13, 2), SDO_TOPO_OBJECT(-14, 2), SDO_TOPO_OBJECT(-17, 2), S
    DO_TOPO_OBJECT(-18, 2), SDO_TOPO_OBJECT(-19, 2), SDO_TOPO_OBJECT(-20, 2), SDO_TO
    PO_OBJECT(-1, 3), SDO_TOPO_OBJECT(3, 3), SDO_TOPO_OBJECT(4, 3), SDO_TOPO_OBJECT(
    5, 3), SDO_TOPO_OBJECT(6, 3), SDO_TOPO_OBJECT(7, 3), SDO_TOPO_OBJECT(8, 3))

**Parent topic:** SDO_TOPO Package Subprograms

### 3.7 SDO_TOPO.INITIALIZE_AFTER_IMPORT

#### Format

    SDO_TOPO.INITIALIZE_AFTER_IMPORT(     
      topology  IN VARCHAR2);

#### Description

Creates (initializes) a topology that was imported from another database.

#### Parameters

topology
Name of the topology to be created. The topology must have been exported from a source database.

#### Usage Notes

This procedure creates the specified topology and all related database structures, adjusts (if necessary) the topology ID values in all feature tables, and creates the feature layers in the correct order.

Before calling this procedure, connect to the database as the user for the schema that is to own the topology to be created.

You must use this procedure after following all other required steps for exporting and importing the topology, as explained in [Exporting and Importing Topology Data](topology-data-model-overview.md).

#### Examples

The following example creates the topology named `CITY_DATA`, using information from the imported tables, including CITY_DATA_EXP\$. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.INITIALIZE_AFTER_IMPORT('CITY_DATA');

**Parent topic:** SDO_TOPO Package Subprograms

### 3.8 SDO_TOPO.INITIALIZE_METADATA

#### Format

    SDO_TOPO.INITIALIZE_METADATA(     
      topology  IN VARCHAR2);

#### Description

Initializes the topology metadata: sets sequence information for the node, edge, and face tables, and creates (or re-creates) required indexes on these tables.

#### Parameters

topology
Name of the topology for which to initialize the sequences. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure.

#### Usage Notes

You should run this procedure after loading data into the node, edge, or face tables, to initialize the sequences for these tables with numeric values 2 higher than the highest ID values stored in those tables. This ensures that no attempt is made to reuse the unique ID values in these tables. (The node, edge, and face tables are described in [Topology Data Model Tables](topology-data-model-overview.md).)

This procedure creates spatial indexes on the geometry or MBR geometry columns in the node, edge, and face tables. If the indexes were dropped before a bulk load operation, running this procedure after the bulk load will re-create these indexes.

#### Examples

The following example initializes the metadata for the topology named `CITY_DATA`. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.INITIALIZE_METADATA('CITY_DATA');

**Parent topic:** SDO_TOPO Package Subprograms

### 3.9 SDO_TOPO.PREPARE_FOR_EXPORT

#### Format

    SDO_TOPO.PREPARE_FOR_EXPORT(     
      topology  IN VARCHAR2);

#### Description

Prepares a topology to be exported to another database.

#### Parameters

topology
Name of the topology to be prepared for export. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure.

#### Usage Notes

This procedure prepares the specified topology in the current database (the source database) to be exported to another database (the target database).

This procedure creates a table in the current schema with a table name in the format \<topology-name\>\_EXP\$. This table contains the same columns as the USER_SDO_TOPO_INFO and ALL_SDO_TOPO_INFO views. These columns are described in [Table 1-8](topology-data-model-overview.md) in [xxx_SDO_TOPO_INFO Views](topology-data-model-overview.md).

Before calling this procedure, connect to the database as the owner of the topology.

For information about exporting and importing topologies, including the steps to be followed, see [Exporting and Importing Topology Data](topology-data-model-overview.md).

#### Examples

The following example prepares the topology named `CITY_DATA` for export to a target database. (The example refers to definitions and data from [Topology Built from Topology Data](topology-data-model-overview.md).)

    EXECUTE SDO_TOPO.PREPARE_FOR_EXPORT('CITY_DATA');

**Parent topic:** SDO_TOPO Package Subprograms

### 3.10 SDO_TOPO.RELATE

#### Format

    SDO_TOPO.RELATE(     
      geom1  IN SDO_TOPO_GEOMETRY,      
      geom2  IN SDO_TOPO_GEOMETRY,      
      mask   IN VARCHAR2      
    ) RETURN VARCHAR2;

or

    SDO_TOPO.RELATE(
      feature1  IN SDO_TOPO_GEOMETRY,
      feature2  IN SDO_GEOMETRY,
      mask      IN VARCHAR2
    ) RETURN VARCHAR2;

or

    SDO_TOPO.RELATE(
      geom            IN SDO_TOPO_GEOMETRY,
      topo_elem_array IN SDO_TOPO_OBJECT_ARRAY,
      mask            IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Examines two topology geometry objects, or a topology geometry and a spatial geometry, or a topology geometry and a topology object array (SDO_TOPO_OBJECT_ARRAY object), to determine their spatial relationship.

#### Parameters

geom1
Topology geometry object.

geom2
Topology geometry object.

feature1
Topology geometry object.

feature2
Spatial geometry object.

geom
Topology geometry object.

topo_elem_array
Topology object array (of type SDO_TOPO_OBJECT_ARRAY, which is described in [Constructors for Insert Operations: Specifying Topological Elements](topology-data-model-overview.md)).

mask
Specifies one or more relationships to check. See the list of keywords in the Usage Notes.

#### Usage Notes

The topology operators (described in [Topology Operators](topology-data-model-overview.md)) provide better performance than the SDO_TOPO.RELATE function if you are checking a large number of objects; however, if you are checking just two objects or a small number, the SDO_TOPO.RELATE function provides better performance. In addition, sometimes you may need to use the SDO_TOPO.RELATE function instead of a topology operator. For example, you cannot specify the DETERMINE mask keyword with the topology operators.

The following keywords can be specified in the `mask` parameter to determine the spatial relationship between two objects:

- ANYINTERACT: Returns TRUE if the objects are not disjoint.

- CONTAINS: Returns TRUE if the second object is entirely within the first object and the object boundaries do not touch; otherwise, returns FALSE.

- COVEREDBY: Returns TRUE if the first object is entirely within the second object and the object boundaries touch at one or more points; otherwise, returns FALSE.

- COVERS: Returns TRUE if the second object is entirely within the first object and the boundaries touch in one or more places; otherwise, returns FALSE.

- DETERMINE: Returns the one relationship keyword that best matches the geometries.

- DISJOINT: Returns TRUE if the objects have no common boundary or interior points; otherwise, returns FALSE.

- EQUAL: Returns TRUE if the objects share every point of their boundaries and interior, including any holes in the objects; otherwise, returns FALSE.

- INSIDE: Returns TRUE if the first object is entirely within the second object and the object boundaries do not touch; otherwise, returns FALSE.

- ON: Returns TRUE if the boundary and interior of a line (the first object) is completely on the boundary of a polygon (the second object); otherwise, returns FALSE.

- OVERLAPBDYDISJOINT: Returns TRUE if the objects overlap, but their boundaries do not interact; otherwise, returns FALSE.

- OVERLAPBDYINTERSECT: Returns TRUE if the objects overlap, and their boundaries intersect in one or more places; otherwise, returns FALSE.

- TOUCH: Returns TRUE if the two objects share a common boundary point, but no interior points; otherwise, returns FALSE.

Values for `mask` (except for DETERMINE) can be combined using the logical Boolean operator OR. For example, 'INSIDE + TOUCH' returns the string TRUE or FALSE depending on the outcome of the test.

#### Examples

The following example finds whether or not the ANYINTERACT relationship exists between each topology geometry object in the CITY_STREETS table and the `P3` land parcel (that is, which streets interact with that land parcel). (The example refers to definitions and data from [Topology Examples (PL/SQL)](topology-data-model-overview.md). The output is reformatted for readability.)

    SELECT c.feature_name,
      SDO_TOPO.RELATE(c.feature, l.feature, 'anyinteract') Any_Interaction
      FROM city_streets c, land_parcels l WHERE l.feature_name = 'P3';

    FEATURE_NAME  ANY_INTERACTION
    ------------  ---------------
    R1            TRUE
    R2            FALSE
    R3            FALSE
    R4            FALSE

The following example finds whether or not the ANYINTERACT relationship exists between each topology geometry object in the CITY_STREETS table and an SDO_TOPO_OBJECT_ARRAY object that happens to be identical to the land parcel feature named P3. (This example uses definitions and data from [Topology Examples (PL/SQL)](topology-data-model-overview.md).) The output is identical to that in the preceding example, and is reformatted for readability.

    SELECT c.feature_name,
      SDO_TOPO.RELATE(c.feature,
        SDO_TOPO_OBJECT_ARRAY (SDO_TOPO_OBJECT (5, 3), SDO_TOPO_OBJECT (8, 3)),
        'anyinteract') Any_Interaction
      FROM city_streets c, land_parcels l WHERE l.feature_name = 'P3';

    FEATURE_NAME  ANY_INTERACTION
    ------------  ---------------
    R1            TRUE
    R2            FALSE
    R3            FALSE
    R4            FALSE

**Parent topic:** SDO_TOPO Package Subprograms
