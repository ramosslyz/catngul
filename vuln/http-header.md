# HTTP HEADER INJECTION
## Cara Identifikasi
  - [How to identify and exploit HTTP Host header vulnerabilities](https://portswigger.net/web-security/host-header/exploiting)
  - [Rewinding Back to the Basics — Injection Attack Series](https://medium.com/@vanessamorales.1023/rewinding-back-to-the-basics-injection-attack-series-226d35d7994e)
  - [Testing for Bypassing Authorization Schema](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/05-Authorization_Testing/02-Testing_for_Bypassing_Authorization_Schema.html)

## User-agent
Untuk menyisipkan payload, bisa XSS atau SQL-injection.
  - [Access to staging environment via User-Agent string](https://medium.com/@yassergersy/access-to-staging-environment-via-user-agent-string-23470546577f)
  - [SQL injection through User-Agent](https://medium.com/@frostnull/sql-injection-through-user-agent-44a1150f6888)

## X-Forwarded-Host
untuk mengarahkan ke situs tertentu (attacker).
  - [Hijacking Reset Password Link in https://www.niteflirt.com/ via Host Header Poisoning (Write Up) ](https://blog.evanricafort.com/2021/02/hijacking-reset-password-link-in.html)

## X-Original-URL / X-Rewrite-Url
Untuk override sebuah request
  - [Bypass front server restrictions and access to forbidden files and directories through X-Rewrite-Url/X-original-url header on account.mackeeper.com](https://hackerone.com/reports/737323)
  - [Testing for Bypassing Authorization Schema](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/05-Authorization_Testing/02-Testing_for_Bypassing_Authorization_Schema.html)
### Step
    - Cari halaman yang mengandung 403 atau 401
    - buka halaman yang 200
    - masukkan value 403/401 pada header tsb
    
## X-Correlationid
Biasa format token berdasarkan waktu.<br>
![image](https://user-images.githubusercontent.com/52058660/168199367-4ddc9e64-f19e-4b6c-a0a9-1e759c83f856.png)<br>
nilai token diatas berarti: 2022, bulai Mei, tanggal 13, jam 8, menit 26, detik 54, dan digit random dibelakang
