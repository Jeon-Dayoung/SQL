# SQL Everyday 문제풀이
## 08월 14일 까지

**hackerrank**
- [The Report](https://www.hackerrank.com/challenges/the-report/problem)
```SQL
#왜 null이 'null' 이 되면 안될까? : null은 예약어라서 저렇게 쓰면 정말 비어있는 건데, 'null'이라고 되면 str 문자 처리가 된다

SELECT (CASE
        WHEN g.grade<8 THEN null ELSE s.name END) as name
    ,g.grade,s.marks
FROM students AS s
    INNER JOIN grades AS g ON s.marks BETWEEN min_mark AND max_mark
ORDER BY g.grade DESC, name, s.marks;
```
**if 문을 이용한 풀이**
```SQL
SELECT
    IF (g.grade >= 8, s.name, NULL) # if문이 세가지 조건: 조건, 조건을 만족할 때 나오는 요소, 아닐 때 나오는 요소를 표시해주면 됨
    , g.grade
    , s.marks
FROM students s
    INNER JOIN grades g ON s.marks BETWEEN min_mark AND max_mark
ORDER BY g.grade DESC, name,s.marks;
```