## 7  SDO_NFE Package Subprograms

The MDSYS.SDO_NFE package contains subprograms (functions and procedures) for performing network feature editing.

**Note:**

SDO_NFE subprograms are supported only if Oracle JVM is enabled on your Oracle Autonomous Database Serverless deployments. To enable Oracle JVM, see [Use Oracle Java](http://www.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-2516EE33-B38D-4270-BE52-30A4F9014E8B) in Using Oracle Autonomous Database Serverless for more information.

To use these subprograms, you must understand the conceptual information in [Network Data Model Graph Overview](network-data-model-graph-overview.md), and especially [Feature Modeling Using Network Feature Editing (NFE)](network-data-model-graph-overview.md).

- SDO_NFE.APPLY_RULE
- SDO_NFE.CLASSIFY_LINES_BY_SIDE
- SDO_NFE.CREATE_MODEL_SEQUENCE
- SDO_NFE.CREATE_MODEL_STRUCTURE
- SDO_NFE.CREATE_MODEL_UNDERLYING_NET
- SDO_NFE.CREATE_MODEL_WORKSPACE
- SDO_NFE.DELETE_ALL_FT_LAYERS
- SDO_NFE.DELETE_ALL_WORKSPACES
- SDO_NFE.DELETE_MODEL_STRUCTURE
- SDO_NFE.DELETE_MODEL_WORKSPACE
- SDO_NFE.DROP_MODEL_SEQUENCE
- SDO_NFE.DROP_MODEL_UNDERLYING_NETWORK
- SDO_NFE.GET_CONNECTION_POINT_GEOM
- SDO_NFE.GET_INTERACTION_GROUPS
- SDO_NFE.GET_LINES_MATCH_LP_RULE
- SDO_NFE.GET_LL_CONN_INTERSECTIONS
- SDO_NFE.GET_LP_CONN_INTERSECTIONS
- SDO_NFE.GET_MODEL_SEQUENCE_NAME
- SDO_NFE.GET_MODEL_TABLE_NAME
- SDO_NFE.GET_MODEL_UNDERLYING_NETWORK
- SDO_NFE.GET_NEXT_SEQUENCE_VALUE
- SDO_NFE.GET_POINTS_MATCH_LP_RULE
- SDO_NFE.IMPORT_NETWORK
- SDO_NFE.SET_MODEL_UNDERLYING_NETWORK

**Parent topic:** [Network Data Model](network-data-model.md)

### 7.1 SDO_NFE.APPLY_RULE

#### Format

    SDO_NFE.APPLY_RULE(
         model_id  IN NUMBER,
         rule_type IN VARCHAR2,
         rule_id   IN NUMBER);

#### Description

Applies a connectivity rule over all the features contained in a specified NFE model.

#### Parameters

model_id
ID of the NFE model.

rule_type
Type of connectivity rule to apply: `RULE_TYPE_LINE` or `RULE_TYPE_POINT`.

rule_id
ID of the connectivity rule.

#### Usage Notes

The specified rule must be registered in the specified model. You can register a connectivity rule in the model tables or through the Java API.

#### Examples

The following example applies a line-line rule to any interacting lines in an NFE model that meet the connectivity rule identified by the rule ID 1.

    DECLARE
      model_id  NUMBER := 1;
      rule_type VARCHAR2(1) := sdo_nfe.RULE_TYPE_LINE_LINE;
      rule_id   NUMBER := 1;
    BEGIN
      sdo_nfe.apply_rule( model_id, rule_type, rule_id );
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.2 SDO_NFE.CLASSIFY_LINES_BY_SIDE

#### Format

    SDO_NFE.CLASSIFY_LINES_BY_SIDE(
         model_id    IN NUMBER,
         ll_rule_id  IN NUMBER,
         lines       IN NUMBER,
         lhs_indexes OUT DBMS_SQL,NUMBER_TABLE,
         rhs_indexes OUT DBMS_SQL,NUMBER_TABLE);

#### Description

Given a set of line features that match a connectivity Line-Line rule, this procedure classifies which lines lie on the left hand side of the rule and which ones on the right hand side.

#### Parameters

model_id
ID of the NFE model.

ll_rule_id
Connectivity Line-Line rule identifier.

lines
Set of line features that meet the rule..

lhs_indexes
Associative array where the indexes of the lines lying on the left hand side of the rule will be stored (in the form (index, index)).

rhs_indexes
Associative array where the indexes of the lines lying on the right hand side of the rule will be stored.

#### Usage Notes

The specified rule must be registered in the specified model. You can register a connectivity rule in the model tables or through the Java API.

#### Examples

The following example first gets all the interacting groups that meet the rule with ID 1 and then classifies the lines by side. Left hand side lines are output in lhs_indexes while rhs_indexes contain the rule’s right hand side lines.

    DECLARE
      model_id    NUMBER := 1;
      ll_rule_id  NUMBER := 1;
      lines       SDO_INTERACT_LINE_FEAT_ARRAY;
      lhs_indexes dbms_sql.NUMBER_TABLE;
      rhs_indexes dbms_sql.NUMBER_TABLE;
      inter_grps  SDO_INTERACTION_ARRAY;
    BEGIN

      -- Get the groups of interacting features that meet the L-L Rule
      inter_grps := sdo_nfe.get_interaction_groups( model_id, sdo_nfe.RULE_TYPE_LINE_LINE, ll_rule_id );

      FOR i IN 1..inter_grps.count loop
        lines := inter_grps(i).lines;

        -- For each group, classify the lines by rule side.
        sdo_nfe.classify_lines_by_side( model_id, ll_rule_id, lines, lhs_indexes, rhs_indexes );
      END loop;

    END;

**Parent topic:** SDO_NFE Package Subprograms

### 7.3 SDO_NFE.CREATE_MODEL_SEQUENCE

#### Format

    SDO_NFE.CREATE_MODEL_SEQUENCE(
         model_id      IN NUMBER,
         owner_name    IN VARCHAR2,
         aequence_name IN VARCHAR2);

#### Description

Creates and registers a sequence for a model.

#### Parameters

model_id
ID of the NFE model.

owner_name
Sequence's related table.

aequence_name
Name of the sequence to be created.

#### Usage Notes

All the sequences for the base tables are created by the SDO_NFE.CREATE_MODEL_STRUCTURE function, but you may need to create other sequences (such as for features).

The NFE model and the sequence’s related table must exist.

#### Examples

The following example creates a sequence for the NFE model identified by the ID 1 and a table named FEATURES.

    SDO_NFE.CREATE_MODEL_SEQUENCE(’1’,’features’,’features_seq’)

**Parent topic:** SDO_NFE Package Subprograms

### 7.4 SDO_NFE.CREATE_MODEL_STRUCTURE

#### Format

    SDO_NFE.CREATE_MODEL_STRUCTURE(
         model_name    IN VARCHAR2,
         edition_mode  IN NUMBER,
         versionable   IN VARCHAR2
    ) RETURN NUMBER;

#### Description

Creates the tables and metadata for an NFE model.

#### Parameters

model_name
Name to be given to the lNFE model.

edition_mode
Edition mode. Must be `SDO_NFE.FROM_SCRATCH` or `SDO_NFE.OVER_EXIST_NETWORK`.

versionable
The string value `Y` if the model will be versionable, otherwise `N`.

#### Usage Notes

This function returns the new model's ID value.

#### Examples

The following example creates a versionable model named `MODEL01` with the `SDO_NFE.FROM_SCRATCH` edition mode.

    DECLARE
      model_id      NUMBER;
      model_name    VARCHAR2(50) := 'MODEL01';
      edition_mode  NUMBER       := SDO_NFE.FROM_SCRATCH;
      versionable   VARCHAR2(1)  := 'Y';
    BEGIN
      model_id := SDO_NFE.create_model_structure( model_name, edition_mode, versionable );
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.5 SDO_NFE.CREATE_MODEL_UNDERLYING_NET

#### Format

    SDO_NFE.CREATE_MODEL_UNDERLYING_NET(
         model_id             IN NUMBER,
         network_name         IN VARCHAR2,
         num_hierarchy_levels IN NUMBER,
         is_directed          IN BOOLDEAN,
         node_with_costs      IN BOOLEAN);

#### Description

Creates a spatial network and associates it to the specified NFE Model. It also creates sequences for its nodes, links, and paths, and registers them in the model's metadata.

#### Parameters

model_id
ID of the NFE model.

network_name
Name of the network to be created.

num_hierarchy_levels
Number of hierarchical levels for the network.

is_directed
`TRUE` if the network is directed.

node_with_costs
`TRUE` if the network’s nodes contain cost values.

#### Usage Notes

An NFE model with the specified ID must exist. The geometry metadata must be registered for the newly created network’s nodes and links tables.

#### Examples

The following example creates an underlying network for an NFE model and registers the geometry metadata for the network’s links and nodes tables.

    DECLARE
      model_id           NUMBER := 1;
      network_name          VARCHAR2(50) := 'MODEL01';
      num_hierarchy_levels  NUMBER := 1;
      is_directed           VARCHAR2(10) := 'TRUE';
      node_with_costs       VARCHAR2(10) := 'TRUE';
    BEGIN
    -- create underlying network
      SDO_NFE.create_model_underlying_net( model_id, network_name, num_hierarchy_levels, is_directed, node_with_costs );
    -- register links and nodes tables geom metadata
      SDO_NET.insert_geom_metadata(network_name, SDO_DIM_ARRAY(SDO_DIM_ELEMENT('LONGITUDE', -180, 180, 0.5), SDO_DIM_ELEMENT('LATITUDE', -90, 90, 0.5)), 8307);
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.6 SDO_NFE.CREATE_MODEL_WORKSPACE

#### Format

    SDO_NFE.CREATE_MODEL_WORKSPACE(
         model_id              IN NUMBER,
         parent_workspace_name IN VARCHAR2,
         workspace_name        IN VARCHAR2,
         is_mbr    IN VARCHAR2,
         is_locked IN VARCHAR2,
         lower_x   IN NUMBER,
         lower_y   IN NUMBER,
         upper_x   IN NUMBER,
         upper_y   IN NUMBER);

#### Description

Creates a new workspace and relates it to an NFE model.

#### Parameters

model_id
ID of the NFE model.

parent_workspace_name
Name of the parent workspace.

workspace_name
Name of the workspace.

is_mbr
The string `TRUE` if the workspace is created for a minimum bounding rectangle (MBR) rectangular area of the model.

is_locked
The string `TRUE` if the workspace is locked.

lower_x
The lower x ordinate of the workspace MBR.

lower_y
The lower y ordinate of the workspace MBR.

upper_x
The upper x ordinate of the workspace MBR.

upper_y
The upper y ordinate of the workspace MBR.

#### Usage Notes

The NFE model must have been created with the `versionable` option enabled.

#### Examples

The following example creates a workspace for an NFE model.

    DECLARE
      model_id        NUMBER := 1;
      parent_ws_name  VARCHAR2(30) := 'LIVE';
      workspace_name  VARCHAR2(30) := 'PROJECT_V1';
      is_mbr          VARCHAR2(1) := 'Y';
      is_locked       VARCHAR2(1) := 'N';
      lower_x NUMBER := -15.575;
      lower_y       NUMBER :=  15.575;
      upper_x NUMBER := -12.825;
      upper_y NUMBER :=  28.975;
    BEGIN
      SDO_NFE.create_model_workspace(model_id, parent_ws_name, workspace_name, is_mbr, is_locked, lower_x, lower_y, upper_x, upper_y);
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.7 SDO_NFE.DELETE_ALL_FT_LAYERS

#### Format

    SDO_NFE.DELETE_ALL_FT_LAYERS(
         model_id  IN NUMBER);

#### Description

Drops all content in a specified NFE model.

#### Parameters

model_id
ID of the NFE model.

#### Usage Notes

This procedure is mainly used before deleting a model and its structure from the database.

#### Examples

The following example deletes all content from the model with the ID value 1.

    EXECUTE SDO_NFE.DELETE_ALL_FT_LAYERS(1);

**Parent topic:** SDO_NFE Package Subprograms

### 7.8 SDO_NFE.DELETE_ALL_WORKSPACES

#### Format

    SDO_NFE.DELETE_ALL_WORKSPACES(
         model_id  IN NUMBER);

#### Description

Dropa all the workspaces related to the specified NFE model, along with their relationship to the model.

#### Parameters

model_id
ID of the NFE model.

#### Usage Notes

This procedure is mainly used before deleting a model and its structure from the database.

#### Examples

The following example deletes all workspaces related to the model with ID value 1.

    EXECUTE SDO_NFE.DELETE_ALL_WORKSPACES(1);

**Parent topic:** SDO_NFE Package Subprograms

### 7.9 SDO_NFE.DELETE_MODEL_STRUCTURE

#### Format

    SDO_NFE.DELETE_MODEL_STRUCTURE(
         model_id  IN NUMBER);

#### Description

Drops all tables in a specified NFE model, and deletes the metadata records for the model.

#### Parameters

model_id
ID of the NFE model.

#### Usage Notes

Before using this procedure, you may need to do the following:

- Delete model’s workspaces by executing the SDO_NFE.DELETE_ALL_WORKSPACES procedure.

- Delete the model’s feature layers by executing the SDO_NFE.DELETE_ALL_FT_LAYERS procedure.

- If f the model’s edition mode is `SDO_NFE.FROM_SCRATCH`, delete the underlying network.

#### Examples

The following example the structure of the model with the ID value 1.

    EXECUTE SDO_NFE.DELETE_MODEL_STRUCTURE(1);

**Parent topic:** SDO_NFE Package Subprograms

### 7.10 SDO_NFE.DELETE_MODEL_WORKSPACE

#### Format

    SDO_NFE.DELETE_MODEL_WORKSPACE(
         model_id       IN NUMBER,
         workspace_name IN VARCHAR2);

#### Description

Drops a workspace along with its relationship with the specified NFE model.

#### Parameters

model_id
ID of the NFE model.

workspace_name
Name of the workspace.

#### Usage Notes

`workspace_name` must be the name of an existing workspace under the specified NFE model. All branches of the workspace are removed.

The relationship with the model is deleted from xxx_SDO_NFE_MODEL_WORKSPACE views.

#### Examples

The following example deletes the workspace named `PROJECT_V4` from the NFE model with the ID 1

    EXECUTE SDO_NFE.DELETE_MODEL_WORKSPACE(1, 'PROJECT_V4');

**Parent topic:** SDO_NFE Package Subprograms

### 7.11 SDO_NFE.DROP_MODEL_SEQUENCE

#### Format

    SDO_NFE.DROP_MODEL_SEQUENCE(
         model_id  IN NUMBER,
         seq_name  IN VARCHAR2);

#### Description

Drops a sequence along with its relationship with the specified NFE model.

#### Parameters

model_id
ID of the NFE model.

seq_name
Name of the sequence.

#### Usage Notes

The relationship of the sequence with the model is deleted from the table registered in SEQUENCE_REG_TAB from the xxx_SDO_NFE_MODEL_METADATA views.

#### Examples

The following example deletes the sequence named `PIPES_FTLAY_ID_SEQ` from the NFE model with the ID 1.

    EXECUTE SDO_NFE.DROP_MODEL_SEQUENCE(1, 'PIPES_FTLAY_ID_SEQ');

**Parent topic:** SDO_NFE Package Subprograms

### 7.12 SDO_NFE.DROP_MODEL_UNDERLYING_NETWORK

#### Format

    SDO_NFE.DROP_MODEL_UNDERLYING_NETWORK
         network_name  IN VARCHAR2);

#### Description

Drops a network and removes its relationship with any NFE model.

#### Parameters

network_name
Name of the network.

#### Usage Notes

The network must be bound to at least one NFE model..

#### Examples

The following example drops the network named `PIPES` and removes its relationship with any existing NFE model.

    EXECUTE SDO_NFE.DROP_MODEL_UNDERLYING_NETWORK('PIPES');

**Parent topic:** SDO_NFE Package Subprograms

### 7.13 SDO_NFE.GET_CONNECTION_POINT_GEOM

#### Format

    SDO_NFE.GET_CONNECTION_POINT_GEOM(
         conn_intersection  IN SDO_INTERACTION
         ) RETURN SDO_GEOMETRY;

#### Description

Given a group of interacting features (lines and/or points), calculates and returns the geometry of the point that must connect them.

#### Parameters

conn_intersection
Interaction group of features. Set of line and/or point features that interact at a common spatial point. (The SDO_INTERACTION type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

#### Usage Notes

This function is mainly used over a validated group of features that must be connected because of the requirement of a connectivity rule (see [NFE Rules](network-data-model-graph-overview.md)). To get this group of features, use SDO_NFE.GET_LP_CONN_INTERSECTIONS for Line-Point Rules or SDO_NFE.GET_LL_CONN_INTERSECTIONS for Line-Line Rules.

#### Examples

The following example gets the connection point geometry for each interacting group that meets the given line-point rule.

    DECLARE
      model_id        NUMBER := 1;
      lp_rule_id      NUMBER := 1;
      inter_grps          SDO_INTERACTION_ARRAY;
      conn_point_geom     SDO_GEOMETRY;
    BEGIN
      -- Get the groups of interacting features that meet the L-P Rule in the model
     inter_grps := sdo_nfe.get_interaction_groups( model_id, sdo_nfe.RULE_TYPE_LINE_POINT, lp_rule_id );
      -- Iterate through the interacting groups
     FOR i IN 1..inter_grps.count loop
      -- Get the connection point geometry for each interacting group
       conn_point_geom := sdo_nfe.get_connection_point_geom( inter_groups(i));
     END loop;
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.14 SDO_NFE.GET_INTERACTION_GROUPS

#### Format

    SDO_NFE.GET_INTERACTION_GROUPS(
         model_id   IN SDO_NUMBER,
         rule_type  IN VARCHAR2,
         rule_id    IN NUMBER
         ) RETURN SDO_INTERACTION_ARRAY;

#### Description

Returns an array of groups of all features that are interacting at spatial points where the specified connectivity rule is being met.

#### Parameters

model_id
NFE model identifier.

rule_type
Connectivity rule type. Possible values: `SDO_NFE.RULE_TYPE_LINE_LINE` or `SDO_NFE.RULE_TYPE_LINE_POINT`.

rule_id
Rule identifier. Must be a value from the LINE_LINE_RULE or LINE_POINT_RULE table.

#### Usage Notes

This function returns an object of type SDO_INTERACTION_ARRAY, which is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).

Each group of the interacting features returned by this function is composed of all the line and point features that interact at a specific spatial point where the specified rule is being met.

By returning the whole group of all interacting features at specific points, this function can help you if you want to create a customized way of connecting features depending on which other features (meeting the rule or not) are taking part in a specified interaction point. (See the discussion of rule decision handlers under [NFE Rules](network-data-model-graph-overview.md).)

#### Examples

The following example gets the interacting groups which met the given line-point rule.

    DECLARE
      model_id        NUMBER := 1;
      lp_rule_id      NUMBER := 1;
      inter_grps          SDO_INTERACTION_ARRAY;
    BEGIN
     inter_grps := sdo_nfe.get_interaction_groups( model_id,
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.15 SDO_NFE.GET_LINES_MATCH_LP_RULE

#### Format

    SDO_NFE.GET_LINES_MATCH_LP_RULE(
         model_id    IN SDO_NUMBER,
         lp_rule_id  IN NUMBER,
         lines       IN SDO_INTERACT_LINE_FEAT_ARRAY,
         ) RETURN DBMS_SQL.NUMBER_TABLE;

#### Description

Given an set of line features, calculates the group of them that match a connectivity line-point rule. Returns a DBMS_SQL.NUMBER_TABLE object with the indexes of the lines in the input array that match the line-point rule.

#### Parameters

model_id
NFE model identifier.

lp_rule_id
Connectivity line-point rule identifier. Must exist in the LINE_POINT_RULE table.

lines
Array of line features where the search will take place. (The SDO_INTERACT_LINE_FEAT_ARRAY type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

#### Usage Notes

This function is mainly used after the SDO_NFE.GET_INTERACTION_GROUPS function, which returned a group of mixed line features where some line features matched a specific connectivity rule and some did not.

#### Examples

The following example finds the lines that meet a connectivity line-point rule from interacting groups.

    DECLARE
      model_id    NUMBER := 1;
      lp_rule_id  NUMBER := 1;
      lines       SDO_INTERACT_LINE_FEAT_ARRAY;
      match_lines dbms_sql.NUMBER_TABLE;
      inter_grps  SDO_INTERACTION_ARRAY;
    BEGIN
      -- find interaction groups
      inter_grps := sdo_nfe.get_interaction_groups( model_id, sdo_nfe.RULE_TYPE_LINE_LINE, 1 );

      FOR i IN 1..inter_grps.count loop
        lines := inter_grps(i).lines;
        match_lines := sdo_nfe.get_lines_match_lp_rule( model_id, lp_rule_id, lines );
      END loop;

    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.16 SDO_NFE.GET_LL_CONN_INTERSECTIONS

#### Format

    SDO_NFE.GET_LL_CONN_INTERSECTIONS(
         model_id               IN SDO_NUMBER,
         ll_rule_id             IN NUMBER,
         interaction_grp        IN OUT SDO_INTERACTION,
         rule_lhs_lines_indexes IN DBMS_SQL.NUMBER_TABLE,
         rule_rhs_lines_indexes IN DBMS_SQL.NUMBER_TABLE,
         rule_points_indexes    IN DBMS_SQL.NUMBER_TABLE,
         ) RETURN SDO_INTERACTION_ARRAY;

#### Description

Given a group of interacting features (lines and points) this function calculates subgroups of these features that can be connected according to the connectivity line-line rule specified, and returns the set of connectable features groups.

#### Parameters

model_id
NFE model identifier.

ll_rule_id
Connectivity line-line rule identifier.. Must exist in the LINE_LINE_RULE table.

interaction_grp
Group of interacting features. (The SDO_INTERACTION type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

rule_lhs_lines_indexes
Among the line features in the interacting group, indexes of the lines that match the left hand side of the line-line rule.

rule_rhs_lines_indexes
Among the line features in the interacting group, indexes of the lines that match the right hand side of the line-line rule.

rule_points_indexes
Among the point features in the interacting group, indexes of the points that match the point feature specification in the line-line rule. These points are the ones to be considered in the conformation of connectable groups.

#### Usage Notes

This function returns an SDO_INTERACTION_ARRAY object. (The SDO_INTERACTION_ARRAY type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

The indexes of LHS and RHS lines can be obtained with the SDO_NFE.CLASSIFY_LINES_BY_SIDE procedure. The indexes of the points can be obtained with the SDO_NFE.GET_POINTS_MATCH_LP_RULE function.

This function is registered by default in the [Rule Decision Handlers Table](network-data-model-graph-overview.md) when a line-line rule is created in a model (using the Java API). However, this function can be replaced by any other user function that calculates the group of connectable features in a customized way. See the information about Rule Decision Handlers under [NFE Rules](network-data-model-graph-overview.md) for information about customizing connections (rule decision handlers).

#### Examples

The following example gets the set of connectable feature groups for each interacting group that match a given line-line rule.

    DECLARE
      model_id    NUMBER := 1;
      ll_rule_id  NUMBER := 1;
      rule_lhs_lines_indexes  dbms_sql.NUMBER_TABLE;
      rule_rhs_lines_indexes  dbms_sql.NUMBER_TABLE;
      rule_points_indexes     dbms_sql.NUMBER_TABLE;
      conn_interacs           SDO_INTERACTION_ARRAY;
      inter_grps              SDO_INTERACTION_ARRAY;
    BEGIN
    -- Get the groups of interacting features that meet the L-L Rule in the model
      inter_grps := sdo_nfe.get_interaction_groups( model_id, sdo_nfe.RULE_TYPE_LINE_LINE, ll_rule_id );
      FOR i IN 1..inter_grps.count loop
        -- Classify the line features by side in the L-L rule (LHS, RHS).
        sdo_nfe.classify_lines_by_side( model_id, ll_rule_id, inter_grps(i).lines, rule_lhs_lines_indexes, rule_rhs_lines_indexes );
        -- Get the specific point features that match the L-L rule.
        rule_points_indexes := sdo_nfe.get_points_match_lp_rule( model_id,  1, inter_grps(i).points );
        -- Get the group of features that can be connected according the L-L rule.
        conn_interacs := sdo_nfe.get_ll_conn_intersections( model_id, ll_rule_id, inter_grps(i), rule_lhs_lines_indexes, rule_rhs_lines_indexes, rule_points_indexes);
      END loop;
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.17 SDO_NFE.GET_LP_CONN_INTERSECTIONS

#### Format

    SDO_NFE.GET_LP_CONN_INTERSECTIONS(
         model_id               IN SDO_NUMBER,
         lp_rule_id             IN NUMBER,
         interaction_grp        IN OUT SDO_INTERACTION,
         rule_lhs_lines_indexes IN DBMS_SQL.NUMBER_TABLE,
         rule_rhs_lines_indexes IN DBMS_SQL.NUMBER_TABLE,
         rule_points_indexes    IN DBMS_SQL.NUMBER_TABLE,
         ) RETURN SDO_INTERACTION_ARRAY;

#### Description

Given a group of interacting features (lines and points) this function calculates subgroups of these features that can be connected according to the connectivity line-point rule specified, and returns the set of connectable features groups.

#### Parameters

model_id
NFE model identifier.

lp_rule_id
Connectivity line-point rule identifier.. Must exist in the LINE_POINT_RULE table.

interaction_grp
Group of interacting features. (The SDO_INTERACTION type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

rule_lhs_lines_indexes
Among the line features in the interacting group, indexes of the lines that match the left hand side of the line-point rule.

rule_rhs_lines_indexes
Among the line features in the interacting group, indexes of the lines that match the right hand side of the line-point rule.

rule_points_indexes
Among the point features in the interacting group, indexes of the points that match the point feature specification in the line-point rule. These points are the ones to be considered in the conformation of connectable groups.

#### Usage Notes

This function returns an SDO_INTERACTION_ARRAY object. (The SDO_INTERACTION_ARRAY type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

The indexes of LHS and RHS lines can be obtained with the SDO_NFE.CLASSIFY_LINES_BY_SIDE procedure. The indexes of the points can be obtained with the SDO_NFE.GET_POINTS_MATCH_LP_RULE function.

This function is registered by default in the [Rule Decision Handlers Table](network-data-model-graph-overview.md) when a line-point rule is created in a model (using the Java API). However, this function can be replaced by any other user function that calculates the group of connectable features in a customized way. See the information about Rule Decision Handlers under [NFE Rules](network-data-model-graph-overview.md) for information about customizing connections (rule decision handlers).

#### Examples

The following example gets the group of feature that can be connected according to a given line-point rule for each interacting group.

    DECLARE
      model_id        NUMBER := 1;
      lp_rule_id      NUMBER := 1;
      rule_lines_indexes  dbms_sql.NUMBER_TABLE;
      rule_points_indexes dbms_sql.NUMBER_TABLE;
      conn_interacs       SDO_INTERACTION_ARRAY;
      inter_grps          SDO_INTERACTION_ARRAY;
    BEGIN
      -- Get the groups of interacting features that meet the L-P Rule in the model
      inter_grps := sdo_nfe.get_interaction_groups( model_id, sdo_nfe.RULE_TYPE_LINE_POINT, lp_rule_id );

      -- For each group:
      FOR i IN 1..inter_grps.count loop
        -- Get the specific line features that match the L-P rule.
        rule_lines_indexes  := sdo_nfe.get_lines_match_lp_rule( model_id, lp_rule_id, inter_grps(i).lines );

        -- Get the specific point features that match the L-P rule.
        rule_points_indexes := sdo_nfe.get_points_match_lp_rule( model_id,  lp_rule_id, inter_grps(i).points );

        -- Get the group of features that can be connected according the L-P rule.
        conn_interacs := sdo_nfe.get_lp_conn_intersections( model_id, lp_rule_id, inter_grps(i), rule_lines_indexes, rule_points_indexes );
      END loop;
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.18 SDO_NFE.GET_MODEL_SEQUENCE_NAME

#### Format

    SDO_NFE.GET_MODEL_SEQUENCE_NAME(
         model_id  IN SDO_NUMBER,
         tab_name  IN VARCHAR2
         ) RETURN VARCHAR2;

#### Description

Returns the sequence name for the specified model’s table.

#### Parameters

model_id
NFE model identifier.

tab_name
Table name for the model.

#### Usage Notes

The table name must exist in the TABLE_REG_TAB table, and the name of its sequence must exist in the SEQUENCE_REG_TAB table. When a new model is created using SDO_NFE.CREATE_MODEL_STRUCTURE, all the model’s tables and sequences are automatically registered in the appropriate views and tables. When SDO_NFE.CREATE_MODEL_SEQUENCEis executed, a sequence for the model’s table is registered.

#### Examples

The following example gets the sequence name defined for the table that holds the feature classes of the NFE model whose ID is 1.

    SELECT SDO_NFE.GET_MODEL_SEQUENCE_NAME(1, sdo_nfe.get_model_table_name(1, SDO_NFE.FT_CLASS));

**Parent topic:** SDO_NFE Package Subprograms

### 7.19 SDO_NFE.GET_MODEL_TABLE_NAME

#### Format

    SDO_NFE.GET_MODEL_TABLE_NAME(
         model_id    IN SDO_NUMBER,
         table_type  IN VARCHAR2
         ) RETURN VARCHAR2;

#### Description

Returns the name of the table of a specified type for an NFE model.

#### Parameters

model_id
NFE model identifier.

table_type
Type of table whose name is to be returned. For example, the value for the feature classes table is `SDO_NFE.FT_CLASS`.

#### Usage Notes

The table name must exist in the TABLE_REG_TAB table, and the name of its sequence must exist in the SEQUENCE_REG_TAB table. When a new model is created using SDO_NFE.CREATE_MODEL_STRUCTURE, the names of all of the model’s tables and sequences are automatically registered in the appropriate views and tables.

#### Examples

The following example gets the name of the table that holds the feature classes in the NFE model with the ID 1.

    SELECT SDO_NFE.GET_MODEL_TABLE_NAME(1, SDO_NFE.FT_CLASS);

**Parent topic:** SDO_NFE Package Subprograms

### 7.20 SDO_NFE.GET_MODEL_UNDERLYING_NETWORK

#### Format

    SDO_NFE.GET_MODEL_UNDERLYING_NETWORK(
         model_id    IN SDO_NUMBER
         ) RETURN VARCHAR2;

#### Description

Returns the name of the network that is associated with an NFE model.

#### Parameters

model_id
NFE model identifier.

#### Usage Notes

A network is associated with an NFE model during the creation process, either when using the SDO_NFE.CREATE_MODEL_UNDERLYING_NET for models in the SDO_NFE.FROM_SCRATCH mode, or using SDO_NFE.SET_MODEL_UNDERLYING_NETWORK for models in the SDO_NFE.OVER_EXIST_NETWORK mode.

#### Examples

The following example gets the underlying network associated with an existing NFE model.

    SELECT SDO_NFE.get_model_underlying_network(1) FROM DUAL;

**Parent topic:** SDO_NFE Package Subprograms

### 7.21 SDO_NFE.GET_NEXT_SEQUENCE_VALUE

#### Format

    SDO_NFE.GET_NEXT_SEQUENCE_VALUE(
         sequence_name        IN VARCHAR2,
         seq_value_increment  IN NUMBER
         ) RETURN NUMBER;

#### Description

Returns the value resulting from adding the value of the second parameter to the current value of the specified sequence.

#### Parameters

sequence_name
Name of the sequence.

seq_value_increment
Integer value to be added to the current value of `sequence_name`. (If the specified value is negative, it is subtracted from the current value.)

#### Usage Notes

This function does not change the INCREMENT BY value of the specified sequence or the current value of that sequence.

This function can be used to manage a block of consecutive sequence numbers.

#### Examples

The following example returns the value that would result from adding 10 to the current value of a sequence named MY_SEQ.

    SELECT SDO_NFE.GET_NEXT_SEQUENCE_VALUE('my_seq', 10) FROM DUAL;

If the current value of MY_SEQ is 100, this example returns the value 110 (100 + 10).

**Parent topic:** SDO_NFE Package Subprograms

### 7.22 SDO_NFE.GET_POINTS_MATCH_LP_RULE

#### Format

    SDO_NFE.GET_POINTS_MATCH_LP_RULE(
         model_id    IN SDO_NUMBER,
         lp_rule_id  IN NUMBER,
         points      IN SDO_INTERACT_POINT_FEAT_ARRAY,
         ) RETURN DBMS_SQL.NUMBER_TABLE;

#### Description

Given an set of point features, this function calculates the group of them that match a connectivity line-point rule. Returns a DBMS_SQL.NUMBER_TABLE object with the indexes of the points in the input array that match the line-point rule.

#### Parameters

model_id
NFE model identifier.

lp_rule_id
Connectivity line-point rule identifier. Must exist in the LINE_POINT_RULE table.

points
Array of point features where the search will take place. (The SDO_INTERACT_POINT_FEAT_ARRAY type is described in [Data Types Used for NFE Connectivity Rules](network-data-model-graph-overview.md).)

#### Usage Notes

This function is mainly used after the SDO_NFE.GET_INTERACTION_GROUPS function, which returned a group of mixed line features where some line features matched a specific connectivity rule and some did not.

#### Examples

The following example gets the specific point features that match a line-point rule.

    DECLARE
      model_id        NUMBER := 1;
      lp_rule_id      NUMBER := 1;
      rule_points_indexes dbms_sql.NUMBER_TABLE;
      inter_grps          SDO_INTERACTION_ARRAY;
    BEGIN
      -- Get the groups of interacting features that meet the L-P Rule in the model
      inter_grps := sdo_nfe.get_interaction_groups( model_id, sdo_nfe.RULE_TYPE_LINE_POINT, lp_rule_id );

      -- For each group:
      FOR i IN 1..inter_grps.count loop
        -- Get the specific point features that match the L-P rule.
        rule_points_indexes := sdo_nfe.get_points_match_lp_rule( model_id,  lp_rule_id, inter_grps(i).points );
      END loop;
    END;
    /

**Parent topic:** SDO_NFE Package Subprograms

### 7.23 SDO_NFE.IMPORT_NETWORK

#### Format

    SDO_NFE.IMPORT_NETWORK(
         model_id          IN NUMBER,
         model_id          IN NUMBER,
         network_from      IN VARCHAR2,
         line_ft_layer_id  IN NUMBER,
         line_ft_class_id  IN NUMBER,
         point_ft_layer_id IN NUMBER,
         point_ft_class_id IN NUMBER);

#### Description

Copies the network elements from an existing network to the underlying network of an NFE model (created in the SDO_NFE.FROM_SCRATCH mode), translating every link in line features from the line feature class (line_ft_class_id), and every node in point features from the point feature class (point_ft_class_id)..

#### Parameters

model_id
NFE model identifier.

network_from
Name of the network to be imported.

line_ft_layer_id
Feature layer ID for the newly created line features (created from the link elements).

line_ft_class_id
Feature class ID for the newly created line features.

point_ft_layer_id
Feature layer ID for the newly created point features (created from the node elements).

point_ft_class_id
Feature class ID for the newly created point features.

#### Usage Notes

The feature classes for the line and point features must already exist in the NFE model.

#### Examples

The following example imports a network named `NET01` to a model identified by the ID 1. Lines and point features will be created for every link and node using the feature layers 10 and 11 and the feature classes 5 and 6.

    EXECUTE SDO_NFE.import_network(1, ‘NET01’, 10, 5, 11, 6);

**Parent topic:** SDO_NFE Package Subprograms

### 7.24 SDO_NFE.SET_MODEL_UNDERLYING_NETWORK

#### Format

    SDO_NFE.SET_MODEL_UNDERLYING_NETWORK(
         model_id     IN SDO_NUMBER
         network_name IN VARCHAR2);

#### Description

Associates a network as the underlying network of an NFE model. (The model must have been created in the SDO_NFE.OVER_EXIST_NETWORK mode.)

#### Parameters

model_id
NFE model identifier.

network_name
Name of the network to be associated with the model.

#### Usage Notes

See also the SDO_NFE.GET_MODEL_UNDERLYING_NETWORK function.

#### Examples

The following example ....

    EXECUTE ... ;

**Parent topic:** SDO_NFE Package Subprograms
