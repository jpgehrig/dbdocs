You can use Oracle SQL function `json_mergepatch` to update specific portions of a JSON document. You pass it a JSON Merge Patch document, which specifies the changes to make to a specified JSON document. JSON Merge Patch is an IETF standard.

You can use `json_mergepatch` in an `UPDATE` statement, to update the documents in a JSON column. Example 12-3 illustrates this.

You can use `json_mergepatch` in a `SELECT` list, to modify the selected documents. The modified documents can be returned or processed further. Example 12-4 illustrates this.

JSON Merge Patch is suitable for updating JSON documents that primarily use objects for their structure and do not make use of explicit `null` values. You cannot use it to add, remove, or change array elements (except by explicitly replacing the whole array). And you cannot use it to set the value of a field to `null`.

JSON Merge Patch acts a bit like a UNIX `patch` utility: you give it (1) a source document to patch and (2) a patch document that specifies the changes to make, and it returns a copy of the source document updated (patched). The patch document specifies the differences between the source and the result documents. For UNIX `patch` the differences are in the form of UNIX `diff` utility output. For JSON Merge Patch both source and patch are JSON documents.

You can think of JSON Merge Patch as merging the contents of the source and the patch. When merging two objects, one from source and one from patch, a member with a field that is in one object but not in the other is kept in the result. An exception is that a patch member with field value is `null` is ignored when the source object has no such field.

When merging object members that have the same field:

- If the patch field value is `null` then the field is dropped from the source — it is not included in the result.

- Otherwise, the field is kept in the result, but its value is the result of merging the source field value with the patch field value. That is, the merging operation in this case is recursive — it dives down into fields whose values are themselves objects.

A little more precisely, JSON Merge Patch acts as follows:

- If the patch is not a JSON object then replace the source by the patch.

- Otherwise (the patch is an object), do the following:

  1.  If the source is not an object then act as if it were the empty object (`{}`).

  2.  Iterate over the (`p-field``:``p–value`) members of the patch object.

      - If the `p-value` of the patch member is `null` then remove the corresponding member from the source.

      - Otherwise, recurse: Replace the value of the corresponding source field with the result of merge-patching that value (as the next source) with the `p-value` (as the next patch).

If a patch field value of `null` did not have a special meaning (remove the corresponding source member with that field) then you could use it as a field value to set the corresponding source field value to `null`. The special removal behavior means you cannot set a source field value to `null`.

Examples:

- Patch member `"PONumber":99999` overrides a source member with field `PONumber`, replacing its value with the patch-specified value, `99999`.

  `json_mergepatch('{"User":"ABULL", "PONumber":1600}', '{"PONumber":99999}')` results in `{"User":"ABULL", "PONumber":99999}`.

- Patch member `"tracking":123456` overrides a missing source member with field `tracking`, adding that patch member to the result. And source member `"PONumber":1600` overrides a missing patch member with field `PONumber` — it is kept in the result.

  `json_mergepatch('{"PONumber":1600}', '{"tracking":123456}')` results in `{"PONumber":1600, "tracking":123456}"`.

- Patch member `"Reference":null` overrides a source member with field `Reference`, removing it from the result.

  `json_mergepatch('{"PONumber":1600, "Reference":"ABULL-20140421"}', '{"Reference":null}')` results in `{"PONumber":1600}`.

- Patch value `[1,2,3]` overrides the corresponding source value, `[4,5,6]`, replacing it.

  `json_mergepatch('{"PONumber":1600, "LineItems":[1, 2, 3]}', '{"LineItems":[4,5,6]}')` results in `{"PONumber":1600, "LineItems":[4, 5, 6]}`.

**Note:**

The merge-patch procedure — in particular the fact that there is no recursive behavior for a non-object patch — means that you cannot add, remove, or replace values of an array individually. To make such a change you must replace the whole array. For example, if the source document has a member `Phone:["999-555-1212", "415-555-1234"]` then to remove the second phone number you can use a patch whose content has a member `"Phone":["999-555-1212"]`.

**See Also:**

- [IETF RFC7396](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=ietf_org_rfc7396) for the definition of JSON Merge Patch

- [Oracle Database SQL Language Reference](../sqlrf/JSON_MERGEPATCH.md) for information about SQL function `json_mergepatch`

Example 12-1 A JSON Merge Patch Document

If applied to the document shown in [Example 2-1](json-data.md), this JSON Merge Patch document does the following:

- Adds member `"Category" : "Platinum"`.

- Removes the member with field `ShippingInstructions`.

- Replaces the value of field `Special Instructions` with the string `"Contact User SBELL"`.

- Replaces the value of field `LineItems` with the empty array, `[]`

- Replaces member `"AllowPartialShipment" : null` with member `"Allow Partial Shipment" : false` (in effect renaming the field, since the field value was already `false`).

<!-- -->

    { "Category" : "Platinum",
      "ShippingInstructions" : null,
      "Special Instructions" : "Contact User SBELL",
      "LineItems" : [],
      "AllowPartialShipment" : null,
      "Allow Partial Shipment" : false }

Example 12-2 A Merge-Patched JSON Document

This example shows the document that results from merge-patching the document in [Example 2-1](json-data.md) with the patch of Example 12-1.

    { "PONumber" : 1600,
      "Reference" : "ABULL-20140421",
      "Requestor" : "Alexis Bull",
      "User" : "ABULL",
      "CostCenter" : "A50",
      "Special Instructions" : "Contact User SBELL",
      "Allow Partial Shipment" : false,
      "LineItems" : [],
      "Category" : "Platinum" }

Example 12-3 Updating a JSON Column Using JSON Merge Patch

This example updates all documents in `j_purchaseorder.po_document`, removing field `"Special Instructions"`.

    UPDATE j_purchaseorder SET po_document =
      json_mergepatch(po_document, '{"Special Instructions":null}');

Example 12-4 Updating Selected JSON Documents On the Fly

This example selects all documents in `j_purchaseorder.po_document`, returning pretty-printed, updated copies of them, where field `"Special Instructions"` has been removed.

    SELECT json_mergepatch(po_document, '{"Special Instructions":null}'
                           RETURNING CLOB PRETTY)
      FROM j_purchaseorder;

**Related Topics**

- [Overview of Inserting, Updating, and Loading JSON Data](overview-of-inserting-updating-loading-JSON-data.md)
- [Using PL/SQL Object Types for JSON](using-PLSQL-object-types-for-JSON.md)
- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)
- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)

**Parent topic:** [Insert, Update, and Load JSON Data](insert-load-and-update-json-data.md)
