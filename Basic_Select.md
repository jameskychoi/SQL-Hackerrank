### **[Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5)**

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

*Sample Input*

Let's say that CITY only has four entries: DEF, ABC, PQRS and WXY

*Sample Output*

ABC 3 

PQRS 4

*Explanation*

When ordered alphabetically, the CITY names are listed as ABC, DEF, PQRS, and WXY, with the respective lengths 3,3,4,3,3,4, and 33. The longest-named city is obviously PQRS, but there are 33 options for shortest-named city; we choose ABC, because it comes first alphabetically.

### **Solution**
```sql
SELECT CITY, length(CITY) 
FROM STATION 
ORDER BY length(CITY) ASC, CITY ASC LIMIT 1;

SELECT CITY, length(CITY) 
FROM STATION 
ORDER BY length(CITY) DESC, CITY ASC LIMIT 1;
```

### **[Weather Observation Station 6](https://www.hackerrank.com/challenges/weather-observation-station-6)**

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE "a%" OR CITY LIKE "e%" OR CITY LIKE "i%" OR CITY LIKE "o%" OR CITY LIKE "u%"
```
### **[Weather Observation Station 7](https://www.hackerrank.com/challenges/weather-observation-station-7)**

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE "%a" OR CITY LIKE "%e" OR CITY LIKE "%i" OR CITY LIKE "%o" OR CITY LIKE "%u"
```
### **[Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8)**

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY RLIKE '^[aeiouAEIOU].*[aeiouAEIOU]$';
/* note:
RLIKE is the regex LIKE, 
^ means starting
. means any character
* means multiple occurence of previous character, in this case the "." 
$ means closing
*/
```
### **[Weather Observation Station 9](https://www.hackerrank.com/challenges/weather-observation-station-9)**

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LEFT(CITY,1) NOT IN ('a','e','i','o','u','A','E','I','O','U')
```

### **[Weather Observation Station 10](https://www.hackerrank.com/challenges/weather-observation-station-10)**

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE RIGHT(CITY,1) NOT IN ('a','e','i','o','u')
```

### **[Weather Observation Station 11](https://www.hackerrank.com/challenges/weather-observation-station-11)**

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE RIGHT(CITY,1) NOT IN ('a','e','i','o','u') OR LEFT(CITY,1) NOT IN ('a','e','i','o','u','A','E','I','O','U')
```
### **[Weather Observation Station 12](https://www.hackerrank.com/challenges/weather-observation-station-12)**

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

**Input Format**

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

### **Solution**
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE RIGHT(CITY,1) NOT IN ('a','e','i','o','u') AND LEFT(CITY,1) NOT IN ('a','e','i','o','u','A','E','I','O','U')
```
------------------------------------------------------------------------------------------------------
### **[Higher Than 75 marks](https://www.hackerrank.com/challenges/more-than-75-marks/problem)**

Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

Input Format

The STUDENTS table is described as follows:

|  Column | Type |
|---|---|
| ID  | INTEGER |
| NAME | STRING   |
| MARKS  | INTEGER  |


The Name column only contains uppercase (A-Z) and lowercase (a-z) letters.

Sample Input

|  ID | NAME | MARKS |
|---|---|----|
| 1  | ASHLEY | 81 | 
| 2 | SAMANTHA   | 75 |
| 4  | JULIA  |  76 |
| 3  | JULIA  |  84 |

Sample Output

```sql
Ashley
Julia
Belvet
```

Explanation

Only Ashley, Julia, and Belvet have Marks > 75. If you look at the last three characters of each of their names, there are no duplicates and 'ley' < 'lia' < 'vet'.

### **Solution**
```sql
SELECT Name
FROM STUDENTS
WHERE Marks > 75
ORDER BY RIGHT(Name,3) ASC, ID ASC   
```
### **[Employee Names](https://www.hackerrank.com/challenges/name-of-employees/problem)**

Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Input Format

The Employee table containing employee data for a company is described as follows:

|  Column | Type |
|---|---|
| employee_id  | INTEGER |
| name | STRING   |
| months | INTEGER  |
| salary | INTEGER |

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.

Sample Input

|  employee_id | name | marks | salary  |
|---|---|----|-----|
| 12228 | Rose | 15 | 1968 |
| 33645 | Angela   | 1 | 3443 |
| 45692  | Frank  | 17  | 1608  |
| 56118  | Patrick  |  7 | 1345
| 59725 | Lisa | 11 | 2330 |
| 74197 | Kimberly   | 16 | 4372 |
| 78454  | Bonnie  |  8 | 1771 |
| 83565 | Michael |  6 | 2017
| 98607  | Todd  |  5 | 3396 |
| 99989 | Joe |  9 | 3573 |

Sample Output

```sql
Angela
Bonnie
Frank
Joe
Kimberly
Lisa
Michael
Patrick
Rose
Todd
```
**Solution**
```sql
SELECT name
FROM Employee
ORDER BY name ASC 
```
