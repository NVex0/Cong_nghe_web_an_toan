Thử nhập info vào form, ta thấy nó trả về thông tin ta nhập:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/40c9f97a-ca02-486e-89db-fe97075fcb13)

View source, để ý code sử dụng hàm eval lên đầu vào, rất nguy hiểm. Hàm eval được sử dụng lên `JSONResponseString`, ta bỏ qua các dòng dưới query đến tên phim bằng cách kết thúc chuỗi `JSONResponseString` và thẻ end javascript bằng payload `"}]}';alert("Hacked")</script>`:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/79b542de-e836-4bdb-a20c-ce8737cafc67)

-> Web có vuln với XSS.
