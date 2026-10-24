CREATE DATABASE qaAuto;
USE qaAuto;
CREATE TABLE car_brands (
id INT AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(100) NOT NULL
);
SHOW TABLES;
DESCRIBE car_brands;
CREATE TABLE car_models (
id INT AUTO_INCREMENT PRIMARY KEY,
carBrandID INT NOT NULL,
FOREIGN KEY (carBrandId) REFERENCES car_brands(id)
);
CREATE TABLE users (
id INT AUTO_INCREMENT PRIMARY KEY,
firstName VARCHAR(100) NOT NULL,
lastName VARCHAR(100) NOT NULL,
email VARCHAR(150) NOT NULL,
password VARCHAR(150) NOT NULL
);
CREATE TABLE cars (
id INT AUTO_INCREMENT PRIMARY KEY,
userID INT NOT NULL,
carBrandId INT NOT NULL,
carModelId INT NOT NULL,
mileage INT NOT NULL,
FOREIGN KEY (userId) REFERENCES users(id),
FOREIGN KEY (carBrandId) REFERENCES car_brands(id),
FOREIGN KEY (carModelId) REFERENCES car_models(id)
);
SHOW TABLES;
INSERT INTO car_brands (title)
VALUES
	('Audi'),
    ('BMW'),
    ('Ford');
    SELECT * FROM car_brands;
    DESCRIBE car_models;
    ALTER TABLE car_models
    ADD COLUMN title VARCHAR(100) NOT NULL;
    DESCRIBE car_models;
    INSERT INTO car_models (carBrandId, title)
    VALUES
    (1, 'TT'),
    (1, 'Q7'),
    (2, '3'),
    (2, 'X5'),
    (3, 'Fiesta'),
    (3, 'Focus');
    SELECT * FROM car_models;
    INSERT INTO users (firstName, lastName, email, password)
    VALUES
		    ('Iryna', 'Ko', 'Iryna.K@example.com', 'Test12345'),
        ('Sasha', 'Sa', 'Saha.S@example.com', 'Test54321');
	SELECT * FROM users;
    ALTER TABLE cars
    ADD COLUMN initialMileage INT NOT NULL;
    SELECT * FROM cars;
    SELECT * FROM users;
    INSERT INTO cars (userID, carBrandId, carModelId, mileage, initialMileage)
    VALUES
		    (1, 1, 1, 45000, 40000),
        (1, 3, 5, 70000, 65000),
        (2, 2, 4, 62000, 60000),
        (2, 3, 6, 80000, 75000);
        SELECT * FROM cars;
