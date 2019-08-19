# SQL Everyday 문제풀이
## 08월 19일 까지

**hackerrank**
- [Challenges](https://www.hackerrank.com/challenges/challenges/problem)


```SQL
SELECT h.hacker_id, 
       h.name, 
       COUNT(c.challenge_id) AS c_count
FROM Hackers h
JOIN Challenges c ON c.hacker_id = h.hacker_id
GROUP BY h.hacker_id, h.name
HAVING c_count = 
    (SELECT COUNT(c2.challenge_id) AS c_max
     FROM challenges as c2 
     GROUP BY c2.hacker_id 
     ORDER BY c_max DESC limit 1)
OR c_count IN 
    (SELECT DISTINCT c_compare AS c_unique
     FROM (SELECT h2.hacker_id, 
                  h2.name, 
                  COUNT(challenge_id) AS c_compare
           FROM Hackers h2
           JOIN Challenges c ON c.hacker_id = h2.hacker_id
           GROUP BY h2.hacker_id, h2.name) counts
     GROUP BY c_compare
     HAVING COUNT(c_compare) = 1)
ORDER BY c_count DESC, h.hacker_id;
```

- [Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem?h_r=next-challenge&h_v=zen)

```SQL
select h.hacker_id, name, sum(score) as total_score
from
hackers as h inner join
/* find max_score*/
(select hacker_id,  max(score) as score from submissions group by challenge_id, hacker_id) max_score

on h.hacker_id=max_score.hacker_id
group by h.hacker_id, name

/* don't accept hackers with total_score=0 */
having total_score > 0

/* finally order as required */
order by total_score desc, h.hacker_id
;
```
- [Symmetric Pairs](https://www.hackerrank.com/challenges/symmetric-pairs/problem?h_r=internal-search)

```SQL
(select f1.x as x, f1.y as y
from Functions as f1
join Functions as f2
where f1.x = f2.y and f1.y = f2.x and f1.x != f1.y and f1.x < f1.y)

union

(select x as x, y
from Functions as f1
group by x, y
having count(*) > 1)
order by x asc
```
-------------------------------------