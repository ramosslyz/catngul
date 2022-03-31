# WAF

## Pendeteksian
- Mengecek Cookie values, biasanya terdapat patern khusus pada cookie yang menandakan bahwa aplikasi menggunakan waf. contoh:<br><img width="500" src="https://user-images.githubusercontent.com/52058660/161025795-b8f751ce-bdaf-458e-8a2f-543d6ee84bd7.png">
- Rewrite header. contoh:<br><img width="500" src="https://user-images.githubusercontent.com/52058660/161026211-879c023a-9eb0-4f35-98a5-49c207829c79.png">
- Memodifikasi http response. Beberapa WAF memiliki response error yang unik. contoh:
  - ModSecurity -> 406 Not Acceptable
  - AQRONIX WebKnight -> 999 No hacking
- Jenis waf yang digunakan ada pada Response body.<br><img width="500" src="https://user-images.githubusercontent.com/52058660/161026998-b7c2bc3b-8ab9-4035-9a83-011fd54f85c4.png">
- Close Connection