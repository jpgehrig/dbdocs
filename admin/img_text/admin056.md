# Description of the illustration admin056.eps

This is a text description of admin056.gif. This figure illustrates how online redo log files are archived. In this case there is only one archive process (ARC0) and only one archived redo log. It shows the following sequence:

- LGWR writes to online redo log file 1 (Log0001).

- When Log0001 is full, ARC0 writes it to the archived redo log.

- LGWR writes to online redo log file 2 (Log0002).

- When Log0002 is full, ARC0 writes it to the archived redo log.

- LGWR writes to online redo log file 3 (Log0003).

- When Log0003 is full, ARC0 writes it to the archived redo log.

- LGWR writes to online redo log file 4 (Log0004).

- When Log0004 is full, ARC0 writes it to the archived redo log.

End of image description.
