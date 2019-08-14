# SQL Everyday 문제풀이
## 08월 13일 까지

**hackerrank**
- [Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle/problem)
```python
SELECT 
  CASE
    WHEN A+B<=C OR A+C<=B OR C+B<=A THEN "Not A Triangle"
    WHEN A=B and B=C THEN "Equilateral"
    WHEN A=B or B=C or C=A THEN "Isosceles"
    ELSE "Scalene"
  END AS answer
 FROM TRIANGLES
```
- [Top Earners](https://www.hackerrank.com/challenges/earnings-of-employees/problem?h_r=internal-search)
```python
SELECT salary * months AS earnings, COUNT(*)
FROM Employee
GROUP BY earnings
ORDER BY earnings DESC
LIMIT 1;
```
```python
SELECT MAX(salary * months) , COUNT(employee_id)
FROM Employee
WHERE month * salary =
     (SELECT MAX(month * salary)
      FROM Employee)
GROUP BY months * salary 
```
---------------------------------

