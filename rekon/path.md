# Path and Content Discovery
 
 <p align="center"><img src="https://user-images.githubusercontent.com/52058660/90960320-1335ac00-e4cb-11ea-8887-70130a069fe3.png" width="700"></p>
 
## Tools
### Crawling
- [Gau](https://github.com/lc/gau)
- [Subjs](https://github.com/lc/subjs)
- [GoSpider](https://github.com/jaeles-project/gospider)
- [Hakrawler](https://github.com/hakluke/hakrawler)
- [waybackurls](https://github.com/tomnomnom/waybackurls/)
- [Burpsuite crawling](https://www.hackingarticles.in/burp-suite-for-pentester-web-scanner-crawler/)

### Fuzzing
- [FuFF - Fery fazz fuzzing](https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)
- [Dirsearch - Mature path discovery](https://github.com/maurosoria/dirsearch)</br>
  ```
  python3 dirsearch.py -u http://uhuy.com:666/ -e .asp, .aspx, .jsp, .php, .csv, .doc, .docx, .xls, .xlsx, .ppt, .pptx, .pdf, .bak, .conf, .config, .old, .sql, .jar, .rar, .zip, .tar, .tar.gz, .apk, .ipa, .cgi, .do, .htm, .html, .js, .json, .rb, .xml, .yml, .svn, .git
  ```
- [Gobuster - Multifungsi fuzzing](https://github.com/OJ/gobuster)
- [Arjun - untuk parameter](https://github.com/s0md3v/Arjun)
- [Parameth - untuk parameter juga](https://github.com/maK-/parameth)


## Javascript Recon
### Method
1. Crawl all the javascript urls (gau, hakrawler, etc.)
2. Fetch all javascript file with (meg or curls)
3. Filter for link and endpoint (linkfinder)
4. Filter for something secret (secretfinder)
5. Get hanging fruite (nuclei or jsa)
6. Manual recon (gf)

### Resource
- [Appsecco - Static Analysis of Client-Side JavaScript for pen testers and bug bounty hunters](https://blog.appsecco.com/static-analysis-of-client-side-javascript-for-pen-testers-and-bug-bounty-hunters-f1cb1a5d5288)
- [Yeasir Arafat - How to look for JS files Vulnerability for fun and profit?](https://medium.com/@Skylinearafat/how-to-look-for-js-files-vulnerability-for-fun-and-profit-78bfdfbd6731)
- [InfosecMatter - Bug Bounty Tips #4](https://www.infosecmatter.com/bug-bounty-tips-4-aug-03/)
- [Black & White Security - BugBounty | Javascript Files Recon | Beginner](https://www.youtube.com/watch?v=btG3LP_3lnA)
- [Kathan Patel](https://medium.com/@patelkathan22/beginners-guide-on-how-you-can-use-javascript-in-bugbounty-492f6eb1f9ea)
- [m4ll0k - My Javascript Recon Process](https://gist.github.com/m4ll0k/31ce0505270e0a022410a50c8b6311ff)
