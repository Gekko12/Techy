# ########## #
# ORACLE SQL #
# ########## #


- data: info we stored somewhere
- database: place where we store organized collection of data
- DBMS: s/w that enables users to access, manipulate and retrieve data
- Entity: table/real thing
- Relationship: connection b/w tables
- Schema: collection of logical structure of data
- Schema objects:
    1. Table: base unit of the db to store data
    2. Views: virtual table provides access to subset of col/row of one or more tables  
    3. Constraints: rules for restricting invalid data entry
    4. Index: used to improve speed of data retreival from table
    5. Sequence: obj which generate unique integers
    6. Synonym: alternative name for db obj
    7. Materialized Views: has real table filled by an SQL query
    8. Fucntions: returns something
    9. Procedure: returns nothing
    10. Triggers: compiled program units stored in db and executed with specific event
    11. db links
    12. Packages
- SQL: Structured Query Language used to interact with db
- Constraints: column lvl and table lvl
    1. Primary Key -NOT NULL+UNIQUE 
    2. Not Null -col lvl
    3. Unique -can have multiple null however
    4. Foreign Key -referential integrity constraint
    5. Check
- table lvl constraints are used for composite constriants
- there is no such difference b/w there(col & table lvl constriants) functionalities
- constraint name should be unique
- ON DELETE CASCADE: deletes dependent rows in the child table when a related row in the parent table is deleted
- ON DELETE SET NULL: updates dependent rows in the child table to NULL when a related row in the parent table is deleted.
- CHECK: can't create check constraints referencing another table
- DDL(definition)
    1. CREATE
    2. ALTER
    3. DROP
    4. TRUNCATE
    5. COMMENT
    6. RENAME
- DML(manipulation)
    1. INSERT
    2. UPDATE
    3. DELETE
    4. MERGE
- TCL (transaction control language): txn will end when any commit or rollback stmt are encountered
    1. COMMIT [syntax: COMMIT;]: permanently saves the changes into db and ends the txn
    2. ROLLBACK [syntax: ROLLBACK [TO savePointName];]: undo the changes made to db and restore data to its previos state 
    3. SAVEPOINT [syntax: SAVEPOINT name;]: saves the current state of a txn and we can roll back to that state. A commit will delete all savepoints. After rollback to certain savepoint consecutive savepoints deleted.
- DCL (data control language)
    1. GRANT
    2. REVOKE
- After DDL or DCL, commit automatically executed
- DELETE is used only to remove data from the table, not to remove a table from the database.
- TRUNCATE is used only to remove data from the table, not to remove a table from the database.
- DROP is used to remove data stored in a table as well as a table structure from a database
- datatype:
    1. VARCHAR2(size) -variable len char data
    2. CHAR(size) -fixed len
    3. NUMBER(p, s)
    4. DATE 
    5. LONG
    6. RAW
    7. BLOB
    8. CLOB
    9. BFILE
    10. ROWID
- NULL means unknown or nonexistent. It doesn't use any space in disc
- SQL stmt are not case sensistive ie. select * from Employees; is same as SELECT * FROM Employees;
- SQL stmt can be separated in multiple lines.
- SQL stmt can be terminated by ; or fwd slash '/'(but in new line)
- there would be atleast one space b/w literals
- *dual table is a dummy table.*
Eg. SELECT 'Adam is my name' AS 'Output' from dual;
- DISTINCT operator eliminates duplicate rows
- UNIQUE operator eleiminates duplicate rows. DISTINCT and UNIQUE both are same, but good to use DISTINCT.
- '||' (concatenation operator). Doesn't concatenate NULL value.
- Arithmetic operators (can be applied to DATE and arithmetic operations with NULL returns NULL): 
    +, -, *, / (BODMAS)
    SELECT sysdate + 3 FROM dual; //new date 3 days ahead
- Comparison operator: <,>,=(equal),<=,>=,<>(not equal),!=(not equal),BETWEEN,AND,LIKE,IS NULL
- BETWEEN operator: lower and upper limit val included
    SELECT * FROM Employees WHERE hire_date BETWEEN '01-DEC-2019' AND '01-JAN-2020';
- IN operator: used to retreive the restricted val in specified list
    SELECT * FROM Employees 
    WHERE hire_date IN ('01-AUG-2020', '15-JAN-2018',...);


- LIKE operator: pattern matching
    '%' 0 or more char match
    '_' matches exactly one char
    SELECT * FROM Employees WHERE job_id LIKE '_r%';
- IS [NOT] NULL: used for searching NULL val = NULL is not same as IS NULL
- Logical operators: AND, OR, NOT
- ORDER BY: clause changes the returning rows order by any column or alias or the numeric posistions of the col in the SELECT list(ASC-default or DESC). NULL val displayed last in ascending order
- NULLS FIRST and NULLS LAST operator: used for changing the order of NULL val
Eg. SELECT emp_id
    FROM Employees
    WHERE salary > 1000
    ORDER BY commission_pct DESC NULLS LAST;
- ROWID: unique id that contains the physical address of a row. Oracle generates a unique ROWID at the time of insertion of a row. It's permanent. It's very fast way to access row.
- ROWNUM: consecutive logical sequence number given to the rows fetched from the table. It's temporary. If we change the query the rownum number will refer to another row.
    SELECT emp_id, ROWID, ROWNUM
    FROM Employees
    WHERE ROWNUM <= 10; //to return first 10 rows
- FETCH: clause is used in conjuction with the SELECT and ORDER BY clauses to limit the rows and retrieve a portion of the returning rows.
[OFFSET rows_to_skip ROW[S]]
    FETCH [FIRST|NEXT] [row_count | percent PERCENT] ROW[S] [ONLY|WITH TIES];
//ORDER BY clause is required for WITH TIES option
- Functions
    1. Single Row -one row I/O return one value
    2. Multiple Row -multiple row I/O
- Case conversion function:
    1. LOWER('MY STR') -> 'my str'
    2. UPPER('my str') -> 'MY STR'
    3. INITCAP('my str') -> 'My str'
- Character manipulation function:
    *index of first char is 1 not 0*
    1. SUBSTR(src, position[, length]) -> SUBSTR('Sql Course', 1, 3) -> 'Sql'
    2. LENGTH(str) -> LENGTH('SQL MY') -> 6
    3. CONCAT(str1, str2) -> CONCAT('oh', 'my') -> 'ohmy'
    4. INSTR(str, substr[, pos_to_start, occurence]) -> INSTR('Sql Course', 'o') -> 6
    5. TRIM([[LEADING|TRAILING|BOTH] trim_char FROM] str) -> TRIM('  Sql Course    ') -> 'Sql Course'
    6. REPLACE(str, str_to_replace[, replacement_str]) -> REPLACE('Sql Course', 's', '*') -> 'Sql Cour*e'
    7. LPAD(str, target_len, padding_expr) -> LPAD('SQL', 3, '-') -> '---SQL'
    8. RPAD(str, target_len, padding_expr)
    9. LTRIM(str[, trim_str]) -> LTRIM('   sql course   ') -> 'sql course   '
    10. RTRIM(str[, trim_str])
- NUMERIC functions:
    1. ROUND(num[,decimal]) -> ROUND(12.136, 2) -> 12.14
    2. TRUNC(num[,deciaml]) -> TRUNC(12.136, 2) -> 12.13
    3. CEIL(num) -> CEIL(2.67) -> 3
    4. FLOOR(num) -> FLOOR(2.67) -> 2
    5. MOD(m, n) -> MOD(8, 5) -> 3

- DATE data types:
    1. DATE
    2. TIMESTAMP
    3. TIMESTAMP WITH TIME ZONE
    4. TIMESTAMP WITH LOCAL TIME ZONE
- DATE functions:
    1. SYSDATE
    2. CURRENT_DATE
    3. SESSIONTIMEZONE
    4. SYSTIMESTAMP
    5. CURRENT_TIMESTAMP
- DATE manipulation functions:
    1. ADD_MONTHS(date ,n) -> add months to date
    2. MOTHS_BETWEEN(date1, date2) -> number of months b/w two dates
    3. NEXT_DAY(date, day_of_week) -> returns the date of the next specified weekday
    4. LAST_DAY(date) -> returns the last day of the month
- Explicit data type conversion:
    1. TO_CHAR(date|number [,format_model] [,nls_param])
    2. TO_NUMBER(char [,format_model])
    3. TO_DATE(char [,format_model])
- NVL(exp1, exp2): replace a null value with meaningful alternative. If exp1 is null then returns exp2
- NVL2(exp1, exp2, exp3): if exp1 is not null then returns exp2. If exp1 is null then exp3 is returned. But exp2 and exp3 must have same data type.
- NULLIF(exp1, exp2): compares exp1 and exp2. If they are equal returns NULL else return exp1. exp1 and exp2 must be in same data type.
- COALESCE(exp1, exp2, ...): accepts a list of args and returns the first one that evals to a non-null val. If all are null then returns null. Accepts atleast two or more params.
- Conditional expr CASE:
    CASE expr WHEN comparison_exp1 THEN result1
              [WHEN comparison_exp2 THEN result2
              :
              ELSE result]
    END
    //expr and comp_exp must be of same data type
    two ways - Simple and Searched Case expr
    CASE first_name
        WHEN 'Alex' THEN 'Name is Alex'
        WHEN 'John' THEN 'Name is John'
        ELSE 'Another'
    END; //simple case expr
    CASE 
        WHEN first_name = 'Alex' THEN 'Name is Alex'
        WHEN first_name = 'John' THEN 'Name is John'
        ELSE 'Another'
    END; //searched case expr
- DECODE function:
    DECODE (col|exp, search1, res1 [,search2, res2]...[default]) //same as CASE expr provide if-then-else




- Group functions: returns one value and input multiple rows. The maximum depth allowed when nesting group functions is 2.
    SELECT group_function([DISTICNT|ALL] coulumn_name), ...
    FROM tableName
    [WHERE condition];
    1. AVG([DISTINCT|ALL] expr) //null val are ignored
    2. COUNT([DISTINCT|ALL] expr|*) //* represents all rows including NULL val
    3. MAX(expr)
    4. MIN(expr)
    5. SUM(expr)
    6. LISTAGG(colName [,delimiter]) WITHIN GROUP (ORDER BY sort_expr) //can be used to display col's result in a single line
    Eg.
    SELECT LISTAGG(first_name, ',') WITHIN GROUP (ORDER BY first_name) AS 'Employees' 
    FROM employees
    WHERE job_id = 'ST_CLERK'; //output: john,ram,shyam
- order of execution:
    1. FROM
    2. WHERE
    3. GROUP BY
    4. HAVING
    5. SELECT
    6. ORDER BY
- JOIN
    1. Natural join: both table must have one same col name which has datatype on which joining is performed. Common col displayed only once in o/p.
        SELECT columns 
        FROM src_tab NATURAL JOIN target_tab;
    2. Equi join:
        SELECT columns 
        FROM tab1 JOIN tab2 USING(commonCol1[commonCol2, ...]);
        //we can handle col ambiguity using table alias
    3. Inner join
        SELECT col1, col2, ...
        FROM tab1 [INNER] JOIN tab2
        {ON tab1.colName = tab2.colName [AND]...}
        |{USING(colName, ...)}
        [WHERE|AND restricting_condition_of_join];
        //ON clause can work if col names are different, whereas USING clause must have same col names in both tables
        //when using USING clause we should not put alias in USING and that col with SELECT
    4. Self join
        SELECT worker.first_name, worker.emp_id, worker.manager_id, manager.emp_id, manager.first_name
        FROM employees worker JOIN employees manager
        ON (worker.manager_id = manager.emp_id);
    5. Non-Equijoin (joining unequal table)
        SELECT e.emp_id, e.first_name, e.job_id, e.salary, j.min_salary, j.max_salary, j.job_id
        FROM employees e JOIN jobs j
        ON e.salary > j.max_salary
        AND j.job_id = 'SA_REP';
                //or
        SELECT e1.emp_id, e1.first_name, e1.last_name
        FROM employees e1 JOIN employees e2
        ON e1.emp_id <> e2.emp_id
        AND e1.first_name = e2.first_name;
    6. OUTER JOIN: to prevent loss of data
        a)left outer b) right outer c) full outer join
            SELECT col1, col2, ...
            FROM tab1 LEFT|RIGHT|FULL [OUTER] JOIN tab2
            {ON tab1.colName = tab2.colName [AND]...};
            |{USING(colName, ...)}
    7. CROSS JOIN(cartesian product/cross product)
        SELECT columns
        FROM tab1 CROSS JOIN tab2;
- Non-ANSI join(old style join syntax)
    1. inner join
        SELECT e.first_name, e.dept_name
        FROM employees e, department d
        WHERE e.dept_id = d.dept_id;
    2. left join
        SELECT e.first_name, e.dept_name
        FROM employees e, department d
        WHERE e.dept_id = d.dept_id(+); //mind the plus opp direction
    3. right join
        SELECT e.first_name, e.dept_name
        FROM employees e, department d
        WHERE e.dept_id(+) = d.dept_id;
    4. full outer join
        SELECT e.first_name, e.dept_name
        FROM employees e, department d
        WHERE e.dept_id(+) = d.dept_id;
        UNION
        SELECT e.first_name, e.dept_name
        FROM employees e, department d
        WHERE e.dept_id = d.dept_id(+);
    Better to use new ANSI syntax to avoid errors
    Don't use Natural joins. Use table alias
- SET operator
    1. UNION [ALL] //duplicate once only displayed when use w/o ALL
    2. INTERSECT
    3. MINUS
    //only one ORDER BY clause is to be used at the end of query and it recognise the aliases and col from first query. Columns heading came from first query and number of col must match is both sets. We can use NULL to match no. of cols.
    SELECT book_id, book_name //this heading is used
    FROM Books
    UNION
    SELECT movie_id, movie_name
    FROM Movies
    ORDER BY book_id; //only one ORDER BY clause





- Subqueries: Inner queries executed first
    1. Single row subqueries: <,>,<=,>=,<>,= used
        SELECT * FROM employees
        WHERE dept_id = (
            SELECT dept_id
            FROM employees
            WHERE emp_id = 145
        );
        If single row subquery returns more that one rows then it generates error.
    2. Multiple row subqueries: IN, ANY, ALL operators used
        ANY and ALL operator should be used with comparison operator(<,>,<>,=,!=)
        SELECT first_name, dept_id, salary
        FROM employees
        where salary > ANY (SELECT salary 
                            from employees
                            where job_id = 'SA_MAN'
        );
    3. Multiple column queries
        //Non-pairwise
        SELECT emp_id, dept_id, salary
        FROM employees
        WHERE dept_id IN 
                        (SELECT dept_id FROM employees
                        WHERE emp_id IN (103,105,110))
        AND salary IN
                        (SELECT salary FROM employees
                        WHERE emp_id IN (103,105,110));
        //Pairwise
        SELECT emp_id, dept_id, salary
        FROM employees
        WHERE (dept_id, salary) IN
                        (SELECT dept_id, salary
                        FROM employees
                        WHERE emp_id IN (103,105,110));
- Inline view
    SELECT * FROM (SELECT dept_id, dept_name
                    FROM departments JOIN locations
                    USING(location_id)
                    ORDER BY dept_id);
- Scalar subqueries: subquery returns one row or one col  
    SELECT * FROM employees
    WHERE dept_id = ( --scalar subquery
            SELECT dept_id FROM employees WHERE emp_id = 145 );
    If scalar subquery returns NULL or 0 rows, the amin query returns nothing (similar to single row subquery)
- Correlated subqueries: when a subquery references to the col from the parent query
    SELECT emp_id, dept_id, salary
    FROM employees a
    WHERE salary = (SELECT MAX(salary)
                    FROM employees b
                    WHERE b.dept_id = a.dept_id);


- [NOT] EXISTS operator: returns true or false. Used to check the existence of rows in the subquery and match the records b/w the subquery and main query
    SELECT emp_id, first_name, dept_id
    FROM employees a
    WHERE EXISTS
        (SELECT * FROM employees WHERE manager_id = a.emp_id);
- VIEWS: Don't include ORDER BY clause in VIEWS, as we need to add it in main query.
    CREATE VIEW view_name AS
    SELECT *
    FROM employees;
        //to delete views
    DROP VIEW viewName;
    View doesn't store table, every time it runs the query saved as view.
        //to create only view so nobody can insert, update to base table
    CREATE [OR REPLACE] VIEW v_jobsAS 
    SELECT * FROM jobs
    [WITH READ ONLY];
- SYNONYM:
    CREATE [OR REPLACE] SYNONYM electricity_bill FOR bill;
- INDEX:
    CREATE [UNIQUE] INDEX building_idx
    ON building(owner_name);







Syntax

CREATE TABLE [SchemaName.]tableName1 (
    col1 NUMBER [CONSTRAINT constriantName UNIQUE], //col lvl 
    col2 VARCHAR(50) [constName PRIMARY KEY],
    col3 VARCHAR(50),
    col4 NUMBER [NOT NULL],
    col5 VARCHAR(11) [CONSTRAINT constriantName1 UNIQUE 
    CONSTRIANT constriantName2 NOT NULL],
    col6 NUMBER [CONSTRAINT constrName REFERENCES tableName2(colName)],   //for foreign key
    col7 NUMBER [CHECK(col4 IN (10,20,30,40))],
    [CONSTRAINT constName UNIQUE(col2, col3, col4) //table lvl], composite constraint
    [CONSTRAINT constName FOREIGN KEY(col) REFERENCES tableNAME(col) ON DELETE CASCADE]
); //constriantName can be useful to debug when we get errors

DESC[RIBE] tableName; //display name, null? and type
INFO[RMATION] tableName;





//Create Table Aa Select Stmt (CTAS)
CREATE TABLE tableName[(col1, col2....)]
AS select_query;
//blank table copy ie. only structure can be copied by using WHERE clause with universal false Eg.
CREATE TABLE emp_copy
AS (SELECT * FROM Employees 
WHERE 1 = 2);
// only null constraints are inherited by using CTAS

ALTER TABLE tableName
ADD (col1 datatype [DEFAULT default_val][NOT NULL],
    col2 datatype,....);

//to modify datatype, size, NULL constraint, default values
ALTER TABLE tableName
MODIFY (col1 modifydatatype....);

ALTER TABLE tableName
DROP COLUMN (col1, col2, ...);

//purge option del table permananetly, dy default table moves to recycle bin but no guarantee
DROP TABLE tableName [PURGE];
//to restore the dropped table from recycle bin
FLASHBACK TABLE tableName to BEFORE DROP;

//delete is slower than truncate, but allows rollback
DELETE FROM tableName;

//truncate doesn't allow rollback
TRUNCATE TABLE [schema_name.]table_name;

//to add explanation to a table or a col
COMMENT ON COLUMN employees.job_id IS 'This column stores abbrevation of job titles';
COMMENT ON TABLE employees IS 'This is table commment';
//to drop comments use empty comment as we can't directly drop a comment
COMMENT ON COLUMN employees.job_id IS '';
COMMENT ON TABLE employees IS '';
//we can query comments from user_tab_comments and user_col_comments views
SELECT * FROM user_tab_comments WHERE table_name = 'employees';
SELECT * FROM user_col_comments WHERE table_name = 'employees';
INFO employees; //it show comments also

ALTER TABLE table_name RENAME COLUMN old_name TO new_name;
//to rename a table
RENAME old_tab_name TO new_tab_name;







INSERT INTO tableName(col1 ,col2, ...)
VALUES(val1, val2, ...);
//below syntax all val we have to insert
INSERT INTO tableName
VALUES(val1, val2, ...);
*Passign NULL val to a col having default val prevent the use of the DEFAULT val*
//we can apply functions to INSERT stmt
INSERT INTO Employees(name, id)
VALUES(upper('john'), 123);

INSERT INTO target_tab(col1, col2, ...)
SELECT (col1, col2, ...) FROM source_tab;

INSERT ALL
  INTO mytable (column1, column2, column_n) VALUES (expr1, expr2, expr_n)
  INTO mytable (column1, column2, column_n) VALUES (expr1, expr2, expr_n)
  INTO mytable (column1, column2, column_n) VALUES (expr1, expr2, expr_n)
SELECT * FROM dual;  //dual is a dummy table which has nothing

UPDATE tableName
SET col1 = val1[, col1 = val2, ...]
[WHERE condition(s)];
//update using subquery
UPDATE employees_copy
    SET (salary, commission_pct) = (SELECT MAX(salary), MAX(commission_pct) FROM employees)
WHERE job_id = 'IT_PROG';

//to del all rows
DELETE [FROM] tableName;

DELETE [FROM] tableName
[WHERE condition];

SELECT exp1,exp2,...,aggregate_function(exp)...|*|{col1, col2, ...} 
FROM tableName
[WHERE logical expression(s)]
[GROUP BY exp1, exp2, ...]
[HAVING condition_with_grouping_functions]
[ORDER BY colName1[,colName2, ...]|colPositions[ASC|DESC]];
//SELECT clause cann't have any other individual columns that what is used with the GROUP BY clause
//ORDER BY clause can't have any other individual columns that the GROUP BY clause has
//column aliases can't be used in group by clause
//we can't use group function in WHERE clause...see order of exec
//HAVING clause use to filter grouped data








//column aliases
SELECT firstName||" "||lastName AS FullName
FROM Employees;
//without AS also aliasing work
SELECT firstName||" "||lastName FullName
FROM Employees;
//aliases should be used with double quotes if it contains space, special chars etc.

//quote operator
SELECT q'[My Name is Steve and I'm good]' as 'Quote operator' FROM dual;

//only one DISTINCT keyword should be used
SELECT DISTINCT id, name FROM Employees;
//it returns unique rows in combination of (id, name) ie. (1, abc) is different than (1, def)

SELECT emp_id, first_name
FROM Employees
WHERE salary > 10000
ORDER BY emp_id ASC, first_name DESC;

//to display first 5 topmost salary with dept_id  80
SELECT emp_id, first_name, salary, ROWID, ROWNUM
FROM (
    SELECT emp_id, first_name, salary
    FROM Employees
    WHERE dept_id = 80
    ORDER BY salary DESC )
WHERE ROWNUM <= 5; //kept after order clause otherwise unsatisfied result will come

SELECT first_name, last_name, salary
FROM Employees
ORDER BY salary DESC
[OFFSET 1 ROW] FETCH 10 ROWS [ONLY|WITH TIES];
//OFFSET clause exclude the specified row

SELECT * 
FROM employees
WHERE LOWER(name) = 'king';

SELECT first_name, job_id,
    CASE job_id WHEN 'ST_CLERK' THEN 1.20 * salary
                WHEN 'ST_MAN' THEN 1.30 * salary
                WHEN 'ST_PROG' THEN 1.40 * salary
                ELSE salary
    END 'UPDATED SALARY'
FROM employees;
// we can use CASE expr in WHERE clause also






SELECT first_name, job_id,
    DECODE(job_id,'ST_CLERK', 1.20 * salary
                  'ST_MAN', 1.30 * salary
                  'ST_PROG', 1.40 * salary
    ) AS 'UPDATED SALARY'
FROM employees;

SELECT job_id, dept_id, AVG(salary)
FROM employees
GROUP BY job_id, dept_id
ORDER BY AVG(salary);


