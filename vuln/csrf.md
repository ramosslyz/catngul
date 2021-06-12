# CSRF


Cross Site Request Forgery adalah serangan yang memaksa pengguna agar backend mengeksekusi perintah yang tidak seharusnya dizinkan, menipu website dari request user yang terpercaya dan mengirim Request palsu dari authenticate user.


## HOW TO FIND THEM
![image](https://user-images.githubusercontent.com/52058660/121527083-3adb0e00-ca24-11eb-800a-f675f28fee14.png)
![image](https://user-images.githubusercontent.com/52058660/121529015-3152a580-ca26-11eb-8676-6c2ab13449e5.png)
- The easiest way to check whether an application is vulnerable is to see if each link and form contains an unpredictable token for each user. Without such an unpredictable token, attackers can forge malicious requests. Focus on the links and forms that invoke state-changing functions, since those are the most important CSRF targets.
- Mengganti content-type non-form  (i.e. `application/json, application/x-url-encoded`, etc.) menjadi `form-multipart`[(2)](#write-up)
- Periksa parameter state. State parameter is used in Oauth to prevent CSRF attacks[(3)](#write-up)


## POC
POC berikut bisa disesuaikan dengan parameter yang pada form html target. Script js berfungsi untuk meng-submit otomatis form tanpa menekan button. 
  ```
  <form method="$method" action="$url">
    <input type="hidden" name="$param1name" value="$param1value">
    <input type="submit" value="submit">
  </form>
  <script> document.forms[0].submit();</script>
  ```


## CORS MISCONFIGURATION
Sebenarnya CORS malah melemahkan browser karena melonggarkan aturan dari Same-origin policy sehingga apabila terjadi misconfigurasi CORS, attacker dapat memanfaatkan celah tersebut untuk melancarkan serangan CSRF.


## PREVENTION
### CSRF Token
- CSRF token should be generated on the server-side
- CSRF token should not be transmitted using cookies
- CSRF token should be unique per session, secret, and unpredictable
- CSRF token should no be leaked in the server logs or in the URL

### Double submit Cookie
```
POST /email/change HTTP/1.1
Host: vulnerable-website.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 68
Cookie: session=1DQGdzYbOJQzLP7460tfyiv3do7MjyPw; csrf=R8ov2YBfTYmzFyjit8o2hKBuoIjXXVpa

csrf=R8ov2YBfTYmzFyjit8o2hKBuoIjXXVpa&email=wiener@normal-user.com 
```

### Samesite Cookie
- bisa dibypass dengan modifikasi GET
```
Set-Cookie: JSESSIONID=xxxxx; SameSite=Strict
Set-Cookie: JSESSIONID=xxxxx; SameSite=Lax
```


## RESOURCE
- [OWASP - Cross Site Request Forgery (CSRF)](https://owasp.org/www-community/attacks/csrf)
- [OWASP - Reviewing Code for Cross-Site Request Forgery Issues
Overview](https://owasp.org/www-project-code-review-guide/reviewing-code-for-csrf-issues)
- [OWASP Web Security Testing Guide - Testing for Cross Site Request Forgery](https://github.com/OWASP/wstg/blob/master/document/4-Web_Application_Security_Testing/06-Session_Management_Testing/05-Testing_for_Cross_Site_Request_Forgery.md)
- [OWASP Cheat Sheet Series - Cross-Site Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)
- [InsiderPhD - Finding Your First Bug: Cross-Site Request Forgery (CSRF)](https://www.youtube.com/watch?v=ULvf6N8AL2A)
- [CSRF, CORS, and HTTP Security headers Demystified](https://blog.vnaik.com/posts/web-attacks.html)
- [PayloadsAllTheThings - Cross-Site Request Forgery](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/CSRF%20Injection#methodology)


## WRITE-UP
1. [CSRF at Kaskus.co.id](https://medium.com/@daffailhamr/csrf-at-kaskus-co-id-f8e31864807f)
2. [Refocusing in bug hunting, Bonus: An interestingly simple to test CSRF bypass](https://medium.com/bugbountywriteup/refocusing-in-bug-hunting-bonus-an-interestingly-simple-to-test-csrf-bypass-8595b3312147)
3. [Got Nice catch by Google](https://parthdeshani.medium.com/got-nice-catch-by-google-5e6a8211371c)


## LAB
- [Portswigger Academy - Cross-site request forgery (CSRF)](https://portswigger.net/web-security/csrf)
- [OWASP Juice Shop - Broken Access Control](https://owasp.org/www-project-juice-shop)
- [OWASP Security Knowledge Framework - CSRF](https://owasp-skf.gitbook.io/asvs-write-ups/kbid-5-csrf)
