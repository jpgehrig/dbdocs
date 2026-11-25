# Description of the illustration sqlrf002.eps

    This graphic shows the order in which Oracle returns the rows
    for a query of a hierarchical tree. Beginning with the root row,
    Oracle returns one child row of the root, and then one child of
    that child row, and so forth until a leaf row (one without children)
    is encountered. At this point, Oracle goes up in the hierarchy until
    the next row with a child row is found, and then Oracle returns that
    child, and so forth until the next leaf row is returned. This process
    continues, with Oracle returning to the root row for the next child
    only when all of the "descendants" of the first child row have been
    returned.
