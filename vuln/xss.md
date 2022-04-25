# Cross Site Scripting
- **Reflected XSS**, tipe yang paling umum, contohnya seperti popup alert
- **Persistent (store) XSS**, hampir mirip seperti reflected, tapi stored didalam aplikasi web
- **DOM XSS**, XSS yang ada oada DOM environtment, two fundamental keyword -> sources and sinks
- **Universal XSS**, XSS pada extention atau plugin browser

## Impact
|Impact|Resource|
|---|---|
|Cookie gathering: script injection -> stealing -> recording and logging|[Exploiting cross-site scripting to steal cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies)|
|Capture password through password auto-fill|[Exploiting cross-site scripting to capture passwords](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capturing-passwords)|
|Chain with CSRF|[Exploiting XSS to perform CSRF](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-perform-csrf)|
|Defacement<br>- Non-persistent or Virtual, jika tidak mengubah existing content<br>- Persistent, jika mengubah existing content||
|Phising: Clonning website -> Choosing a domain name (urlcrazy)||
|Keylogger, with Metasploit(http_javascript_keylogger) and BeEG event logger||
|Network attackp: ip detection -> subnet detection -> ping sweeping -> port scanning||
|Self-XSS, menkombinasikan dengan social engineering||


## Tools
  - [XSS Hunter](https://xsshunter.com/) - ???
  - [Interactsh](https://github.com/projectdiscovery/interactsh) - Burp collaborator alternative
  - [BeEF](https://github.com/beefproject/beef) - ???


## Payload 
Dewasa ini, alert() sudah di disable oleh kebanyakan browser, namun banyak payload alternatif yang bisa digunakan dan memiliki efek yang sama<br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161474516-5007db3d-03f5-4e2e-b853-ac2a0be3234e.png"><img width="500" src="https://user-images.githubusercontent.com/52058660/161474550-2a34a0a8-051c-448c-a78c-daf920a07ff4.png">
<img width="500" src="https://user-images.githubusercontent.com/52058660/161482070-5620781b-8e7f-4fcb-82a1-2058520a8411.png"><br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161007476-e5215d5e-1853-4628-a8c3-976857b30e4c.png"><img width="500" src="https://user-images.githubusercontent.com/52058660/161009852-1085935b-5a5e-4d5b-a0d1-369c54c2dcb4.png">
<img width="500" src="https://user-images.githubusercontent.com/52058660/161014105-44de9c1e-e57c-4db5-8b3f-147cda5375be.png">

## How to find them ?
### Reflected XSS
- Search form. cek apakah reflected

### Stored XSS
- Comment posting

### Based on context
#### XSS betwen HTML tags
|Tips|Resource|
|---|---|
|Membutuhkan some HTML tag untuk mentrigger script javascript, seperti `<script>alert(document.domain)</script>` atau `<img src=1 onerror=alert(1)>`. Analisa semua entry point yang mereflected-kan input|[Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)|
|Analisa Semua entry point yang men-stored-kan payload|[Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)|
|Mencari tahu Tag HTML dan atribut apa yang tidak diblok oleh WAF. menggunakan intruder dan memanfaatkan payload dari portswigger|[Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)|
#### XSS in HTML tags
#### XSS in tags aribut
#### XSS into javascript
#### XSS in the context of the AngularJS
### Urutan inject payload
Selalu mulai dengan payload yang paling simpel dan secara bertahap menuju ke payload yang ribet
1. Test inject normal, masukkan payload normal yang seharusnya user masukkan dengan aman. berfungsi untuk memperlajari cara kerja aplikasi
2. Test filtering, input karakter yang seharusnya tidak diinputkan oleh user, seperti <>;'"=`\'/ . Cek reaksi aplikasi apakah difilter? apakah stored? apakah reflected ?
3. Test inject tag html, mulai dari yang tidak berbahaya seperti <b>, <h1> dan <i>, lanjutkan inject tag yang umumnya di block oleh waf seperti <script> dan alert(1). Bagaiamana response aplikasi ?
4. Jika tag diatas di tolak, coba brute tag html, jika sudah menemukan tag yang diaccept aplikasi, lanjutkan brute event yang diaccept aplikasi.
5. Test encoding payload

## How to protect ?
- HTTPOnly
- XST
- CVE-2012-0054 (Apache HTTP Server 2.2.x through 2.2.21) -> bisa manual bisa juga menggunakan BeEF <br><img width="500" src="https://user-images.githubusercontent.com/52058660/161483548-3ac21b8c-d55a-4b5c-b9ea-22c0d18d20ae.png"> 


## Resource
  - [Stealing HttpOnly Cookie via XSS](https://medium.com/@yassergersy/xss-to-session-hijack-6039e11e6a81)
  - [The Dark Side of XSS revealed](https://blog.yeswehack.com/best-practices/the-dark-side-of-xss-revealed/)
  - [Finding Your First Bug: Cross Site Scripting (XSS)](https://www.youtube.com/watch?v=IWbmP0Z-yQg)
  - [Script to take advantage of CVE-2012-0053](https://gist.github.com/pilate/1955a1c28324d4724b7b)
  - [filterbypass](https://github.com/masatokinugawa/filterbypass/wiki/Browser's-XSS-Filter-Bypass-Cheat-Sheet)
  - [alert() is dead, long live print()](https://portswigger.net/research/alert-is-dead-long-live-print)
  - [Do NOT use alert(1) in XSS](https://liveoverflow.com/do-not-use-alert-1-in-xss/)
  - [Cross-site scripting (XSS) cheat sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

