Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../dbaccess/package-summary.md)**
- **[Next Package](../differ/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package oracle.xml.diff**

**Provides an API for comparison of XML inputs.**

**See: Description**

- **Interface Summary**

  | Interface                           | Description     |
  |-------------------------------------|-----------------|
  | [DiffOpReceiver](DiffOpReceiver.md) | DiffOpReceiver. |

- **Class Summary**

  | Class                           | Description   |
  |---------------------------------|---------------|
  | [AppendDiffOp](AppendDiffOp.md) | AppendDiffOp. |
  | [DeleteDiffOp](DeleteDiffOp.md) | DeleteDiffOp. |
  | [DiffOp](DiffOp.md)             | DiffOp.       |
  | [InsertDiffOp](InsertDiffOp.md) | InsertDiffOp. |
  | [Options](Options.md)           | Options.      |
  | [XmlUtils](XmlUtils.md)         | XmlUtils.     |

- **Enum Summary**

  | Enum                          | Description |
  |-------------------------------|-------------|
  | [DiffOp.Name](DiffOp.Name.md) |             |

## **Package oracle.xml.diff Description**

**Provides an API for comparison of XML inputs. Diff, hash, and equal methods are provided. See [`XmlUtils`](XmlUtils.md) class which is a starting point for this package, and which provides the diff, hash, and equal methods. Note that the diff algorithm is specifically designed for the use-case of large multiple megabyte XML inputs where the minimal diff is not required. In other words, it is able to handle multiple megabyte XML inputs quickly, sometimes at the cost of producing a non-minimal diff.**

## **Related Documentation**

**For further documentation of this package, please see:**

- **<http://www.oracle.com/technetwork/indexes/documentation/index.html>**
- **[`XmlUtils`](XmlUtils.md)**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../dbaccess/package-summary.md)**
- **[Next Package](../differ/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
