## SQL Aggregate Functions

- Các hàm tổng hợp trong SQL cho phép thực hiện tính toán trên nhiều bản ghi và trả về một giá trị duy nhất.
- Có thể sử dụng aggregate functions trong `SELECT` và mệnh đề `HAVING`
- Một số hàm thường dùng:
- `COUNT(*)`: Đếm tổng số bản ghi
- `COUNT(column_name)`: Đếm số bản ghi có giá trị của cột column_name khác null
- `SUM(column_name)`: Tính tổng giá trị của cột column_name
- `AVG(column_name)`: Tính trung bình cộng của cột column_name
- `MAX(column_name)`: Tìm giá trị lớn nhất của cột column_name
- `MIN(column_name)`: Tìm giá trị nhỏ nhất của cột column_name
- `FIRST_VALUE(column_name)`: Trả về giá trị đầu tiên của cột column_name
- `LAST_VALUE(column_name)`: Trả về giá trị cuối cùng của cột column_name

#### 1.AVG

- Dùng để tính toán trung bình cộng của các giá trị trong một cột
- Mặc định AVG() sử dụng `ALL`
- AVG sẽ bỏ qua các giá trị **NULL**
- Nếu muốn tính trung bình của các giá trị duy nhất, ta có thể thêm từ khóa `DISTINCT` vào trước expression

```
AVG([ALL|DISTINCT] expression)
```

#### 2. MIN

- MIN() trả về giá trị nhỏ nhất của cột được chỉ định
- MIN sẽ bỏ qua các giá trị **NULL**
- `DISTINCT` không thể áp dụng cho MIN() vì nó chỉ trả về 1 giá trị.
- Cú pháp:

```
MIN(expression)
```

#### 3. COUNT

- COUNT() đếm số bản ghi trong bảng hoặc kết quả truy vấn
- COUNT(\*) đếm tất cả bản ghi bao gồm cả những bản ghi có giá trị NULL

```
COUNT([ALL | DISTINCT] expression);

ALL : trả về tất cả
DISTINCE : trả về số lượng giá trị duy nhất mà không tính giá trị trùng lặp
```

- Kết quả của `COUNT` phụ thuộc vào giá trị truyền vào

#### 4. SUM

- SUM() tính tổng của các giá trị trong một cột

## SQL GROUP DATA

#### 1. GROUP BY

- Dùng để nhóm dữ liệu theo một hoặc nhiều cột và thực hiện các hàm tổng hợp trên các nhóm đó.
- Khi sử dụng `GROUP BY` thì trong câu lệnh SELECT chỉ được lấy các cột nằm trong GROUP BY hoặc các hàm tổng hợp như COUNT(), SUM(), AVG(), MIN(), MAX()...

```
SELECT
	column1,
	column2,
	aggregate_function(column3)
FROM
	table_name
GROUP BY
	column1,
	column2;
```

#### 2. HAVING

- HAVING được sử dụng để lọc dữ liệu sau khi nhóm dữ liệu với GROUP BY
- Cú pháp:

```
SELECT
	column1,
	column2,
	AGGREGATE_FUNCTION (column3)
FROM
	table1
GROUP BY
	column1,
	column2
HAVING
	group_condition;
```

#### 3. ROLLUP

- ROLLUP được sử dụng để tính toán tổng cộng các nhóm con và tổng chung của các cột nhóm.

```
SELECT
    c1, c2, aggregate_function(c3)
FROM
    table_name
GROUP BY c1, c2 WITH ROLLUP;

```

#### 4. CUBE

- `CUBE` là một phần mở rộng của `GROUP BY` trong SQL , dùng để tạo ra các tổng hợp có thể từ những cột được chọn
