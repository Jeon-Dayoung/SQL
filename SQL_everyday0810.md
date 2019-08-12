# SQL Everyday 문제풀이
## 08월 12일 까지

**LeetCode**
- [184. Department Highest Salary](https://leetcode.com/problems/department-highest-salary/)

```SQL
SELECT
    d.name AS 'Department',
    e.name AS 'Employee',
    Salary
FROM
    Employee AS e
    INNER JOIN Department AS d ON e.DepartmentId = d.Id
WHERE
    (e.DepartmentId , Salary) IN
    (   SELECT
            DepartmentId, MAX(Salary)
        FROM
            Employee
        GROUP BY DepartmentId
	)
;
```

- [180. Consecutive Numbers](https://leetcode.com/problems/consecutive-numbers/)

```SQL
SELECT df.department as department,
       e.name as employee,
       e.salary as salary
FROM (SELECT d.name as department,
            d.Id AS Id,
            MAX(salary) AS salary
      FROM employee as e
      INNER JOIN department AS d
      ON e.departmentId = d.Id
      GROUP BY d.name) AS df
  INNER JOIN employee as e
  ON e.departmentId = df.Id
WHERE e.salary = df.salary
```


-----------------------------------------

## **새롭게 알게 된 정보**
## Pandas 복습하기

## 1. median
> [1, 2, 3, ``` 10]일 때, 5+6/2
* 간단히 말하자면 중간값 두 개를 더해서 나온 평균값을 알려줍니다.

## 2. tips['smoker'].unique
* smoker에 해당되는 내용만 표시합니다.

## 3. tips(tips['smoker'] == 'Yes')
* 'Yes'인 값만 보여줍니다.

## 4. tips.groupby(['day','sex'])['total_bill'].sum().reset_index
* 원하는 테이블을 엮어서 'total_bill'과 총값을 알려줍니다.