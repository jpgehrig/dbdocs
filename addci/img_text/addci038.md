The Point Quadtree index structure is illustrated in three successive states. Each Node has four cells that represent four compass points (at positions 1, 2, 3, and 4); these may or may not point to child Nodes.

- State 1:

  - Top (root) Node has a position 1 pointer to a child Node

  - The child Node has a position 3 pointer to Node A

- State 2: Same as State 1, and the following:

  - Top (root) Node has a position 3 pointer to another child Node

  - This child Node has a position 3 pointer to Node B

- State 3: Same as State 2, and the following:

  - Top (root) Node has a position 4 pointer to yet another child Node

  - This child Node has a position 3 pointer to Node C
