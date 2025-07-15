# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```
SELECT 
	ROUND(MAX(resale_price / floor_area_sqm ),0) AS max_price_per_sqm, 
	ROUND(MIN(resale_price / floor_area_sqm ),0) AS min_price_per_sqm
FROM main.resale_flat_prices_2017;

```

### Question 2

Select the average price per sqm for flats in each town.

```
SELECT town,	
	ROUND(AVG(resale_price / floor_area_sqm),0) AS avg_price_per_squm
FROM main.resale_flat_prices_2017
GROUP BY town;

```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```
SELECT CASE 
		WHEN resale_price < 400000 THEN '1 Budget'
		WHEN resale_price <= 700000 THEN '2 Mid-Range'
		ELSE '3 Premium'
	END AS flat_category,
	COUNT (*) AS num_flats
FROM main.resale_flat_prices_2017
GROUP BY flat_category
ORDER BY flat_category;

```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```
SELECT town, COUNT(*) AS unit_sold
FROM main.resale_flat_prices_2017
WHERE month IN('2017-01', '2017-02', '2017-03')
GROUP BY town
ORDER BY town;

```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
