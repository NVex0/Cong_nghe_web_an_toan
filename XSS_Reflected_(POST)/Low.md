Thực hiện tương tự như XSS-R Get để kiểm tra web có vuln với XSS hay không.

Vì phương thức GET thì truyền dữ liệu thông qua URL, còn POST thì truyền dữ liệu thông qua phần thân các gói HTTP, nên nếu muốn xem payload, ta phải capture lại. Ở đây em dùng Wireshark:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/44e8eed8-381f-4c35-a986-1cff3eed92ab)

Ở đây ta thấy payload được post lên. Decode ra vì nó đang ở HTML encode:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/5939cfa5-2fa5-46ed-8762-15e4f795ada8)
