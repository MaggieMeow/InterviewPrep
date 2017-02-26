# SQL Notes

Although I did not have any previous experiences on SQL in actual projects, upon realising that SQL is required for the job of a data analyst, I gave myself a crash course online to learn the syntax of it.

### COMMANDS
**SELECT** title, genre //columns
FROM movies; //table

SELECT * // all columns 
FROM movies;

SELECT title
FROM movies
WHERE id = 2; // a condition for selection, returns all rows/cells satisfying the the condition. comparators are available too like below 

…
WHERE duration <= 100;

**Not equal to is <> or !=**

**Use AND or OR to add more conditions**:
…
WHERE id = 1
AND genre = ‘Comedy’; // can replace AND with OR

…
WHERE title = ’The Kid’; // Use single quotes for searches of exact sequences of characters

SELECT FROM ORDER BY; // default is ascending order, unless DESC is specified like below

SELECT title FROM movies ORDER BY duration DESC;

**INSERT INTO** table (column1, column2) // insert row
VALUES (‘column value’, value 2’); // order of values must match order of columns. null represents blank.

primary key is automatically incremented by the database each time a new row is added to the table.

**UPDATE** table SET column = newValue, column2 = newValue2 WHERE condition OR condition2; // without the WHERE clause, all rows in the column would be updated

**DELETE** FROM table WHERE condition; // without the WHERE, whole table would be deleted

**CREATE DATABASE** newDatabase; // empty upon creation
**DROP DATABASE** oldDatabas; // Completely remove the database
**CREATE TABLE** tableName
(
	columnName int, // primary key that holds unique values
	columnName2 varchar(50) // allows data here to have a variable length of letters and numbers within this field less than 50 characters
); 

**DROP TABLE** tableName; // remove an entire table from database

**ALTER TABLE** tableName **ADD COLUMN** columnName datatype; // Add columns can use DROP COLUMN columnName too





