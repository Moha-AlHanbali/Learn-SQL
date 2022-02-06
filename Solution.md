# Exercises Solution

## Setup

- Follow this [guide](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database) to install MySQL on WSL2.

- Install  [MySQL](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2) Extension on `VSCode`.

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

