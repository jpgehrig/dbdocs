## 11.7 XS_NAMESPACE Package

The `XS_NAMESPACE` package includes subprograms to create, manage, and delete namespace templates and attributes.

This section includes the following topics:

- Security Model

- Constants

- Object Types, Constructor Functions, Synonyms, and Grants

- Summary of XS_NAMESPACE Subprograms

### 11.7.1 Security Model

The `XS_NAMESPACE` package is created under the `SYS` schema. The `DBA` role is granted the `ADMIN_ANY_SEC_POLICY`, which allows it to administer namespace templates and attributes.

### 11.7.2 Constants

The following are attribute event constants:

    NO_EVENT                     CONSTANT PLS_INTEGER := 0;
    FIRSTREAD_EVENT              CONSTANT PLS_INTEGER := 1;
    UPDATE_EVENT                 CONSTANT PLS_INTEGER := 2;
    FIRSTREAD_PLUS_UPDATE_EVENT  CONSTANT PLS_INTEGER := 3;

### 11.7.3 Object Types, Constructor Functions, Synonyms, and Grants

The following object types, constructor functions, synonyms, and `GRANT` statements are defined for this package.

    -- Type definition for namespace template attribute
    CREATE OR REPLACE TYPE XS$NS_ATTRIBUTE AS OBJECT (
    -- Member Variables
    -- Name of the namespace template attribute
    -- Must be unique within a namespace template
    -- Cannot be null
    name              VARCHAR2(4000),
    -- Default value assigned to the attribute
    default_value     VARCHAR2(4000),
    -- Trigger events associated with the attribute
    -- Allowed values are :
    -- 0 : NO_EVENT
    -- 1 : FIRST_READ_EVENT
    -- 2 : UPDATE_EVENT
    -- 3 : FIRST_READ_PLUS_UPDATE_EVENT
    attribute_events  NUMBER,

    -- Constructor function
    CONSTRUCTOR FUNCTION XS$NS_ATTRIBUTE
                        (name             IN VARCHAR2,
                         default_value    IN VARCHAR2 := NULL,
                         attribute_events IN NUMBER := 0)
                         RETURN SELF AS RESULT,

    -- Return the name of the attribute
    MEMBER FUNCTION GET_NAME RETURN VARCHAR2,
    -- Return the default value of the attribute
    MEMBER FUNCTION GET_DEFAULT_VALUE RETURN VARCHAR2,
    -- Return the trigger events associated with attribute
    MEMBER FUNCTION GET_ATTRIBUTE_EVENTS RETURN NUMBER,
    -- Mutator procedures
    -- Set the default value for the attribute
    MEMBER PROCEDURE SET_DEFAULT_VALUE(default_value IN VARCHAR2),
    -- Associate trigger events to the attribute
    MEMBER PROCEDURE SET_ATTRIBUTE_EVENTS(attribute_events IN NUMBER)
    );
    CREATE OR REPLACE TYPE XS$NS_ATTRIBUTE_LIST AS VARRAY(1000) OF XS$NS_ATTRIBUTE;

### 11.7.4 Summary of XS_NAMESPACE Subprograms

Table 11-9 Summary of XS_NAMESPACE Subprograms

| Subprogram                  | Description                                                      |
|:----------------------------|:-----------------------------------------------------------------|
| CREATE_TEMPLATE Procedure   | Creates a new namespace template.                                |
| ADD_ATTRIBUTES Procedure    | Adds one or more attributes to an existing namespace template.   |
| REMOVE_ATTRIBUTES Procedure | Removes one or more attributes from a namespace template.        |
| SET_HANDLER Procedure       | Assigns a handler function for the specified namespace template. |
| SET_DESCRIPTION Procedure   | Sets a description string for the specified namespace template.  |
| DELETE_TEMPLATE Procedure   | Deletes the specified namespace template.                        |

####

This section describes the following XS_NAMESPACE subprograms:

#### 11.7.4.1 CREATE_TEMPLATE Procedure

The CREATE_TEMPLATE procedure creates a new namespace template.

##### Syntax

    XS_NAMESPACE.CREATE_TEMPLATE (
      name             IN VARCHAR2,
      attr_list        IN XS$NS_ATTRIBUTE_LIST := NULL,
      schema           IN VARCHAR2 := NULL,
      package          IN VARCHAR2 := NULL,
      function         IN VARCHAR2 := NULL,
      acl              IN VARCHAR2 := 'SYS.NS_UNRESTRICTED_ACL'
      description      IN VARCHAR2 := NULL);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                  |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`        | The name of the namespace template to be created.                                                                                                                                                            |
| `attr_list`   | The attributes contained in the namespace template together with their default values and associated attribute events, such as `UPDATE_EVENT`.                                                               |
| `schema`      | The schema that contains the handler function for the namespace template.                                                                                                                                    |
| `package`     | The package that contains the handler function for the namespace template.                                                                                                                                   |
| `function`    | The handler function for the namespace template. The handler function is called when an attribute event occurs.                                                                                              |
| `acl`         | The name of the ACL for this namespace template. If no ACL is provided, the default is the predefined ACL `SYS.NS_UNRESTRICTED_ACL`, which allows unrestricted attribute operations by the application user. |
| `description` | An optional description string for the namespace template.                                                                                                                                                   |

##### Examples

The following example creates a namespace template called `POAttrs`. The namespace template contains a list of attributes defined by `attrlist`. The handler function for the namespace template is called `Populate_Order_Func`. This handler function is part of the `Orders_Pckg` package, which is contained in the `SCOTT` schema. The namespace template has `NS_UNRESTRICTED_ACL` set on the template, which allows unrestricted operation on namespaces created from the template.

    DECLARE
      attrlist XS$NS_ATTRIBUTE_LIST;
    BEGIN
      attrlist := XS$NS_ATTRIBUTE_LIST();
      attrlist.extend(2);
      attrlist(1) := XS$NS_ATTRIBUTE('desc', 'general');
      attrlist(2) := XS$NS_ATTRIBUTE(name=>'item_no',
                     attribute_events=>XS_NAMESPACE.FIRSTREAD_EVENT);
      SYS.XS_NAMESPACE.CREATE_TEMPLATE('POAttrs', attrlist, 'SCOTT',
                                       'Orders_Pckg','Populate_Order_Func',
                                       'SYS.NS_UNRESTRICTED_ACL',
                                       'Purchase Order Attributes');
    END;

#### 11.7.4.2 ADD_ATTRIBUTES Procedure

The `ADD_ATTRIBUTES` procedure adds one or more attributes to an existing namespace template.

##### Syntax

    XS_NAMESPACE.ADD_ATTRIBUTES (
      template         IN VARCHAR2,
      attribute        IN VARCHAR2,
      default_value    IN VARCHAR2 := NULL,
      attribute_events IN PLS_INTEGER := XS_NAMESPACE.NO_EVENT);

    XS_NAMESPACE.ADD_ATTRIBUTES (
      template  IN VARCHAR2,
      attr_list IN XS$NS_ATTRIBUTE_LIST);

##### Parameters

| Parameter          | Description                                                                       |
|:-------------------|:----------------------------------------------------------------------------------|
| `template`         | The name of the namespace templates to which the attribute(s) is/are to be added. |
| `attribute`        | The name of the attribute to be added.                                            |
| `attr_list`        | The list of attributes to be added.                                               |
| `default_value`    | The default value of the attribute.                                               |
| `attribute_events` | The attribute event associated with the attribute, such as update event.          |

##### Examples

The following example adds an attribute called `item_type` to the `POAttrs` namespace. It also specifies a default value and attribute event for the new attribute that is added.

    BEGIN
      SYS.XS_NAMESPACE.ADD_ATTRIBUTES(template=>'POAttrs',attribute=>'item_type',
                                      default_value=>'generic',
                                      attribute_events=>XS_NAMESPACE.update_event);
    END;

#### 11.7.4.3 REMOVE_ATTRIBUTES Procedure

The `REMOVE_ATTRIBUTES` procedure removes one or more attributes from a namespace template. If no attribute names are specified, then all attributes are removed from the namespace template.

##### Syntax

    XS_NAMESPACE.REMOVE_ATTRIBUTES (
      template  IN VARCHAR2,
      attribute IN VARCHAR2);

    XS_NAMESPACE.REMOVE_ATTRIBUTES (
      template  IN VARCHAR2,
      attr_list IN XS$LIST);

    XS_NAMESPACE.REMOVE_ATTRIBUTES (
      template   IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                          |
|:------------|:-------------------------------------------------------------------------------------|
| `template`  | The name of the namespace template from which the attribute(s) is/are to be removed. |
| `attribute` | The name of the attribute to be removed.                                             |
| `attr_list` | The list of attribute names to be removed.                                           |

##### Examples

The following example removes the `item_type` attribute from the `POAttrs` namespace.

    BEGIN
      SYS.XS_NAMESPACE.REMOVE_ATTRIBUTES('POAttrs','item_type');
    END;

The following example removes all attributes from the `POAttrs` namespace template.

    BEGIN
      SYS.XS_NAMESPACE.REMOVE_ATTRIBUTES('POAttrs');
    END;

#### 11.7.4.4 SET_HANDLER Procedure

The `SET_HANDLER` procedure assigns a handler function for the specified namespace template.

##### Syntax

    XS_NAMESPACE.SET_HANDLER (
      template         IN VARCHAR2,
      schema           IN VARCHAR2,
      package          IN VARCHAR2,
      function         IN VARCHAR2);

##### Parameters

| Parameter  | Description                                                                     |
|:-----------|:--------------------------------------------------------------------------------|
| `template` | The name of the namespace template for which the handler function is to be set. |
| `schema`   | The schema containing the handler package and function.                         |
| `package`  | The name of the package that contains the handler function.                     |
| `function` | The name of the handler function for the namespace template.                    |

##### Examples

The following example sets a handler function, called `Populate_Order_Func`, for the `POAttrs` namespace template.

    BEGIN
      SYS.XS_NAMESPACE.SET_HANDLER('POAttrs','SCOTT',
                                   'Orders_Pckg','Populate_Order_Func');
    END;

#### 11.7.4.5 SET_DESCRIPTION Procedure

The `SET_DESCRIPTION` procedure sets a description string for the specified namespace template.

##### Syntax

    XS_NAMESPACE.SET_DESCRIPTION (
      template     IN VARCHAR2,
      description  IN VARCHAR2);

##### Parameters

| Parameter     | Description                                                        |
|:--------------|:-------------------------------------------------------------------|
| `template`    | The name of the namespace template whose description is to be set. |
| `description` | A description string for the specified namespace template.         |

##### Examples

The following example sets a description string for the `POAttrs` namespace template.

    BEGIN
      SYS.XS_NAMESPACE.SET_DESCRIPTION('POAttrs','Purchase Order Attributes');
    END;

#### 11.7.4.6 DELETE_TEMPLATE Procedure

The `DELETE_TEMPLATE` procedure deletes the specified namespace template.

##### Syntax

    XS_NAMESPACE.DELETE_TEMPLATE(
      template      IN VARCHAR2,
      delete_option IN PLS_INTEGER := XS_ADMIN_UTIL.DEFAULT_OPTION);

##### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `template`      | The name of the namespace template to be deleted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `delete_option` | The delete option to use. To the namespace template, the behavior of the following options is the same:<br>• `DEFAULT_OPTION:`<br>• The default option allows deleting a namespace template only if it is not referenced elsewhere. If there are other entities that reference the namespace template, then the namespace template cannot be deleted.<br>• `CASCADE_OPTION`:<br>• The cascade option deletes the namespace template together with any references to it. The user deleting the namespace template deletes these references as well.<br>• `ALLOW_INCONSISTENCIES_OPTION: `<br>• The allow inconsistencies option lets you delete the entity even if other entities have late binding references to it. If the entity is part of an early dependency, then the delete fails and an error is raised. |

##### Examples

The following example deletes the POAttrs namespace template using the default delete option.

    BEGIN
      SYS.XS_NAMESPACE.DELETE_TEMPLATE('POAttrs',XS_ADMIN_UTIL.DEFAULT_OPTION);
    END;
