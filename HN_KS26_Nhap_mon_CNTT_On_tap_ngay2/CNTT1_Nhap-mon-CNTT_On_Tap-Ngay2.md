# BÀI LÀM – ÔN TẬP NGÀY 2


## Bài 1. Lọc log thủ công



### Lệnh đã chạy


grep "ERROR" logs/access.log > logs/error_report.txt
cat logs/error_report.txt

### 2 dòng lỗi đầu tiên trong error_report.txt



```
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline


### Lệnh


grep "WARNING" logs/access.log | wc -l
grep "ERROR" logs/payment.log | wc -l

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)


```
WARNING trong access.log: 4
ERROR trong payment.log: 3

```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)
### Nội dung script sau khi hoàn thiện:
#Script: auto_warning.ps1
#Tac gia: Hoàng Văn Trái 
 #Ngay tao: 21/10/2026 Write-Host "Dang loc canh bao thanh toan..." "=== CANH BAO THANH TOAN ===" > logs/warning_report.txt Get-Content logs/payment.log | Select-String "WARNING" >> logs/warning_report.txt Write-Host "Hoan thanh!
 ### Cách chạy script từ thư mục gốc:
 - .\auto_warning.ps1 Get-Content logs/warning_report.txt






## Bài 4. Báo cáo tổng hợp



### - Các lệnh đã chạy


echo "=== TONG HOP ACCESS LOG ===" > logs/tong_hop_ngay2.txt
grep "ERROR" logs/access.log >> logs/tong_hop_ngay2.txt
grep "WARNING" logs/payment.log | wc -l >> logs/tong_hop_ngay2.txt



## Bài 5. Câu hỏi ngắn



-   **a)** Dấu `>` dùng để ghi mới, nếu trong file đã có chữ thì xoá sạch rồi mới ghi nội dung mới vào. Dấu `>>` giữ lại nội dung cũ và viết nối tiếp phần mới vào cuối file
-   **b)** File sẽ mất dòng tiêu đề `=== TONG HOP ACCESS LOG ===` mà lệnh 1 vừa ghi, vì lệnh thứ 2 đã dùng dấu `>`nên nó đã xoá sạch nội dung cũ. File còn lại chỉ có 6 dòng ERROR mà không có tiêu đề.
-   **c)** Vì đường dẫn tuyệt đối gắn chặt với từng máy, /Users/traihoang/... chỉ đúng với máy mình, nếu sang máy khác là máy đó không tìm thấy file và báo lỗi. Dùng đường dẫn tương đối logs/payment.log thì nó tính từ thư mục hiện tại, chỉ cần giữ nguyên thư mục là sang máy nào cũng chạy được, khi nộp và chia sẻ cho người khác cũng không cần phải sửa lại đường dẫn
