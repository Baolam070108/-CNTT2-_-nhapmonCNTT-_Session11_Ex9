# -CNTT2-_-nhapmonCNTT-_Session11_Ex9
Phần 1: Phân tích bài toán (I/O)
1. Xác định các thành phần VLOOKUP
Thành phần	Ý nghĩa / Giá trị
Lookup_value	Mã tác giả ở cột C của sheet DanhSachBaoCao, dùng TRIM để bỏ khoảng trắng thừa.
Table_array	Vùng $A$2:$E$81 trong sheet DanhMucTacGia, được cố định bằng dấu $.
Col_index_num cột D	2 – lấy Tên tác giả.
Col_index_num cột E, F	4 – lấy Phòng; 5 – lấy Thù lao.
2. Chiến lược xử lý 3 bẫy dữ liệu
- Bẫy 1 – Khoảng trắng: Dùng TRIM(C2) để loại bỏ khoảng trắng thừa trong mã tác giả.
- Bẫy 2 – Không tìm thấy mã: Dùng IFERROR(...,"Chưa cập nhật") để thay lỗi #N/A bằng thông báo dễ hiểu.
- Bẫy 3 – Vùng tra cứu bị trôi: Dùng $A$2:$E$81 để cố định vùng dữ liệu khi kéo công thức xuống các dòng dưới.
3. Các bước thực hiện trong Excel
1. Mở sheet DanhSachBaoCao, xác định cột C chứa mã tác giả.
2. Tại ô D2, nhập công thức VLOOKUP kết hợp TRIM và IFERROR.
3. Cố định vùng tra cứu của sheet DanhMucTacGia bằng dấu $.
4. Sao chép công thức từ D2 xuống D81.
5. Tại ô E2 và F2, nhập công thức tương tự, thay chỉ số cột cần lấy dữ liệu.
6. Kéo công thức xuống các dòng còn lại và kiểm tra các trường hợp hiện Chưa cập nhật.
Phần 2: Triển khai và chống lỗi
4. Công thức ô D2 – Tên tác giả
=IFERROR(VLOOKUP(TRIM(C2),DanhMucTacGia!$A$2:$E$81,2,FALSE),"Chưa cập nhật")


Giải thích:
- TRIM(C2): loại bỏ khoảng trắng thừa trong mã tác giả.
- DanhMucTacGia!$A$2:$E$81: lấy dữ liệu tra cứu từ sheet DanhMucTacGia và cố định vùng.
- 2: trả về tên tác giả ở cột thứ 2 trong vùng tra cứu.
- FALSE: yêu cầu tìm mã khớp chính xác.
- IFERROR: hiển thị Chưa cập nhật nếu xảy ra lỗi tra cứu.
5. Công thức ô E2 và F2
Ô E2 – Phòng trình bày:
=IFERROR(VLOOKUP(TRIM(C2),DanhMucTacGia!$A$2:$E$81,4,FALSE),"Chưa cập nhật")


Ô F2 – Thù lao:
=IFERROR(VLOOKUP(TRIM(C2),DanhMucTacGia!$A$2:$E$81,5,FALSE),"Chưa cập nhật")


- Cả ba công thức đều tìm theo mã tác giả ở cột C và sử dụng cùng vùng tra cứu. Chỉ cần thay Col_index_num từ 2 thành 4 hoặc 5 để lấy dữ liệu ở cột Phòng hoặc Thù lao, không cần viết lại logic tra cứu.
6. Điều gì xảy ra nếu bỏ dấu $?
Nếu công thức D2 sử dụng vùng tương đối DanhMucTacGia!A2:E81, khi kéo công thức xuống, vùng tra cứu sẽ tự dịch chuyển theo số dòng.

