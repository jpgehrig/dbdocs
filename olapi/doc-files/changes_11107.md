<table class="oac_no_warn" data-border="0" data-cellpadding="1" data-cellspacing="0" data-summary="Layout table... probably." width="100%">
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Overview </td>
<td style="text-align: right;" data-valign="top"><em><strong>Oracle® OLAP Java API Reference<br />
19c</strong><br />
E96404-01</em></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

# Changes in 11.1.0.7

In Oracle Database 11*g*, Release 1 (11.1.0.7), the Oracle OLAP Java API has added the following classes, fields, methods, and property settings.

## New Classes

The following classes are new additions to the Oracle OLAP Java API. The classes are listed by package.

**`oracle.olapi.metadata`**

   `BatchedException`
   `MetadataRenameNotSupportedException`

**`oracle.olapi.syntax`**

   `AggregateOverClause`
   `AggregateOverMemberClause`
   `AggregationFunctionExpression`

## New Fields, Methods, and Settings

The following classes have new fields, methods, or settings. The classes are listed by package.

**`oracle.olapi.data.source`**

The `MetadataReaderMode` setting of the `DataProvider` class has the new value of `ALL`.

**`oracle.olapi.metadata`**

   `BaseMetadataObject.getName()`

**`oracle.olapi.metadata.deployment`**

   `AWCubeOrganization.REWRITE_WITH_ATTRIBUTES_MV_OPTION`
   `AWCubeOrganization.getName()`

   `MVCreationOptions.getName()`

**`oracle.olapi.metadata.mapping`**

   `DimensionMap.findOrCreateAttributeMap(MdmBaseAttribute attribute, String language)`

**`oracle.olapi.metadata.mdm`**

   `MdmBaseAttribute.getAttributeGroupName()`
   `MdmBaseAttribute.isPopulateLineage()`
   `MdmBaseAttribute.setAttributeGroupName(String group)`
   `MdmBaseAttribute.setPopulateLineage(boolean isPopulateLineage)`

   `MdmCube.getNamespace()`

   `MdmDatabaseSchema.findOrCreateCube(String publicName, String nameSpace)`
   `MdmDatabaseSchema.findOrCreateOrganizationalSchema(String publicName, String nameSpace)`
   `MdmDatabaseSchema.findOrCreateStandardDimension(String publicName, String nameSpace)`
   `MdmDatabaseSchema.findOrCreateTimeDimension(String publicName,String nameSpace)`

   `MdmDimensionality.getETAttrPrefix()`
   `MdmDimensionality.setETAttrPrefix(String value)`

   `MdmMetadataProvider.AWXML_CUBE_NAMESPACE`
   `MdmMetadataProvider.AWXML_DIMENSION_NAMESPACE`
   `MdmMetadataProvider.AWXML_FOLDER_NAMESPACE`
   `MdmMetadataProvider.CWM_CUBE_NAMESPACE`
   `MdmMetadataProvider.CWM_DIMENSION_NAMESPACE`
   `MdmMetadataProvider.CWM_FOLDER_NAMESPACE`
   `MdmMetadataProvider.DEFAULT_NAMESPACE`
   `MdmMetadataProvider.NAMESPACE_DELIMITER`
   `MdmMetadataProvider.getValidNamespaces`

   `MdmObject.addDescription(MdmDescription desc)`
   `MdmObject.addObjectClassification(String classification)`
   `MdmObject.getDescriptions()`
   `MdmObject.getNewName()`
   `MdmObject.getObjectClassifications()`
   `MdmObject.isClassifiedAs(String classification)`
   `MdmObject.removeDescription(MdmDescription desc)`
   `MdmObject.removeObjectClassification(String classification)`

   `MdmPrimaryDimension.getNamespace()`

**`oracle.olapi.syntax`**

   `ClearCommand.CLEAR_AGGREGATES_PARALLEL`
   `ClearCommand.CLEAR_AGGREGATES_SERIAL`
   `ClearCommand.CLEAR_LEAVES_PARALLEL`
   `ClearCommand.CLEAR_LEAVES_SERIAL`
   `ClearCommand.CLEAR_PARALLEL`
   `ClearCommand.CLEAR_SERIAL`
   `ClearCommand.CLEAR_VALUES_PARALLEL`
   `ClearCommand.CLEAR_VALUES_SERIAL`

   `LoadCommand.DEFAULT`
   `LoadCommand.DEFAULT_OPTION`
   `LoadCommand.NO_SYNCH_OPTION`
   `LoadCommand.PARALLEL`
   `LoadCommand.PARALLEL_OPTION`
   `LoadCommand.PRUNE`
   `LoadCommand.PRUNE_OPTION`
   `LoadCommand.SERIAL`
   `LoadCommand.SERIAL_OPTION`
   `LoadCommand.SYNCH_OPTION`
   `LoadCommand.LoadCommand()`
   `LoadCommand.LoadCommand(String option)`
   `LoadCommand.LoadCommand(String option, String cubeMapName)`
   `LoadCommand.getCubeMapName()`
   `LoadCommand.getLoadOption()`

   `SolveCommand.SOLVE_PARALLEL`
   `SolveCommand.SOLVE_SERIAL`

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
