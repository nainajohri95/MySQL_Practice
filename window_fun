CREATE DATABASE IF NOT EXISTS windowdb;
use windowdb;
CREATE TABLE DATA(
new_id int,
new_cat VARCHAR(20)
);

INSERT INTO DATA VALUES 
(100, 'Agni'),
(200, 'Agni'),
(500, 'Dharti'),
(700, 'Dharti'),
(200, 'Vayu'),
(300, 'Vayu'),
(500, 'Vayu');


-- 	Aggregate  window fun

-- Partition By
SELECT new_id, new_cat,
SUM(new_id) OVER(PARTITION BY new_cat) AS "Total",
AVG(new_id) OVER(PARTITION BY new_cat) AS "Average",
COUNT(new_id) OVER(PARTITION BY new_cat) AS "Count",
MIN(new_id) OVER(PARTITION BY new_cat) AS "Min",
MAX(new_id) OVER(PARTITION BY new_cat) AS "Max"
FROM DATA;

-- Rows
SELECT new_id, new_cat,
SUM(new_id) OVER(ORDER BY new_id ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS "Total",
AVG(new_id) OVER(ORDER BY new_id ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS "Average",
COUNT(new_id) OVER(ORDER BY new_id ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS "Count",
MIN(new_id) OVER(ORDER BY new_id ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS "Min",
MAX(new_id) OVER(ORDER BY new_id ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS "Max"
FROM DATA;

-- Rank
SELECT new_id,
ROW_NUMBER() OVER(ORDER BY new_id) AS "Row_Number",
Rank() OVER(ORDER BY new_id) AS "Rank",
DENSE_RANK() OVER(ORDER BY new_id) AS "Dense_Rank",
PERCENT_RANK() OVER(ORDER BY new_id) AS "Percent_Rank"
FROM DATA;

-- Analytic function
-- Ifwe dont use any Partition BY or ROWS Clause then in case of LAST_VALUE we will get same col value 
-- If we actually want the LAST_VALUE We should use ROWS BETWWEN/ UNBOUNEDE PRECEDING/ UNBOUBDED FOLLOWING
SELECT new_id,
FIRST_VALUE(new_id) OVER(ORDER BY new_id) AS "FIRST VALUE",
LAST_VALUE(new_id) OVER(ORDER BY new_id) AS "LAST VALUE",
LEAD(new_id) OVER(ORDER BY new_id) AS "LEAD",
LAG(new_id) OVER(ORDER BY new_id) AS "LAG"
FROM DATA;

-- QUE Offset the LEAD and LAG value by 2 in the o/p column
SELECT new_id,
LEAD(new_id,2) OVER(ORDER BY  new_id) AS "LEAD_BY2",
LAG(new_id,2) OVER(ORDER BY new_id) AS "LAG_BY2"
FROM DATA;
