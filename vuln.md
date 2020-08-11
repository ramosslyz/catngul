# Vulnerability
online resource:
- [bugbounty-cheatsheet](https://github.com/EdOverflow/bugbounty-cheatsheet) - by EdOverflow
---

## XXE
Sebelum memahami XXE, kita harus memiliki pengetahuan dasar XML, DTD dan entity. Tools yang digunakan Burpsuite, lebih mantap lagi jika menggunakan Burp Collaborator (*berbayar*).
- Detection
  - Look for applications that uses an XML format to transmit data between the browser and the server
  
- Exploitation
  - Inject [payload](https://github.com/payloadbox/xxe-injection-payload-list) ke bagian !DOCTYPE
  - Jika tidak bisa modifikasi !DOCTYPE, gunakan `XInclude`

- Prevention
  - Disable DTD
  - Disable entity saja

## Subdomain Takeover


## SQL Injection


## XSS

