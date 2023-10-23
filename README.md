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
1: 
``` 
CREATE TABLE address (
    address_id SMALLINT,
    address VARCHAR(50),
    address2 VARCHAR(50),
    district VARCHAR(20),
    city_id SMALLINT,
    postal_code VARCHAR(10),
    phone VARCHAR(20),
    last_update TIMESTAMP,
    PRIMARY KEY (address_id)
);

CREATE TABLE city (
    city_id SMALLINT,
    city VARCHAR(50),
    country_id SMALLINT,
    last_update TIMESTAMP,
    PRIMARY KEY (city_id)
);

CREATE TABLE country (
    country_id SMALLINT,
    country VARCHAR(50),
    last_update TIMESTAMP,
    PRIMARY KEY (country_id)
);
```
2:
```
INSERT INTO country (country_id, country, last_update)
VALUES
    (1, 'Country 1', CURRENT_TIMESTAMP),
    (2, 'Country 2', CURRENT_TIMESTAMP),
    (3, 'Country 3', CURRENT_TIMESTAMP),

INSERT INTO city (city_id, city, country_id, last_update)
VALUES
    (1, 'City 1', 1, CURRENT_TIMESTAMP),
    (2, 'City 2', 1, CURRENT_TIMESTAMP),
    (3, 'City 3', 2, CURRENT_TIMESTAMP),

INSERT INTO address (address_id, address, address2, district, city_id, postal_code, phone, last_update)
VALUES
    (1, '123 Main St', 'Apt 4B', 'Downtown', 1, '12345', '555-123-4567', CURRENT_TIMESTAMP),
    (2, '456 Elm St', NULL, 'Suburb', 2, '67890', '555-987-6543', CURRENT_TIMESTAMP),
    (3, '789 Oak St', 'Unit 7', 'Downtown', 1, '54321', '555-789-0123', CURRENT_TIMESTAMP),
```


3:
```
SELECT
    co.country_id,
    co.country,
    ci.city_id,
    ci.city,
    a.address_id,
    a.address,
    a.address2,
    a.district,
    a.postal_code,
    a.phone
FROM country co
JOIN city ci ON co.country_id = ci.country_id
JOIN address a ON ci.city_id = a.city_id
LIMIT 20;
```

## Exercise 8
1:  
```
CREATE TABLE Salesman (
    salesman_id NUMERIC(5) PRIMARY KEY,
    name VARCHAR(30),
    city VARCHAR(15),
    commission DECIMAL(5,2)
);

CREATE TABLE Customer (
    customer_id NUMERIC(5) PRIMARY KEY,
    customer_name VARCHAR(30),
    city VARCHAR(15),
    grade NUMERIC(3)
);

CREATE TABLE Orders (
    ordern_num NUMERIC(5),
    purchase_amt DECIMAL(8,2),
    order_date DATE,
    customer_id NUMERIC(5),
    salesman_id NUMERIC(5),
    FOREIGN KEY (customer_id) REFERENCES Customer(customer_id),
    FOREIGN KEY (salesman_id) REFERENCES Salesman(salesman_id)
);
```

2:  
```
INSERT INTO Salesman (salesman_id, name, city, commission)
VALUES
    (1, 'John Doe', 'New York', 0.10),
    (2, 'Jane Smith', 'Los Angeles', 0.12),
    (3, 'Bob Johnson', 'Chicago', 0.08),
    (4, 'Alice Brown', 'San Francisco', 0.15);

INSERT INTO Customer (customer_id, customer_name, city, grade)
VALUES
    (101, 'ACME Inc.', 'New York', 1),
    (102, 'Widgets R Us', 'Los Angeles', 2),
    (103, 'Tech Solutions', 'Chicago', 1),
    (104, 'Global Traders', 'San Francisco', 3);

INSERT INTO Orders (ordern_num, purchase_amt, order_date, customer_id, salesman_id)
VALUES
    (1001, 5000.00, '2023-10-15', 101, 1),
    (1002, 3000.00, '2023-10-16', 102, 2),
    (1003, 8000.00, '2023-10-17', 103, 3),
    (1004, 12000.00, '2023-10-18', 104, 4);
```

3,4 & 5:  
```
SELECT DISTINCT customer_name
FROM Customer;

SELECT *
FROM Salesman
ORDER BY commission DESC;

SELECT MAX(purchase_amt) AS max_purchase_amt
FROM Orders;

SELECT MIN(purchase_amt) AS min_purchase_amt
FROM Orders;
```

