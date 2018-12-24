# SQLtopForEachRow

SELECT *,

(SELECT Max(x)
        FROM (VALUES (Biology),(Physics),(Calculus)) AS Y(x) ) AS highest_grade,
        
(SELECT x
        FROM (VALUES (Biology),(Physics),(Calculus)) AS Y(x) ORDER BY x DESC OFFSET 1 ROWS FETCH next 1 ROWS ONLY ) AS second_highest_grade,
        
(SELECT x
        FROM (VALUES (Biology),(Physics),(Calculus)) AS Y(x) ORDER BY x DESC OFFSET 2 ROWS FETCH next 1 ROWS ONLY ) AS third_highest_grade


FROM
(SELECT *
FROM grades) AS T
