# CSRF


Cross Site Request Forgery adalah serangan yang memaksa pengguna agar backend mengeksekusi perintah yang tidak seharusnya dizinkan, menipu website dari request user yang terpercaya dan mengirim Request palsu dari authenticate user.

![image](https://user-images.githubusercontent.com/52058660/121773442-33437280-cba6-11eb-8890-9f5d2f7900fa.png)


## HOW TO FIND THEM
![image](https://user-images.githubusercontent.com/52058660/121527083-3adb0e00-ca24-11eb-800a-f675f28fee14.png)
![image](https://user-images.githubusercontent.com/52058660/121529015-3152a580-ca26-11eb-8676-6c2ab13449e5.png)
- The easiest way to check whether an application is vulnerable is to see if each link and form contains an unpredictable token for each user. Without such an unpredictable token, attackers can forge malicious requests. Focus on the links and forms that invoke state-changing functions, since those are the most important CSRF targets.
- Mengganti content-type non-form  (i.e. `application/json, application/x-url-encoded`, etc.) menjadi `form-multipart`[(2)](#write-up)
- Periksa parameter state. State parameter is used in Oauth to prevent CSRF attacks[(3)](#write-up)
- "When first hunting for CSRF bugs I look for areas on the website which should contain protection around them, such as updating your account information."[(7)](#resource)
  - What behavior do you see when sending a blank CSRF value, did it reveal any framework information from an error?
  - Did it reflect your changes but with a CSRF error?
  - Have you seen this parameter name used on other websites? Perhaps there isn’t even any protection! Test their most secure features (account functions usually as mentioned above) and work your way backwards.
- Salah satu langkah preventif untuk menanggulangi CSRF adalah memastian referer header berisikan website yang valid. Tapi bagaimana jika fielder header tersebut dihilangkan? kadang kita bisa membypass nya dengan meta tag berikut.[(7)](#resource)
```
<meta name="referrer" content="no-referrer" />
<iframe src=”data:text/html;base64,form_code_here”>
```
- Kadang developer juga hanya memastika bahwa referer header mengandung domain mereka, kita bisa mengakalinya dengan menambahkan sebuah direktori dengan domain target pada evil server kita, contoh: `https://www.yoursite.com/https://www.theirsite.com/` atau `https://www.theirsite.computer/`.[(7)](#resource)


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
1. [OWASP - Cross Site Request Forgery (CSRF)](https://owasp.org/www-community/attacks/csrf)
2. [OWASP - Reviewing Code for Cross-Site Request Forgery Issues Overview](https://owasp.org/www-project-code-review-guide/reviewing-code-for-csrf-issues)
3. [OWASP Web Security Testing Guide - Testing for Cross Site Request Forgery](https://github.com/OWASP/wstg/blob/master/document/4-Web_Application_Security_Testing/06-Session_Management_Testing/05-Testing_for_Cross_Site_Request_Forgery.md)
4. [OWASP Cheat Sheet Series - Cross-Site Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)
5. [InsiderPhD - Finding Your First Bug: Cross-Site Request Forgery (CSRF)](https://www.youtube.com/watch?v=ULvf6N8AL2A)
6. [CSRF, CORS, and HTTP Security headers Demystified](https://blog.vnaik.com/posts/web-attacks.html)[PayloadsAllTheThings - Cross-Site Request Forgery](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/CSRF%20Injection#methodology)
7. [Zseano's Methodology - CSRF](https://www.bugbountyhunter.com/methodology/loader.php#page=22)
8. [BugBountyHunter - CSRF](https://www.bugbountyhunter.com/vulnerability/?type=csrf)


## WRITE-UP
1. [CSRF at Kaskus.co.id](https://medium.com/@daffailhamr/csrf-at-kaskus-co-id-f8e31864807f)
2. [Refocusing in bug hunting, Bonus: An interestingly simple to test CSRF bypass](https://medium.com/bugbountywriteup/refocusing-in-bug-hunting-bonus-an-interestingly-simple-to-test-csrf-bypass-8595b3312147)
3. [Got Nice catch by Google](https://parthdeshani.medium.com/got-nice-catch-by-google-5e6a8211371c)


## LAB
- [Portswigger Academy - Cross-site request forgery (CSRF)](https://portswigger.net/web-security/csrf)
- [OWASP Juice Shop - Broken Access Control](https://owasp.org/www-project-juice-shop)
- [OWASP Security Knowledge Framework - CSRF](https://owasp-skf.gitbook.io/asvs-write-ups/kbid-5-csrf)
