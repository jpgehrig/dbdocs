This diagram shows an Oracle database. Three bidirectional arrows connect to it from above.

The first bidirectional arrow from the left connects a box labeled "HTTP Protocol Handler" inside the database to a box above the database labeled "Direct HTTP Access".

The second bidirectional arrow from the left connects a box labeled "SQL Engine" inside the database to a box above the database labeled "Oracle Net Access". A box labeled "Oracle Streams AQ Access" is to the right of this arrow. There is an arrow from the "Oracle Streams AQ Access" to this arrow. The "Oracle Net Access" box connects above it with a bidirectional arrow to a box labeled "JDBC".

The third bidirectional arrow from the left connects a box labeled "DAV, FTP Protocol Handlers" inside the database to a box above it labeled "WebDAV Access and FTP Access".

Inside the database is a dashed box labeled "Oracle XML DB". The three database boxes described earlier, "HTTP Protocol Handler"," SQL Engine", and "DAV, FTP Protocol Handlers", are inside this dashed box, as is everything else shown inside the database. Below these boxes is a box labeled "XML Schemas". This box has two arrows that connect to a box labeled "XMLType Tables" and a box labeled "XMLType Views".

Box "XMLType Tables" has two tables inside it. Box "XMLType Views" has two views inside it. To the left of box "XMLType Tables" is a box labeled "Indexes", which includes a list of five bullets: XMLIndex, B-Tree, and XML Full Text. There is an arrow from the "Indexes" box to box "XMLType Tables". To the right of box "XMLType Views" is a box labeled "Repository", which has three folder icons inside it. The top folder icon in this box has a dashed line that connects to the top table inside the box labeled "XMLType Tables". The bottom folder icon in the "Repository" box has a dashed line that connects to the bottom view in the box labeled "XMLType Views". There is a box labeled "Hierarchical Index" to the right of the "Repository" box. An arrow connects from box "Hierarchical Index" to box "Repository".

The box labeled "XMLType Views" has two lines that connect below it to a box named "Local Tables" and a box named "DBLinks". Box "DBLinks" connects with a bidirectional arrow to a box on the right side, outside the database, named "Remote Tables Accessed via DBLinks".

The box labeled "XMLType Tables" has three lines that connect below it to two boxes named "Binary XML Storage", and "Object-Relational Storage".
