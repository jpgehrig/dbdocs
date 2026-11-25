## 15  CTX_ULEXER Package

This chapter provides reference information on how to use the `CTX_ULEXER` PL/SQL package with the user-defined lexer.

`CTX_ULEXER` declares the following type:

| Name         | Description                                                                                                                                          |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|
| WILDCARD_TAB | Index-by table type that you use to specify the offset of characters to be treated as wildcard characters by the user-defined lexer query procedure. |

**Note:**

The APIs in the `CTX_ULEXER` package do not support identifiers that are prefixed with the schema or the owner name.

### 15.1 WILDCARD_TAB

    TYPE WILDCARD_TAB IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;

Use this index-by table type to specify the offset of those characters in the query word to be treated as wildcard characters by the user-defined lexer query procedure.

Character offset information follows USC-2 codepoint semantics.
