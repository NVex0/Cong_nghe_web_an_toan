App cũ quá nên khi em query thì lỗi hàm do cái app xài php cũ quá, các hàm sql đến PHP ver 7 là bị xóa, thay thế bằng hàm sqli:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/26184f21-e9fd-4f37-8868-36d9616d6228)

Mà em cũng không tìm được các bản cũ hơn nên em đọc source làm chay:

Đầu tiên, file `xss_href-1.php` xử lý thông tin nhập vào từ ô trống bằng file `xss_href-2.php`. Vào file đó, ta biết được cái ô trống điền bất kì cái gì cũng được, khác "" là được:

`if(isset($_GET["name"]) and $_GET["name"] != "")`

Tức là không có cơ chế lọc đầu vào ở đây. Kế tiếp là trả về msg là biến $name, chính là đầu vào chúng ta nhập:

```
{

    $name = $_GET["name"];

    $message = "<p>Hello " . ucwords(xss_check_3($name)) . ", please vote for your favorite movie.</p>";
    $message.= "<p>Remember, Tony Stark wants to win every time...</p>";

}
```

Sau đó gọi tới `xss_href-3.php` với các tham số đầu vào:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/c73b07bb-34bd-400a-b6ea-3f2b435067da)

Vì không có cơ chế lọc ký tự, ta sẽ tiến hành exploit bằng cách ngắt href và truyền payload vào sau:

`><script>alert('Hacked by Tran Manh Hung.')</script>`
