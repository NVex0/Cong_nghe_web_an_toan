Thử nhập vào 2 box nhập họ tên, ta thấy có response lại là 1 message chào họ tên ta vừa nhập:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/901302a7-0605-4af3-8568-f801acc22ddb)

Để ý trên URL, 2 trường này được GET toàn bộ thông tin ta nhập vào rồi trả về đúng như thế. Có thể thử thêm bằng bôi đen:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/01069ea9-0246-489f-87b7-0ac861c09285)

Như vậy ta đoán được web vulnerable với XSS, thử truyền vào javascript `<script>alert("Hacked")</script>`:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/9333478e-3959-4351-a3d2-395854fa816b)
