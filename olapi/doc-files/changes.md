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

**Changes in This Release for the OLAP Java API**

This page lists the changes in the Oracle OLAP Java API.

# Changes in Oracle Database 12*c* Release 1 (12.1)

The following are changes in the Oracle OLAP Java API for Oracle Database 12*c* Release 1 (12.1). For changes in previous releases, see [Changes in Previous Releases](changes_prev_rel.md).

## New Features

The following features are new in this release:

- Varying the aggregation method of a measure depending on dimension members or attribute values.

  In implementing this feature, the following classes in the `oracle.olapi.syntax` package have new methods:

  - `AggregationCase`
    - Constructors that take an `aggregationSwitchValue` parameter that specifies an attribute value or a dimension member
    - `getAggregationSwitchValue()`
    - `getMeasureID()`
  - `AggregationCommand`
    - Constructors that take an `aggregationSwitch` parameter that specifies an attribute value or a dimension member
    - `getAggregationSwitch()`
    - `getAggregationSwitchID()`

- Specifying no aggregation for a dimension in an `AggregationCommand`.

  If you specify `NO_AGGREGATE` as the function of an `AggregationCommand`, then Oracle OLAP does not aggregate the values of the measure for the specified dimension.

- Preventing changes to the parentage of a previously loaded dimension member during the load of a dimension.

  In implementing this feature, the `LoadCommand` class has the new static fields `RETAIN` and `RETAIN_OPTION`.

- Specifying the OLAP DML \$LOOP_TYPE system property for an `MdmDerivedMeasure`.

  The \$LOOP_TYPE property determines how Oracle OLAP loops over composites for an `MdmDerivedMeasure` that has an `Expression` that references measures from more than one cube. The `MdmDerivedMeasure` has new static constants and methods that you can use to get or set the type of looping.

- A base class for objects that you can export to XML.

  The `PublicMetadataObject` class is the base class for OLAP Java API objects that you can export to XML. You export objects to XML by using methods of an `MdmMetadataProvider`.

## Desupported Features

Some features previously described in this document are desupported in Oracle Database 12*c* Release 1 (12.1). See *Oracle Database Upgrade Guide* for a list of desupported features.

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
