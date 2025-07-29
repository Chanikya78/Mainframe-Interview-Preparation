**RUNSTATS utility in DB2**

In IBM Db2, RUNSTATS is a utility used to collect and update statistics about database tables, indexes, and columns. These statistics help the Db2 optimizer make efficient query execution plans.

Syntax:

RUNSTATS ON TABLE schema.table_name
AND INDEXES ALL
WITH DISTRIBUTION
DETAILED INDEXES ALL;

**Key Components**

-> ON TABLE schema.table_name – Specifies the table for which statistics should be collected.
-> AND INDEXES ALL – Updates statistics for all indexes on the table.
-> WITH DISTRIBUTION – Collects frequency distribution statistics for columns, improving cardinality estimation.
-> DETAILED INDEXES ALL – Collects detailed index statistics, which help in index selection.

** Example Usage**

RUNSTATS ON TABLE HR.EMPLOYEES
AND INDEXES ALL
WITH DISTRIBUTION
DETAILED INDEXES ALL;

->This command updates statistics for the HR.EMPLOYEES table and all its indexes.

** When to Run RUNSTATS? **

-> After inserting, deleting, or updating a significant number of rows.
-> After reorganizing (REORG) a table.
-> Before running performance-intensive queries.
-> Periodically, as part of database maintenance.
