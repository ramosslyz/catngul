# Vulnerability
online resource:
- [bugbounty-cheatsheet](https://github.com/EdOverflow/bugbounty-cheatsheet) - by EdOverflow
---

## XXE
Sebelum memahami XXE, kita harus memiliki pengetahuan dasar XML, DTD dan entity. Tools yang digunakan Burpsuite, lebih mantap lagi jika menggunakan Burp Collaborator (*berbayar*).
- Detection
  - [Cari](https://christian-schneider.net/GenericXxeDetection.html) aplikasi yang mengirimkan data dalam format XML
  - Intercept web page, lalu lihat request header`Content-Type: text/xml` atau `application/xml
  - Cara cepat menemukan XML endpoint adalah automasi
  - Cari fitur web yang mengunakan XML, seperti RSS
  
- Exploitation
  - Retrieve Files
    - Inject [payload](https://github.com/payloadbox/xxe-injection-payload-list) ke bagian !DOCTYPE
    - `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM “file:///etc/passwd”> ]>`
  - Exploiting to perform Server Side Request Forgery (SSRF)
    - Sama seperti cara di atas. Tapi jika sebelumnya menggunakan `file`, untuk exploitasi ini menggunakan `http` dilanjutkan dengan ip server
    - `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM “http://1”> ]>`
  - Jika tidak bisa modifikasi !DOCTYPE, gunakan `XInclude`
  - Test local machine port (gunakan burp intruder): `<!DOCTYPE data SYSTEM "http://127.0.0.1:§port§/"` juga cek http (port 80) dan https (port 443)

- Prevention
  - Disable DTD
  - Disable entity saja
---
## Subdomain Takeover

---
## SQL Injection

---
## XSS

