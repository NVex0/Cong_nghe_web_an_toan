Thực hiện như readme 1, ta sẽ thấy không thể truyền thẳng payload vào được, khi truyền payload vào ô bất kì đều không response lại:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/fc0ab482-b8fc-4918-a4a3-9a68ad2a92ea)

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/1bb60c0c-c28f-46a7-b96b-43c85d3cf9e6)

Có thể do cơ chế lọc chữ của web, ta thử bypass bằng ascii encode:

`<script>alert(String.fromCharCode(72,97,99,107,101,100))</script>`

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/1fa568a2-6831-42e7-92f9-734739dd17a7)

Web có vuln với XSS:

![image](https://github.com/NVex0/Cong_nghe_web_an_toan/assets/113530029/4b718a73-3f7b-49a7-9425-a82e079589d4)
