# Regular expression - Starting with AEIOU vowels
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```
select unique city from station where regexp_like (city,'^[^AEIOU]') or regexp_like (city,'[^aeiou]$');
```

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```
select unique city from station where regexp_like (city,'^[^AEIOU].+[^aeiou]$');
```
Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.
```
with salary as(
    select friends.id id,friend_id,salary from friends join packages on friends.id = packages.id
),
friendsalary as(
  select friends.id id,friend_id,salary as fri_sal from friends join packages on friends.friend_id = packages.id                       
),
salaries as(
    select salary.id id,salary.friend_id,salary,fri_sal from salary join friendsalary on salary.id = friendsalary.id
)
select name from students join salaries on students.id = salaries.id where fri_sal> salary  order by fri_sal;
```