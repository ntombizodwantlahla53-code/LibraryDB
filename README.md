# LibraryDB

<img src="https://socialify.git.ci/ntombizodwantlahla53-code/LibraryDB/image?language=1&owner=1&name=1&stargazers=1&theme=Light" alt="LibraryDB" width="640" height="320" />

## Sprint 1: Project Setup
```sql

CREATE TABLE IF NOT EXISTS books(
book_id BIGSERIAL PRIMARY KEY NOT NULL,
title VARCHAR(50) NOT NULL,
genres TEXT[], 
published_year INT NOT NULL, 
availability BOOLEAN NOT NULL,
author_id INT
);

CREATE TABLE IF NOT EXISTS authors(
author_id BIGSERIAL PRIMARY KEY NOT NULL,
name VARCHAR(50) NOT NULL,
nationality VARCHAR(49) NOT NULL, 
birth_year INT NOT NULL, 
death_year INT NOT NULL
);

CREATE TABLE IF NOT EXISTS patrons(
patron_id BIGSERIAL PRIMARY KEY NOT NULL,
name VARCHAR(50) NOT NULL,
email VARCHAR(50) NOT NULL, 
borrowed_books INT
);
```

## Sprint 2: Insert Data
```sql

INSERT INTO books (book_id, title, author_id, genres, published_year, availability) 
VALUES
(1, '1984', 1, ARRAY['Dystopian', 'Political Fiction'], 1949, TRUE),
(2, 'To Kill a Mockingbird', 2, ARRAY['Southern Gothic', 'Bildungsroman'], 1960, TRUE),
(3, 'The Great Gatsby', 3, ARRAY['Tragedy'], 1925, TRUE),
(4, 'Brave New World', 4, ARRAY['Dystopian', 'Science Fiction'], 1932, TRUE),
(5, 'The Catcher in the Rye', 5, ARRAY['Realist Novel', 'Bildungsroman'], 1951, TRUE),
(6, 'Moby-Dick', 6, ARRAY['Adventure Fiction'], 1851, TRUE),
(7, 'Pride and Prejudice', 7, ARRAY['Romantic Novel'], 1813, TRUE),
(8, 'War and Peace', 8, ARRAY['Historical Novel'], 1869, TRUE),
(9, 'Crime and Punishment', 9, ARRAY['Philosophical Novel'], 1866, TRUE),
(10, 'The Hobbit', 10, ARRAY['Fantasy'], 1937, TRUE);


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

INSERT INTO patrons (patron_id, name, email, borrowed_books) 
VALUES
(1, 'Alice Johnson', 'alice@example.com', ARRAY[]::INT[]),
(2, 'Bob Smith', 'bob@example.com', ARRAY[1, 2]),
(3, 'Carol White', 'carol@example.com', ARRAY[]::INT[]),
(4, 'David Brown', 'david@example.com', ARRAY[3]),
(5, 'Eve Davis', 'eve@example.com', ARRAY[]::INT[]),
(6, 'Frank Moore', 'frank@example.com', ARRAY[4, 5]),
(7, 'Grace Miller', 'grace@example.com', ARRAY[]::INT[]),
(8, 'Hank Wilson', 'hank@example.com', ARRAY[6]),
(9, 'Ivy Taylor', 'ivy@example.com', ARRAY[]::INT[]),
(10, 'Jack Anderson', 'jack@example.com', ARRAY[7, 8]);
```
## Sprint 3: Read Operations (Queries)
```sql

SELECT * FROM books

SELECT title FROM books;

SELECT * FROM books
WHERE author_id = 1;

SELECT * FROM books
WHERE availability = true;
```
## Sprint 4: Update Operations
```sql

UPDATE books
SET available = false
WHERE book_id = 1;

UPDATE books
SET genres = genres || ARRAY['My Africa']
WHERE book_id = 6;

UPDATE patrons
SET borrowed_books = array_append(borrowed_books,1)
WHERE patron_id =1;

```
## Sprint 5: Delete Operations
```sql

DELETE FROM books
WHERE title = 'Moby-Dick';

DELETE FROM books
WHERE author_id = 10;

DELETE FROM authors
WHERE author_id = 10;
```
## Sprint 6: Advanced Queries
```sql

SELECT * FROM books 
WHERE published_year > 1950;

SELECT * FROM authors
WHERE nationality = 'American';

UPDATE books
SET available = true;

SELECT * FROM authors
WHERE name LIKE '%George%';

UPDATE books
SET availability = false
WHERE book_id = 1;

UPDATE books
SET published_year = published_year + 1
WHERE published_year = 1869;
```



