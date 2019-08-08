# SQL Everyday 문제풀이
## 08월 09일 까지

**LeetCode**
- [596. Classes More Than 5 Students](https://leetcode.com/problems/classes-more-than-5-students/)

```SQL
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student) >= 5 ;
```

- [595. Big Countries](https://leetcode.com/problems/big-countries/)

```SQL
SELECT name, population, area
FROM World
WHERE area > 3000000 OR population > 25000000 ;
```

- [620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies/)
```SQL
SELECT id, movie, description, rating
FROM cinema
WHERE MOD(id, 2) = 1
AND description != "boring"
ORDER BY rating DESC; 
```

- [197. Rising Temperature](https://leetcode.com/problems/rising-temperature/)
```SQL
# Write your MySQL query statement below
SELECT today.id
FROM Weather AS today
  INNER JOIN Weather As yesterday ON DATEDIFF(today.RecordDate, yesterday.RecordDate) = 1
     AND yesterday.Temperature < today.Temperature ;
```
-----------------------------------------

## **새롭게 알게 된 정보**
MySQL에서 두 날짜간의 차이를 가져올 때 사용하는 함수가 두 가지가 있습니다.

단순히 일 차이를 가져올 때 사용하는 것이 **DATEDIFF** 함수입니다.

이 외에도 차이를 연, 분기, 월, 주, 일, 시, 분, 초를 지정하여 가져올 때 사용하는 함수가 **TIMESTAMPDIFF** 함수입니다.


## 1. DATEDIFF
> DATEDIFF (날짜1, 날짜2);
* 간단히 말하자면 날짜1 - 날짜2 동작입니다.

## 2. TIMESTAMPDIFF
> TIMESTAMPDIFF (단위, 날짜1, 날짜2);

단위
* SECOND : 초
* MINUTE : 분
* HOUR : 시
* DAY : 일
* WEEK : 주
* MONTH : 월
* QUARTER : 분기
* YEAR : 연
