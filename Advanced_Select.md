### **[Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle/problem)**

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

    Equilateral: It's a triangle with sides of equal length.
    Isosceles: It's a triangle with sides of equal length.
    Scalene: It's a triangle with sides of differing lengths.
    Not A Triangle: The given values of A, B, and C don't form a triangle.

**Input Format**

The TRIANGLES table is described as follows:

|  Column | Type |
|---|---|
| A  | INTEGER |
| B | INTEGER  |
| C  | INTEGER |

Each row in the table denotes the lengths of each of a triangle's three sides.

*Sample Input*

| A | B | C|
|---|---|---|
| 20|20|23|
|20|20|20|
|20|21|22|
|13|14|30|

*Sample Output*

```sql
Isosceles
Equilateral
Scalene
Not A Triangle
```
*Explanation*

Values in the tuple $(20,20,23)$ form an Isosceles triangle, because $A \equiv B$.
Values in the tuple $(20,20,20)$ form an Equilateral triangle, because $A \equiv B \equiv C$ . Values in the tuple $(20,21,22)$ form a Scalene triangle, because $A \neq B \neq C $.
Values in the tuple $(13,14,30)$ cannot form a triangle because the combined value of sides $A$ and $B$ is not larger than that of side $C$ .
### **Solution**
```sql
SELECT 
CASE 
  WHEN A + B > C AND A + C > B AND B + C > A THEN
    CASE 
      WHEN A = B AND B = C THEN "Equilateral"
      WHEN A = B OR B = C OR C = A THEN "Isosceles"
      WHEN A <> B AND B <> C THEN "Scalene"
    END
  ELSE "Not A Triangle" 
END 
FROM TRIANGLES
```

### **[The PADS](https://www.hackerrank.com/challenges/the-pads/problem)**

Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).

Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format: 

```sql
There are a total of [occupation_count] [occupation]s.
```
 where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.  

Note: There will be at least two entries in the table for each type of occupation.

**Input Format**
The OCCUPATIONS table is described as follows: 
|  Column | Type |
|---|---|
| Name | String |
| Occupation | String |

Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

Sample Input

An OCCUPATIONS table that contains the following records:

*Sample Input*

| Name | Occupation |
|---|---|
|Samantha|Doctor|
| Julia|Actor|

*Sample Output*

```sql
Ashely(P)
Christeen(P)
Jane(A)
Jenny(D)
Julia(A)
Ketty(P)
Maria(A)
Meera(S)
Priya(S)
Samantha(D)
There are a total of 2 doctors.
There are a total of 2 singers.
There are a total of 3 actors.
There are a total of 3 professors.
```
*Explanation*

The results of the first query are formatted to the problem description's specifications.
The results of the second query are ascendingly ordered first by number of names corresponding to each profession $(2 \geq 2 \geq 3 \geq 3)$
), and then alphabetically by profession $(doctor <= singer\, and\ actor <= professor)$.

### **Solution**
```sql
SELECT CONCAT(Name,'(', LEFT(Occupation,1), ')')
FROM OCCUPATIONS
ORDER BY Name;

SELECT CONCAT('There are a total of ',COUNT(Occupation),' ',LOWER(Occupation),'s.')
FROM OCCUPATIONS
GROUP BY Occupation
ORDER BY COUNT(Occupation), Occupation;
```
