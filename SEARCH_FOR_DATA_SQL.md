SELECT userId, name, lastName
FROM user_profiles
WHERE name LIKE '%am%';

SELECT MAX(expenses.totalCost) AS maxexpense
FROM expenses
JOIN cars ON expenses.carId = cars.id
JOIN car_brands ON cars.carBrandId = car_brands.id
WHERE car_brands.title = 'AUDI';

SELECT car_brands.title AS car_brand,
	COUNT(car_models.id) AS count_models,
	car_brands.id AS car_id
FROM car_models
JOIN car_brands ON car_models.carBrandId = car_brands.id
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

SELECT DISTINCT name
FROM user_profiles
WHERE userId IN (
	SELECT userId
    FROM cars
    );
