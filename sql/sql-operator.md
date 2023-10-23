## SQL Case

- `SQL CASE` cho phép tính toán 1 danh sách của điều kiện và trả về 1 kết quả đáp ứng đủ điều kiện
- `CASE` có 2 định dạng : **simple CASE** và **searched CASE**

#### 1. Simple CASE expression

```
CASE expression
WHEN when_expression_1 THEN
	result_1
WHEN when_expression_2 THEN
	result_2
WHEN when_expression_3 THEN
	result_3
...
ELSE
	else_result
END
```

```
SELECT
    first_name,
    last_name,
    hire_date,
    CASE (2000 - YEAR(hire_date))
        WHEN 1 THEN '1 year'
        WHEN 3 THEN '3 years'
        WHEN 5 THEN '5 years'
        WHEN 10 THEN '10 years'
        WHEN 15 THEN '15 years'
        WHEN 20 THEN '20 years'
        WHEN 25 THEN '25 years'
        WHEN 30 THEN '30 years'
    END year_join
FROM
    employees
ORDER BY first_name;
```

- `CASE` so sánh 1 giá trị của biếu thức với tập giá trị của biểu thức điều kiện sử dụng toán tử (=)
- `CASE` trả về các kết quả result_1, result_2 , result_3 . Nếu biểu thức đúng
- Nếu không có kết quả nào thoả mãn điều kiện thì sẽ trả về mệnh đề **ELSE**
- Nếu bỏ qua mệnh đề **ELSE** sẽ trả về giá trị `NULL`
- Có thể sử dụng biểu thức CASE trong các câu lệnh như **SELECT**, **DELETE** và **UPDATE** hoặc trong các mệnh đề như **SELECT**, **ORDER BY** và **HAVING**.

#### 2. Searched CASE expression

- Hoạt động tương tự như simple CASE expression

```
CASE
WHEN boolean_expression_1 THEN
	result_1
WHEN boolean_expression_2 THEN
	result_2
WHEN boolean_expression_3 THEN
	result_3
ELSE
	else_result
END;
```

```
SELECT
     first_name ,
     last_name ,
     salary,
     CASE
          WHEN salary < 3000 THEN 'thap'
          WHEN salary >= 3000 AND salary <= 5000 THEN 'trungbinh'
          ELSE 'cao'
     END danhgia

FROM
     employees;
```

## SQL Alias

- Cho phép gán 1 table hoặc 1 column với 1 tên tạm thời trong thời gian thực hiện câu lệnh truy vấn
- Có 2 loại Alias : **table** và **column**

```
column_name AS 'Alias Name'
```

## INNER JOIN

- Trả về tất cả bản ghi từ cả 2 bảng được nối khi có ít nhất một bản ghi ở cả 2 bảng
- Điều kiện nối sau `ON`
- Có thể thực hiện `INNER JOIN` trên nhiều mảng

```
SELECT
  A.n
FROM A
INNER JOIN B ON B.n = A.n
INNER JOIN C ON C.n = A.n;
```

```
SELECT
     e.employee_id ,
     e.first_name ,
     e.last_name ,
     e.job_id ,
     j.job_id ,
     j.job_title ,
     e.department_id ,
     d.department_id ,
     d.department_name
FROM
     employees e
     INNER JOIN
     departments d ON e.department_id  = d.department_id
     INNER JOIN
     jobs j ON e.job_id = e.job_id
WHERE
     e.department_id IN (1,2,3)
ORDER BY
     j.job_id DESC;
```

## LEFT JOIN

- Trả về tất cả bản ghi từ bảng bên trái và các bản ghi tương ứng từ bảng bên phải. Nếu không có bản ghi tương ứng, các cột từ bảng bên phải sẽ có giá trị NULL.
- LEFT JOIN nhiều bảng sẽ JOIN các kết quả trước đó với các bảng tiếp theo theo thứ tự từ trái sang phải.

```
SELECT
	A.n
FROM
	A
LEFT JOIN B ON B.n = A.n;
```

```
SELECT
     r.region_name  ,
     c.country_name ,
     l.street_address
FROM
     regions r
     LEFT JOIN countries c ON r.region_id = c.region_id
     LEFT JOIN locations l ON l.country_id  = c.country_id
```

## RIGHT JOIN

- Trả về tất cả bản ghi từ bảng bên phải và các bản ghi tương ứng từ bảng bên trái. Nếu không có bản ghi tương ứng, các cột từ bảng bên trái sẽ có giá trị NULL.
- Cú pháp tương tự LEFT JOIN nhưng bảng bên phải sẽ là bảng chính và bảng bên trái sẽ được LEFT JOIN vào bảng bên phải.

```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;

The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
```

## FULL OUTER JOIN

- Trả về tất cả bản ghi từ cả 2 bảng dù có hay không có bản ghi phù hợp. Nếu không có bản ghi phù hợp, các cột từ bảng không phù hợp sẽ có giá trị NULL.

```
SELECT column_list
FROM A
FULL OUTER JOIN B ON B.n = A.n;
```

## SELF JOIN

- Cho phép join 1 bảng với chính nó
- Sử dụng `INNER JOIN` hoặc `LEFT JOIN` với điều kiện join trên các cột khác nhau trong cùng 1 bảng
- Sử dụng trong mối quan hệ đệ quy và phân cấp

```
SELECT
	column1,
	column2,
	column3,
        ...
FROM
	table1 A
INNER JOIN table1 B ON B.column1 = A.column2;
```

```
SELECT
    e.first_name || ' ' || e.last_name AS employee,
    m.first_name || ' ' || m.last_name AS manager
FROM
    employees e
        LEFT JOIN
    employees m ON m.employee_id = e.manager_id
ORDER BY manager;
```
