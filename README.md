## Phần 1:Phân tích

-Trong mã nguồn AI gợi ý cho có 3 tham số:

-Path:Xác định đường dẫn đến tệp hoặc thư mục cần xóa. 

-Recurse:Cho phép xóa đệ quy, nghĩa là xóa toàn bộ thư mục con và các tệp bên trong nó (thường dùng khi xóa thư mục). 

-Force:Buộc xóa cả các tệp đang bị ẩn, tệp chỉ đọc (read-only), hoặc tệp đang bị khóa. 

—-->Khi kết hợp cả 3 tham số này và chạy script như AI gợi ý thì sẽ khiến cưỡng chế xóa toàn bộ ổ C → gây sập hệ → làm hỏng hệ điều hành

## Phần 2: Triển khai

#Di chuyển tới log

cd logs

#Hiển thị thông báo lên màn hình

write-host "Hệ thống dọn tệp cũ"

#Thông báo đang chạy

write-host "đang tìm WARNING"

select-string "WARNING" system.log | out-file issues.txt

#Xóa tệp

remove-item *.tmp

#Thông báo hoàn thành

write-host "đã xong"

## Phần 3: Kiểm thử (Verify)

Dùng lệnh Get-Content issues.txt để xem nội dung tệp báo cáo vừa lọc.

Cách kiểm tra thành công: Xuất hiện danh sách các dòng chứa từ khóa WARNING trên màn hình.

Dùng lệnh Get-ChildItem để liệt kê lại thư mục dự án.

Cách kiểm tra thành công: Các tệp có phần mở rộng .tmp đã biến mất khỏi danh sách.

Dùng lệnh Test-Path issues.txt để kiểm tra sự tồn tại của tệp báo cáo.

Cách kiểm tra thành công: Trả về kết quả True.
