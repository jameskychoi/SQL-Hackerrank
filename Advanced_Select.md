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

Explanation

Values in the tuple $(20,20,23)$
form an Isosceles triangle, because .
Values in the tuple form an Equilateral triangle, because . Values in the tuple form a Scalene triangle, because .
Values in the tuple cannot form a triangle because the combined value of sides and is not larger than that of side .
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