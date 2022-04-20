# Cross Site Scripting
XSS bertujuan untuk mencuri cookie sehingga attacker bisa melakukan session hijacking. XSS bisa efektif jika cookie tersebut tidak termasuk HttpOnly, jika ya perlu usaha lebih lanjut. Sangat bagus dikombinasikan dengan CSRF. XSS dikelompokkan menjadi:
- **Reflected XSS**, tipe yang paling umum, contohnya seperti popup alert
- **Persistent (store) XSS**, hampir mirip seperti reflected, tapi stored didalam aplikasi web
- **DOM XSS**, XSS yang ada oada DOM environtment, two fundamental keyword -> sources and sinks
- **Universal XSS**, XSS pada extention atau plugin browser

## Impact
|Impact|Resource|
|---|---|
|Cookie gathering: script injection -> stealing -> recording and logging|[Exploiting cross-site scripting to steal cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies)
- Defacement
  - Non-persistent or Virtual, jika tidak mengubah existing content
  - Persistent, jika mengubah existing content
- Phising: Clonning website -> Choosing a domain name (urlcrazy)
- Keylogger, with Metasploit(http_javascript_keylogger) and BeEG event logger
- Network attackp: ip detection -> subnet detection -> ping sweeping -> port scanning
- Self-XSS, menkombinasikan dengan social engineering
- Password autofill
- Chain with CSRF


## Tools
  - [XSS Hunter](https://xsshunter.com/)
  - [BeEF](https://github.com/beefproject/beef)
  - [Interactsh](https://github.com/projectdiscovery/interactsh)


## Payload 
Dewasa ini, alert() sudah di disable oleh kebanyakan browser, namun banyak payload alternatif yang bisa digunakan dan memiliki efek yang sama<br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161474516-5007db3d-03f5-4e2e-b853-ac2a0be3234e.png"><img width="500" src="https://user-images.githubusercontent.com/52058660/161474550-2a34a0a8-051c-448c-a78c-daf920a07ff4.png">
<img width="500" src="https://user-images.githubusercontent.com/52058660/161482070-5620781b-8e7f-4fcb-82a1-2058520a8411.png"><br>
<img width="500" src="https://user-images.githubusercontent.com/52058660/161007476-e5215d5e-1853-4628-a8c3-976857b30e4c.png"><img width="500" src="https://user-images.githubusercontent.com/52058660/161009852-1085935b-5a5e-4d5b-a0d1-369c54c2dcb4.png">
<img width="500" src="https://user-images.githubusercontent.com/52058660/161014105-44de9c1e-e57c-4db5-8b3f-147cda5375be.png">

## How to find them ?
### Reflected XSS
- Search form. cek apakah reflected

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

