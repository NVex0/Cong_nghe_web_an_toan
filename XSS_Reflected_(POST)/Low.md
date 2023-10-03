Thực hiện tương tự như XSS-R Get để kiểm tra web có vuln với XSS hay không.

Vì phương thức GET thì truyền dữ liệu thông qua URL, còn POST thì truyền dữ liệu thông qua phần thân các gói HTTP, nên nếu muốn xem payload, ta phải capture lại. Ở đây em dùng Wireshark:


