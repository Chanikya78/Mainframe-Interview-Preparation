**What are Subscript and Index, and why do we use Subscript and Index ?**

In COBOL, both subscript and index are used to access individual elements within tables (arrays).

However, they have distinct characteristics and usage:

* A subscript is an integer value that directly specifies the position or occurrence number of an element within a table.

Usage:
--> Can be any positive integer or an integer data item.
-→ Used directly with the table element name to access a specific occurrence.
--> Can be used in arithmetic expressions.

Example:

01 TABLE-A.
05 TABLE-ELEMENT PIC X(10) OCCURS 10 TIMES.

MOVE 'VALUE1' TO TABLE-ELEMENT(3) -- Accesses the 3rd element

* An index is a special type of data item that is associated with a table using the INDEXED BY clause in the OCCURS statement.

Usage:
--> Primarily used with the SET, SEARCH, and PERFORM statements for efficient table processing.
--> Cannot be used directly in arithmetic expressions.
--> Provides faster access to table elements compared to subscripts, especially for large tables.

Example:

01 TABLE-A.
05 TABLE-ELEMENT PIC X(10) OCCURS 10 TIMES INDEXED BY INDEX-A.

SET INDEX-A TO 3. -- Sets the index to the 3rd element
MOVE 'VALUE2' TO TABLE-ELEMENT. -- Accesses the element using the index
