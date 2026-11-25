# Description of the illustration dbr_rep_wait_time_dist.gif

The Wait Time Distribution subsection of a sample report is shown in this graphic. This subsection contains two tables.

The first table, named Time Period (1), contains three columns: Event (1), Wait Time (1), and Event Count (1). The values of each row in this table are as follows:

- log file switch (checkpoint incomplete) Configuration, 239.88801, 12

- direct path write temp User I/O, 10, 2924

- log buffer space Configuration, 10, 6

The second table, named Time Period (2), contains three columns: Event (2), Wait Time (2), and Event Count (2). The values of each row in this table are as follows:

- direct path read user I/O, 590, 185443

- log file switch (checkpoint incomplete) Configuration, 114.33483, 20

- direct path read temp User I/O, 80, 132686

- free buffer waits Configuration, 70, 435

- direct path write temp User I/O, 50, 73

- db file sequential read User I/O, 50, 11617

- log file switch completion Configuration, 30. 44

- log buffer space Configuration, 30, 34

- latch: row cache objects Concurrency, 10, 28

- undo segment extension Configuration, 10, 4

End of image description.
