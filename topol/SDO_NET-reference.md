## 6  SDO_NET Package Subprograms

The MDSYS.SDO_NET package contains subprograms (functions and procedures) for managing networks.

To use the subprograms in this chapter, you must understand the conceptual information in [Network Data Model Graph Overview](network-data-model-graph-overview.md).

**Note:**

SDO_NET subprograms are supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](http://www.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

For a listing of the subprograms grouped in logical categories, see [Network Data Model Graph PL/SQL Interface](network-data-model-graph-overview.md). The rest of this chapter provides reference information about the subprograms, listed in alphabetical order.

- SDO_NET.ADD_CHILD_FEATURE
- SDO_NET.ADD_CHILD_FEATURES
- SDO_NET.ADD_FEATURE
- SDO_NET.ADD_FEATURE_ELEMENT
- SDO_NET.ADD_FEATURE_ELEMENTS
- SDO_NET.ADD_FEATURE_LAYER
- SDO_NET.COMPUTE_PATH_GEOMETRY
- SDO_NET.COPY_NETWORK
- SDO_NET.CREATE_LINK_TABLE
- SDO_NET.CREATE_LOGICAL_NETWORK
- SDO_NET.CREATE_LRS_NETWORK
- SDO_NET.CREATE_LRS_TABLE
- SDO_NET.CREATE_NODE_TABLE
- SDO_NET.CREATE_PARTITION_TABLE
- SDO_NET.CREATE_PATH_LINK_TABLE
- SDO_NET.CREATE_PATH_TABLE
- SDO_NET.CREATE_SDO_NETWORK
- SDO_NET.CREATE_SUBPATH_TABLE
- SDO_NET.CREATE_TOPO_NETWORK
- SDO_NET.DELETE_CHILD_FEATURES
- SDO_NET.DELETE_CHILD_FEATURES_AT
- SDO_NET.DELETE_DANGLING_FEATURES
- SDO_NET.DELETE_DANGLING_LINKS
- SDO_NET.DELETE_DANGLING_NODES
- SDO_NET.DELETE_FEATURE_ELEMENTS
- SDO_NET.DELETE_FEATURE_ELEMENTS_AT
- SDO_NET.DELETE_FEATURES
- SDO_NET.DELETE_LINK
- SDO_NET.DELETE_NODE
- SDO_NET.DELETE_PATH
- SDO_NET.DELETE_PHANTOM_FEATURES
- SDO_NET.DELETE_SUBPATH
- SDO_NET.DEREGISTER_CONSTRAINT
- SDO_NET.DROP_FEATURE_LAYER
- SDO_NET.DROP_NETWORK
- SDO_NET.FIND_CONNECTED_COMPONENTS
- SDO_NET.GENERATE_NODE_LEVELS
- SDO_NET.GENERATE_PARTITION_BLOB
- SDO_NET.GENERATE_PARTITION_BLOBS
- SDO_NET.GET_CHILD_FEATURE_IDS
- SDO_NET.GET_CHILD_LINKS
- SDO_NET.GET_CHILD_NODES
- SDO_NET.GET_DANGLING_FEATURES
- SDO_NET.GET_DANGLING_LINKS
- SDO_NET.GET_DANGLING_NODES
- SDO_NET.GET_FEATURE_ELEMENTS
- SDO_NET.GET_FEATURE_LAYER_ID
- SDO_NET.GET_FEATURES_ON_LINKS
- SDO_NET.GET_FEATURES_ON_NODES
- SDO_NET.GET_GEOMETRY_TYPE
- SDO_NET.GET_IN_LINKS
- SDO_NET.GET_INVALID_LINKS
- SDO_NET.GET_INVALID_NODES
- SDO_NET.GET_INVALID_PATHS
- SDO_NET.GET_ISOLATED_NODES
- SDO_NET.GET_LINK_COST_COLUMN
- SDO_NET.GET_LINK_DIRECTION
- SDO_NET.GET_LINK_GEOM_COLUMN
- SDO_NET.GET_LINK_GEOMETRY
- SDO_NET.GET_LINK_TABLE_NAME
- SDO_NET.GET_LINKS_IN_PATH
- SDO_NET.GET_LRS_GEOM_COLUMN
- SDO_NET.GET_LRS_LINK_GEOMETRY
- SDO_NET.GET_LRS_NODE_GEOMETRY
- SDO_NET.GET_LRS_TABLE_NAME
- SDO_NET.GET_NETWORK_TYPE
- SDO_NET.GET_NO_OF_HIERARCHY_LEVELS
- SDO_NET.GET_NO_OF_LINKS
- SDO_NET.GET_NO_OF_NODES
- SDO_NET.GET_NODE_DEGREE
- SDO_NET.GET_NODE_GEOM_COLUMN
- SDO_NET.GET_NODE_GEOMETRY
- SDO_NET.GET_NODE_IN_DEGREE
- SDO_NET.GET_NODE_OUT_DEGREE
- SDO_NET.GET_NODE_TABLE_NAME
- SDO_NET.GET_OUT_LINKS
- SDO_NET.GET_PARENT_FEATURE_IDS
- SDO_NET.GET_PARTITION_SIZE
- SDO_NET.GET_PATH_GEOM_COLUMN
- SDO_NET.GET_PATH_TABLE_NAME
- SDO_NET.GET_PERCENTAGE
- SDO_NET.GET_PHANTOM_FEATURES
- SDO_NET.GET_PT
- SDO_NET.IS_HIERARCHICAL
- SDO_NET.IS_LINK_IN_PATH
- SDO_NET.IS_LOGICAL
- SDO_NET.IS_NODE_IN_PATH
- SDO_NET.IS_SPATIAL
- SDO_NET.LOAD_CONFIG
- SDO_NET.LOGICAL_PARTITION
- SDO_NET.LOGICAL_POWERLAW_PARTITION
- SDO_NET.LRS_GEOMETRY_NETWORK
- SDO_NET.NETWORK_EXISTS
- SDO_NET.POST_XML
- SDO_NET.REGISTER_CONSTRAINT
- SDO_NET.SDO_GEOMETRY_NETWORK
- SDO_NET.SET_LOGGING_LEVEL
- SDO_NET.SET_MAX_JAVA_HEAP_SIZE
- SDO_NET.SPATIAL_PARTITION
- SDO_NET.TOPO_GEOMETRY_NETWORK
- SDO_NET.UPDATE_FEATURE
- SDO_NET.UPDATE_FEATURE_ELEMENT
- SDO_NET.VALIDATE_LINK_SCHEMA
- SDO_NET.VALIDATE_LRS_SCHEMA
- SDO_NET.VALIDATE_NETWORK
- SDO_NET.VALIDATE_NODE_SCHEMA
- SDO_NET.VALIDATE_PARTITION_SCHEMA
- SDO_NET.VALIDATE_PATH_SCHEMA
- SDO_NET.VALIDATE_SUBPATH_SCHEMA

**Parent topic:** [Network Data Model](network-data-model.md)

### 6.1 SDO_NET.ADD_CHILD_FEATURE

#### Format

    SDO_NET.ADD_CHILD_FEATURE(
         parent_layer_id   IN NUMBER,
         parent_feature_id IN NUMBER,
         child_layer_id    IN NUMBER,
         child_feature_id  IN SDO_NET_LAYER_FEAT,
         sequence_number   IN NUMBER DEFAULT NULL,
         check_integrity   IN BOOLEAN DEFAULT TRUE);

#### Description

Associates a feature as a child feature of a specified parent feature.

#### Parameters

parent_layer_id
ID of the parent feature layer.

parent_feature_id
ID of the feature that is to become the parent feature of the specified child feature.

child_layer_id
ID of the child feature layer.

child_feature_id
ID of the feature to be associated as a child feature of the specified parent feature. (The SDO_NET_LAYER_FEAT type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

sequence_number
Sequence number of the `child_feature_id` feature in the child feature layer. If this parameter is null, a sequence number after the last current number is assigned.

check_integrity
`TRUE` (the default) checks if the child feature exists; and if it does not exist, an error is generated. `FALSE` does not check if the child feature exists.

#### Usage Notes

The specified child feature must already exist.

To associate multiple features as child features, use the SDO_NET.ADD_CHILD_FEATURES procedure.

#### Examples

The following example adds a child feature at sequence number 2.

    DECLARE
      parent_layer_id NUMBER;
      parent_feature_id NUMBER := 1;
      child_layer_id NUMBER;
      child_feature_id NUMBER := 3;
    BEGIN
      parent_layer_id := sdo_net.get_feature_layer_id('GRID', 'PARENT_LAYER');
      child_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      sdo_net.add_child_feature(parent_layer_id, parent_feature_id, child_layer_id, child_feature_id, 2, true);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.2 SDO_NET.ADD_CHILD_FEATURES

#### Format

    SDO_NET.ADD_CHILD_FEATURES(
         parent_layer_id   IN NUMBER,
         parent_feature_id IN NUMBER,
         child_feature_ids IN SDO_NET_LAYER_FEAT_ARRAY,
         check_integrity   IN BOOLEAN DEFAULT TRUE);

#### Description

Associates multiple features as child features of a specified parent feature.

#### Parameters

parent_layer_id
ID of the parent feature layer.

parent_feature_id
ID of the feature that is to become the parent feature of the specified child features.

child_feature_ids
IDs of features to be associated as child features of the specified parent feature. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

check_integrity
`TRUE` (the default) checks if the child features exist; and if any do not exist, an error is generated. `FALSE` does not check if the child features exist.

#### Usage Notes

The specified child features must already exist.

To associate a single feature as a child feature, use the SDO_NET.ADD_CHILD_FEATURE procedure.

#### Examples

The following example adds two child features at the end of the parent feature.

    DECLARE
      parent_layer_id NUMBER;
      parent_feature_id NUMBER := 1;
      child_layer_id NUMBER;
      child_feature_ids SDO_NET_LAYER_FEAT_ARRAY := SDO_NET_LAYER_FEAT_ARRAY();
    BEGIN
      parent_layer_id := sdo_net.get_feature_layer_id('GRID', 'PARENT_LAYER');
      child_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      child_feature_ids.extend;
      child_feature_ids(1) := SDO_NET_LAYER_FEAT(child_layer_id, 4);
      child_feature_ids.extend;
      child_feature_ids(2) := SDO_NET_LAYER_FEAT(child_layer_id, 10);
      sdo_net.add_child_features(parent_layer_id, parent_feature_id, child_feature_ids, true);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.3 SDO_NET.ADD_FEATURE

#### Format

    SDO_NET.ADD_FEATURE(
         feature_layer_id  IN NUMBER,
         feature_id        IN NUMBER,
         feature_elements  IN SDO_NET_FEAT_ELEM_ARRAY DEFAULT NULL,
         child_feature_ids IN SDO_NET_LAYER_FEAT_ARRAY DEFAULT NULL,
         check_integrity   IN BOOLEAN DEFAULT TRUE);

#### Description

Adds a feature to a feature layer.

#### Parameters

feature_layer_id
ID of the feature layer to which to add the feature.

feature_id
ID of the feature to be added to the feature layer.

feature_elements
Feature elements of the feature to be added. If this parameter is null, no feature elements are defined for this feature. (The SDO_NET_FEAT_ELEM_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

child_feature_ids
IDs of the child features of the feature that are to be added along with the feature. If this parameter is null, no child features are to be added. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

check_integrity
`TRUE` (the default) checks if the input network elements exist; and if any do not exist, an error is generated. `FALSE` does not check if the input network elements exist.

#### Usage Notes

To update a feature in a feature layer, use the SDO_NET.UPDATE_FEATURE procedure.

#### Examples

The following example adds a feature associated with a point at 20% on link 1314.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      elements SDO_NET_FEAT_ELEM_ARRAY := SDO_NET_FEAT_ELEM_ARRAY();
      link_id NUMBER := 1314;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      elements.extend;
      elements(1) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.2, null);
      sdo_net.add_feature(feature_layer_id, feature_id, elements, null);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.4 SDO_NET.ADD_FEATURE_ELEMENT

#### Format

    SDO_NET.ADD_FEATURE_ELEMENT(
         feature_layer_id IN NUMBER,
         feature_id       IN NUMBER,
         feature_element  IN SDO_NET_FEAT_ELEM,
         sequence_number  IN NUMBER DEFAULT NULL,
         check_integrity  IN BOOLEAN DEFAULT TRUE);

#### Description

Adds a feature element to a feature.

#### Parameters

feature_layer_id
ID of the feature layer for the feature.

feature_id
ID of the feature.

feature_element
Feature element to be added to the feature. This feature element is automatically appended to the end of any existing feature elements in the feature. (The SDO_NET_FEAT_ELEM type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

sequence_number
Sequence number of the added feature element in the feature. If this parameter is null, a sequence number after the last current number is assigned.

check_integrity
`TRUE` (the default) checks if the input network elements exist; and if any do not exist, an error is generated. `FALSE` does not check if the input network elements exist.

#### Usage Notes

To add multiple feature elements to a feature in a single operation, use the SDO_NET.ADD_FEATURE_ELEMENTS procedure.

To update a feature element, use the SDO_NET.UPDATE_FEATURE_ELEMENT procedure.

#### Examples

The following example adds a point feature for node ID 13 at sequence number 2.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      feature_element SDO_NET_FEAT_ELEM;
      node_id NUMBER := 13;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      feature_element := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_PON, node_id, null, null);
      sdo_net.add_feature_element(feature_layer_id, feature_id, feature_element, 2);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.5 SDO_NET.ADD_FEATURE_ELEMENTS

#### Format

    SDO_NET.ADD_FEATURE_ELEMENTS(
         feature_layer_id IN NUMBER,
         feature_id       IN NUMBER,
         feature_elements IN SDO_NET_FEAT_ELEM,_ARRAY,
         check_integrity  IN BOOLEAN DEFAULT TRUE);

#### Description

Adds an array of feature elements to a feature.

#### Parameters

feature_layer_id
ID of the feature layer for the feature.

feature_id
ID of the feature.

feature_elements
Feature elements to be added to the feature. These feature elements are automatically appended to the end of any existing feature elements in the feature. (The SDO_NET_FEAT_ELEM_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

check_integrity
`TRUE` (the default) checks if the input network elements exist; and if any do not exist, an error is generated. `FALSE` does not check if the input network elements exist.

#### Usage Notes

To add a single feature element to a feature, use the SDO_NET.ADD_FEATURE_ELEMENT procedure.

#### Examples

The following example adds two point feature elements at the end of the feature elements associated with feature ID 1.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      elements SDO_NET_FEAT_ELEM_ARRAY := SDO_NET_FEAT_ELEM_ARRAY();
      link_id NUMBER := 1314;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      elements.extend;
      elements(1) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.7, null);
      elements.extend;
      elements(2) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.8, null);
      sdo_net.add_feature_elements(feature_layer_id, feature_id, elements);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.6 SDO_NET.ADD_FEATURE_LAYER

#### Format

    SDO_NET.ADD_FEATURE_LAYER(
         network_name IN VARCHAR2,
         feature_layer_name IN VARCHAR2,
         feature_layer_type IN VARCHAR2,
         feature_table      IN VARCHAR2,
         relation_table     IN VARCHAR2,
         hierarchy_table    IN VARCHAR2);

#### Description

Adds a feature layer.

#### Parameters

network_name
Name of the network.

feature_layer_name
Name of the feature layer.

feature_layer_type
Type of features in the layer (from [Table 5-1](network-data-model-graph-overview.md)).

feature_table
Name of the feature table (see [Feature Table](network-data-model-graph-overview.md)).

relation_table
Name of the feature element relationships table (see [Feature Element Relationships Table](network-data-model-graph-overview.md)).

hierarchy_table
Name of the feature hierarchy table (see [Feature Hierarchy Table](network-data-model-graph-overview.md)).

#### Usage Notes

A feature layer ID is automatically generated for the feature layer.

#### Examples

The following example creates a feature layer named `POI` (points of interest) of multipoints (`SDO_NET.FEAT_TYPE_MPOINT`).

    BEGIN
      sdo_net.add_feature_layer(
        'GRID',
        'POI',
        SDO_NET.FEAT_TYPE_MPOINT,
        'POI_FEAT$',
        'POI_REL$',
        NULL
      );
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.7 SDO_NET.COMPUTE_PATH_GEOMETRY

#### Format

    SDO_NET.COMPUTE_PATH_GEOMETRY(
         network   IN VARCHAR2,
         path_id   IN NUMBER,
         tolerance IN NUMBER
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the spatial geometry for a path.

#### Parameters

network
Network name.

path_id
Path ID number.

tolerance
Tolerance value associated with geometries in the network. (Tolerance is explained in Chapter 1 of [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md).) This value should be consistent with the tolerance values of the geometries in the link table and node table for the network.

#### Usage Notes

This function computes and returns the SDO_GEOMETRY object for the specified path.

This function and the SDO_NET_MEM.PATH.COMPUTE_GEOMETRY procedure (documented in SDO_NET Package Subprograms) both compute a path geometry, but they have the following differences:

- The SDO_NET.COMPUTE_PATH_GEOMETRY function computes the path from the links in the database, and does not use a network memory object. It returns the path geometry.

- The SDO_NET_MEM.PATH.COMPUTE_GEOMETRY procedure computes the path using a network memory object that has been loaded. It does not return the path geometry; you must use the SDO_NET_MEM.PATH.GET_GEOMETRY function to get the geometry.

#### Examples

The following example computes and returns the spatial geometry of the path with path ID 1 in the network named `SDO_NET1`, using a tolerance value of 0.005. The returned path geometry is a straight line from (1,1) to (15,1) because this path consists of a single link.

    SELECT SDO_NET.COMPUTE_PATH_GEOMETRY('SDO_NET1', 1, 0.005) FROM DUAL;

    SDO_NET.COMPUTE_PATH_GEOMETRY('SDO_NET1',1,0.005)(SDO_GTYPE, SDO_SRID, SDO_POINT
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1), SDO_ORDINATE_ARRAY(
    1, 1, 15, 1))

**Parent topic:** SDO_NET Package Subprograms

### 6.8 SDO_NET.COPY_NETWORK

#### Format

    SDO_NET.COPY_NETWORK(
         source_network     IN VARCHAR2,
         target_network     IN VARCHAR2,
         storage_parameters IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a copy of a network, including its metadata tables.

#### Parameters

source_network
Name of the network to be copied.

target_network
Name of the network to be created as a copy of `source_network`.

storage_parameters
Physical storage parameters used internally to create network tables. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure creates an entry in the xxx_SDO_NETWORK_METADATA views (described in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)) for `target_network` that has the same information as for `source_network`, except for the new network name.

This procedure also creates a new node table, link table, and path table (if a path table exists for `source_network`) for `target_network` based on the metadata and data in these tables for `source_network`. These tables have names in the form \<target-network\>\_NODE\$, \<target-network\>\_LINK\$, and \<target-network\>\_PATH\$. For example, if `target_network` has the value `ROADS_NETWORK2` and if `source_network` has a path table, the names of the created metadata tables are ROADS_NETWORK2_NODE\$, ROADS_NETWORK2_LINK\$, and ROADS_NETWORK2_PATH\$.

#### Examples

The following example creates a new network named `ROADS_NETWORK2` that is a copy of the network named `ROADS_NETWORK`.

    EXECUTE SDO_NET.COPY_NETWORK('ROADS_NETWORK', 'ROADS_NETWORK2');

**Parent topic:** SDO_NET Package Subprograms

### 6.9 SDO_NET.CREATE_LINK_TABLE

#### Format

    SDO_NET.CREATE_LINK_TABLE(
         table_name             IN VARCHAR2,
         geom_type              IN VARCHAR2,
         geom_column            IN VARCHAR2,
         cost_column            IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         add_bidirected_column  IN BOOLEAN DEFALT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a link table for a network.

#### Parameters

table_name
Name of the link table.

geom_type
For a spatial network, specify a value indicating the geometry type of links: `SDO_GEOMETRY` for non-LRS SDO_GEOMETRY objects, `LRS_GEOMETRY` for LRS SDO_GEOMETRY objects, or `TOPO_GEOMETRY` for SDO_TOPO_GEOMETRY objects.

geom_column
For a spatial network, the name of the column containing the geometry objects associated with the links. (If the `geom_type` value is not spelled correctly, the `geom_column` column is not included in the table.)

cost_column
Name of the column containing the cost values to be associated with the links.

no_of_hierarchy_levels
Number of hierarchy levels for links in the network. (For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).)

add_bidirected_column
`TRUE` adds a column named BIDIRECTED to the link table; `FALSE` (the default) does not add a column named BIDIRECTED to the link table.

storage_parameters
Physical storage parameters used internally to create the link table. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

The link table is described in [Link Table](network-data-model-graph-overview.md).

#### Examples

The following example creates a link table named ROADS_LINKS, with a geometry column named LINK_GEOMETRY that will contain LRS geometries, a cost column named COST, and a single hierarchy level.

    EXECUTE SDO_NET.CREATE_LINK_TABLE('ROADS_LINKS', 'LRS_GEOMETRY', 'LINK_GEOMETRY', 'COST', 1);

**Parent topic:** SDO_NET Package Subprograms

### 6.10 SDO_NET.CREATE_LOGICAL_NETWORK

#### Format

    SDO_NET.CREATE_LOGICAL_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_with_cost         IN BOOLEAN DEFAULT FALSE,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

    or

    SDO_NET.CREATE_LOGICAL_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_table_name        IN VARCHAR2,
         node_cost_column       IN VARCHAR2,
         link_table_name        IN VARCHAR2,
         link_cost_column       IN VARCHAR2,
         path_table_name        IN VARCHAR2,
         path_link_table_name   IN VARCHAR2,
         subpath_table_name     IN VARCHAR2,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a logical network, creates all necessary tables, and updates the network metadata.

#### Parameters

network
Network name.

no_of_hierarchy_levels
Number of hierarchy levels for links in the network. (For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).)

is_directed
A Boolean value. `TRUE` indicates that the links are directed; `FALSE` indicates that the links are undirected (not directed).

node_with_cost
A Boolean value. `TRUE` causes a column named COST to be included in the \<network-name\>\_NODE\$ table; `FALSE` (the default) causes a column named COST not to be included in the \<network-name\>\_NODE\$ table.

node_table_name
Name of the node table to be created. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a node table named \<network-name\>\_NODE\$ is created.

node_cost_column
Name of the cost column in the node table. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

link_table_name
Name of the link table to be created. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a link table named \<network-name\>\_LINK\$ is created.

link_cost_column
Name of the cost column in the link table. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

path_table_name
Name of the path table to be created. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path table named \<network-name\>\_PATH\$ is created.

path_link_table_name
Name of the path-link table to be created. (The path-link table is explained in [Path-Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path-link table named \<network-name\>\_PLINK\$ is created.

subpath_table_name
Name of the subpath table to be created. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).)

is_complex
Reserved for future use. Ignored for the current release.

storage_parameters
Physical storage parameters used internally to create network tables. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure provides a convenient way to create a logical network when the node, link, and optional related tables do not already exist. The procedure creates the network; creates the node, link, path, and path-link tables for the network; and inserts the appropriate information in the xxx_SDO_NETWORK_METADATA views (described in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

An exception is generated if any of the tables to be created already exists.

The procedure has two formats. The simpler format creates the tables using default values for the table name and the cost column name. The other format lets you specify names for the tables and the cost column.

As an alternative to using this procedure, you can create the network as follows: create the tables using the SDO_NET.CREATE_NODE_TABLE, SDO_NET.CREATE_LINK_TABLE, SDO_NET.CREATE_PATH_TABLE, and SDO_NET.CREATE_PATH_LINK_TABLE procedures; and insert the appropriate row in the USER_SDO_NETWORK_METADATA view.

#### Examples

The following example creates a directed logical network named `LOG_NET1`. The example creates the LOG_NET1_NODE\$, LOG_NET1_LINK\$,LOG_NET1_PATH\$, and LOG_NET1_PLINK\$ tables, and updates the xxx_SDO_NETWORK_METADATA views. Both the node and link tables contain a cost column named COST.

    EXECUTE SDO_NET.CREATE_LOGICAL_NETWORK('LOG_NET1', 1, TRUE, TRUE);

**Parent topic:** SDO_NET Package Subprograms

### 6.11 SDO_NET.CREATE_LRS_NETWORK

#### Format

    SDO_NET.CREATE_LRS_NETWORK(
         network IN VARCHAR2,
         lrs_table_name         IN VARCHAR2,
         lrs_geom_column        IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_with_cost         IN BOOLEAN DEFAULT FALSE,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

    or

    SDO_NET.CREATE_LRS_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_table_name        IN VARCHAR2,
         node_cost_column       IN VARCHAR2,
         link_table_name        IN VARCHAR2,
         link_cost_column       IN VARCHAR2,
         lrs_table_name         IN VARCHAR2,
         lrs_geom_column        IN VARCHAR2,
         path_table_name        IN VARCHAR2,
         path_geom_column       IN VARCHAR2,
         path_link_table_name   IN VARCHAR2,
         subpath_table_name     IN VARCHAR2,
         subpath_geom_column    IN VARCHAR2,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a spatial network containing LRS SDO_GEOMETRY objects, creates all necessary tables, and updates the network metadata.

#### Parameters

network
Network name.

lrs_table_name
Name of the table containing the LRS geometry column.

lrs_geom_column
Name of the column in `lrs_table_name` that contains LRS geometries (that is, SDO_GEOMETRY objects that include measure information for linear referencing).

is_directed
A Boolean value. `TRUE` indicates that the links are directed; `FALSE` indicates that the links are undirected (not directed).

no_of_hierarchy_levels
Number of hierarchy levels for links in the network. (For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).)

node_with_cost
A Boolean value. `TRUE` causes a column named COST to be included in the \<network-name\>\_NODE\$ table; `FALSE` (the default) causes a column named COST not to be included in the \<network-name\>\_NODE\$ table.

is_complex
Reserved for future use. Ignored for the current release.

node_table_name
Name of the node table to be created. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a node table named \<network-name\>\_NODE\$ is created.

node_cost_column
Name of the cost column in the node table. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

link_table_name
Name of the link table to be created. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a link table named \<network-name\>\_LINK\$ is created.

link_cost_column
Name of the cost column in the link table. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

path_table_name
Name of the path table to be created. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path table named \<network-name\>\_PATH\$ is created.

path_geom_column
Name of the geometry column in the path table. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named GEOMETRY.

path_link_table_name
Name of the path-link table to be created. (The path-link table is explained in [Path-Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path-link table named \<network-name\>\_PLINK\$ is created.

subpath_table_name
Name of the subpath table to be created. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).).

subpath_geom_column
Name of the geometry column in the subpath table. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).)

storage_parameters
Physical storage parameters used internally to create network tables. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure provides a convenient way to create a spatial network of LRS geometries when the node, link, and optional related tables do not already exist. The procedure creates the network; creates the node, link, path, and path-link tables for the network; and inserts the appropriate information in the xxx_SDO_NETWORK_METADATA views (described in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

An exception is generated if any of the tables to be created already exists.

The procedure has two formats. The simpler format creates the tables using default values for the table name and the geometry and cost column names. The other format lets you specify names for the tables and the geometry and cost columns.

As an alternative to using this procedure, you can create the network as follows: create the tables using the SDO_NET.CREATE_NODE_TABLE, SDO_NET.CREATE_LINK_TABLE, SDO_NET.CREATE_PATH_TABLE, and SDO_NET.CREATE_PATH_LINK_TABLE procedures; and insert the appropriate row in the USER_SDO_NETWORK_METADATA view.

#### Examples

The following example creates a directed spatial network named `LRS_NET1`. The LRS geometries are in the column named LRS_GEOM in the table named LRS_TAB. The example creates the LRS_NET1_NODE\$, LRS_NET1_LINK\$, LRS_NET1_PATH\$, and LRS_NET1_PLINK\$ tables, and updates the xxx_SDO_NETWORK_METADATA views. All geometry columns are named GEOMETRY. Both the node and link tables contain a cost column named COST.

    EXECUTE SDO_NET.CREATE_LRS_NETWORK('LRS_NET1', 'LRS_TAB', 'LRS_GEOM', 1, TRUE, TRUE);

**Parent topic:** SDO_NET Package Subprograms

### 6.12 SDO_NET.CREATE_LRS_TABLE

#### Format

    SDO_NET.CREATE_LRS_TABLE(
         table_name         IN VARCHAR2,
         geom_column        IN VARCHAR2,
         storage_parameters IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a table for storing Oracle Spatial and Graph linear referencing system (LRS) geometries.

#### Parameters

table_name
Name of the table containing the geometry column specified in `geom_column`.

geom_column
Name of the column (of type SDO_GEOMETRY) to contain geometry objects.

storage_parameters
Physical storage parameters used internally to create the LRS table. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure creates a table named `table_name` with two columns: GEOM_ID of type NUMBER and `geom_column` of type SDO_GEOMETRY.

Although the created table does not need to be used to store LRS geometries, the procedure is intended as a convenient method for creating a table to store such geometries. You will probably want to modify the table to add other columns before you store data in the table.

#### Examples

The following example creates a table named HIGHWAYS with a geometry column named GEOM.

    EXECUTE SDO_NET.CREATE_LRS_TABLE('HIGHWAYS', 'GEOM');

    PL/SQL procedure successfully completed.

    DESCRIBE highways
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     GEOM_ID                                   NOT NULL NUMBER
     GEOM                                               MDSYS.SDO_GEOMETRY

**Parent topic:** SDO_NET Package Subprograms

### 6.13 SDO_NET.CREATE_NODE_TABLE

#### Format

    SDO_NET.CREATE_NODE_TABLE(
         table_name             IN VARCHAR2,
         geom_type              IN VARCHAR2,
         geom_column            IN VARCHAR2,
         cost_column            IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

    or

    SDO_NET.CREATE_NODE_TABLE(
         table_name             IN VARCHAR2,
         geom_type              IN VARCHAR2,
         geom_column            IN VARCHAR2,
         cost_column            IN VARCHAR2,
         partition_column       IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a node table.

#### Parameters

table_name
Name of the node table.

geom_type
For a spatial network, specify a value indicating the geometry type of nodes: `SDO_GEOMETRY` for non-LRS SDO_GEOMETRY objects, `LRS_GEOMETRY` for LRS SDO_GEOMETRY objects, or `TOPO_GEOMETRY` for SDO_TOPO_GEOMETRY objects. (If the `geom_type` value is not spelled correctly, the `geom_column` column is not included in the table.)

geom_column
For a spatial network, the name of the column containing the geometry objects associated with the nodes.

cost_column
Name of the column containing the cost values to be associated with the nodes.

partition_column
Name of the column containing the partition ID values to be associated with the nodes.

no_of_hierarchy_levels
Number of hierarchy levels for nodes in the network. (For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).)

is_complex
Reserved for future use. Ignored for the current release.

storage_parameters
Physical storage parameters used internally to create the \<network-name\>\_NODE\$ table (described in [Node Table](network-data-model-graph-overview.md)). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure has two formats, one without the `partition_column` parameter and one with the `partition_column` parameter.

The node table is described in [Node Table](network-data-model-graph-overview.md).

#### Examples

The following example creates a node table named ROADS_NODES with a geometry column named NODE_GEOMETRY that will contain LRS geometries, no cost column, and a single hierarchy level.

    EXECUTE SDO_NET.CREATE_NODE_TABLE('ROADS_NODES', 'LRS_GEOMETRY', 'NODE_GEOMETRY', NULL, 1);

**Parent topic:** SDO_NET Package Subprograms

### 6.14 SDO_NET.CREATE_PARTITION_TABLE

#### Format

    SDO_NET.CREATE_PARTITION_TABLE(
         table_name IN VARCHAR2);

#### Description

Creates a partition table.

#### Parameters

table_name
Name of the partition table.

#### Usage Notes

The partition table is described in [Partition Table](network-data-model-graph-overview.md).

For information about using partitioned networks to perform analysis using the load on demand approach, see [Network Analysis Using Load on Demand](network-data-model-graph-overview.md).

#### Examples

The following example creates a partition table named MY_PART_TAB.

    EXECUTE SDO_NET.CREATE_PARTITION_TABLE('MY_PART_TAB');

**Parent topic:** SDO_NET Package Subprograms

### 6.15 SDO_NET.CREATE_PATH_LINK_TABLE

#### Format

    SDO_NET.CREATE_PATH_LINK_TABLE(
         table_name         IN VARCHAR2,
         storage_parameters IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a path-link table, that is, a table with a row for each link in each path in the path table.

#### Parameters

table_name
Name of the path-link table.

storage_parameters
Physical storage parameters used internally to create the path-link table. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

The path-link table is described in [Path-Link Table](network-data-model-graph-overview.md).

To use paths with a network, you must populate the path-link table.

#### Examples

The following example creates a path-link table named ROADS_PATHS_LINKS.

    EXECUTE SDO_NET.CREATE_PATH_LINK_TABLE('ROADS_PATHS_LINKS');

**Parent topic:** SDO_NET Package Subprograms

### 6.16 SDO_NET.CREATE_PATH_TABLE

#### Format

    SDO_NET.CREATE_PATH_TABLE(
         table_name         IN VARCHAR2,
         geom_column        IN VARCHAR2,
         storage_parameters IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a path table.

#### Parameters

table_name
Name of the path table.

geom_column
For a spatial network, name of the column containing the geometry objects associated with the paths.

storage_parameters
Physical storage parameters used internally to create the path table. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

The path table is described in [Path Table](network-data-model-graph-overview.md).

To use paths with a network, after you create the path table, you must create the path-link table using the SDO_NET.CREATE_PATH_LINK_TABLE procedure, and populate the path-link table.

#### Examples

The following example creates a path table named ROADS_PATHS that contains a geometry column named PATH_GEOMETRY.

    EXECUTE SDO_NET.CREATE_PATH_TABLE('ROADS_PATHS', 'PATH_GEOMETRY');

**Parent topic:** SDO_NET Package Subprograms

### 6.17 SDO_NET.CREATE_SDO_NETWORK

#### Format

    SDO_NET.CREATE_SDO_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_with_cost         IN BOOLEAN DEFAULT FALSE,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

    or

    SDO_NET.CREATE_SDO_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_table_name        IN VARCHAR2,
         node_geom_column       IN VARCHAR2,
         node_cost_column       IN VARCHAR2,
         link_table_name        IN VARCHAR2,
         link_geom_column       IN VARCHAR2,
         link_cost_column       IN VARCHAR2,
         path_table_name        IN VARCHAR2,
         path_geom_column       IN VARCHAR2,
         path_link_table_name   IN VARCHAR2,
         subpath_table_name     IN VARCHAR2,
         subpath_geom_column    IN VARCHAR2,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a spatial network containing non-LRS SDO_GEOMETRY objects, creates all necessary tables, and updates the network metadata.

#### Parameters

network
Network name.

no_of_hierarchy_levels
Number of hierarchy levels for links in the network. (For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).)

is_directed
A Boolean value. `TRUE` indicates that the links are directed; `FALSE` indicates that the links are undirected (not directed).

node_with_cost
A Boolean value. `TRUE` causes a column named COST to be included in the \<network-name\>\_NODE\$ table; `FALSE` (the default) causes a column named COST not to be included in the \<network-name\>\_NODE\$ table.

node_table_name
Name of the node table to be created. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a node table named \<network-name\>\_NODE\$ is created.

node_geom_column
Name of the geometry column in the node table. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named GEOMETRY.

node_cost_column
Name of the cost column in the node table. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

link_table_name
Name of the link table to be created. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a link table named \<network-name\>\_LINK\$ is created.

link_geom_column
Name of the geometry column in the link table. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named GEOMETRY.

link_cost_column
Name of the cost column in the link table. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

path_table_name
Name of the path table to be created. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path table named \<network-name\>\_PATH\$ is created.

path_geom_column
Name of the geometry column in the path table. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named GEOMETRY.

path_link_table_name
Name of the path-link table to be created. (The path-link table is explained in [Path-Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path-link table named \<network-name\>\_PLINK\$ is created.

subpath_table_name
Name of the subpath table to be created. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).)

subpath_geom_column
Name of the geometry column in the subpath table. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).).

is_complex
Reserved for future use. Ignored for the current release.

storage_parameters
Physical storage parameters used internally to create network tables. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure provides a convenient way to create a spatial network when the node, link, and optional related tables do not already exist. The procedure creates the network; creates the node, link, path, and path-link tables for the network; and inserts the appropriate information in the xxx_SDO_NETWORK_METADATA views (described in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

An exception is generated if any of the tables to be created already exists.

The procedure has two formats. The simpler format creates the tables using default values for the table name and the geometry and cost column names. The other format lets you specify names for the tables and the geometry and cost columns.

As an alternative to using this procedure, you can create the network as follows: create the tables using the SDO_NET.CREATE_NODE_TABLE, SDO_NET.CREATE_LINK_TABLE, SDO_NET.CREATE_PATH_TABLE, and SDO_NET.CREATE_PATH_LINK_TABLE procedures; and insert the appropriate row in the USER_SDO_NETWORK_METADATA view.

#### Examples

The following example creates a directed spatial network named `SDO_NET1`. The example creates the SDO_NET1_NODE\$, SDO_NET1_LINK\$, SDO_NET1_PATH\$, and SDO_NET1_PLINK\$ tables, and updates the xxx_SDO_NETWORK_METADATA views. All geometry columns are named GEOMETRY. Both the node and link tables contain a cost column named COST.

    EXECUTE SDO_NET.CREATE_SDO_NETWORK('SDO_NET1', 1, TRUE, TRUE);

**Parent topic:** SDO_NET Package Subprograms

### 6.18 SDO_NET.CREATE_SUBPATH_TABLE

#### Format

    SDO_NET.CREATE_SUBPATH_TABLE(
         table_name         IN VARCHAR2,
         geom_column        IN VARCHAR2,
         storage_parameters IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a subpath table.

#### Parameters

table_name
Name of the subpath table.

geom_column
For a spatial network, name of the column containing the geometry objects associated with the subpaths.

storage_parameters
Physical storage parameters used internally to create the subpath table (described in [Node Table](network-data-model-graph-overview.md)). Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

The subpath table is described in [Subpath Table](network-data-model-graph-overview.md).

To use subpaths with a network, you must create one or more path tables and their associated path-link tables.

#### Examples

The following example creates a subpath table named ROADS_SUBPATHS that contains a geometry column named SUBPATH_GEOMETRY.

    EXECUTE SDO_NET.CREATE_SUBPATH_TABLE('ROADS_SUBPATHS', 'SUBPATH_GEOMETRY');

**Parent topic:** SDO_NET Package Subprograms

### 6.19 SDO_NET.CREATE_TOPO_NETWORK

#### Format

    SDO_NET.CREATE_TOPO_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_with_cost         IN BOOLEAN DEFAULT FALSE,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

    or

    SDO_NET.CREATE_TOPO_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_table_name        IN VARCHAR2,
         node_cost_column       IN VARCHAR2,
         link_table_name        IN VARCHAR2,
         link_cost_column       IN VARCHAR2,
         path_table_name        IN VARCHAR2,
         path_geom_column       IN VARCHAR2,
         path_link_table_name   IN VARCHAR2,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

    or

    SDO_NET.CREATE_TOPO_NETWORK(
         network                IN VARCHAR2,
         no_of_hierarchy_levels IN NUMBER,
         is_directed            IN BOOLEAN,
         node_table_name        IN VARCHAR2,
         node_geom_column       IN VARCHAR2,
         node_cost_column       IN VARCHAR2,
         link_table_name        IN VARCHAR2,
         link_cost_column       IN VARCHAR2,
         path_table_name        IN VARCHAR2,
         path_geom_column       IN VARCHAR2,
         path_link_table_name   IN VARCHAR2,
         subpath_table_name     IN VARCHAR2,
         subpath_geom_column    IN VARCHAR2,
         is_complex             IN BOOLEAN DEFAULT FALSE,
         storage_parameters     IN VARCHAR2 DEFAULT NULL);

#### Description

Creates a spatial topology network containing SDO_TOPO_GEOMETRY objects, creates all necessary tables, and updates the network metadata.

#### Parameters

network
Network name.

no_of_hierarchy_levels
Number of hierarchy levels for links in the network. (For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).)

is_directed
A Boolean value. `TRUE` indicates that the links are directed; `FALSE` indicates that the links are undirected (not directed).

node_with_cost
A Boolean value. `TRUE` causes a column named COST to be included in the \<network-name\>\_NODE\$ table; `FALSE` (the default) causes a column named COST not to be included in the \<network-name\>\_NODE\$ table.

node_table_name
Name of the node table to be created. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a node table named \<network-name\>\_NODE\$ is created.

node_cost_column
Name of the cost column in the node table. (The node table is explained in [Node Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

link_table_name
Name of the link table to be created. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a link table named \<network-name\>\_LINK\$ is created.

link_cost_column
Name of the cost column in the link table. (The link table is explained in [Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named COST.

path_table_name
Name of the path table to be created. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path table named \<network-name\>\_PATH\$ is created.

path_geom_column
Name of the geometry column in the path table. (The path table is explained in [Path Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, the geometry column is named GEOMETRY.

path_link_table_name
Name of the path-link table to be created. (The path-link table is explained in [Path-Link Table](network-data-model-graph-overview.md).) If you use the format that does not specify this parameter, a path-link table named \<network-name\>\_PLINK\$ is created.

subpath_table_name
Name of the subpath table to be created. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).).

subpath_geom_column
Name of the geometry column in the subpath table. (The subpath table is explained in [Subpath Table](network-data-model-graph-overview.md).)

is_complex
Reserved for future use. Ignored for the current release.

storage_parameters
Physical storage parameters used internally to create network tables. Must be a valid string for use with the CREATE TABLE statement. For example: `TABLESPACE tbs_3 STORAGE (INITIAL 100K NEXT 200K)`. If you do not specify this parameter, the default physical storage values are used.

#### Usage Notes

This procedure provides a convenient way to create a spatial network when the node, link, and optional related tables do not already exist. The procedure creates the network; creates the node, link, path, and path-link tables for the network; and inserts the appropriate information in the xxx_SDO_NETWORK_METADATA views (described in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)). The node and link tables contain a topology geometry column named TOPO_GEOMETRY of type SDO_TOPO_GEOMETRY.

An exception is generated if any of the tables to be created already exists.

The procedure has two formats. The simpler format creates the tables using default values for the table name and the geometry and cost column names. The other format lets you specify names for the tables and the geometry and cost columns.

As an alternative to using this procedure, you can create the network as follows: create the tables using the SDO_NET.CREATE_NODE_TABLE, SDO_NET.CREATE_LINK_TABLE, SDO_NET.CREATE_PATH_TABLE, and SDO_NET.CREATE_PATH_LINK_TABLE procedures; and insert the appropriate row in the USER_SDO_NETWORK_METADATA view.

#### Examples

The following example creates a directed spatial topology geometry network named `TOPO_NET1`. The example creates the TOPO_NET1_NODE\$, TOPO_NET1_LINK\$, TOPO_NET1_PATH\$, and TOPO_NET1_PLINK\$ tables, and updates the xxx_SDO_NETWORK_METADATA views. The topology geometry columns are named TOPO_GEOMETRY. Both the node and link tables contain a cost column named COST.

    EXECUTE SDO_NET.CREATE_TOPO_NETWORK('TOPO_NET1', 1, TRUE, TRUE);

**Parent topic:** SDO_NET Package Subprograms

### 6.20 SDO_NET.DELETE_CHILD_FEATURES

#### Format

    SDO_NET.DELETE_CHILD_FEATURES(
         parent_layer_id   IN NUMBER,
         parent_feature_id IN NUMBER,
         child_feature_ids IN SDO_NET_LAYER_FEAT_ARRAY);

#### Description

Removes the parent-child relationship for the input child features.

#### Parameters

parent_layer_id
ID of the parent feature layer.

parent_feature_id
ID of the parent feature of the specified child features.

child_feature_ids
IDs of the child features. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

#### Usage Notes

The specified parent and child features must exist.

To delete the child features at specified sequence points, use the SDO_NET.DELETE_CHILD_FEATURES_AT procedure.

#### Examples

The following example deletes a child feature with feature ID 1 in the `POI` feature layer.

    DECLARE
      parent_layer_id NUMBER;
      parent_feature_id NUMBER := 1;
      child_layer_id NUMBER;
      child_feature_ids SDO_NET_LAYER_FEAT_ARRAY := SDO_NET_LAYER_FEAT_ARRAY();
    BEGIN
      parent_layer_id := sdo_net.get_feature_layer_id('GRID', 'PARENT_LAYER');
      child_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      child_feature_ids.extend;
      child_feature_ids(1) := SDO_NET_LAYER_FEAT(child_layer_id, 1);
      sdo_net.delete_child_features(parent_layer_id, parent_feature_id, child_feature_ids);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.21 SDO_NET.DELETE_CHILD_FEATURES_AT

#### Format

    SDO_NET.DELETE_CHILD_FEATURES_AT(
         parent_layer_id   IN NUMBER,
         parent_feature_id IN NUMBER,
         sequence_numbers  IN SDO_NUMBER_ARRAY);

#### Description

Removes the parent-child relationship for the child features at the specified sequence numbers.

#### Parameters

parent_layer_id
ID of the parent feature layer.

parent_feature_id
ID of the parent feature of the specified child features.

child_feature_ids
IDs of the child features. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

#### Usage Notes

The specified parent and child features must exist.

To delete child features specified by their ID values, use the SDO_NET.DELETE_CHILD_FEATURES procedure.

#### Examples

The following example deletes a child feature at sequence number 1.

    DECLARE
      parent_layer_id NUMBER;
      parent_feature_id NUMBER := 1;
      sequence_numbers SDO_NUMBER_ARRAY := SDO_NUMBER_ARRAY(1);
    BEGIN
      parent_layer_id := sdo_net.get_feature_layer_id('GRID', 'PARENT_LAYER');
      sdo_net.delete_child_features_at(parent_layer_id, parent_feature_id, sequence_numbers);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.22 SDO_NET.DELETE_DANGLING_FEATURES

#### Format

    SDO_NET.DELETE_DANGLING_FEATURES(
         feature_layer_id IN NUMBER);

#### Description

Deletes dangling features in a feature layer. A dangling feature is a feature that is not associated with any network elements (nodes or links).

#### Parameters

feature_layer_id
ID of the feature layer containing the features.

#### Usage Notes

To find the dangling features in a feature layer, use the SDO_NET.GET_DANGLING_FEATURES function.

#### Examples

The following example deletes any dangling features in the `POI` feature layer in the `GRID` network.

    DECLARE
      feature_layer_id NUMBER;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      sdo_net.delete_dangling_features(feature_layer_id);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.23 SDO_NET.DELETE_DANGLING_LINKS

#### Format

    SDO_NET.DELETE_DANGLING_LINKS(
         network IN VARCHAR2);

#### Description

Deletes links that are not referenced by any feature in any feature layer.

#### Parameters

network
Name of the network.

#### Usage Notes

To find the dangling links in a network, use the SDO_NET.GET_DANGLING_LINKS function.

#### Examples

The following example deletes any dangling links in the `GRID` network.

    EXECUTE sdo_net.delete_dangling_links('GRID');

**Parent topic:** SDO_NET Package Subprograms

### 6.24 SDO_NET.DELETE_DANGLING_NODES

#### Format

    SDO_NET.DELETE_DANGLING_NODES(
         network IN VARCHAR2);

#### Description

Deletes nodes that are not referenced by any feature in any feature layer.

#### Parameters

network
Name of the network.

#### Usage Notes

To find the dangling nodes in a network, use the SDO_NET.GET_DANGLING_NODES function.

#### Examples

The following example deletes any dangling nodes in the `GRID` network.

    EXECUTE sdo_net.delete_dangling_nodes('GRID');

**Parent topic:** SDO_NET Package Subprograms

### 6.25 SDO_NET.DELETE_FEATURE_ELEMENTS

#### Format

    SDO_NET.DELETE_FEATURE_ELEMENTS(
         feature_layer_id IN NUMBER,
         feature_id       IN NUMBER,
         feature_elements IN SDO_NET_FEAT_ELEM_ARRAY,
         delete_net_elems IN BOOLEAN DEFAULT FALSE);

#### Description

Deletes feature elements from a feature.

#### Parameters

feature_layer_id
ID of the feature layer containing the feature.

feature_id
ID of the feature from which to delete the feature elements.

feature_elements
Feature elements to be deleted. (The SDO_NET_FEAT_ELEM_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

delete_net_elems
Controls whether all network elements that are referenced only by the specified features are also deleted: `TRUE` also deletes such elements; `FALSE` (the default) does not also delete such elements.

#### Usage Notes

Contrast this procedure with SDO_NET.DELETE_FEATURE_ELEMENTS_AT.

#### Examples

The following example two point feature elements from a specified feature layer.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      elements SDO_NET_FEAT_ELEM_ARRAY := SDO_NET_FEAT_ELEM_ARRAY();
      link_id NUMBER := 1314;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      elements.extend;
      elements(1) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.2, null);
      elements.extend;
      elements(2) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.7, null);
      sdo_net.delete_feature_elements(feature_layer_id, feature_id, elements);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.26 SDO_NET.DELETE_FEATURE_ELEMENTS_AT

#### Format

    SDO_NET.DELETE_FEATURE_ELEMENTS_AT(
         feature_layer_id IN NUMBER,
         feature_id       IN NUMBER,
         sequence_numbers IN SDO_NUMBER_ARRAY,
         delete_net_elems IN BOOLEAN DEFAULT FALSE);

#### Description

Deletes the feature elements with specified sequence numbers from a feature.

#### Parameters

feature_layer_id
ID of the feature layer containing the feature.

feature_id
ID of the feature from which to delete the feature elements.

sequence_numbers
Array of sequence numbers for the feature elements to be deleted.

delete_net_elems
Controls whether all network elements that are referenced only by the specified features are also deleted: `TRUE` also deletes such elements; `FALSE` (the default) does not also delete such elements.

#### Usage Notes

Contrast this procedure with SDO_NET.DELETE_FEATURE_ELEMENTS

#### Examples

The following example deletes the feature element at sequence number 1.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      sequence_numbers SDO_NUMBER_ARRAY := SDO_NUMBER_ARRAY();
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      sequence_numbers.extend;
      sequence_numbers(1) := 1;
      sdo_net.delete_feature_elements_at(feature_layer_id, feature_id, sequence_numbers);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.27 SDO_NET.DELETE_FEATURES

#### Format

    SDO_NET.DELETE_FEATURES(
         feature_layer_id IN NUMBER,
         feature_ids      IN SDO_NUMBER_ARRAY,
         delete_net_elems IN BOOLEAN DEFAULT FALSE,
         delete_children  IN BOOLEAN DEFAULT FALSE);

#### Description

Deletes features.

#### Parameters

feature_layer_id
ID of the feature layer containing the features

feature_ids
IDs of the features to be deleted.

delete_net_elems
Controls whether all network elements that are referenced only by the specified features are also deleted: `TRUE` also deletes such elements; `FALSE` (the default) does not also delete such elements.

delete_children
Controls whether all child features that are referenced only by the specified features are also deleted: `TRUE` also deletes such features; `FALSE` (the default) does not also delete such features.

#### Usage Notes

(None.)

#### Examples

The following example deletes the feature with feature ID 1 from the `POI` feature layer in the `GRID` network.

    DECLARE
      feature_layer_id NUMBER;
      feature_ids SDO_NUMBER_ARRAY := SDO_NUMBER_ARRAY(1);
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      sdo_net.delete_features(feature_layer_id, feature_ids, false, false);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.28 SDO_NET.DELETE_LINK

#### Format

    SDO_NET.DELETE_LINK(
         network IN VARCHAR2,
         link_id IN NUMBER);

#### Description

Deletes a link, along with all dependent network elements and all references to the link from features.

#### Parameters

network
Network name.

link_id
ID of the link to delete.

#### Usage Notes

This procedure deletes the specified link from the link table (described in [Link Table](network-data-model-graph-overview.md)), and it deletes any other network elements that depend on this link. For example, if the specified link is included in any paths and subpaths, those paths and subpaths are deleted also.

#### Examples

The following example deletes the link in the SDO_NET2 network whose link ID is 1.

    SELECT SDO_NET.DELETE_LINK('SDO_NET2', 1);

**Parent topic:** SDO_NET Package Subprograms

### 6.29 SDO_NET.DELETE_NODE

#### Format

    SDO_NET.DELETE_NODE(
         network IN VARCHAR2,
         node_id IN NUMBER);

#### Description

Deletes a node, along with all dependent network elements and all references to the node from features.

#### Parameters

network
Network name.

node_id
ID of the node to delete.

#### Usage Notes

This procedure deletes the specified node from the node table (described in [Node Table](network-data-model-graph-overview.md)), and it deletes any other network elements that depend on this node. For example, if the specified node is included in any link definitions, those links are deleted; and if any of the deleted links are included in any paths and subpaths, those paths and subpaths are deleted also.

#### Examples

The following example deletes the node in the SDO_NET2 network whose node ID is 1.

    SELECT SDO_NET.DELETE_NODE('SDO_NET2', 1);

**Parent topic:** SDO_NET Package Subprograms

### 6.30 SDO_NET.DELETE_PATH

#### Format

    SDO_NET.DELETE_PATH(
         network IN VARCHAR2,
         path_id IN NUMBER);

#### Description

Deletes a path and all dependent network elements.

#### Parameters

network
Network name.

path_id
ID of the path to delete.

#### Usage Notes

This procedure deletes the specified path from the path table (described in [Path Table](network-data-model-graph-overview.md)), and it deletes any other network elements that depend on this path. For example, if the specified path has any subpaths, those subpaths are deleted also.

#### Examples

The following example deletes the path in the SDO_NET2 network whose path ID is 1.

    SELECT SDO_NET.DELETE_PATH('SDO_NET2', 1);

**Parent topic:** SDO_NET Package Subprograms

### 6.31 SDO_NET.DELETE_PHANTOM_FEATURES

#### Format

    SDO_NET.DELETE_PHANTOM_FEATURES(
         feature_layer_id IN NUMBER);

#### Description

Deletes phantom features in a feature layer. A phantom feature is a feature that references nonexistent network elements (nodes or links).

#### Parameters

feature_layer_id
ID of the feature layer containing the features.

#### Usage Notes

To find the phantom features in a feature layer, use the SDO_NET.GET_PHANTOM_FEATURES function.

#### Examples

The following example deletes any phantom features in the `POI` feature layer in the `GRID` network.

    DECLARE
      feature_layer_id NUMBER;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      sdo_net.delete_phantom_features(feature_layer_id);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.32 SDO_NET.DELETE_SUBPATH

#### Format

    SDO_NET.DELETE_SUBPATH(
         network    IN VARCHAR2,
         subpath_id IN NUMBER);

#### Description

Deletes a subpath.

#### Parameters

network
Network name.

subpath_id
ID of the subpath to delete.

#### Usage Notes

This procedure deletes the specified subpath from the path table (described in [Path Table](network-data-model-graph-overview.md)). It does not delete any other network elements, because no other elements depend on a subpath definition.

#### Examples

The following example deletes the subpath in the SDO_NET2 network whose subpath ID is 17.

    SELECT SDO_NET.DELETE_SUBPATH('SDO_NET2', 17);

**Parent topic:** SDO_NET Package Subprograms

### 6.33 SDO_NET.DEREGISTER_CONSTRAINT

#### Format

    SDO_NET.DEREGISTER_CONSTRAINT(
         constraint_name IN VARCHAR2);

#### Description

Unloads (removes) the class for the specified network constraint from the Java repository in the database, and deletes the row for that constraint from the USER_SDO_NETWORK_CONSTRAINTS view (described in [xxx_SDO_NETWORK_CONSTRAINTS Views](network-data-model-graph-overview.md)).

#### Parameters

constraint_name
Name of the network constraint. Must match a value in the CONSTRAINT column of the USER_SDO_NETWORK_CONSTRAINTS view.

#### Usage Notes

Use this procedure if you want to disable a network constraint that you had previously enabled, such as by using the SDO_NET.REGISTER_CONSTRAINTprocedure. For more information about network constraints, see [Network Constraints](network-data-model-graph-overview.md).

#### Examples

The following example deregisters (disables) a network constraint named `GivenProhibitedTurn`.

    EXECUTE SDO_NET.DEREGISTER_CONSTRAINT('GivenProhibitedTurn');

**Parent topic:** SDO_NET Package Subprograms

### 6.34 SDO_NET.DROP_FEATURE_LAYER

#### Format

    SDO_NET.DROP_FEATURE_LAYER(
         network_name       IN VARCHAR2,
         feature_layer_name IN VARCHAR2,
         drop_tables        IN BOOLEAN DEFAULT FALSE);

#### Description

Drops (deletes) a feature layer.

#### Parameters

network_name
Name of the network containing the feature layer to be dropped.

feature_layer_name
Name of the feature layer to be dropped.

drop_tables
Controls whether all relevant tables are deleted along with the feature layer metadata: `TRUE` drops the feature table, feature element relationships table, and feature hierarchy table, and deletes the feature layer metadata; `FALSE` (the default) deletes the feature layer metadata but does not drop the feature table, feature element relationships table, and feature hierarchy table.

#### Usage Notes

(None.)

#### Examples

The following example drops the `POI` feature layer in the `GRID` network, and (because `drop_tables` is `true`) drops the feature table, feature element relationships table, and feature hierarchy table, and deletes the feature layer metadata

    EXECUTE sdo_net.drop_feature_layer('GRID', 'POI', true);

**Parent topic:** SDO_NET Package Subprograms

### 6.35 SDO_NET.DROP_NETWORK

#### Format

    SDO_NET.DROP_NETWORK(
         network IN VARCHAR2);

#### Description

Drops (deletes) a network.

#### Parameters

network
Name of the network to be dropped.

#### Usage Notes

This procedure also deletes the node, link, and path tables associated with the network, and the network metadata for the network.

#### Examples

The following example drops the network named `ROADS_NETWORK`.

    EXECUTE SDO_NET.DROP_NETWORK('ROADS_NETWORK');

**Parent topic:** SDO_NET Package Subprograms

### 6.36 SDO_NET.FIND_CONNECTED_COMPONENTS

#### Format

    SDO_NET.FIND_CONNECTED_COMPONENTS(
         network IN VARCHAR2);

#### Description

Finds all connected components for a specified link level in a network, and stores the information in the connected component table.

#### Parameters

network
Network name.

link_level
Link level for which to find connected components (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in computing a path.

component_table_name
Name of the connected component table, which is created by this procedure. (If an existing table with the specified name already exists, it is updated with information for the specified link level.) The connected component table is described in [Connected Component Table](network-data-model-graph-overview.md).

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about spatial network operations, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

#### Usage Notes

This procedure finds, for each node in the specified network, information about all other nodes that are reachable from that node, and it stores the information in the specified connected component table. Having this information in the table enables better performance for many network analysis operations.

#### Examples

The following example finds the connected components for link level 1 in the SDO_PARTITIONED network, and creates or updates the SDO_PARTITIONED_CONN_COMP_TAB table. Information about the operation is added (`open_mode => 'a'`) to the `sdo_partitioned.log` file, located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.FIND_CONNECTED_COMPONENTS(-
      network => 'SDO_PARTITIONED', -
      link_level => 1,-
      component_table_name => 'sdo_partitioned_conn_comp_tab',-
      log_loc => 'LOG_DIR', log_file=> 'sdo_partitioned.log',-
      open_mode => 'a');

**Parent topic:** SDO_NET Package Subprograms

### 6.37 SDO_NET.GENERATE_NODE_LEVELS

#### Format

    SDO_NET.GENERATE_NODE_LEVELS(
         network               IN VARCHAR2,
         node_level_table_name IN VARCHAR2,
         overwrite             IN BOOLEAN DEFAULT FALSE,
         log_loc               IN VARCHAR2,
         log_file              IN VARCHAR2,
         open_mode             IN VARCHAR2 DEFAULT 'A');

#### Description

Generates node levels for a specified multilevel network, and stores the information in a table.

#### Parameters

network
Network name.

node_level_table_name
Table in which to store node level information. This table must have the following definition: `(node_id NUMBER PRIMARY KEY, link_level NUMBER)`

overwrite
Controls the behavior if the table specified in `node_level_table_name` already exists: `TRUE` replaces the contents of that table with new data; `FALSE` (the default) generates an error. (This parameter has no effect if the table specified in `node_level_table_name` does not exist.)

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about spatial network operations, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

#### Usage Notes

If `network` is not a multilevel network (one with multiple link levels), this procedure does not perform any operation.

This procedure is used internally by the SDO_NET.GENERATE_PARTITION_BLOBS procedure. Therefore, if you have executed SDO_NET.GENERATE_PARTITION_BLOBS, you do not need to execute this procedure. However, you do need to execute this procedure explicitly in these cases:

- When a Java application has been configured to read partitions from the node or link tables instead of from BLOBs, and partition BLOBs have never been generated on the network.

- When a higher-level node has been added or deleted in the network and the node-partition relationship has been updated. Before you execute SDO_NET.GENERATE_PARTITION_BLOB to regenerate the containing partition BLOB or BLOBs, you must manually either update the node level table or execute this procedure (SDO_NET.GENERATE_NODE_LEVELS).

The node level table name is stored in the NODE_LEVEL_TABLE_NAME column of the USER_SDO_NETWORK_METADATA view, which is described in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md).

#### Examples

The following example generates the node level information for the MY_MULTILEVEL_NET network, and stores the information in the MY_NET_NODE_LEVELS table. Information about the operation is added (`open_mode => 'a'`) to the `my_multilevel_net.log` file, located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.GENERATE_NODE_LEVELS(-
      network => 'MY_MULTILEVEL_NET', -
      node_level_table_name => 'MY_NET_NODE_LEVELS',-
      overwrite => FALSE,-
      log_loc => 'LOG_DIR', log_file=> 'my_multilevel_net.log',-
      open_mode => 'a');

**Parent topic:** SDO_NET Package Subprograms

### 6.38 SDO_NET.GENERATE_PARTITION_BLOB

#### Format

    SDO_NET.GENERATE_PARTITION_BLOB(
         network              IN VARCHAR2,
         link_level           IN NUMBER DEFAULT 1,
         partition_id         IN VARCHAR2,
         include_user_data    IN BOOLEAN,
         log_loc              IN VARCHAR2,
         log_file             IN VARCHAR2,
         open_mode            IN VARCHAR2 DEFAULT 'A',
         preform_delta_update IN BOOLEAN DEFAULT FALSE);

#### Description

Generates a single binary large object (BLOB) representation for a specified partition associated with a specified link level in the network, and stores the information in the existing partition BLOB table.

#### Parameters

network
Network name.

link_level
Link level for links to be included in the BLOB (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in computing a path.

partition_id
Partition ID number. Network elements associated with the specified combination of link level and partition ID are included in the generated BLOB.

include_user_data
`TRUE` if the BLOB should include any user data of category 0 (zero) associated with the network elements represented in each BLOB, or `FALSE` if the BLOB should not include any user data.

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about spatial network operations, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

perform_delta_update
(Reserved for future use. The only permitted value is `FALSE`, the default.)

#### Usage Notes

This procedure adds a single new BLOB or replaces a single existing BLOB in the partition BLOB table, which must have been previously created using the SDO_NET.GENERATE_PARTITION_BLOBS procedure.

One use for this procedure is to perform a relatively quick update of the BLOB for a desired partition in a network that contains multiple large partitions, as opposed to than updating the BLOBs for all partitions using the SDO_NET.GENERATE_PARTITION_BLOBS procedure.

#### Examples

The following example generates the partition BLOB for the partition associated with partition ID 1 and link level 1 in the SDO_PARTITIONED network, and adds or replaces the appropriate BLOB in the SDO_PARTITIONED_PART_BLOB_TAB table. Any user data of category 0 (zero) associated with the network elements is also included. Information about the operation is added (`open_mode => 'a'`) to the `sdo_partitioned.log` file, located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.GENERATE_PARTITION_BLOB(-
      network => 'SDO_PARTITIONED', -
      link_level => 1,-
      partition_id => 1,-
      include_user_data => true,-
      log_loc => 'LOG_DIR', log_file=> 'sdo_partitioned.log',-
      open_mode => 'a');

**Parent topic:** SDO_NET Package Subprograms

### 6.39 SDO_NET.GENERATE_PARTITION_BLOBS

#### Format

    SDO_NET.GENERATE_PARTITION_BLOBS(
         network                   IN VARCHAR2,
         link_level                IN NUMBER DEFAULT 1,
         partition_blob_table_name IN VARCHAR2,
         include_user_data         IN BOOLEAN,
         commit_for_each_blob      IN BOOLEAN DEFAULT TRUE,
         log_loc                   IN VARCHAR2,
         log_file                  IN VARCHAR2,
         open_mode                 IN VARCHAR2 DEFAULT 'A',
         perform_delta_update      IN BOOLEAN DEFAULT FALSE,
         regenerate_node_levels    IN BOOLEAN DEFAULT FALSE);

#### Description

Generates a binary large object (BLOB) representation for partitions associated with a specified link level in the network, and stores the information in the partition BLOB table.

#### Parameters

network
Network name.

link_level
Link level for links to be included in each BLOB (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in computing a path.

partition_blob_table_name
Name of the partition BLOB table, which is created by this procedure. (If an existing table with the specified name already exists, it is updated with information for the specified link level.) The partition BLOB table is described in [Partition BLOB Table](network-data-model-graph-overview.md).

include_user_data
`TRUE` if each BLOB should include any user data of category 0 (zero) associated with the network elements represented in each BLOB, or `FALSE` if each BLOB should not include any user data.

commit_for_each_blob
`TRUE` (the default) if each partition BLOB should be committed to the database after it is generated, or `FALSE` if each BLOB should not be committed (in which case you must perform one or more explicit commit operations).

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about spatial network operations, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

perform_delta_update
(Reserved for future use. The only permitted value is `FALSE`, the default.)

regenerate_node_levels
`TRUE` to regenerate the node level table for multilevel networks, or `FALSE` (the default) not to regenerate the node level table for multilevel networks. You should set this parameter to `TRUE` if higher-level (second level or above) nodes are added or deleted from the network, or if the level of a node is changed. The level of a node is defined as the maximum link level coming into or out of the node.

#### Usage Notes

Generating partition BLOBs enables better performance for many network analysis operations, especially with large networks.

If the network is not partitioned, this procedure generates a single BLOB representing the entire network.

When this procedure is first executed on a multilevel network, it internally calls SDO_NET.GENERATE_NODE_LEVELS to create and populate the node level table (described in [Node Level Table (Optional)](network-data-model-graph-overview.md)). When this procedure is called subsequently on a multilevel network, you can use the `regenerate_node_levels` parameter to specify whether to overwrite the existing node level table.

Do not confuse this procedure with SDO_NET.GENERATE_PARTITION_BLOB, which regenerates a single BLOB for a specified combination of link level and partition ID, and adds that information to the existing partition BLOB table.

#### Examples

The following example generates partition BLOBs for link level 1 in the SDO_PARTITIONED network, and creates or updates the SDO_PARTITIONED_PART_BLOB_TAB table. Any user data of category 0 (zero) associated with the network elements is also included. Information about the operation is added (`open_mode => 'a'`) to the `sdo_partitioned.log` file, located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.GENERATE_PARTITION_BLOBS(-
      network => 'SDO_PARTITIONED', -
      link_level => 1,-
      partition_blob_table_name => 'sdo_partitioned_part_blob_tab',-
      include_user_data => true,-
      log_loc => 'LOG_DIR', log_file=> 'sdo_partitioned.log',-
      open_mode => 'a');

**Parent topic:** SDO_NET Package Subprograms

### 6.40 SDO_NET.GET_CHILD_FEATURE_IDS

#### Format

    SDO_NET.GET_CHILD_FEATURE_IDS(
         feature_layer_id IN NUMBER,
         feature_id       IN NUMBER
    ) RETURN SDO_NET_LAYER_FEAT_ARRAY;

#### Description

Returns the feature layer ID and child feature IDs for the specified feature. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

#### Parameters

feature_layer_id
ID of the feature layer for the feature (that is, the parent feature).

feature_id
ID of the feature.

#### Usage Notes

To get the feature layer ID and feature ID of the parent features for a specified feature, use the SDO_NET.GET_PARENT_FEATURE_IDS function.

For information about features, including parent and child features, see [Features and Feature Layers](network-data-model-graph-overview.md).

#### Examples

The following example returns and displays the child feature IDs for feature 1 in the `PARENT_LAYER` feature layer.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      feature_ids SDO_NET_LAYER_FEAT_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'PARENT_LAYER');
      feature_ids := sdo_net.get_child_feature_ids(feature_layer_id, feature_id);
      FOR i in 1..feature_ids.count
      LOOP
        --dbms_output.put_line('['||i||']'||' FEATURE_LAYER_ID   = '||feature_ids(i).feature_layer_id);
        dbms_output.put_line('['||i||']'||' FEATURE_ID         = '||feature_ids(i).feature_id);
        dbms_output.put_line('---');
      END LOOP;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.41 SDO_NET.GET_CHILD_LINKS

#### Format

    SDO_NET.GET_CHILD_LINKS(
         network IN VARCHAR2,
         link_id IN NUMBER
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the child links of a link.

#### Parameters

network
Network name.

link_id
ID of the link for which to return the child links.

#### Usage Notes

For information about parent and child nodes and links in a network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).

#### Examples

The following example returns the child links of the link in the `XYZ_NETWORK` network whose link ID is 1001.

    SELECT SDO_NET.GET_CHILD_LINKS('XYZ_NETWORK', 1001) FROM DUAL;

    SDO_NET.GET_CHILD_LINKS('XYZ_NETWORK',1001)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(1108, 1109)

**Parent topic:** SDO_NET Package Subprograms

### 6.42 SDO_NET.GET_CHILD_NODES

#### Format

    SDO_NET.GET_CHILD_NODES(
         network IN VARCHAR2,
         node_id IN NUMBER
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the child nodes of a node.

#### Parameters

network
Network name.

node_id
ID of the node for which to return the child nodes.

#### Usage Notes

For information about parent and child nodes and links in a network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).

#### Examples

The following example returns the child nodes of the node in the `XYZ_NETWORK` network whose node ID is 1.

    SELECT SDO_NET.GET_CHILD_NODES('XYZ_NETWORK', 1) FROM DUAL;

    SDO_NET.GET_CHILD_NODES('XYZ_NETWORK',1)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(101, 102, 103, 104, 105, 106)

**Parent topic:** SDO_NET Package Subprograms

### 6.43 SDO_NET.GET_DANGLING_FEATURES

#### Format

    SDO_NET.GET_DANGLING_FEATURES(
         feature_layer_id IN NUMBER
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the IDs of dangling features in a feature layer. A dangling feature is a feature that is not associated with any network elements (nodes or links).

#### Parameters

feature_layer_id
ID of the feature layer containing the features.

#### Usage Notes

To delete the dangling features in a feature layer, use the SDO_NET.DELETE_DANGLING_FEATURES procedure.

#### Examples

The following example gets the dangling features in the `POI` feature layer of the `GRID` network and then displays their feature IDs.

    DECLARE
      feature_layer_id NUMBER;
      feature_ids SDO_NUMBER_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      feature_ids := sdo_net.get_dangling_features(feature_layer_id);
      dbms_output.put_line('Dangling Features:');
      for i in 1..feature_ids.count loop
        dbms_output.put_line('['||i||'] '||feature_ids(i));
      end loop;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.44 SDO_NET.GET_DANGLING_LINKS

#### Format

    SDO_NET.GET_DANGLING_LINKS(
         network IN VARCHAR2
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns links that are not referenced by any feature in any feature layer.

#### Parameters

network
Name of the network.

#### Usage Notes

To delete the dangling links in a network, use the SDO_NET.DELETE_DANGLING_LINKS procedure.

#### Examples

The following example gets the dangling links in the `GRID` network and then displays the number (count) of dangling links found.

    DECLARE
      link_ids SDO_NUMBER_ARRAY;
    BEGIN
      link_ids := sdo_net.get_dangling_links('GRID');
      dbms_output.put_line('Number of dangling Links: '||link_ids.count);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.45 SDO_NET.GET_DANGLING_NODES

#### Format

    SDO_NET.GET_DANGLING_NODES(
         network IN VARCHAR2
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns nodes that are not referenced by any feature in any feature layer.

#### Parameters

network
Name of the network.

#### Usage Notes

To delete the dangling nodes in a network, use the SDO_NET.DELETE_DANGLING_NODES procedure.

#### Examples

The following example gets the dangling nodes in the `GRID` network and then displays the number (count) of dangling nodes found.

    DECLARE
      node_ids SDO_NUMBER_ARRAY;
    BEGIN
      node_ids := sdo_net.get_dangling_nodes('GRID');
      dbms_output.put_line('Number of dangling Nodes: '||node_ids.count);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.46 SDO_NET.GET_FEATURE_ELEMENTS

#### Format

    SDO_NET.GET_FEATURE_ELEMENTS(
         feature_layer_id IN NUMBER,
         feature_id       IN NUMBER
    ) RETURN SDO_NET_FEAT_ELEM_ARRAY;

#### Description

Returns the feature elements in a feature layer. (The SDO_NET_FEAT_ELEM_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

#### Parameters

feature_layer_id
ID of the feature layer for the feature.

feature_id
ID of the feature.

#### Usage Notes

To add a feature element to a feature, use the SDO_NET.ADD_FEATURE_ELEMENT procedure; to add multiple feature elements in a single operation, use the SDO_NET.ADD_FEATURE_ELEMENTS procedure.

#### Examples

The following example gets the feature layer ID for a specified feature layer, then gets and displays information about the feature elements for feature 1 in this feature layer.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      elements SDO_NET_FEAT_ELEM_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      elements := sdo_net.get_feature_elements(feature_layer_id, feature_id);
      FOR i in 1..elements.count
      LOOP
        dbms_output.put_line('['||i||']'||' FEAT_ELEM_TYPE   = '||elements(i).feat_elem_type);
        dbms_output.put_line('['||i||']'||' NET_ELEM_ID      = '||elements(i).net_elem_id);
        dbms_output.put_line('['||i||']'||' START_PERCENTAGE = '||elements(i).start_percentage);
        dbms_output.put_line('['||i||']'||' END_PERCENTAGE   = '||elements(i).end_percentage);
        dbms_output.put_line('---');
      END LOOP;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.47 SDO_NET.GET_FEATURE_LAYER_ID

#### Format

    SDO_NET.GET_FEATURE_LAYER_ID(
         network_name       IN VARCHAR2
         feature_layer_name IN VARCHAR2
    ) RETURN NUMBER;

#### Description

Returns the feature layer ID for a specified feature layer.

#### Parameters

network_name
Network name.

feature_layer_name
Feature layer name.

#### Usage Notes

This function returns the value of the FEATURE_LAYER_ID column for the network and feature layer combination in the USER_SDO_NETWORK_FEATURE view (see [Table 5-36](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_FEATURE Views](network-data-model-graph-overview.md)).

#### Examples

The following example gets and displays the feature layer ID for a specified feature layer.

    DECLARE
      feature_layer_id NUMBER;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      dbms_output.put_line('Feature layer ID for the POI feature layer is '||feature_layer_id);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.48 SDO_NET.GET_FEATURES_ON_LINKS

#### Format

    SDO_NET.GET_FEATURES_ON_LINKS
         feature_layer_id IN NUMBER,
         link_ids         IN SDO_NUMBER_ARRAY
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the IDs of features in a feature layer that reference specified links.

#### Parameters

feature_layer_id
ID of the feature layer containing the features.

link_ids
IDs of the links to check for features.

#### Usage Notes

To find the IDs of features in a feature layer that reference specified nodes, use the SDO_NET.GET_FEATURES_ON_NODES procedure.

#### Examples

The following example gets and displays the feature IDs of features on a specified link.

    DECLARE
      feature_layer_id NUMBER;
      link_ids SDO_NUMBER_ARRAY := SDO_NUMBER_ARRAY(1314);
      feature_ids SDO_NUMBER_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      feature_ids := sdo_net.get_features_on_links(feature_layer_id, link_ids);
      dbms_output.put_line('Features On Link '||link_ids(1)||':');
      for i in 1..feature_ids.count loop
        dbms_output.put_line('['||i||'] '||feature_ids(i));
      end loop;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.49 SDO_NET.GET_FEATURES_ON_NODES

#### Format

    SDO_NET.GET_FEATURES_ON_NODES
         feature_layer_id IN NUMBER,
         node_ids         IN SDO_NUMBER_ARRAY
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the IDs of features in a feature layer that reference specified nodes.

#### Parameters

feature_layer_id
ID of the feature layer containing the features.

node_ids
IDs of the nodes to check for features.

#### Usage Notes

To find the IDs of features in a feature layer that reference specified links, use the SDO_NET.GET_FEATURES_ON_LINKS procedure.

#### Examples

The following example gets and displays the feature IDs of features on a specified node.

    DECLARE
      feature_layer_id NUMBER;
      node_ids SDO_NUMBER_ARRAY := SDO_NUMBER_ARRAY(13);
      feature_ids SDO_NUMBER_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      feature_ids := sdo_net.get_features_on_nodes(feature_layer_id, node_ids);
      dbms_output.put_line('Features On Node '||node_ids(1)||':');
      for i in 1..feature_ids.count loop
        dbms_output.put_line('['||i||'] '||feature_ids(i));
      end loop;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.50 SDO_NET.GET_GEOMETRY_TYPE

#### Format

    SDO_NET.GET_GEOMETRY_TYPE(
         network IN VARCHAR2
    ) RETURN VARCHAR2;

#### Description

Returns the geometry type for a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the GEOMETRY_TYPE column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the geometry type for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_GEOMETRY_TYPE('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_GEOMETRY_TYPE('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    LRS_GEOMETRY

**Parent topic:** SDO_NET Package Subprograms

### 6.51 SDO_NET.GET_IN_LINKS

#### Format

    SDO_NET.GET_IN_LINKS(
         network IN VARCHAR2,
         node_id IN NUMBER
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns an array of link ID numbers of the inbound links to a node.

#### Parameters

network
Network name.

node_id
ID of the node for which to return the array of inbound links.

#### Usage Notes

For information about inbound links and related Network Data Model Graph concepts, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns an array of link ID numbers of the inbound links into the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_IN_LINKS('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_IN_LINKS('ROADS_NETWORK',3)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(102)

**Parent topic:** SDO_NET Package Subprograms

### 6.52 SDO_NET.GET_INVALID_LINKS

#### Format

    SDO_NET.GET_INVALID_LINKS(
         network IN VARCHAR2
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the invalid links in a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns an SDO_NUMBER_ARRAY object with a comma-delimited list of node ID numbers of invalid links in the specified network. If there are no invalid links, this function returns a null value.

#### Examples

The following example returns the invalid links in the SDO_PARTITIONED network.

    SELECT SDO_NET.GET_INVALID_LINKS('SDO_PARTITIONED') FROM DUAL;

**Parent topic:** SDO_NET Package Subprograms

### 6.53 SDO_NET.GET_INVALID_NODES

#### Format

    SDO_NET.GET_INVALID_NODES(
         network IN VARCHAR2
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the invalid nodes in a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns an SDO_NUMBER_ARRAY object with a comma-delimited list of node ID numbers of invalid nodes in the specified network. If there are no invalid nodes, this function returns a null value.

#### Examples

The following example returns the invalid nodes in the SDO_PARTITIONED network.

    SELECT SDO_NET.GET_INVALID_NODES('SDO_PARTITIONED') FROM DUAL;

**Parent topic:** SDO_NET Package Subprograms

### 6.54 SDO_NET.GET_INVALID_PATHS

#### Format

    SDO_NET.GET_INVALID_PATHS(
         network IN VARCHAR2
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the invalid paths in a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns an SDO_NUMBER_ARRAY object with a comma-delimited list of node ID numbers of invalid paths in the specified network. If there are no invalid paths, this function returns a null value.

#### Examples

The following example returns the invalid paths in the SDO_PARTITIONED network.

    SELECT SDO_NET.GET_INVALID_PATHS('SDO_PARTITIONED') FROM DUAL;

**Parent topic:** SDO_NET Package Subprograms

### 6.55 SDO_NET.GET_ISOLATED_NODES

#### Format

    SDO_NET.GET_ISOLATED_NODES(
         network  IN VARCHAR2      
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the isolated nodes in a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns an SDO_NUMBER_ARRAY object with a comma-delimited list of node ID numbers of isolated nodes in the specified network. If there are no isolated nodes, this function returns a null value.

For a brief explanation of isolated nodes in a network, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns the isolated nodes in the SDO_PARTITIONED network.

    SELECT SDO_NET.GET_ISOLATED_NODES('SDO_PARTITIONED') FROM DUAL;

**Parent topic:** SDO_NET Package Subprograms

### 6.56 SDO_NET.GET_LINK_COST_COLUMN

#### Format

    SDO_NET.GET_LINK_COST_COLUMN(      
         network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the link cost column for a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the LINK_COST_COLUMN column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the link cost column for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LINK_COST_COLUMN('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_LINK_COST_COLUMN('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    COST

**Parent topic:** SDO_NET Package Subprograms

### 6.57 SDO_NET.GET_LINK_DIRECTION

#### Format

    SDO_NET.GET_LINK_DIRECTION(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the link direction for a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the LINK_DIRECTION column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the link direction for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LINK_DIRECTION('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_LINK_DIRECTION('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    DIRECTED

**Parent topic:** SDO_NET Package Subprograms

### 6.58 SDO_NET.GET_LINK_GEOM_COLUMN

#### Format

    SDO_NET.GET_LINK_GEOM_COLUMN(    
      network  IN VARCHAR2     
    ) RETURN VARCHAR2;

#### Description

Returns the name of the link geometry column for a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the LINK_GEOM_COLUMN column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the link geometry column for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LINK_GEOM_COLUMN('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_LINK_GEOM_COLUMN('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    LINK_GEOMETRY

**Parent topic:** SDO_NET Package Subprograms

### 6.59 SDO_NET.GET_LINK_GEOMETRY

#### Format

    SDO_NET.GET_LINK_GEOMETRY(      
      network          IN VARCHAR2,      
      link_id          IN NUMBER,      
      start_percentage IN NUMBER DEFAULT 0,      
      end_percentage   IN NUMBER DEFAULT 1.0      
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the entire geometry or a portion of the geometry associated with a link in a spatial network.

#### Parameters

network
Network name.

link_id
ID number of the link for which to return the geometry.

start_percentage
Percentage of the distance along the link to be used for the start point of the returned geometry. Expressed as a number between 0 and 1.0; for example, 0.5 is 50 percent. The default value is 0; that is, the start of the returned geometry is associated with the start point of the link.

end_percentage
Percentage of the distance along the link to be used for the end point of the returned geometry. Expressed as a number between 0 and 1.0; for example, 0.5 is 50 percent. The default value is 1.0; that is, the end of returned geometry is associated with the end point of the link.

#### Usage Notes

None.

#### Examples

The following example returns the geometry associated with the link whose link ID is 103 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LINK_GEOMETRY('ROADS_NETWORK', 103) FROM DUAL;

    SDO_NET.GET_LINK_GEOMETRY('ROADS_NETWORK',103)(SDO_GTYPE, SDO_SRID, SDO_POINT(X,
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1), SDO_ORDINATE_ARRAY(
    8, 4, 12, 4))

**Parent topic:** SDO_NET Package Subprograms

### 6.60 SDO_NET.GET_LINK_TABLE_NAME

#### Format

    SDO_NET.GET_LINK_TABLE_NAME(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the link table for a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the LINK_TABLE_NAME column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the link table for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LINK_TABLE_NAME('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_LINK_TABLE_NAME('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    ROADS_LINKS

**Parent topic:** SDO_NET Package Subprograms

### 6.61 SDO_NET.GET_LINKS_IN_PATH

#### Format

    SDO_NET.GET_LINKS_IN_PATH(      
      network  IN VARCHAR2,     
      path_id  IN NUMBER      
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the links in a path.

#### Parameters

network
Network name.

path_id
ID of the path for which to return the links.

#### Usage Notes

For an explanation of links and paths, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns the link ID values of links in the path in the `XYZ_NETWORK` network whose path ID is 1.

    SELECT SDO_NET.GET_LINKS_IN_PATH('XYZ_NETWORK', 1) FROM DUAL;

    SDO_NET.GET_LINKS_IN_PATH('XYZ_NETWORK',1)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(1102, 1104, 1105)

**Parent topic:** SDO_NET Package Subprograms

### 6.62 SDO_NET.GET_LRS_GEOM_COLUMN

#### Format

    SDO_NET.GET_LRS_GEOM_COLUMN(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the LRS geometry column for a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the LRS_GEOM_COLUMN column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the LRS geometry column for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LRS_GEOM_COLUMN('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_LRS_GEOM_COLUMN('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    ROAD_GEOM

**Parent topic:** SDO_NET Package Subprograms

### 6.63 SDO_NET.GET_LRS_LINK_GEOMETRY

#### Format

    SDO_NET.GET_LRS_LINK_GEOMETRY(
      network  IN VARCHAR2,      
      link_id  IN NUMBER      
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the LRS geometry associated with a link in a spatial LRS network.

#### Parameters

network
Network name.

link_id
ID number of the link for which to return the geometry.

#### Usage Notes

None.

#### Examples

The following example returns the LRS geometry associated with the link whose link ID is 103 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LRS_LINK_GEOMETRY('ROADS_NETWORK', 103) FROM DUAL;

    SDO_NET.GET_LRS_LINK_GEOMETRY('ROADS_NETWORK',103)(SDO_GTYPE, SDO_SRID, SDO_POIN
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2002, NULL, NULL, SDO_ELEM_INFO_ARRAY(1, 2, 1), SDO_ORDINATE_ARRAY(
    8, 4, 12, 4))

**Parent topic:** SDO_NET Package Subprograms

### 6.64 SDO_NET.GET_LRS_NODE_GEOMETRY

#### Format

    SDO_NET.GET_LRS_NODE_GEOMETRY(     
      network IN VARCHAR2,      
      node_id IN NUMBER      
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the LRS geometry associated with a node in a spatial LRS network.

#### Parameters

network
Network name.

node_id
ID number of the node for which to return the geometry.

#### Usage Notes

None.

#### Examples

The following example returns the LRS geometry associated with the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LRS_NODE_GEOMETRY('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_LRS_NODE_GEOMETRY('ROADS_NETWORK',3)(SDO_GTYPE, SDO_SRID, SDO_POINT(
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(8, 4, NULL), NULL, NULL)

**Parent topic:** SDO_NET Package Subprograms

### 6.65 SDO_NET.GET_LRS_TABLE_NAME

#### Format

    SDO_NET.GET_LRS_TABLE_NAME(      
      network  IN VARCHAR2     
    ) RETURN VARCHAR2;

#### Description

Returns the name of the table containing LRS geometries in a spatial LRS network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the LRS_TABLE_NAME column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the table that contains LRS geometries for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_LRS_TABLE_NAME('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_LRS_TABLE_NAME('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    ROADS

**Parent topic:** SDO_NET Package Subprograms

### 6.66 SDO_NET.GET_NETWORK_TYPE

#### Format

    SDO_NET.GET_NETWORK_TYPE(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the network type.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the NETWORK_TYPE column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the network type for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NETWORK_TYPE('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_NETWORK_TYPE('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    Roadways

**Parent topic:** SDO_NET Package Subprograms

### 6.67 SDO_NET.GET_NO_OF_HIERARCHY_LEVELS

#### Format

    SDO_NET.GET_NO_OF_HIERARCHY_LEVELS(      
      network  IN VARCHAR2      
    ) RETURN NUMBER;

#### Description

Returns the number of hierarchy levels for a network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the NO_OF_HIERARCHY_LEVELS column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).

#### Examples

The following example returns the number of hierarchy levels for the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NO_OF_HIERARCHY_LEVELS('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_NO_OF_HIERARCHY_LEVELS('ROADS_NETWORK')
    ---------------------------------------------------
                                                      1

**Parent topic:** SDO_NET Package Subprograms

### 6.68 SDO_NET.GET_NO_OF_LINKS

#### Format

    SDO_NET.GET_NO_OF_LINKS(      
      network  IN VARCHAR2      
    ) RETURN NUMBER;

or

    SDO_NET.GET_NO_OF_LINKS(      
      network       IN VARCHAR2,      
      hierarchy_id  IN NUMBER      
    ) RETURN NUMBER;

#### Description

Returns the number of links for a network or a hierarchy level in a network.

#### Parameters

network
Network name.

hierarchy_id
Hierarchy level number for which to return the number of links.

#### Usage Notes

None.

#### Examples

The following example returns the number of links in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NO_OF_LINKS('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_NO_OF_LINKS('ROADS_NETWORK')
    ----------------------------------------
                                          10

**Parent topic:** SDO_NET Package Subprograms

### 6.69 SDO_NET.GET_NO_OF_NODES

#### Format

    SDO_NET.GET_NO_OF_NODES(      
      network  IN VARCHAR2      
    ) RETURN NUMBER;

or

    SDO_NET.GET_NO_OF_NODES(      
      network       IN VARCHAR2,      
      hierarchy_id  IN NUMBER      
    ) RETURN NUMBER;

#### Description

Returns the number of nodes for a network or a hierarchy level in a network.

#### Parameters

network
Network name.

hierarchy_id
Hierarchy level number for which to return the number of nodes.

#### Usage Notes

For information about nodes and related concepts, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns the number of nodes in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NO_OF_NODES('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_NO_OF_NODES('ROADS_NETWORK')
    ----------------------------------------
                                           8

**Parent topic:** SDO_NET Package Subprograms

### 6.70 SDO_NET.GET_NODE_DEGREE

#### Format

    SDO_NET.GET_NODE_DEGREE(      
      network  IN VARCHAR2,      
      node_id  IN NUMBER      
    ) RETURN NUMBER;

#### Description

Returns the number of links to a node.

#### Parameters

network
Network name.

node_id
Node ID of the node for which to return the number of links.

#### Usage Notes

For information about node degree and related Network Data Model Graph concepts, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns the number of links to the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NODE_DEGREE('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_NODE_DEGREE('ROADS_NETWORK',3)
    ------------------------------------------
                                             3

**Parent topic:** SDO_NET Package Subprograms

### 6.71 SDO_NET.GET_NODE_GEOM_COLUMN

#### Format

    SDO_NET.GET_NODE_GEOM_COLUMN(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the geometry column for nodes in a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the NODE_GEOM_COLUMN column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the geometry column for nodes in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NODE_GEOM_COLUMN('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_NODE_GEOM_COLUMN('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    NODE_GEOMETRY

**Parent topic:** SDO_NET Package Subprograms

### 6.72 SDO_NET.GET_NODE_GEOMETRY

#### Format

    SDO_NET.GET_NODE_GEOMETRY(      
      network  IN VARCHAR2,      
      node_id  IN NUMBER      
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the LRS geometry associated with a node in a spatial network.

#### Parameters

network
Network name.

node_id
ID number of the node for which to return the geometry.

#### Usage Notes

None.

#### Examples

The following example returns the geometry associated with the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NODE_GEOMETRY('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_NODE_GEOMETRY('ROADS_NETWORK',3)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(8, 4, NULL), NULL, NULL)

**Parent topic:** SDO_NET Package Subprograms

### 6.73 SDO_NET.GET_NODE_IN_DEGREE

#### Format

    SDO_NET.GET_NODE_IN_DEGREE(      
      network  IN VARCHAR2,      
      node_id  IN NUMBER      
    ) RETURN NUMBER;

#### Description

Returns the number of inbound links to a node.

#### Parameters

network
Network name.

node_id
Node ID of the node for which to return the number of inbound links.

#### Usage Notes

For information about node degree and related Network Data Model Graph concepts, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns the number of inbound links to the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NODE_IN_DEGREE('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_NODE_IN_DEGREE('ROADS_NETWORK',3)
    ---------------------------------------------
                                                1

**Parent topic:** SDO_NET Package Subprograms

### 6.74 SDO_NET.GET_NODE_OUT_DEGREE

#### Format

    SDO_NET.GET_NODE_OUT_DEGREE(      
      network  IN VARCHAR2,      
      node_id  IN NUMBER      
    ) RETURN NUMBER;

#### Description

Returns the number of outbound links from a node.

#### Parameters

network
Network name.

node_id
Node ID of the node for which to return the number of outbound links.

#### Usage Notes

For information about node degree and related Network Data Model Graph concepts, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns the number of outbound links from the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NODE_OUT_DEGREE('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_NODE_OUT_DEGREE('ROADS_NETWORK',3)
    ----------------------------------------------
                                                 2

**Parent topic:** SDO_NET Package Subprograms

### 6.75 SDO_NET.GET_NODE_TABLE_NAME

#### Format

    SDO_NET.GET_NODE_TABLE_NAME(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the table that contains the nodes in a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the NODE_TABLE_NAME column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the table that contains the nodes in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_NODE_TABLE_NAME('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_NODE_TABLE_NAME('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    ROADS_NODES

**Parent topic:** SDO_NET Package Subprograms

### 6.76 SDO_NET.GET_OUT_LINKS

#### Format

    SDO_NET.GET_OUT_LINKS(      
      network  IN VARCHAR2,      
      node_id  IN NUMBER      
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns an array of link ID numbers of the outbound links from a node.

#### Parameters

network
Network name.

node_id
ID of the node for which to return the array of outbound links.

#### Usage Notes

For information about outbound links and related Network Data Model Graph concepts, see [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example returns an array of link ID numbers of the outbound links from the node whose node ID is 3 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_OUT_LINKS('ROADS_NETWORK', 3) FROM DUAL;

    SDO_NET.GET_OUT_LINKS('ROADS_NETWORK',3)
    --------------------------------------------------------------------------------
    SDO_NUMBER_ARRAY(103, 201)

**Parent topic:** SDO_NET Package Subprograms

### 6.77 SDO_NET.GET_PARENT_FEATURE_IDS

#### Format

    SDO_NET.GET_PARENT_FEATURE_IDS(      
      feature_layer_id  IN NUMBER,      
      feature_id        IN NUMBER      
    ) RETURN SDO_NET_LAYER_FEAT_ARRAY;

#### Description

Returns the feature layer ID and parent feature IDs for the specified feature. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

#### Parameters

feature_layer_id
ID of the feature layer for the feature (that is, the child feature).

feature_id
ID of the feature.

#### Usage Notes

To get the feature layer ID and feature ID of the child features for a specified feature, use the SDO_NET.GET_CHILD_FEATURE_IDS function.

For information about features, including parent and child features, see [Features and Feature Layers](network-data-model-graph-overview.md).

#### Examples

The following example returns and displays the parent feature IDs for feature 1 in the `POI` feature layer.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      feature_ids SDO_NET_LAYER_FEAT_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      feature_ids := sdo_net.get_parent_feature_ids(feature_layer_id, feature_id);
      FOR i in 1..feature_ids.count
      LOOP
        --dbms_output.put_line('['||i||']'||' FEATURE_LAYER_ID   = '||feature_ids(i).feature_layer_id);
        dbms_output.put_line('['||i||']'||' FEATURE_ID         = '||feature_ids(i).feature_id);
        dbms_output.put_line('---');
      END LOOP;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.78 SDO_NET.GET_PARTITION_SIZE

#### Format

    SDO_NET.GET_PARTITION_SIZE(      
      network              IN VARCHAR2,      
      partition_id         IN VARCHAR2,      
      link_level           IN NUMBER DEFAULT 1,      
      include_user_data    IN VARCHAR2 DEFAULT 'FALSE',      
      include_spatial_data IN VARCHAR2 DEFAULT 'FALSE'
    ) RETURN NUMBER;

#### Description

Gets the estimated size (in bytes) for a specified combination of partition ID and link level.

#### Parameters

network
Network name.

partition_id
Partition ID number.

link_level
Link level (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in computing a path.

include_user_data
`TRUE` if the size should include any user data associated with the network elements represented in each BLOB, or `FALSE` (the default) if the size should not include any user data.

include_spatial_data
`TRUE` if the size should include spatial geometry definitions associated with the network elements represented in each BLOB, or `FALSE` (the default) if the size should not include spatial geometry definitions.

#### Usage Notes

The returned size of a network partition is a rough estimate and might vary depending on the Java Virtual Machine and garbage collection.

For information about using partitioned networks to perform analysis using the load on demand approach, see [Network Analysis Using Load on Demand](network-data-model-graph-overview.md).

#### Examples

The following example returns the number of bytes for the partition associated with partition ID 1 and link level 1 in the SDO_PARTITIONED network, not including any user data or spatial data.

    SELECT SDO_NET.GET_PARTITION_SIZE('SDO_PARTITIONED', 1, 1, 'N', 'N') FROM DUAL;

    SDO_NET.GET_PARTITION_SIZE('SDO_PARTITIONED',1,1,'FALSE','FALSE')
    ---------------------------------------------------------
                                                         5192

**Parent topic:** SDO_NET Package Subprograms

### 6.79 SDO_NET.GET_PATH_GEOM_COLUMN

#### Format

    SDO_NET.GET_PATH_GEOM_COLUMN(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the geometry column for paths in a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the PATH_GEOM_COLUMN column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the geometry column for paths in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_PATH_GEOM_COLUMN('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_PATH_GEOM_COLUMN('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    PATH_GEOMETRY

**Parent topic:** SDO_NET Package Subprograms

### 6.80 SDO_NET.GET_PATH_TABLE_NAME

#### Format

    SDO_NET.GET_PATH_TABLE_NAME(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the name of the table that contains the paths in a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

This function returns the value of the PATH_TABLE_NAME column for the network in the USER_SDO_NETWORK_METADATA view (see [Table 5-33](network-data-model-graph-overview.md) in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md)).

#### Examples

The following example returns the name of the table that contains the paths in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_PATH_TABLE_NAME('ROADS_NETWORK') FROM DUAL;

    SDO_NET.GET_PATH_TABLE_NAME('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    ROADS_PATHS

**Parent topic:** SDO_NET Package Subprograms

### 6.81 SDO_NET.GET_PERCENTAGE

#### Format

    SDO_NET.GET_PERCENTAGE(      
      network  IN VARCHAR2,      
      link_id  IN NUMBER,      
      pt_geom  IN SDO_GEOMETRY      
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the percentage of the distance along a link's line string geometry of a point geometry.

#### Parameters

network
Network name.

link_id
ID number of the link.

pt_geom
Point geometry.

#### Usage Notes

This function returns a value between 0 and 1. For example, if the point is 25 percent (one-fourth) of the distance between the start node and end node for the link, the function returns .25.

If `pt_geom` is not on the link geometry, the nearest point on the link geometry to `pt_geom` is used.

To find the point geometry that is a specified percentage of the distance along a link's line string geometry, use the SDO_NET.GET_PT function.

#### Examples

The following example returns the percentage (as a decimal fraction) of the distance of a specified point along the geometry associated with the link whose link ID is 101 in the network named `ROADS_NETWORK`.

    SQL> SELECT SDO_NET.GET_PERCENTAGE('ROADS_NETWORK', 101,
      SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(2, 2.5, NULL), NULL, NULL))
      FROM DUAL;  2    3

    SDO_NET.GET_PERCENTAGE('ROADS_NETWORK',101,SDO_GEOMETRY(2001,NULL,SDO_POINT_TYPE
    --------------------------------------------------------------------------------
                                                                                 .25

**Parent topic:** SDO_NET Package Subprograms

### 6.82 SDO_NET.GET_PHANTOM_FEATURES

#### Format

    SDO_NET.GET_PHANTOM_FEATURES(      
      feature_layer_id  IN NUMBER      
    ) RETURN SDO_NUMBER_ARRAY;

#### Description

Returns the IDs of phantom features in a feature layer. A phantom feature is a feature that references nonexistent network elements (nodes or links).

#### Parameters

feature_layer_id
ID of the feature layer containing the features.

#### Usage Notes

To delete the phantom features in a feature layer, use the SDO_NET.DELETE_PHANTOM_FEATURES procedure.

#### Examples

The following example gets and displays the feature IDs of phantom features in a specified feature layer.

    DECLARE
      feature_layer_id NUMBER;
      feature_ids SDO_NUMBER_ARRAY;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      feature_ids := sdo_net.get_phantom_features(feature_layer_id);
      dbms_output.put_line('Phantom Features:');
      for i in 1..feature_ids.count loop
        dbms_output.put_line('['||i||'] '||feature_ids(i));
      end loop;
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.83 SDO_NET.GET_PT

#### Format

    SDO_NET.GET_PT(      
      network     IN VARCHAR2,      
      link_id     IN NUMBER,      
      percentage  IN NUMBER      
    ) RETURN SDO_GEOMETRY;

#### Description

Returns the point geometry that is a specified percentage of the distance along a link's line string geometry.

#### Parameters

network
Network name.

link_id
ID number of the link for which to return the point geometry at the specified `percentage` distance.

percentage
Percentage value as a decimal fraction between 0 and 1. For example, 0.25 is 25 percent.

#### Usage Notes

To find the percentage along a link geometry for a specified point, use the SDO_NET.GET_PERCENTAGE function.

#### Examples

The following example returns the point geometry that is 25 percent of the distance from the start node along the geometry associated with the link whose link ID is 101 in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.GET_PT('ROADS_NETWORK', 101, 0.25) FROM DUAL;

    SDO_NET.GET_PT('ROADS_NETWORK',101,0.25)(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z)
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2001, NULL, SDO_POINT_TYPE(2, 2.5, NULL), NULL, NULL)

**Parent topic:** SDO_NET Package Subprograms

### 6.84 SDO_NET.IS_HIERARCHICAL

#### Format

    SDO_NET.IS_HIERARCHICAL(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network has more than one level of hierarchy; returns the string `FALSE` if the network does not have more than one level of hierarchy.

#### Parameters

network
Network name.

#### Usage Notes

For an explanation of network hierarchy, see [Network Hierarchy](network-data-model-graph-overview.md).

#### Examples

The following example checks if the network named `ROADS_NETWORK` has more than one level of hierarchy.

    SELECT SDO_NET.IS_HIERARCHICAL('ROADS_NETWORK') FROM DUAL;

    SDO_NET.IS_HIERARCHICAL('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.85 SDO_NET.IS_LINK_IN_PATH

#### Format

    SDO_NET.IS_LINK_IN_PATH(      
      network  IN VARCHAR2,      
      path_id  IN NUMBER,      
      link_id  IN NUMBER,      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the specified link is in the specified path; returns the string `FALSE` if the specified link is not in the specified path.

#### Parameters

network
Network name.

path_id
ID number of the path.

link_id
ID number of the link.

#### Usage Notes

You can use this function to check if a specific link is included in a specific path.

#### Examples

The following example checks if the link with link ID 1 is in the path with path ID 1 in the network named `SDO_NET1`.

    SELECT SDO_NET.IS_LINK_IN_PATH('SDO_NET1', 1, 1) FROM DUAL;

    SDO_NET.IS_LINK_IN_PATH('SDO_NET1',1,1)
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.86 SDO_NET.IS_LOGICAL

#### Format

    SDO_NET.IS_LOGICAL(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network is a logical network; returns the string `FALSE` if the network is not a logical network.

#### Parameters

network
Network name.

#### Usage Notes

A network can be a spatial network or a logical network, as explained in [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

#### Examples

The following example checks if the network named `ROADS_NETWORK` is a logical network.

    SELECT SDO_NET.IS_LOGICAL('ROADS_NETWORK') FROM DUAL;

    SDO_NET.IS_LOGICAL('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    FALSE

**Parent topic:** SDO_NET Package Subprograms

### 6.87 SDO_NET.IS_NODE_IN_PATH

#### Format

    SDO_NET.IS_NODE_IN_PATH(      
      network  IN VARCHAR2,      
      path_id  IN NUMBER,      
      node_id  IN NUMBER,      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the specified node is in the specified path; returns the string `FALSE` if the specified node is not in the specified path.

#### Parameters

network
Network name.

path_id
ID number of the path.

node_id
ID number of the node.

#### Usage Notes

You can use this function to check if a specific node is included in a specific path.

#### Examples

The following example checks if the node with node ID 1 is in the path with path ID 1 in the network named `SDO_NET1`.

    SELECT SDO_NET.IS_NODE_IN_PATH('SDO_NET1', 1, 1) FROM DUAL;

    SDO_NET.IS_NODE_IN_PATH('SDO_NET1',1,1)
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.88 SDO_NET.IS_SPATIAL

#### Format

    SDO_NET.IS_SPATIAL(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network is a spatial network; returns the string `FALSE` if the network is not a spatial network.

#### Parameters

network
Network name.

#### Usage Notes

A network can be a spatial network or a logical network, as explained in [Network Data Model Graph Concepts](network-data-model-graph-overview.md).

You can further check for the geometry type of a spatial network by using the following functions: SDO_NET.LRS_GEOMETRY_NETWORK, SDO_NET.SDO_GEOMETRY_NETWORK, and SDO_NET.TOPO_GEOMETRY_NETWORK.

#### Examples

The following example checks if the network named `ROADS_NETWORK` is a spatial network.

    SELECT SDO_NET.IS_SPATIAL('ROADS_NETWORK') FROM DUAL;

    SDO_NET.IS_SPATIAL('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.89 SDO_NET.LOAD_CONFIG

#### Format

    SDO_NET.LOAD_CONFIG(     
      file_directory  IN VARCHAR2,     
      file_name       IN VARCHAR2);

#### Description

Loads (or reloads) the configuration for load on demand Java stored procedures from the specified XML file. The load on demand configuration is mainly for partition BLOB translation and partition cache configuration. (The Java stored procedures are classes in the package `oracle.spatial.network.lod`.)

#### Parameters

file_directory
Directory object that identifies the path for the XML file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

file_name
Name of the XML file containing the information to be loaded.

#### Usage Notes

A default configuration is provided for load on demand. You can use this procedure if you need to change the default configuration.

For information about configuring the load on demand environment, including the partition cache, see [Configuring the Partition Cache](network-data-model-graph-overview.md).

#### Examples

The following example loads the load on demand configuration from a specified XML file.

    EXECUTE SDO_NET.LOAD_CONFIG('WORK_DIR', 'netlodcfg.xml');

**Parent topic:** SDO_NET Package Subprograms

### 6.90 SDO_NET.LOGICAL_PARTITION

#### Format

    SDO_NET.LOGICAL_PARTITION(      
      network              IN VARCHAR2,      
      partition_table_name IN VARCHAR2,      
      max_num_nodes        IN NUMBER,      
      log_loc              IN VARCHAR2,      
      log_file             IN VARCHAR2,      
      open_mode            IN VARCHAR2 DEFAULT 'A',      
      link_level           IN NUMBER DEFAULT 1);

or

    SDO_NET.LOGICAL_PARTITION(      
      network              IN VARCHAR2,      
      partition_table_name IN VARCHAR2,      
      max_num_nodes        IN NUMBER,      
      log_loc              IN VARCHAR2,      
      log_file             IN VARCHAR2,      
      open_mode            IN VARCHAR2 DEFAULT 'A',      
      link_level           IN NUMBER DEFAULT 1,      
      part_size_tolerance  IN NUMBER);

#### Description

Partitions a logical network, and stores the information in the partition table.

**Note:**

If the logical network is a power law (scale-free) network, do not use this procedure to partition it, but instead use the SDO_NET.LOGICAL_POWERLAW_PARTITION procedure.

#### Parameters

network
Network name.

partition_table_name
Name of the partition table, which is created by this procedure. (If an existing table with the specified name already exists, it is updated with partition information for the specified link level.) The partition table is described in [Partition Table](network-data-model-graph-overview.md).

max_num_nodes
Maximum number of nodes to include in each partition. For example, if you specify 5000 and if the network contains 50,000 nodes, each partition will have 5000 or fewer nodes, and the total number of partitions will be 10 or higher.

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about operations on the logical network, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

link_level
Network link level on which to perform the partitioning (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in computing a path.

part_size_tolerance
Allowed tolerance in partition size expressed as a decimal fraction of `max_num_nodes`. Must be from 0 to 1. This parameter allows the partitioning procedure to create partitions with sizes larger than the one specified by `max_num_nodes`, thereby providing the flexibility to generate partitions with reduced inter-connectivity. For example, if `max_num_nodes` is 5000 and `part_size_tolerance` is 0.1, a partition can include up to 5500 (5000+500 because 500 is 0.1\*5000) nodes.

#### Usage Notes

The format with the `part_size_tolerance` parameter enables you to partition logical networks with a primary focus on reducing the inter-connectivity among partitions while keeping the edge-cut small.

After you use this procedure to create the partitions, consider using the SDO_NET.GENERATE_PARTITION_BLOBS procedure, to enable better performance for many network analysis operations, especially with large networks.

#### Examples

The following example creates partitions for link level 1 in the `MY_LOGICAL_NET` network, and creates the MY_LOGICAL_PART_TAB table. The maximum number of nodes to be placed in any partition is 5000. Information about the operation is added (`open_mode => 'a'`) to the `my_logical_part.log` file located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.LOGICAL_PARTITION(network => 'MY_LOGICAL_NET', -
      partition_table_name => 'my_logical_part_tab',-
      max_num_nodes => 5000,-
      log_loc => 'LOG_DIR', log_file=> 'my_logical_part.log',-
      link_level => 1, open_mode => 'a');

The following example creates partitions for link level 1 in the `MY_LOGICAL_NET` network, and creates the MY_LOGICAL_PART_TAB table. The maximum number of nodes to be placed in any partition is 5500 because of the combination of the `max_num_nodes` and `part_size_tolerance` values (5000 + 0.1\*5000 = 5500). Information about the operation is written (`open_mode => 'w'`) to the `my_logical_part.log` file located in the location associated with the directory object named `LOG_DIR`, replacing any existing file with that name in that location.

    EXECUTE SDO_NET.LOGICAL_PARTITION(network => 'MY_LOGICAL_NET', -
      partition_table_name => 'my_logical_part_tab',-
      max_num_nodes => 5000,-
      log_loc => 'LOG_DIR', log_file=> 'my_logical_part.log',-
      link_level => 1, open_mode => 'w',
      part_size_tolerance => 0.1);

**Parent topic:** SDO_NET Package Subprograms

### 6.91 SDO_NET.LOGICAL_POWERLAW_PARTITION

#### Format

    SDO_NET.LOGICAL_POWERLAW_PARTITION(      
      network              IN VARCHAR2,      
      partition_table_name IN VARCHAR2,      
      max_num_nodes        IN NUMBER,      
      log_loc              IN VARCHAR2,      
      log_file             IN VARCHAR2,      
      open_mode            IN VARCHAR2 DEFAULT 'A',      
      link_level           IN NUMBER DEFAULT 1,      
      part_size_tolerance  IN NUMBER DEFAULT 0);

#### Description

Partitions a logical power law (also called scale-free) network, and stores the information in the partition table. (In a power law network, the node degree values contain the power law information.)

#### Parameters

network
Network name.

partition_table_name
Name of the partition table, which is created by this procedure. (If an existing table with the specified name already exists, it is updated with partition information for the specified link level.) The partition table is described in [Partition Table](network-data-model-graph-overview.md).

max_num_nodes
Maximum number of nodes to include in each partition. For example, if you specify 5000 and if the network contains 50,000 nodes, each partition will have 5000 or fewer nodes, and the total number of partitions will be 10 or higher.

If the `part_size_tolerance` value is greater than 0, the maximum number of nodes to include in each partition is increased, as explained in the description of that parameter.

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about operations on the logical power law network, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

link_level
Network link level on which to perform the partitioning (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in computing a path.

part_size_tolerance
Allowed tolerance in partition size expressed as a percentage of `max_num_nodes`. Must be from 0 (the default) to 100.

A `part_size_tolerance` value greater than 0 effectively raises the `max_num_nodes` value. For example, if `max_num_nodes` is 5000 and you specify `part_size_tolerance` as 10, then the actual maximum number of nodes to include in each partition is 5500 (5000 + 500, because 500 is 10 percent of 5000). In deciding whether to use `part_size_tolerance` and what value to specify, consider the cache size and the probability of related nodes being placed in different partitions.

#### Usage Notes

After you use this procedure to create the partitions, consider using the SDO_NET.GENERATE_PARTITION_BLOBS procedure, to enable better performance for many network analysis operations, especially with large networks.

If the logical network is not a power law network, do not use this procedure, but instead use the SDO_NET.LOGICAL_PARTITION procedure.

#### Examples

The following example creates partitions for link level 1 in the `MY_LOGICAL_PLAW_NET` network, and creates the MY_LOGICAL_PLAW_PART_TAB table. The maximum number of nodes to be placed in any partition is 5000. Information about the operation is added (`open_mode => 'a'`) to the `my_logical_plaw_part.log` file, located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.LOGICAL_POWERLAW_PARTITION(network => 'MY_LOGICAL_PLAW_NET', -
      partition_table_name => 'my_logical_plaw_part_tab',-
      max_num_nodes => 5000,-
      log_loc => 'LOG_DIR', log_file=> 'my_logical_plaw_part.log',-
      link_level => 1, open_mode => 'a');

**Parent topic:** SDO_NET Package Subprograms

### 6.92 SDO_NET.LRS_GEOMETRY_NETWORK

#### Format

    SDO_NET.LRS_GEOMETRY_NETWORK(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network is a spatial network containing LRS geometries; returns the string `FALSE` if the network is not a spatial network containing LRS geometries.

#### Parameters

network
Network name.

#### Usage Notes

A network contains LRS geometries if the GEOMETRY_TYPE column in its entry in the USER_SDO_NETWORK_METADATA view contains the value `LRS_GEOMETRY`. (The USER_SDO_NETWORK_METADATA view is explained in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md).)

#### Examples

The following example checks if the network named `ROADS_NETWORK` is a spatial network containing LRS geometries.

    SELECT SDO_NET.LRS_GEOMETRY_NETWORK('ROADS_NETWORK') FROM DUAL;

    SDO_NET.LRS_GEOMETRY_NETWORK('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.93 SDO_NET.NETWORK_EXISTS

#### Format

    SDO_NET.NETWORK_EXISTS(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network exists; returns the string `FALSE` if the network does not exist.

#### Parameters

network
Network name.

#### Usage Notes

If you drop a network (using the SDO_NET.DROP_NETWORK procedure), the network no longer exists.

#### Examples

The following example checks if the network named `ROADS_NETWORK` exists.

    SELECT SDO_NET.NETWORK_EXISTS('ROADS_NETWORK') FROM DUAL;

    SDO_NET.NETWORK_EXISTS('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.94 SDO_NET.POST_XML

#### Format

    SDO_NET.POST_XML(      
      url      IN VARCHAR2,      
      request  IN XMLTYPE      
    ) RETURN XMLTYPE;

#### Description

Sends an XML request to a URL, and returns the XML response.

#### Parameters

url
Uniform resource locator (URL) to receive the request.

request
Request in XML form.

#### Usage Notes

For information about the XML API to the Network Data Model Graph, see [Network Data Model Graph XML Interface](network-data-model-graph-overview.md).

#### Examples

The following example specifies an XML request, and sends it to a URL and returns the XML response, which it then displays.

    DECLARE
      xml_request varchar2(4000);
      ndmws_url varchar2(4000);
      xml_response xmltype;
    BEGIN
      xml_request :=
    '<?xml version="1.0" ?>
    <networkAnalysisRequest
       xmlns="http://xmlns.oracle.com/spatial/network"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:gml="http://www.opengis.net/gml">
      <networkName>HILLSBOROUGH_NETWORK2</networkName>
      <shortestPath>
        <startPoint>
          <nodeID>1533</nodeID>
        </startPoint>
        <endPoint>
          <nodeID>10043</nodeID>
        </endPoint>
        <subPathRequestParameter>
          <cost> true </cost>
          <isFullPath> true </isFullPath>
          <startLinkIndex> true </startLinkIndex>
          <startPercentage> true </startPercentage>
          <endLinkIndex> true </endLinkIndex>
          <endPercentage> true </endPercentage>
        <pathRequestParameter>
          <cost> true </cost>
          <isSimple> true </isSimple>
          <startNodeID>true</startNodeID>
          <endNodeID>true</endNodeID>
          <noOfLinks>true</noOfLinks>
          <linksRequestParameter>
            <onlyLinkID>true</onlyLinkID>
          </linksRequestParameter>
          <nodesRequestParameter>
            <onlyNodeID>true</onlyNodeID>
          </nodesRequestParameter>
        </pathRequestParameter>
        </subPathRequestParameter>
      </shortestPath>
    </networkAnalysisRequest>';
      ndmws_url := 'http://localhost:7001/SpatialWS-SpatialWS-context-root/SpatialWSXmlServlet';
      xml_response := sdo_net.POST_XML(ndmws_url, XMLTYPE(xml_request));
      dbms_output.put_line(xml_response.getStringVal());
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.95 SDO_NET.REGISTER_CONSTRAINT

#### Format

    SDO_NET.REGISTER_CONSTRAINT(      
      constraint_name IN VARCHAR2,      
      class_name      IN VARCHAR2,      
      directory_name  IN VARCHAR2,      
      description     IN VARCHAR2);

#### Description

Loads the compiled Java code for the specified network constraint into the Java class repository in the database, and loads the class name into the CLASS column of the USER_SDO_NETWORK_CONSTRAINTS view (described in [xxx_SDO_NETWORK_CONSTRAINTS Views](network-data-model-graph-overview.md)).

#### Parameters

constraint_name
Name of the network constraint.

<!-- -->

class_name
Fully qualified name (including the name of the package) of the class that implements the network constraint.

<!-- -->

directory_name
Name of the directory object (created using the SQL statement CREATE DIRECTORY) that identifies the location of the class file created when you compiled the network constraint.

<!-- -->

description
Description of the network constraint.

#### Usage Notes

Before you call this procedure, you must insert a row into the USER_SDO_NETWORK_CONSTRAINTS view, compile the code for the Java class that implements the network constraint, and use the CREATE DIRECTORY statement to create a directory object identifying the location of the compiled class. For more information about network constraints, see [Network Constraints](network-data-model-graph-overview.md).

To delete the row for the constraint from the USER_SDO_NETWORK_CONSTRAINTS view and thus disable the constraint, use the SDO_NET.DEREGISTER_CONSTRAINT procedure.

#### Examples

The following example registers a network constraint named `GivenProhibitedTurn`.

    -- Set up the network constraint.
    REM
    REM Create the geor_dir on the file system first.
    REM
    -- Connect as SYSTEM.
    DECLARE
      -- This is the directory that contains the CLASS file generated when you
      -- compiled the network constraint.
      geor_dir varchar2(1000) := 'C:\my_data\files81\PROTOTYPES\NETWORK_CONSTRAINT\PLSQL_EXAMPLE';
    BEGIN
      EXECUTE IMMEDIATE 'CREATE OR REPLACE DIRECTORY work_dir AS''' || geor_dir || '''';
    END;
    /
    GRANT read,write on directory work_dir to net_con;

    -- Connect as the user that will register the constraint.

    REM
    REM Compile GivenProhibitedTurn before you register the constraint.
    REM
    BEGIN
      SDO_NET.REGISTER_CONSTRAINT('GivenProhibitedTurn',
         'com/network/constraints/ProhibitedTurn',
         'WORK_DIR', 'This is a network constraint that '||
         'prohibits certain turns');

    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.96 SDO_NET.SDO_GEOMETRY_NETWORK

#### Format

    SDO_NET.SDO_GEOMETRY_NETWORK(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network is a spatial network containing SDO geometries (spatial geometries without measure information); returns the string `FALSE` if the network is not a spatial network containing SDO geometries.

#### Parameters

network
Network name.

#### Usage Notes

A network contains SDO geometries if the GEOMETRY_TYPE column in its entry in the USER_SDO_NETWORK_METADATA view contains the value `SDO_GEOMETRY`. (The USER_SDO_NETWORK_METADATA view is explained in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md).)

#### Examples

The following example checks if the network named `ROADS_NETWORK` is a spatial network containing SDO geometries.

    SELECT SDO_NET.SDO_GEOMETRY_NETWORK('ROADS_NETWORK') FROM DUAL;

    SDO_NET.SDO_GEOMETRY_NETWORK('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    FALSE

**Parent topic:** SDO_NET Package Subprograms

### 6.97 SDO_NET.SET_LOGGING_LEVEL

#### Format

    SDO_NET.SET_LOGGING_LEVEL(      
      level  IN NUMBER);

#### Description

Sets the minimum level of severity for messages to be displayed for network operations.

#### Parameters

level
Minimum severity level for messages to be displayed for network operations. Must be one of the numeric constants specified in the Usage Notes.

#### Usage Notes

All messages at the specified logging level and higher levels will be written. The logging levels, from highest to lowest, are:

    SDO_NET.LOGGING_LEVEL_FATAL
    SDO_NET.LOGGING_LEVEL_ERROR
    SDO_NET.LOGGING_LEVEL_WARN
    SDO_NET.LOGGING_LEVEL_INFO
    SDO_NET.LOGGING_LEVEL_DEBUG
    SDO_NET.LOGGING_LEVEL_FINEST

The logging level is the Java logging level from the underlying implementation of this function; therefore, to see the Java logging output on the console, execute the following statements beforehand:

    SET SERVEROUTPUT ON;
    EXECUTE DBMS_JAVA.SET_OUTPUT(10000);

#### Examples

The following example sets the logging level at `SDO_NET.``LOGGING_LEVEL_ERROR`, which means that only messages with a severity of `SDO_NET.LOGGING_LEVEL_ERROR` or `SDO_NET.LOGGING_LEVEL_FATAL` will be displayed.

    EXECUTE SDO_NET.SET_LOGGING_LEVEL(SDO_NET.LOGGING_LEVEL_ERROR);

**Parent topic:** SDO_NET Package Subprograms

### 6.98 SDO_NET.SET_MAX_JAVA_HEAP_SIZE

#### Format

    SDO_NET.SET_MAX_JAVA_HEAP_SIZE(      
      bytes  IN NUMBER);

#### Description

Sets the Java maximum heap size for an application to run in an Oracle Java virtual machine.

#### Parameters

bytes
Number of bytes for the Java maximum heap size.

#### Usage Notes

If you encounter the `java.lang.OutOfMemoryError` exception, you can use this procedure to increase the maximum heap size.

If you specify a value greater than the system limit, the system limit is used.

#### Examples

The following example sets the Java maximum heap size to 536870912 (512 MB).

    EXECUTE SDO_NET.SET_MAX_JAVA_HEAP_SIZE(536870912);

**Parent topic:** SDO_NET Package Subprograms

### 6.99 SDO_NET.SPATIAL_PARTITION

#### Format

    SDO_NET.SPATIAL_PARTITION(      
      network              IN VARCHAR2,      
      partition_table_name IN VARCHAR2,      
      max_num_nodes        IN NUMBER,      
      log_loc              IN VARCHAR2,      
      log_file             IN VARCHAR2,      
      open_mode            IN VARCHAR2 DEFAULT 'A',      
      link_level           IN NUMBER DEFAULT 1);

#### Description

Partitions a spatial network, and stores the information in the partition table.

#### Parameters

network
Network name.

partition_table_name
Name of the partition table, which is created by this procedure. (If an existing table with the specified name already exists, it is updated with partition information for the specified link level.) The partition table is described in [Partition Table](network-data-model-graph-overview.md).

max_num_nodes
Maximum number of nodes to include in each partition. For example, if you specify 5000 and if the network contains 50,000 nodes, each partition will have 5000 or fewer nodes, and the total number of partitions will be 10 or higher.

log_loc
Directory object that identifies the path for the log file. To create a directory object, use the SQL\*Plus command CREATE DIRECTORY.

log_file
Log file containing information about spatial network operations, including any possible errors or problems.

open_mode
A one-character code indicating the mode in which to open the log file: `W` for write over (that is, delete any existing log file at the specified location and name, and create a new file), or `A` (the default) for append (that is, append information to the existing specified log file). If you specify `A` and the log file does not exist, a new log file is created.

link_level
Network link level on which to perform the partitioning (default = 1). The link level reflects the priority level for the link, and is used for network analysis, so that links with higher priority levels can be considered first in network computations.

#### Usage Notes

After you use this procedure to create the partitions, consider using the SDO_NET.GENERATE_PARTITION_BLOBS procedure, to enable better performance for many network analysis operations, especially with large networks.

#### Examples

The following example creates partitions for link level 1 in the `MY_PARTITIONED_NET` network, and creates the MY_PARTITIONED_NET_TAB table. The maximum number of nodes to be placed in any partition is 5000. Information about the operation is added (`open_mode => 'a'`) to the `my_partitioned_net.log` file, located in the location associated with the directory object named `LOG_DIR`.

    EXECUTE SDO_NET.SPATIAL_PARTITION(network => 'MY_PARTITIONED_NET', -
      partition_table_name => 'my_partitioned_net_tab',-
      max_num_nodes => 5000,-
      log_loc => 'LOG_DIR', log_file=> 'my_partitioned_net.log',-
      link_level => 1, open_mode => 'a');

**Parent topic:** SDO_NET Package Subprograms

### 6.100 SDO_NET.TOPO_GEOMETRY_NETWORK

#### Format

    SDO_NET.TOPO_GEOMETRY_NETWORK(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network is a spatial network containing SDO_TOPO_GEOMETRY (topology geometry) objects; returns the string `FALSE` if the network is not a spatial network containing SDO_TOPO_GEOMETRY objects.

#### Parameters

network
Network name.

#### Usage Notes

A network contains SDO_TOPO_GEOMETRY objects if the GEOMETRY_TYPE column in its entry in the USER_SDO_NETWORK_METADATA view contains the value `TOPO_GEOMETRY`. (The USER_SDO_NETWORK_METADATA view is explained in [xxx_SDO_NETWORK_METADATA Views](network-data-model-graph-overview.md).)

#### Examples

The following example checks if the network named `ROADS_NETWORK` is a spatial network containing SDO_TOPO_GEOMETRY objects.

    SELECT SDO_NET.TOPO_GEOMETRY_NETWORK('ROADS_NETWORK') FROM DUAL;

    SDO_NET.TOPO_GEOMETRY_NETWORK('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    FALSE

**Parent topic:** SDO_NET Package Subprograms

### 6.101 SDO_NET.UPDATE_FEATURE

#### Format

    SDO_NET.UPDATE_FEATURE(      
      feature_layer_id   IN NUMBER,      
      feature_id         IN NUMBER,      
      feature_elements   IN SDO_NET_FEAT_ELEM_ARRAY DEFAULT NULL,      
      child_feature_ids  IN SDO_NET_LAYER_FEAT_ARRAY DEFAULT NULL,      
      check_integrity    IN BOOLEAN DEFAULT TRUE);

#### Description

Updates a feature in a feature layer.

#### Parameters

feature_layer_id
ID of the feature layer to which to update the feature.

feature_id
ID of the feature to be updated.

feature_elements
Feature elements of the feature to add to any existing feature elements. If this parameter is null, the existing feature elements are not changed. If this parameter in empty, any existing feature elements are removed. (The SDO_NET_FEAT_ELEM_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

child_feature_ids
Child features of the feature that are to add to any existing child features. If this parameter is null, the existing child features are not changed. If this parameter in empty, any existing parent relationships for this feature with child features are removed. (The SDO_NET_LAYER_FEAT_ARRAY type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

check_integrity
`TRUE` (the default) checks if the input network elements exist; and if any do not exist, an error is generated. `FALSE` does not check if the input network elements exist.

#### Usage Notes

To add a feature to a feature layer, use the SDO_NET.ADD_FEATURE procedure.

A feature layer ID is automatically generated for the feature layer.

#### Examples

The following example updates a specified feature by defining two feature elements and adding them.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      elements SDO_NET_FEAT_ELEM_ARRAY := SDO_NET_FEAT_ELEM_ARRAY();
      link_id NUMBER := 1314;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      elements.extend;
      elements(1) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.7, null);
      elements.extend;
      elements(2) := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.8, null);
      sdo_net.update_feature(feature_layer_id, feature_id, elements, null);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.102 SDO_NET.UPDATE_FEATURE_ELEMENT

#### Format

    SDO_NET.UPDATE_FEATURE_ELEMENT(      
      feature_layer_id IN NUMBER,      
      feature_id       IN NUMBER,      
      sequence_number  IN NUMBER,      
      feature_element  IN SDO_NET_FEAT_ELEM,      
      check_integrity  IN BOOLEAN DEFAULT TRUE);

#### Description

Updates a feature element.

#### Parameters

feature_layer_id
ID of the feature layer for the feature.

feature_id
ID of the feature.

sequence_number
Sequence number of the feature element to be updated.

feature_element
Feature element definition to replace the specified feature element. (The SDO_NET_FEAT_ELEM type is described in [Data Types Used for Feature Modeling](network-data-model-graph-overview.md).)

check_integrity
`TRUE` (the default) checks if the input network elements exist; and if any do not exist, an error is generated. `FALSE` does not check if the input network elements exist.

#### Usage Notes

To add a feature element, use the SDO_NET.ADD_FEATURE_ELEMENT procedure; to add multiple feature elements in a single operation, use the SDO_NET.ADD_FEATURE_ELEMENTS procedure.

#### Examples

The following example updates the feature element at sequence number 2 on link ID 1314 of feature ID 1.

    DECLARE
      feature_layer_id NUMBER;
      feature_id NUMBER := 1;
      element SDO_NET_FEAT_ELEM;
      link_id NUMBER := 1314;
    BEGIN
      feature_layer_id := sdo_net.get_feature_layer_id('GRID', 'POI');
      element := SDO_NET_FEAT_ELEM(SDO_NET.FEAT_ELEM_TYPE_POL, link_id, 0.2, null);
      sdo_net.update_feature_element(feature_layer_id, feature_id, 1, element);
    END;
    /

**Parent topic:** SDO_NET Package Subprograms

### 6.103 SDO_NET.VALIDATE_LINK_SCHEMA

#### Format

    SDO_NET.VALIDATE_LINK_SCHEMA(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the metadata relating to links in a network is valid; returns the string `FALSE` if the metadata relating to links in a network is not valid.

#### Parameters

network
Network name.

#### Usage Notes

This function checks the following for validity: table name, geometry column, and cost column for spatial networks; measure-related information for LRS networks; topology-related information for topology networks; and hierarchy-related information for hierarchical networks.

#### Examples

The following example checks the validity of the metadata related to links in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.VALIDATE_LINK_SCHEMA('ROADS_NETWORK') FROM DUAL;

    SDO_NET.VALIDATE_LINK_SCHEMA('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.104 SDO_NET.VALIDATE_LRS_SCHEMA

#### Format

    SDO_NET.VALIDATE_LRS_SCHEMA(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the metadata relating to LRS information in a network is valid; returns the string `FALSE` if the metadata relating to LRS information in a network is not valid.

#### Parameters

network
Network name.

#### Usage Notes

None.

#### Examples

The following example checks the validity of the metadata related to LRS information in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.VALIDATE_LRS_SCHEMA('ROADS_NETWORK') FROM DUAL;

    SDO_NET.VALIDATE_LRS_SCHEMA('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.105 SDO_NET.VALIDATE_NETWORK

#### Format

    SDO_NET.VALIDATE_NETWORK(      
      network     IN VARCHAR2,      
      check_data  IN VARCHAR2 DEFAULT 'FALSE'       
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the network is valid; returns the string `FALSE` if the network is not valid.

#### Parameters

network
Network name.

check_data
`TRUE` performs additional checks on the referential integrity of network data; `FALSE` (the default) performs basic checks, but not additional checks, on the referential integrity of network data.

#### Usage Notes

This function checks the metadata for the network and any applicable network schema structures (link, node, path, subpath, LRS). It performs basic referential integrity checks on the network data, and it optionally performs additional checks. If any errors are found, the function returns the string `FALSE`.

The checks performed by this function include the following:

- The network exists.

- The node and link tables for the network exist, and they contain the required columns.

- The start and end nodes of each link exist in the node table.

- For an LRS geometry network, the LRS table exists and contains the required columns.

- For a spatial network, columns for the node and path geometries exist and have spatial indexes defined on them.

- If `check_data` is `TRUE`, additional referential integrity checking on the network data is performed. This will take longer, especially if the network is large.

#### Examples

The following example validates the network named `LOG_NET1`.

    SELECT SDO_NET.VALIDATE_NETWORK('LOG_NET1') FROM DUAL;

    SDO_NET.VALIDATE_NETWORK('LOG_NET1')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.106 SDO_NET.VALIDATE_NODE_SCHEMA

#### Format

    SDO_NET.VALIDATE_NODE_SCHEMA(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the metadata relating to nodes in a network is valid; returns the string `FALSE` if the metadata relating to nodes in a network is not valid.

#### Parameters

network
Network name.

#### Usage Notes

This function checks the following for validity: table name, geometry column, and cost column for spatial networks; measure-related information for LRS networks; topology-related information for topology networks; and hierarchy-related information for hierarchical networks.

#### Examples

The following example checks the validity of the metadata related to nodes in the network named `LOG_NET1`.

    SELECT SDO_NET.VALIDATE_NODE_SCHEMA('LOG_NET1') FROM DUAL;

    SDO_NET.VALIDATE_NODE_SCHEMA('LOG_NET1')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.107 SDO_NET.VALIDATE_PARTITION_SCHEMA

#### Format

    SDO_NET.VALIDATE_PARTITION_SCHEMA(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the metadata relating to partitions in a network is valid; returns the string `FALSE` if the metadata relating to partitions in a network is not valid.

#### Parameters

network
Network name.

#### Usage Notes

This function checks the validity of information in the partition table, which is described in [Partition Table](network-data-model-graph-overview.md).

#### Examples

The following example checks the validity of the metadata related to partitions in the network named `SDO_PARTITIONED`.

    SELECT SDO_NET.VALIDATE_PARTITION_SCHEMA('SDO_PARTITIONED') FROM DUAL;

    SDO_NET.VALIDATE_PARTITION_SCHEMA('SDO_PARTITIONED')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.108 SDO_NET.VALIDATE_PATH_SCHEMA

#### Format

    SDO_NET.VALIDATE_PATH_SCHEMA(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the metadata relating to paths in a network is valid; returns the string `FALSE` if the metadata relating to paths in a network is not valid.

#### Parameters

network
Network name.

#### Usage Notes

This function checks the following for validity: table name, geometry column, and cost column for spatial networks; measure-related information for LRS networks; topology-related information for topology networks; and hierarchy-related information for hierarchical networks.

#### Examples

The following example checks the validity of the metadata related to paths in the network named `ROADS_NETWORK`.

    SELECT SDO_NET.VALIDATE_PATH_SCHEMA('ROADS_NETWORK') FROM DUAL;

    SDO_NET.VALIDATE_PATH_SCHEMA('ROADS_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms

### 6.109 SDO_NET.VALIDATE_SUBPATH_SCHEMA

#### Format

    SDO_NET.VALIDATE_SUBPATH_SCHEMA(      
      network  IN VARCHAR2      
    ) RETURN VARCHAR2;

#### Description

Returns the string `TRUE` if the metadata relating to subpaths in a network is valid; returns the string `FALSE` if the metadata relating to subpaths in a network is not valid.

#### Parameters

network
Network name.

#### Usage Notes

This function checks the validity of information in the subpath table, which is described in [Subpath Table](network-data-model-graph-overview.md).

#### Examples

The following example checks the validity of the metadata related to subpaths in the network named `MY_NETWORK`.

    SELECT SDO_NET.VALIDATE_SUBPATH_SCHEMA('MY_NETWORK') FROM DUAL;

    SDO_NET.VALIDATE_SUBPATH_SCHEMA('MY_NETWORK')
    --------------------------------------------------------------------------------
    TRUE

**Parent topic:** SDO_NET Package Subprograms
