SELECT *
FROM user_profiles
WHERE name LIKE '%am%';
DESCRIBE cars;
DESCRIBE car_brands;
DESCRIBE car_models;

SELECT MAX(e.totalCost) AS max_expense
FROM expenses AS e
JOIN cars AS c ON e.carId = c.id
JOIN car_brands AS cb ON c.carBrandId = cb.id
WHERE cb.title = 'AUDI';
DESCRIBE car_brands;
DESCRIBE car_models;
DESCRIBE cars;

SELECT
	car_brands.title AS car_brand,
	COUNT(*) AS count_models,
  car_brands.id AS car_id
FROM car_models
JOIN car_brands ON
car_models.carBrandId = car_brands.id
WHERE car_brands.title IN ('AUDI', 'BMW')
GROUP BY car_brands.id, car_brands.title;

SELECT
	car_models.title AS car_model,
  car_brands.title AS car_brand,
  COUNT(DISTINCT cars.userId) AS user_count
FROM cars
JOIN car_models ON cars.carModelId = car_models.id
JOIN car_brands ON cars.carBrandId = car_brands.id
GROUP BY car_models.title, car_brands.title;

SELECT DISTINCT user_profiles.name
FROM user_profiles
JOIN cars ON user_profiles.userId = cars.userId;
