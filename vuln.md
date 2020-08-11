# Vulnerability
online resource:
- [bugbounty-cheatsheet](https://github.com/EdOverflow/bugbounty-cheatsheet) - by EdOverflow
---

## XXE
Untuk memahami XXE anda harus memiliki pengetahuan dasar XML, DTD dan entity. Tools yang digunakan untuk adalah Burpsuite, lebih mantap lagi jika menggunakan Burp Collaborator (*berbayar*).
- Detection
  - Look for applications that uses an XML format to transmit data between the browser and the server.
  
- Exploit
  - Inject payload ke bagian !DOCTYPE. 
  - [xxe-injection-payload-list](https://github.com/payloadbox/xxe-injection-payload-list) - by Payload Box 
  - Jika tidak bisa modifikasi !DOCTYPE, gunakan `XInclude`

- Prevention
  - Disable DTD
  - Disable entity saja

## Subdomain Takeover


## SQL Injection


## XSS

