# Vulnerability
online resource:
- [bugbounty-cheatsheet](https://github.com/EdOverflow/bugbounty-cheatsheet) - by EdOverflow
---

## XXE
Sebelum memahami XXE, kita harus memiliki pengetahuan dasar XML, DTD dan entity. Tools yang digunakan Burpsuite, lebih mantap lagi jika menggunakan Burp Collaborator (*berbayar*).
- Detection
  - Cari aplikasi yang mengirimkan data dalam format XML
  - Intercept web page, lalu lihat request header`Content-Type: text/xml` atau `application/xml`
  - Cari fitur web yang mengunakan XML, seperti RSS
  
- Exploitation
  - Inject [payload](https://github.com/payloadbox/xxe-injection-payload-list) ke bagian !DOCTYPE
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

