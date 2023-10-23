# WINDOW FUNCTION trong sql

- window funtion là một tập hợp các hàm cho phép thực hiện phép tính trên một tập dữ liệu liên quan đến một cửa sổ di chuyển dọc theo dữ liệu. Có các hàm window function phổ biến như:
- **rank()** : Xếp hạng các giá trị trong một cửa sổ theo thứ tự tăng dần hoặc giảm dần
- **dense_rank()** : Tương tự rank() nhưng không bỏ qua các giá trị trùng nhau
- **first_value()** : Trả về giá trị đầu tiên trong cùng cửa sổ dữ liệu
- **last_value()**: Trả về giá trị cuối cùng trong cùng cửa sổ dữ liệu
- **partition by** : Dùng thể thực hiện các phép tính trên các nhóm dữ liệu được phân chia theo các cột được chỉ định mà không cần dùng đến sub query và các truy vấn phức tạp khác
- **lead()** : Trả về giá trị của hàng tiếp theo dựa trên cột được chỉ định và số lượng bản ghi được chuyển tiếp
- **lag()** : Trả về giá trị của hàng trước đó dựa trên cột đuọc chỉ định
- **row_number()** : Sẽ gán 1 số thứ tự nhất định cho tập kết quả
