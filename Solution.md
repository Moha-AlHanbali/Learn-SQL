# Exercises Solution

## Setup

- Follow this [guide](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database) to install MySQL on WSL2.

- Install  [MySQL](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2) Extension on `VSCode`.

- Run the command `$ sudo service mysql start`.

- Create a new connection with the extension, using the credentials you created while installing MySQL earlier.

- Go to Database tab and right-click on the connection, choose New Database.

- Enter the following and run code:

```sql
CREATE DATABASE record_company;
USE record_company;

CREATE TABLE bands (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  PRIMARY KEY (id)
);

CREATE TABLE albums (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  release_year INT,
  band_id INT NOT NULL,
  PRIMARY KEY (id),
  FOREIGN KEY (band_id) REFERENCES bands(id)
);
```

- To make queries, hover over the Database and click the page icon that appears on the right side.

## Solutions

### 1. Create a Songs Table

```sql
CREATE TABLE songs (
  id INT AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  length FLOAT NOT NULL,
  album_id INT NOT NULL,
  PRIMARY KEY(id),
  FOREIGN KEY(album_id) REFERENCES albums(id)
);
```

- Copy data from `data.sql`, paste it in workspace, highlight all content and run code.

<br>

### 2. Select only the Names of all the Bands

```sql
SELECT name FROM bands;
SELECT bands.name AS 'Band Name' FROM bands;
```

<br>

### 3. Select the Oldest Album

```sql
SELECT * FROM albums
WHERE release_year IS NOT NULL
ORDER BY release_year ASC 
LIMIT 1;
```

<br>

### 4. Get all Bands that have Albums

```sql
SELECT bands.name AS 'Band Name' FROM bands
JOIN albums ON bands.id = albums.band_id
GROUP BY albums.band_id
HAVING COUNT(albums.id) > 0;
```

<br>

### 5. Get all Bands that have No Albums

```sql
SELECT bands.name AS 'Band Name' FROM bands
LEFT JOIN albums ON bands.id = albums.band_id
GROUP BY bands.id, albums.band_id
HAVING COUNT(albums.id) = 0;
```

<br>

### 6. Get the Longest Album

```sql
SELECT albums.name AS 'Name', albums.release_year AS 'Release Year', SUM(songs.length) AS 'Duration' FROM albums
JOIN songs ON albums.id = songs.album_id
GROUP BY songs.album_id 
ORDER BY Duration DESC
LIMIT 1; 
```
<br>

### 7. Update the Release Year of the Album with no Release Year

```sql
SELECT * FROM albums
WHERE release_year IS NULL;

UPDATE albums
SET release_year = 1986
WHERE id = 4;
```

<br>

### 8. Insert a record for your favorite Band and one of their Albums

```sql
INSERT INTO bands
VALUES (8, 'Draconian');
SELECT * FROM bands;

INSERT INTO albums
VALUES (19, 'Turning Season Within', 2008, 8);

SELECT * FROM albums;
```

<br>

### 9. Delete the Band and Album you added in #8

```sql
DELETE FROM albums 
WHERE id = 19;

SELECT * FROM albums;

DELETE FROM bands
WHERE id = 8;

SELECT * FROM bands;
```

<br>

### 10. Get the Average Length of all Songs

```sql
SELECT AVG(length) AS 'Average Song Duration' FROM songs;
```

<br>

### 11. Select the longest Song off each Album

```sql
SELECT albums.name AS 'Album', albums.release_year AS 'Release Year',
MAX(songs.length) AS 'Duration'
FROM albums
JOIN songs
ON albums.id = songs.album_id
GROUP BY songs.album_id;
```

<br>