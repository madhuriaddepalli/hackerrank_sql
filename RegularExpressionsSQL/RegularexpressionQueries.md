# Regular expression - Starting with AEIOU vowels
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```
select unique city from station where regexp_like (city,'^[^AEIOU]') or regexp_like (city,'[^aeiou]$');
```

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```
select unique city from station where regexp_like (city,'^[^AEIOU].+[^aeiou]$');
```
