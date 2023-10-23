# Giới thiệu về SQL

- Tự đọc : **https://www.sqltutorial.org/**

# Sql syntax

- Một câu lệnh sql được bắt đầu với 1 động từ : Select , Insert, Update, Delete, ...
- Mỗi câu lệnh sql kết thúc bằng dấu **;**
- Mỗi câu lệnh bao gồm : giá trị cụ thể , từ khoá ( ví dụ như Select , Where , ...) , định danh (các bảng) , biểu thức

```
SELECT
    first_name, last_name
FROM
    employees;

DELETE FROM employees
WHERE
    hire_date < '1990-01-01';
```

### 1. Literals (Giá trị cụ thể )

- SQL cung cấp 3 loại giá trị : string , number , binary
- Ví dụ string

```
'John'
'1990-01-01'
'50'
```

- **Chú ý** : SQL phân biệt chữ hoa và chữ thường. Ví dụ 'John' khác với 'JOHN'.Vì thế 2 giá trị không bằng sau

- Ví dụ number

```
200
-5
6.0221415E23
```

- Ví dụ binary

```
x'01'
x'0f0ff'

```

### 3. Comment

- Sử dụng '--' để viết 1 comment

```
SELECT
    employee_id, salary
FROM
    employees
WHERE
    salary < 3000;-- employees with low salary
```
