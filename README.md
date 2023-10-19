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
## Exercise 5
```
USE execises_db;

INSERT INTO Genre(genre) VALUES
	("Rock"),
    ("Jazz"),
    ("Bachata"),
    ("POP"),
    ("Techno"),
    ("Hardstyle"),
    ("Classical"),
    ("Indie"),
    ("Funk"),
    ("Country");
    
INSERT INTO Album( albumName, dateReleased) VALUES
	("Amarillo","2010-07-20"),
    ("Una Rosa espinosa","2020-05-29"),
    ("El meado","2023-10-16"),
    ("La furgoneta","2023-10-16"),
    ("Mobil enterrado","2019-03-06"),
    ("Mounir","2009-07-20"),
    ("ASCII Lover","1999-07-20"),
    ("GUCCI","2013-05-20"),
    ("Learner","2010-07-20"),
    ("Amarillo","2010-07-20");
    
INSERT INTO Artist(artistName) VALUES
	("Lil Nas"),
    ("XXX Tentacion"),
    ("Dragonflame"),
    ("Polyphia"),
    ("Aries"),  
    ("Wiguez"),
    ("Quevedo"),
    ("Duki"),
    ("La Rosalia"),
    ("Mounir");
```  
## Exercise 6
1: ``` SELECT postalZip AS 'código postal', region AS 'región', country AS 'país' FROM mytable; ```  
2: ``` SELECT * FROM mytable WHERE phone LIKE '811%'; ```  
3: ``` SELECT * FROM mytable WHERE country IN ("Italy","Spain"); ```   
4: ``` SELECT COUNT(*) FROM mytable; ``` 
5: ``` SELECT region, country, postalZip FROM mytable WHERE id IN(SELECT id FROM mytable WHERE country IN('Turkey',"Germany")); ```  
6: ``` SELECT MIN(id), MAX(id) FROM mytable; ```  
7: ``` SELECT country, COUNT(*) FROM mytable GROUP BY country; ```  
8: ``` SELECT * FROM mytable ORDER BY postalZip LIMIT 10; ```  
9: ``` DELETE FROM mytable WHERE country = 'Singapore'; ```  

## Exercise 7



