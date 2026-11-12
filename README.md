# LibraryDB

<img src="https://socialify.git.ci/ntombizodwantlahla53-code/LibraryDB/image?language=1&owner=1&name=1&stargazers=1&theme=Light" alt="LibraryDB" width="640" height="320" />

## Project Overview
```
LibraryDB is a PostgreSQL database project for managing a library. It stores information about books, authors, and patrons. The project uses SQL commands to create tables, insert data, retrieve records, update information, and delete records.
```

## Technologies Used
```
- PostgreSQL
- pgAdmin 4
- SQL
```

## Instructions for Running Queries in pgAdmin or psql
### Using pgAdmin 4
1. Open pgAdmin 4.
2. Connect to your PostgreSQL server.
3. Right-click **Databases** and select **Create>Database**.
4. Enter `LibraryDB` as the database name and save.
5. Select the LibraryDB database.
6. Open **Query Tool**.
7. Copy and paste the SQL commands from each sprint.
8. Click **Execute** to run the queries and view the results.

```sql
CREATE DATABASE LibraryDB;
```
3. Connect to the database:
```sql
\c librarydb
```
4. Run the SQL commands from each sprint.


## Sprint 1: Project Setup
### Create Database
```sql
CREATE DATABASE LibraryDB;
```

### Create Books Table

```sql
CREATE TABLE IF NOT EXISTS books (
    book_id BIGSERIAL PRIMARY KEY NOT NULL,
    title VARCHAR(50) NOT NULL,
    genres TEXT[],
    published_year INT NOT NULL,
    availability BOOLEAN NOT NULL,
    author_id BIGINT
);
```
### Create Authors Table

```sql
CREATE TABLE IF NOT EXISTS authors (
    author_id BIGSERIAL PRIMARY KEY NOT NULL,
    name VARCHAR(50) NOT NULL,
    nationality VARCHAR(49) NOT NULL,
    birth_year INT NOT NULL,
    death_year INT NOT NULL
);
```
### Create Patrons Table

```sql
CREATE TABLE IF NOT EXISTS patrons (
    patron_id BIGSERIAL PRIMARY KEY NOT NULL,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(50) NOT NULL,
    borrowed_books INT[]
);
```

## Sprint 2: Insert Data
### 1. Insert at Least 10 Sample Books

```sql
INSERT INTO books (book_id, title, genres, published_year, availability, author_id)
VALUES
(1, '1984', ARRAY['Dystopian', 'Political Fiction'], 1949, TRUE, 1),
(2, 'To Kill a Mockingbird', ARRAY['Southern Gothic', 'Bildungsroman'], 1960, TRUE, 2),
(3, 'The Great Gatsby', ARRAY['Tragedy'], 1925, TRUE, 3),
(4, 'Brave New World', ARRAY['Dystopian', 'Science Fiction'], 1932, TRUE, 4),
(5, 'The Catcher in the Rye', ARRAY['Realist Novel', 'Bildungsroman'], 1951, TRUE, 5),
(6, 'Moby-Dick', ARRAY['Adventure Fiction'], 1851, TRUE, 6),
(7, 'Pride and Prejudice', ARRAY['Romantic Novel'], 1813, TRUE, 7),
(8, 'War and Peace', ARRAY['Historical Novel'], 1869, TRUE, 8),
(9, 'Crime and Punishment', ARRAY['Philosophical Novel'], 1866, TRUE, 9),
(10, 'The Hobbit', ARRAY['Fantasy'], 1937, TRUE, 10);
```
### 2. Insert 10 Sample Authors

```sql
INSERT INTO authors (author_id, name, nationality, birth_year, death_year)
VALUES
(1, 'George Orwell', 'British', 1903, 1950),
(2, 'Harper Lee', 'American', 1926, 2016),
(3, 'F. Scott Fitzgerald', 'American', 1896, 1940),
(4, 'Aldous Huxley', 'British', 1894, 1963),
(5, 'J.D. Salinger', 'American', 1919, 2010),
(6, 'Herman Melville', 'American', 1819, 1891),
(7, 'Jane Austen', 'British', 1775, 1817),
(8, 'Leo Tolstoy', 'Russian', 1828, 1910),
(9, 'Fyodor Dostoevsky', 'Russian', 1821, 1881),
(10, 'J.R.R. Tolkien', 'British', 1892, 1973);
```
### 3. Insert 10 Sample Patrons

```sql
INSERT INTO patrons (patron_id, name, email, borrowed_books)
VALUES
(1, 'Alice Johnson', 'alice@gmail.com', ARRAY[]::INT[]),
(2, 'Bob Smith', 'bob@gmail.com', ARRAY[1, 2]),
(3, 'Carol White', 'carol@gmail.com', ARRAY[3]),
(4, 'David Brown', 'david@gmail.com', ARRAY[4, 5]),
(5, 'Eve Davis', 'eve@gmail.com', ARRAY[]::INT[]),
(6, 'Frank Moore', 'frank@gmail.com', ARRAY[6]),
(7, 'Grace Miller', 'grace@gmail.com', ARRAY[7, 8]),
(8, 'Hank Wilson', 'hank@gmail.com', ARRAY[]::INT[]),
(9, 'Ivy Taylor', 'ivy@gmail.com', ARRAY[9]),
(10, 'Jack Anderson', 'jack@gmail.com', ARRAY[10]);
```

## Sprint 3: Read Operations (Queries)
### 1. Get All Books

```sql
SELECT * FROM books;
```
### 2. Get a Book by Title

```sql
SELECT * FROM books
WHERE title = '1984';
```
### 3. Get All Books by a Specific Author

```sql
SELECT * FROM books
WHERE author_id = 1;
```
### 4. Get All Available Books

```sql
SELECT * FROM books
WHERE availability = TRUE;
```

## Sprint 4: Update Operations
### 1. Mark a Book as Borrowed

```sql
UPDATE books
SET availability = FALSE
WHERE book_id = 1;
```
### 2. Add a New Genre to an Existing Book

```sql
UPDATE books
SET genres = array_append(genres, 'Classic')
WHERE book_id = 1;
```
### 3. Add a Borrowed Book to a Patron's Record

```sql
UPDATE patrons
SET borrowed_books = array_append(borrowed_books, 3)
WHERE patron_id = 1;
```

## Sprint 5: Delete Operations
### 1. Delete a Book by Title

```sql
DELETE FROM books
WHERE title = 'Moby-Dick';
```
### 2. Delete an Author by ID

```sql
DELETE FROM authors
WHERE author_id = 10;
```

## Sprint 6: Advanced Queries
### 1. Find Books Published After 1950

```sql
SELECT * FROM books
WHERE published_year > 1950;
```
### 2. Find All American Authors

```sql
SELECT * FROM authors
WHERE nationality = 'American';
```
### 3. Set All Books as Available

```sql
UPDATE books
SET availability = TRUE;
```
### 4. Find All Books That Are Available AND Published After 1950

```sql
SELECT * FROM books
WHERE availability = TRUE
AND published_year > 1950;
```
### 5. Find Authors Whose Names Contain "George"

```sql
SELECT * FROM authors
WHERE name LIKE '%George%';
```
### 6. Increment the Published Year 1869 by 1

```sql
UPDATE books
SET published_year = published_year + 1
WHERE published_year = 1869;
```