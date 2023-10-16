## Exercise 2  
```
USE SYS;
CREATE TABLE IF NOT EXISTS sys_config;
```  

## Exercise 3
1: DATE  
2: LONGTEXT  
4: FLOAT
5 & 6:  
```
USE execises_db;

CREATE TABLE IF NOT EXISTS Book (
	bookID INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
    textContent LONGTEXT,
    stars FLOAT DEFAULT 0
);

USE Book;
```  
## Exercise 4
```
USE execises_db;

CREATE TABLE IF NOT EXISTS Genre (
	idGenre INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
    genre VARCHAR(255)
);

CREATE TABLE IF NOT EXISTS Album (
    idAlbum INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
    albumName VARCHAR(255),
    dateReleased DATETIME
);

CREATE TABLE IF NOT EXISTS Artist (
	idArtist INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
    artistName VARCHAR(255)
);
```
