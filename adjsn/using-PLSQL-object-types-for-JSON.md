Some examples of using PL/SQL object types for JSON are presented.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_ARRAY_T`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_ELEMENT_T`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_OBJECT_T`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/json-types.md) for information about `JSON_KEY_LIST`

Example 25-1 Constructing and Serializing an In-Memory JSON Object

This example uses function `parse` to parse a string of JSON data that represents a JSON object with one field, `name`, creating an instance `je` of object type `JSON_ELEMENT_T`. This instance is tested to see if it represents an object, using introspection method (predicate) `is_object()`.

If it represents an object (the predicate returns `TRUE` for `je`), it is cast to an instance of `JSON_OBJECT_T` and assigned to variable `jo`. Method `put()` for object type `JSON_OBJECT_T` is then used to add object field `price` with value `149.99`.

Finally, `JSON_ELEMENT_T` instance `je` (which is the same data in memory as `JSON_OBJECT_T` instance `jo`) is serialized to a string using method `to_string()`, and this string is printed out using procedure `DBMS_OUTPUT.put_line`. The result printed out shows the updated object as `{"name":"Radio-controlled plane","price":149.99}`.

The updated transient object `je` is serialized here only to be printed out; the resulting text is not stored in the database. Sometime after the example code is executed, the memory allocated for object-type instances `je` and `jo` is reclaimed by the garbage collector.

    DECLARE
      je JSON_ELEMENT_T;
      jo JSON_OBJECT_T;
    BEGIN
      je := JSON_ELEMENT_T.parse('{"name":"Radio controlled plane"}');
      IF (je.is_Object) THEN
        jo := treat(je AS JSON_OBJECT_T);
        jo.put('price', 149.99);
      END IF;
      DBMS_OUTPUT.put_line(je.to_string);
    END;
    /

Example 25-2 Using Method GET_KEYS() to Obtain a List of Object Fields

PL/SQL method `get_keys()` is defined for PL/SQL object type `JSON_OBJECT_T`. It returns an instance of PL/SQL object type `JSON_KEY_LIST`, which is a varray of `VARCHAR2(4000)`. The varray contains all of the field names for the given `JSON_OBJECT_T` instance.

This example iterates through the fields returned by `get_keys()`, adding them to an instance of PL/SQL object type `JSON_ARRAY_T`. It then uses method `to_string()` to serialize that JSON array and then prints the resulting string.

    DECLARE
      jo          JSON_OBJECT_T;
      ja          JSON_ARRAY_T;
      keys        JSON_KEY_LIST;
      keys_string VARCHAR2(100);
    BEGIN
      ja := new JSON_ARRAY_T;
      jo := JSON_OBJECT_T.parse('{"name":"Beda",
                                  "jobTitle":"codmonki",
                                  "projects":["json", "xml"]}');
      keys := jo.get_keys;
      FOR i IN 1..keys.COUNT LOOP
         ja.append(keys(i));
      END LOOP;
      keys_string := ja.to_string;
      DBMS_OUTPUT.put_line(keys_string);
    END;
    /

The printed output is `["name","jobTitle","projects"]`.

Example 25-3 Using Method PUT() to Update Parts of JSON Documents

This example updates each purchase-order document in JSON column `po_document` of table `j_purchaseorder`. It iterates over the JSON array `LineItems` in each document (variable `li_arr`), calculating the total price and quantity for each line-item object (variable `li_obj`), and it uses method `put()` to add these totals to `li_obj` as the values of new fields `totalQuantity` and `totalPrice`. This is done by user-defined function `add_totals`.

The `SELECT` statement here selects one of the documents that has been updated.

    CREATE OR REPLACE FUNCTION add_totals(purchaseOrder IN VARCHAR2) RETURN VARCHAR2 IS
      po_obj        JSON_OBJECT_T;
      li_arr        JSON_ARRAY_T;
      li_item       JSON_ELEMENT_T;
      li_obj        JSON_OBJECT_T;
      unitPrice     NUMBER;
      quantity      NUMBER;
      totalPrice    NUMBER := 0;
      totalQuantity NUMBER := 0;
    BEGIN
      po_obj := JSON_OBJECT_T.parse(purchaseOrder);
      li_arr := po_obj.get_Array('LineItems');
      FOR i IN 0 .. li_arr.get_size - 1 LOOP
        li_obj := JSON_OBJECT_T(li_arr.get(i));
        quantity := li_obj.get_Number('Quantity');
        unitPrice := li_obj.get_Object('Part').get_Number('UnitPrice');
        totalPrice := totalPrice + (quantity * unitPrice);
        totalQuantity := totalQuantity + quantity;
      END LOOP;
      po_obj.put('totalQuantity', totalQuantity);
      po_obj.put('totalPrice', totalPrice);
      RETURN po_obj.to_string;
    END;
    /

    UPDATE j_purchaseorder SET (po_document) = add_totals(po_document);

    SELECT po_document FROM j_purchaseorder po WHERE po.po_document.PONumber = 1600;

That selects this updated document:

    {"PONumber": 1600,
     "Reference": "ABULL-20140421",
     "Requestor": "Alexis Bull",
     "User": "ABULL",
     "CostCenter": "A50",
     "ShippingInstructions": {"name": "Alexis Bull",
                              "Address": {"street": "200 Sporting Green",
                                          "city": "South San Francisco",
                                          "state": "CA",
                                          "zipCode": 99236,
                                          "country": "United States of America"},
                              "Phone": [{"type": "Office", "number": "909-555-7307"},
                                        {"type": "Mobile", "number": "415-555-1234"}]},
     "Special Instructions": null,
     "AllowPartialShipment": true,
     "LineItems": [{"ItemNumber": 1,
                    "Part": {"Description": "One Magic Christmas",
                             "UnitPrice": 19.95,
                             "UPCCode": 13131092899},
                    "Quantity": 9.0},
                   {"ItemNumber": 2,
                    "Part": {"Description": "Lethal Weapon",
                             "UnitPrice": 19.95,
                             "UPCCode": 85391628927},
                    "Quantity": 5.0}],
     "totalQuantity": 14,
     "totalPrice": 279.3}

**Related Topics**

- [Overview of PL/SQL Object Types for JSON](overview-of-pl-sql-object-types-for-json.md)
- [Updating a JSON Document with JSON Merge Patch](updating-json-document-json-merge-patch.md)

**Parent topic:** [PL/SQL Object Types for JSON](pl-sql-object-types-for-json.md)
