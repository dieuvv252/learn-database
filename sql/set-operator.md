# SET opeartors

## 1. UNION and UNION ALL

- `UNION` kết hợp 2 hoặc nhiều kết quả của câu lệnh `SELECT` vào 1 kết quả
- Để sử dụng UNION , viết những câu lệnh riêng lẻ và nối chúng bằng từ khoá **UNION**
- Mỗi câu lệnh `SELECT` phải có cùng số cột và kiểu dữ liệu ứng với từng cột
- Hệ thống cơ sở dữ liệu thực hiện 2 câu truy vấn trước , sau đó kết hợp kết quả thành 1 bảng duy nhất bằng cách loại bỏ các bản ghi trùng lặp
- Để giữ lại các bản ghi trùng lặp, ta sử dụng `UNION ALL` thay vì `UNION`
- ![hình minh hoạ union và unionall](/sql/img/union-union-all.png)

```
SELECT
    column1, column2
FROM
    table1
UNION [ALL]
SELECT
    column3, column4
FROM
    table2;
```
